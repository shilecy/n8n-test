# n8n Workflow: AI-Generated Video to Facebook Publishing
## Workflow Overview

This workflow automates the end-to-end process of generating AI-driven video content and publishing it to a Facebook Page. The workflow includes idea generation, video production, logging, and final social media publishing.

## Nodes in Workflow:

1. Manual Trigger – Starts the workflow on demand.

2. AI Agent: Generate Idea – Uses Gemini AI to generate video concepts, titles, and captions.

3. AI Subnodes (2A, 2B) – Auxiliary AI processing for prompt refinement and metadata generation.

4. Google Sheets: Log Idea – Appends generated video ideas, title, and caption to a Google Sheet for record-keeping.

5. Veo 3: Generate Video – Sends the AI-generated prompt to Veo 3 (or mock endpoint) to generate the video.

6. Processing / Wait – Wait node simulates the video generation process for asynchronous handling.

7. Get Video URL / ID – Retrieves the generated video URL or ID from Veo 3.

8. Video Ingestion – Prepares the video for publishing (e.g., downloading from GitHub raw URL or internal storage).

9. Facebook: Publish – Posts the video to a connected Facebook Page, using title and caption metadata.

## Assumptions & Notes

Veo 3: For the demo, a mock endpoint is used; in production, the actual Veo 3 API would generate real videos.

Facebook Access Token: A Page access token is required with the pages_manage_posts and pages_read_engagement permissions.

Video URL: Videos are hosted on GitHub raw URLs to simplify ingestion. No public hosting or Google Drive API is required.

AI Metadata: Title, caption, and prompts are passed from the AI agent to subsequent nodes; care was taken to preserve this data to avoid loss between nodes.

## Setup Instructions

Import the provided .json workflow into n8n.

Configure credentials:

Google Sheets – API credentials for appending and updating rows.

Facebook Graph API – Page access token.

AI Agent – Gemini API Key or OAuth setup.

(Optional) Adjust Veo 3 endpoint to real API when available.

Run the workflow using the Manual Trigger.

Confirm video posts appear on the Facebook Page.

## Potential Improvements

LinkedIn Publishing – Extend workflow to also post videos to LinkedIn Pages or Profiles.

Error Handling – Add retry or fallback nodes for Veo 3 video generation and HTTP errors.

Scheduling – Automate idea generation and publishing at defined intervals using the Cron node.

Parameterization – Make Page IDs, sheet URLs, and video URLs dynamic for multiple campaigns.

## Deliverables

Workflow Video Demo – Screen recording showing the workflow execution and Facebook post.

Exported n8n Workflow JSON – .json file for import and testing.

Short Documentation – This 1–2 page brief explaining workflow, assumptions, and credentials.

Bonus – LinkedIn publishing integration (optional).
