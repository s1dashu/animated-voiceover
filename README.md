<h1 align="center">Animated Voiceover</h1>

<p align="center">
  <strong>English</strong> · <a href="./README_CN.md">简体中文</a>
</p>

<p align="center">
  <strong>Turn personal stories and complex ideas into AI-animated videos worth watching.</strong>
</p>

<p align="center">
  <img src="./repository-assets/repository-covers/animated-voiceover-cover.png" alt="Animated Voiceover — a multi-mode Agent workflow for AI animated videos" width="100%">
</p>

<p align="center">
  <a href="./SKILL.md"><img alt="Agent Skill" src="https://img.shields.io/badge/Agent-Skill-111111"></a>
  <a href="#what-it-can-do-for-you"><img alt="Animated Explainer: production validated" src="https://img.shields.io/badge/Explainer-validated-2EA44F"></a>
  <a href="./LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-2EA44F"></a>
</p>

<p align="center">
  <a href="#what-it-can-do-for-you">Core Capabilities</a> ·
  <a href="#video-examples">Examples</a> ·
  <a href="#built-in-visual-styles">Visual Styles</a> ·
  <a href="#installation">Installation</a> ·
  <a href="#start-with-a-single-sentence">Get Started</a>
</p>

`animated-voiceover` separates a video's editorial format from its visual look. Choose a production Mode first, then a prompt-defined style, reusable voice, and media CLI. The current release routes between Storytime Animation and Animated Explainer without forcing one format's writing rules onto the other.

Animated Explainer and Storytime Animation have both been validated in production. Storytime has completed its first five-clip English project, including reusable character design, direct-to-camera narration, reenactment, stable voice identity, and multi-clip generation.

## What It Can Do for You

- **Choose the right production grammar.** Use first-person storytelling when the narrator's experience drives the film, or concept explanation when the goal is to make an idea understandable.
- **Make complex ideas easy to follow.** From topic research and editorial decisions to narration structure, it helps you build a line your audience can understand and wants to keep watching.
- **Turn a script into a production-ready animation plan.** It breaks the narrative into balanced segments, directs multiple shots for each one, and produces video prompts ready for Seedance.
- **Keep the entire video consistent.** Prompt-defined styles, required character references, and voice anchors reduce character drift, style shifts, and voice inconsistency across clips.
- **Go from idea to editable clips.** Beyond writing, it can continue through reference planning, clip generation, and task tracking, then hand the generated clips to your editor for final assembly and light cleanup.

## Video Examples

<table>
  <tr>
    <td width="50%">
      <img src="./repository-assets/examples/video-effect-01.webp" alt="Animated philosophy explainer scene" width="100%">
    </td>
    <td width="50%">
      <img src="./repository-assets/examples/video-effect-02.webp" alt="Animated psychology explainer scene" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center"><sub><b>Philosophy</b> — bringing ideas into characters and stories</sub></td>
    <td align="center"><sub><b>Psychology</b> — explaining abstract concepts through concrete events</sub></td>
  </tr>
</table>

## Built-in Visual Styles

The Skill includes seven carefully developed visual languages, ranging from cinematic 3D to clean white-character Storytime animation and hand-drawn crayon animation. Each style defines more than what the image should look like: it also provides creative direction for character design, materials, color, camera movement, and animation rhythm.

These styles are starting points, not templates. The Skill redesigns the setting, characters, and shots around each new topic. You can also provide your own textual style description to create an entirely different visual direction; visual style references are not image assets.

<table>
  <tr>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v3.webp"><img src="./repository-assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v3.webp" alt="Cinematic 3D animation preview" height="220"></a><br>
      <b>Cinematic 3D Animation</b><br>
      <sub>Painterly surfaces, restrained color, and story-rich cinematic lighting</sub><br>
      <a href="./styles/cinematic-3d-animation.md">View style guide</a>
    </td>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/clay-stop-motion.webp"><img src="./repository-assets/style-previews/clay-stop-motion.webp" alt="Clay stop-motion preview" height="220"></a><br>
      <b>Clay Stop-Motion</b><br>
      <sub>Handmade clay figures, miniature sets, and tactile frame-by-frame motion</sub><br>
      <a href="./styles/clay-stop-motion.md">View style guide</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/melancholic-blue-simple-line-animation.webp"><img src="./repository-assets/style-previews/melancholic-blue-simple-line-animation.webp" alt="Melancholic blue line animation preview" height="220"></a><br>
      <b>Melancholic Blue Line Animation</b><br>
      <sub>Cool blue-gray paper, awkward pencil lines, and a quiet introspective mood</sub><br>
      <a href="./styles/melancholic-blue-simple-line-animation.md">View style guide</a>
    </td>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/soft-colored-pencil-cute-animation.webp"><img src="./repository-assets/style-previews/soft-colored-pencil-cute-animation.webp" alt="Soft colored-pencil cute animation preview" height="220"></a><br>
      <b>Soft Colored-Pencil Animation</b><br>
      <sub>Gentle outlines, warm paper texture, and an approachable playful tone</sub><br>
      <a href="./styles/soft-colored-pencil-cute-animation.md">View style guide</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/clean-line-crayon-animation.webp"><img src="./repository-assets/style-previews/clean-line-crayon-animation.webp" alt="Clean-line crayon animation preview" height="220"></a><br>
      <b>Clean-Line Crayon Animation</b><br>
      <sub>Bright color blocks, clear hand-drawn lines, and an orderly 2D world</sub><br>
      <a href="./styles/clean-line-crayon-animation.md">View style guide</a>
    </td>
    <td width="50%" align="center">
      <a href="./repository-assets/style-previews/dopamine-cute-3d-animation-16x9-v2.webp"><img src="./repository-assets/style-previews/dopamine-cute-3d-animation-16x9-v2.webp" alt="Dopamine cute 3D animation preview" height="220"></a><br>
      <b>Dopamine Cute 3D Animation</b><br>
      <sub>Bouncy characters, vibrant colors, and energetic layered compositions</sub><br>
      <a href="./styles/dopamine-cute-3d-animation.md">View style guide</a>
    </td>
  </tr>
