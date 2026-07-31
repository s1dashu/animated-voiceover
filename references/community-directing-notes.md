# Seedance 2.0 Community Direction and Continuity Notes

> Scope: a traceable summary of community practice, not official documentation. If these notes conflict with official Doubao guidance, the live LibTV schema, or user-approved requirements, those sources take precedence.

## Source Snapshot

- [Emily2040/seedance-2.0](https://github.com/Emily2040/seedance-2.0/tree/6c51262377b96592b9f87a8c8b0219e6335378f7), commit `6c51262377b96592b9f87a8c8b0219e6335378f7`, especially:
  - `skills/seedance-prompt/SKILL.md`
  - `skills/seedance-camera/SKILL.md`
  - `skills/seedance-motion/SKILL.md`
  - `skills/seedance-sequence/SKILL.md`
  - `skills/seedance-prompt-short/SKILL.md`
- [dexhunter/seedance2-skill](https://github.com/dexhunter/seedance2-skill/tree/e06c7c63a766d623004a2807881c30685ce517af), commit `e06c7c63a766d623004a2807881c30685ce517af`, especially `zh/SKILL.md`.
- [nolanx-ai/nolanx.ai](https://github.com/nolanx-ai/nolanx.ai/tree/595d86364377f654e24ddf2c9e875496d85e8246), commit `595d86364377f654e24ddf2c9e875496d85e8246`, especially `skills/sd2-pe/SKILL.md`.

Verified on 2026-07-30.

## Practices Adopted by This Skill

1. Treat a prompt as a concise shooting plan, not a pile of adjectives. Give each shot one distinct narrative job.
2. Define each shot's starting composition, principal subject or camera movement, speed, and end state. Camera moves need destinations; actions need visible consequences.
3. Allow cinematic hard cuts. A cut may deliberately change shot size, angle, direction, setting, or narrative focus; the cut itself is not a continuity error.
4. Track both camera-move progress and action progress. Do not restart a completed push-in, zoom, follow, focus pull, or subject action from a similar state in the next shot unless repetition is intentional.
5. End each shot in a visibly new state. Continue after that result instead of replaying the completed action. Loops that do not change state create a conspicuous AI-generated feel.
6. When shortening a prompt, preserve reference responsibilities, the subject, action verbs, a visible end state, and one principal camera move. Remove repeated style adjectives, vague quality terms, secondary actions, and secondary camera moves first.

## Practices Not Adopted by This Skill

- Do not make exact timestamped shot lists the default. Official guidance notes that precise timing constraints can be unstable, so use event order such as `Shot 1`, `Shot 2`, and so on.
- Do not copy provider calls, prices, resolutions, or asset limits from community skills. Resolve those from the live LibTV schema.
- Do not copy long negative-prompt templates. Include only constraints required by the user or active project; the skill must not choose subtitle, logo, watermark, music, or lip-sync policy on its own.
- Do not repeat style adjectives in the video prompt. When an approved image controls style only, write: `Use Image 1 only as the visual-style reference.`
