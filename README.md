# 🤖 Smart Job Hunter

An AI-powered job search assistant that helps you find relevant jobs based on your resume, filters by eligibility requirements, and exports to Notion.

## Features

- 📄 **Resume Analysis** - Upload your CV and get AI to extract skills, experience, and education
- 🔍 **Multi-Platform Search** - Searches LinkedIn, Indeed, Google Jobs, Boss直聘
- ✅ **Eligibility Filtering** - Automatically filters jobs based on:
  - Years of experience required
  - Graduation year requirements
  - Degree requirements (PhD/Master's/Bachelor's)
  - Work authorization / sponsorship
- 🔎 **Availability Check** - Verifies jobs are still open before adding
- 📝 **Match Analysis** - Explains why each job is a good fit
- 📊 **Notion Export** - Exports all relevant jobs to Notion with status tracking

## Platforms Supported

| Region | Platforms |
|--------|-----------|
| Overseas (UK/US/Europe) | LinkedIn, Indeed, Google Jobs |
| China | LinkedIn China, Boss直聘 |

## Setup

### 1. OpenCLAW Setup

If you don't have OpenCLAW yet:

```bash
# Install OpenCLAW
npm install -g openclaw

# Start the gateway
openclaw gateway start
```

### 2. Notion Setup

**Step 1: Create a Notion Integration**
1. Go to https://www.notion.so/my-integrations
2. Click **"+ New integration"**
3. Select **"Internal integration"** (NOT Public)
4. Give it a name (e.g., "Job Hunter")
5. Click **Create**
6. Copy the **Internal Integration Secret** (starts with `ntn_` or `secret_`)

**Step 2: Save the API Key**

Save your Notion API key:
```bash
mkdir -p ~/.config/notion
echo "YOUR_NOTION_API_KEY" > ~/.config/notion/api_key
```

**Step 3: Create a Notion Page for Job Tracking**
1. Create a new page in Notion (e.g., "Job Applications")
2. Click the **⋮** menu → **Connect to** → Select your integration
3. Create a database with these properties:
   - **Job Title** (Title)
   - **Company** (Text)
   - **Status** (Select: Wishlist / Applied / Interview / Offer / Rejected)
   - **Link** (URL)
   - **Requirements** (Text)
   - **Notes** (Text)
   - **Date Applied** (Date)

### 3. Add the Skill to OpenCLAW

```bash
# Copy the skill to your OpenCLAW workspace
mkdir -p ~/.openclaw/workspace/skills
cp -r smart-job-hunter ~/.openclaw/workspace/skills/

# Restart OpenCLAW gateway
openclaw gateway restart
```

## Usage

1. **Start a job search** - Tell the AI:
   - Expected job title(s)
   - Location
   - Earliest start date
   - Work authorization (sponsorship needed?)

2. **Upload your resume** - The AI will analyze your skills and experience

3. **Get matched jobs** - Receive a list of eligible jobs with match analysis

4. **Track in Notion** - All jobs are exported to Notion for easy tracking

## Notion Database Schema

Create a Notion database with these fields:

| Field | Type | Description |
|-------|------|-------------|
| Job Title | Title | Position name |
| Company | Text | Company name |
| Status | Select | Wishlist / Applied / Interview / Offer / Rejected |
| Link | URL | Application URL |
| Requirements | Text | Key requirements from JD |
| Notes | Text | Match analysis |
| Date Applied | Date | When you applied |

## Example

```
User: I want to find AI Product Manager jobs in London
AI: Sure! Let me ask a few questions:
- What's your expected job title?
- What's your location?
- When can you start?
- Do you need visa sponsorship?

User: AI Product Manager, London, June 2026, no sponsorship
AI: Great! I'll search for relevant jobs and filter by your eligibility.
```

## Contributing

Pull requests are welcome! Please feel free to submit issues.

## License

MIT
