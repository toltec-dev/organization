<table>
<tr>
    <th>Date and time</th>
    <td>2021-02-18T15:00Z</td>
</tr>
<tr>
    <th>Topic</th>
    <td>Working group discussion on new application registration format for Toltec packages</td>
</tr>
</table>

# Participants

## In Attendance

| Name                                               | Information                                                  |
| :------------------------------------------------- | ------------------------------------------------------------ |
| [@dixonary](https://github.com/dixonary)           | [Draft](https://github.com/dixonary/draft-reMarkable) launcher and .draft format author |
| [@Eeems](https://github.com/Eeems)                 | [Oxide](https://github.com/Eeems/oxide) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |
| [@danshick](https://github.com/danshick)           | [Toltec](https://github.com/toltec-dev/toltec) contributor                                                   |

- Current proposals
    - XDG
    - Draft (extension)
    - Oxide
    - Eeems’ proposal
    - (YAML|TOML) + Schema

### JSON / YAML

Pros: 
* forward-compatible
* easily parsed with existing library tools
* first party support for arrays, nested data

### .draft v2

Pros: 
* can be formalised quickly
* may be less readable than yaml
* requires zero effort from users who do not wish to upgrade their launcher

### XDG .desktop

Pros:
* existing format
* can be customised

# Notes:

Conclusion: Let's run with XDG .desktop format, as it is a well supported, easily extensible format with wide use in similar roles already.

- We will need to support every format (in principle) for some amount of time.

- Each launcher may instigate their own transition procedure

- We will want a strict subset of XDG as our basis.

- `.desktop` cannot take a sequence of shell commands as input in the way that `.draft` can. So we will need to write shell scripts instead for some programs which currently run a sequence of operations in their `.draft` file.

### Timescale for introducing new format

TBD


### Minimum basis

```
[Desktop Entry]
Version=1.5 (optional)
Name= (`name` from draft)
Exec= (`call` from draft, changed as specified above)
Comment= (`desc` from draft, optional)
Type= (Application, Link or Directory - launchers need only support Application)
Icon= (absolute path, optional)

[X-ReMarkable]
OnStop= (follow same specification as exec, optional)
User= (specific user name for programs to run as, optional (default to root))
Group= (as with User, optional (default to root))
Environments= (specifies key-value pairs to be introduced to the environment of a running command, separated by semicolon, optional)
```

Expected behaviour if a required key is absent: Log an error, ignore the file.

