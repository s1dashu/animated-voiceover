# Animated Voiceover Video Prompt Guide

## Navigation

- Inputs and fixed prompt order
- Voice references
- Reference-asset responsibilities
- Shot design and continuity
- Full-frame composition and aspect-ratio review
- Content that does not belong in the prompt
- Conversational delivery format
- Preflight and post-generation checks

## Scope

Use this guide to convert an approved 15-second narration segment into a Seedance 2.0 animated voiceover prompt. The goal is to make reference responsibilities, narration, visible action, and shot progression unambiguous while preserving voice and visual consistency across clips.

Use [official-seedance-2.0-prompt-guide.md](official-seedance-2.0-prompt-guide.md) as the official-source index and operational digest. Use [community-directing-notes.md](community-directing-notes.md) only as a supplement for directing practice. Resolve model parameters, input modes, and asset limits from the live LibTV schema.

## Inputs

Confirm all of the following before writing a prompt:

1. The final narration for the current clip and its spoken Han-character count.
2. For Clip 1, whether the user provided an approved voice reference. For later clips, whether the pure audio extracted from Clip 1 is attached as `Audio 1`, or whether the target platform's equivalent voice identity is configured.
3. Which approved visual-style reference to use and whether it controls style only.
4. Whether the full-video cast list is complete and every main or important supporting character in the current clip has an approved identity reference.
5. Whether the character-to-reference-to-clip table is complete and the node has every reference actually required by this clip.
6. The clip's single knowledge, emotional, or narrative task.
7. Which visible actions will translate the abstract narration into images.

Do not revise narration while storyboarding. Finalize the narration first; shots must not compensate for missing facts.

## Fixed Prompt Order

Build every clip as an independent, complete prompt in this order:

1. The current audio's voice-reference responsibility; omit when no audio reference exists.
2. The responsibility of every reference image.
3. Narration language, voice source, delivery, and the exact text for this clip.
4. Necessary global visual requirements.
5. Shots in event order.

Standard structure:

```markdown
Use Audio 1 only as the reference for {approved voice characteristics}.

Use Image 1 only as the visual-style reference.

Use off-screen narration in Chinese, with the voice identity from Audio 1 and {approved speaking rate and delivery}. Speak the following text completely, exactly, and in order: {exact narration for this clip}. {approved sound and music constraints}

Shot 1:
[shot size or camera geometry + subject + setting + starting state -> visible change -> end state + one principal camera move]

Shot 2:
[shot size or camera geometry + subject + setting + starting state -> visible change -> end state + one principal camera move]

Shot 3:
[shot size or camera geometry + subject + setting + starting state -> visible change -> end state + one principal camera move]
```

A 15-second clip normally extends the structure to Shot 5. Adjust for the material instead of fixing the count at three. Include narration once, inside `{}`. Shot paragraphs describe visuals only and must not repeat narration.

When Clip 1 has no approved voice reference, omit the `Audio 1` line and directly specify only the voice characteristics the user requires. Starting with Clip 2, use the approved pure audio extracted from Clip 1.

## Voice Reference

- When the user supplies an approved voice reference, use it to generate Clip 1. Otherwise generate Clip 1 from a voice description. In both cases, extract pure audio after Clip 1 passes review.
- Starting with Clip 2, attach the same Clip 1 audio as `Audio 1` to every later clip, or use one equivalent voice ID on the target platform.
- The exact text for the current clip comes only from the narration inside `{}`. Never repeat or borrow the reference sample's original words or meaning.
- Unless the user explicitly changes the voice, do not regenerate the sample, switch to another candidate, or substitute a video clip for the pure-audio reference.

## Reference-Asset Responsibilities

### Audio as a Voice Reference

