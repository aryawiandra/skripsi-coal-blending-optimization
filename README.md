# Coal Blending Optimization

Repository for undergraduate thesis research on machine learning-based coal blending optimization and supply chain modeling, with case study context from PT Adaro Andalan Indonesia Tbk (AAI).

## Overview

Coal blending is the process of mixing coal from different pits, seams, and stockpiles to fulfill commercial contract specifications while minimizing quality giveaway and penalty risks. Unlike simplified linear assumptions, parameters like moisture (TM, IM), ash content, and Gross As Received (GAR) caloric values exhibit non-linear interactions during handling and storage.

This repository hosts research notes, data request proposals, reference materials, and interactive simulation tools.

## Repository Structure

```text
├── documents/       # Data proposals and thesis monograph template
├── materials/       # Literature papers and company annual reports
├── notes/           # Research logs, session summaries, and analysis
├── visual-checks/   # Automated browser evidence and test screenshots
├── visualizations/  # Interactive 3D and 2D web models
└── vercel.json      # Vercel deployment configuration
```

## Interactive Models

The `visualizations/` directory contains standalone web tools built with vanilla JavaScript, Three.js, and CSS:

- **Coal Supply Chain Map (`peta-rantai-batubara-adaro.html`)**: Interactive 3D visualization showing the end-to-end flow from pit and seam extraction, 89 km hauling road, Kelanis CPBL, barging along the Barito River, to Taboneo floating terminal and IBT Pulau Laut. Includes the embedded Blend Lab simulation.
- **GAR Coal Model (`model-gar-batubara.html`)**: Interactive tool demonstrating non-linear moisture and ash dynamics across DAF, DB, AD, and AR bases.
- **Blending Process Diagram (`diagram-proses-blending-batubara.html`)**: Detailed workflow diagram of stockpile blending.
- **GAR Value Chain Diagram (`rantai-nilai-blending-gar.html`)**: Value chain and blending decision points.

## Deployment

The web visualization is configured for static hosting on Vercel via `vercel.json`. Root requests (`/`) automatically route to `peta-rantai-batubara-adaro.html`.

To preview locally:

```bash
# Open directly in a web browser
open visualizations/peta-rantai-batubara-adaro.html
```

## Author

Muhammad Arya Wiandra Utomo  
Computer Engineering, Faculty of Engineering, Universitas Indonesia
