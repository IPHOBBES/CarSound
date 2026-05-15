# CarSound — activity POC

A lightweight **touch kiosk**: cars sit on a “road” glow over a background image; **tap a car** to play its engine sound. Designed as a **proof-of-concept** for an interactive activity — single-page HTML, no build step.

---

## For participants (end users)

1. **Open the experience**  
   Someone will load `CarSound` on a tablet or kiosk (usually fullscreen).

2. **Tap a car**  
   Each car plays its own sound. Only one sound plays at a time.

3. **That’s it**  
   There are no visible menus during normal use — just the scene and the cars.

*(Optional detail for hosts: a small gear icon appears in the corner for setup only; participants don’t need to use it.)*

---

## For facilitators & team (“us”)

### Running it

- **Important:** Open **`index.html` from the project root** (`CarSound/index.html`), not from inside `Assets/`.  
  Paths assume **`cars/`**, **`sounds/`**, and **`background.jpg`** live **next to** `index.html`.

- **Local file:** Double-click `index.html` or use “Open file” in the browser. Some browsers restrict autoplay/audio less once the user has tapped.

- **More reliable:** Serve the folder with any static server (e.g. `npx serve .` from the `CarSound` folder) so URLs stay consistent on tablets.

### Layout / tuning (hidden controls)

- **Open the Layout panel:** **five quick taps** on the **gear** (bottom-right), **or** add **`?layout=1`** to the URL (e.g. `index.html?layout=1`).

- **Road glow:** opacity, width, vertical position, line thickness, optional **glow animation** (toggle + strength).

- **Car focus:** idle vs dimmed opacity when a sound is playing, plus **wobble** strength on the active car.

- **Per car:** position (**TOP / LEFT**) and size (**WIDTH**); add/remove cars; paths shown for image + sound files.

### Persistence & reset

- Layout choices are saved in the browser’s **`localStorage`** on that device (road, cars, focus). Clearing site data or another browser profile starts fresh.

- **Reset** in the panel restores built-in defaults (cars + road + focus sliders).

- **Copy JSON** exports the current scene — useful for backing up a tuned layout or sharing between machines (paste/edit manually if needed).

### Assets

| Location | Role |
|----------|------|
| **`background.jpg`** (next to `index.html`) | Full-screen backdrop |
| **`cars/carN.png`** | Car images |
| **`sounds/engineN.mp3`** | Audio per car |

**Adding a car:** **+ Add car** picks the next index (`car4.png` / `engine4.mp3`, etc.). Put matching files in **`cars/`** and **`sounds/`** before relying on that slot.

**`Assets/` folder (here):** Working PSDs, older experiments (`Old index/`), or exports — **not** what the live page loads by default. The running POC reads from the **repo root** paths above.

### Accessibility

- **Reduce motion:** If the OS requests reduced motion, **car wobble** and **road glow pulse** are toned down or disabled per browser/CSS rules.

---

## Technical snapshot

- **Single file:** `index.html` (inline CSS + JS).

- **No npm / build** — copy the folder to a device or host statically.

- **Modern browsers:** Uses `localStorage`, CSS variables, and Web Audio via `<audio>`.

---

## Contact / ownership

Keep this README with the repo so whoever runs the activity knows **how to open the app**, **how to tune it**, and **what “tap the car” means** for participants.
