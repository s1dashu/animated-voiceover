---
name: animated-voiceover
description: Develop AI-generated educational animated voiceover videos about philosophy, psychology, history, economics, finance, and technology. Use when Codex needs to research or structure a topic, write narration, divide a 1–5 minute video into balanced Seedance clips, design image or multi-shot video prompts, maintain narrator voice consistency, create text-forward cover images, or plan CLI-based multimodal generation and assembly. The currently maintained execution path uses LibTV CLI, while the production method can be adapted to Higgsfield, Jimeng, and comparable multimodal CLIs after consulting their latest official documentation.
---

# Animated Voiceover

## End-to-End Workflow

1. **Write the complete narration first.** Confirm the topic, audience, and final runtime. Finish the full script before dividing it into clips. Read [Narration Script Guide](references/narration-script-guide.md) in full before writing or revising narration.
2. **Lock the visual style and reference images.** Reuse a user-approved style reference or generate a new one and obtain approval. Build a cast list from the complete storyboard, then create separate reference images for every main character and important supporting character.
3. **Write prompts for every clip.** Finalize each narration segment before designing reference responsibilities, shots, actions, and cuts. Read [Video Prompt Guide](references/video-prompt-guide.md) in full before writing, revising, or troubleshooting prompts.
4. **Generate only Clip 1 first.** If the user has not supplied an approved voice reference, do not attach an audio reference to Clip 1. Describe only the required voice characteristics in the prompt. Inspect its narration, voice, style, characters, and effective aspect ratio before approving it as the anchor for later clips.
5. **Extract audio from Clip 1.** On the maintained LibTV path, download the approved Clip 1 through LibTV CLI, then read and follow [Audio Extraction and Conversion Guide](references/audio-extraction-guide.md) for the current operating system. Use `afconvert` or FFmpeg on macOS and FFmpeg on Windows or Linux. Produce a 48 kHz, stereo, 16-bit PCM WAV and upload it through LibTV CLI as a separate audio node. M4A was previously rejected by Seedance and must not be used until revalidated.
6. **Generate the remaining clips in parallel.** Starting with Clip 2, attach the pure audio extracted from Clip 1 as `Audio 1` on every video node and use it only as a voice reference. The exact narration for each clip must still come only from that clip's prompt. Verify all upstream assets, prompts, and generation parameters before submitting the remaining clips in parallel.
7. **Quality-check and assemble the final video.** Inspect narration completeness, voice consistency, character identity, visible shot motion, effective framing, and end-of-clip audio. Assemble only clips that pass review.

## Narration Structure

Finish the complete narration before splitting it into video clips. The argument, story, and emotional progression must work at the full-script level; never damage the overall logic merely to hit a per-clip character target.

Read [references/narration-script-guide.md](references/narration-script-guide.md) in full before writing or revising narration. It defines audience calibration, context, 15-second segmentation, the 60-Han-character counting convention, runtime-based structure, spoken style, fact-checking, visual relationships, and the default delivery format.

## Clip Segmentation

Prefer Seedance 2.0 Pro for video generation. Apply these production rules:

1. Set each video clip to 15 seconds.
2. Target 60 spoken Chinese Han characters per clip. Prefer 59–61 and relax to 58–62 only when required for natural, complete meaning. Count only spoken Han characters, not punctuation, shot directions, reference descriptions, voice notes, or constraints.
3. Estimate the clip count from the full narration, then redistribute and rewrite sentences so clip lengths remain balanced.
4. Split at complete ideas and natural transitions. Rewrite the narration when the count is wrong; never cut sentences mechanically.
5. Verify every segment with Unicode Han-character counting and review information density. Keep segment lengths even enough to avoid noticeable speaking-rate changes.
6. Use a natural, steady narration pace with short, clear pauses. Do not stack clauses or sacrifice clarity to reach a number.

The 60-character target is a production preference validated through real generations, not an official Seedance limit. Proper nouns, numbers, English terms, and difficult pronunciations may require a small deviation and rebalancing elsewhere.

## Visual Language and Image Prompts

Prepare one user-approved visual-style reference before generating production clips. Use it to lock linework, materials, color, lighting, and rendering style without automatically copying its subject, composition, text, or story.

Let the user reuse an approved historical style reference or create a new one with the configured generation tool. Do not switch style references silently between clips.

