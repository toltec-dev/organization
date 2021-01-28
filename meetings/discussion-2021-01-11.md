<table>
<tr>
    <th>Date and time</th>
    <td>2021-01-11T15:00Z</td>
</tr>
<tr>
    <th>Topic</th>
    <td>Initial discussion about a new shared application registration format</td>
</tr>
<tr>
    <th>Next Meeting</th>
    <td>2021-01-15T15:00Z</td>
</tr>
</table>

## Participants

* [@dixonary](https://github.com/dixonary) ([Draft](https://github.com/dixonary/draft-reMarkable) launcher and .draft format author).
* [@Eeems](https://github.com/Eeems) ([Oxide](https://github.com/Eeems/oxide) author).
* [@LinusCDE](https://github.com/LinusCDE) ([Toltec](https://github.com/toltec-dev/toltec) maintainer).
* [@matteodelabre](https://github.com/matteodelabre) ([Toltec](https://github.com/toltec-dev/toltec) maintainer).
* [@raisjn](https://github.com/raisjn) ([remux](https://rmkit.dev/apps/remux) author).

## Summary

We had a high-level discussion about a new application file format. The .draft format is no longer suitable for the more advanced behaviour that we would want to support.

It would be ideal to have a new format ASAP.

## Background

- .draft: first format, key-value store

```
key=value
```

Q: is this sufficient? Does it need upgrades or replacement, etc?

.draft parser is bad in the original implementation (crashes on unexpected keys)

JSON is hard to parse, relative to other formats like .draft.

Q: will we need .draft and .oxide (or whatever) files forever?

## Goals

- Minimise difficulty with interoperability
- Easy to read, easy to write
- Hard to break (in the way that json is easy to break!)
- Open-ended and extensible
- Minimise the number of required fields

## Ideal specification language features

- Key-value storage, like .draft already has [minimum required]
- Nested storage
- Arrays, or a way of representing multiple values mapped to the same key
- Namespacing for the sake of launcher-specific options

## Paths to a new format

1. Construct an entirely new format; officially deprecate .draft and provide an upgrade path for old .draft files to be replaced by new files
2. Expand .draft in a backwards-compatible way
3. Create a shell-accessible binary file or interoperable (C?) library which parses whatever format

## Name?

* .draft format is the old name and (obviously) draft-specific
* .oxide is the oxide format currently
* linux uses .desktop

* .inklet 

* .rmapp has support pending any better suggestions.

* leave this question open to the community - do you have a better name?

## Potential Solutions

### JSON / YAML

- forward-compatible
- easily parsed with existing library tools
- first party support for arrays, nested data

### .draft v2

- can be formalised quickly
- may be less readable than yaml
- requires zero effort from users who do not wish to upgrade their launcher


## Additional nice things

- An interactive program which queries for values and outputs a complete application specification
- A list-applications binary (or similar) which can output all found applications in all known locations

### Supported program locations

Current
- `/etc/draft`
- `/opt/etc/draft`
- `$HOME/.config/draft`
- `/opt/usr/share/applications`

New
- `/usr/share/applications`
- `$HOME/.local/share/applications`

## Decision process

* The future standard should be unanimously approved by all current launcher devs (i.e. [@Eeems](https://github.com/Eeems), [@dixonary](https://github.com/dixonary), and [@raisjn](https://github.com/raisjn)).
* Other parties also can share their proposals and opinions on the standard.
