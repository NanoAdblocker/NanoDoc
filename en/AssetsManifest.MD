# Assets Manifest

Nano Adblocker uses a
[different assets manifest](https://github.com/NanoAdblocker/NanoCore2/blob/master/src/assets.json).
Beside a few extra filter lists being added, some links and update period are
also modified.

Nano Adblocker will also load uBlock Resources file from a mirror in
[Nano Filters repository](https://github.com/NanoAdblocker/NanoFilters). This
means that upstream updates may not be immediately picked up by Nano Adblocker.
I believe this is necessary tradeoff as the resource library is very powerful,
and ensuring its integrity is more important than some minor inconvenience.
Nano Filters repository can only be modified by me, unlike
[uAssets repository](https://github.com/uBlockOrigin/uAssets) where 4 people
have write access, it is far more difficult to compromise Nano Filters
repository. Nano Adblocker will still load uBlock Filters from uAssets
repository as filter lists can only cause very limited damage.
