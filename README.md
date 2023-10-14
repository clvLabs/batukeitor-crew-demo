# Batukeitor scores: demo

This is an example of how [Batukeitor](https://github.com/clvLabs/batukeitor) scores are written and serves as a sample score demo pack for the app.

## The `index.yml` file
```yml
# Batukeitor crew file
name: Demo
scores:
  demo1: "Demo"
  teoria: "Teoría"
```

* All lines starting with `#` are interpreted as comments.
* The `name` field should be filled with the crew name.
* The `scores` list should contain, for each score we want published:
  * Its filename (without the `.yml` extension).
  * A description string (score long name).

Given the example above, score:
* `scores/demo1.yml` will be published as `Demo`.
* `scores/teoria.yml` will be published as `Teoría`.

## The `scores` folder
All score `yml` files should be placed under this folder.

Subfolders can be created

## The `Batukeitor yaml` score format

(see any of the `scores` folder `yml` files for an example)

### The `name` field
```yml
name: Demo 1
```
The _display name_ of the score, used in the user interface.

### The `bpm` field
```yml
bpm: 110
```
The initial/recommended `BPM` for the score.

### The `score` field
```yml
score:
  intro
  ---
  base1 base1 base1 c1
  base1 base1 base1 c3
  ---
  base2 base2 base2 c2
  base2 base2 base2 c3
  ---
  fin
```
The sequence of `sections` used to build the full score:

* Sections can be grouped to help with bar counts, etc.
* Groups can be separated with `---`

### The `sections` field
```yml
sections:

  intro:
    # (...section contents...)

  base1:
    # (...section contents...)

  #(...more sections...)
```
The list of available `sections` in the score.


### Individual `section`
3 different examples for 3 time signatures:
```yml
  b44:
    name: Base 4/4
    color: "#006000"
    tracks:
      #   "1---2---3---4---"
      DD: "                "
      AP: "                "
      CH: "X--XX--XX--XX--X"
      AG: "                "
      CC: "X --X --X --X - "
      CV: "                "
      TB: "    X  X X  X  X"
      RP: "    X  X X  X  X"
      CX: "----X--X-X--X--X"
      S3: "X     X       X "
      S2: "X  X  X   X     "
      S1: "X  X  X   X     "

  b24:
    name: Base 2/4
    color: "#00a0a0"
    timeSignature: 2/4
    tracks:
      #   "1---2---"
      DD: "        "
      AP: "        "
      CH: "X   X   "
      AG: "        "
      CC: "  XX  XX"
      CV: "        "
      TB: "X   X   "
      RP: "X   X   "
      CX: "X---X---"
      S3: "X   X   "
      S2: "X   X   "
      S1: "X   X   "

  b68:
    name: Base 6/8
    color: "#9d09ff"
    timeSignature: 6/8
    tracks:
      #   "1-----2-----"
      DD: "            "
      AP: "            "
      CH: "X     X     "
      AG: "            "
      CC: "  X X   X X "
      CV: "            "
      TB: "X     X     "
      RP: "X     X     "
      CX: "X - - X - - "
      S3: "X     X     "
      S2: "X     X     "
      S1: "X     X     "


  longintro:
    name: Long Intro
    color: "#c3a012"
    tracks:
      #   "1---2---3---4---1---2---3---4---1---2---3---4---1---2---3---4---1---2---3---4---1---2---3---4---1---2---3---4---"
      DD: "                                                                                                                "
      AP: "                                                                                                                "
      CH: "                                X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --X --"
      AG: "X - X - X- -X - X - X - X- -X - X - X - X- -X - X - X - X- -X - X - X - X- -X - X - X - X- -X - X - X - X- -X - "
      CC: "                                 X  X X  X  X X  X  X X  X  X X  X  X X  X  X X  X  X X  X  X X  X  X X  X  X X "
      CV: "                                                                                                                "
      TB: "                                                                                                                "
      RP: "                                                                                                X X X X  X X XXX"
      CX: "                                                                                                X X X X  X X XXX"
      S3: "                                                                                                X X X X  X X XXX"
      S2: "                                                                                                X X X X  X X XXX"
      S1: "                                                                                                X X X X  X X XXX"

```

* The `identificators` of the sections are `b44`, `b24`, `b68` and `longintro`.
  * These are the ones to be used in the `score` field.
* Each one of them has:
  * `name` with the _display name_.
  * `color` with the _display color_.
  * `timeSignature` with the time signature. Allowed values:
    * `2/4`
    * `3/4`
    * `4/4`
    * `6/8`
    * `9/8`
    * `12/8`
    * If not specified, `4/4` will be assumed.
  * `tracks` with the list of tracks.
    * A comment line is used to help putting notes in place.
    * Each `track` is identified by its `instrument id` (Please see the [instruments pack README](https://github.com/clvLabs/batukeitor-instruments/blob/master/README.md) for more details on instruments).
    * Each character (symbol) in a `track` represents an eighth note.
      * Where a space is found, no sound will be played.
      * Where a character is found, the corresponding `sample` for its `instrument` will be played.
    * Multiple barscan be joined, as in the `longintro` sample.


_Advice_: Sometimes while writing a `section`, it's useful to duplicate the _guide comment line_ for each `track`:
```yml
  b68x2:
    name: Base 6/8 (2bars)
    color: "#9d09ff"
    timeSignature: 6/8
    tracks:
      #   "1-----2-----1-----2-----"
      DD: "                        "
      #   "1-----2-----1-----2-----"
      AP: "                        "
      #   "1-----2-----1-----2-----"
      CH: "X     X     X     X     "
      #   "1-----2-----1-----2-----"
      AG: "                        "
      #   "1-----2-----1-----2-----"
      CC: "  X X   X X   X X   X X "
      #   "1-----2-----1-----2-----"
      CV: "                        "
      #   "1-----2-----1-----2-----"
      TB: "X     X     X     X     "
      #   "1-----2-----1-----2-----"
      RP: "X     X     X     X     "
      #   "1-----2-----1-----2-----"
      CX: "X - - X - - X - - X - - "
      #   "1-----2-----1-----2-----"
      S3: "X     X     X     X     "
      #   "1-----2-----1-----2-----"
      S2: "X     X     X     X     "
      #   "1-----2-----1-----2-----"
      S1: "X     X     X     X     "
```
