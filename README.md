# Batukeitor scores: demo

This is an example of how `Batukeitor` scores are written and serves as a sample score demo pack for the app.

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
