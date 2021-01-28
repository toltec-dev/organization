<table>
<tr>
    <th>Date and time</th>
    <td>2021-01-28T15:00Z</td>
</tr>
<tr>
    <th>Topic</th>
    <td>Review of proposals for the standard application registration format</td>
</tr>
<tr>
    <th>Next Meeting</th>
    <td>?</td>
</tr>
</table>


# Participants

## In Attendance

| Name                                               | Information                                                  |
| :------------------------------------------------- | ------------------------------------------------------------ |
| [@Eeems](https://github.com/Eeems)                 | [Oxide](https://github.com/Eeems/oxide) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |
| [@LinusCDE](https://github.com/LinusCDE)           | [Toltec](https://github.com/toltec-dev/toltec) maintainer    |
| [@matteodelabre](https://github.com/matteodelabre) | [Toltec](https://github.com/toltec-dev/toltec) maintainer    |
| [@raisjn](https://github.com/raisjn)               | [remux](https://rmkit.dev/apps/remux) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |
| [@danshick](https://github.com/danshick)           | [Toltec](https://github.com/toltec-dev/toltec) contributor   |

## Regrets

| Name                                               | Information                                                                             |
| -------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [@dixonary](https://github.com/dixonary)           | [Draft](https://github.com/dixonary/draft-reMarkable) launcher and .draft format author |

# Standing Items

- Determine next meeting date
    - To be determined offline
- Confirm meeting notes from previous meeting
    - OK
- Determine if Toltec target release date should be moved
    - Important issues: device-incompatible packages, code of conduct & security
        - Architecture separation: WIP
            - Should be done by the end of the week
        - Security waiting on dixonary’s review
        - Privacy policy
            - Don’t log anything until we get this sorted out?
            - GDPR does not apply to IP addresses?
            - See <https://eeems.website/privacy-policy/> for an example
    - Target date: February 15
- Call for new business

# Old Business

- Select format for files & supported program locations
    - Is Oxide blocked by the app format standard decision?
        - Eeems will continue with the existing .oxide format in the meantime
    - danshick wants to keep the standard XDG format
        - Why a new standard?
            - reMarkable-specific events (pause, resume)
                - Does that belong to the app format?
                - Note: Draft only supports the stop event
    - We can’t enumerate all fields that will be needed in the future
        - Decide on what could get standardized in the future
        - Make it extensible (like XDG)
    - Is having the environment setup in the app file a good solution?
        - Bash scripts will always be needed
        - It allows users to directly launch the app
    - Program locations
        - Draft is in [/opt]/etc/draft
        - Oxide is in /opt/usr/share/applications/*.oxide
    - Schedule another meeting to talk about this again

# New Business

- Increasing the bus factor
    - Grant some/all maintainers the admin role in the org
    - okeh: Not needed
    - LinusCDE: Keep a core admin team
    - danshick: Rotate admins
        - Eeems: Maybe not worthy since we have a small team
    - Eeems: Have at least another admin
        - Only use their admin right if Matteo can’t be contacted for a set amount of time
        - On another continent?
            - Maybe not needed
    - Actually there are other items needed to increase the bus factor
        - Access to the production server
        - Access to the DNS zone
        - Matteo will inform others before moving
        - _Decision postponed to a later meeting_
- Review standard proposals
    - _Postponed to a later meeting_
- Criterion for sign off on testing branch PRs
    - _Postponed to a later meeting_
- Stable Merge Process
    - If a package holds up merge, what do we do with it?
    - Set a timeframe after which we leave out the bad packages
    - Current timeframe:
        - PR opens on Saturday
        - Should be merged by Monday
        - Take into account that we have limited free time/all of us are contributing on our free time

# Decision log

| Description                | Decision               |
| -------------------------- | ---------------------- |
| Keep release date          | Everyone agrees        |
