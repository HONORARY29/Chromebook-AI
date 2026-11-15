CHROMEBOOK AI V1 — LOCAL WEBGPU STARTER

This is an early working prototype package, not the finished autonomous assistant.

INCLUDED
- Browser chat interface.
- WebLLM integration using the same Qwen2.5-0.5B model ID tested in the playground.
- Streaming model responses.
- Conversation history saved in localStorage.
- Clear and export conversation controls.
- PWA manifest and a service worker that caches the app shell.

IMPORTANT LIMITATIONS
- The app shell is cacheable, but fully offline startup has NOT been verified.
- The WebLLM JavaScript library is loaded from esm.run, so a first-time app load needs internet.
- WebLLM model files are cached by the browser; browser storage may be evicted or cleared.
- The app has not been tested on your physical Chromebook by the assistant.
- Screenshot understanding, browser automation, and general-purpose file management are not included yet.
- Model inference is local once loaded; the code does not send prompts to a cloud AI endpoint.

HOW TO RUN
1. Extract this ZIP.
2. Host the folder on an HTTPS static host. GitHub Pages is one option.
   Opening index.html directly as a file is not suitable because the app uses
   JavaScript modules, WebGPU, and a service worker.
3. Open the HTTPS page in Chrome on the Chromebook.
4. Press "Load local AI" and wait for the model to initialize.
5. Send a test prompt.
6. Use Chrome's Install app option if it is offered.

OFFLINE TEST
1. After the first successful model load, close and reopen the app while online.
2. Confirm the app and model initialize again.
3. Disconnect Wi-Fi or enable Airplane mode.
4. Reopen the app and try another prompt.
5. Record the exact error if it fails. Do not consider offline operation confirmed until this succeeds.

MODEL
Qwen2.5-0.5B-Instruct-q4f16_1-MLC

ENGINE
@mlc-ai/web-llm, imported from esm.run.

NEXT DEVELOPMENT STEPS
1. Verify install and offline startup on the actual C723.
2. Move model work into a Web Worker to keep the interface responsive.
3. Improve memory controls and persistence.
4. Add safe task planning with explicit approval before actions.
5. Evaluate vision models only after measuring memory and performance.
