# 🛰️ NetTrace — IP Geolocation & WHOIS Network Tracer

A lightweight Streamlit dashboard that traces any domain or IPv4 address and shows its
geolocation, routing metadata (ASN, ISP, organization) and WHOIS registration details.
**No API keys, tokens or credit cards required.**

## Features

- Accepts a domain (`github.com`, `https://github.com/path`) or an IP (`8.8.8.8`) and cleans the input automatically
- Resolves domains to IPv4 with `socket.gethostbyname()`
- ASN, ISP, organization, country, city, timezone and coordinates via [ip-api.com](https://ip-api.com)
- Reverse DNS and proxy / hosting / mobile flags
- Interactive Folium map with a pinned marker
- WHOIS: owner, registrar, creation date, expiry date, days remaining, name servers
- Falls back to the parent domain for subdomains
- Cached lookups to stay within the free rate limit (~45 requests/min)
- Expandable raw JSON viewer

## Run locally

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

## Deploy on Streamlit Community Cloud

1. Push `app.py`, `requirements.txt` and `README.md` to a GitHub repository.
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
3. Click **New app**, choose your repo and branch, and set the main file to `app.py`.
4. Click **Deploy**. No secrets or environment variables are needed.

## Project structure

```
.
├── app.py
├── requirements.txt
└── README.md
```

## Notes & limitations

- ip-api.com's free tier is HTTP-only and limited to about 45 requests per minute per IP.
- Geolocation is approximate and often points to the ISP's hub, not the exact device.
- Some TLDs hide WHOIS data or rate-limit queries, so results may be empty or redacted.
- Only IPv4 resolution is performed for domains.
- For commercial use, review ip-api.com's terms and consider their paid plan.

## Tech stack

Python · Streamlit · Requests · Pandas · python-whois · Folium · streamlit-folium

## License

MIT
