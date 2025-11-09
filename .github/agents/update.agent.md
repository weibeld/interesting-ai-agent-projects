---
name: Update Agent
description: Researches unprocessed items and updates the README with the results
---

# AI Agent Instructions: Research and Format Project Entries

## Overview

Your task is to research and format AI agent project entries in the README.md file. You will:
1. Process unprocessed items (bullet points with URLs) and convert them into formatted table entries
2. Update GitHub star counts for existing entries
3. Maintain the Table of Contents
4. Update the last update date

## Table Format

Each section should have a table with the following columns:

```markdown
| Project | Description | Open-Source | GitHub | Type | Released |
|---------|-------------|-------------|------|------|----------|
```

### Column Specifications

**Project:**
- Format: `**[Project Name](URL)**` or `**[Project Name](URL)** (by Organization)`
- Make the link bold
- **Parent organization - only add for well-known organizations:**
  - Only add `(by Organization)` if the parent company/organization is well-known (e.g., Google, AWS, ByteDance, Microsoft, Meta, etc.)
  - Well-known means: major tech companies, organizations with many other widely-used projects, or household names
  - Do NOT add for lesser-known companies or startups that most people wouldn't recognize
  - Examples where you SHOULD add: `**[NotebookLM](url)** (by Google)`, `**[TRAE](url)** (by ByteDance)`, `**[Amazon Bedrock AgentCore Memory](url)** (by AWS)`
  - Examples where you should NOT add: small startups, unknown companies, individual developers
  - When in doubt, omit the organization unless it's clearly a major well-known entity
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

**Type:**
- Use emoji icons based on the type of software:
  - 💻 CLI Tool: Command-line interface tool (runs in terminal)
  - 📊 Desktop App: Application installed locally with graphical interface (e.g., desktop IDE or editor)
  - 🧩 Plugin/Extension: Extension or plugin for existing software (e.g., IDE extensions, browser plugins)
  - 🌍 Web App: Web-based application (accessed through a browser)
  - 🔌 API: Service that provides an API as its main contribution (e.g., REST API, GraphQL API) without a primary GUI, designed to be accessed programmatically by other software
  - 🧰 SDK: Software development kit or framework for building software, not runnable software itself (e.g., Claude Agent SDK, development libraries)
- If a project supports multiple types, include all applicable emoji icons (e.g., `💻 CLI Tool, 🌍 Web App`)
- **Distinguishing between types:**
  - **API vs Web App:** If the main functionality is an API endpoint (accessed programmatically), use API. If the main functionality is a web interface to be used by users, use Web App
  - **SDK vs CLI Tool:** If it's a library/framework for building apps (imported/used as dependency), use SDK. If it's an executable tool run from command line, use CLI Tool

**Released:**
- Format: `[Mon YYYY](source-url)`
- Example: `[Oct 2025](https://news.ycombinator.com/item?id=12345)`
- Link to a reliable source documenting the release date
- **For open-source projects with GitHub repos, check releases/tags FIRST:**
  - **IF you are the GitHub Copilot coding agent AND have `github-mcp-server/list_releases` and `github-mcp-server/list_tags` tools:**
    - Use `github-mcp-server/list_releases` to get all releases and find the FIRST/oldest one
    - Use `github-mcp-server/list_tags` to get all tags and find the FIRST/oldest one
  - **ELSE IF you have other GitHub MCP server tools for releases/tags:** Use those tools
  - **ELSE:**
    - Use WebFetch on GitHub releases page: `github.com/user/repo/releases`
    - Use WebFetch on GitHub tags page: `github.com/user/repo/tags`
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

### 2. Type
- **CRITICAL:** Identify the PRIMARY/MAIN product, not auxiliary tools
  - Start with official website - what does the homepage promote?
  - Use your model knowledge - ask yourself "What is [Product Name]?"
  - Check documentation (Docs link) - look for "What is...?", "Introduction", "Quickstart" sections
  - Example: TRAE's main product is a Desktop App IDE, even though they also have a separate "Trae Agent" CLI tool
