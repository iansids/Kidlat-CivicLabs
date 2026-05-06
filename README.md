# Kidlat CivicLabs — Official Website

Kidlat CivicLabs is a civic technology lab that helps government agencies and partners develop innovative digital solutions to the Philippines' most pressing societal challenges.

---

## Tech Stack

| Layer | Tool |
|---|---|
| Framework | Next.js (App Router) + Tailwind CSS |
| Hosting | Vercel |
| Email | Resend + React Email |
| Forms | React Hook Form + Zod |
| Rate Limiting | Upstash Ratelimit |
| CAPTCHA | Cloudflare Turnstile |
| CMS (Optional) | Sanity |

---

## Getting Started

### Prerequisites

- Node.js v18.17 or later
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/kidlatciviclabs/website.git
cd website

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
```

### Environment Variables

Fill in the following in your `.env.local`:

```bash
RESEND_API_KEY=
UPSTASH_REDIS_REST_URL=
UPSTASH_REDIS_REST_TOKEN=
NEXT_PUBLIC_SITE_URL=https://kidlatciviclabs.org
```

### Run Locally

```bash
npm run dev
# → http://localhost:3000
```

---

## Project Structure

```
src/
└── app/
    ├── page.js              # Homepage
    ├── about/               # About page
    ├── projects/            # Projects & case studies
    ├── research/            # Research & publications
    ├── contact/             # Contact page
    └── api/contact/         # Email API route
```

---

## Contributing

Please read our [Git Workflow Guidelines](./docs/git-guidelines.md) before contributing. All changes must go through a Pull Request — no direct commits to `main` or `staging`.

---

## Contact

**official@kidlatciviclabs.org**

---

*Kidlat CivicLabs — All Rights Reserved 2025*