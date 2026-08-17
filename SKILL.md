---
name: scene-distillation-zine-v1-3
description: "Transform a user-supplied single photo or multi-panel image into one or two premium zine outcomes: a photo-preserving editorial poster that combines the truthful original image with source-derived typography and graphics, and an original illustrated mood distillation that retains no photographic pixels. Use whenever the user asks to make a photo feel高级、高级感、杂志感、海报化、艺术化、意境化, requests a zine treatment, or invokes this skill with an image. Default to delivering both complementary outcomes unless the user selects `原图高级感模式`, `意境化模式`, or `双方案模式`. Preserve the legacy exact `单色块模式` trigger for the illustrated outcome. Do not use for routine retouching, restoration, or photorealistic object edits."
compatibility: "Requires an image-generation/editing tool and local image inspection."
---

# Scene Distillation Zine v1.4 — Dual Output

Create two complementary readings of a supplied image:

1. **方案 A · 原图高级感** — keep the photograph truthful and recognizable, then art-direct it with typography, source-derived graphic intervention, color structure, framing, and negative space.
2. **方案 B · 意境化重构** — use the photograph only as semantic evidence and create a fully original paper illustration with no retained photo pixels.

The two results should feel like siblings: they share one source reading and emotional direction, but they must not look like minor variations of the same template.

Return generated raster image(s), a concise Chinese creative rationale, and concise art-direction notes. Do not reveal generation prompts.

## Mode Router

Resolve mode before composing. User intent outranks defaults.

- Exact `原图高级感模式` → generate **A only**.
- Exact `意境化模式` → generate **B only**.
- Exact `双方案模式` → generate **A and B**.
- Exact `单色块模式` → apply Solid Color-Block Mode to **B**. If no primary mode is stated, generate B only for legacy compatibility. With `双方案模式`, generate standard A plus solid-color-block B.
- Clear requests to retain the photo, add copy, create magazine layout, or make a premium photo poster → A only.
- Clear requests to abstract, redraw, distill, poeticize, remove realism, or retain no photo material → B only.
- A generic invocation such as “处理一下这张图” → generate **both A and B by default**.

Do not ask the user to select a mode when the router resolves it safely. Ask only when explicit instructions conflict.

## Consent, Privacy, and Source Roles

- Treat a supplied image plus a transformation request as consent to use image generation; do not ask again.
- Inspect local images before generation. Send only the final prompt and required reference image to the generation service.
- Do not browse, search, share, or upload the source elsewhere.
- Do not save the source into project files unless the user asks.
- Label source roles explicitly:
  - A: **edit target / immutable photographic anchor**.
  - B: **semantic reference only**.
- State briefly after generation that the prompt and reference image were used by the generation service.

## Source Topology and Confidence

Before interpreting content, classify the supplied file:

- **single scene** — one photographic moment;
- **multi-panel sequence** — panels visibly belong to one event or progression;
- **multi-panel parallel** — panels share place, subject, motif, or geometry but their relationship is uncertain;
- **before / after** — only when the user or visible evidence establishes change;
- **screenshot / layout artifact** — UI, borders, captions, or accidental composition must not become source meaning.

For multi-panel input, identify each panel's subject, orientation, and shared visual cue before choosing the final canvas. Do not let the outer dimensions of a collage override the spatial logic of its panels.

Use three narrative-confidence levels:

- **Observed:** directly visible facts may be stated.
- **Supported:** a visual relationship may guide metaphor without being claimed as biography.
- **Unknown:** keep the relationship formally open.

Never invent kinship, romance, ownership, chronology, location, or personal history. When relationships are unknown, use language such as parallel, interval, echo, shared direction, or two arrivals rather than factual claims.

## Shared Source Card

Resolve once, then use it differently in A and B:

- semantic nucleus;
- one core subject or at most two inseparable subjects;
- one to three place or atmosphere cues;
- dominant gesture, path, gaze, rhythm, or convergence;
- key spatial invariant;
- native palette and meaningful minor color;
- visual-weight map and natural quiet areas;
- two to four source anchors;
- discard list;
- emotional residue;
- narrative-confidence level;
- intended identity policy.

### Identity Policy

Choose the least literal level that still respects the request:

- **Anonymous silhouette:** posture and number of people only.
- **Semantic likeness — default:** preserve distinguishing cues such as glasses, hairstyle, clothing silhouette, bag, posture, or spacing without requiring realistic facial rendering.
- **Recognizable likeness:** use only when the user explicitly requests identity preservation; keep face, body, pose, and defining accessories stable.

In A, preserve recognizable people and scene geometry unless the user asks otherwise. In B, use Semantic likeness by default rather than erasing every source-specific cue.

## Shared Creative Direction

Write one internal proposition that can drive both outcomes. Build it through:

```text
source fact → emotional residue → proposition → one central tension → source-derived visual metaphor → visible consequence → interpretive opening
```

Use one central tension and one central metaphor. Make formal choices carry meaning through scale, interval, direction, overlap, enclosure, interruption, material, and color. Avoid generic labels such as “healing,” “dreamy,” or “nostalgic” unless visible structure earns them.

## Variant A · Photo-Preserving Editorial

When A is selected, read `references/photo-editorial-mode.md` completely before generating.

Non-negotiable intent:

