# Optimasi Blending Batubara Berbasis Machine Learning

*Coal blending optimization with prediction under uncertainty (predict-then-optimize).*

Repository for undergraduate thesis research on machine learning-based coal blending optimization and supply chain modeling, with case study context from PT Adaro Andalan Indonesia Tbk (AAI), research heavily based on Financial Statement (FS) AADI and ATRI.

## Overview

Coal blending is the process of mixing coal from different pits, seams, and stockpiles to fulfill commercial contract specifications while minimizing quality giveaway and penalty risks. Unlike simplified linear assumptions, parameters like moisture (TM, IM), ash content, and Gross As Received (GAR) caloric values exhibit non-linear interactions during handling and storage.

This repository separates the public web deployment from the academic research materials.

## Repository Structure

```text
├── research/        # Academic thesis materials and study documents
│   ├── documents/   # Data proposals and thesis monograph template
│   ├── materials/   # Literature papers and company annual reports
│   └── notes/       # Research logs, session summaries, and analysis
├── web/             # Interactive visualizations and deployment assets
│   ├── index.html   # Primary entry point (Coal Supply Chain Map)
│   ├── peta-riset-skripsi.html # Research map: clickable BPMN, risk/Pareto labs, glossary
│   ├── *.html       # Process diagrams, GAR model, and value chain
│   ├── visual-checks/ # Automated browser evidence and test screenshots
│   └── vercel.json  # Scoped Vercel configuration
├── vercel.json      # Root Vercel deployment configuration
└── README.md
```

## Interactive Models

The `web/` directory contains standalone web tools built with vanilla JavaScript, Three.js, and CSS:

- **Research Map (`web/peta-riset-skripsi.html`)**: Start here when you need to explain the thesis. A clickable BPMN flow of the whole pipeline (contract, physics model, ML for realization deviation, optimization, evaluation) with a step-by-step walkthrough, two interactive labs (VaR/CVaR risk and Pareto/NSGA-II), a searchable glossary of technical terms with analogies, and a status board of what is decided vs. still an option.
- **Coal Supply Chain Map (`web/index.html` / `web/peta-rantai-batubara-adaro.html`)**: Interactive 3D visualization showing the end-to-end flow from pit and seam extraction, 89 km hauling road, Kelanis CPBL, barging along the Barito River, to Taboneo floating terminal and IBT Pulau Laut. Includes the embedded Blend Lab simulation.
- **GAR Coal Model (`web/model-gar-batubara.html`)**: Interactive tool demonstrating non-linear moisture and ash dynamics across DAF, DB, AD, and AR bases.
- **Blending Process Diagram (`web/diagram-proses-blending-batubara.html`)**: Detailed workflow diagram of stockpile blending.
- **GAR Value Chain Diagram (`web/rantai-nilai-blending-gar.html`)**: Value chain and blending decision points.

## Deployment

The web visualization is configured for static hosting on Vercel:

- When deploying from the repository root, `vercel.json` rewrites requests directly to `web/index.html`.
- Alternatively, you can set the Root Directory to `web` in the Vercel dashboard.

To preview locally:

```bash
# Open directly in a web browser
open web/index.html
```

## Author

Muhammad Arya Wiandra Utomo  
Computer Engineering, Faculty of Engineering, Universitas Indonesia
