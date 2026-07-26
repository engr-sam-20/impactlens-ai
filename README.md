# ImpactLens AI

An intelligent evaluation framework and strategic report generator for social innovations, non-profit initiatives, and impact ventures. Powered by **Google Gemini 3.6 Flash** and benchmarked against the **United Nations Sustainable Development Goals (SDGs)** framework.

Live Application: [https://impactlens-ai.ai.studio/](https://impactlens-ai.ai.studio/)

## Overview

Translating early-stage social impact concepts into investor-ready, grant-compliant proposals is often a time-consuming barrier for founders, NGOs, and grant writers. **ImpactLens AI** streamlines this evaluation process by providing structured multi-dimensional analysis, root-cause identification, stakeholder mapping, risk mitigation matrices, and operational roadmaps within seconds.

## Core Capabilities

- **Problem & Root Cause Deconstruction**: Analyzes underlying economic, structural, and regulatory drivers behind complex societal challenges and assigns severity ratings with actionable rationale.
- **UN SDG Alignment & Benchmarking**: Quantifies project alignment across all 17 UN Sustainable Development Goals, providing specific target level justifications and alignment ratios.
- **Executive Scoring Matrix**: Evaluates projects across 4 critical pillars: *Feasibility*, *Impact Potential*, *Innovation*, and *Long-Term Sustainability* (0-100 scale).
- **Stakeholder & Value Proposition Mapping**: Identifies primary beneficiaries, demographic profiles, key ecosystem stakeholders, and custom incentive alignment strategies.
- **Risk Analysis & KPI Framework**: Breaks down operational, technical, financial, and adoption risks alongside practical mitigations and measurable primary/secondary target metrics.
- **90-Day Phased Execution Plan**: Generates an interactive, milestone-driven execution roadmap split into 30, 60, and 90-day pilot phases.
- **Context-Aware AI Advisory Chat**: An integrated side drawer that acts as a senior social innovation consultant. Users can ask follow-up questions, draft donor pitches, outline pilot budgets, or generate grant application answers.
- **Export & Saved Reports Library**: Allows saving reports locally for quick reference, searching and filtering past evaluations, and exporting formatted Markdown or print-ready PDF reports.
- **Interactive SDG Reference Explorer**: A built-in index to search and inspect official targets, background details, and metrics for all 17 United Nations SDGs.

## Architecture & Technology Stack

The application is structured as a full-stack Node.js and React application with server-side proxying to keep Gemini API credentials secure.

- **Frontend**: React 19, TypeScript, Vite, Tailwind CSS v4, Lucide React
- **Backend**: Node.js, Express, `esbuild` bundling
- **AI Integration**: `@google/genai` SDK querying the `gemini-3.6-flash` model
- **Persistence**: Browser `localStorage` for offline report bookmarking
- **Security**: Server-side proxy architecture (`/api/analyze` and `/api/chat-refine`) ensuring `GEMINI_API_KEY` is never exposed in client bundles

## Directory Layout

```
├── server.ts               # Express backend handling Gemini API proxy routes & static file serving
├── src/
│   ├── App.tsx             # Main layout & navigation state controller
│   ├── types.ts            # Core TypeScript interfaces & domain models
│   ├── index.css           # Tailwind CSS directives & custom print styles
│   ├── data/
│   │   ├── sdgs.ts         # UN Sustainable Development Goals dataset
│   │   └── samples.ts      # Sample social innovation presets for testing
│   └── components/
│       ├── Navbar.tsx      # Top bar navigation & saved count indicator
│       ├── Hero.tsx        # Application header & quick CTA
│       ├── IdeaForm.tsx    # Multi-field proposal submission form
│       ├── LoadingState.tsx# Progress feedback during analysis generation
│       ├── ReportView.tsx  # Multi-tab generated report viewer
│       ├── ChatDrawer.tsx  # Interactive AI consultant chat interface
│       ├── SavedReports.tsx# Searchable local report library
│       ├── SDGExplorer.tsx # Interactive 17 SDGs guide
│       └── Footer.tsx      # Minimal footer
├── metadata.json           # Application platform configuration
└── package.json            # Node.js dependencies and script definitions
```

## Getting Started

### Prerequisites

- **Node.js**: v18.x or higher
- **npm**: v9.x or higher
- **Google Gemini API Key**: Obtainable from [Google AI Studio](https://aistudio.google.com/)

### Environment Setup

1. Clone the repository and navigate to the project directory:
   ```bash
   git clone https://github.com/your-username/impactlens-ai.git
   cd impactlens-ai
   ```

2. Create a `.env` file in the root directory:
   ```bash
   cp .env.example .env
   ```

3. Add your Gemini API key to `.env`:
   ```env
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

### Installation & Development Server

1. Install project dependencies:
   ```bash
   npm install
   ```

2. Start the development server (runs on port 3000 by default):
   ```bash
   npm run dev
   ```

3. Open `http://localhost:3000` in your web browser.

## Production Build & Deployment

To bundle the client assets and compile the Express server for production:

```bash
npm run build
npm start
```

- `npm run build` triggers `vite build` for client assets followed by `esbuild` to compile `server.ts` into a standalone CommonJS bundle at `dist/server.cjs`.
- `npm start` executes `node dist/server.cjs` on port 3000.

## License

Distributed under the Apache-2.0 License. Built for social entrepreneurs, changemakers, and impact organizations worldwide.
