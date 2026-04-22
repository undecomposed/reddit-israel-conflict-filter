# Reddit Israel/Palestine Topic Suppression Filter

This repository contains a custom filter list for hiding Reddit content related to the Israel/Palestine topic area.

The filter is intended for use with:

- uBlock Origin
- AdGuard

The main filter file is:

- [reddit-conflict-filter.txt](https://raw.githubusercontent.com/undecomposed/reddit-israel-conflict-filter/refs/heads/main/reddit-conflict-filter.txt)

What it does:

- hides posts whose titles match the blocked topic patterns
- hides comments whose visible text matches the blocked topic patterns
- hides inbox notifications whose title or body matches the blocked topic patterns
- hides posts from subreddits and communities whose names match the blocked topic patterns
- hides Reddit search result cards and previews that match the blocked topic patterns
- blocks direct visits to subreddit paths that match the blocked topic patterns

How keyword matching works:

- text-based rules use a shared regex pattern near the top of the filter file
- some Reddit-specific rules must repeat keywords literally because ABP-style filter syntax does not support reusable variables
- wildcard-style matching in path rules and broader regex matching in text rules both need to be kept in sync
- notification filtering applies to inbox rows, notification titles, and notification bodies

How to add more keywords:

1. Update the regex comment near the top of `reddit-conflict-filter.txt`.
2. Add any needed literal matches for subreddit path blocking.
3. Add any needed literal matches for Reddit metadata attributes where the file already repeats keywords.
4. Reload the custom filter list in your blocker.

How to add it to uBlock Origin:

1. Click the uBlock Origin icon.
2. Click the gear icon labeled Open the dashboard.
3. Open the Filter lists tab.
4. Click `Import...` at the very bottom of the list.
5. Paste `https://raw.githubusercontent.com/undecomposed/reddit-israel-conflict-filter/refs/heads/main/reddit-conflict-filter.txt`.
6. Click Apply changes at the top.
7. Reload any Reddit pages that were already open.

This adds the filter list as a subscribed list in uBlock Origin.

Known limitations:

- Reddit changes markup often, so selectors may need adjustment over time
- some search, recommendation, or comment layouts may require additional selectors
- ABP-style filters cannot define a keyword list once and reference it everywhere
- cosmetic filtering hides matching content in the page; it does not change Reddit’s underlying search index or recommendations at the source

Maintenance notes:

- the filter metadata currently uses `! Expires: 1 day`
- that expiration value is only a refresh hint for subscribed lists
- if the rules are pasted manually into `My filters`, the expiration value has little practical effect
