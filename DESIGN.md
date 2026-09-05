# DESIGN.md
<!-- verified: 2026-09-05 -->

Quarters tokens. Every value lives in the `:root` block at the top of `index.html`; there is no build step and no other stylesheet. Change a token there first, then here.

## Ground and neutrals (dark CRT)
| Token | Value | Use |
|---|---|---|
| `--bg` | #03040a | page ground, boot overlay |
| `--screen` | #070a16 | the cabinet face, dialogs |
| `--panel` | #0b0f20 | collapsibles, tiles, inputs, buttons |
| `--line` | #1c2240 | borders, table rules, dotted row dividers |
| `--dim` | #55608c | secondary text, notes, footers |
| `--unlit` | #2a3050 | off pips, the footer hint |

Cabinet bezel: 10px solid #11142a with a 2px #232849 outline, radius 22px. Scanlines and a vignette are overlaid on the cabinet with pseudo-elements.

## Accents
| Token | Value | Use |
|---|---|---|
| `--green` | #3aff6e | body text, live rows, `h1`, heatmap top step |
| `--cyan` | #29d8ff | labels, summaries, table headers, GitHub pip |
| `--magenta` | #ff3fd4 | "in play" groups, vault pip, bonus button |
| `--yellow` | #ffd23f | section titles, focus ring, coin button, local pip, rank 1 |
| `--red` | #ff4560 | dead projects, "game over" groups, warning tiles |

Glow: accents carry a `text-shadow` or `box-shadow` of the same color at 0.35 to 0.65 alpha. Heatmap steps: #101731 (empty), #123f24, #1a7a3c, #28c058, #3aff6e.

## Type
| Token | Stack | Use |
|---|---|---|
| `--px` | 'Press Start 2P', monospace | headings, labels, buttons, pips; sizes 0.38rem to 0.72rem, `h1` clamp(1.05rem, 3.4vw, 1.7rem), tile values 1.02rem |
| `--term` | 'VT323', 'Courier New', monospace | body, rows, tables, dialogs; 1.02rem to 1.35rem |

Both fonts are inlined as base64 `@font-face` with `font-display: swap`. Pixel text uses letter-spacing 0.06em to 0.2em; terminal text 0.02em to 0.05em.

## Layout rules
- Cabinet and power bar: `max-width: 960px`, centered; body padding 2.5rem 1rem 3.5rem; cabinet padding 2.6rem 2.2rem 2.8rem.
- Sections are 2.6rem apart. Roster is a two-column grid (2.2rem gap); cabinet lists are two CSS columns; stat tiles are a three-column grid (0.9rem gap).
- Breakpoints: 700px collapses roster, lists, and topbar to one column and tiles to two; 460px takes tiles to one.
- Dialogs: `max-width: min(92vw, 640px)`, game dialog min(94vw, 700px); tables and the heatmap scroll inside `overflow-x: auto` wrappers, min table width 560px.
- Focus ring: 2px solid `--yellow`, 2px offset. `prefers-reduced-motion` disables the power-off transition and every blink.
