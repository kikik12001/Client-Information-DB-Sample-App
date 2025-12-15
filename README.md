\# CA1 B8IS124 - Cloud Application Deployment



\## Live Application

\[!\[App Status](https://img.shields.io/badge/Status-Live-brightgreen)](https://mydeployproject-481214.ew.r.appspot.com/)



\*\*URL\*\*: https://mydeployproject-481214.ew.r.appspot.com/



\## Architecture

User Browser → App Engine (Node.js) → Cloud SQL (PostgreSQL)

↓

Secret Manager (DATABASE\_URL)

↓

Cloud Build (CI/CD)

↓

GitHub (Source)



text



\## GCP Services Used (3 services)

| Service | Purpose | Configuration |

|---------|---------|---------------|

| \*\*App Engine\*\* | Node.js runtime | nodejs20, F1 instances, auto-scaling max=2 |

| \*\*Cloud SQL\*\* | PostgreSQL DB | europe-west2:clientinfo-db |

| \*\*Secret Manager\*\* | Secure DATABASE\_URL | Automatic access in Cloud Build |



\## Automated Deployment Pipeline

\*\*Trigger\*\*: `git push origin main`



\*\*cloudbuild.yaml (3 Steps)\*\*:

1\. `npm install` - Install 294 Node.js packages

2\. `sequelize db:migrate` - Cloud SQL Proxy + database migrations

3\. `gcloud app deploy` - Deploy new version live



\## Cost Estimate

£59.45/month (Google Cloud Pricing Calculator)

\- Cloud SQL: £59.20 (main cost)

\- App Engine: £0.20 

\- Others: Free tier

