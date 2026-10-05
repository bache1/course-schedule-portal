# Automated Academic Schedule & Google Calendar Integration Portal
> A resilient, serverless web application designed to streamline academic schedule management and automate course synchronization with personal calendars. Built with a cloud-native architecture on AWS and integrated with the Google Calendar API.

## System Architecture & Workflow
1. **Frontend Layer**: Hosted securely on AWS S3, providing a responsive interface where users can view available courses fetched via Amazon API Gateway.

2. **Data Management Layer**: Course metadata and user subscriptions are managed and persisted in Amazon DynamoDB.

3. **Serverless Compute Layer**: AWS Lambda (Python) handles backend logic, including RESTful endpoints, database queries, and external API requests.

4. **Calendar Synchronization Flow**:
   - Users select their courses and authenticate via Google OAuth 2.0 (```text access_type=offline for refresh tokens```).
   - The backend parses course days and time ranges, mapping them accurately to local time zones (```text Asia/Jakarta / UTC+7```) while handling casing variations.
   - Dynamically generates and pushes calendar events (/events API) with custom descriptions and notifications.

## Key Technical Features
- **Cloud-Native & Serverless**: Utilizes AWS Lambda and API Gateway for a scalable, cost-effective, and maintenance-free backend infrastructure.
- **Precise Timezone Handling**: Custom Python```text datetime``` parsing logic that maps weekday strings (e.g., Senin, Selasa) to exact ISO timestamps adjusted for WIB (```text +07:00```) to prevent offset discrepancies.
- **Robust Error Handling & Resilience**: Implements granular```text try-except``` blocks per course iteration and sanitization logic (e.g.,```text .capitalize```()) to ensure that malformed data or single API failures do not trigger catastrophic```text 500 Internal Server Error``` responses.
- **Secure Authentication**: Implements OAuth 2.0 authorization code exchange flow to securely acquire, store, and manage user access/refresh tokens.

## Tech Stack
- **Cloud Infrastructure & Services**: AWS Lambda, Amazon DynamoDB, Amazon API Gateway, AWS S3
- **Backend Language**: Python 3.12
- **Frontend**: HTML5, JavaScript (ES6+), CSS
- **APIs & Protocols**: Google Calendar REST API, OAuth 2.0, HTTP/REST

## Repository Structure
```text
sabil-course-schedule-portal/
│
├── backend/
│   └── lambda_function.py      # Kode Python AWS Lambda (Database handler, Time parser, & Google Calendar API)
│
├── frontend/
│   ├── index.html              # Antarmuka web (Form, Checkbox courses, & Script integrasi API)
│   └── assets/                 # Folder aset pendukung (opsional)
│
└── README.md                   # Dokumentasi lengkap project
```


**Salsabila Bachtiar**
- Informatics Student | Aspiring DevOps & Cloud Engineer  
[LinkedIn](https://www.linkedin.com/in/salsabila-bachtiar-30161724a) | [GitHub](https://github.com/bache1)