- the supplied photograph remains the factual anchor;
- people, faces, scene identity, perspective, and meaningful objects stay truthful;
- typography and graphics derive from source geometry or emotion rather than decorating empty corners;
- “premium” means disciplined hierarchy, spacing, typography, crop, material, and color—not generic luxury styling.

Use an image-edit workflow. Preserve the source aggressively. Do not ask the image model to repaint the entire photograph when framing, extension, typography, or graphic overlays can solve the design.

## Variant B · Illustrated Mood Distillation

When B is selected, read `references/scene-distillation-mode.md` completely before generating.

Non-negotiable intent:

- treat the source as semantic evidence only;
- retain two to four specific anchors and remove most descriptive reality;
- create a complete independent artwork with original illustration, paper, and optional typography only;
- do not reproduce, embed, crop, collage, trace, or retain photographic pixels or photorealistic regions from the reference.

## Paired-Outcome Direction

When generating both:

- use the same target ratio unless the user requests otherwise;
- share one proposition, one tension, and one color decision;
- give A a photographic hierarchy and B an illustrative hierarchy;
- vary composition enough that B is not merely A with the photo removed;
- allow wording to echo across both, but do not force identical typography or placement;
- generate each result in a separate image-generation call.

Preserve source orientation by default: 3:5 portrait for portrait logic, 5:3 landscape for landscape logic. For ambiguous composites, derive orientation from the dominant panels and requested use; default to 3:5 only when no stronger cue exists.

## Typography Integrity

Classify text before generation:

- **Exact copy:** user-supplied wording must be reproduced verbatim. Keep it short when possible and verify characters after generation.
- **Authored copy:** write source-specific language that changes or deepens the reading. Prefer one concise headline or fragment over filler metadata.
- **Expressive text:** partial obstruction, fragmentation, or low legibility is allowed only when wording accuracy is not essential.
- **No text:** valid whenever image and structure already carry the proposition.

Do not invent dates, coordinates, issue numbers, quotations, credits, logos, or pseudo-editorial metadata merely to make the result look designed.

## Prompt Budget

Compile one prompt per output. Aim for roughly 250–450 English words, using only decisions that can become visible pixels.

Prioritize:

1. proposition, tension, metaphor, and visible consequence;
2. canvas, hierarchy, eye path, and quiet space;
3. source anchors, invariants, transformations, and omissions;
4. material, color, graphics, and text;
5. no more than 8–12 highest-risk avoids.

Treat numeric ranges as internal art-direction targets. Translate them into perceptual language such as “about three quarters quiet paper” or “one small saturated directional accent” rather than flooding the prompt with percentages.

## Generation Workflow

1. Inspect the supplied image.
2. Resolve mode, topology, source orientation, narrative confidence, and identity policy.
3. Build the Shared Source Card.
4. Establish the shared proposition, tension, metaphor, and color decision.
5. Read only the reference file(s) required by the selected mode.
6. Compile one lean prompt for each output.
7. Generate A and/or B using the correct source role.
8. Run the bounded quality gate below.
9. Save project-bound outputs non-destructively with descriptive sibling filenames.
10. Return image(s), concise rationale, art direction, and the generation-service disclosure.

Generate by default. Stop at prompt-only only when the user explicitly requests a prompt.

## Bounded Quality Gate

Inspect once at normal and thumbnail scale. Do not regenerate for taste alone.

Check every selected output:

- correct mode, count, ratio, and readable file;
- required subjects and panels are represented;
- eye path, hierarchy, and source-specific anchor are visible;
- supplied exact text is correct enough to use;
- no logo, watermark, fake attribution, or accidental extra subject appears.

Check A:

- the photographic scene remains recognizable and truthful;
- identity, face, body, pose, perspective, and defining objects are not unintentionally redrawn;
- copy and graphics perform structural work and do not imitate generic luxury advertising.

Check B:

- no photographic pixels or photorealistic window remains;
- one proposition, one tension, and one source-derived metaphor are legible;
- abstraction remains source-specific;
- Standard Accent or Solid Color-Block rules are visibly respected.

Allow at most one targeted regeneration for an objective failure: source loss, damaged photography, wrong subject count, photo leakage in B, wrong color mode, unreadable exact copy, broken ratio, or missing output. Correct only the observed failure.

## Boundaries with Adjacent Skills

- Use this skill for paired editorial + illustrated outcomes, clean premium photo posters, or fully illustrated mood distillation.
- `scenes-gathered-zine-v1-3` remains the specialist for a photo-preserving **hand-torn fibrous collage** with a large abstract illustration field. Do not force torn-paper treatment into A unless the user requests it.
- Do not use either zine skill for routine denoising, face beautification, object removal, restoration, or photorealistic background replacement.

## Output Format

For dual output:

```markdown
**方案 A · 原图高级感**

![Photo Editorial poster](absolute-image-path-or-rendered-image)

**方案 B · 意境化重构**

![Scene Distillation poster](absolute-image-path-or-rendered-image)

**创作思路**

[One concise Chinese paragraph explaining the shared proposition and how A and B interpret it differently.]

**艺术指导**

- Shared: [source nucleus / tension / metaphor / identity policy]
- A: [photo hierarchy / layout / graphic intervention / typography / color]
- B: [abstraction / composition / edge / color mode / typography]
```

For a single selected mode, return only that image and its relevant rationale. Keep the explanation concise and do not reveal the prompt.

