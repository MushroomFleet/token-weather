# Token Weather Report

> *"Just as no business sends trucks into a hurricane without checking the forecast, no enterprise deploys AI pipelines without checking the Token Weather."*

**Token Weather Report (TWR)** is a real-time monitoring service for AI API infrastructure health, styled after weather and traffic broadcast services. It translates raw provider status data into universally understood conditions — so anyone from engineers to executives can assess AI service reliability at a glance.

**Live Dashboard:** [https://tokenweather.com/](https://tokenweather.com/)

---

## How It Works

TWR monitors the Big 5 AI API providers every 10 minutes and scores each on a 0–100 **Token Condition Index (TCI)**:

| TCI Score | Condition | What It Means |
|-----------|-----------|---------------|
| 95–100 | **Token Clear** | All systems operational. No degradation detected. |
| 80–94 | **Token Drizzle** | Minor elevated latency or error rates. |
| 60–79 | **Token Fog** | Intermittent degradation. Some requests may fail. |
| 30–59 | **Token Squall** | Significant disruption. Expect elevated errors. |
| 0–29 | **Token Storm** | Major outage. Service severely impacted. |

### Monitored Providers

- **Anthropic** (Claude)
- **OpenAI** (GPT)
- **Google Gemini**
- **Google Cloud AI** (Vertex AI)
- **xAI** (Grok)

---

## Dashboard Views

### Overview
Live provider cards showing TCI score gauges, 24-hour sparklines, component status, and a scrolling bulletin ticker in broadcast style.

### Weather
Current atmospheric conditions for each provider. When incidents occur, they appear as weather events — Token Storms, Token Squalls, Token Fog — with severity-coded alerts and bulletin text.

### Traffic
Real-time congestion flow across all providers. Shows throughput status (Free Flow, Token Slowdown, Token Congestion, Token Gridlock), rush hour alerts during peak UTC hours, and scheduled maintenance displayed as Token Roadworks.

### Map
Interactive 3D globe powered by CesiumJS. Datacenter nodes are plotted geographically and colored by TCI score. Traffic flow lines connect same-provider regions. Filter by individual provider.

### Forecast
Forward-looking intelligence:
- **7-Day Token Outlook** — per-provider expected conditions based on maintenance schedules and historical baselines
- **Maintenance Calendar** — upcoming Token Roadworks with affected components and timing
- **Monthly Token Climate Report** — narrative summary of provider reliability trends in broadcast style

### History
Historical analytics and incident archive:
- **Trend Charts** — per-provider daily TCI over selectable periods (7/14/30/90 days)
- **Reliability Ranking** — providers ranked by average TCI with visual bar comparison
- **Incident Archive** — day-grouped incident log with today's events expanded in detail and past days collapsible

---

## Alert System

TWR uses a four-tier alert escalation mirroring meteorological standards:

| Level | Meaning | Triggered By |
|-------|---------|--------------|
| **Token Advisory** | Informational, monitor closely | Single anomalous TCI reading |
| **Token Watch** | Prepare contingencies | 3+ consecutive anomalies |
| **Token Warning** | Active or imminent significant event | TCI below 60 with active incidents |
| **Token Emergency** | Catastrophic multi-provider event | 3+ providers simultaneously degraded |

Alerts are displayed as banner notifications across the dashboard and delivered via webhook for integration with Slack, PagerDuty, or custom systems.

---

## TWR Lexicon

TWR uses two parallel terminology systems drawn from broadcast media:

### Weather Terms — Sudden / Unplanned Events

| Term | Meaning |
|------|---------|
| **Token Storm** | Major unplanned API outage |
| **Token Squall** | Sudden short-duration error spike |
| **Token Fog** | Intermittent, inconsistent responses |
| **Token Drizzle** | Minor elevated error rates |
| **Token Clear** | Fully operational, no degradation |
| **Token Front** | Incoming degradation pattern detected |
| **Token Anomaly** | Statistical departure from baseline |
| **Token Whiteout** | Total loss of visibility — status page also down |

### Traffic Terms — Congestion / Planned Events

| Term | Meaning |
|------|---------|
| **Token Gridlock** | Rate limit saturation — full queue block |
| **Token Slowdown** | Elevated latency, throughput reduced but flowing |
| **Token Roadworks** | Planned maintenance window |
| **Token Rush Hour** | Predictable high-demand period |
| **Token Lane Closure** | Specific model endpoint unavailable |
| **Token Detour** | Fallback provider recommended |
| **Token Clearance** | Maintenance concluded, full service restored |

### Forecast Terms — Long-Range / Predictive

| Term | Meaning |
|------|---------|
| **Token Climate** | 30–90 day reliability profile for a provider |
| **Token Outlook** | 7-day forward forecast |
| **Token Season** | Recurring patterns (model launches, end-of-quarter) |
| **Token Baseline** | Provider's normal operating performance envelope |

---

## RSS Feed

Subscribe to TWR bulletins via RSS at the `/api/v1/rss` endpoint for integration into your existing monitoring dashboards or feed readers.

---

## Use Cases

| Scenario | How TWR Helps |
|----------|---------------|
| **AI pipeline reliability planning** | Weekly Outlook informs deployment scheduling around known maintenance |
| **Multi-provider failover** | Token Warning triggers automated routing to fallback providers |
| **SLA compliance reporting** | Historical TCI data provides evidence for provider reliability claims |
| **DevOps morning briefing** | Dashboard replaces manual checking of 5 separate status pages |
| **Procurement decisions** | 90-day Token Climate reports compare provider reliability side by side |
| **Incident post-mortems** | Timestamped incident archive provides narrative of event progression |

---

## Data Sources

All data is sourced from publicly available provider status pages. TWR is a presentation and aggregation layer — it does not intercept, reverse-engineer, or probe provider APIs. Forecast language is clearly labelled as predictive, not guaranteed. Provider names are used for identification purposes under nominative fair use.

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
