# Figures & Assets Master Index — Wave 1 (seed for Appendix G)

Generation pipeline: Nano Banana 2 (`gemini-3.1-flash-image-preview`) via
`image-generator` CLI (`scripts/gen-book-wave1.sh`), style grid
`image-generator/style-grids/book-burnt-orange.png` (2×2 grid built from four
established book figures: ch03-homography-calibration, ch06-ball-tracknet,
ch11-live-latency-budget, ch02-evidence-taxonomy).

Style DNA enforced in template `image-generator/templates/book/burnt-orange/config.json`:
white background, black engineering linework, burnt-orange #CC5500 accents only,
clean sans-serif labels, flat technical diagram, 2-3px line weight, no watermarks.

| File | Chapter | Kind | Status | Alt prompt (for regeneration) |
|---|---|---|---|---|
| ch01-five-verbs.png | C01 | diagram | ✅ integrated | Five verbs horizontal flow: Watching -> Tagging -> Modelling -> Interpreting -> Acting, rounded black rectangles, burnt-orange arrows |
| pb-rules-court-crosssection.png | C03 | diagram | ✅ integrated | Court cross-section: NVZ 2.13m, net 0.86m, double-bounce rule, 13.41m length |
| pb-rules-state-machine.png | C03 | diagram | ✅ integrated | Rally state machine: PRE_SERVE -> SERVE -> RECEIVE -> THIRD_SHOT -> DINK_BATTLE -> terminals |
| rl-set-structure.png | C03 | diagram | ✅ integrated | Six-tackle set ladder T1-T6, PTB icons, 10m retreat, kick branch to handover |
| cam-fov-placement.png | C04 | diagram | ✅ integrated (v2: fixed court length 13.41m) | 4.5m pole, 3m setback, sight-line grazing net tape to far kitchen line |
| cam-blur-chart.png | C04 | chart | ✅ integrated | log-log blur vs shutter; 10/20/31 m/s lines; 37mm threshold; SHOOT 1/1000s |
| cam-placement-poster.png | C04 | poster | ✅ integrated | Single-cam blind zone + 66mm parallax vs 2-cam ELC clean sight-lines |
| ingest-pipeline.png | C05 | diagram | ✅ integrated | RAW -> SLICE -> FRAMES -> DETECT -> TRACK -> CALIBRATE -> EVENT -> DUCKDB |
| spine-one-data-model.png | C05 | diagram | ✅ integrated | PBN/EPTS one-spine with tracks/events in, reports/training/replay out |
| stats-bootstrap-ci.png | C20 | chart | ✅ integrated | Naive vs rally-cluster CI comparison at 0.846; design-effect callout |
| stats-calibration.png | C20 | chart | ✅ integrated | Reliability curve with overconfident gap; Brier annotation |

## Regeneration protocol

1. `cd /Users/mehran/Documents/github/image-generator`
2. `node scripts/generate.js --template book/burnt-orange --prompt "<alt prompt verbatim>" --output <book>/state/drafts-v3/images/<file>.png --style-grid style-grids/book-burnt-orange.png`
3. Verify: white bg, black linework, #CC5500 accents, correct facts (dimensions, rule numbers) — every figure is reviewed by the author.
4. Update manifest.json (sha256).

## Known limitations (honest)

- Text in generated diagrams can contain subtle errors (e.g. first FOV pass said "22ft" — corrected to 13.41m/44ft). ALWAYS fact-check the labels.
- AI text rendering of long labels can garble; keep prompts short-label.
- Style grid is from 4 established book figures; if the book style evolves, rebuild the grid first.
