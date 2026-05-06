# 📘 Architecture Overview — Automation Platform

**Version:** 1.0  
**Author:** Dr. Girija  
**Last Updated:** 07 May 2026  
**Status:** Active

---

# 🏗️ 1. System Overview

The Automation Platform is a serverless, event‑driven system designed to automate:

- Flyer generation  
- Video creation  
- Website updates  
- Payment reminders  
- WhatsApp notifications  
- Google Drive photo ingestion  
- Stripe payment events  
- Daily/weekly/monthly workflows  

The architecture is built on AWS, Google Cloud, and Stripe using a modular microservice approach.

---

# 🟦 2. High-Level Architecture Diagram (Text-Based)

┌──────────────────────────┐
│      EventBridge          │
│  (Daily / Weekly / Monthly)
└──────────────┬───────────┘
│
▼
┌────────────────────┐
│  scheduler-agent    │
│  (Lambda Function)  │
└──────────┬─────────┘
│
┌────────────────────────────────┼────────────────────────────────┐
▼                                ▼                                ▼
┌────────────────┐             ┌────────────────┐             ┌────────────────────┐
│  flyer-agent   │             │  video-agent   │             │  payment-agent      │
│ (Lambda)       │             │ (Lambda)       │             │ (Lambda)            │
└──────┬─────────┘             └──────┬─────────┘             └──────────┬─────────┘
│                                │                                 │
▼                                ▼                                 ▼
┌──────────────┐              ┌────────────────┐              ┌────────────────────┐
│ S3: Flyers   │              │ S3: Clips      │              │ WhatsApp API        │
└──────────────┘              └────────────────┘              └────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
▼                                                                      ▼
┌────────────────────────┐                                      ┌────────────────────────┐
│ drive-webhook-handler  │                                      │ stripe-webhook-handler │
│ (Lambda)               │                                      │ (Lambda)               │
└──────────┬─────────────┘                                      └──────────┬─────────────┘
│                                                                │
▼                                                                ▼
┌────────────────────────┐                                      ┌────────────────────────┐
│ Google Drive API       │                                      │ Stripe API             │
└────────────────────────┘                                      └────────────────────────┘


---

# 🟩 3. AWS Components

## 3.1 S3 Buckets
- `automation-flyers`
- `automation-clips`

Used for storing generated media.

---

## 3.2 Lambda Functions

| Function | Purpose |
|---------|----------|
| flyer-agent | Generate flyers using AI |
| video-agent | Generate short clips |
| website-agent | Update website content |
| payment-agent | Send fee reminders |
| scheduler-agent | Run daily/weekly/monthly tasks |
| drive-webhook-handler | Handle Google Drive events |
| stripe-webhook-handler | Handle Stripe events |

All Lambdas use:

automation-lambda-role


---

## 3.3 IAM Role

Role: `automation-lambda-role`

Policies:
- AWSLambdaBasicExecutionRole  
- AmazonS3FullAccess  
- CloudWatchFullAccess  

---

## 3.4 EventBridge Scheduler

Three schedules created:

| Schedule | Cron | Purpose |
|----------|------|---------|
| Daily | `0 8 * * ? *` | Daily automation |
| Weekly | `0 9 ? * MON *` | Weekly automation |
| Monthly | `0 7 1 * ? *` | Monthly automation |

All schedules target:

scheduler-agent

---

# 🟧 4. Google Cloud Components (Day 2)

Will include:

- Google Cloud Project  
- Drive API  
- YouTube API  
- OAuth credentials  
- Service accounts  
- Drive webhook  

---

# 🟨 5. Stripe Components (Day 3)

Will include:

- Webhook endpoint  
- Payment event handling  
- Invoice reminders  

---

# 🟪 6. Data Flow Summary

### Inbound Events
- Google Drive → drive-webhook-handler  
- Stripe → stripe-webhook-handler  
- EventBridge → scheduler-agent  

### Outbound Actions
- S3 uploads  
- WhatsApp messages  
- Website updates  
- YouTube uploads  

---

# 🟫 7. Security Considerations

- IAM least privilege  
- Encrypted S3 buckets  
- EventBridge minimal roles  
- No long-lived credentials in code  
- `.env` stored locally only  

---

# 🟦 8. Future Enhancements

- CI/CD deployment pipeline  
- RDS or DynamoDB for state tracking  
- Admin dashboard  
- Multi-tenant support  

---

# ⭐ End of Architecture Document


