# `sticky-scroll-mode`

Sticky scroll mode is a minor mode to enable sticky scrolling in any buffer, language agnostic.
If you'd prefer not to have a live sticky scroll window, and would rather have a temporary popup, you can use
`sticky-scroll-popup` to briefly show the outer, offscreen context.

## Example
<img width="834" alt="Screenshot 2024-08-10 at 10 26 02 PM" src="https://github.com/user-attachments/assets/b1606e65-3127-45f9-8904-e860d2df802c">

## Approach 

Uses an indentation approach, to find offscreen lines that are levels of indentation lower than the current point.

This works surprising well and quickly.

### Sticky scroll window

The package exposes the `sticky-scroll--max-window-height` which can be thought of as "the max number of outer contexts shown". If
the sticky scroll buffer has more lines than `sticky-scroll--max-window-height`, only the last `sticky-scroll--max-window-height` are shown.
Otherwise, the sticky window shows all lines.

## Known bugs

The live sticky window is tempermental. Closing the buffer with the live window successfully closes the sticky window and cleans up resources, as does disabling `sticky-scroll-toggle`.
However, changing buffers is super finnicky and I don't recommend it (for now). I am quickly working on a release to manage that better.
