name: Update Agent
description: Researches unprocessed items and updates the README with the results
---

# AI Agent Instructions: Research and Format Project Entries

## Overview

Your task is to research and format AI agent project entries in the README.md file. You will process unprocessed items (bullet points with URLs) and convert them into formatted table entries.

## Table Format

Each section should have a table with the following columns:

```markdown
| Project | Description | Open-Source | GitHub | Runtime | Released |
|---------|-------------|-------------|--------|---------|----------|
```

### Column Specifications

**Project:**
- Format: `**[Project Name](URL)**` or `**[Project Name](URL)** (by Organization)`
- Make the link bold
- **ALWAYS check for parent organization:**
  - If project has a parent company/organization different from the project name, add it as `(by Organization)`
  - Examples: `**[NotebookLM](url)** (by Google)`, `**[TRAE](url)** (by ByteDance)`
  - Check: About page, footer, legal documents, press releases, Wikipedia
- **CRITICAL:** Pay special attention to the exact spelling of project names:
  - Capitalization (e.g., "Superdesign" not "SuperDesign", "TRAE" not "Trae")
  - Spaces vs. hyphens (e.g., "Project Name" vs. "Project-Name")
  - Special characters or styling
- **To verify official spelling, check IN THIS ORDER:**
  1. **Primary source (official website):**
     - Copyright notice at the bottom (e.g., "©2025 TRAE. All rights reserved.")
     - Legal documents (Terms of Service, Privacy Policy, About pages)
     - Logo and branding as displayed on the official site
  2. Secondary sources (news articles) - use only if primary source is unclear
  - **NEVER** rely solely on how journalists or bloggers spell the name
  - Primary sources are ALWAYS more authoritative than secondary sources

**Description:**
- If the unprocessed item has text after the URL (e.g., `- https://example.com: foo bar baz`), use that text as the description
- Only fix obvious typos if present
- If the unprocessed item has only a URL, create a single short sentence description
- Maximum length: 80 characters (if possible)
- **Avoid all marketing language:**
  - No buzzwords: "AI-powered", "revolutionary", "cutting-edge", "intelligent", "smart"
  - No qualitative adjectives: "fast", "powerful", "best", "professional", "amazing", "advanced", "modern"
  - No marketing modifiers: "adaptive", "seamless", "intuitive", "innovative", "robust", "comprehensive"
  - Strip these words out completely - e.g., "Adaptive AI IDE" → "IDE", "Intelligent code editor" → "Code editor"
- Keep it factual and concise - describe what it IS, not how good it is
- End with a period

**Open-Source:**
- Use ✅ for open-source projects
- Use ❌ for closed-source projects

**GitHub:**
- If open-source with a GitHub repository: `[user/repo](https://github.com/user/repo) (⭐️ ~Xk)`
- Format: Shorten URL to `user/repo` in the link text
- Add star count in format: `(⭐️ ~X.Xk)` for thousands, `(⭐️ ~X)` for under 1k
- Round to one decimal place for thousands (e.g., 5214 → ~5.2k, 847 → ~800, 12543 → ~12.5k)
- If no repository: ❌

**Runtime:**
- Use emoji icons based on where/how the project runs:
  - 💻 CLI: Command-line interface tool (runs in terminal)
  - 🖥️ Binary: Standalone application to install locally (e.g., desktop IDE or editor)
  - 🧩 Plugin: Extension or plugin for existing software (e.g., IDE extensions, editor plugins)
  - 🌍 Web: Web-based application (accessed through a browser)
- If a project supports multiple runtimes, include all applicable emoji icons (e.g., `💻 CLI, 🌍 Web`)

**Released:**
- Format: `[Mon YYYY](source-url)`
- Example: `[Oct 2025](https://news.ycombinator.com/item?id=12345)`
- Link to a reliable source documenting the release date
- **For open-source projects with GitHub repos, check releases/tags FIRST:**
  - GitHub releases page: `github.com/user/repo/releases`
  - GitHub tags page: `github.com/user/repo/tags`
  - Look for v0.01, v0.1, v1.0, or first release/tag - this indicates initial launch date
  - Use the date of the first release/tag as the launch date
- **Finding approximate dates is better than "Unknown"**:
  - Look for Product Hunt launch pages (e.g., producthunt.com/products/[name]/launches)
  - Look for Hacker News INITIAL launch posts (e.g., "Show HN" or "Launch HN" - NOT version updates)
  - **CRITICAL:** When checking HN/PH posts, verify it's the INITIAL/FIRST launch, not a version announcement (v0.005, v2.0, etc.)
  - Articles dated shortly after launch often indicate launch timeframe
  - Multiple sources saying "recently launched" around the same time period
  - Even if you can't find the exact date, finding the month/year is acceptable
  - Being off by a few days or even one month is better than "Unknown"
- Only use `Unknown` (no link) if truly no evidence of launch timeframe can be found after exhaustive research

## Research Requirements

For each unprocessed item, research the following:

### 1. Project Name and Parent Organization
- Official name of the project
- **Verify exact spelling from primary sources:**
  - Check copyright notice on official website (e.g., "©2025 TRAE. All rights reserved.")
  - Check legal documents (Terms of Service, Privacy Policy)
  - Look at logo and branding on official site
  - Do NOT rely solely on secondary sources (news articles, blog posts)
