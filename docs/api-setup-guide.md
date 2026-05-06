# 🔧 API Setup Guide

This guide explains how to configure all required APIs for the AI Business Automation Platform.

---

## 1. Google Drive API (Uploads Trigger)

### Steps:
1. Go to Google Cloud Console  
2. Create a new project  
3. Enable:
   - Google Drive API  
   - Google OAuth 2.0  
4. Create OAuth Credentials:
   - OAuth Client ID  
   - OAuth Client Secret  
5. Create API Key  
6. Add redirect URIs for your backend

### Save to `.env`:
- GOOGLE_CLIENT_ID  
- GOOGLE_CLIENT_SECRET  
- GOOGLE_DRIVE_API_KEY  

---

## 2. Gemini API (LLM)

### Steps:
1. Go to Google AI Studio  
2. Create API Key  
3. Enable Gemini 1.5 Flash  

### Save to `.env`:
- GEMINI_API_KEY  

---

## 3. Meta Graph API (Instagram + Facebook)

### Steps:
1. Go to Meta Developers  
2. Create an App  
3. Add:
   - Instagram Basic Display  
   - Instagram Content Publishing  
   - Facebook Pages  
4. Generate:
   - App ID  
   - App Secret  
   - Page Access Token  
   - Instagram Business Token  

### Save to `.env`:
- META_APP_ID  
- META_APP_SECRET  
- META_PAGE_ACCESS_TOKEN  
- META_IG_ACCESS_TOKEN  

---

## 4. YouTube Data API

### Steps:
1. Go to Google Cloud Console  
2. Enable YouTube Data API v3  
3. Create:
   - API Key  
   - OAuth Client ID  
   - OAuth Client Secret  

### Save to `.env`:
- YOUTUBE_API_KEY  
- YOUTUBE_CLIENT_ID  
- YOUTUBE_CLIENT_SECRET  

---

## 5. Stripe Payments

### Steps:
1. Create Stripe Account  
2. Go to Developers → API Keys  
3. Copy:
   - Publishable Key  
   - Secret Key  
4. Create Webhook Endpoint  
5. Copy Webhook Signing Secret  

### Save to `.env`:
- STRIPE_PUBLISHABLE_KEY  
- STRIPE_SECRET_KEY  
- STRIPE_WEBHOOK_SECRET  

---

## 6. AWS (Lambda, S3, SES, EventBridge)

### Steps:
1. Create IAM User  
2. Enable:
   - Lambda  
   - S3  
   - SES  
   - EventBridge  
3. Generate:
   - Access Key  
   - Secret Key  

### Save to `.env`:
- AWS_ACCESS_KEY  
- AWS_SECRET_KEY  
- AWS_REGION  

---

## 7. Firebase (Database)

### Steps:
1. Create Firebase Project  
2. Enable Firestore  
3. Generate Admin SDK Key  

### Save to `.env`:
- FIREBASE_PROJECT_ID  
- FIREBASE_ADMIN_KEY  

---

## 8. Twilio (Optional SMS)

### Steps:
1. Create Twilio Account  
2. Copy:
   - Account SID  
   - Auth Token  

### Save to `.env`:
- TWILIO_SID  
- TWILIO_AUTH_TOKEN  

---
