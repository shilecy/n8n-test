# n8n Workflow: AI-Generated Video to Facebook Publishing
## Workflow Overview

This workflow automates the end-to-end process of generating AI-driven video content and publishing it to a Facebook Page. The workflow includes idea generation, video production, logging, and final social media publishing. 

Note: This workflow is a mock video generation (without a real Veo3 (paid tier) video generation) that simulate real video generation to FB page posting via n8n. Video is stored in GitHub and push to FB page.

## Nodes in Workflow:

1. Manual Trigger – Starts the workflow on demand.

2. AI Agent: Generate Idea – Uses Gemini AI to generate video concepts, titles, and captions.
   AI Subnodes (2A, 2B) – Auxiliary AI processing for prompt refinement and metadata generation.

4. Flatten AI output to be parsed to Gsheet.

5. Google Sheets: Log Idea – Appends generated video ideas, title, and caption to a Google Sheet for record-keeping.

6. Veo 3: Generate Video – Sends the AI-generated prompt to Veo 3 (or mock endpoint) to generate the video. (simulate)

7. Processing / Wait – Wait node simulates the video generation process for asynchronous handling. (simulate)

8. Get Video URL / ID – Retrieves the generated video URL or ID from Veo 3. (simulate)

9. Video Ingestion – Prepares the video for publishing (this case: downloading from GitHub raw URL or internal storage). (simulate)

10. Facebook: Publish – Posts the video to a connected Facebook Page, using title and caption metadata.

## Assumptions & Notes

Veo 3: For the demo, a mock endpoint is used; in production, the actual Veo 3 API would generate real videos.

Facebook Access Token: A Page access token is required with the pages_manage_posts and pages_read_engagement permissions.

Video URL: Videos are hosted on GitHub raw URLs to simplify ingestion. No public hosting or Google Drive API is required.

AI Metadata: Title, caption, and prompts are passed from the AI agent to subsequent nodes; care was taken to preserve this data to avoid loss between nodes.

## Setup Instructions

Import the provided .json workflow into n8n.

Configure credentials:

Google Sheets – API credentials for appending and updating rows. (please use your gsheet)

Facebook Graph API – Page access token. (must create your own fb page)

AI Agent – Gemini API Key or OAuth setup. (set your own api key)

Video upload to GitHub (use raw url).

(Optional) Adjust Veo 3 endpoint to real API when available.

Run the workflow using the Manual Trigger.

Confirm video posts appear on the Facebook Page.

## Potential Improvements

LinkedIn Publishing – Extend workflow to also post videos to LinkedIn Pages.

Error Handling – Add retry or fallback nodes for Veo 3 video generation and HTTP errors.

Scheduling – Automate idea generation and publishing at defined intervals using the Cron node.

Parameterization – Make Page IDs, sheet URLs, and video URLs dynamic for multiple campaigns.

## Deliverables

Workflow Video Demo – Screen recording showing the workflow execution, Gsheet update and Facebook post. (Veo3 to FB.webm)

Exported n8n Workflow JSON – .json file for import and testing. (Veo3 to FB post.json)

Short Documentation – This 1–2 page brief explaining workflow, assumptions, and credentials. (README.md)
