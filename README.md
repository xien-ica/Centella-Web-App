# Centella Web App

Web app for **Centella Homes HOA**, built with React and Vite and backed by Supabase. It uses the same Supabase project as the [Centella Admin App](https://github.com/xien-ica/Centella-Admin-App) (the desktop app for HOA administrators).

## Features

> Edit this list to match what the app does today.

- Sign in and account access through Supabase Auth
- Data loading and updates through Supabase
- QR code generation
- Safe rendering of user-provided HTML (sanitized with DOMPurify)
- Loading skeletons and client-side routing

## Tech stack

| Area | Tools |
| --- | --- |
| UI | React 19, React Router 7 |
| Build | Vite 7 |
| Backend | Supabase (`@supabase/supabase-js`) |
| Icons | lucide-react, react-icons |
| Extras | qrcode.react, DOMPurify, react-loading-skeleton |
| Code quality | ESLint 9 |

## Project structure

```
Centella-Web-App/
├── public/              # Static assets
├── src/                 # Application source
├── index.html
├── vite.config.js
├── eslint.config.js
└── package.json
```

## Getting started

### Requirements

- Node.js 20 or newer (22 recommended)
- npm
- The Supabase project used by the Centella apps

### Install

```bash
git clone https://github.com/xien-ica/Centella-Web-App.git
cd Centella-Web-App
npm install
```

### Environment variables

Create a `.env` file in the project root. It is gitignored, so it is never committed.

```env
VITE_SUPABASE_URL=https://<your-project-ref>.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=<your-publishable-key>
```

Find both values in the Supabase dashboard: click **Connect**, then choose **Framework → React → Vite**. Variables must start with `VITE_` to be available in the browser. Restart the dev server after changing `.env`.

Only use the **publishable** (public) key here. Everything in a web app is visible to anyone who opens it, so never put a secret or `service_role` key in the code or `.env`. Third-party secrets (email, payments, push notifications) stay in Supabase Edge Function secrets, and Row Level Security (RLS) policies protect your data.

### Run in development

```bash
npm run dev
```

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite dev server with hot reload |
| `npm run build` | Create a production build in `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |

## Deployment

`npm run build` outputs static files to `dist/`, which you can host on any static host (Vercel, Netlify, Cloudflare Pages, GitHub Pages). Add the two `VITE_SUPABASE_*` variables in your host's environment settings, because the `.env` file is not uploaded.

Because the app uses client-side routing, configure the host to serve `index.html` for all routes.

## Related repositories

- [Centella Admin App](https://github.com/xien-ica/Centella-Admin-App): desktop app for HOA administrators (Electron + React)
