=== Lotalytics – Lottery Results ===
Contributors: lotalytics
Tags: lottery results, lotto, winning numbers, draw results, lottery
Requires at least: 6.5
Tested up to: 7.1
Requires PHP: 7.4
Stable tag: 0.2.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Official winning numbers and next draw dates for 50+ lotteries, as blocks, shortcodes or a widget. Information only: no betting, no tickets.

== Description ==

Readers come looking for the winning numbers the evening of every draw. This plugin puts them on your site: the latest results and the next draw date of Powerball, Mega Millions, EuroMillions, Eurojackpot, Lotto 6/49, SuperEnalotto, Mega-Sena, Bonoloto and 40+ other lotteries, kept current on their own. Add a block, pick a game, done: no account, no key, no cost.

It suits local news sites, community and hobby blogs, and any site whose readers ask "what were last night's numbers?".

= Information only, not gambling =

The plugin publishes public facts, as announced by the official lottery operators: winning numbers, bonus numbers and draw dates. It is not a gambling product.

* It does not sell tickets, take bets or wagers, or handle money of any kind.
* It does not link to, advertise or earn commissions from lottery operators, ticket resellers or betting sites.
* It shows no predictions, tips, "hot numbers" or systems, and never suggests that any number is more likely to be drawn.
* It collects nothing about your visitors.

Lotalytics is an independent results and statistics service. It is not affiliated with, endorsed by or connected to any lottery operator. Game names such as Powerball, Mega Millions and EuroMillions are trademarks of their owners and are used only to name the games. Always check a ticket against the official lottery's own results.

= What you get =

* **Two blocks**: "Lottery results" (the latest 1–5 draws) and "Next lottery draw".
* **Shortcodes** for classic themes and page builders: `[lotalytics_results game="powerball" draws="5"]` and `[lotalytics_next_draw game="powerball"]`.
* **A classic widget** for widget areas.
* **Fits your theme**: the blocks take your theme's colours, fonts and spacing; the stylesheet is tiny, only loads where results are shown, and can be turned off. Templates can be overridden from your theme (`yourtheme/lotalytics/latest-results.php`).
* **Fast**: results are fetched by your server and cached; your pages never wait on us, and if the service is briefly unavailable the last results are shown.
* **In your language**: English, Spanish, Portuguese, French, German and Italian. Dates follow your site's date format.
* **No tracking, no ads**: nothing about your visitors is collected or sent, and the plugin adds no advertising to your pages.

= With a Lotalytics API key =

Add a key under **Settings → Lotalytics** (or define `LOTALYTICS_API_KEY` in wp-config.php). Paid plans add:

* **A results archive**: the "Lottery results archive" block and `[lotalytics_archive game="powerball"]`, every past draw your plan covers, page by page.
* **A results section on your site**: `/lottery/` (the address is a setting), `/lottery/powerball/` and a page per draw such as `/lottery/powerball/2026-10-14/`, inside your theme, with their own titles, descriptions and canonical links, and listed in your WordPress sitemap.
* **Pre-fetching**: after each draw the plugin refreshes the results in the background, so visitors never wait.

The settings page shows your plan, its games and your usage. Near the plan's request limit the plugin caches for longer, and Site Health tells you. The free results blocks never spend your key's requests.

= External service =

This plugin is a front end for the **Lotalytics** results service (https://lotalytics.com). It requests data from `https://api.lotalytics.com` to display lottery results:

* **What is sent, and when**: when a page with results is rendered and the cached copy has expired, your server requests `https://api.lotalytics.com/public/embed/<game>` with the number of draws, the page language and your site's home address; the editor's game list comes from `https://api.lotalytics.com/public/games`. With an API key, the archive and draw pages come from `https://api.lotalytics.com/v1/…` with your key in the request header; the settings page reads `/v1/account`; "Register this site" sends your site's address to `/v1/account/sites`. The requests are made by your server, never by your visitors' browsers (your key never reaches a browser), and contain no information about your visitors.
* **Terms of service**: https://lotalytics.com/terms
* **Privacy policy**: https://lotalytics.com/privacy

= Credit link =

The plugin never adds a link to your site unless you ask it to. Under **Settings → Lotalytics** you can turn on a small "Results by Lotalytics" credit under the results. The free service asks sites that use it to show this credit.

= For developers =

Filters: `lotalytics_results_data` (the payload before rendering), `lotalytics_ball_html` (one ball), `lotalytics_credit_html`, `lotalytics_cache_ttl` (seconds), `lotalytics_api_base` (point the plugin at a staging API; or define `LOTALYTICS_API_BASE` in wp-config.php). Every CSS colour and size is a custom property (`--ltc-ball-bg`, `--ltc-bonus-bg`, `--ltc-ball-size`…).

== Installation ==

1. Install and activate the plugin.
2. Add the "Lottery results" block to a page (or the shortcode, or the widget) and pick a game.
3. Optional: set a default game, and the credit link, under Settings → Lotalytics.

== Frequently Asked Questions ==

= Is it free? =

Yes. The plugin is free, and the latest-results blocks use Lotalytics' free service, no key needed. A paid Lotalytics API plan adds the archive and a results section with a page per draw.

= Is this a gambling plugin? =

No. It shows public lottery results and draw dates, the same facts a newspaper prints. It sells nothing, takes no bets, links to no lottery or betting site, and makes no predictions. See "Information only, not gambling" above.

= Where do the results come from? =

From the official results each lottery publishes. Lotalytics collects them after every draw and checks them before they are shown. The plugin always names the draw date, so readers can compare with the official source.

= Do I have to link to Lotalytics? =

No. The plugin never adds a link on its own. You can turn on a small credit under the results in Settings → Lotalytics if you'd like to credit the source.

= How fast do results appear after a draw? =

Usually within minutes of the official results being published. The plugin checks more often around a game's draw date.

= Which games are supported? =

Every game listed at https://lotalytics.com/games: the US multi-state and state games, the UK and European lotteries, Canada, Australia, Brazil, Mexico and more. The block's game picker always shows the current list.

= The results look different from my theme =

The blocks follow your theme's colours and fonts. To restyle further, override the CSS custom properties in your theme, turn the plugin stylesheet off in Settings → Lotalytics, or copy a template into `yourtheme/lotalytics/`.

== Screenshots ==

1. Results on a news site using Twenty Twenty-Five: the "Lottery results" and "Next lottery draw" blocks.
2. The block settings in the editor: game, number of draws, title, compact mode.
3. Settings → Lotalytics: optional API key, results section, credit link (off by default), default game.

== Changelog ==

= 0.2.0 =
* API keys: a key field with your plan, games and usage; "Register this site" for the free plan's credit link.
* The "Lottery results archive" block and `[lotalytics_archive]`.
* A results section on your site (`/lottery/…`) with a page per draw, in your sitemap.
* Hourly pre-fetch after draws; longer caching near a plan's limit; Site Health checks the key.
* Fixes: a failed request is no longer retried on every page view; "Clear cached results" also clears copies kept during an outage; "Disable the plugin stylesheet" now also covers the blocks.

= 0.1.0 =
* First release: "Lottery results" and "Next lottery draw" blocks, shortcodes, classic widget, opt-in credit link, six languages.
