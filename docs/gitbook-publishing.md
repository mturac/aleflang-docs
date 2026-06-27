# GitBook Publishing

This repo is ready to import into GitBook.

## Structure

```text
README.md
SUMMARY.md
docs/
  syntax.md
  tutorial-ticketdesk-ui.md
  tutorial-native-api.md
  tutorial-ai-native.md
```

GitBook uses:

- `README.md` as the landing page
- `SUMMARY.md` as navigation
- linked Markdown files as pages

## Import

1. Create a GitBook space.
2. Connect GitHub.
3. Select the `aleflang-docs` repository.
4. Keep the root directory as `/`.
5. Publish from the GitBook UI.

## Publishing Rule

Every new page must be linked from `SUMMARY.md`, otherwise it can exist in the
repo without appearing in the GitBook navigation.

