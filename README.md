# multipool_setup

Installation files for [Multi-Pool-Installer](https://github.com/myGIGlife-claude/Multi-Pool-Installer).

#### These files do nothing on their own. Please go to https://github.com/myGIGlife-claude/Multi-Pool-Installer

Supported operating systems: Ubuntu 22.04, 24.04 and 26.04 LTS (x86_64).

How the pieces fit:
1. **Multi-Pool-Installer:** its bootstrap script clones this repo.
2. **multipool_setup:** creates the multipool user, writes `/etc/multipool.conf` and shows the menu.
3. The menu hands off to [multipool_yiimp_single](https://github.com/myGIGlife-claude/multipool_yiimp_single) or [multipool_yiimp_multi](https://github.com/myGIGlife-claude/multipool_yiimp_multi).
4. Those install [YiiMP](https://github.com/myGIGlife-claude/yiimp).

## Install-time overrides

These environment variables can be set before running `multipool`:

| Variable | Default | Purpose |
|:--|:--|:--|
| `PHP_VERSION` | `8.3` | PHP version installed from `ppa:ondrej/php` (only used on first install; stored in `/etc/multipool.conf`) |
| `MULTIPOOL_GITHUB` | `https://github.com/myGIGlife-claude` | Where the YiiMP installers are cloned from (for forks) |
| `YIIMP_SINGLE_REF` / `YIIMP_MULTI_REF` | `master` | Branch or tag of the YiiMP single/multi installers |
| `MULTIPOOL_SKIP_OS_CHECK` | unset | Set to `1` to try an unsupported OS release |

The YiiMP Stratum Upgrade, NOMP and Daemon Builder options still install the
last releases of the original cryptopool-builders repositories, which have not
been updated for current Ubuntu releases. They are marked "legacy" in the menu.
