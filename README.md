# CommonProjectFiles
Contains a set of file configurations, that are common for the BetonQuest development environment

## Howto setup
By setting up the following GitHub Action, the common files will be synced to the repository.
This will be done by creating a PR with the changes.

Suggested name: `.github/workflows/sync-common-files.yml`

```yaml
name: Sync Common Files

on:
  schedule:
    - cron: '0 0 * * *' # Runs nightly
  workflow_dispatch:

jobs:
  sync-files:
    runs-on: ubuntu-latest

    steps:
      - name: Sync Common Files
        uses: BetonQuest/CommonFileSync@main
```
