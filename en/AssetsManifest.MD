# Assets Manifest

Nano Adblocker uses a
[different assets manifest](https://github.com/NanoAdblocker/NanoCore2/blob/master/src/assets.json).
Beside a few extra filter lists, some links and update period are also
modified.

Note that uBlock Resources file is loaded from a mirror in
[Nano Filters repository](https://github.com/NanoAdblocker/NanoFilters). This
means that upstream updates may not be immediately picked up by Nano Adblocker.
I believe this is necessary tradeoff as the resource library is very powerful,
and ensuring its integrity is more important than some minor inconvenience.
Nano Filters repository can only be modified by me, unlike
[uAssets repository](https://github.com/uBlockOrigin/uAssets) with 4 people
with write access, it is far more difficult to compromise Nano Filters
repository.
