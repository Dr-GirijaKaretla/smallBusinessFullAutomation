```mermaid
flowchart TD

A[Google Drive Uploads] --> B[Drive Webhook API]

B --> C[Multi-Agent System]

C --> C1[Flyer Agent]
C --> C2[Video Clip Agent]
C --> C3[Website Agent]
C --> C4[Payment Agent]
C --> C5[Scheduler Agent]

C1 --> S3[AWS S3 Storage]
C2 --> S3

C1 --> SM[Instagram/Facebook/YouTube]
C2 --> SM

C4 --> STRIPE[Stripe Webhooks]

S3 --> FE[Frontend Website]

