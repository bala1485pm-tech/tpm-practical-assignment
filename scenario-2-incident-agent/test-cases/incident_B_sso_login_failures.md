# INC-2033: SSO login failures


---

**Incident ID:** INC-2033
**Severity:** Sev2
**Affected service:** auth-service
**Onset:** 2026-09-16 08:22 UTC
**Detected:** 2026-09-16 08:30 UTC

**Symptoms**
- About 60 percent of SSO logins failing with HTTP 504
- Password logins are succeeding normally
- Existing sessions and token validation are unaffected

**Observations so far (on-call, 08:34 UTC)**
- auth-service logs: "upstream timeout calling external-idp token endpoint (10 s)"
- identity-db latency, connections, and error rate are normal
- auth-service CPU, memory, and pod count are normal
- SSO login request volume is in line with a normal weekday morning
- No error-rate change on payments-api, web-checkout, or mobile-gateway apart from failed logins

**Question for the agent:** What changed?
