# ozb.txt

A simple RSS deal and news reader that looks like a plain text file. No API keys, no subscriptions, no costs.

## Setup

1. Download `index.html`
2. Upload to a GitHub repo
3. Go to **Settings → Pages → Deploy from main branch**
4. Access at `https://yourusername.github.io/yourrepo/`

You can also just open `index.html` directly in your browser, though hosting on GitHub Pages works more reliably for fetching external feeds.

## Feeds

| Feed | Source |
|---|---|
| OzBargain | https://www.ozbargain.com.au/feed |
| ABC News | https://www.abc.net.au/news/feed/51120/rss.xml |
| Guardian AU | https://www.theguardian.com/australia-news/rss |
| BBC Tech | https://feeds.bbci.co.uk/news/technology/rss.xml |

Enable or disable feeds using the checkboxes at the top. OzBargain is on by default.

## Features

- **Keyword filter** — Type in the search box to filter deals by title or description. Matches highlight in yellow.
- **Sort** — Toggle between newest and oldest.
- **Mark as read** — Click a deal title or press "mark read" to fade it out. Click "unread" to restore it. Read state is saved in your browser.
- **Hide read** — Press the "Toggle Read" button (or `H`) to hide all read deals.
- **Comments** — Click `[view comments]` on OzBargain deals to load comments inline. Only available for OzBargain.
- **Expired deals** — OzBargain deals older than 7 days are automatically faded and struck through.
- **Auto-refresh** — Feeds refresh every 15 minutes automatically.

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `ESC` | Toggle stealth mode (switches to a fake config file) |
| `R` | Refresh all feeds |
| `H` | Toggle hide/show read deals |
| `/` | Focus the search box |

## How It Works

- Fetches RSS feeds directly from the source sites using public CORS proxies
- Parses the XML client-side — no server or backend needed
- Comments are scraped from the OzBargain deal page when you click to load them
- Read state is stored in browser localStorage
- Everything runs in a single HTML file with no dependencies

## Troubleshooting

**Feeds not loading**
The page relies on third-party CORS proxies to fetch RSS feeds. If all proxies are down or blocked, feeds will fail to load. Try again in a few minutes, or check if you can access the feed URLs directly in your browser.

**Comments not loading**
OzBargain may block or rate-limit proxy requests for full page scrapes. If comments fail, open the deal directly on the OzBargain site.

**Adding new feeds**
Open `index.html` in a text editor. Find the `FEEDS` object near the top of the script and add a new entry:

```js
yourfeed: { url: 'https://example.com/rss.xml', label: 'YF' }
```

Then add a matching checkbox in the HTML controls section.

## Version History

| Version | Changes |
|---|---|
| v10 | Rewrote proxy system with fallbacks and timeouts. Fixed corsproxy.io format change. Added separate proxy lists for RSS vs HTML. Fixed keyboard shortcuts firing while typing in search. |
| v9 | Added multiple RSS feeds, keyword search, sort, read/hide system, auto-refresh, expired deal detection, keyboard shortcuts, stealth mode. |
| v8 | Made links black with no underline to match plain text aesthetic. |
| v7 | Removed all blue link styling and underlines. |
| v6 | Stripped all visual styling to look like Windows 11 Notepad. |
| v5 | Added duplicate comment filtering. |
| v4 | Fixed single-click comments loading. Filtered out login prompt from comments. |
| v3 | Added inline comments scraping from OzBargain deal pages. |
| v2 | Added multiple CORS proxy fallbacks. |
| v1 | Initial version. Single HTML file, OzBargain RSS feed, plain text layout. |
