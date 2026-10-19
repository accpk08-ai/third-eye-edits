# Prompt Camera — website starter

A mobile-friendly browser camera with prompt entry, capture, original-photo download, and a server-side styling adapter.

## Requirements
- Node.js 20+ (recommended)
- A modern browser with camera access
- HTTPS when deployed; `localhost` is allowed for local development

## Run locally

```bash
npm install
npm run server
```

In a second terminal:

```bash
npm run dev
```

Open the Vite URL shown in the terminal (usually `http://localhost:5173`). Allow camera access.

## What works immediately
- Front/back camera selection where supported
- Camera preview and photo capture
- Original image kept separately in browser memory
- Download original
- Prompt input and styling request flow
- Server-side provider adapter endpoint
- Responsive mobile-first UI

## Connect an AI image editor

Set `STYLE_API_URL` to a server endpoint you control that accepts:

```json
{
  "image": "data:image/jpeg;base64,...",
  "prompt": "Make the background a sunset..."
}
```

and responds with:

```json
{
  "image": "data:image/png;base64,..."
}
```

Copy `.env.example` to `.env`, fill in the values, then restart `npm run server`. The endpoint shown here is a provider adapter contract, not a built-in AI service. Never put a private API key in React/browser code.

## Strict face preservation — important

An instruction in the prompt is not a guarantee. Generative editors may subtly redraw a face even if told not to.

For pixel-identical face preservation, the image pipeline needs to:
1. Generate a styled background/image in a separate layer or with a usable edit mask.
2. Create a face/skin mask using a suitable segmentation model, with manual correction for hairline, ears, and jaw edges.
3. Composite the original captured pixels back over the generated result within that mask.
4. Keep the original photo available as an independent download.

A face mask is not a magic identity guarantee: check edge quality and alignment. If the subject's position changes, original pixels may not line up. For the strongest guarantee, limit edits to background areas and do not allow geometry changes, reframing, or full-image regeneration.

## Privacy
- Camera capture happens in the browser.
- The original stays in browser memory until you leave/retake; download it to keep a copy.
- If you connect an AI provider, the image is sent to your server/provider for processing. Disclose this to users and obtain consent.
- Add upload limits, authentication/rate limits, deletion policies, and appropriate privacy terms before public deployment.
