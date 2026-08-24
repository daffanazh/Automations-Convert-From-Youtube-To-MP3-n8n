# RESTful API Orchestrator: Custom Webhook to WhatsApp Gateway

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/944a1767-f379-49f2-a0b1-0fba56bc1360" />

## Executive Summary
This project demonstrates a lightweight, high-performance API orchestration engine built in **n8n**. Utilizing pure HTTP protocols rather than pre-built application nodes, this workflow acts as a middleware server. It intercepts incoming POST payloads via Webhooks, processes conditional business logic, fetches external media via third-party APIs, and dynamically pushes the payload to a WhatsApp gateway (Fonnte) for automated messaging.

## Business Value
* **System Agnostic:** Can be triggered by any external application, website, or CRM capable of sending a standard POST request.
* **Low Latency & Scalable:** By bypassing bloated application nodes and using raw HTTP Requests, the execution time is minimized, making it ideal for high-volume transactional messages.
* **Conditional Message Routing:** Ensures the right payload is sent to the right endpoint, preventing system errors or irrelevant message delivery.
* **Seamless API Bridging:** Connects completely isolated systems (e.g., custom Web Apps, Media Converters, and WhatsApp) into one synchronized pipeline.

## System Architecture & API Pipeline
This workflow relies entirely on foundational web protocols to process and route data:

1. **Ingestion Endpoint (`Webhook`):** Acts as the entry point, listening for incoming `POST` payloads from an external source (such as a custom frontend or third-party CRM).
2. **Logic Gate (`If` Statement):** Evaluates the incoming JSON payload against predefined conditional rules to determine the correct execution path.
3. **Execution Branch - True (Media Processing):**
   * **Data Fetch (`HTTP Request - GET`):** Calls an external media API (e.g., a YouTube-to-MP3 converter) to retrieve dynamic media links or binary data based on the user's input.
   * **Data Dispatch (`HTTP Request - POST`):** Constructs a new payload containing the retrieved media and pushes it to the **Fonnte API** for WhatsApp delivery.
4. **Execution Branch - False (Standard Notification):**
   * **Direct Dispatch (`HTTP Request - POST`):** Bypasses the media fetch and immediately sends a standard text/notification payload directly to the Fonnte WhatsApp endpoint.

## Tech Stack
* **Workflow Engine:** n8n (Pure HTTP Orchestration)
* **API Integration:** Custom RESTful APIs, Fonnte API (WhatsApp Gateway)
* **Data Protocols:** JSON, Webhooks, GET/POST Methods
* **Architecture:** Middleware / API Bridge

---
*Architected for custom system integrations and high-speed data routing. Open for backend consulting and API development.*