When an image is responsible only for visual style, write only: `Use Image 1 only as the visual-style reference.` Do not restate its materials, palette, lighting, or linework, and do not repeat style requirements at the end of the prompt. Keep the detailed style description in the reference-asset record and let the image carry the constraint.

### Character References and Whole-Video Style Consistency

Before production generation, build a cast list from the complete narration and storyboard. Separate main characters, important supporting characters, and extras:

1. Create and obtain approval for a separate character reference image for every recurring or narratively important identifiable character. Do not let an important character first appear through text-only improvisation inside a video node.
2. Maintain a character-to-reference-to-clip table. Attach every required character reference to each relevant clip and state precisely which image controls identity and which controls style.
3. Stop production generation if any main or important supporting character lacks an approved reference. Do not substitute a similar character, vague description, or another person's reference.
4. Extras and one-off background characters may omit identity references, but they must inherit the same visual medium, design language, materials, proportions, linework, palette, and lighting from a specified character or style reference.
5. Do not mix incompatible character-rendering systems in one video. If main characters are stylized 3D animation, extras must not drift into photorealistic humans or flat 2D illustration.
6. State whether each character reference controls identity, style, or both. Prevent the model from applying one referenced face or outfit to other characters.

## Reusable Reference Assets

Treat approved voice and style references as reusable assets:

1. At the start of a video, inspect existing approved voice and style references and let the user reuse or replace them. Use an existing voice reference only to generate Clip 1; otherwise describe the required voice in Clip 1's prompt.
2. After Clip 1 passes review, always extract its pure audio and use that approved audio to unify every later clip.
3. Record a stable identifier, type, purpose, description, complete generation prompt, source LibTV workspace/canvas/node, local download path, and approval state for every approved reference.
4. Reuse a node directly only within the same canvas. For cross-canvas reuse, download through LibTV CLI, upload to the target canvas, and attach the new resource node.
5. Never connect nodes across canvases, construct private LibTV HTTP requests, or regenerate an existing reference through a personal API key.
6. Create and reapprove a new version when changing a reference. Never overwrite or silently replace an approved asset.

## Video Prompts

Plan visuals only after the narration has been segmented. Read [references/video-prompt-guide.md](references/video-prompt-guide.md) in full before writing, revising, or troubleshooting Seedance prompts.

Keep these core rules:

1. Use `Clip N` only for display and task management. Remove it before model submission.
2. Pass `duration`, `ratio`, `resolution`, `enableSound`, `count`, and `modeType` only as CLI parameters, never inside the creative prompt.
3. A 15-second clip normally uses five shots. Adjust only for a genuinely slower long action or a tighter montage. Give every shot a clear start, visible change, and end; after a cut, advance to new information instead of restarting a completed action or camera move.
4. Remove visual ambiguity. Specify subject, facing direction, frame position, shot size, camera geometry, light direction, moving body part, motion amplitude, and speed. Convert abstract concepts and emotions into visible objects, actions, or body details.
5. Add a shared spatial-continuity description only when several shots revisit the same identifiable space and continuity matters. Independent scenes, parallel examples, symbolic images, and cross-time montages should define their own spaces.
6. Treat five shots as five distinct visual events, normally with one principal action result per shot. Do not pack several mandatory outcomes into one shot.
7. Describe camera geometry explicitly: position, height, direction, and what appears on the left, center, and right. Carry forward a completed state only when adjacent shots intentionally divide one continuous action.
8. When a style image controls style only, write `Use Image 1 only as the visual-style reference.` Never mislabel it as a first frame, last frame, or composition to reproduce.
9. Use approved identity references for every main and important supporting character. Explicitly make unreferenced extras inherit the overall design system without copying a referenced person's identity.
10. Include only negative constraints explicitly required by the user or project. Do not automatically add no-subtitles, no-logo, no-watermark, no-background-music, or no-lip-sync requirements.
11. Use an existing voice reference for Clip 1 when one is provided. Otherwise generate Clip 1 first and extract its audio. Attach that pure audio to every later clip as `Audio 1`, or use the target platform's equivalent voice-identity mechanism. The exact narration must come only from the text inside `{}` in the current prompt.

## Voice Reference

Use an existing voice reference only to generate Clip 1. If none exists, generate Clip 1 from an explicit voice description. In both cases, extract pure audio from the approved final Clip 1 and use it as the voice anchor for all later clips:

