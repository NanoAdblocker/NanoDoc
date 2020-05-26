# Filter Syntax Differences

Nano Adblocker has
[extra resources](https://github.com/NanoAdblocker/NanoCore2/blob/master/src/snippets.js),
and when a filter references one of those resources, it will not work as
intended in uBlock Origin out of the box. You can, however, load these extra
resources to uBlock Origin in advanced settings to make those filters work.

To combat extra stubborn websites, Nano Adblocker also has a few privileged
resources. These resources, which start with `nanop-`, are very powerful
so only privileged filters are allowed to use them. For security reasons,
they will not work in uBlock Origin.

If you are a filter lists maintainer and want to have access to these
privileged resources, please let us know by opening an issue
[here](https://github.com/NanoAdblocker/NanoCore/issues).

Beside extra resources, Nano Adblocker also handles some options differently.

## Convenience Options

Nano Adblocker and uBlock Origin will map options as follows for convenience:
```
   1p -> first-party
   3p -> third-party
  css -> stylesheet
  doc -> document
ehide -> elemhide
frame -> subdocument
ghide -> generichide
shide -> specifichide
  xhr -> xmlhttprequest
```

Additionally, Nano Adblocker will map `iframe` to `subdocument`. uBlock Origin
will discard filters that use the `iframe` option.

## The option `fetch`

Nano Adblocker does not differentiate between `fetch` and `xmlhttprequest`
requests and does not recognize `fetch` as an option. `fetch` requests
are mapped to `xmlhttprequest` by
[Edgyfy](https://github.com/jspenguin2017/Edgyfy). uBlock Origin on Edge
differentiates between `fetch` and `xmlhttprequest` but does not recognize
`fetch` as an option.

If you are a filter lists maintainer and this difference is causing problems
for you, please let us know by opening an issue
[here](https://github.com/NanoAdblocker/NanoCore/issues).

## The Filters Editor

Nano Editor is powered by Ace, and most
[shortcut keys](https://github.com/ajaxorg/ace/wiki/Default-Keyboard-Shortcuts)
are the same.
