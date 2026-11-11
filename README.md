# SENTINEL 13-indicator auto paper bot

Deploy as a **separate** Streamlit app with `app.py` as the main file. No real orders or Kalshi API keys.

Defaults: Automatic paper enabled, 60-second start buffer, 20-cent take profit, 15-cent stop loss, opposing-signal exit. Entry prices are based on observed public Kalshi quotes and are not guaranteed fills.

**Durable history**: Set `DATABASE_URL` in Streamlit app Secrets to a Supabase Postgres connection string. The app will create a `sentinel_state` table. Without `DATABASE_URL`, local SQLite is used; Streamlit Community Cloud can erase local storage on restart. Do not put the database password in GitHub.

**Critical limitations**: Streamlit refresh runs only while the session is active. It is not a 24/7 background worker. Expired positions are not automatically settled. The dashboard does not backfill missed fills. 13 indicator votes are not a calibrated win probability. For persistent unattended monitoring, deploy a separate worker with durable database and idempotent market processing.