- Determine what TYPE the PRIMARY product is:
  - **💻 CLI Tool:** Runs in a terminal/command line
  - **📊 Desktop App:** Application installed locally with graphical interface (e.g., IDE, editor)
  - **🧩 Plugin/Extension:** Extension for existing software (e.g., VS Code extension, browser plugin)
  - **🌍 Web App:** Web-based service accessed through a browser
  - **🔌 API:** Service providing an API as main contribution (REST, GraphQL, etc.), accessed programmatically, no primary GUI
  - **🧰 SDK:** Framework or library for building software, not runnable software itself (development kits, libraries)
- If the PRIMARY product supports multiple types, list all applicable types
- Do NOT classify based on auxiliary/secondary tools in the ecosystem

### 3. Open-Source Status
- Is the code publicly available?
- Check for GitHub, GitLab, or other public repositories

### 4. GitHub Repository
- If open-source, find the GitHub repository URL
- **Get the current star count:**
  - **IF you are the GitHub Copilot coding agent** (https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent) **AND** you have the `github-mcp-server/search_repositories` tool available:
    - Use the `github-mcp-server/search_repositories` tool to retrieve the star count
    - Extract the `stargazers_count` field from the response
  - **ELSE IF you have another GitHub MCP server tool** that can retrieve repository information:
    - Use that tool to get the star count
  - **ELSE:**
    - Use the public GitHub API (e.g., `https://api.github.com/repos/OWNER/REPO`)
    - OR use WebFetch to scrape the GitHub repository web page
- Format as `user/repo` with star count

### 5. Release Date
- **CRITICAL:** Take extra care when researching release dates
- **Priority: Find at least the month/year** - this is better than "Unknown"
- Sources to check (in order of reliability):
  1. **For open-source projects:** GitHub releases/tags (use date of FIRST release/tag)
     - **IF you are the GitHub Copilot coding agent AND have `github-mcp-server/list_releases` and `github-mcp-server/list_tags` tools:**
       - Use `github-mcp-server/list_releases` to get all releases and find the FIRST/oldest one
       - Use `github-mcp-server/list_tags` to get all tags and find the FIRST/oldest one
     - **ELSE IF you have other GitHub MCP server tools for releases/tags:** Use those tools
     - **ELSE:**
       - Use WebFetch on `github.com/user/repo/releases`
       - Use WebFetch on `github.com/user/repo/tags`
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
   - **For star counts:**
     - **IF you are the GitHub Copilot coding agent AND have `github-mcp-server/search_repositories` tool:** Use that tool (extract `stargazers_count` field)
     - **ELSE IF you have another GitHub MCP server tool:** Use that tool
     - **ELSE:** Use public GitHub API (`https://api.github.com/repos/OWNER/REPO`) OR use WebFetch on the web interface (`github.com/user/repo`)
   - **For release dates:**
     - **IF you are the GitHub Copilot coding agent AND have `github-mcp-server/list_releases` and `github-mcp-server/list_tags` tools:**
       - Use `github-mcp-server/list_releases` to get all releases and find the FIRST/oldest one
       - Use `github-mcp-server/list_tags` to get all tags and find the FIRST/oldest one
     - **ELSE IF you have other GitHub MCP server tools for releases/tags:** Use those tools
     - **ELSE:**
       - Use WebFetch on `github.com/user/repo/releases` for release dates
       - Use WebFetch on `github.com/user/repo/tags` for version tags
     - Look for FIRST release/tag to determine launch date
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

1. **Get the current star count for each repository:**
   - **IF you are the GitHub Copilot coding agent AND have `github-mcp-server/search_repositories` tool:** Use that tool to retrieve star counts (extract `stargazers_count` field)
   - **ELSE IF you have another GitHub MCP server tool:** Use that tool to get star counts
   - **ELSE:** Use the public GitHub API (`https://api.github.com/repos/OWNER/REPO`) OR use WebFetch to scrape the repository web page
