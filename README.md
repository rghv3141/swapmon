Swapmon
=======

Overview
--------
Swapmon is a shell script that dynamically adds and removes swap space
based on system usage. It is designed for FreeBSD but can likely be
adapted easily for other BSD variants.

The script monitors swap usage and automatically manages swap files
according to configurable low and high watermark thresholds.

Features
--------
- Dynamic addition and removal of swap space
- Configurable low and high watermark thresholds (percentage-based)
- Automatic cleanup of previously created swap files
- Notification via cron when swap space is adjusted
- rc.d and daemon mode support

Limitations
-----------
Swapmon can only react when it is executed, typically once or twice per
minute. As a result, the system may still run out of swap space if usage
spikes faster than the execution interval.

Installation
------------
Place the script in a suitable location, for example:

    /usr/local/sbin/swapmon

Make it executable:

    chmod +x /usr/local/sbin/swapmon

You may either:
- Add a symlink to swapmon in `/usr/local/etc/rc.d`, or
- Run it via cron.

Usage
-----
Run once per minute using cron:

    * * * * * /usr/local/sbin/swapmon

To run twice per minute without daemon mode:

    * * * * * sleep 30 && /usr/local/sbin/swapmon

Configuration
-------------
Low and high watermark thresholds are configurable within the script.
When the high watermark is reached, additional swap space is added.
When usage falls below the low watermark, previously added swap space
is removed.

Version
-------
Current version: 1.5  
Release date: June 26, 2012

Distribution:
- swapmon-1.5.tbz (7,660 bytes)
- SHA1: 3768e3d10d22d8fa8324b35dd75b1e29643285c4

TODO
----
- Find a better trigger mechanism than periodic execution

Changelog
---------
1.5 (Jun 26, 2012)
- Clean up leftover swap files on startup
- Create minimal swap file if no swap is configured

1.4 (Aug 4, 2010)
- Split startup script and main script
- Introduced test run instead of enforcing UID == 0
- Reduced duplicate code
- Port accepted

1.3 (Aug 4, 2010)
- Implemented rc.subr integration
- Added standard start/stop/restart/status commands
- Removed distfile

1.2 (Jul 23, 2010)
- Added daemon mode and startup script support
- Wrote manpage
- Submitted port

1.1 (May 2, 2010)
- Replaced awk and bc calls with shell substitutions
- Added version to notifications

1.0 (May 1, 2010)
- Initial release




This repository is an unofficial VCS mirror created to support FreeBSD port>
Original BSD-2-Clause license by Alexander Kuehn (2010) is preserved.
