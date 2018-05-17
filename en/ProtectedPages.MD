# Protected Pages

Every browser has some pages that are protected from extensions. Requests from
these pages may not be blockable and cosmetic filtering will not work on these
pages.

## Chrome and Chromium

Fully protected:
* `chrome://` scheme
* `chrome-extension://` scheme of other extensions
* `https://chrome.google.com/` (extension store) except YouTube embeds

Partially protected:
* The default new tab page, only network requests can be filtered

## Edge

Fully protected:
* The default new tab page
* `ms-browser-extension://` scheme

## Firefox

Fully protected:
* `about:` scheme
* The default new tab page
* `https://addons.mozilla.org/` (extension store), network requests are visible
  from extensions, but cannot be filtered or redirected (this includes the Google
  Analytics script)
* `moz-extension://` scheme of other extensions
