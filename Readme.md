# 🎙️ AI Voice Booking Agent for suzie Hair Beauty

An automated, low-latency Voice AI solution designed to handle inbound salon inquiries, validate client data, and manage bookings autonomously.

## 🚀 Overview
This project integrates **Retell AI** for natural language voice processing and **n8n** for backend workflow automation. It bridges the gap between customer calls and administrative management by automatically logging appointments into Google Sheets.

## ✨ Key Features
* **Natural Language Interaction:** Context-aware AI agent that handles greetings, service inquiries, and booking requests.
* **Strict Data Validation:** Implemented regex-based validation to ensure only valid **10-digit Australian phone numbers** are processed, eliminating data entry errors.
* **Hallucination Control:** Fine-tuned system prompts to keep the agent strictly focused on salon services and booking rules.
* **Real-time Synchronization:** End-to-end automation where call data is pushed to Google Sheets via n8n webhooks immediately after a call ends.
* **Low Latency:** Optimized STT (Speech-to-Text) and LLM orchestration to provide human-like response times.

## 🛠️ Tech Stack
* **Voice Orchestration:** Retell AI
* **Workflow Automation:** n8n
* **Database/Storage:** Google Sheets API
* **Validation:** Regex & Custom n8n Logic

## 🏗️ System Architecture
1. **Inbound Call:** Customer calls the salon number managed by Retell AI.
2. **Voice Processing:** Retell handles the conversation using LLM logic.
3. **Webhook Trigger:** Upon call completion, Retell sends a JSON payload to an n8n webhook.
4. **Data Extraction:** n8n parses the name, 10-digit phone number, and booking time.
5. **Persistence:** The validated data is appended as a new row in the Salon's Booking Google Sheet.

## 🐞 Challenges Overcome: The "Hardest Bug"
The primary challenge was managing **asynchronous data persistence**. Occasionally, if a user hung up abruptly, the webhook would fail to trigger before the LLM could extract final details. I resolved this by implementing an asynchronous post-call processing logic in n8n that captures partial data and ensures no lead is lost, even during interrupted sessions.

## 📺 Demo
Check out the live demo of the agent in action: [Watch on YouTube](https://youtu.be/FbwpecrA5zc)

---
*Developed during my internship for Shijos Hair Beauty, Melbourne.*
