# Under the Oasis

A virtual exhibition on Morocco's khettaras: underground tunnels that carry groundwater for kilometres to the oases, moved by gravity alone.

**Live site:** https://aminebrr.github.io/Khettara/

The page explains how a khettara works, how families share its water, and why many are drying up. At its centre is an interactive 3D model. Lower the water table and you can watch the part of the tunnel that still captures water shrink.

The exhibition is designed as a deep-dive companion to the Morocco case in *The Voices of Water*, the Global Network of Water Museums exhibition on UNESCO's Virtual Science Museum. It is a work sample by Amine Brahimi, not an official UNESCO publication.

## What's on the page

- **3D model.** Turn the model, tap the labels (mother well, shafts, gallery, water table, outlet, palm grove) and test four scenarios, from rainy years to an exhausted aquifer.
- **History.** How the qanat spread from Persia to Marrakech and the Tafilalet.
- **Sharing.** Water measured in time: the nouba and the tanast, a pierced bowl that sinks in about 45 minutes.
- **Figures.** How many khettaras still flow, shown as a field of 570 dots with 304 lit, each figure linked to its source.
- **The dilemma.** Some communities pump groundwater into their khettara to keep it alive, but the same pumps lower the water table further.
- **Three lessons for ages 11 to 15.** Science, maths and citizenship activities that use simple classroom materials.
- **Sources.** Nine references: research papers, UNESCO documents and water museum material.

The whole page is in English and French, with a language switch at the top.

## How it's built

- One self-contained `index.html` file, with no build step and no framework.
- [three.js](https://threejs.org/) 0.160 (loaded from jsDelivr) for the model. The terrain, tunnel, palm grove and village are all generated in code, and so are their textures (sand ripples, gravel, rammed earth, soil grain), so the repository has no texture files.
- The two "before and after" pictures are rendered from the same 3D scene in the browser.
- Photographs come from Wikimedia Commons under CC BY-SA licences, credited beside each image and in the sources list.
- Fonts: Source Serif 4, Archivo and Noto Naskh Arabic (Google Fonts).
- Accessibility:
  - keyboard navigation and a skip link
  - text alternatives for the model and pictures
  - a reduced-motion mode
  - a written description if WebGL is unavailable

## Accessibility

The page aims at WCAG 2.2 AA: keyboard access to everything, including the 3D model through viewpoint and zoom buttons; a text description and diagram of the model; alt text for every photograph; reduced-motion support; and English, French and Arabic marked up with the right `lang` and direction. See [ACCESSIBILITY.md](ACCESSIBILITY.md) for the audit, the changes and what still needs testing by hand.

## Run it locally

Clone the repository and serve the folder with any static server. The page needs an internet connection for three.js, the fonts and the photographs.

```bash
git clone https://github.com/aminebrr/Khettara.git
cd Khettara
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Sources

Every figure on the page links to its source in the "Sources and further reading" section. The main references are:

- Global Network of Water Museums / Museum of Water Civilisation in Morocco, *Moroccan khettaras*
- Beraaouz et al. (2022), *Khettaras in the Tafilalet oasis (Morocco)*, Built Heritage
- Khardi et al. (2023), *Pumping or disappearing*, Cahiers Agricultures
- UNESCO World Heritage Committee (2016), *The Persian Qanat*

## Author

Amine Brahimi, communication and cultural mediation.
Portfolio: https://aminebrr.github.io/Portfolio/

---

*Sous l'oasis* : une exposition virtuelle sur les khettaras du Maroc, avec une maquette 3D interactive. Le site est entièrement bilingue (français / anglais).
