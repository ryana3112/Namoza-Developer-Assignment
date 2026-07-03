# Task 1 – GTM Event Schema

## Event Tracking Plan

| User Action | Event Name | Parameters | Purpose |
|-------------|------------|------------|---------|
| Landing Page Viewed | page_view | page_name, page_url | Track page visits |
| Form Started | consultation_form_started | page_name | Measure form engagement |
| Name Entered | consultation_name_entered | patient_name | Capture first step completion |
| Phone Entered | consultation_phone_entered | phone_number | Track contact details entry |
| Form Submitted | consultation_form_submitted | patient_name, phone_number | Measure successful submissions |
| Thank You Page Viewed | consultation_success | page_name | Track successful lead generation |

---

## Sample dataLayer Push

```javascript
window.dataLayer = window.dataLayer || [];

window.dataLayer.push({
    event: "consultation_form_submitted",
    patient_name: "Aryan Sharma",
    phone_number: "9876543210"
});
```

---

## Google Analytics 4 Mapping

| GTM Event | GA4 Event |
|-----------|-----------|
| page_view | page_view |
| consultation_form_started | form_start |
| consultation_form_submitted | generate_lead |
| consultation_success | conversion |

---

## Google Ads Conversion

The `consultation_form_submitted` event should be configured as a Google Ads Conversion event using Google Tag Manager. This enables conversion tracking and campaign optimization for healthcare consultation leads.

---

## Funnel

Landing Page

↓

Form Started

↓

Name Entered

↓

Phone Entered

↓

Form Submitted

↓

Thank You Page

↓

GA4 Conversion

↓

Google Ads Conversion
