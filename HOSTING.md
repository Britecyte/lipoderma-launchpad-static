# launchpad.lipoderma.com hosting (pre–Rails cutover)

Until the Rails app replaces this page:

| What | Where |
|------|--------|
| **Marketing / library HTML** | `launchpad.lipoderma.com` → GitHub Pages (`britecyte.github.io`, repo `lipoderma-launchpad-static`) |
| **Videos & PDFs** | `media.lipoderma.com` → Bunny pull zone (`lipoderma-videos`) |
| **Rails app (beta)** | `lipoderma-launchpad.onrender.com` only — **do not** attach `launchpad.lipoderma.com` on Render yet |

`index.html` links training media directly to Bunny, not Render, so library traffic does not depend on the Render disk or `/media` redirects.

When going live on Rails: point DNS (or a subdomain like `app.launchpad.lipoderma.com`) to Render, set `APP_HOST`, and retire or redirect this static repo as needed.

Verify CDN after media changes:

```bash
cd ../launchpadNew && python3 script/verify_training_media_on_bunny.py --check-mp4
```
