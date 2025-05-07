# QR Code Generator Web App for Board Game Projects

A serverless web application for generating and managing static and dynamic QR codes. Built using Flutter Web and AWS serverless technologies.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Functional Requirements](#functional-requirements)
- [Technical Requirements](#technical-requirements)
- [User Interface Requirements](#user-interface-requirements)
- [Non-Functional Requirements](#non-functional-requirements)
- [Future Enhancements](#future-enhancements)

---

## Project Overview

This app allows users to generate QR codes. Users can choose between:

- **Static QR Codes**: Encodes fixed data or URLs.
- **Dynamic QR Codes**: Points to a short URL that can be redirected later. Useful for analytics or redirecting based on context.

---

## Functional Requirements

### User Authentication

- Sign-up / sign-in using AWS Cognito
- User-specific dashboard to manage generated codes

### QR Code Generation

- **Static QR Codes**
  - Input: Text or URL
  - Output: Downloadable image (PNG/SVG)
- **Dynamic QR Codes**
  - Input: Redirect URL
  - Output: Shortened dynamic URL with associated QR code
  - Track scan count (hit analytics)
  - Editable redirect target

### Dashboard Features

- List all created QR codes
- Edit or delete dynamic QR codes
- View analytics for dynamic QR codes (scan count, last accessed time)

---

## Technical Requirements

### Frontend

- **Framework**: Flutter for Web
- **Hosting**: AWS S3 + CloudFront

### Backend (Serverless Stack)

- **QR Code Generation**: AWS Lambda function (e.g., using Python or Node.js QR libraries)
- **API Gateway**: Routing for all frontend requests
- **Authentication**: AWS Cognito
- **Database**: AWS DynamoDB
  - Stores dynamic QR code data (user ID, redirect URL, scan count)
- **Storage**: AWS S3 (for downloadable QR images if needed)

### Infrastructure as Code

- **Deployment Tool**: AWS SAM (Serverless Application Model)

---

## User Interface Requirements

- Minimal, clean UI
- Input fields to create QR codes
- QR code preview after generation
- Analytics panel for dynamic QR codes
- Mobile-friendly and responsive

---

## Non-Functional Requirements

- **Performance**: Instant QR generation, <1s page loads
- **Security**: OAuth2 via Cognito; IAM permissions scoped per user
- **Scalability**: Built entirely on scalable AWS serverless services
- **Availability**: S3 and Lambda SLA-based uptime
- **Monitoring**: CloudWatch for logs and alerts

---

## Future Enhancements

- Support for QR types beyond URLs (e.g., vCards, Wi-Fi access, JSON)
- Custom QR design options (colors, embedded logos)
