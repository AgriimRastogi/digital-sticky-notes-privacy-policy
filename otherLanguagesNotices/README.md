# Multi-Language Notices for Digital Sticky Notes

This directory contains localized notice JSON files hosted on GitHub Pages (`https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/`).

## How It Works

1. **Default English**:
   - `notices.json` sits at the root of the repository.
   - Endpoint: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/notices.json`

2. **Other Languages**:
   - Stored in this folder with the format: `notices_<lang>.json`
   - Example endpoints:
     - Spanish: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/notices_es.json`
     - Hindi: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/notices_hi.json`
     - French: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/notices_fr.json`
     - German: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/notices_de.json`
     - Japanese: `https://agriimrastogi.github.io/digital-sticky-notes-privacy-policy/otherLanguagesNotices/notices_ja.json`

3. **Graceful Fallback**:
   - If an announcement is only drafted in English and the localized file does not exist yet (HTTP 404), the app automatically falls back to `notices.json` so no user ever misses an announcement.

4. **GitHub Pages Rate Limits & Bandwidth**:
   - **No API Rate Limits**: GitHub Pages is served through Fastly CDN and is designed for public static website hosting (not restricted by GitHub's 60 req/hr API limits).
   - **ETag (HTTP 304)**: The app uses `If-None-Match` caching; unchanged checks return `304 Not Modified` with 0 bytes transferred.
   - **1-Hour TTL**: Client caches locally in `AsyncStorage` and cools down for 1 hour between checks.
