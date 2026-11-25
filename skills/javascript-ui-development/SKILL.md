---
name: javascript-ui-development
description: Use when working on XIVA browser-side behavior, vanilla JavaScript, jQuery, AJAX, forms, tables, and UI interactions.
---

# JavaScript and UI Development

## Discover existing conventions
Inspect nearby HTML, JavaScript, CSS, asset loading, and plugin initialization. Determine whether the area uses vanilla JavaScript, jQuery, or an existing component/plugin before editing. Do not introduce React, Vue, TypeScript, a bundler, or another framework unless requested.

## Implementation
- Prefer readable vanilla JavaScript or the existing jQuery style.
- Use `const` by default and `let` when reassignment is needed.
- Avoid unnecessary global variables. Follow established namespace conventions if the project uses them.
- Bind events safely and avoid duplicate handlers when content is reloaded.
- Handle loading, success, empty, validation, and error states.
- Prevent double submission where appropriate, without hiding server-side idempotency requirements.
- Keep API request and response handling consistent with the existing contract.
- Do not trust client-side validation or client-provided role/permission values.
- Escape or safely render untrusted content. Avoid unsafe `innerHTML` / `.html()` with untrusted data.
- Preserve accessibility: labels, keyboard behavior, focus management, and meaningful status feedback.

## UI plugins
Before adding or changing a plugin, inspect its installed version and initialization pattern. Do not assume the latest API. Avoid loading duplicate copies or changing shared initialization for a local feature.

## Verification
Check browser console errors where tools allow, inspect network request/response behavior, test empty and error cases, and review responsive behavior if the change affects layout. Clearly distinguish static review from an executed browser test.
