AI-Powered Viral Video Generator and YouTube Auto-Uploader

Overview

This n8n workflow automates viral short-form video creation from text ideas. It generates cinematic "found footage" prompts using AI, creates videos with Sora AI, generates optimized YouTube titles, and automatically uploads to YouTube.

What This Workflow Does

Users submit a video idea through a web form, AI generates a detailed cinematic prompt, creates an optimized YouTube title with hashtags, generates the video using Sora AI, retrieves the completed video, and automatically uploads it to YouTube.

Key Features

One-Click Video Creation - From idea to published video automatically
Cinematic Prompt Generation - Creates detailed found footage style prompts (500-2000 characters)
AI Title Optimization - Generates viral titles under 100 characters with hashtags
Sora AI Integration - Text-to-video generation via KIE.ai API
Automatic YouTube Upload - Publishes directly to your channel
Form-Based Input - Simple web form for video ideas

Use Cases

Content Creators - Automate YouTube Shorts production
Social Media Managers - Generate multiple viral videos quickly
Marketing Teams - Create engaging promotional content at scale
Entertainment - Generate horror, mystery, or thriller content

Workflow Architecture

Form Trigger - Captures video idea through web form
AI Prompt Generator (Gemini) - Creates detailed cinematic found footage prompt
Title Generator (Gemini) - Creates viral-optimized YouTube title with hashtags
Video Generation (KIE.ai) - Sends prompt to Sora AI model
Video Retrieval - Gets completed video download URL
YouTube Upload - Publishes video with generated title

Prerequisites

Required Services

n8n instance (version 1.0+)
Google Gemini API account
KIE.ai API account with Sora access
YouTube account with API enabled
Google Cloud Console project with YouTube Data API v3

Required Credentials

Google Gemini API Key
KIE.ai API Bearer Token
YouTube OAuth2 Credentials

Installation Steps

Import Workflow - Download and import JSON into n8n
Configure Google Gemini - Add API key in both Gemini Chat Model nodes
Configure KIE.ai - Add Bearer Token in HTTP Request headers
Configure YouTube - Add OAuth2 credentials in Upload node
Test Form - Access webhook URL and submit test idea

Video Prompt Generation Rules

Mandatory Elements

Settings: abandoned town, research facility, deep ocean base, remote forest, mountain outpost, empty subway, desert ruins, forgotten bunker
Objects: flashlight, old camera, flickering light, damaged radio, steel door, wristwatch, notebook, broken drone
Sounds: low-frequency hum, static noise, footsteps, metal creaking, distant alarm, wind, faint voice
Camera Style: handheld, grainy, slightly shaky, timestamped, natural lighting, imperfect focus

Dialogue Requirements

English only, natural and reactive
Examples: "What was that sound?", "Did you see it move?", "Run. Now!"

Output Specifications

Length: 500-2000 characters
Format: Flowing paragraph, no bullet points
Tone: Cinematic, tense, believable
Includes: Timestamps, reactions, ambient sounds, camera motion

Example Output

Grainy 9:16 vertical footage. 00:07 - two explorers enter a dark research corridor. The floor is wet, reflecting dim emergency lights. "Keep recording," one whispers. 00:15 - a metallic sound echoes. Camera shakes. "Who's there?" The focus blurs on a steel door slowly opening. 00:21 - static. A shadow moves past the lens. "Run!" someone shouts. 00:25 - camera drops, showing boots splashing through water before cutting to black.

Title Generation Rules

Maximum 100 characters total
Video title under 20 characters
Includes: viralshort, shorts, viral hashtags
Optimized for YouTube Shorts algorithm

Video Generation Settings

Model: sora-2-text-to-video
Aspect Ratio: landscape (change to 9:16 for vertical shorts)
Frame Count: 10 frames (adjustable)
Watermark Removal: enabled

API Configuration

KIE.ai Create Task

URL: https://api.kie.ai/api/v1/jobs/createTask
Method: POST
Authorization: Bearer token
Parameters: model, prompt, aspect_ratio, n_frames, remove_watermark

KIE.ai Record Info

URL: https://api.kie.ai/api/v1/jobs/recordInfo
Method: GET
Query: taskId
Returns: video status, download URL

Customization Options

Change Video Style - Modify AI Agent system message for different genres
Adjust Video Length - Change n_frames parameter
Change Aspect Ratio - Update to "9:16" for vertical shorts or "square" for Instagram
Add More Hashtags - Edit title generator system message

Workflow Execution Example

User submits: "A mysterious abandoned space station"
AI generates detailed found footage prompt with dialogue
AI creates title: "Lost in Space viralshort shorts viral"
System sends to KIE.ai for video generation
Retrieves completed video URL
Uploads to YouTube automatically

Troubleshooting

Form Not Submitting - Check webhook URL accessibility
Prompt Generation Failed - Verify Gemini API key and quota
Video Generation Errors - Confirm KIE.ai token and account balance
Video Not Retrieved - Allow time for generation, check taskId
YouTube Upload Failed - Verify OAuth2 credentials and API quota
Title Too Long - Adjust character limits in system message

Performance Optimization

Use fewer frames for faster generation
Simplify prompt complexity
Set daily execution limits
Monitor API usage and costs
Implement approval step before generation

Best Practices

Prompt Writing

Be specific about setting and mood
Include sensory details and realistic dialogue
Use timestamps for pacing
Stay within 500-2000 character limit

Title Creation

Front-load important keywords
Keep core title under 20 characters
Include trending hashtags
Test variations for performance

Content Strategy

Generate variations of successful concepts
Track performance metrics
Maintain consistent posting schedule
Review videos before publishing

Security

Store API keys in n8n credential manager
Use OAuth2 for YouTube access
Rotate keys regularly
Monitor API usage for unauthorized access
Ensure content meets YouTube guidelines

Integration Possibilities

Social Media - Add Instagram Reels, TikTok, Facebook posting
Analytics - Connect Google Analytics for tracking
Storage - Save videos to Google Drive or Dropbox
Collaboration - Add approval workflows and team notifications

Future Enhancements

Multiple video style presets
Custom thumbnail generation
Automated A/B testing
Voice-over generation
Background music integration
Multi-language support
Scheduled publishing
Batch video generation

Contributing

Fork repository, create feature branch, test thoroughly, document changes, and submit pull request.

License

MIT License - Free for personal and commercial use.

Support

Open issues for questions or feature requests in this repository.

Built With

n8n workflow automation
Google Gemini AI for content generation
KIE.ai Sora API for video creation
YouTube Data API v3 for uploads