2. Update the star count in the format `(⭐️ ~X.Xk)` or `(⭐️ ~X)` (rounded to one decimal place for thousands)
3. ONLY update the GitHub star count. Do NOT change any other fields (project name, description, type, release date, etc.)

## Handling Mixed Processed and Unprocessed Items

A section may contain:
- **Only unprocessed items** (bullet list): Create a new table
- **Only processed items** (table): Update star counts
- **Both processed and unprocessed items** (table + bullet list): Add new rows to the existing table

When a table already exists:
1. Add new rows to the existing table for unprocessed items
2. Insert new entries in the correct position according to the project ordering rules (see "Project Ordering" section)
3. Remove the bullet points after adding them to the table

## Project Ordering

Within each table, projects must be ordered as follows:

1. **First: All open-source projects with GitHub repositories**
   - Ordered by star count (highest to lowest)
   - Example: A project with ~42.8k stars comes before one with ~5.2k stars

2. **Second: All closed-source projects (no GitHub repo)**
   - Ordered by release date (newest to oldest)
   - Example: Oct 2025 comes before Jan 2025

When adding new entries to an existing table, insert them in the correct position according to these rules, not just at the end.

## Table of Contents Maintenance

The README has a "## Contents" section that must be kept up to date:

1. List all level-2 headings (##) in the README, excluding "Contents" itself
2. Use an ordered list with bold section names
3. Format as markdown links: `1. **[Section Name](#section-anchor)**`
4. Convert section names to GitHub anchor format:
   - Lowercase all letters
   - Replace spaces with hyphens
   - Remove special characters
   - Number the sections (1. Agents, 2. Agent Memory, etc.)
   - Example: "Agent Memory" → `#agent-memory`
5. Keep it single-level (only ## headings, not ### subheadings)

Example:
```markdown
## Contents

1. **[Agents](#agents)**
2. **[Agent Memory](#agent-memory)**
```

## Section Navigation Links

At the end of each level-2 section (##), after all subsections and tables, add a navigation link back to the Table of Contents:

```markdown
⬆️ [Back to Contents](#contents)
```

This should appear after the last subsection's table in each main section.

## Final Steps

After processing all items:

1. Remove all processed bullet points
2. Ensure all projects within each table are ordered correctly (open-source by stars desc, then closed-source by date desc)
3. Add "⬆️ [Back to Contents](#contents)" link at the end of each level-2 section
4. Update the Table of Contents:
   - Use ordered list format (1., 2., etc.)
   - Make section names bold
   - Format: `1. **[Section Name](#section-anchor)**`
5. Update the top-level line near the beginning of README.md to today's date
   - Format: `> **✨🤖 The contents of this file have been researched by AI. ✅ Last updated: YYYY-MM-DD.**`
   - Use today's date in ISO format (YYYY-MM-DD)

## Final Commit Message Format

**IMPORTANT:** After completing ALL updates to the README, create ONE FINAL commit that summarizes all the work done. This is the LAST commit you make. You may have made other commits during your work, but this final commit must follow the format below.

### Message Structure

```
Perform update

Added projects:
- Added: [ProjectName] ([URL])
- Added: [ProjectName] ([URL])

Other changes:
- Updated star counts for N open-source projects
- Updated Table of Contents
- Reordered projects by star count and release date
- Updated last updated date to YYYY-MM-DD
```

### Important Guidelines

1. **Use "Added:" prefix for each project**
   - Format: `- Added: [ProjectName] ([URL])`
   - This allows unambiguous searching (e.g., searching for "Added: Mem0" will find exactly when Mem0 was added)
   - Use the exact project name as it appears in the README (with correct capitalization and spacing)

2. **List ALL added projects**
   - Include every project that was converted from bullet points to table entries during this update session
   - List them in the order they appear in the README (by section)

3. **Summarize other changes**
   - Mention if star counts were updated (and how many projects)
   - Note if Table of Contents was updated
   - Note if projects were reordered
   - Include the new "last updated" date

4. **Keep it concise but complete**
   - The commit message should be scannable
   - Someone reading commit history should immediately understand what was added

### Example

```
Perform update

Added projects:
- Added: Mem0 (https://mem0.ai/)
- Added: Supermemory (https://supermemory.ai/)
- Added: Amazon Bedrock AgentCore Memory (https://aws.amazon.com/bedrock/agentcore/)
- Added: myNeutron (https://myneutron.ai/)
- Added: Cognee (https://www.cognee.ai/)
- Added: MemOS (https://github.com/MemTensor/MemOS)

Other changes:
- Updated star counts for 5 open-source projects
- Reordered projects by star count and release date
- Updated last updated date to 2025-11-07
```

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

| Project | Description | Open-Source | GitHub | Type | Released |
|---------|-------------|-------------|--------|------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.2k) | 💻 CLI Tool | [Mar 2024](https://github.com/user/example-tool/releases) |
| **[AnotherTool](https://another-tool.io)** | Creates automated workflows for development teams. | ❌ | ❌ | 🌍 Web App | [Jan 2025](https://news.ycombinator.com/item?id=12345) |
```

### Example 2: Existing Table with New Unprocessed Items

**Before:**
```markdown
## General

| Project | Description | Open-Source | GitHub | Type | Released |
|---------|-------------|-------------|--------|------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.0k) | 💻 CLI Tool | [Mar 2024](https://github.com/user/example-tool/releases) |

- https://newproject.com
```

**After:**
```markdown
## General

| Project | Description | Open-Source | GitHub | Type | Released |
|---------|-------------|-------------|--------|------|----------|
| **[ExampleTool](https://example.com/tool)** | Helps with testing. | ✅ | [user/example-tool](https://github.com/user/example-tool) (⭐️ ~3.2k) | 💻 CLI Tool | [Mar 2024](https://github.com/user/example-tool/releases) |
| **[NewProject](https://newproject.com)** | Manages infrastructure deployments. | ✅ | [company/newproject](https://github.com/company/newproject) (⭐️ ~1.8k) | 📊 Desktop App | [Sep 2024](https://newproject.com/blog/launch) |
```

Note: The star count was updated from ~3.0k to ~3.2k.

## Quality Guidelines

1. **Accuracy:** All information must be verified from reliable sources
2. **Consistency:** Follow the exact format specifications
3. **Neutrality:** Avoid promotional language
4. **Completeness:** Research all required fields
5. **Verification:** Double-check release dates with reliable sources, but approximate dates (month/year) are better than "Unknown"
6. **Timeliness:** Update the Table of Contents and top-level "Last updated" date when processing
7. **Spelling:** ALWAYS verify exact project name spelling from primary sources (copyright notices, legal documents) - NEVER rely solely on secondary sources like news articles
8. **Primary Product Focus:** Always identify and describe the MAIN/PRIMARY product, not auxiliary tools - use model knowledge + official website + docs to determine what the core product is

## Important Notes

- Process ALL unprocessed items in the README (all sections and subsections)
- Update star counts for ALL existing GitHub repositories
- For existing items: ONLY update the GitHub star count, do NOT modify any other fields
- Update the Table of Contents to reflect all current level-2 sections
- Update the top-level line near the beginning of README.md with today's date (format: `> **✨🤖 Note: the content of this file has been researched by AI. Last updated YYYY-MM-DD.**`)
- Be especially careful with release date research
- **CRITICAL:** Always focus on the PRIMARY/MAIN product - check official website homepage and use your model knowledge to identify what the core product is (not auxiliary tools)
- Maintain consistent formatting throughout
