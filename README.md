reaperf
=======

File reaper. Lists or consolidates duplicate files. Support for multiple matching strategies and directory recursion.


### Features

* Duplicate file detection via an identification strategy:
 * Hashing (MD5, SHA1)
 * Image fingerprinting
* Can list all duplicates within a hierarchy and consolidate them interactively or in automatic mode

### Usage

`reaperf [options] {strategy} {granularity} {discard-policy} directory`

### `strategy`

How files should be matched.

* `md5`
* `sha1`
* `img` Image files will be scaled down and a Hamming distance comparison will be made. If the scaling factor would result in an image smaller than 4px in any dimension, the image is scaled to that size. This strategy is heuristic, and it is recommended to run in interactive mode to confirm duplicates when operating on important pictures.

### `granularity`

Granularity, in addition to the strategy, defines what hierarchical structure constitutes a duplicate.

* `global` Keep only the first file between duplicates, throughout the hierarchy; discard the others.
* `dir` Discard only files which are duplicates at the same hierarchy position.

### `discard-policy`

* `delete` Delete the file.
* `rename` Append an extension to files determined to be duplicates, increasing numerically. (.001, .002, etc.)

### Options

* `-h {x}` *Hamming distance tolerance*: If the strategy uses a hamming distance to compare files, the tolerance value is set to `x`. The default tolerance is TODO.
* `-s {x}` *Scale factor*: If the strategy uses a scale factor, the scale factor will be set to `x`. The default scaling factor is 256.
* `-i` *Interactive mode*: If specified, duplicates will be displayed side-by-side and a user will be able to choose which action to take.