- Starting with Clip 2, attach the same approved pure audio extracted from Clip 1 and ensure the prompt refers to it as `Audio 1`.
- State that `Audio 1` controls voice identity only. Add only necessary voice traits already approved by the user.
- Take current narration solely from the text inside `{}`.
- When combining `Audio 1` with a visual-style image, select a live-schema-supported mode such as `mixed2video`. The Seedance 2.0 VIP schema observed on 2026-07-30 supported this combination; query it again before production.
- Do not attach a video merely for voice identity. Download approved Clip 1 through LibTV CLI, follow [Audio Extraction and Format Conversion Guide](audio-extraction-guide.md), produce a 48 kHz stereo 16-bit PCM WAV, and upload it through LibTV CLI as a separate audio node. This WAV format passed Seedance 2.0 validation; M4A was rejected. Video references cost more and may contaminate the visual result.

### Image as a Visual-Style Reference

- When an image controls only visual style, write exactly: `Use Image 1 only as the visual-style reference.`
- Do not restate its material, palette, lighting, or linework, and do not copy its characters, setting, composition, or plot.
- If an image also controls a character, prop, setting, or composition, enumerate those responsibilities precisely instead of using a vague `refer to the image` instruction.
- A style reference is not a first or last frame. Unless explicitly requested and supported by the live schema, do not instruct the model to start from the reference or use it as an endpoint.
- Attach only assets that perform a real job. Do not connect unrelated images, videos, or audio merely because they might help.

### Character References and Extra Styling

- After the full storyboard is approved, list the entire cast. Create and obtain approval for a separate identity reference for every recurring or narratively important main and supporting character.
- Do not let an important character first appear through text-only improvisation. Stop and create the missing reference instead of substituting a similar person, vague description, or another character's image.
- Attach only the character references needed by the current clip. State precise responsibilities such as `Image N controls the identity of Character X` or `Image N controls both the identity of Character X and the overall visual style`.
- When one character image controls both identity and style, prevent its appearance from being copied to other people. Separate `preserve this character's identity` from `other characters inherit only the style`.
- Extras and one-off background characters may omit identity references, but state: `Background characters without separate identity references inherit the overall visual style and character-design language of Image N without copying the referenced person's face, hairstyle, or clothing.`
- Keep extras and main characters in the same visual medium and rendering system. If the main cast uses stylized 3D animation, extras must not become photorealistic humans, flat illustration, or another cartoon style.
- Maintain a character-to-reference-to-clip table before generation. If a newly added character gains a distinct narrative role, treat that character as important, create a reference, and update affected nodes before production.

## Shot Design

### Shot Count and Rhythm

- A 15-second clip normally uses five shots so that approximately 60 spoken Han characters continue to receive new visual information.
- Five shots is the validated default rhythm, not a requirement to break apart one naturally long action. Use fewer shots for a deliberately unhurried action and more for a tight montage.
- Use six or seven shots only for a very dense montage, and reduce action and camera complexity in each one.
- Do not default to exact ranges such as `0–3 seconds`. Express event order with `Shot 1`, `Shot 2`, and so on, and let the model allocate timing.

### Add Spatial Continuity Only When Needed

When several shots revisit one identifiable location and spatial continuity matters, add one shared description before those shots. Define only what needs to remain stable:

1. The basic shape and scale of the setting.
2. The direction and placement of subjects, large furniture, doors, windows, and background objects.
3. The fixed left-to-right or front-to-back order of critical props.
4. The principal light direction and which surfaces receive warm or cool light.
5. Which spatial relationships and object positions remain unchanged after cuts.

Use the shared description to define the location once. Each related shot should choose a camera position within that space and advance the action. Do not redescribe a slightly different room in every shot.

A 15-second runtime does not require all five shots to share one place or continuous timeline. A clip may use hard cuts across independent settings, parallel examples, symbolic images, or different periods. In that case, do not force a shared layout or state transition. Define a clear setting, subject, starting state, visible change, and endpoint for each shot.

### Required Content in Every Shot

Give each shot one principal narrative task and specify:

1. The subject.
2. The setting and visible starting state.
3. A clear, visible change in the subject or setting.
4. The new visual state at the end.
5. Shot size, camera geometry, or one principal camera move.

