# Diagnostic Methodology

## 1. Classify the symptom
Possible layers: power, hardware, firmware/boot, operating system, network, monitoring.

## 2. Collect evidence
Ask what failed, when it failed, whether power/BMC work, what the Event Log says, what Remote Console shows, and whether the component is detected.

## 3. Form a hypothesis
A hypothesis is an explanation based on evidence. Do not confuse it with proof. For example, a missing NVMe may be caused by the drive, connector, riser, backplane, PCIe path, power, or firmware.

## 4. Follow the runbook
The runbook gives approved checks, safe actions, replacement instructions, verification, and escalation conditions.

## 5. Verify
Return to the original symptom after the action. Ask: did the problem actually disappear?

## 6. Document
Record symptom, evidence, checks, action, replacement if any, verification, and escalation.

### Evidence vs hypothesis
**Evidence:** BMC reports Fan 1 at 0 RPM.

**Hypothesis:** Fan 1 is physically faulty.

The first is a fact; the second requires confirmation.
