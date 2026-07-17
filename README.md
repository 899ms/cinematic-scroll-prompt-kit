# Cinematic Scroll Website — Reusable AI Build Kit

A reusable prompt and project-brief system for building cinematic, scroll-driven 2.5D websites with coding agents such as Codex, Claude Code, Hermes Agent, and Kimi Code.

The kit is intentionally framework-agnostic. It can be used in a new static HTML/CSS/JavaScript project or adapted to an existing React, Next.js, Vue, Svelte, Astro, or similar codebase.

## What this kit helps you build

The prompt guides an agent to create:

- one continuous sticky or pinned cinematic stage;
- a layered 2.5D visual world controlled by vertical scrolling;
- depth-aware translation, scaling, blur, tint, and opacity;
- reversible narrative scenes with enter, hold, and exit phases;
- subtle pointer parallax;
- a final interactive card rail or catalog;
- responsive, accessible, reduced-motion-safe behavior;
- documented asset roles and timeline checkpoints;
- a tested, production-oriented implementation rather than a visual scaffold.

It does not require WebGL, Three.js, GSAP, Lenis, or a prerecorded video timeline. An agent may use an existing project dependency when justified, but the default mechanic works with native browser APIs.

## Repository contents

```text
.
├── README.md
├── PROMPT.txt
└── examples
    ├── PROJECT_BRIEF.example.md
    └── assets.example.json
```

- `PROMPT.txt` — the complete agent-agnostic implementation prompt.
- `PROJECT_BRIEF.example.md` — a reusable input template for each new project.
- `assets.example.json` — an example layer manifest.

## Quick start

### 1. Create a project copy

Clone or download this repository. Keep the kit outside your application repository, or copy the three working files into a temporary planning folder inside the project:

```text
your-project/
├── ...
└── cinematic-build-brief/
    ├── PROMPT.txt
    ├── PROJECT_BRIEF.md
    └── assets.json
```

Do not overwrite your application files with this repository. The kit is an instruction layer, not a starter framework.

### 2. Prepare the project brief

Copy:

```text
examples/PROJECT_BRIEF.example.md
```

to:

```text
PROJECT_BRIEF.md
```

Replace every `{{PLACEHOLDER}}`. At minimum, define:

- the subject or brand;
- the primary message;
- the desired narrative beats;
- the final interaction;
- the visual direction;
- the paths to assets and reference media;
- the existing technology stack;
- the required devices and browsers.

Specific inputs produce more reliable results than broad adjectives. Instead of “make it premium,” describe the actual composition, pacing, typography, light, camera, and intended emotional tone.

### 3. Prepare visual assets

Use a single approved master composition. Separate it into aligned depth layers that share:

- the same camera and focal length;
- the same horizon and perspective;
- the same canvas ratio;
- the same light direction and color grade;
- stable anchor positions;
- enough image bleed for zoom and parallax.

A typical layer stack is:

```text
00-sky
10-landscape
20-midground
30-hero
40-foreground-left
41-foreground-right
50-edge-frame
```

Use an opaque WebP or AVIF for the background when possible. Use lossless WebP or optimized PNG for layers requiring alpha transparency.

Avoid:

- text baked into images;
- black or white backgrounds pretending to be transparency;
- mismatched camera angles;
- inconsistent lighting;
- tightly cropped foreground objects;
- visible white or black halos around cutouts;
- different canvas sizes without documented alignment rules.

Update `assets.json` with every file’s role, dimensions, anchor, depth, and responsive variants.

### 4. Give the kit to your coding agent

Open the target application repository in your coding agent.

Provide these inputs together:

1. the full contents of `PROMPT.txt`;
2. the completed `PROJECT_BRIEF.md`;
3. `assets.json`;
4. the actual asset folder;
5. the reference screencast or screenshots.

You can paste the prompt into a new task, attach the files, or reference their paths when the agent can access the local repository.

Recommended opening message:

```text
Use the attached PROMPT.txt as the implementation contract.
Use PROJECT_BRIEF.md and assets.json as project-specific inputs.
Inspect the existing repository and reference media before making changes.
Implement the experience, run it, inspect all timeline checkpoints,
fix visible defects, and return the verification results.
```

Do not ask the agent only to “make something similar.” The prompt is designed to establish a measurable implementation and QA contract.

### 5. Let the agent inspect before coding

The first pass should identify:

- the current stack and run commands;
- existing user changes that must be preserved;
- image dimensions and alpha channels;
- asset roles and anchor points;
- the scene sequence visible in the reference;
- missing or misaligned layers;
- likely performance risks.

If the agent starts writing code without inspecting these inputs, stop it and ask for the asset map and scene map first.

### 6. Review the first implementation by checkpoints

Review the stage at normalized progress values:

```text
0.00  complete hero
0.18  opening copy has exited
0.27  first narrative panel
0.44  clean panorama
0.58  second narrative panel
0.74  world returns to focus
0.90  catalog enters
1.00  final interactive state
```

At every checkpoint, inspect:

- composition;
- layer order;
- transparency gaps;
- accidental cropping;
- text contrast;
- transform continuity;
- asset loading;
- responsive behavior.

Scroll backward as well as forward. A deterministic timeline must reverse cleanly.

