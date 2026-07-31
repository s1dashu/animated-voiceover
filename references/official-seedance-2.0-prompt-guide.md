# Seedance 2.0 Official Guidance: Source Index and Operational Digest

## Status and Source Policy

This file is an English operational digest of the official Chinese Seedance 2.0 prompt guide, not an official English translation. The former repository copy was a long snapshot of third-party documentation and embedded media. It was replaced with this concise index so public users consult the maintained official source for current capabilities and examples.

Official entry points:

- [Volcengine visual-generation documentation](https://www.volcengine.com/docs/82379)
- [Official camera-language reference](https://www.volcengine.com/docs/82379/1631633#afc80793)
- [Official text-generation guidance](https://www.volcengine.com/docs/82379/2222480#081b2c64)
- [Official Seedance 1.5 Pro voice-prompt guidance](https://www.volcengine.com/docs/82379/2168087)
- [Seedance 2.0 console examples](https://console.volcengine.com/ark/region:ark+cn-beijing/experience/vision?modelId=doubao-seedance-2-0-260128&tab=GenVideo)

Official documentation and model behavior can change. Read the current source and query the target platform's live model schema before production. When this digest conflicts with current official documentation or a live schema, use the current sources and update this file.

## Official Task Categories

Seedance 2.0 supports image, video, and audio references. The official guide separates reference-based generation into these task types:

1. **Multimodal reference:** extract selected properties such as subject identity, movement, camera language, style, setting, sound effect, or voice and generate a new video.
2. **Video editing:** modify explicitly named parts of an existing video while leaving unspecified parts unchanged.
3. **Video extension:** continue a source video forward or backward while preserving its audiovisual style, subjects, and narrative.
4. **Combined tasks:** use one asset as a reference while editing another.

Distinguish a video used as editable source material from a video used only as a reference. Follow the current provider syntax; vague wording can route the task incorrectly.

## Prompt Construction

The official guide frames Seedance as a multimodal director that reasons about both space and time. An effective prompt specifies:

- A uniquely identifiable subject.
- Detailed, visible action.
- Setting and spatial relationships.
- Lighting and color when they are not already controlled by a reference.
- Shot size and camera movement.
- Visual style when it is not already controlled by a reference.
- Necessary quality and boundary constraints.

Write operational instructions rather than an adjective-heavy creative brief. First establish who does what, then where it happens, how it unfolds, and how it is filmed.

## Subject Identity and References

- When an image or video contains several subjects, identify the intended subject by two or three stable visual traits and assign one consistent label.
- If several assets show the same subject, bind them under the same label.
- Define every important subject separately in multi-character scenes and reuse the same label throughout the prompt.
- Refer to the numbered image or video input, not only an internal asset ID; the model cannot infer which visible content an asset ID is meant to represent.
- Keep descriptions concise and non-contradictory.
- Put the most identity-critical reference early.
- For a recurring person, an isolated face close-up plus a full-body reference is generally safer than a composite multi-view sheet. Multi-view sheets may be interpreted as several people and can cause face drift or duplicate characters.

## Shot Order and Timing

- Organize complex prompts as an ordered shot sequence.
- In every shot, specify camera or cut, subject action and expression, location or spatial change, and relevant audio.
- Prefer event order such as `Shot 1`, `Shot 2`, and `Shot 3` over exact timestamps.
- The official guide warns that constraints such as `0–3 seconds` can be unstable and produce abnormal timing.
- Use standard shot and camera terms directly.
- Prefer one principal camera movement per shot; combining several moves can reduce stability.

## Action and Emotion

- Name the moving body part and quantify direction, amplitude, speed, and force.
- Describe the physical transition between consecutive actions so motion remains continuous.
- Express emotion through visible posture, hands, gaze, breathing, or facial detail instead of abstract labels alone.
- The official guide generally recommends low-intensity, continuous movement over extreme high-energy motion when stability is important. Adapt this to the story, but reduce simultaneous action and camera complexity in demanding shots.

## Asset Strategy

Assign each input one functional role:

1. Character identity.
2. Setting or visual-style control.
3. Camera or motion reference.
4. Rhythm, atmosphere, sound, or voice reference.

Do not fill the model's entire asset allowance automatically. Too many inputs make priority unclear and can cause style conflict, weak identity matching, or unexpected results. Use the fewest references that each have a precise responsibility, and resolve actual limits from the live schema.

## Language, Dialogue, and Text

- Keep dialogue language consistent except for necessary proper nouns.
- Put spoken dialogue in the provider's current dialogue syntax and identify less common languages explicitly.
- The model can render common text for titles, captions, and speech bubbles, but rare characters and unusual symbols are less reliable.
- When accurate text matters, specify exact copy, style, placement, appearance, and timing, then inspect the generated result character by character.
- Treat subtitles, logos, watermarks, lip sync, and music as explicit production choices. Add constraints only when the user or active project requires them.

## Common Failure Modes in the Official Guide

### Character identity drift

Use a clean, isolated face close-up in addition to a full-body reference. State which image controls face identity and which controls wardrobe or full-body styling. Avoid placing unrelated crops and reference purposes into one composite image.

### Duplicate characters

Define each person and bind each to the correct reference. Prefer one-person reference images over multi-view sheets. When many characters are required, group them into a smaller number of intermediate images before video generation. The official snapshot reported reduced stability above four referenced people; confirm current behavior before relying on that number.

### Unwanted subtitles, logos, or watermarks

Use explicit prohibitions only when those outputs are unwanted. Remove unnecessary visible text from input assets before generation. No prompt can guarantee perfect suppression, so inspect the result.

### Style drift

Use input assets already converted to the intended style. State an explicit style only when the reference does not already control it. In this skill's workflow, a dedicated approved style image should carry the detailed visual specification.

### Extension seams and quality loss

Repeated extension may produce seam jumps, content rollback, and cumulative image degradation. Prefer independent clip generation and deliberate editing when the story contains scene or action changes. Use extension primarily for a genuinely continuous scene, and inspect every join.

### Incorrect special effects

When a precise effect has nontrivial motion logic, provide a reference video instead of relying only on prose.

### End-of-video audio noise

Inspect the tail for clicks, truncation, or abrupt noise. Regenerate or apply a deliberate fade during authorized post-production; do not pass a noisy clip as complete.

### Pronunciation errors

Rare or ambiguous written forms may be mispronounced. Test the actual spoken result. A phonetic respelling can help, but it changes submitted copy and therefore requires explicit review.

### Voice mismatch

Describe relevant voice characteristics in addition to attaching the audio reference. Similar delivery and emotional register between reference and target narration can improve consistency. Always judge the generated audio, not merely whether a reference was attached.

## How This Digest Applies to Animated Voiceover

The official material describes many Seedance task types. This skill uses a narrower, validated subset:

- Generate independent 15-second clips rather than defaulting to repeated extension.
- Use a complete, ordered multi-shot plan without exact timestamps.
- Assign one explicit responsibility to every attached asset.
- Approve Clip 1, extract its voice as pure audio, and use that audio to anchor later clips.
- Treat live provider schema as the source of truth for technical parameters and limits.
- Inspect narration, identity, style, motion, effective framing, and audio after generation.

For the complete production rules, use [Video Prompt Guide](video-prompt-guide.md). Do not treat this digest as a substitute for checking current official documentation.
