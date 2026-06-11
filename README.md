# FraudGuard: Real-Time Fraud Detection & Notification Pipeline

FraudGuard is an automated financial risk evaluation and notification engine built using **n8n**. The pipeline reads incoming transaction streams, passes them through an isolated **JavaScript processing sandbox** to evaluate custom-defined fraud vectors, dynamically metrics a risk-score tier, updates a master Google Sheets database, and triggers instantaneous contextual email alerts via **Gmail API** for medium and high-risk flags.

---

## 🚀 System Architecture

The pipeline processes transaction items linearly through conditional evaluation blocks:

```text
[Manual/Webhook Trigger] 
          │
          ▼
 [Fetch Google Sheet Rows] 
          │
          ▼
 [Custom JavaScript Engine] ──► (Calculates Risk Score & Rules)
          │
          ▼
     [IF Block] ───(Risk Score ≥ 4)───► [Update Sheet: HIGH] ───► [Gmail Notification]
          │
          ▼ (False)
    [IF1 Block] ───(Risk Score ≥ 2)───► [Update Sheet: MEDIUM] ─► [Gmail Notification]
          │
          ▼ (False)
    [IF2 Block] ───(Risk Score == 1)──► [Update Sheet: LOW]
          │
          ▼ (False)
 [Update Sheet: CLEAR]
