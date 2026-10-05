# INC-2041: payments-api latency and errors


---

**Incident ID:** INC-2041
**Severity:** Sev1
**Affected service:** payments-api
**Onset:** 2026-09-17 13:40 UTC (p99 latency began climbing)
**Detected:** 2026-09-17 14:12 UTC (alert fired)

**Symptoms**
- payments-api p99 latency rose from 180 ms to 4.2 s
- 12 percent of payment requests returning HTTP 503
- Errors are concentrated on the payment posting step

**Observations so far (on-call, 14:15 UTC)**
- Trace breakdown: almost all added latency sits in the call from payments-api to ledger-service
- ledger-service logs: repeated "timeout acquiring database connection (waited 3000 ms)"
- fraud-scoring and auth-service spans look normal
- ledger-postgres primary CPU and disk are within normal range
- Daily traffic peak normally runs from about 13:45 to 15:00 UTC
- Yesterday's peak passed without issues

**Question for the agent:** What changed?
