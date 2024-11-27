# CommonProjectFiles
Contains a set of file configurations, that are common for the BetonQuest development environment

## Howto setup
By setting up the following GitHub Action, the common files will be synced to the repository.
This will be done by creating a PR with the changes.

Suggested name: `.github/workflows/sync_common_files.yml`

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
        uses: BetonQuest/CommonProjectFiles@main
```

You can also run the action with the following arguments:

```yaml
        with:
          source-repo: https://github.com/BetonQuest/CommonProjectFiles
          ignored-files: mvnw,mvnw.cmd
          include-default-ignored-files: .github/workflows/editorconfig.yml
          token: ${{ secrets.ACCESS_TOKEN }}
```

Especially the `token` is important,
if you want that the created PR can trigger `on: push` or `on: pull_request` workflows,
or if you want to edit workflows.
