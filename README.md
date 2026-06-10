# 🪐 3D Solar System Simulation

[Tiếng Việt](./README.vi.md) | English

An interactive 3D simulation of the solar system that runs entirely in the browser — no build step, no installation. Open the HTML file and explore the Sun, all 8 planets, 11 major moons, and a rocky asteroid belt rendered with real NASA-derived surface textures.

![Solar System Simulation](screenshot.png)

## ✨ Features

- **Full 3D scene** built with Three.js — drag to orbit the camera, scroll to zoom in and out
- **Fly-to navigation** — click any body in the 3D scene or in the left sidebar and the camera smoothly flies to it and follows it along its orbit
- **Real surface textures** for the Sun, all 8 planets, and major moons (Io, Europa, Ganymede, Callisto, Titan, Triton, the Moon...)
- **Info panel** — selecting a body opens a panel on the right with its photo, a short introduction, and key stats (diameter, distance, orbital period, number of moons)
- **11 major moons** orbiting their parent planets, including irregular potato-shaped Phobos and Deimos
- **Rocky asteroid belt** — 260 individually shaped and textured 3D rocks drifting between Mars and Jupiter, each tumbling on its own axis
- **Saturn's rings** rendered with a real ring texture, including visible ring divisions
- **Time control** — pause/resume and adjust simulation speed from 0 to 200 days per second, with a live simulation date display
- **Display toggles** — orbit lines, body labels, and the asteroid belt can each be switched on/off
- **Relative orbital speeds are accurate** — Mercury whips around while Neptune crawls, matching real period ratios
- Available in **two languages**: English (`index.html`) and Vietnamese (`index.vi.html`)

## 🚀 Getting Started

No dependencies to install. Just clone and open:

```bash
git clone https://github.com/<your-username>/solar-system-3d.git
cd solar-system-3d
```

Then open `index.html` (English) or `index.vi.html` (Vietnamese) in any modern browser.

> **Note:** An internet connection is required on first load — Three.js and the planet textures are fetched from public CDNs (cdnjs and jsDelivr). Without a connection the simulation still runs, but bodies fall back to solid colors.

For the best experience you can also serve it locally:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## 🎮 Controls

| Action | Effect |
|---|---|
| Drag mouse | Orbit the camera around the selected body |
| Scroll wheel | Zoom in / out |
| Click a body (3D or sidebar) | Fly to and follow that body |
| ❚❚ / ▶ button | Pause / resume time |
| Speed slider | 0–200 simulated days per second |
| ✕ on info panel | Close the introduction panel |

## 🛠️ Tech Stack

- [Three.js r128](https://threejs.org/) — WebGL rendering
- Vanilla HTML / CSS / JavaScript — single self-contained file per language, no framework, no bundler
- Custom spherical-coordinate camera controller with smooth fly-to interpolation
- DOM-overlay labels projected from 3D world positions each frame

## 📁 Project Structure

```
.
├── index.html       # English version
├── index.vi.html    # Vietnamese version
├── screenshot.png   # Preview image used in this README
├── README.md        # This file
└── README.vi.md     # Vietnamese README
```

## 🎨 Customization

All celestial data lives in one array near the top of the script — each body is a plain object:

```js
{
  name: 'Mars',
  r: 1.7,          // visual radius
  orbit: 64,        // visual orbit radius
  period: 687,      // real orbital period in days
  tex: 'mars.jpg',  // surface texture file
  desc: '...',      // intro text for the info panel
  stats: [...],     // key/value rows for the info panel
  moons: [...]      // nested moon objects
}
```

Add a dwarf planet, a comet, or extra moons by appending objects to this array — orbits, labels, sidebar rows, and the info panel are all generated automatically.

> Orbital distances and body sizes are compressed for visual clarity (a true-scale system would put Neptune ~30× farther out than Earth). Orbital period ratios, however, are real.

## 🙏 Credits

- Planet and moon textures from [KyleGough/solar-system](https://github.com/KyleGough/solar-system), served via jsDelivr — originally sourced from NASA imagery, [Solar System Scope](https://www.solarsystemscope.com/textures/), and [Planet Pixel Emporium](https://planetpixelemporium.com/)
- Built with [Three.js](https://threejs.org/)

## 📄 License

This project is released under the MIT License — see [LICENSE](./LICENSE) for details. Texture assets remain under their original authors' terms; please review the credited sources above before commercial use.

## 🤝 Contributing

Issues and pull requests are welcome! Ideas that would make great first contributions:

- Pluto and the Kuiper belt
- Comets with elliptical orbits and tails
- Real axial tilts (Uranus rolling on its side!)
- Earth cloud layer and city lights at night
- An in-app language switcher (VI/EN in one file)
- Touch controls for mobile
