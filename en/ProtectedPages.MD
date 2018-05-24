# Protected Pages

Every browser has some pages that are protected from extensions. Requests from
these pages are not blockable and cosmetic filtering will not work on these
pages.

If you do not like the default new tab, you have to replace it with something
else, Nano Adblocker and uBlock Origin cannot make small changes to it (except
for Chrome and Chromium where part of it can be blocked using network filters).

## Chrome and Chromium

Note that apps can protect additional pages when installed.

Fully protected:
* `about:` scheme
* `chrome://` scheme
* `chrome-extension://` scheme of other extensions
* `chrome.google.com` (extension store) except YouTube embeds

Partially protected:
* The default new tab page, only network requests can be filtered

## Edge

Fully protected:
* `about:` scheme
* The default new tab page
* `ms-browser-extension://` scheme

## Firefox

Fully protected:
* `about:` scheme
* For the following protected pages, network requests are sometimes visible to
  extensions, but cannot be filtered or redirected since directives from
  extensions are ignored (this includes the Google Analytics script for the
  extension store):
  * `accounts-static.cdn.mozilla.net`
  * `accounts.firefox.com`
  * `addons.cdn.mozilla.net`
  * `addons.mozilla.org` (extension store)
  * `api.accounts.firefox.com`
  * `content.cdn.mozilla.net`
  * `discovery.addons.mozilla.org`
  * `input.mozilla.org`
  * `install.mozilla.org`
  * `oauth.accounts.firefox.com`
  * `profile.accounts.firefox.com`
  * `support.mozilla.org`
  * `sync.services.mozilla.com`
  * `testpilot.firefox.com`
* The default new tab page
* `moz-extension://` scheme of other extensions
