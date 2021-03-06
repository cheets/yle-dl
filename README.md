download videos from Yle servers

Copyright (C) 2010-2014 Antti Ajanki, antti.ajanki@iki.fi

License: GPLv2

Homepage: http://aajanki.github.com/yle-dl/index-en.html

Source code: https://github.com/aajanki/yle-dl

yle-dl is a tool for downloading media files from the video streaming
services of the Finnish national broadcasting company Yle: [Yle
Areena] and [Elävä Arkisto].

[Yle Areena]:http://areena.yle.fi/
[Elävä arkisto]:http://www.yle.fi/elavaarkisto/

Installation
------------

Install dependencies: rtmpdump (version 2.4 or newer), python (2.6 or
newer), pycrypto, AdobeHDS.php, php and the following php extensions:
bcmath, curl and SimpleXML.

On Debian `apt-get install rtmpdump python python-crypto php5-cli
php5-curl` satisfies the dependencies.

On OS X install rtmpdump with homebrew: `brew install --HEAD
rtmpdump` and pycrypto with pip: `pip install -r requirements.txt`

To install run:

```
make install-adobehds
make install
```

Instead of install-adobehds you can also manually download
https://raw.githubusercontent.com/K-S-V/Scripts/master/AdobeHDS.php
to /usr/local/share/yle-dl.

Starting from version 1.99.9 yle-dl doesn't anymore require a modified
rtmpdump or plugin. Instead, everything is now downloadable with the
plain rtmpdump. To remove the remnants of previous versions run "make
uninstall-old-rtmpdump".

Packages for various distros
----------------------------

See http://aajanki.github.com/yle-dl/index-en.html for a list of
available installation packages.

RPM packaging:

contrib/yle-dl.spec is a spec file for creating a RPM-package for
Fedora.

Usage
-----

```
yle-dl [yle-dl or rtmpdump options] URL
```

where URL is the address of the Areena or Elävä arkisto web page where
you would normally watch the video in a browser.

yle-dl options:

* `--latestepisode`   Download the latest episodes

* `--showurl`         Print librtmp-compatible URL, don't download

* `--showtitle`       Print stream title, don't download

* `--vfat`            Create Windows-compatible filenames

* `--sublang lang`    Download subtitles, lang = fin, swe, smi, none or all

* `--rtmpdump path`   Set path to rtmpdump binary

* `--adobehds cmd`    Set command for executing AdobeHDS.php script

* `--destdir dir`     Save files to dir

Type `rtmpdump --help` to see a full list of options.

Firewall must allow outgoing traffic on ports 80 and 1935.

Examples
--------

```
yle-dl http://areena.yle.fi/tv/1544491 -o video.flv
```

```
yle-dl "http://www.yle.fi/elavaarkisto/?s=s&g=4&ag=28&t=&a=9390"
```

Playing in mplayer (or vlc and others) without downloading first:

```
mplayer "$(yle-dl --showurl http://areena.yle.fi/tv/1544491)"
```
