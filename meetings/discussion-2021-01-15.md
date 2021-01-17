<table>
<tr>
    <th>Date and time</th>
    <td>2021-01-15T15:00Z</td>
</tr>
<tr>
    <th>Topic</th>
    <td>Continued discussion about a new shared application registration format and organization policies for Toltec</td>
</tr>
<tr>
    <th>Next Meeting</th>
    <td>2021-01-28T15:00Z</td>
</tr>
</table>

# Participants

## In Attendance

| Name                                               | Information                                                  |
| :------------------------------------------------- | ------------------------------------------------------------ |
| [@dixonary](https://github.com/dixonary)           | [Draft](https://github.com/dixonary/draft-reMarkable) launcher and .draft format author |
| [@Eeems](https://github.com/Eeems)                 | [Oxide](https://github.com/Eeems/oxide) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |
| [@LinusCDE](https://github.com/LinusCDE)           | [Toltec](https://github.com/toltec-dev/toltec) maintainer    |
| [@matteodelabre](https://github.com/matteodelabre) | [Toltec](https://github.com/toltec-dev/toltec) maintainer    |
| [@raisjn](https://github.com/raisjn)               | [remux](https://rmkit.dev/apps/remux) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |

## Regrets

No regrets.

# Standing Items

- Determine Next meeting date
    - January 28 @ 3 PM UTC
    - Allow for smaller meetings in the meantime
    - Wait until the meeting w/ everyone to make decisions
- Confirm meeting notes from previous meeting
    - Ensure that PR for meeting notes has been approved and merged
- Determine Toltec release date
    - Important issues: device-incompatible packages, code of conduct & security
    - Target date: February 15
- Call for new Business
    - Code of conduct
        - Interaction with the user community
        - This repo will probably go under the Toltec umbrella
    - Clarify standardization policy

# Old Business

- Select format for files
    - JSON, YAML, TOML, etc
    - XDG Desktop File
        - Good support in Qt (not tested yet)
        - Support in Rust: library available
        - Support in Python: configparser
        - Translating Draft v1 to XDG Desktop is low-effort
        - No support for the complex data types
        - Can we define a reMarkable-specific Type= value?
            - Avoid conflict with future extensions of the XDG format
        - Make local changes to the standard
            - Don’t break parsers
    - Draft v2
        - Draft v1 is a strict subset of XDG Desktop
        - Not strictly compatible with XDG at the moment (missing header)?
- Supported program locations
    - Wait until a format is selected

# New Business

- Should we have a Code of Conduct?
    - Enforced by committee
    - Create a common repo for the code of conduct (see below)
- Move the repository under Toltec org
    - Avoid representing the Toltec org as the only rM community effort
    - Bring representatives from the reHackable org
    - Rename reMarkable-appfile → organization
    - Add documents in that repo (code of conduct, …)
    - Also see <https://github.com/nixos>
    - Avoid over-structuring?
        - Allow for changes to the policies
        - Find the right balance
    - Move issues from toltec-dev/toltec
- Standard name
    - [@LinusCDE](https://github.com/LinusCDE): Ask people for opinions about this for the next meeting
    - Ask in the #matrix channel
    - No name needed if we go with the XDG Desktop format?

# Decision log

| Description             | Decision               |
| ----------------------- | ---------------------- |
| Choose a code of conduct | Use the [_Contributor Covenant Code of Conduct_](https://www.contributor-covenant.org/version/1/4/code-of-conduct/) |
| Move the repository under the Toltec org and rename it to `organization` | Everyone agrees |
