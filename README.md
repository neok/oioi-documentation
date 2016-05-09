![OIOI Logo](https://www.plugsurfing.com/assets/img/icons/ps-oioi-logo-small.png)
# OIOI Documentation
Documentation for the OIOI interface to connect to the PlugSurfing service.

Please see http://docs.plugsurfing.com for a readable version.

Please see http://docs.plugsurfing.com for a readable version.

## Theme
When cloning, use the `--recursive` flag.
The theme is included as a git submodule.

To update the theme, use `git submodule update --remote`.

## Building HTML
Change into `docs` and run `make html`.
Sphinx writes the resulting files into the `_build` directory.

## Requirements
- python 2.7
- Sphinx
- sphinx-autobuild

Run `pip install Sphinx sphinx-autobuild`, if you have pip installed.
