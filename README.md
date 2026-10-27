# 《从0到1》读书会简明版

A phone-friendly reader for a simplified-Chinese, 5th-grade-level book club guide to *Zero to One* (Peter Thiel). Readers can highlight any sentence, ask a question about it, say how well they understood each chapter, tick off the weekly task, and send all of it back to the organizer in one tap.

The guide is an original plain-language companion written for the book club, not a translation of the book.

## What's in the repo
- `index.html`: the whole app in one file. It uses no web fonts, CDNs or trackers, so it loads in China and inside WeChat's browser.
- `manifest.json`, `icon-*.png`: let readers add the app to their home screen with its own icon. It opens full-screen.
- `sw.js`: saves the app on the phone after the first visit so it works offline. **When you change `index.html`, change `VERSION` in `sw.js`** (for example `v1` → `v2`) so readers get the update.
- Upload all of these files together. Home-screen install and offline mode only work over https, which GitHub Pages provides.

## Publish on GitHub Pages
1. Create a public repo (for example `zero-to-one-bookclub`) and add `index.html`.
2. Go to **Settings → Pages → Build and deployment**, set **Source: Deploy from a branch**, pick **Branch: main / (root)**, and save.
3. After a minute the site is live at `https://<your-username>.github.io/zero-to-one-bookclub/`.
4. Share that link in WeChat. Readers can go straight to a chapter with `#c1` … `#c14`, `#toc` (contents) or `#club` (how to run a session).

## How feedback reaches you
Each reader's highlights, questions, chapter ratings and finished tasks are saved **only in their own browser** (localStorage). Nothing is uploaded.

Under **我的问题 → 复制，去微信发送**, the reader copies a ready-made summary and pastes it into a WeChat chat with you. The summary looks like this:

```
《从0到1》读书会简明版 · 读者反馈
读者：小王

【第3章　好公司都不一样】
看懂了吗：有一点难
这周试一试：做了
· 划线：「小区里有很多修理」
  问题：为什么不用拼低价？
```

**Optional automatic collection:** set `CONFIG.feedbackUrl` at the top of the script to any endpoint that accepts a JSON POST. The app will then send `{name, text, notes, level, tasks}` there, and fall back to copying if the request fails. Pick a service that's reachable from China if your readers are there.

Change `CONFIG.sendTo` to tell readers where to send their feedback.

## Notes
- `github.io` usually works in mainland China but can be slow or blocked at times. If readers can't open it, host the same `index.html` on a China-reachable static host.
- To edit the content, change `INTRO`, `CHAPTERS` and `CLUB` in `index.html`. Each chapter has `one` (main idea), `plain` (explanation), `ex` (everyday example) and `task` (weekly exercise).
