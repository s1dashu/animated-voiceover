# Animated Voiceover Cover Image Guide

## Navigation

- Cover brief
- Character and style references
- Composition and text
- LibTV generation
- Downloading and records
- Quality control

## Scope

Use this guide to generate, revise, compare, and review text-forward covers, thumbnails, title cards, and poster-like key art for animated voiceover videos. Cover creation is one stage of `animated-voiceover`, not a separate skill.

Before any cover operation, read the active project's tool and media policy. Reuse its approved characters, visual styles, and reference assets. LibTV CLI is the currently maintained cover-generation path. When a project specifies another platform, follow the portability rules in the main skill and read that platform's latest official documentation first.

## Cover Brief

Lock these decisions before writing a prompt:

1. Exact title and optional subtitle copy.
2. The user-required aspect ratio and placement context; do not inherit the video's ratio automatically.
3. One visual proposition that represents the episode.
4. Approved main-character reference nodes and the responsibility of each one.
5. A separate style reference, unless a character reference explicitly controls both identity and style.
6. The model or models to use and whether their outputs will be compared under the same brief.

For a multi-model comparison, keep the copy, references, layout hierarchy, symbols, and core art direction constant. Change only model parameters required by each live schema.

## Character and Style References

- Use an approved identity reference for every main character on the cover. If one is missing, create and approve it before generating the cover.
- State whether each image controls character identity, overall style, or both.
- Preserve face, age, hairstyle, clothing, and recognizable silhouette. Do not apply one character reference to another character.
- Extras without identity references must inherit the specified character or style reference's medium, design language, materials, proportions, palette, and lighting without copying a referenced person's face or clothes.
- Do not mix incompatible systems such as photorealistic people, stylized 3D animation, and hand-drawn illustration on one cover.

## Composition and Thumbnail Legibility

Prefer only:

1. One dominant character, face, or symbol.
2. One title area with an unmistakable reading order.
3. One supporting symbol directly tied to the video's central idea.
4. Clear foreground/background separation and safe margins.

The character must remain recognizable at phone-thumbnail size. Reserve an uncluttered text area and keep the title away from faces and critical symbols. Unless requested, avoid collages, multiple frames, and several competing focal points.

## Direct Text Rendering

When the selected model supports text rendering, include the exact copy in the image prompt and define:

- Exact text on every line.
- Main-title and subtitle hierarchy.
- Position, size, alignment, color, contrast, and safe margins.
- A legible type direction appropriate to the copy's language.

Include this constraint:

> Only the following specified text may appear in the image: [list the exact copy line by line]. Do not add any other letters, words, numbers, punctuation, logos, or watermarks.

Do not rewrite the title or add hooks, episode numbers, quotations, or translations. Compare the generated text character by character. Reject misspellings, variants, omissions, repetitions, reordering, deformation, and gibberish even when the result looks approximately correct.

## Prompt Order

1. Reference-image responsibilities and identity features that must remain stable.
2. Cover purpose, subject placement, and visual hierarchy.
3. Background, symbols, color, lighting, and spatial depth.
4. Exact line-by-line copy and typographic hierarchy.
5. The prohibition on extra text and any other composition constraints.

Put creative composition in the prompt. Pass `ratio`, resolution, quality, output count, and `modeType` only through LibTV parameters.

## LibTV Generation

Before production:

1. Confirm that `libtv` is installed and authenticated and that the current directory is bound to the correct workspace and canvas.
2. Resolve the target canvas UUID and pass `-p <projectUuid>` explicitly to production commands.
3. Read [libtv/model-name-map.md](libtv/model-name-map.md) in full to resolve the user's model name.
4. Run `libtv model search --type image ...` and `libtv model <modelName|modelKey>`. Treat the live schema as authoritative.
5. Confirm that every reference node belongs to the target canvas.

Common mappings:

| Common name | LibTV `modelName` |
| --- | --- |
| GPT Image 2 | `Lib Image` |
| Nano Banana Pro | `General image Pro` |
| Seedream 5.0 Pro | `Seedream 5.0 Pro` |

These mappings are only a snapshot. Update `libtv/model-name-map.md` when live results change.

When attaching any image reference, pass `modeType=image2image` explicitly. LibTV rejects nodes that have image inputs but remain in `text2image` mode.

Use a unique node name for every model and version. Attach approved references with `--left`. Default to `count=1` unless the user requests several candidates. Use `--run` to wait for the terminal state instead of adding an external polling loop.

## Downloads and Traceability

Download completed nodes with `libtv download` and pass the target canvas UUID explicitly. Put same-round outputs from several models in one comparison directory. Include the subject, model, text status, and version in each filename.

Retain:

- Canvas UUID.
- Node name, node key, and task ID.
- Terminal state, model display name, and model key.
- Actual parameters and complete prompt.
- Local path and actual dimensions.

Do not claim completion when a task succeeds but the node has no asset URL.

## Quality Control

Inspect every cover at full size and phone-thumbnail size. Revise the prompt and regenerate through LibTV if any of these failures appear:

- Wrong ratio or dimensions, borders, black bars, inherited reference-image frames, or an accidental collage.
- Missing, wrong, repeated, deformed, reordered, or obscured title characters, or any extra text, logo, or watermark.
- A main character diverges from the approved reference, or characters exchange faces or clothes.
- Extras use a different medium, design language, or rendering system from the main character.
- The title is illegible at thumbnail size, has weak contrast, or crosses safe margins.
- Character, title, and symbol lack a clear hierarchy.

Do not hide textual or identity failures with local patchwork unless the user explicitly requests local post-production.

## Delivery

Show each selected model's result and link the comparison directory. Briefly report exact-copy accuracy, character and style consistency, dimensions, and the most important composition difference between models. Record a cover as an approved asset only after the user explicitly selects it.
