# Animated Voiceover Narration Script Guide

## Navigation

- Scope and objectives
- Writing workflow and clip-length counting
- Runtime-based narrative structure
- Spoken language, facts, and visuals
- Default delivery format
- Pre-delivery checklist

## Scope

Use this guide for educational animated voiceover videos about philosophy, psychology, history, economics, finance, technology, and related subjects. Before writing, confirm the target audience, final runtime, series positioning, and title requirements.

Make the essential ideas understandable without prior specialist knowledge, but do not flatten complex thought into slogans or generic inspiration. Preserve title and series conventions already approved by the user. Ask before proceeding when missing information would materially change the result.

## Objectives

1. Answer one clear question per video instead of listing people, terms, and concepts without structure.
2. Establish the historical context, personal situation, or origin of the problem before explaining the central idea.
3. Advance knowledge through cause and effect, conflict, or a sequence of questions that gives the audience a reason to continue.
4. Connect the subject to real modern problems without distorting the original idea merely to create relatability.
5. Make the narration intelligible without the visuals. Visuals should deepen understanding, not repair missing information.

## Writing Workflow

1. Define the title, central question, and the one sentence the audience should understand by the end.
2. Verify the necessary biography, historical background, conceptual sources, common misconceptions, and controversies.
3. Write the complete narration and validate its overall argument and story.
4. Reorganize it into 15-second clips; never slice the original prose mechanically.
5. Rewrite sentences so each segment approaches 60 spoken Chinese Han characters while preserving complete, natural meaning.
6. Count Unicode Han characters per segment, then read the narration aloud to check pace, pauses, and pronunciation of proper nouns.
7. Confirm that adjacent clips introduce new information. Remove repeated conclusions and transitions that perform no work.

## Clip Length and Counting

- Each video clip is 15 seconds.
- Target 60 spoken Chinese Han characters per narration segment.
- Prefer 59–61 characters. Relax to 58–62 only when natural, complete meaning requires it.
- A one-minute video normally uses about 4 clips, a two-minute video about 8, and a five-minute video about 20.
- Count only narration characters that will be spoken. Exclude punctuation, clip headings, count labels, shot directions, asset notes, and prompt constraints.
- Prefer spelling Arabic numerals in the Chinese form that will actually be spoken. If numerals, English, or abbreviations must remain, check duration by reading them aloud; never exploit their exclusion from the Han-character count to overload a segment.
- Proper nouns, rare terms, and long numbers take more speaking time. Reduce information density when they appear.
- Do not stack clauses, synonyms, or empty conclusions to hit a number. Natural speech is more important than one or two characters inside the allowed range.

The character target applies to Chinese narration. For narration in another language, measure real spoken duration instead of transferring the Chinese count mechanically.

## Structure by Runtime

Choose the information load and clip count from the approved runtime. At 15 seconds per clip, one minute is usually about 4 clips, two minutes about 8, and five minutes about 20. Adjust for complete meaning, speaking rate, and actual model capability.

The following eight-part structure is a useful starting point for a two-minute video. Compress, expand, or combine it for other runtimes instead of applying it mechanically:

1. Open with the subject, a counterintuitive claim, or the central question.
2. Establish the person and period, explaining why the question arose.
3. Present the conflict, crisis, or turning point that shaped the idea.
4. Explain the first central concept.
5. Explain a second concept and its relationship to the first.
6. Explain a third concept, a practical method, or a deeper implication.
7. Correct the most common misunderstanding or place the idea in a modern situation.
8. Answer the opening question with an accurate, restrained conclusion that leaves room for thought.

Keep only biographical details that explain the origin, development, or later misreading of the ideas. Do not turn a philosophy video into a chronological biography, but do not present concepts without explaining why the underlying problems emerged.

## Spoken Style

- Use natural, clear, restrained modern Chinese, as if explaining the subject to an intelligent listener who is new to it.
- Prefer short sentences and precise verbs. Give each sentence one principal claim whenever possible.
- Explain a new term in ordinary language when it first appears. Do not introduce several unexplained terms in succession.
- Give each clip one main information task: at most one core concept and one necessary example.
- Use natural transitions equivalent to `but`, `therefore`, or `the real question is`; avoid chains of suspense hooks and promotional rhetorical questions.
- Avoid broadcast-script filler, academic prose, encyclopedia style, motivational slogans, and unexplained abstractions.
- Do not place storyboard directions such as `Shot 1` or `the image shows` inside the narration.

## Facts and Interpretation

- Distinguish verifiable facts, a thinker's original claims, later interpretations, and the current script's own summary.
- Do not present popular paraphrases as direct quotations. Verify a source before using quotation marks; otherwise paraphrase.
- Do not substitute a single aphorism for a complete explanation or derive an entire philosophy from a sentence removed from its historical and textual context.
- For disputed concepts, give the most defensible core interpretation and clarify what it does not mean.
- When posthumous editing, political appropriation, or popular misreading matters, distinguish the original thinker, editors, and later users.
- Preserve uncertainty when evidence is insufficient. Do not invent motives, inner thoughts, dialogue, or dramatic details.

## Relationship to Visuals

- Give each narration segment a clear, visualizable knowledge claim: a conflict, choice, transformation, relationship, or metaphor.
- Ground abstract ideas in intelligible lived experience, but do not prescribe camera movement during narration writing.
- Avoid several consecutive clips that repeat indistinguishable states such as a person thinking, suffering, or reaching insight.
- Plan shots only after the narration is final. Symbolic visuals may reinforce the argument but must not alter its facts or logic.

## Default Delivery Format

1. Start with the video title. Use the central proposition only as an internal writing check; do not include it in the delivered script or spoken narration.
2. Give each clip its own level-three heading. Put the character count on a separate line and the narration in a separate paragraph.
3. Use this review layout by default:

   ```markdown
   ## Video Title

   ### Clip 1

   *60 Han characters*

   Narration...

   ### Clip 2

   *59 Han characters*

   Narration...
   ```

4. Separate clips with headings and blank lines. Do not stack horizontal rules, tables, or repeated `Narration:` labels.
5. `Clip N`, counts, and the central proposition are only for review and task management. They are not part of the narration submitted to a video model.
6. After a multi-clip script, summarize counts in one line, for example: `Character check: 60 / 59 / 61 / 60`. Do not duplicate the narration or use a table by default.
7. Present scripts as ordinary Markdown paragraphs in conversation, not fenced `text`, `plaintext`, or language-specific blocks. The block above exists only to document layout.
8. Iterate in conversation until the user approves the script. Save a topic-specific final script only when the user confirms it or explicitly requests a file.

## Pre-Delivery Checklist

- Is there enough context for a beginner to understand where the problem came from?
- Are core concepts explained in ordinary language instead of merely named?
- Do all clips form a continuous progression instead of a collection of disconnected aphorisms?
- Is each segment close to 60 Han characters without sounding rushed when read aloud?
- Are there fabricated quotations, timeline errors, mixed concepts, or later interpretations presented as original intent?
- Has a complex idea been reduced incorrectly to success advice, emotional reassurance, or a political label?
- Does the ending actually answer the opening rather than forcing a sudden inspirational uplift?
