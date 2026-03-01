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

## Setup

1. Clone this repository or copy the `SKILL.md` file
2. Configure Notion API:
   - Create an integration at https://www.notion.so/my-integrations
   - Share a page with the integration
   - Save the API key

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
