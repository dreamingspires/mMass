# mMass3

This is the official repository for mMass3: [mMass](http://www.mmass.org) on Python3.
It is currently highly experimental - much of the UI remains broken amidst updating various dependencies.

For more information please see the official mMass homepage at [www.mmass.org](http://www.mmass.org).  Many thanks to Martin Strohalm for his hard work on the project over many years!

We are currently in pre-release mode.  Therefore, the software has not been packaged.  In the future, you can expect pre-built packages on PyPI.

## Building from source
### Linux
mMass3 uses [poetry](python-poetry.org/) as the build system.  To get started ensure poetry is [installed](https://python-poetry.org/docs/#installation), then clone the mMass3 repository.

Due to this [well-known issue](https://wxpython.org/blog/2017-08-17-builds-for-linux-with-pip/index.html), the wxPython toolkit must be compiled from scratch.  Poetry will handle this, but you require the build dependencies.

Ensure all the [dependencies for building wxPython](https://wxpython.org/blog/2017-08-17-builds-for-linux-with-pip/index.html) are installed on your system.  For Fedora GNU/Linux (32), this is currently:
```
python3
python3-devel
gtk3
gtk3-devel
gstreamer1
gstreamer1-devel
freeglut
freeglut-devel
libjpeg-turbo
libjpeg-turbo-devel
libpng
libpng-devel
libtiff
libtiff-devel
SDL
SDL-devel
libnotify
libnotify-devel
libSM
libSM-devel
```

From within the repository, install the dependencies into the _venv_ with:

`poetry install`

Don't be surprised if installing wxPython takes a long time: the entire UI toolkit is being compiled from source.

Run the software:

`poetry run mmass`

Build software packages with:

`poetry build`

Your packages will be built within the `dist/` directory.

### Windows
Microsoft Windows does not come with a C compiler built in.  Since mMass uses a Python extension module, written in C, to speed up certain calculations, we must first install Microsoft Visual C++ 14.0 (or newer).

Go to the [Visual Studio downloads page](https://visualstudio.microsoft.com/downloads/), and download Visual Studio 2019 (or newer) Community edition.  Run the installer.

You will be presented with a list of packages to install.  Under the `Workloads` tab, select `Desktop development with C++, and in the sidebar ensure that the MSVC option is selected.

You might also want to use this installed to install Python onto your machine, if you haven't already done so.

Ensure you have installed the [poetry build system](https://python-poetry.org/docs/#installation), clone the mMass3 repository.

From within the repository, install the dependencies into the _venv_ with:

`poetry install`

Run the software:

`poetry run mmass`

Build software packages with:

`poetry build`

Your packages will be built within the `dist/` directory.

## Packaging
### Windows

Ensure that `makensis` is installed:

```
choco install nsis.portable
```

Build the executable in `dist/`.  From the root directory of the repo:

```
poetry install
poetry run pyinstaller .\installer\windows.spec
```

Build the installer in `dist/`.  From the root directory of the repo:

```
makensis.exe /DPRODUCT_VERSION=0.1.0 installer\windows_installer.nsi
```

## Contributing

Issues can be file in the GitHub bug tracker.  PRs welcomed!

## Release procedure

* Update version in `pyproject.toml` and `gui/config.py`
* (Future) run unit tests
* Build installers (see below)
* Test installers
* Commit, tag, push
* Publish to PyPi with poetry publish
* Create a release on Github, including the changelog, source, and installers

## Disclaimer

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE.

For Research Use Only. Not for use in diagnostic procedures.

## License

This program and its documentation are Copyright 2005-2013 by Martin Strohalm, 2020 by Edd Salkield.

This program, along with all associated documentation, is free software;
you can redistribute it and/or modify it under the terms of the GNU General
Public License as published by the Free Software Foundation.
See the LICENSE.TXT file for details (and make sure that you have entirely
read and understood it!)

Please note in particular that, if you use this program, or ANY part of
it - even a single line of code - in another application, the resulting
application becomes also GPL. In other words, GPL is a "contaminating" license.

If you do not understand any portion of this notice, please seek appropriate
professional legal advice. If you do not or - for any reason - you can not
accept ALL of these conditions, then you must not use nor distribute this
program.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
(file LICENSE.TXT) for more details.

The origin of this software must not be misrepresented; you must not claim
that you wrote the original software. Altered source versions must be clearly
marked as such, and must not be misrepresented as being the original software.

This notice must not be removed or altered from any source distribution.
