# Comment trigger avatar evidence

Browser evidence for a contribution to [Multica](https://github.com/multica-ai/multica).

Before: unmodified upstream main at d8fa885d26acbdecde49010276e905cc9de5a056. After: 584ea2dbf4843eef57cdbb04bcdfe959c6c0a1ef.
Both captures mount the real upstream CommentInput, ReplyInput, ContentEditor,
CommentTriggerChips and ActorAvatar with production styles. The preview hook,
API client, response schema and browser image loading are real.

This is a component reproduction using fictional fixture data. A local HTTP API
on port 4318 replaces the Go backend, authentication and database. The frontend
runs on port 4317. The returned avatar_url is /uploads/agent-custom-avatar.png.
The image is the unmodified apps/web/public/icons/icon-192.png from upstream,
representing an already saved custom avatar. No upload API or installed Desktop
application was exercised, and sending is disabled.

Before, each composer requests the image from the frontend origin, receives
HTTP 404 and renders the generic Bot fallback. After, both request the API
origin, receive HTTP 200 and decode the 192-pixel PNG. The control image loads
directly from the API origin in both captures. No browser requests are
intercepted and no image-error event is artificially dispatched.

The PNG files are unedited Playwright Chromium 1208 locator screenshots,
captured with a 1280x1050 CSS viewport, device scale factor 2, en-US and light
theme. The paired JSON files preserve request and DOM evidence.

The only production change imports the existing resolvePublicFileUrl helper
and applies it to TriggerAgentAvatar's avatarUrl prop. The code contribution
also adds a focused regression test.

## Attribution and license

Multica component rendering and bundled icon originate from multica-ai/multica.
The reproduction host and fixture were added for this contribution. Upstream
LICENSE and NOTICE are included unchanged; the full Multica License applies.
