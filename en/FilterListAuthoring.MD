# Filter List Authoring

A filter list is simply a text file, it can be served over HTTPS or file system.
HTTP is also accepted for backwards compatibility. However, unless served from
localhost, filter lists served over HTTP may be rejected in the future.

## Headers

Although optional, it is highly recommended that you write a well formatted
header. This can not only help others to understand the purpose of your filter,
but also make automated indexing easier.

Unlike Adblock Plus, Nano Adblocker and uBlock Origin will **only** parse a
limited set of headers. Any headers that you want to be parsed must also be in
the first 1024 characters of your filter list, and only the *first* one will
take effect if you have duplicate headers (for example, if you have 3 title
headers, then the first one that appears will override the next two). Note that
Adblock Plus will instead take the *last* one in case of duplicate.

### `! Title: <title>` or `# Title: <title>`

Indicates the title of the filter list, it is displayed in filter lists manager.
If this header is missing, the URL of the filter list will be used.

Examples:
```
! Title: My Filter List
# Title: My Hosts File
```

### `! Expires: <time>` or `# Expires: <time>`

Indicates the update interval of the filter list. Time can be expressed as days
or hours, but you must use an integer in either case. If you use hour as unit,
it will be rounded *up* to the nearest day. The lower cap is 1 day and the upper
cap is 60. uBlock Origin does not enforce an upper cap. Shorthands such as `1d`
and `24h` are also accepted. If you omit the unit, it will be assumed to be
days.

If this header is missing, Nano Adblocker will default to 3 days and uBlock
Origin will default to 5. Some built-in filter lists of Nano Adblocker
also have different update intervals than uBlock Origin, please check the
appropriate `assets.json` file for more details. Note that this header will
override the value set in `assets.json`.

If your filter list used to have this header, but removed (or became invalid)
later, then Nano Adblocker will reset the update interval to the default value;
uBlock Origin does not do this and will keep the last update interval that it
has.

The header is only parsed until the first letter of time unit, so you can add
comments after.

Examples:
```
! Expires: 3 (this means 3 days)
! Expires: 1d (this is some comments)
# Expires: 36h (this is rounded up to 2 days)
! Expires: 1 day
! Expires: 24 hours
# Expires: 3 days
# Expires: 3 days (update interval)
```

### Other Common Headers

The first line of most filter lists is `[Adblock Plus 2.0]`; you should name
the primary adblocker that your filter list support, that is, `[Nano Adblocker]`
or `[uBlock Origin]`. Keep in mind that even if you write `[Adblock Plus 2.0]`,
Adblock Plus will still reject your filter list if you use extended filter
syntax. Note that if you want your filter to work at all in Adblock Plus, then
this first line must be `[Adblock Plus 2.0]`.

As a side note, lines starting with `[` are treated as comments in Nano
Adblocker and uBlock Origin.

Although not parsed, these are some headers that you should consider including:
- `[! or #] Description: <short description>`
- `[! or #] Author[s]: <author or list of authors>`
- `[! or #] Version: <version number>`
- `[! or #] Last modified: <date>`
- `[! or #] Homepage: <URL>`
- `[! or #] Support: <URL or email>`
- `[! or #] Licen[s or c]e: <SPDX license identifier or URL>`

## Publishing

Although users can easily subscribe to filter lists from the dashboard, it is
usually better to allow them to subscribe by simply clicking a link.

To make such link, you need to assign `href` of an anchor element (`<a>`) to:
```
ubo://subscribe?location=<URL>&title=<title>
```

Make sure the URL is pointing to a *raw* text file and not HTML. Also, only
anchor elements work, and the click must be initiated by the user. If you abuse
this feature, your domain will be blacklisted.

At lease one of such link must be present on the page within 997 milliseconds
(0.997 seconds) after `load` event is fired. This also means those links will
not work until this timeout finishes.

Unlike Adblock Plus, Nano Adblocker and uBlock Origin do not parse the link
like a query string, so do not switch the order of `location` and `title`.
You should encode the URL and title with `encodeURIComponent`. Also, the title
field is required even though it does not replace the `title` header.

Note that `abp://` is also accepted, but it is recommended to use `ubo://` for
filter lists with extended syntax.

Examples (with URL to be `https://example.com/filter.txt` and title `My
Filter`):
```
ubo://subscribe?location=https%3A%2F%2Fexample.com%2Ffilter.txt&title=My%20Filter
abp://subscribe?location=https%3A%2F%2Fexample.com%2Ffilter.txt&title=My%20Filter
```

If custom protocol cannot be used, you can also use the dummy domain
`subscribe.adblockplus.org`:
```
https://subscribe.adblockplus.org/?location=<URL>&title=<title>
```
