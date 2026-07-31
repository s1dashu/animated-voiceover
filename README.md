# Animated Voiceover

`animated-voiceover` is an open-source Codex skill for creating AI-generated educational animated voiceover videos about philosophy, psychology, history, economics, finance, technology, and related subjects.

It turns a topic into a complete narration, balanced video clips, consistent visual references, production-ready multimodal prompts, a stable narrator voice, and a quality-controlled final assembly plan.

## Video Examples

Replace the placeholders below with representative 16:9 screenshots from finished videos.

<!-- Suggested image paths: assets/examples/example-01.jpg, example-02.jpg, example-03.jpg -->

| Video example 1 | Video example 2 | Video example 3 |
| :---: | :---: | :---: |
| *Add screenshot* | *Add screenshot* | *Add screenshot* |

## What It Does

- Researches and structures educational topics.
- Writes clear narration and divides it into balanced 15-second clips.
- Plans visual style, character references, and multi-shot direction.
- Writes Seedance-ready prompts with explicit asset responsibilities.
- Uses the approved first clip as the voice anchor for later clips.
- Checks narration, voice, identity, motion, framing, and audio before assembly.

## Core Workflow

1. Write and approve the complete narration.
2. Lock the visual style and character references.
3. Write prompts for all clips.
4. Generate and approve Clip 1, then extract its voice reference.
5. Generate later clips in parallel, review them, and assemble the final video.

The currently validated production rhythm uses 15-second clips, approximately 60 spoken Chinese Han characters per clip, and normally five shots per clip.

## Tool Support

The maintained and tested execution path uses LibTV CLI. The creative workflow can also be adapted to Higgsfield, Jimeng, and comparable multimodal CLIs after consulting their latest official documentation and live model schemas.

## Installation

Ask Codex to install the skill from this repository:

> Install the `animated-voiceover` skill from `https://github.com/s1dashu/animated-voiceover`.

You can also clone or copy the repository into your Codex skills directory.

## Usage

Start with a request such as:

> Use `$animated-voiceover` to create a two-minute educational animated voiceover video about the psychology of confirmation bias.

See [SKILL.md](./SKILL.md) for the complete workflow and [references](./references) for detailed writing, directing, audio, cover-image, and LibTV guidance.

## Current Scope

- Optimized and validated for multiple 15-second clips.
- Seedance 2.5 Pro 30-second clips are not yet systematically optimized.
- LibTV CLI is the only officially maintained execution path in the current release.

## License

Original material in this repository is released under the [MIT License](./LICENSE). Third-party documentation and linked materials remain subject to their respective owners' terms.
