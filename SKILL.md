---
name: smart-job-hunter
description: "Scans resume, searches for matching jobs, filters by hard requirements, and exports to Notion."
allowed-tools: ["read_file", "web_search", "fetch_url", "browser", "exec", "message", "notion"]
---

# Workflow

## 1. Initial Inquiry
Ask the user for:
- Expected job title(s)
- Earliest start date
- Location (Overseas / China)
- Work authorization (sponsorship needed?)

Wait for user input before proceeding.

## 2. Platform Selection
- **Overseas** (UK/US/Europe): LinkedIn, Indeed, Google Jobs
- **China**: LinkedIn China, Boss直聘 (via Google search)

## 3. Resume Processing
Prompt the user to upload their resume (PDF). Use `read_file` to extract:
- Core skills (technical + soft)
- Total years of experience
- Graduation year
- Education level (Bachelor/Master/PhD)

## 4. Eligibility Rules
Define strict filters BEFORE searching:
- **Max experience required**: If JD requires 3+ years and user has <1 year → discard
- **Graduation year**: If JD requires 2027/2028 grad but user is 2026 → discard
- **Degree requirement**: If JD requires PhD but user has Master's → discard
- **Work authorization**: If JD needs sponsorship and user can't get it → discard
- **Job type**: Exclude contractor/permanent mismatch if user wants permanent

## 5. Targeted Search
Use browser or web_search to find jobs:
- Search by job title + location
- Filter by "Intern" or "Entry Level" or "Graduate"
- **Sort by date** - prioritize jobs posted within last 7 days
- Get top 10 relevant listings

## 6. Availability Check (IMPORTANT)
Before adding to Notion, **double-check each job is still open**:
- Click the job link and verify it says "正在招聘" / "Hiring" / "Accepting applications"
- **Discard if**: "职位已关闭" / "Job Closed" / "Expired" / "No longer accepting applications"
- Skip jobs that require login to view details - mark as "需要登录" and note in notes

**Pro tips:**
- Jobs posted >7 days ago have higher chance of being closed - always verify
- If search results show "5天前" / "1周前" but job link shows "职位已关闭" → still discard
- Only add jobs that clearly show "招聘中" / "Hiring"

## 7. Hard Requirement Filtering
For each job, analyze the JD and **discard** if:
- Required years > user's actual experience + 1 year buffer
- Graduation year specified and doesn't match
- PhD required (for Master's students)
- Requires 3+ years experience
- Work authorization mismatch

Keep only **eligible** jobs.

## 8. Match Analysis
For each remaining job, add notes explaining:
- How the user's skills match the job requirements
- Why this is a good fit
- Any gaps to address in cover letter

## 9. Anti-Bot Protocol
If `fetch_url` returns 403 or blocked:
- Use browser tool to navigate directly
- Fall back to Google search with site: operator
- Slow down requests to avoid rate limiting

## 10. Notion Export
Export to Notion database with fields:
- **Job Title**: Position name
- **Company**: Company name
- **Status**: Wishlist / Applied / Interview / Offer / Rejected
- **Link**: Application URL
- **Requirements**: Key requirements from JD
- **Notes**: Match analysis (skills match, why apply, any gaps)
- **Date Applied**: (fill when user applies)

## 11. User Summary
Send WhatsApp message summarizing:
- Number of jobs found
- Number eligible after filtering
- Top 3 recommended positions
- Link to Notion for full list
