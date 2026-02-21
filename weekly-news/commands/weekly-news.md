---
name: weekly-news
description: Generate an impact-scored weekly news report for any industry or topic
trigger: /weekly-news
---

# Weekly News Report Generator

Generate a comprehensive weekly news report with impact scoring for any industry or topic area.

## Execution Steps

### Step 1: Gather Requirements

Use AskUserQuestion to collect:

**Question 1: Research Topic**
- Header: "Topic"
- Question: "What topic or industry should this weekly report cover?"
- Options:
  - Insurance industry (comprehensive U.S. insurance coverage)
  - AI and technology (artificial intelligence developments)
  - Financial services (banking, fintech, payments)
  - Healthcare (medical, pharma, health tech)
- multiSelect: false

**Question 2: Date Range**
- Header: "Time period"
- Question: "What time period should the report cover?"
- Options:
  - Past 7 days (most recent week of news)
  - Past 14 days (two-week period)
  - Custom date range (I'll specify start and end dates)
- multiSelect: false

**Question 3: Output Location**
- Header: "Save location"
- Question: "Where should the completed report be saved?"
- Options:
  - Default folder (~/Desktop/Weekly News/)
  - Workspace outputs (current session outputs folder)
  - Custom location (I'll specify the path)
- multiSelect: false

**Question 4: Source Focus** (only if user selected custom topic)
- Header: "Sources"
- Question: "Do you have specific sources or websites you want prioritized?"
- Options:
  - Let Claude identify authoritative sources
  - I'll provide a list of sources to focus on
- multiSelect: false

### Step 2: Load Research Skills

Invoke the weekly-news-research skill to access:
- Impact scoring methodology
- Source identification guidance
- Story compilation process
- Analysis and synthesis techniques

If the user selected a topic with a reference example (like insurance), mention that you'll use that as a guide for scoring criteria and sources.

### Step 3: Define Impact Scoring Framework

Based on the topic, either:
- **Use existing framework** - If insurance or another domain with a reference file, use that scoring system
- **Create custom framework** - Work with the user to define 4-6 scoring dimensions appropriate for their topic

Present the scoring framework to the user and confirm before proceeding.

### Step 4: Identify Sources

Based on the topic and any user-provided sources:
1. List 10-20 primary sources to review
2. Categorize sources (trade publications, research firms, regulatory bodies, company sources, etc.)
3. Explain the rationale for source selection
4. Get user confirmation

If user provided custom sources, incorporate those prominently.

### Step 5: Execute Research

Systematically search for and compile stories:

1. **Broad searches** - General topic + date range
2. **Specific searches** - Major companies, regulatory bodies, key terms
3. **Direct source review** - Visit primary trade publications and scan recent headlines
4. **Cross-reference** - Follow up on related developments mentioned in stories

For each story found:
- Assess using the impact scoring framework
- Record: headline, companies involved, key details, sources/URLs
- Focus on stories scoring 10+ points
- Aim for 8-12 total stories

### Step 6: Analyze and Synthesize

Identify patterns across the week's stories:
- Recurring themes and trends
- Strategic implications
- Competitive dynamics
- Future outlook
- Risk factors

Note any particularly significant development that deserves spotlight treatment.

### Step 7: Format Report

Load the weekly-news-format skill to ensure consistent output structure.

Format the report following the standard template:
- Sort stories by impact score (highest first)
- Include all required sections for each story
- Add visual indicators (🔥 high impact, ⚖️ regulatory, 🤖 AI/tech, 💰 financial)
- Ensure source links are working and properly formatted

### Step 8: Save Report

Determine the full output path:
- If default folder: `~/Desktop/Weekly News/[Topic] Weekly [DATE].md`
- If workspace: `/sessions/tender-determined-bell/mnt/outputs/[Topic] Weekly [DATE].md`
- If custom: user-specified path

Use the filesystem MCP connector to write the file.

Provide the user with a direct link to the completed report.

## Output Requirements

The final report must include:
- Clear headline for each story
- Impact score (X/25) prominently displayed
- Companies/entities involved (clean names, no Inc/LLC)
- Detailed analysis covering: key details, implications, timeline
- Source URLs for verification
- Total length: 1,500-2,500 words depending on story count

## Quality Checks

Before saving the final report, verify:
- [ ] All stories scored using the defined framework
- [ ] Scoring rationale is defensible and consistent
- [ ] Sources are cited with working links
- [ ] Company names are formatted consistently
- [ ] Report follows the weekly-news-format template
- [ ] Strategic implications are explained for each story
- [ ] Overall trends or patterns are identified
- [ ] Report length is appropriate (not too verbose or too sparse)

## Error Handling

If you encounter issues:
- **No stories found** - Expand search terms, try broader queries, check if date range is too narrow
- **All stories score low** - Consider whether scoring criteria are too strict, or if it was genuinely a slow news week
- **Source access issues** - Document which sources couldn't be accessed, use alternative sources
- **Ambiguous scoring** - When in doubt, score conservatively and note the uncertainty in the analysis

## User Communication

Throughout execution:
- Provide progress updates (e.g., "Searching insurance trade publications...")
- Ask for clarification if topic scope is unclear
- Present the impact framework for approval before scoring
- Summarize key findings briefly when delivering the report
- Offer to refine the report if user wants adjustments

## Customization Notes

This command is designed to be flexible:
- Works for any industry or topic area
- Adapts scoring criteria to domain-specific drivers
- Can incorporate user-provided sources and preferences
- Balances automation with user input for best results

Use the reference examples in the weekly-news-research skill as templates, but don't be constrained by them. The methodology adapts to any domain where systematic news monitoring adds value.
