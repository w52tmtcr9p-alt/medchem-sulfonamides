# MedChem Studio — Sulfonamides

An iPhone-first, installable Progressive Web App built from the uploaded 33-page Sulfonamides lecture PDF.

## Run locally

Because the app uses a service worker, serve this folder over HTTP (not `file://`). For example:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080` in a browser. On iPhone, host the folder on an HTTPS static host, open the URL in Safari, tap Share → Add to Home Screen. Once loaded, the app caches its core files for offline use.

## Included

- 33 slide records in original order, each with slide number, title, source-derived content, terms, and source limitation notes.
- 8 learning modules.
- Search and module filtering across slide content.
- Completion tracking, bookmarks, personal notes, recent slides, local persistence.
- pKa/ionization calculator for a monoprotic weak-acid teaching model.
- Folate pathway step explorer.
- Lecture-derived SAR feature explorer (schematic scaffold only).
- New 3D Molecular Lab with rotatable computational conformers for sulfanilamide, sulfathiazole, sulfamethoxazole, sulfisoxazole, sulfadiazine, sulfacetamide, sulfapyridine and trimethoprim.
- Color-coded 2D structures and 3D atom overlays: teal = shared para-aminobenzenesulfonamide pharmacophore; gold = variable substituent; trimethoprim shown as a separate scaffold.
- Curated analogue navigator displays documented drug names rather than inventing names for arbitrary substitutions.
- N-acetylation consequence chain.
- Drug directory populated only with lecture-supported facts.
- Binding interaction review.
- 12 source-linked randomized MCQs with explanations and score history.
- JSON export of local study progress.
- Dark/light appearance and service-worker caching.

## Scientific boundaries

- Original lecture statements are kept distinct from explanatory UI copy.
- The pKa calculator calculates ionized fraction only; it does not predict measured solubility, permeability, potency, or clinical outcomes.
- The legacy SAR drawing remains schematic. The new Molecular Lab uses RDKit-generated, energy-minimized conformers from PubChem-referenced SMILES. These are rotatable computational conformers, not experimental crystal structures or protein-bound poses.
- 3D rendering uses the 3Dmol.js browser library. The molecular data and color-coded 2D structures are bundled locally; the 3Dmol.js engine is loaded from its CDN and therefore requires an internet connection unless the browser has cached it.
- Several pages are image-led or contain question prompts without answers. These are flagged rather than filled with invented lecture content.
- Slide 14 wording about the enzyme named in Panel D is preserved as written in the source rather than silently reconciled.

## Quality/coverage report

- Source file: `01. Sulfonamides-Students-F26.pdf`
- PDF pages/slides: 33
- Slide records represented: 33/33
- Learning modules: 8
- Drug examples explicitly indexed: Prontosil Rubrum, sulfanilamide, sulfisoxazole, sulfamethoxazole, sulfadiazine, sulfacetamide, sulfadoxine, sulfathiazole, sulfapyridine, sulfasalazine, mesalamine, trimethoprim.
- Drug comparison entries: 7
- Interactive learning tools: 7 (pKa, folate pathway, SAR, 3D Molecular Lab, metabolism, drug comparison, binding interactions)
- MCQ bank: 12 questions
- Local persistence: localStorage
- Offline: service worker caches the app shell and core assets after first successful load.

## Manual review flags

- Slides 1, 6, 8, 9, 12, 13, 15, 16, 20, 23, 25, 29, 30, 31, 32 and 33 rely substantially on figures or diagrams; verify the original page image for fine structural labels and handwritten annotations.
- Slide 5 and slide 7 are question prompts without supplied answers.
- Slide 17 asks about intrinsic resistance but does not state the answer.
- Slide 25 contains only “Question” in the extractable text and requires manual inspection.
- The new 3D Molecular Lab displays computational conformers; these are not crystallographic structures and do not model ligand binding or predict activity. The external 3Dmol.js renderer needs an initial internet connection.

## Browser/device testing performed

- JavaScript syntax check (see delivery validation).
- Core UI is responsive with a mobile-first layout and safe-area bottom navigation.
- Progress and notes use browser localStorage.
- Service-worker registration and offline cache are implemented.

This is a PWA source project, not a compiled native SwiftUI/Xcode project. A native iOS build would require Xcode/macOS and a separate SwiftUI implementation.


## Molecular data provenance (new Molecular Lab)

Canonical/standard SMILES and compound identifiers used to construct the bundled educational models were checked against PubChem records for: sulfanilamide (CID 5333), sulfamethoxazole (CID 5329), sulfathiazole (CID 5340), sulfisoxazole (CID 5344), sulfadiazine (CID 5215), sulfacetamide (CID 5320), sulfapyridine (CID 5336), and trimethoprim (CID 5578). The 3D coordinates are locally generated computational conformers (RDKit ETKDG followed by MMFF/UFF optimization), not PubChem crystal structures.

The named analogue buttons are a curated selector of known compounds discussed or depicted in the lecture; they are not a reaction engine. No new compound name is generated for arbitrary substitutions.