- Verify capitalization, spaces, and hyphens
- **Parent organization:**
  - Check if project has a parent company/organization different from the project name
  - Common sources: About page, footer, legal documents, press releases
  - Examples: NotebookLM is by Google, TRAE is by ByteDance
  - If parent organization exists and differs from project name, add it as "(by Organization Name)"

### 2. Runtime
- **CRITICAL:** Identify the PRIMARY/MAIN product, not auxiliary tools
  - Start with official website - what does the homepage promote?
  - Use your model knowledge - ask yourself "What is [Product Name]?"
  - Check documentation (Docs link) - look for "What is...?", "Introduction", "Quickstart" sections
  - Example: TRAE's main product is an IDE (desktop app, plugins, web), even though they also have a separate "Trae Agent" CLI tool
- Determine where/how the PRIMARY product runs:
  - **💻 CLI:** Runs in a terminal/command line
  - **🖥️ Binary:** Standalone desktop application to install locally (e.g., IDE, editor)
  - **🧩 Plugin:** Extension for existing software (e.g., VS Code extension, browser plugin)
  - **🌍 Web:** Web-based service accessed through a browser
- If the PRIMARY product supports multiple runtimes, list all applicable types
- Do NOT classify based on auxiliary/secondary tools in the ecosystem

### 3. Open-Source Status
- Is the code publicly available?
- Check for GitHub, GitLab, or other public repositories

### 4. GitHub Repository
- If open-source, find the GitHub repository URL
- Get the current star count
- Format as `user/repo` with star count

### 5. Release Date
- **CRITICAL:** Take extra care when researching release dates
- **Priority: Find at least the month/year** - this is better than "Unknown"
- Sources to check (in order of reliability):
  1. **For open-source projects:** GitHub releases/tags pages (use date of FIRST release/tag)
     - `github.com/user/repo/releases`
     - `github.com/user/repo/tags`
     - Look for v0.01, v0.1, v1.0, or earliest release
  2. Official launch announcements (company blog, press releases)
  3. Product Hunt launch page (producthunt.com/products/[name]/launches)
  4. Hacker News INITIAL launch posts (search for "Show HN" or "Launch HN")
     - **CRITICAL:** Verify it's the INITIAL launch, not a version update (v0.005, v2.0, etc.)
  5. Wikipedia with cited sources
  6. News articles dated shortly after launch
  7. Multiple sources mentioning "recently launched" around the same timeframe
- **Inferring approximate dates is acceptable:**
  - An article from October 2025 about a "newly launched" product → likely Oct 2025
  - Multiple sources in early November saying "launched a few days ago" → likely late Oct or early Nov 2025
  - Being off by a few days or even one month is acceptable
- Do NOT use company founding dates unless explicitly stated as the release date
- Do NOT use version announcements (v0.005, v2.0) as launch dates - these are updates, not launches
- Link to the most specific source you found (GitHub releases > Product Hunt > Hacker News > news article)
- Only use `Unknown` if absolutely no evidence of launch timeframe exists after exhaustive research

### 6. Description
- If text exists after the URL in the bullet point, use it (with typo fixes only)
- If no text exists, create a concise single-sentence description
- **Describe the PRIMARY/MAIN product:**
  - Focus on what the main product IS (IDE, editor, platform, etc.)
  - NOT auxiliary tools (CLI companions, SDKs, etc.)
  - Use your model knowledge and official website to identify the primary product
  - Example: For TRAE, describe the IDE (main product), not the Trae Agent CLI tool (auxiliary)
- **Strip ALL marketing language:**
  - Remove adjectives: "adaptive", "intelligent", "smart", "advanced", "modern", "powerful"
  - Focus on WHAT it is, not HOW GOOD it is
  - Example: "Adaptive AI IDE" → "IDE"
  - Example: "Intelligent code completion tool" → "Code completion tool"
- Be factual and neutral - describe function, not quality

## Research Process

1. **Identify the PRIMARY product first:**
   - Use your model knowledge - ask yourself "What is [Product Name]?"
   - This gives you a baseline understanding before doing research
2. **Use WebFetch** to visit the project's official website:
   - **Understand the main product** - what does the homepage promote?
   - Look for download buttons, screenshots, main features
   - Check documentation (Docs link) for "What is...", "Introduction", "Quickstart" sections
   - **Check copyright notice** for official spelling (e.g., "©2025 TRAE. All rights reserved.")
   - Check Terms of Service / Privacy Policy for official company name
   - Look at logo and branding
   - Check About page / footer for parent organization
3. **Use WebSearch** to find additional information, but always prioritize official sources
4. **Check GitHub** (if open-source):
   - **Use WebFetch on the web interface** (NOT the GitHub API):
     - `github.com/user/repo` for star count
     - `github.com/user/repo/releases` for release dates
     - `github.com/user/repo/tags` for version tags
   - Look for FIRST release/tag to determine launch date
   - Get current star count from the main repo page
