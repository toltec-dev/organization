<table>
<tr>
    <th>Date and time</th>
    <td>2021-02-12T15:00Z</td>
</tr>
<tr>
    <th>Topic</th>
    <td>Review of proposals for the standard application registration format</td>
</tr>
<tr>
    <th>Next Meeting</th>
    <td>2021-02-26T15:00Z<td>
</tr>
</table>


# Participants

## In Attendance

| Name                                               | Information                                                                                                  |
| :------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| [@Eeems](https://github.com/Eeems)                 | [Oxide](https://github.com/Eeems/oxide) author and [Toltec](https://github.com/toltec-dev/toltec) maintainer |
| [@LinusCDE](https://github.com/LinusCDE)           | [Toltec](https://github.com/toltec-dev/toltec) maintainer                                                    |
| [@matteodelabre](https://github.com/matteodelabre) | [Toltec](https://github.com/toltec-dev/toltec) maintainer                                                    |
| [@raisjn](https://github.com/raisjn)               | [Toltec](https://github.com/toltec-dev/toltec) maintainer   |
| [@dixonary](https://github.com/dixonary)           | [Draft](https://github.com/dixonary/draft-reMarkable) launcher and .draft format author                      |
| [@danshick](https://github.com/danshick)           | [Toltec](https://github.com/toltec-dev/toltec) contributor                                                   |

## Regrets

No regrets.

# Standing Items

- Determine next meeting date: 2021-02-26T15:00Z
- Confirm meeting notes from previous meeting: OK
- Determine if Toltec target release date should be moved
    - Current target date: February 15 (Monday)
        - This target will most probably not be met
        - Defer decision of a new target date until next meeting
    - We want to have good support for reMarkable 2 before announcing
        - We don’t want to have to deal with too many support requests
        - Prevent installation of incompatible packages on reMarkable 1
    - Display support for reMarkable 2
        - Make packages that use the display depend on a display package
        - Split the display package so that
            - On reMarkable 1 it does nothing
            - On reMarkable 2 it installs rm2fb
        - In the future, display could become a metapackage provided by several implementations
    - Pending pull requests/changes
        - <https://github.com/toltec-dev/toltec/pull/274>
        - <https://github.com/toltec-dev/toltec/tree/tooling/split-architectures>
    - Sort out how to do incremental updates without needing to re-run the bootstrap script
        - How to notify users for manual intervention?
            - Hook into `opkg` to show messages from maintainers
                - Needs a wrapper script or opkg patch
            - Central webpage for messages

# Old Business

- Schedule meeting to select format for files & supported program locations
    - Current proposals
        - XDG
        - Draft (extension)
        - Oxide
        - Eeems’ proposal
        - (YAML|TOML) + Schema
    - Participants
        - [@dixonary](https://github.com/dixonary)
        - [@Eeems](https://github.com/Eeems)
        - [@danshick](https://github.com/danshick)
        - [@raisjn](https://github.com/raisjn)
    - Date: **To be determined later today**
- Criterion for sign off on testing branch PRs
    - What’s the _testing/stable_ model?
        - What level of QA?
    - Reduce redundant work for stable merges
    - Criteria for merging to _testing_
        - Must pass the CI checks
        - Must run on the device
        - Have a test plan:
            - Stating what the author has tested
            - Asking for extra testing from the reviewer
        - Add a pull request template for this
            - Note: Multiple templates are supported in GitHub
            - [@LinusCDE](https://github.com/LinusCDE) will create the template
    - Must update <https://github.com/toltec-dev/toltec/blob/stable/docs/branches.md>
- Increasing the bus factor
    - Nothing to add
    - Final decision should be part of the standard operating procedure
        - Especially re. the notification to maintainers if Mattéo moves

# New Business

- Adding new members
    - Core team: Repository maintainers
        - Ability to approve and merge new packages
    - Collaborators: Package maintainers
        - Approval from Git file owner?
    - Decide on the process for adding members to the core team
        - Currently based on a graph of trust
        - Recommendation process from one existing member
        - Give enough time for everyone to think about it
        - Part of the standard operating procedure
    - Add [@danshick](https://github.com/danshick) to the core team
    - Make a document to have a log of core team members
    - A PR will be opened for both creating the members list and adding [@danshick](https://github.com/danshick)
- Enable discussions for Toltec
    - Will be done by [@matteodelabre](https://github.com/matteodelabre)

# Decision log

| Description                | Decision               |
| -------------------------- | ---------------------- |
| Use a PR-based process for adding new members | Everyone agrees |
