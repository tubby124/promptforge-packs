# promptforge-packs

Live style pack JSON for the [PromptForge](https://github.com/tubby124/promptforge) Chrome extension.

The extension fetches `v1.json` from GitHub Pages on a 6-hour refresh cycle (and on browser start). To push an update — edit, commit, push. Users get it within 6 hours, or instantly via Settings → "Refresh now".

## Files

- `v1.json` — the live pack. Schema lives in [PromptForge/packs/default-pack.json](https://github.com/tubby124/promptforge/blob/main/packs/default-pack.json) (bundled fallback).

## Adding a new image style

Edit the `image_styles` object in `v1.json`:

```json
"my-style-name": {
  "composition": "...",
  "camera": "...",
  "lighting": "...",
  "color": "...",
  "mood": "...",
  "style": "...",
  "quality": "..."
}
```

Commit + push. Done.

## Adding a new site adapter

The extension uses pack-supplied selectors to inject prompts into LLM sites. To fix DOM drift on (e.g.) ChatGPT without shipping a code release:

```json
"site_adapters": {
  "chatgpt.com": {
    "textareaSelectors": ["#prompt-textarea"],
    "editableSelectors": ["#prompt-textarea[contenteditable]"]
  }
}
```

## Adding a role template

`role_library` entries become picks in the profile editor template dropdown:

```json
"role_library": {
  "your-role-key": "Description sentence. Used as the voice cue when the user picks this template."
}
```

## Hosting

GitHub Pages serves this from `https://tubby124.github.io/promptforge-packs/v1.json`. The extension defaults to that URL; users can point at their own fork via Settings.
