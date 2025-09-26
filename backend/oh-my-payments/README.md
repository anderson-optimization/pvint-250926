# Oh My Payments (60-Minute Live Exercise)

This task is intentionally time-boxed to ~1 hour. You won’t finish everything—and that’s fine. We care about how you reason, prioritize, communicate trade-offs, and write code under constraints.

## Context

You’ll build a backend service that ingests and analyzes payments.

What We’re Evaluating:

- Can you quickly ship something correct (Tier 1–2)?
- Do you structure code cleanly even when rushing?
- Do you know how to introduce concurrency safely (Tier 3)?
- Can you think creatively about anomalies/performance (Tier 4), even if you only stub or explain?

Deliverables (within the hour):

1. Design diagram for Tier 0.
2. Working code for as many tiers as you can reasonably complete.

### Tiered Requirements

Progress through tiers in order. It’s OK to jump ahead and leave TODOs if you explain your plan.

### Tier 1 — Parse & Summarize (Baseline)

Read data from [data/example_input.txt](./data/example_input.txt), count occurrences of each payment status (e.g., SUCCESS, INFO, FAILURE) and write summary JSON to output/summary.json. Handle basic errors (don’t crash on bad data).

Each line has the shape: `[timestamp] [payment_status] [service_name] [user_id] [message]`, Example: `2025-07-22T12:34:56Z INFO AuthenticationService user123 User login successful`.

Example summary:

```json
{
  "SUCCESS": 1000,
  "INFO": 120,
  "FAILURE": 30
}
```

```txt
Write the simplest possible program in <YOUR_LANGUAGE> that:
1. Reads a text file line by line from data/input.txt.
2. Counts how many times each log level (INFO, WARN, ERROR) appears.
3. Writes a JSON file to output/summary.json with counts per log level.
4. Ignores malformed lines without stopping the program.

Keep it minimal — no over*engineering, no abstractions, no separation of concerns.

Each line has the shape: timestamp] [payment_status] [service_name] [user_id] [message]
Example: 2025-07-22T12:34:56Z INFO AuthenticationService user123 User login successful

Example summary:
{
  "SUCCESS": 1000,
  "INFO": 120,
  "FAILURE": 30
}
```


### Tier 2 — Deeper Analytics
In addition to Tier 1:

Identify top 10 services and top 10 users by payment volume.

Compute peak usage hours (group by hour of day).

Extend output/summary.json:
``` json
{
  "payment_statuses": {"SUCCESS": 1000, "INFO": 120, "FAILURE": 30},
  "top_services": ["AuthService", "PaymentService", ...],
  "top_users": ["user123", "user456", ...],
  "peak_hours": ["12:00-13:00", "16:00-17:00"]
}
```

### Tier 3 — Concurrency & “Real-Time” Simulation
In addition to Tier 2:

File watcher / trigger: Detect new files in data/ and process them without restarting (polling, FS events, or queued tasks - your choice).

Concurrent processing: Use threads/async/workers to process multiple files or chunks concurrently.

Show you considered safety (race conditions, back-pressure) even if it’s minimal (e.g., a queue + worker pool).

### Tier 4 — Anomalies & Performance Constraints (Stretch)
In addition to Tier 3 (design, pseudo-code or partial implementation is acceptable):

Anomaly detection: Define and detect at least one anomaly type (e.g., weird timestamp, unknown status, error spikes, single user spamming). Output to output/anomalies.json.

Performance/Memory visibility: Log or print execution time & peak memory usage.

Scalability thought experiment: Briefly outline (code or notes) how you’d handle larger inputs (multi-GB / billions of lines) under a 500MB RAM cap and <60s latency for new files.

### Tech Instructions
- Use any backend language: Python, .NET, Node.js, Rust, Go, etc.
- Use internet to lookup syntax if you need.
- Except for the initial Tier 1 baseline, do not use AI to generate a working solution—we are interested to see your thought process and problem solving ability, not someone else’s.

### Tips
- Small, composable functions win over giant scripts.
- Leave TODO: comments where you skip (explain briefly).
- Prefer streaming/batching reads over loading entire files (if you get to perf).
- For concurrency, a simple worker pool beats over-engineering.

Good luck — have fun and narrate your thinking as you go!