1. If an approved voice reference exists, attach it only to Clip 1. Otherwise attach no audio reference and describe the required voice characteristics in the prompt. Generate only Clip 1 first.
2. Inspect narration completeness, voice identity, volume, speaking rate, and end-of-clip noise. Establish an anchor only after the voice passes review.
3. Download Clip 1 through LibTV CLI, read [Audio Extraction and Conversion Guide](references/audio-extraction-guide.md) in full, convert it to 48 kHz stereo 16-bit PCM WAV, and upload it through LibTV CLI as a separate audio node. This format passed Seedance 2.0 validation; M4A was rejected and must not be used until revalidated.
4. Starting with Clip 2, attach the pure audio as `Audio 1` to every later clip, or use one consistent voice ID on another platform. Verify assets, prompts, and parameters before submitting later clips in parallel.
5. State only that the audio controls voice identity, plus any necessary user-approved voice characteristics. The exact narration must come only from the current text inside `{}`. Never repeat or borrow the sample's original wording or meaning.
6. Attach only pure audio for later clips. Do not use the whole video as a voice reference because video references cost more and may contaminate visual output.
7. When combining audio and image references, use a live-schema-supported mode such as `mixed2video`. The Seedance 2.0 VIP (`star-video2`) schema observed on 2026-07-30 supported both; query the schema again before production.
8. Connect an approved audio node directly only within the same canvas. Across canvases, download and re-upload through LibTV CLI, then use the new resource node as `Audio 1`.
9. Set sound parameters from the current audio strategy and live schema. If Seedance generates narration and sound directly, explicitly keep `enableSound=on`.
10. Create and approve a new asset record when changing voice. Never switch the selected source silently.

## Video Covers

Read [references/video-cover-image-guide.md](references/video-cover-image-guide.md) in full before generating, modifying, comparing, or reviewing a cover. It defines cover briefs, character references, extra styling, direct text rendering, fair multi-model comparison, LibTV parameters, downloads, records, and quality checks.

Reuse the approved character and style assets. Do not generate a cover with an unapproved main character. Inspect every rendered glyph in a text-forward cover; task success does not prove textual or identity accuracy.

## Media-Generation Portability and Support

LibTV CLI is the only image, audio, and video execution path currently maintained and validated by this skill. Formal support means the skill includes tested command habits, model-name mapping, task traceability, asset-node handling, and output checks. It does not mean the creative method is inherently limited to LibTV.

The production method is platform-independent: complete narration, clip segmentation, spoken-length control, reference responsibilities, character consistency, multi-shot direction, framing, voice consistency, output review, and final assembly can work with Higgsfield CLI, Jimeng CLI, or another multimodal CLI. Changing platforms changes installation, authentication, model discovery, parameter names, uploads, polling, downloads, and assembly—not the creative or quality standards unless the model's real capabilities require adaptation.

When only another platform CLI is available:

1. Find and read the platform's latest official CLI documentation. Never infer commands by translating LibTV syntax.
2. Confirm installation and authentication. Query the live model catalog, schema, input modes, asset limits and formats, clip duration, aspect ratio, resolution, sound controls, asynchronous task behavior, download flow, and assembly options.
3. Map this skill's asset responsibilities and generation steps to the target CLI while retaining task IDs, failure states, stderr, or equivalent logs.
4. Keep platform-specific commands, model names, and parameter maps in separate references. Never mix LibTV, Higgsfield, Jimeng, or other provider syntax.
5. Stop clearly when current official documentation, authentication, or required model capability is missing. Never invent commands or switch platforms silently.

Current CLI documentation entry points:

