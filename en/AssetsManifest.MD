# Assets Manifest

Nano Adblocker uses a
[different assets manifest](https://github.com/NanoAdblocker/NanoCore2/blob/master/src/assets.json).
Beside a few extra filter lists being added, some links and update period are
also modified.

One important difference is that Nano Adblocker will load uBlock Resources file
from
[a mirror](https://raw.githubusercontent.com/NanoAdblocker/NanoFilters/master/NanoMirror/uBlockResources.txt)
in NanoFilters repository. This means that upstream updates in uAssets
repository may not be immediately picked up by Nano Adblocker. I believe this
is a necessary tradeoff as the resource library is very powerful, and ensuring
its integrity is more important than the minor inconvenience that delayed
updates can cause. I do check uAssets repository regularly, so the mirror will
probably be only 1 or 2 days behind.

NanoFilters repository can only be modified by me, unlike uAssets repository
where 4 people have write access, it is far more difficult to compromise
NanoFilters repository. Nano Adblocker will still load uBlock Filters from
uAssets repository as filter lists can only cause very limited damage.
