# YouTube Shorts Blocker

**35 lines of code. That's it.**

A brutally minimal browser extension that hides YouTube Shorts everywhere.

## Why This Extension?

- **35 lines of code** - You can read and verify everything in 30 seconds
- **22 CSS rules** - Maximum efficiency, minimal footprint
- **Zero complexity** - No settings, no UI, no bloat
- **Completely secure** - No permissions beyond YouTube, no external connections

## Installation

### Chrome / Edge / Brave

1. Download this repository
2. Go to `chrome://extensions/`
3. Enable Developer mode → Load unpacked
4. Done

### Firefox

1. Download this repository
2. Go to `about:debugging#/runtime/this-firefox`
3. Load Temporary Add-on → Select manifest.json
4. Done

## What It Does

Hides Shorts navigation tabs, shelves, and videos across all YouTube pages.

## Security & Privacy

This is the entire extension - 35 lines of actual code:

```javascript
function hide() {
    document
        .querySelectorAll(
            `
        ytd-guide-entry-renderer a[title="Shorts"],
        ytd-mini-guide-entry-renderer a[title="Shorts"],
        ytm-pivot-bar-item-renderer a[href="/shorts"],
        ytd-reel-shelf-renderer,
        ytd-rich-shelf-renderer:has([href*="/shorts/"]),
        ytm-reel-shelf-renderer,
        ytm-rich-section-renderer:has([href^="/shorts/"]),
        grid-shelf-view-model:has([href^="/shorts/"]),
        ytd-rich-grid-group:has([href^="/shorts/"]),
        [href^="/shorts/"],
        ytd-reel-item-renderer,
        ytm-reel-item-renderer,
        ytm-shorts-lockup-view-model,
        ytd-rich-item-renderer:has([href^="/shorts/"]),
        ytd-video-renderer:has([href^="/shorts/"]),
        ytd-grid-video-renderer:has([href^="/shorts/"]),
        ytd-compact-video-renderer:has([href^="/shorts/"]),
        ytm-rich-item-renderer:has([href^="/shorts/"]),
        ytm-video-with-context-renderer:has([href^="/shorts/"]),
        ytm-grid-video-renderer:has([href^="/shorts/"]),
        ytd-notification-renderer:has([href^="/shorts/"])`
        )
        .forEach((el) => (el.style.display = 'none'));
}

hide();
new MutationObserver(hide).observe(document.body || document.documentElement, {
    childList: true,
    subtree: true,
});
```

**That's it. No tracking. No data collection. No external servers.**

## License

Copyright 2025 TN3W

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