### 7. Require a complete verification pass

Before accepting the result, require:

- desktop, tablet, and mobile screenshots;
- upward and downward scroll checks;
- keyboard navigation;
- touch or swipe behavior for the final rail;
- reduced-motion behavior;
- console-error review;
- confirmation that every visible control works;
- confirmation that navigation targets are valid;
- a concise asset manifest and timeline map.

## Reusing the kit across projects

Keep `PROMPT.txt` stable and treat it as the implementation contract. Put project-specific information only in:

- `PROJECT_BRIEF.md`;
- `assets.json`;
- the asset folder;
- reference media.

This separation makes the workflow reusable:

```text
stable implementation prompt
        +
project-specific brief
        +
project-specific asset manifest
        +
reference media
        =
new cinematic website
```

For a new project:

1. Duplicate the example brief.
2. Replace the placeholders.
3. Create a new asset manifest.
4. Supply the new visual layers.
5. Reuse the same prompt unchanged.

Only modify the core prompt when you want to change the production contract for every future project.

## Adapting the narrative

The default timeline contains:

1. hero;
2. first focused narrative;
3. clean-world reveal;
4. second narrative;
5. final catalog.

You can change the content model without changing the core mechanic.

Examples:

- Travel: destination → landmark → local culture → itinerary cards.
- Product: product hero → engineering detail → use context → feature cards.
- Architecture: exterior → structural detail → interior → project facts.
- Portfolio: identity → selected case study → process → project index.
- Event: atmosphere → headline speaker → venue → program cards.

Keep the number of major beats limited. More scenes do not automatically create a more cinematic experience.

## Adapting to an existing framework

The prompt asks the agent to reuse the existing stack.

Typical mappings:

- DOM layers become components only when component boundaries improve maintenance.
- CSS custom properties remain the render interface.
- Timeline state should remain local to the cinematic section.
- Content can move into JSON, CMS data, or component props.
- Framework lifecycle hooks should manage measurement, listeners, and cleanup.
- Server-rendered applications must avoid hydration-dependent first-frame shifts.

Do not rebuild a stable application only to accommodate the effect.

## Asset-generation workflow

AI image tools are best used to create a coherent master composition and controlled variations. Final transparent layers should be composited and cleaned in an image editor.

Recommended sequence:

1. Generate one strong 16:9 master frame.
2. Lock the camera, horizon, light, palette, and framing.
3. Reuse the approved frame as a visual reference.
4. Generate a clean background plate.
5. Generate controlled variants with one object changed or removed.
6. Align every result pixel-for-pixel in an image editor.
7. Cut the final masks.
8. Reconstruct hidden areas behind the hero object.
9. Test edges on both light and dark backgrounds.
10. Export full-size masters and optimized responsive versions.

Do not rely on image generation alone to produce production-ready transparent layers.

## Customization guidance

Safe project-level changes:

- copy and content;
- colors and typography;
- layer files and anchors;
- scene labels;
- timeline durations;
- final card data;
- breakpoint-specific crop positions;
- scroll length;
- parallax intensity.

Changes that require retesting the entire experience:

- adding or removing a major narrative beat;
- changing the master aspect ratio;
- changing the hero object or portal geometry;
- moving the catalog into or out of a scaled world group;
- introducing a smooth-scroll library;
- replacing CSS transforms with canvas or WebGL;
- changing the mobile experience from cinematic scroll to normal document flow.

## Common failure modes

### The motion feels cheap

Usually caused by:

- all layers moving at the same speed;
- excessive travel;
- linear interpolation;
- no hold time between transitions;
- text and images entering simultaneously;
- animation that ignores the composition.

### The scene reveals empty edges

Increase asset bleed, adjust crop rules, or reduce motion. Do not cover the problem with a permanent vignette.

### The page is slow

Check:

- uncompressed 4K PNG files;
- too many full-screen blur filters;
- forced layout inside the frame loop;
- continuous animation after values converge;
- all late-stage assets loaded above the fold;
- unnecessary framework rerenders.

### Mobile composition is broken

Desktop `object-position` and transform origins rarely transfer directly. Define mobile-specific focal points, reduce parallax, and reconsider the scroll length.

### Reduced motion still feels aggressive

Disabling smoothing is not enough. Remove large zoom, lateral motion, and blur. Preserve information using static composition, normal-flow content, or short crossfades.

### The infinite slider is inaccessible

Hide duplicate clones from assistive technology and tab order. Keep a single logical active set, add keyboard support, and use semantic interactive elements.

## Suggested project handoff

Ask the agent to return:

```text
Implementation summary
Timeline map
Asset map
Files changed
Run command
Validation performed
Responsive results
Accessibility results
Reduced-motion behavior
Known limitations
Missing production assets
```

## Versioning the prompt

For team use:

- keep the core prompt in source control;
- tag stable releases;
- document prompt changes in commit messages;
- avoid silently editing the prompt for a single project;
- record project-specific exceptions in the project brief;
- review the prompt after several implementations and promote only broadly useful improvements.

Suggested version tags:

```text
v1.0.0  initial reusable production contract
v1.1.0  new optional capability or QA requirement
v2.0.0  incompatible architecture or workflow change
```

## License

MIT. See `LICENSE`.
