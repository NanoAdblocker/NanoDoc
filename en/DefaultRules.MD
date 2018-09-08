# Default Dynamic Filtering Rules

When installed, uBlock Origin comes with these dynamic filtering rules:

```
no-large-media: behind-the-scene false
no-scripting: behind-the-scene false
behind-the-scene * * noop
behind-the-scene * 1p-script noop
behind-the-scene * 3p noop
behind-the-scene * 3p-frame noop
behind-the-scene * 3p-script noop
behind-the-scene * image noop
behind-the-scene * inline-script noop
```

Nano Adblocker has `no-csp-reports: * true` along with rules above.
