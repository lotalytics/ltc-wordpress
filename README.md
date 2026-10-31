# Lotalytics – Lottery Results (WordPress plugin)

The WordPress plugin for [Lotalytics](https://lotalytics.com): latest lottery
results and next-draw dates for 50+ lotteries, as blocks, shortcodes and a
classic widget. Spec: `docs/backlog/WORDPRESS_PLUGIN.md` in the ltc API repo.

GPL-2.0-or-later, like WordPress.

## Layout

- `lotalytics-lottery-results/` — the plugin, exactly as it ships.
- `dev/` — local WordPress in Docker, the wp-cli wrapper, the translation seed.
- `bin/build-zip.sh` — packages the plugin folder into `dist/`.

## Develop

```
docker compose -f dev/docker-compose.yml -p ltcwp up -d
dev/wp core install --url=http://localhost:8089 --title=LTC --admin_user=admin \
  --admin_password=admin --admin_email=admin@example.com --skip-email
dev/wp plugin activate lotalytics-lottery-results
```

Before a release: `dev/wp plugin install plugin-check --activate` then
`dev/wp plugin check lotalytics-lottery-results` must report no errors, and
every PHP file must lint on PHP 7.4 (the declared minimum):

```
docker run --rm -v "$PWD/lotalytics-lottery-results:/p:ro" php:7.4-cli \
  sh -c 'for f in $(find /p -name "*.php"); do php -l "$f"; done'
```

## Translations

Strings change → `dev/wp i18n make-pot wp-content/plugins/lotalytics-lottery-results wp-content/plugins/lotalytics-lottery-results/languages/lotalytics-lottery-results.pot`,
add the new strings to `dev/translations.py`, run it, then `dev/wp i18n make-mo`
and `dev/wp i18n make-php` on the languages folder. Once the plugin is on
wordpress.org, translate.wordpress.org takes over and wins over these files.

## Release to wordpress.org

1. Bump `Version:` in the plugin header and `Stable tag:` in `readme.txt` together, add a changelog entry.
2. Plugin Check and the PHP 7.4 lint above must be clean.
3. `bin/build-zip.sh` → `dist/lotalytics-lottery-results-<version>.zip` (the plugin folder only).
4. **First release only:** upload the zip at https://wordpress.org/plugins/developers/add/ from the `lotalytics` wordpress.org account and wait for review. Answer the reviewers by email from the same account.
5. **After approval (and every later release):** SVN. Copy the plugin folder into `trunk/`, `svn cp trunk tags/<version>`, and copy `.wordpress-org/*` into the SVN `assets/` folder (icons, banners, screenshots; never inside the zip).

`.wordpress-org/` holds the listing art. Screenshots are real captures of the dev site; icon and banner were rendered from HTML with the brand gradient. The listing deliberately shows result balls, not the Lotalytics die: the plugin is information-only and the art should not read as gambling.
