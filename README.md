# Settings clipboard evidence

Browser evidence for a contribution to [Multica](https://github.com/multica-ai/multica).

Before: upstream main at d8fa885d26acbdecde49010276e905cc9de5a056. After: 0a9a7f040a4904dd30e94eca25b29f58e340f5b4.
These are unedited Chromium screenshots of the production MembersTab and VCSTab
components, production translations, shared clipboard helper, and Sonner toasts.
Both versions use the same local reproduction host, production styles, and fictional
member, share-link, and VCS connection data. Query hooks and providers are real;
API methods are replaced with local fixture responses. No real credentials,
workspace data, Go backend, database, or installed desktop application is used.

Playwright sets navigator.clipboard to undefined. For the members scenario it
sets document.execCommand("copy") to return false; for VCS it returns true.
The paired JSON files record those calls and the rendered text. This controlled
browser API setup demonstrates the two call-site branches; it is not evidence
that a particular real operating-system clipboard was written successfully.
The screenshot headers disclose the fixture and the controlled conditions.

- Members before: the legacy API returns false but the UI says Link copied.
- Members after: the same failure produces Failed to copy link.
- VCS before: the UI says Could not copy without calling the legacy API.
- VCS after: the legacy API is called and its true result produces Copied to clipboard.

Captured on 2026-09-08 using Playwright Chromium, a 1150x1000 CSS viewport,
device scale factor 1, and light theme. The screenshot files are not part of
the code PR diff. Automated regressions in the code PR reproduce these branches.

## Attribution and license

The rendered components, translations, and styles originate from multica-ai/multica.
The reproduction host and fixture were added for this contribution. Upstream
LICENSE and NOTICE are included unchanged; the full Multica License applies.