</table>

The shared library also includes [Clean White-Character Storytime Animation](./styles/clean-white-character-storytime-animation.md): rounded white 2D characters, crisp black outlines, limited flat colors, expressive performance, and environments that are more detailed than the cast.

## More Than a Look: Reusable Voices

Alongside the seven prompt-defined visual styles, the Skill includes multiple standardized Chinese and English voices.

You can use one of these voices directly, or create a dedicated voice for the current production from the first clip. The Skill asks you to make the choice—it never silently decides the style or voice for you.

See the complete [built-in voice library](./references/reference-asset-library.md).

## Production-Validated Workflows

Storytime Animation adds first-person story collection, a reusable Storytime-only [character library](./modes/storytime-animation/characters/character-library.md), conversational character co-design, narrator performance, and flexible movement between direct address and reenactment. Animated Explainer retains the production workflow that existed before the Mode architecture.

1. **Decide what to say.** Research the topic around your audience and target duration, then write a clear, well-structured narration script.
2. **Decide how it should look.** Choose a built-in or custom prompt-defined style, then create references only for characters who must remain recognizable.
3. **Direct the words into scenes.** Break the script into balanced segments and design concrete events, multi-shot direction, and generation-ready prompts for each one.
4. **Validate before scaling.** Produce the first clip, confirm the visual and vocal direction, then lock the voice and required character references before generating the rest.
5. **Finish in an editor.** Download every generated clip, then manually assemble and lightly trim failed edge frames, tiny end-of-clip audio glitches, pacing, and cut points. Automated assembly remains available only when explicitly requested.

The production rhythm validated so far breaks a 1–5 minute video into 15-second clips. Animated Explainer typically targets roughly 60 Chinese characters or about 32 English words and around five shots. English Storytime targets 30 spoken words, normally 28–32, and usually uses 3–5 shots, with about four as the current stable starting point.

## Installation

Clone or copy this repository into a skills directory your Agent can access.

If you use Codex, you can also tell it directly:

> Install the `$animated-voiceover` skill from `https://github.com/s1dashu/animated-voiceover`.

## Start with a Single Sentence

Once installed, you can begin with a request like this:

> Use the `animated-voiceover` Skill to create a two-minute animated explainer: “Stoicism in Two Minutes.”

Or include more creative direction:

> Use the `animated-voiceover` Skill to turn “Why do people procrastinate?” into a 90-second psychology explainer. Use a gentle tone and a hand-drawn style, and confirm the script and visual direction with me first.

The Skill will guide you through the necessary choices. You do not need to understand Seedance prompting, voice anchors, or multimodal asset connections in advance.

## Tools and Scope

The officially maintained and production-tested media execution path currently uses [LibTV CLI](https://libtv.ai/). The underlying methods for narration structure, visual consistency, character references, multi-shot direction, and voice management are not tied to a single platform. After reviewing the latest official documentation for the target platform, they can also be adapted to Higgsfield, Jimeng, and other multimodal generation CLIs.

The current workflow is designed primarily for 1–5 minute videos assembled from multiple 15-second clips. Seedance 2.5 Pro's 30-second clips have not yet been systematically validated, so they are not presented as a default capability of this release.

For the full execution rules, read [SKILL.md](./SKILL.md). The methods for narration, video prompts, voice references, and cover production are organized under [`references/`](./references/).

## License

Original content in this repository is released under the [MIT License](./LICENSE). Third-party documentation and externally linked content remain subject to their respective licenses and rights.

<p align="center">
  <strong>If you want to make animated stories and ideas more watchable, try it, share it, and give the project a Star.</strong>
</p>
