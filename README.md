# Token Weather Report (TWR)

> *"Just as no business sends trucks into a hurricane without checking the forecast, no enterprise deploys AI pipelines without checking the Token Weather."*

**Token Weather Report** is a real-time AI API infrastructure health monitoring service that translates raw provider status data into universally understood weather and traffic broadcast language.

**Live:** [token-weather-report.web.app](https://token-weather-report.web.app)

**Source:** [github.com/MushroomFleet/token-weather](https://github.com/MushroomFleet/token-weather)

---

## What It Does

TWR monitors 11 AI service providers every 10 minutes and presents their health as a broadcast-style dashboard. Providers are organized into three service categories:

### LLM Services

| Provider | Status Source |
|----------|-------------|
| **Anthropic** (Claude) | status.anthropic.com |
| **OpenAI** (GPT) | status.openai.com |
| **Google Gemini** | status.cloud.google.com |
| **Google Cloud AI** | status.cloud.google.com |
| **xAI** (Grok) | status.x.ai |

### Image Services

| Provider | Status Source |
|----------|-------------|
| **OpenAI Image** (DALL-E) | status.openai.com |
| **Stability AI** (Stable Diffusion) | status.stability.ai |
| **Black Forest Labs** (FLUX) | status.bfl.ml |
| **Ideogram** | status.ideogram.ai |

### Multi-Modal Services

| Provider | Status Source |
|----------|-------------|
| **Replicate** | replicatestatus.com |
| **ElevenLabs** | status.elevenlabs.io |

Each provider receives a **Token Condition Index (TCI)** score from 0-100:

| TCI Range | Condition | Meaning |
|-----------|-----------|---------|
| 95-100 | Token Clear | Fully operational |
| 80-94 | Token Drizzle | Minor elevated errors |
| 60-79 | Token Fog | Intermittent degradation |
| 30-59 | Token Squall | Significant disruption |
| 0-29 | Token Storm | Major outage |

---

## Views

- **Overview** -- Provider cards with live TCI gauges, sparklines, and bulletin feed, grouped by service category
- **Weather** -- Current conditions per provider with active incident details and severity alerts
- **Traffic** -- Congestion flow status, rush hour alerts, lane closures, and scheduled maintenance (Token Roadworks)
- **Forecast** -- 7-day Token Outlook, maintenance calendar, and monthly Token Climate Report
- **History** -- Trend analytics with per-provider charts, reliability ranking, day-grouped incident archive, and category filtering

All views display providers in three labeled sections: LLM Services, Image Services, and Multi-Modal Services. The History view includes a category filter (ALL / LLM / IMAGE / MULTIMODAL) for focused analysis.

---

## How It Works

```
[11 Provider Status Pages]
        |
        v  (poll every 10 min)
[Cloudflare Worker]
   |-- TCI Scoring Engine
   |-- Anomaly Detection (Z-score)
   |-- Alert Escalation (advisory -> watch -> warning -> emergency)
   |-- Multi-Front Detection (3+ providers degraded)
   |-- Bulletin Generation (TWR weather language)
   |-- Webhook Notifications
        |
   [D1 Database] [KV Cache] [R2 Storage]
        |
        v
[React Dashboard]  -->  Firebase Hosting
```

Provider status pages are polled automatically. Raw status data is converted into TCI scores, weather conditions are assessed, bulletins are generated in TWR broadcast language, and results are served to the dashboard in real time.

---

## TWR Lexicon

TWR uses a custom broadcast vocabulary to describe AI infrastructure conditions. This language is consistent across all views and bulletins.

### Weather Terms (Sudden / Unplanned)

| Term | Meaning |
|------|---------|
| **Token Storm** | Major unplanned API outage |
| **Token Squall** | Sudden short-duration error spike |
| **Token Fog** | Intermittent, inconsistent responses |
| **Token Drizzle** | Minor elevated error rates |
| **Token Clear** | Fully operational |
| **Token Front** | Incoming degradation pattern detected |
| **Token Anomaly** | Statistical departure from baseline |

### Traffic Terms (Congestion / Planned)

| Term | Meaning |
|------|---------|
| **Token Gridlock** | Rate limit saturation |
| **Token Slowdown** | Elevated latency, reduced throughput |
| **Token Roadworks** | Planned maintenance window |
| **Token Rush Hour** | Predictable high-demand period (14:00-20:00 UTC) |
| **Token Lane Closure** | Specific endpoint unavailable |
| **Token Detour** | Fallback provider recommended |

---

## API

TWR exposes a public REST API for programmatic access to provider health data.

**Base URL:** `https://twr-api.djzgallery.workers.dev`

| Endpoint | Description |
|----------|-------------|
| `GET /api/v1/tci/current` | Current TCI scores for all 11 providers |
| `GET /api/v1/tci/history/:providerId?hours=24` | Historical TCI readings |
| `GET /api/v1/incidents/active` | Active (unresolved) incidents |
| `GET /api/v1/incidents/history` | All incidents (paginated) |
| `GET /api/v1/providers` | Provider metadata with category field |
| `GET /api/v1/forecast/maintenance` | Scheduled maintenance windows |
| `GET /api/v1/forecast/weekly` | 7-day provider outlooks |
| `GET /api/v1/forecast/climate` | Monthly climate report |
| `GET /api/v1/analytics/trends?days=30` | Trend analytics and reliability ranking |
| `GET /api/v1/bulletins/latest` | Recent bulletin feed |
| `GET /api/v1/rss` | RSS 2.0 feed |

---

## Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{token_weather_report,
  title = {Token Weather Report: Real-time AI API Infrastructure Health Monitoring},
  author = {Drift Johnson},
  year = {2025},
  url = {https://github.com/MushroomFleet/token-weather},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