An action may be slow, but it must create a visible result. Prefer displacement, a major posture change, moving or separating objects, aggregation, fracture, deformation, a door or window opening, scene construction, or spatial reconfiguration. Do not rely only on breathing, hesitation, micro-expressions, or slowly shifting light.

Interpret `one principal narrative task` as `one principal action result`. Closing a book and sliding it beside a candle can be one shot. Standing, walking around a table, crossing the room, unlocking and opening a window, then turning toward the camera contains several results and should be divided. Long action chains often stop halfway.

### Eliminate Visual Ambiguity

Write every shot for a cinematographer and production designer who cannot ask follow-up questions and cannot see the image in your head. Any unresolved choice can become visual drift. A different reader should stage almost the same image from the words alone.

1. Identify the subject precisely: identity, appearance, facing direction, frame position, and shot size. Avoid vague references such as `a person`, `something`, or `it`. Use stable names and descriptions across adjacent shots.
2. Define the space: location, foreground/midground/background placement, and light direction. Describe the camera geometrically—at the doorway, outside a window, to the character's left, or directly above a table; at eye, shoulder, or table height; facing a specific direction. State what occupies the left, center, and right when needed.
3. Refine body movement and quantify degree: specify the moving hand, head, shoulder, foot, or torso, then give amplitude, speed, force, and direction. Write `slowly raises the right hand to chest height`, not `moves slightly`.
4. Externalize abstract concepts and emotions as visible objects, actions, or body details. Do not ask the image itself to be `pain`, `desire`, `will`, or `freedom`. For example, repeated reaches that close on empty space can visualize desire.
5. Make starting state, change, and endpoint concrete. Avoid `slowly changes` or `gradually appears` without stating what changes into what and by what visible process.
6. Prefer a longer deterministic shot description over a short ambiguous one. When trimming, remove repeated style words and vague quality terms, not spatial and action details that make the result unique.

Use one principal camera move per shot. Do not combine push, pull, pan, truck, and orbit. Simplify the camera when subject action is complex; simplify subject action when camera movement is complex.

### Hard Cuts and Continuity

- Use cinematic hard cuts freely and change shot size, angle, motion direction, setting, or visual focus when useful.
- Continuity does not require a smooth transition or identical composition between every shot.
- Give every shot a `start -> movement -> end`. Land the action before cutting, then continue with new information or a new action.
- Carry a completed state forward only when adjacent shots intentionally divide one continuous action. For example: `Begin with the pen tip already suspended above the paper, then lower it to make the first mark.` Independent settings, parallel examples, symbols, and different times should start from newly defined states.
- Do not complete a push-in and then restart another push-in from a similar medium shot. Do not repeat a completed look-up, stand, focus pull, enlargement, tug, release, or door opening.
- Reset only when repetition has explicit narrative meaning, and identify it as a new, intentional repetition.

## Full-Frame Composition and Aspect-Ratio Review

- Read target aspect ratio and resolution from the user or active configuration. Pass actual `ratio` and `resolution` explicitly through the current CLI whenever creating or regenerating a node. Do not inherit old canvas values, copied node settings, or model defaults.
- Pass ratio, resolution, and clip duration as CLI parameters. Do not repeat them in the creative prompt.
- A correct technical container does not guarantee a full-frame image. The model may create internal letterboxing or pillarboxing.
- Avoid phrases such as `ultrawide cinema`, `anamorphic`, `cinematic matte`, and `letterbox` unless that effect is required.
- When earlier output contains internal bars, add this positive composition requirement on regeneration: `Every shot uses a full-frame composition; the scene and background cover the entire visible image area.` Do not restate technical parameters.
- After generation, inspect both metadata and actual frames at the beginning, middle, and end. Reject top, bottom, or side bars; shrunken content; a centered image inside a mismatched container; or an inherited frame from a reference image.
- Mark a clip as failed when its container or effective image does not match the target ratio. Keep task and node logs and regenerate it; do not include it in the final assembly.

## Content That Does Not Belong in the Prompt

