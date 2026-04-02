# Interactive Business Model Canvas with Cascade Analysis

## What it does
Give it a company name or a business description. It generates a single self-contained HTML file with:
- Standard 9-block Business Model Canvas (Osterwalder format)
- Tap any block to see which other blocks are affected
- 2-3 "what if" scenarios per block with cascade effects
- Risk tags (red) and opportunity tags (green) for each scenario
- Mobile responsive, dark theme, no dependencies

## How to use

### With Claude Code
```
Prompt: "Build an interactive business model canvas for [company/business].
Use the BMC cascade format: 9-block grid, tap any block to see 2-3
scenarios showing how changes cascade to other blocks. Each scenario
has risk tags (red) and opportunity tags (green). Output as a single
self-contained HTML file. Dark background (#1C1917), gold accents
(#c9951a), white cards. Mobile responsive."
```

### With any AI coding tool
Paste the prompt above into Cursor, Windsurf, Copilot, or any AI code editor. The key elements:
1. Standard BMC 9-block grid layout (CSS Grid, 5 columns)
2. Each block has `data-id` attribute matching: kp, ka, kr, vp, cr, ch, cs, cost, rev
3. JavaScript `data` object maps each block to: `title`, `affects` (array of block IDs), `chains` (array of scenarios)
4. Each scenario has: `t` (title), `d` (detail), `r` (risk tags array), `o` (opportunity tags array)
5. Click handler highlights active block, dims unaffected blocks, shows impact panel below

## Example output
- Apple: https://estategenie.ai/canvas-apple.html
- (Your business here)

## Template structure

```html
<!-- Each block in the grid -->
<div class="block" data-id="kp">
  <h2>Key Partners</h2>
  <ul><li><strong>Partner 1</strong> - what they do</li>...</ul>
</div>

<!-- Cascade data (JavaScript object) -->
var data = {
  kp: {
    title: "If Key Partners Change...",
    affects: ["ka", "cost", "vp"],  // which blocks light up
    chains: [
      {
        t: "Scenario title",
        d: "What happens and why it matters",
        r: ["risk 1", "risk 2"],     // red tags
        o: ["opportunity 1"]          // green tags
      }
    ]
  }
};
```

## Tips for good cascades
- Think "what breaks if this block changes?" not just "what's related"
- Best scenarios are specific: "TSMC raises prices 20%" not "supply chain issues"
- Risks should be concrete and named, not vague
- Opportunities should show the flip side of the same change
- 2-3 scenarios per block is the sweet spot. More gets overwhelming.
- The best insight is when a change in one block creates BOTH a risk and an opportunity in the same downstream block

## License
Free. Share it. Build on it. If you make something cool, tell Jared.

---

Built at Harbor Early Stage Workshop, April 2026.
Contact: jared@estategenie.ai