5. **Verify release dates** carefully:
   - For open-source: GitHub releases/tags FIRST (look for earliest release)
   - Check Product Hunt launch page (producthunt.com/products/[name]/launches)
   - Check Hacker News for INITIAL launch posts (search for "Show HN" or "Launch HN")
     - Verify it's the INITIAL launch, not a version update
   - Check Wikipedia with cited sources
   - Look for official blog posts or announcements
   - Search for "launched" or "released" in news articles
   - Look at article publication dates - articles about "newly launched" products indicate timeframe
   - Multiple sources saying "recently launched" around same time indicate approximate launch date
   - Finding month/year is better than saying "Unknown"

## Updating Existing Entries

For existing table entries with GitHub repositories:

1. Visit each GitHub repository URL
2. Get the current star count
3. Update the star count in the format `(⭐️ ~X.Xk)` or `(⭐️ ~X)` (rounded to one decimal place for thousands)
4. ONLY update the GitHub star count. Do NOT change any other fields (project name, description, type, release date, etc.)

## Handling Mixed Processed and Unprocessed Items

A section may contain:
- **Only unprocessed items** (bullet list): Create a new table
- **Only processed items** (table): Update star counts and "Last updated" date
- **Both processed and unprocessed items** (table + bullet list): Add new rows to the existing table

When a table already exists:
1. Add new rows to the existing table for unprocessed items
2. Append new entries to the end of the table in the same order as they appear in the bullet list
3. Remove the bullet points after adding them to the table
4. The "🤖 Content researched by AI. Last updated YYYY-MM-DD." line already exists below the table
5. Update the date in that line to today's date

## Final Steps

After processing all items in a section:

1. Remove the processed bullet points
2. If no "🤖 Content researched by AI. Last updated YYYY-MM-DD." line exists, add it below the table
3. If the line already exists, update the date to today's date
4. Use today's date in ISO format (YYYY-MM-DD)

After processing ALL sections in the README:

1. Update ALL "Last updated" dates below tables to today's date
2. Update the top-level "Content last updated" line near the beginning of README.md (format: `_**🤖 Content last updated YYYY-MM-DD by AI.**_`) to today's date

## Example Transformations

### Example 1: New Section (Only Unprocessed Items)

**Before:**
```markdown
## General

- https://example.com/tool: helps with testing
- https://another-tool.io
```

**After:**
```markdown
## General

| Project | Description | Open-Source | GitHub | Runtime | Released |
|---------|-------------|-------------|--------|---------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.2k) | 💻 CLI | [Mar 2024](https://github.com/user/example-tool/releases) |
| **[AnotherTool](https://another-tool.io)** | Creates automated workflows for development teams. | ❌ | ❌ | 🌍 Web | [Jan 2025](https://news.ycombinator.com/item?id=12345) |

🤖 Content researched by AI. Last updated 2025-11-04.
```

### Example 2: Existing Table with New Unprocessed Items

**Before:**
```markdown
## General

| Project | Description | Open-Source | GitHub | Runtime | Released |
|---------|-------------|-------------|--------|---------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.0k) | 💻 CLI | [Mar 2024](https://github.com/user/example-tool/releases) |

🤖 Content researched by AI. Last updated 2025-10-15.

- https://newproject.com
```

**After:**
```markdown
## General

| Project | Description | Open-Source | GitHub | Runtime | Released |
|---------|-------------|-------------|--------|---------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.2k) | 💻 CLI | [Mar 2024](https://github.com/user/example-tool/releases) |
| **[NewProject](https://newproject.com)** | Manages infrastructure deployments. | ✅ | [company/newproject](https://github.com/company/newproject) (⭐️ ~1.8k) | 🖥️ Binary | [Sep 2024](https://newproject.com/blog/launch) |

🤖 Content researched by AI. Last updated 2025-11-04.
```

Note: The star count was updated from ~3.0k to ~3.2k and the date was updated to today.

## Quality Guidlines

1. **Accuracy:** All information must be verified from reliable sources
2. **Consistency:** Follow the exact format specifications
3. **Neutrality:** Avoid promotional language
4. **Completeness:** Research all required fields
5. **Verification:** Double-check release dates with reliable sources, but approximate dates (month/year) are better than "Unknown"
6. **Timeliness:** Update all "Last updated" dates to current date when processing
7. **Spelling:** ALWAYS verify exact project name spelling from primary sources (copyright notices, legal documents) - NEVER rely solely on secondary sources like news articles
8. **Primary Product Focus:** Always identify and describe the MAIN/PRIMARY product, not auxiliary tools - use model knowledge + official website + docs to determine what the core product is

## Important Notes

- Process ALL unprocessed items in the README (all sections)
- Update star counts for ALL existing GitHub repositories
- For existing items: ONLY update the GitHub star count, do NOT modify any other fields
- Update ALL "Last updated" dates to today's date (both at the top of the document and below each table)
- Update the top-level "Content last updated" line near the beginning of README.md with today's date
- Be especially careful with release date research
- **CRITICAL:** Always focus on the PRIMARY/MAIN product - check official website homepage and use your model knowledge to identify what the core product is (not auxiliary tools)
- Maintain consistent formatting throughout
