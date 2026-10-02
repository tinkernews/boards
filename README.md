# TinkerNews Boards — open dev-board dataset

Machine-readable data for **3,000+ microcontroller and single-board computers**,
built for makers: who makes it, which chip it runs, its **GPIO/pin map** (with
alternate names like `SDA`, `NEOPIXEL`, `TX`), and its **software support status**
(CircuitPython and friends). 565 makers, 2,673 MCUs and 421 SBCs.

This is the dataset behind the [TinkerNews boards explorer](https://www.tinkernews.com/boards) —
free to use under CC BY 4.0 in your own tools, configs, and projects.

## What's inside

| | |
|---|---|
| `data/boards.json` | All boards in one array — the easy entry point |
| `data/imported/*.json` | One file per board (2,900+), stable `slug` filenames |
| `data/curated/*.json` | Hand-curated board records |
| `data/aliases.json` | Alternative names → canonical board slugs |
| `data/promoted.json` | Curator's featured boards |

**Coverage:** 3,094 boards · 565 makers · 2,986 with software-support data · 591 with full pin maps. Top chips: ESP32 (189), ESP32-S3 (164), RP2040 (148), ATSAMD21 (112), nRF52840 (99), ESP32-S2 (78), RP2350 (53), ATmega328P (47), ESP32-C3 (47), ESP8266 (44).

## Schema

```json
{
  "slug": "01space-esp32-c3-0-42lcd",
  "name": "ESP32-C3-0.42LCD",
  "tier": "imported",
  "kind": "mcu",
  "maker": "01space",
  "chip": "esp32-c3",
  "ids": { "circuitpython": ["01space_lcd042_esp32c3"] },
  "software": [
    { "platform": "circuitpython", "status": "supported",
      "url": "https://circuitpython.org/board/01space_lcd042_esp32c3/" }
  ],
  "pins": {
    "source": "circuitpython-pins:01space_lcd042_esp32c3",
    "list": [
      { "pin": "GPIO2", "names": ["NEOPIXEL", "IO2"] },
      { "pin": "GPIO5", "names": ["SDA", "IO5"] }
    ]
  }
}
```

## Quick start

```python
import json

boards = json.load(open("data/boards.json"))
esp32 = [b for b in boards if (b.get("chip") or "").startswith("esp32")]
for b in esp32[:5]:
    print(b["name"], "-", b.get("maker"), "-", b["slug"])
```

## Ideas

- Board pickers, pinout cards, or config generators for PlatformIO/Arduino/ESPHome
- "Which board has SDA on GPIO5?"-style tooling
- Dataset joins with your own inventory or shop data

---

### 📬 From TinkerNews — a free weekly DIY electronics newsletter

This dataset is curated by **[TinkerNews](https://www.tinkernews.com/?utm_source=github&utm_campaign=boards-repo)**,
a **free weekly email newsletter** featuring the best DIY electronics builds on the
web — ESP32, Arduino, Raspberry Pi, robotics and IoT projects, with honest hardware
notes and links to every source.

- **Subscribe free → [tinkernews.com](https://www.tinkernews.com/?utm_source=github&utm_campaign=boards-repo)** — one issue every Sunday, no spam, unsubscribe anytime.
- **Explore these boards in your browser → [tinkernews.com/boards](https://www.tinkernews.com/boards?utm_source=github&utm_campaign=boards-repo)**
- Listening is easier: there's a [podcast edition](https://tinkernews.github.io/tinkernews-digest/podcast.xml) too.

If this dataset saved you time, the newsletter will too. ⭐ stars appreciated.

## License

Data: [CC BY 4.0](LICENSE) — share and adapt, with attribution to TinkerNews
(link to tinkernews.com is enough).
