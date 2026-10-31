# AI Smart Patient

Flask-based patient monitoring dashboard with Firebase Realtime Database, an ICU risk model, PDF reports, and scheduled email alerts.

## Run locally

1. Install dependencies: `pip install -r requirements.txt`
2. Put your Firebase service account file at `firebase-key.json` (or set `FIREBASE_SERVICE_ACCOUNT_JSON` to its JSON contents).
3. Configure `GMAIL_SENDER`, `GMAIL_APP_PASSWORD`, and `ALERT_RECIPIENT` in an untracked `.env` file if email alerts are needed.
4. Run `python app.py` and open the local URL shown by Flask.

The local development login defaults to `admin` / `1234`. Set `APP_USERNAME` and `APP_PASSWORD` in `.env` to change it.

## Deploy to Render

The root `render.yaml` defines a Singapore web service on Render's free compute plan. Free services may sleep after 15 minutes without requests, and Render blocks outbound SMTP on the free plan, so this configuration is for demos rather than continuous monitoring or email alerts. On the first Blueprint setup, provide these secret values in Render's prompt; do not commit them:

- `FIREBASE_SERVICE_ACCOUNT_JSON`: the Firebase service-account JSON contents
- `APP_PASSWORD`: a strong dashboard password
- `GMAIL_SENDER`, `GMAIL_APP_PASSWORD`, and `ALERT_RECIPIENT`: optional, for email notifications

Render generates `FLASK_SECRET_KEY` automatically. After applying the Blueprint, open the service URL and sign in with username `admin` and the password you supplied.
