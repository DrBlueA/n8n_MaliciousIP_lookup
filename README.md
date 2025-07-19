![webhook](https://i.imgur.com/D6SP9P0.png)

## 🛡️ Workflow Overview: Real-Time Suspicious Login Detection

This n8n workflow is designed to detect and enrich suspicious login activity in real time using contextual data and external threat intelligence from MaliciousIP. Whether triggered manually for testing or via live webhook, it processes login attempts, scores the threat, and summarizes the findings using an LLM for rapid triage.

🔗 **MaliciousIP API documentation**:  
[https://documenter.getpostman.com/view/32449314/2sAYdZuZSn](https://documenter.getpostman.com/view/32449314/2sAYdZuZSn)  
[https://maliciousip.com/](https://maliciousip.com)

---

### 🔍 Key Features

- **Data Extraction**  
  Extracts IP address, user ID, timestamp, page URL, and user agent from the login payload.

- **Threat Enrichment**  
  Queries MaliciousIP using the extracted IP to gather:
  - Threat score
  - Known TTPs
  - ASN and geolocation data

- **Threat Evaluation**  
  Uses an IF node to check if the threat score is greater than 0 and routes to a LangChain LLM node for interpretation.

- **LLM-Powered Insight**  
  The `Basic LLM Chain` evaluates the context and returns an analyst-style summary — humorous if benign, actionable if malicious.

---

### ⚙️ Workflow Triggers

- **Webhook**: Listens for new login attempts at the `/login` path  
- **Manual Trigger**: Executes the workflow with a sample login event for testing

Once triggered, the flow continues with data parsing, enrichment, risk evaluation, and AI summarization. Alerts can be extended with Slack, email, or SOAR integrations as needed.

## 🧭 Workflow Overview

![Workflow Diagram](./workflow.png)


---

This setup demonstrates how n8n and MaliciousIP can work together to automate early detection and contextual interpretation of suspicious activity — no code required, and no analyst left in the dark.
