# Ticket 4 – WAF blocking a known Apache Struts‑like probe

# Title: “Security test shows WAF blocks Struts exploit attempt”

    ##Ticket description

        Security team wants proof WAF detects Apache Struts/OGNL attacks.

        They ask you to run a safe test and show them the WAF event.

    ##Context

        VIP: /Common/vs_java_https.

        Policy: /Common/pol_java_asm with Java/Struts signatures enabled.

        App URL: /upload.action.

    ##Tasks

        Send a Struts‑style test request from the jumphost (or a lab script):

```
        bash
        curl -k -v \
          "https://java.example.com/upload.action" \
          -H 'Content-Type: ${(#_="multipart/form-data").(#context["com.opensymphony.xwork2.dispatcher.HttpServletResponse"].addHeader("X-Struts-POC","1"))}' \
          --data-binary 'test'
```

        Verify that the request is blocked and logged by ASM/AWAF as a Java/Struts/OGNL RCE attempt.

        Collect the event details (signature ID, attack type, severity).

        Prepare a short explanation targeted at a non‑F5 security person.

    ##Deliverables

        Screenshot of the specific WAF request log entry (showing attack signature, severity, blocking).

        Short “exec summary” paragraph explaining what kind of attack was detected and how WAF mitigates it.

    ##Hints

        “Filter events by URL /upload.action and your test client IP.”

        “Look at the ‘Attack Type’ field in the event.”