- [Higgsfield official CLI repository and guide](https://github.com/higgsfield-ai/cli). Check its [latest release](https://github.com/higgsfield-ai/cli/releases/latest) and live model list before use.
- [Jimeng CLI usage guide](https://bytedance.larkoffice.com/wiki/FVTwwm0bGiishxkKOoScdHR2nsg). Access may require the relevant Lark account.

The currently validated rhythm splits a 1–5 minute final video into 15-second clips, with about 60 spoken Chinese Han characters and normally five shots per clip. Seedance 2.5 Pro supports clips up to 30 seconds, but this skill has not systematically validated narration length, shot count, action density, continuity, audio stability, or cross-clip strategy at 30 seconds. Do not double 15-second rules mechanically or make 30 seconds the default before real tests confirm them.

## LibTV Generation and Assembly

Read [references/libtv/model-name-map.md](references/libtv/model-name-map.md) in full before resolving user model names, LibTV `modelName`, or `modelKey`. Pass the mapped LibTV `modelName` to `libtv node ... -s model=...`, not `modelKey`; still treat live search and schema as authoritative.

Keep provider-specific references separated. LibTV documentation belongs under `references/libtv/`; add separate directories for Higgsfield, Jimeng, or other CLIs only after practical validation.

Query video models and schema live through LibTV CLI. Prefer Seedance 2.0 Pro, currently mapped to Seedance 2.0 VIP (`star-video2`). The validated default clip duration is `duration=15`; read `ratio`, `resolution`, and `enableSound` from the active requirements. Pass every required value explicitly when creating or regenerating a node. Never inherit a canvas value, cloned-node setting, or model default. Resolve model labels, `modeType`, sound controls, resolution, ratio, and asset limits from the live schema.

Pass duration, aspect ratio, resolution, sound, output count, and input mode only as CLI parameters, not in the creative prompt. Let task logs remain the traceable single source of truth for actual technical settings.

After resolving the target canvas UUID, pass `-p <projectUuid>` explicitly to production create, generate, upload, download, and assembly commands. Verify the returned canvas UUID, node ID, and task ID.

Follow the active tool and media policy for every image, video, reference, generation, and assembly operation. Stop and report a policy conflict instead of choosing silently.

## Quality Control

Before generation, apply the preflight checklist in [references/video-prompt-guide.md](references/video-prompt-guide.md). After generation, use its post-generation checks for narration, voice identity, effective full-frame coverage, shot motion, repeated actions, visual style, and end-of-clip audio.

Do not validate aspect ratio from `ratio`, resolution, or container metadata alone. The model may place letterboxing or pillarboxing inside a technically correct container. Inspect representative frames at the beginning, middle, and end. Mark a clip as failed and regenerate it if its container or effective image does not match the target ratio, if black bars appear, or if content is shrunk into a mismatched container.

When Clip 1 had no existing voice reference, confirm that its voice was approved as the anchor. Starting with Clip 2, verify that every clip actually attaches that `Audio 1` or equivalent voice identity and matches the anchor.

Inspect every main character against the approved identity reference and confirm that extras share the same design and rendering system. Regenerate identity drift, swapped faces, or extras rendered in a visibly different medium.

## Output Format

Return draft scripts, narration, storyboards, and Seedance prompts as normal conversational paragraphs:

1. Use the default review layout from `references/narration-script-guide.md`: clip heading, character count, and narration on separate lines.
2. When showing several prompts, use clear external `Clip N` headings and blank lines. `Shot N` belongs inside the prompt. Remove external clip headings before model submission.
3. Do not place creative scripts or prompts inside fenced `text`, `plaintext`, or language-specific code blocks.
4. Do not create Markdown files merely to deliver a draft. Save project content only when the user explicitly requests it or confirms it as final.
5. Technical commands, JSON, and parameter examples may use code blocks when necessary.

## Authoritative References

Before writing or troubleshooting Seedance 2.0 prompts, read [references/video-prompt-guide.md](references/video-prompt-guide.md) and then [references/official-seedance-2.0-prompt-guide.md](references/official-seedance-2.0-prompt-guide.md) in full. The latter is an English source index and operational digest for the official Seedance documentation, including multimodal references, subject definition, shot sequencing, motion, camera, audio, text, extension, common failures, and examples.

For multi-shot direction or repeated camera moves and actions, also read [references/community-directing-notes.md](references/community-directing-notes.md). It records traceable community sources and explicitly separates adopted practices from rejected ones.

When searching official material, prioritize these concepts:

- basic formula, multimodal reference, video editing, video extension
- subject definition, shot sequence, action detail, camera movement
- special-character rules, inaccurate voice reference, identity drift, style drift
- extension versus segmented assembly, end noise, pronunciation

Treat live LibTV schema as authoritative for model parameters and capabilities, official Seedance material as authoritative for prompt behavior, and this skill's validated production experience as authoritative for the 60-Han-character target, natural delivery, five-shot rhythm, and visible state changes.
