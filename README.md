<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# ⏫ Promote Draft Release

Promotes a draft GitHub release to a full release.

## draft-release-promote-action

## Usage Example

<!-- markdownlint-disable MD046 -->

```yaml
steps:
  - name: "Promote Draft Release"
    uses: lfreleng-actions/draft-release-promote-action@main
    with:
      TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

<!-- markdownlint-enable MD046 -->

## Token Permissions

The token needs the following permissions:

`contents: write`

## Inputs

<!-- markdownlint-disable MD013 -->

| Variable Name | Required | Description                            |
| ------------- | -------- | -------------------------------------- |
| TOKEN         | True     | GitHub token with relevant permissions |
| TAG           | False    | Tag of draft release to promote        |
| NAME          | False    | Name of draft release to promote       |
| SORT_BY       | False    | Sort by this json element parameter    |
| SORT_REVERSE  | False    | Reverse the sort order of results      |

<!-- markdownlint-enable MD013 -->

## Implementation Details

Uses the GitHub CLI command:

`gh release list --json name,tagName,createdAt,isDraft`

Example output:

```json
[
  {
    "createdAt": "2025-04-16T04:37:36Z",
    "isDraft": true,
    "name": "Draft release v0.1.1",
    "tagName": "v0.1.1"
  },
  {
    "createdAt": "2025-04-16T04:32:37Z",
    "isDraft": true,
    "name": "Draft release v0.1.0",
    "tagName": "v0.1.0"
  },
  {
    "createdAt": "2025-04-16T04:18:11Z",
    "isDraft": false,
    "name": "Release v0.0.1",
    "tagName": "v0.0.1"
  }
]
```

This is then passed through the JQ command:

`jq` # Placeholder

## Notes
