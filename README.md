# Automated Personal Assistant for Educators (n8n + Docker + ngrok)

A lightweight automation system that helps teachers handle routine admin work—daily email summaries to Telegram, signature detection for attachments (with approval), and smart meeting scheduling that checks Google Calendar availability. 

## Features

Daily Gmail Summary → Telegram
Get a 24-hour digest of all incoming emails, summarized by AI and sent to Telegram.

Signature Detection & Approval
Automatically detect documents requiring signatures, ask for approval, then sign and reply.

Smart Calendar Helper
Parse dates and times from emails and check Google Calendar for conflicts.

Task Assignment via Telegram
Assign work directly to team members from Telegram, track tasks in real time.

## How it’s built

* **Main workflow** orchestrates Gmail triggers and routing
* **Child workflows** manage specialized tasks: (1) email summaries, (2) attachment and signature processing, (3) calendar conflict checks, and (4) task assignments via Telegram.
* **Stack:** n8n (workflows), Docker (deployment), ngrok (webhooks/OAuth), **DeepSeek** (AI tasks), Gmail/Sheets/Calendar + Telegram APIs

## Workflows (n8n)

Main Flow: Gmail trigger → classify → route to child flows

All Email Summarize Flow: DeepSeek summarize all emails → send to Telegram

Attachment Flow: Detect keywords/AI → ask for approval → sign → reply via Gmail

Check Event Flow: Parse proposed times → check Google Calendar for conflicts

Telegram Flow: Assign work → manage task approvals and updates via Telegram

