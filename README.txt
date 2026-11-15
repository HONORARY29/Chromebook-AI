CHROMEBOOK AI V1 — REMOTE CONTROL CENTER BUILD

Files: index.html, manifest.webmanifest, sw.js, README.txt.

Features:
- Local WebLLM chat using Qwen2.5-0.5B-Instruct-q4f16_1-MLC.
- Local browser conversation history, export and clear controls.
- PWA manifest and service worker app-shell caching.
- Remote Control Center with links to Chrome Remote Desktop access and support.
- AI-assisted safety checklist.

Important limitations:
- The live Chrome Remote Desktop session is not embedded in this website.
- This prototype cannot inspect, click, type into, or control the remote desktop session.
- Chromebook-as-host support depends on ChromeOS features and administrator policy.
- Google's standard unattended remote-access setup documents Mac, Windows and Linux hosts.
- The AI checklist is guidance only; user approval and manual action are required.
- Never enter Google passwords, remote-access PINs, or one-time support codes into AI chat.
- Full offline startup has not been verified. The WebLLM JavaScript library is fetched from esm.run.
- Host this folder on HTTPS (GitHub Pages works). Upload the four files to the repository root.
