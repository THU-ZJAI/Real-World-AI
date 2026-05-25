# Real-World AI

Real-World AI (RWAI) is an open-source project for collecting, evaluating, and sharing production-oriented AI best practices. It focuses on real implementation scenarios rather than abstract model benchmarks, helping teams understand what to build, how to deploy it, and how to evaluate whether it works in practice.

The project is initiated by the Artificial Intelligence Innovation Research Center at the Yangtze Delta Region Institute of Tsinghua University, Zhejiang.

## What This Project Provides

- **AI best-practice arena**: curated implementation cases for real business and operational scenarios.
- **End-to-end implementation guidance**: scenario descriptions, architecture notes, workflow design, technical configuration, and reusable implementation references.
- **Bilingual content**: Chinese and English pages powered by `next-intl`.
- **Static deployment support**: optimized for Cloudflare Pages, GitHub Pages, and other static hosting platforms.
- **Open content pipeline**: source materials live under `Content/`, with scripts for generating structured static data.

## Website Sections

- **Home**: project overview, value proposition, featured AI practices, and entry points.
- **Arena**: searchable best-practice cases covering industries, task types, verification status, highlights, implementation details, and technical configuration.
- **Framework**: RWAI-S framework, including task-set formalization, contextual alignment, human-in-the-loop, and human-AI symbiosis concepts.
- **About**: project background, initiating team, partners, and contact information.
- **FAQ**: common questions about project scope, participation, and reuse.

## Tech Stack

- **Framework**: Next.js 16 App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Internationalization**: next-intl
- **UI and animation**: Framer Motion, Radix UI, Lucide React
- **Charts**: Recharts
- **Content processing**: Markdown, JSON, XLSX, custom sync scripts

## Getting Started

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

## Common Commands

```bash
# Start local development
npm run dev

# Generate static JSON data from content files
npm run export-static-data

# Build the Next.js app
npm run build

# Build after syncing content
npm run build:sync

# Run lint checks
npm run lint

# Preview static export output
npm run start:static
```

## Static Build

This project supports static export through the `STATIC_EXPORT` environment variable. For static hosting, run:

```bash
STATIC_EXPORT=1 npm run export-static-data
STATIC_EXPORT=1 npm run build
```

The exported site is generated in:

```text
out/
```

For local static preview:

```bash
npm run start:static
```

## Cloudflare Pages Deployment

Recommended Cloudflare Pages settings:

```text
Framework preset: Next.js (Static HTML Export)
Build command: npm run export-static-data && npm run build
Build output directory: out
Root directory: /
Node.js version: 20
```

Environment variables:

```text
STATIC_EXPORT=1
NEXT_BASE_PATH=
NEXT_PUBLIC_BASE_PATH=
```

`NEXT_BASE_PATH` and `NEXT_PUBLIC_BASE_PATH` should usually stay empty on Cloudflare Pages because the site is served from the domain root.

## GitHub Pages Deployment

The repository also includes `.github/workflows/deploy.yml` for GitHub Pages static deployment. It runs on pushes to `main` and can also be triggered manually from GitHub Actions.

For GitHub Pages project-site deployment, the workflow sets the required base path automatically.

## Content Structure

```text
Content/
├── Homepage/              # Homepage source content
├── About/                 # About page source content
├── FAQ/                   # FAQ source content
├── Framework/             # Framework page source content
├── Arena/
│   ├── List of Arenas.*   # Arena index source files
│   ├── page.*.json        # Arena page structured content
│   └── All Arenas/        # Individual arena case content
└── Partners/              # Partner logos and images
```

Generated static data is written to:

```text
public/data/
├── arenas.json
└── arena-content.json
```

## Project Structure

```text
app/                       # Next.js App Router pages
components/                # Layout, UI, and visual components
i18n/                      # next-intl request configuration
lib/                       # Content loading, static data, types, utilities
locales/                   # UI translation dictionaries
public/                    # Public assets and generated static data
scripts/                   # Content sync and validation scripts
Content/                   # Source content and arena materials
PRD/                       # Product, design, QA, and workflow documents
```

## Content Update Workflow

When arena content or page copy changes:

```bash
npm run export-static-data
npm run build
```

Before publishing, check the generated files under `public/data/` and verify the static build.

## Contributing

Contributions are welcome in the following areas:

- New real-world AI implementation cases
- Improvements to arena content and evaluation dimensions
- UI, accessibility, and internationalization improvements
- Content pipeline and deployment improvements
- Documentation fixes

Please keep contributions focused on practical, reproducible AI implementation knowledge.

## Contact

For cooperation, feedback, or contribution discussions, contact:

```text
xuyuyao@tsinghua-zj.edu.cn
```

## License

License information will be provided by the project maintainers. Before commercial reuse, please confirm the applicable license and usage terms with the maintainers.
