# IRONFORGE Gym Website

A responsive, multi-section gym website with a dark and light theme, built with plain HTML, CSS and JavaScript. No frameworks or build tools needed.

## Features

- Dark and light theme that follows the device setting and remembers the visitor's choice
- Hero slideshow of gym equipment images
- Equipment section with 8 illustrated cards: dumbbells, barbells, kettlebells, treadmills, power rack and bench, battle ropes, cable machine and weight plates
- Exercise library with focus filters (Push, Pull, Legs, Core, Cardio), sets and reps, and form cues
- Weekly class timetable
- Coaches section
- BMI calculator
- Membership pricing with a monthly and yearly toggle
- Free trial form
- Fully responsive layout and reduced-motion support

## Project structure

```
ironforge-gym/
├── index.html
├── style.css
├── script.js
└── images/
    ├── dumbbell.svg
    ├── barbell.svg
    ├── kettlebell.svg
    ├── treadmill.svg
    ├── bench.svg
    ├── battle-rope.svg
    ├── cable-machine.svg
    └── weight-plates.svg
```

## Run locally

1. Unzip the project.
2. Open `index.html` in any browser.

## Deploy on GitHub Pages

1. Create a new repository, for example `ironforge-gym`.
2. Upload all the files, keeping the `images` folder.
3. Go to **Settings → Pages**.
4. Under **Branch**, choose `main` and `/ (root)`, then click **Save**.
5. Your site will be live at `https://syedhasanshahqadri-ops.github.io/ironforge-gym/`.

## Customize

- **Name, address, phone, prices:** edit `index.html` (contact and join sections) and the `plans` data in `script.js`.
- **Colors and fonts:** change the variables at the top of `style.css`.
- **Equipment, exercises, classes, coaches:** edit the data arrays in `script.js`.
- **Use real photos:** add your photos to `images/` with the same file names, for example `barbell.jpg`. Then change `.svg` to `.jpg` in the `img` helper in `script.js` and in the `<link rel="icon">` and logo image in `index.html`.

## Tech

- HTML5
- CSS3 (custom properties, grid, flexbox)
- Vanilla JavaScript
- Google Fonts: Barlow and Saira Stencil One

## Author

Syed Hasan Shah, Full Stack Web Developer · Graphic Designer · Video Editor# GYM-WEB
