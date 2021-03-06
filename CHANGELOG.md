# Change Log
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/) and
and [human-readable changelog](http://keepachangelog.com/).

## [1.2.0] - 2019-04-04
The I can see clearly now release.

### Added
 - Visible images can now be extracted with `getVisImages`.

### Changed
 - Documentation now hosted at https://stuart-cls.github.io/python-opusfc-dist/

### Removed
 - Python 2.7, 3.4 builds

### Fixed
 - 3D-TRS (time-resolved) files without "Z Axis Label" parameter can now be loaded.
 - Loading issue for some processed 3D-IMAGE files.

## [1.1.2] - 2018-10-10

### Added
 - Python 3.7 builds

### Fixed
 - Fix annotated map reading for files generated by Opus 6.5

## [1.1.1] - 2018-03-21

### Fixed
 - Fix datablock list generation for extra-large 3D Image files
   *NOTE:* This filetype cannot be opened in 32-bit Windows builds
 - 3D-MAP multiregion arbitrary map files (`MultiRegionDataReturn`) which contain
   point groups where the points are arbitrary locations (not a grid or a linescan)
   are now properly loaded
   - Multiregion: handle non-standard point group ordering
   - Multiregion: handle annotations for files with multiple visible images

## [1.1.0] - 2017-03-01
The 3D blocks that aren't hyperspectral cubes release.

### Added
 - Support for 3D-MAP multiregion arbitrary map files
 - Support for 3D-TRS Time-resolved spectra files

### Changed
 - Object returned by `.getOpusData` is now a DataReturn class specific to that
   data type. This allows consumers to easily determine data structure using
   `type(dataObject)` instead of guessing. Object structure for previously
   supported files remains the same, so should be backwards compatible.

### Fixed
 - `TRARI` blocks are no longer mis-identified as `TRC` blocks by `.listContents`

## [1.0.0b1] - 2016-09-08
First pypi.org release.

### Added
 - Basic test suite
 - Docstrings
 - Sphinx based documentation
 - `.paramDict` provides natural-language translation of three-letter parameter
   codes. Not inclusive of all possible codes.

### Changed
 - `.getOpusData` now takes a tuple(DataBlockType, Dimensions, Derivative) as
   the second argument.
 - `.listContents` returns a list of datablock tuples
 - 3D TRC data is now return as a 3D numpy array under `.traces` with the structure
   `.traces[row][column][trace]` where trace corresponds to the `.labels` index
   of the trace. Individual trace maps can be accessed as `.traces[:,:,trace]`

### Fixed
 - Properly terminate parameter strings

## [1.0.0a3] - 2016-08-15
The "I heard you like parameters" release
### Added
 - This change log (CHANGELOG.md)
 - `.parameters` now returns Acquisition, Instrument, Sample and FT parameters
   in addition to the existing Data parameters

### Changed
 - Parameters are now returned in `.parameters` instead of `.paramList`
 - Support editable enumerated string parameter type

### Fixed
 - `.parameters`/`.paramList` strings are now unicode literals

## [1.0.0a1] - 2016-05-10
Released to limited audience as win32-py3.4 and linux64-py3.4 binary wheels.
### Added
 - Python 3 support:
  - all binary literals are `bytes`
  - cython reads source .pyx file in language_level=3
 - test.py tests 3D example file
 - profile.py profiles using onion map2.0 file

### Changed
 - Python 2 has been futurized to maintain a single 2/3 codebase
 - `_readFloats` replaced with numpy.fromfile
 - Add metadata to `setup.py`

### Deprecated
 - Python 2 support will likely be ignored in the future (No Python 2 consumers)
