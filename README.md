<h1 align="center">Animated Voiceover</h1>

<p align="center">
  <strong>Turn complex ideas into cinematic AI-animated educational videos.</strong>
</p>

<p align="center">
  From research and narration to multi-shot prompts, voice consistency, quality control, and final assembly.
</p>

<p align="center">
  <a href="https://github.com/s1dashu/animated-voiceover/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/s1dashu/animated-voiceover?style=for-the-badge&logo=github&color=F4C430"></a>
  <a href="https://github.com/s1dashu/animated-voiceover/network/members"><img alt="GitHub forks" src="https://img.shields.io/github/forks/s1dashu/animated-voiceover?style=for-the-badge&logo=github"></a>
  <a href="./LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-2EA44F?style=for-the-badge"></a>
  <a href="https://github.com/s1dashu/animated-voiceover/commits/main"><img alt="Last commit" src="https://img.shields.io/github/last-commit/s1dashu/animated-voiceover?style=for-the-badge"></a>
  <img alt="Codex skill" src="https://img.shields.io/badge/Codex-Skill-111111?style=for-the-badge&logo=openai&logoColor=white">
</p>

<p align="center">
  <a href="#video-examples">Examples</a> ·
  <a href="#what-it-does">Features</a> ·
  <a href="#installation">Installation</a> ·
  <a href="#usage">Usage</a>
</p>

`animated-voiceover` is an open-source Codex skill for creating AI-generated educational animated voiceover videos about philosophy, psychology, history, economics, finance, technology, and related subjects.

## Video Examples

<table>
  <tr>
    <td width="50%">
      <img src="./assets/examples/video-effect-01.png" alt="Animated philosophy voiceover video frame" width="100%">
    </td>
    <td width="50%">
      <img src="./assets/examples/video-effect-02.png" alt="Animated psychology voiceover video frame" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center"><sub><b>Philosophy explainer</b> — cinematic character storytelling</sub></td>
    <td align="center"><sub><b>Psychology explainer</b> — abstract ideas made visual</sub></td>
  </tr>
</table>

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

<p align="center">
  If this workflow helps you create something worth sharing, consider starring the repository.
</p>
