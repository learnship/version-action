# GitHub Action: Extract Short SHA and Create Label

This GitHub Action extracts the short SHA from the HEAD of your Git repository and creates a label with the format `sha-<short_sha>`.

## Usage

### 1. Add the Action to your workflow

```yaml
name: Your workflow

on:
  push:
    branches:
      - main  # Replace with your branch name

jobs:
  labeler:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Extract Short SHA and Label
        id: version
        uses: learnship/version-action@main

      - name: Use the outputs
        run: |
          echo "Short SHA: ${{ steps.version.outputs.short_sha }}"
          echo "Label: ${{ steps.version.outputs.label }}"
