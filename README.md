# What's Overhead

A free, phone-friendly web page that shows which satellites are above you right now.

Live page: https://crb0229.github.io/overhead/

## What it does

- **Globe:** a 3D Earth with satellites on it, your location, and a circle showing how far away a satellite can be and still be seen from where you stand. Day and night are shaded. Tap a satellite to see its orbit ahead of it.
- **Look up:** a first-person view of the sky. Drag to look around, pinch to zoom, or tap "Point phone at sky" and the view follows where your phone points. Planets, the Moon, bright stars and the Milky Way are in this view only, and each can be turned off. The sky color follows the Sun.
- **Sky:** a flat star-map style chart centered on straight up.
- **Passes:** upcoming passes over the next 24 hours, including which are bright enough to see by eye.
- **Starlink trains:** freshly launched Starlink satellites that are still in a line.
- **Filters:** show only stations, Starlink, other constellations, navigation, weather, rocket bodies, debris or other, or only what is visible to the eye right now.
- **Shapes:** cross with panels = space station or Hubble, triangle = rocket body, x = debris, diamond = navigation, square = weather, dot = everything else.
- **Full screen** button, and a red-light mode that keeps your eyes dark-adapted outside.

"Use my location" fills in where you are. Without it, the page starts from a default spot and you can change it.

## Install it like an app

On a phone, open the page, then use Share, then Add to Home Screen. It opens without browser bars. It still needs the internet for orbit data.

## How it works

Everything runs in your browser. Nothing you do is sent anywhere, and your location stays on your device.

- Orbit data comes from [CelesTrak](https://celestrak.org). A scheduled GitHub Action (`.github/workflows/update-orbits.yml`) refreshes the files in `data/` once a day, and the page also tries CelesTrak directly.
- Satellite positions are worked out with [satellite.js](https://github.com/shashwatak/satellite-js).
- Planets and the Moon use [astronomy-engine](https://github.com/cosinekitty/astronomy).
- Star positions and constellation lines come from [d3-celestial](https://github.com/ofrohn/d3-celestial) data.
- The whole page is one file, `index.html`, hosted with GitHub Pages.

## Limits

- Orbit data is only as fresh as the last daily refresh. Predictions drift after a few days without new data.
- Whether a satellite is "visible to the eye" is an estimate based on sunlight on the satellite and how dark your sky is. Brightness is not calculated.
- Satellite types are guessed from catalog names, so a few land in the wrong group.
- Phone pointing depends on your phone's compass. If labels look rotated, aim at the Moon or a bright planet and tap Align.
- Debris is rarely visible to the eye, so only the brighter objects are loaded.
