# Task 3 – Integration Design

## Overview

The landing page collects the user's name and phone number through a consultation form. Once the form is submitted, the data is first pushed to the `dataLayer`, allowing Google Tag Manager (GTM) to capture the event for analytics and marketing tracking.

The form data is then sent to the backend through an API endpoint. The backend validates the request and forwards the lead information to HubSpot CRM using the HubSpot Contacts API. HubSpot stores the lead and automatically creates or updates the contact based on business rules.

After a successful CRM insertion, a Google Ads Conversion event is triggered to measure campaign performance. The backend also sends a WhatsApp confirmation message using the Karix API, informing the user that their consultation request has been received.

---

## Data Flow

Landing Page

↓

Google Tag Manager (`dataLayer.push()`)

↓

Backend API

↓

HubSpot CRM

↓

Google Ads Conversion

↓

Karix WhatsApp API

↓

Confirmation Message to User

---

## Failure Handling

If HubSpot is temporarily unavailable, the backend should store the lead in a retry queue or database instead of losing the submission. Once HubSpot becomes available again, the queued requests can be processed automatically.

If the WhatsApp API fails, the lead should still be saved successfully in HubSpot. Notification failures should be logged and retried later without affecting the user's form submission.

---

## Monitoring

The system should maintain logs for every API request and response. Failed requests should generate alerts, while successful submissions should be tracked through Google Analytics 4 and Google Ads Conversion tracking to monitor overall lead generation performance.

This architecture ensures reliable lead capture, accurate marketing attribution, and a seamless user experience while minimizing data loss.
