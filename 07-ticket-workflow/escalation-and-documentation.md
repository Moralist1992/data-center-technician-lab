# Escalation and Documentation

## Escalation is not failure
Safe operations matter more than pretending to know everything.

A useful escalation contains:
1. Problem statement.
2. Server/device identification.
3. Relevant time/event context.
4. Evidence.
5. Checks completed.
6. Actions taken.
7. Verification result.
8. Reason for escalation.

Weak:
> Server broken. Please check.

Strong:
> Server is unreachable. BMC is available. Hardware Event Log shows no current PSU or fan failure. Remote Console shows Linux, but SSH is unavailable. Network checks were performed according to the runbook. Escalating for further investigation.

Document facts first. `BMC reports Fan 1 at 0 RPM` is evidence; `Fan 1 is definitely broken` is a conclusion that still needs confirmation.