- Do not submit external management labels such as `Clip 1:`. Begin with reference responsibilities or narration requirements.
- Do not repeat duration, aspect ratio, resolution, sound controls, count, or `modeType` already passed through LibTV.
- Do not expand `Use Image 1 only as the visual-style reference.` into a long style description.
- Do not choose project policy by adding no-subtitles, no-logo, no-watermark, no-lip-sync, or no-background-music constraints by default. Include only constraints explicitly required by the user or active project.
- Do not submit the full script, creative rationale, character counts, or storyboard reasoning with a clip prompt.
- Do not mislabel a style image as a first frame, last frame, keyframe, or composition to reproduce.
- Do not stack vague quality terms such as premium, stunning, cinematic, epic, or beautiful when they do not translate into a concrete visual instruction.

## Conversational Delivery Format

When presenting several prompts to the user, use external headings and blank lines, not fenced `text` or `plaintext` blocks:

```markdown
### Clip 1

*Narration: 60 Han characters*

Use Image 1 only as the visual-style reference.

Use off-screen narration in Chinese. Speak...

...
```

`Clip 1` and the character count exist only for review. Remove them before copying the prompt into LibTV. The text inside `{}` remains the sole source of narration.

## Preflight Checklist

- For Clip 1, did you correctly distinguish between an existing approved voice reference and no established anchor? For a later clip, did you attach the approved pure audio extracted from Clip 1 instead of a video or another candidate?
- Does upstream asset order match references such as `Audio 1` and `Image 1`?
- Does the prompt make `Audio 1` responsible only for approved voice identity without importing its original words or meaning?
- Are the complete cast list and character-to-reference-to-clip table ready?
- Does every main and important supporting character in this clip have an approved reference attached to the node?
- Is each character image's identity and style responsibility precise, without copying a referenced appearance to other characters?
- Do unreferenced extras explicitly inherit the selected style and character-design language?
- Does the node explicitly set required `ratio` and `resolution` instead of inheriting old or default values?
- Does the prompt refer only to assets that are actually attached?
- Does narration match the final copy exactly, appear once, and sit inside `{}`?
- Were external labels such as `Clip N` and count notes removed?
- Does every shot have a subject, starting state, visible change, and end state?
- Is each shot deterministic about identity, facing direction, position, shot size, camera geometry, light direction, moving body part, amplitude, and speed?
- Have abstract ideas and emotions become visible objects, actions, or body details?
- Are vague phrases such as `slowly changes`, `gradually appears`, and `moves slightly` eliminated?
- Does a 15-second clip normally use five shots, each with one executable principal action result?
- If several shots revisit one space and continuity matters, is there one consistent spatial description without conflicting props, doors, windows, or light directions?
- Does each camera position specify location, height, direction, and necessary left/center/right distribution?
- When adjacent shots divide one continuous action, does the next shot inherit the completed state? When settings are independent, did you avoid forcing an unrelated transition?
- Does each adjacent shot add new information instead of restarting an action or camera move?
- Is there one principal camera move per shot, and is the shot count suitable for 15 seconds?
- Did you avoid exact timestamps, first/last-frame misuse, technical parameters, and repeated style descriptions?
- Are sound, subtitles, logos, watermarks, and music constraints limited to explicit requirements?
- If earlier outputs contained internal bars, is the positive full-frame requirement included?

## Post-Generation Checklist

- Is narration complete and in the right order, with stable voice identity, volume, and pace?
- Was Clip 1's voice approved as the anchor? Do later clips match the attached `Audio 1` or equivalent voice ID?
- Do both the container and effective image match the target aspect ratio?
- Does every shot create a clear, visible change, or has the clip degraded into a static illustration?
- Do hard cuts advance to new images without repeated push-ins, enlargements, or action resets?
- Does every main character match the correct approved reference without face swaps or improvised redesigns?
- Do extras and background characters share the main cast's visual medium, design language, and rendering system?
- Are style, character identity, and critical props stable within and across clips?
- Does the ending contain cut-off speech, a click, or abrupt noise?
