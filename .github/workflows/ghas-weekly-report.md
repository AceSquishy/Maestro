---
emoji: 🛡️
name: GHAS Weekly Report
description: Weekly report on all GitHub Advanced Security findings categorized by severity with detailed context
on:
  schedule: weekly on monday around 9am UTC
permissions:
  contents: read
  security-events: read
  issues: read
  pull-requests: read
  vulnerability-alerts: read
tools:
  github:
    mode: gh-proxy
    toolsets: [default, code_security, secret_protection, dependabot]
safe-outputs:
  create-issue:
---

# GHAS Weekly Security Report

## Task

Generate a comprehensive weekly report of all GitHub Advanced Security (GHAS) findings in this repository, categorized by severity. Create a GitHub issue with the report.

## Instructions

1. **Collect all GHAS findings** from the following sources:
   - Code scanning alerts (CodeQL and any other tools)
   - Secret scanning alerts
   - Dependabot alerts

2. **Categorize findings by severity** using the following sections:
   - 🔴 **Critical**
   - 🟠 **High**
   - 🟡 **Medium**
   - 🔵 **Low**
   - ⚪ **Informational / Advisory**

3. **For each finding, include the following context:**
   - Alert title and description
   - Severity level
   - Tool or source that detected it (e.g., CodeQL, Dependabot, Secret Scanning)
   - File path and line number where the vulnerability was found
   - The rule or CWE identifier (if available)
   - When it was first detected
   - Current state (open, dismissed, fixed)
   - A brief explanation of the vulnerability and its potential impact
   - Suggested remediation if available from the alert data

4. **Report structure:**
   - Start with an executive summary showing total counts per severity
   - Include a breakdown table: severity | count | source
   - Then list each finding grouped by severity with full context
   - Use `<details><summary>...</summary>` blocks for individual findings to keep the report readable
   - End with a trends section comparing to the previous week if data is available

5. **Report formatting:**
   - Use GitHub-flavored markdown
   - Start nested headings at `###`
   - Include timestamps for when the report was generated
   - Title the issue: "🛡️ Weekly GHAS Security Report - [date]"
   - Add labels: `security`, `report`, `automated`

## Safe Outputs

- Use `create-issue` to publish the weekly security report as a new GitHub issue.
- Use `noop` with a short explanation if there are no GHAS findings to report.
