

    Title: “F5 BIG‑IP Troubleshooting Lab: LTM & ASM/AWAF Tickets”

    Audience: Intermediate F5 admins familiar with basic VS/pool/WAF concepts.

    Objectives:

        Use BIG‑IP tools (GUI, tmsh, logs) to troubleshoot L4–L7 issues.

        Diagnose and fix misconfigurations in LTM and ASM/AWAF.

        Interpret WAF events (false positives vs real attacks).

    Environment:

        Diagram: Client ↔ BIG‑IP ↔ Web servers, with WAF on one or more VIPs.

        Access info: mgmt IP/URL, credentials, jumphost info.

2. How to use this lab

    Scenario: You are a Tier‑2 engineer receiving tickets from users or Tier‑1.

    Tools expected:

        tmsh, System › Logs › Local Traffic / Application, tcpdump/ssldump, curl from BIG‑IP, browser.

    Student deliverables per ticket:

        Root cause explanation.

        Exact fix applied.

        Evidence (screenshot or command output).
