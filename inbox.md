# Inbox: found outside the wiki

Lines Claude adds during work when it finds something the wiki lacks or has wrong. The nightly update files each one
into the wiki and removes it. Format: `- YYYY-MM-DD · what · source/reference`.

- 2026-11-21 · System documents' "Last reviewed" is now 2026-11-21 for the SSP, Configuration Management Plan, Resource Management Plan, O&M Plan and Detailed System Design. Each now counts 110 functions (69 callable): the new `apiUsage` tripwire. The O&M Plan has a new Maintenance line for the Dec 19 unused-function review. The Change Management Plan is unchanged. The component diagram PNG still says 109 functions; re-render it from the doc's Mermaid source at the next diagram change. · mac-app #893, #876
- 2026-11-21 · Owner's call: keep the 13 caller-less app functions until a Dec 19, 2026 review, with a tripwire (`apiUsage` logs `unused-api-called`; read with Actions → Function logs, match). A one-time scheduled task runs the review and opens a removal PR for the unused ones, for his OK. · mac-app #876, #893
