# Virtual Memory Page Replacement Visualizer

An interactive, single-file web app that shows how an operating system decides which page to evict when physical memory is full. Pick an algorithm, enter a reference string, and step through every page fault and hit.

**No build step, no dependencies.** Open `index.html` in any modern browser.

## Features

- Four algorithms: **FIFO**, **LRU**, **Optimal (Belady's MIN)** and **Clock (Second Chance)**
- Step forward and back, play/pause with adjustable speed, jump to the end
- Frame-by-frame table: red cells are faults, green cells are hits
- Clock mode shows each frame's reference bit and the hand position (`*`)
- Live stats: faults, hits, hit ratio
- Side-by-side comparison of all four algorithms on the same input
- Presets: random reference string and **Belady's anomaly** (FIFO, 3 vs 4 frames)
- Light and dark themes (follows the system setting)

## Usage

1. Enter a reference string (numbers separated by spaces or commas), e.g. `7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1`
2. Choose the number of frames (1 to 10) and an algorithm
3. Click **Step**, or **Play** to animate
4. Scroll to the comparison panel to see all algorithms side by side

### Sample results (3 frames, string above)

| Algorithm | Page faults |
|-----------|-------------|
| FIFO      | 15 |
| LRU       | 12 |
| Optimal   | 9  |
| Clock     | 14 |

## How the algorithms work

| Algorithm | Evicts | Notes |
|-----------|--------|-------|
| FIFO | The page that has been in memory longest | Simple, but can suffer Belady's anomaly |
| LRU | The page unused for the longest time | Good in practice, needs usage tracking |
| Optimal | The page whose next use is farthest in the future (or never) | Needs future knowledge, so it is a benchmark only |
| Clock | First page found with reference bit 0, clearing bits as the hand sweeps | Cheap approximation of LRU |

## Project structure

```
index.html   # the whole app (HTML + CSS + JS)
README.md    # this file
Page_Replacement_Visualizer.pdf   # report with theory, examples and complexity
```

## Hosting on GitHub Pages

Push the files, then go to **Settings → Pages**, choose the `main` branch and root folder, and save. The visualizer will be live at `https://<username>.github.io/<repo>/`.

## License

MIT
