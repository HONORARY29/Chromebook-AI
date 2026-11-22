CHROMEBOOK AI V1 — DEXTRADESK + BROWSER LINUX VM BUILD

Files: index.html, manifest.webmanifest, sw.js, README.txt.

Features:
- Local WebLLM chat configured for Qwen2.5-0.5B-Instruct-q4f16_1-MLC.
- Browser-local conversation history, export and clear controls.
- PWA manifest and service-worker app-shell caching.
- DextraDesk remote PC panel embedded at https://app.dextradesk.com/.
- New Browser Linux VM panel embedding LinuxOnTab's Alpine Linux environment.

VM design and important boundaries:
- LinuxOnTab describes its environment as a browser-side Linux system running in WebAssembly, with an Alpine Linux userland. It says computation runs in the browser tab and VM data/snapshots are stored in IndexedDB.
- This is not ChromeOS Linux development environment, not a Windows-hosted VM, and not a cloud compute instance.
- First load requires internet. LinuxOnTab says its page and VM image can be cached for offline boot, but offline operation has NOT been tested on this Chromebook.
- The embedded panel uses LinuxOnTab's shell page. Third-party iframe embedding may be blocked by provider/browser policy; if it fails, use the separate-page link or report the exact error.
- v86's published compatibility notes state that normal 64-bit Linux kernels are not supported; Alpine Linux is supported.
- Keep the VM lightweight. Running it at the same time as the local WebLLM model may consume substantial RAM on an 8 GB Chromebook. Close or stop one when using the other if performance suffers.
- The VM is not automatically connected to the Chromebook AI. The AI cannot inspect the VM terminal or run commands in it in this build.
- Do not enter passwords, API keys, or sensitive files into a third-party environment unless you understand its storage and security model.

Deployment:
1. Extract this ZIP.
2. Open chromebook_ai_v1.
3. Upload all four files to the root of your GitHub Pages repository, replacing the existing versions.
4. Wait for GitHub Pages to redeploy.
5. Reopen/refresh the Chromebook AI website. If the old version remains, close the installed PWA and reopen it.
6. Scroll to Browser Linux VM — Alpine and wait for the VM page to load and boot.

Sources:
- v86 project and compatibility: https://github.com/copy/v86
- LinuxOnTab product, offline/storage and embed parameters: https://linuxontab.com/
- LinuxOnTab shell: https://linuxontab.com/shell/?pip=1&piph=400&pipw=600&pipx=20&pipy=50

Verification status:
- The ZIP and HTML integration were created and checked locally.
- This build has NOT been tested on the user's Chromebook.
- The embedded Linux VM boot, iframe permission, offline caching and persistence must be confirmed on the Chromebook.
