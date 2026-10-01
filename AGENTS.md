# Markdown Viewer guidance

This browser-extension fork renders Markdown with configurable parsers, themes and optional rich content. Read [README](README.md), [Firefox notes](firefox.md), and the target browser manifest before editing.

Follow the affected surface through `background/`, `content/`, `options/` and `popup/`. Keep browser-specific behavior in the existing manifest/build paths. Preserve extension permissions, origin access controls and script execution boundaries; do not broaden host permissions to make a test pass. Untrusted Markdown, embedded HTML, remote resources and optional diagrams require explicit security review.

## Build and verification

From a disposable checkout, the documented entry points are `sh build/package.sh chrome` and `sh build/package.sh firefox`. The script removes/recreates `themes/` and `vendor/`, replaces root `manifest.json`, builds dependencies and produces `markdown-viewer.zip`. Do not use it over unrelated local changes or mistake generated assets for canonical edits.

Load the resulting unpacked extension in an isolated browser profile using README instructions. Exercise the changed parser/theme/options behavior, local files and permitted remote origins; include denied-origin and malformed-content cases when relevant. Chrome and Firefox package layouts differ, so validate the affected browser rather than assuming one package proves both.

No automated CI or test gate was found in the inspected tree. Report package creation separately from actual extension loading and rendering. Publishing store/release assets is a separate authorized action. Keep browser history, captured document content and credentials out of fixtures and logs; preserve upstream licensing and attribution.
