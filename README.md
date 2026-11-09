# Chip Lab

**An interactive lab for understanding how computers work, from a single transistor up to CPUs, GPUs and AI chips, and how that hardware shows up in everyday code.**

An [AP Tensor Lab](https://github.com/aparve08) project · **[Try it live →](https://aparve08.github.io/chip-lab/)**

![Live chip: zoom from the whole die down to one transistor](docs/live-chip.png)

---

## What's inside

| Mode | What you do |
|---|---|
| **Learn** | 9 short lessons: bits → logic gates → adders → a 4-bit adder → memory (SR latch). Every circuit is live, with a truth table and readout. |
| **Build** | Wire gates together, test them, and save them as reusable chips. Chips can contain other chips. Includes undo/redo, a hex display, a clock, and export/import. |
| **Live chip** | A running chip you can zoom into: die → CPU core / GPU / NPU / L3 cache → adders, multipliers and memory cells → NAND gates → a single transistor. Plus a **race**: the same matrix multiply on a CPU, a GPU and an NPU. |
| **For devs** | 10 labs linking code to hardware: integer overflow, floating point, bitwise ops, cache locality, branch prediction, race conditions, struct padding & endianness, the call stack, virtual memory and SIMD. Plus a **Number inspector** tool. |
| **Transistor view** | The real CMOS circuit inside NOT, NAND, NOR, AND, OR, XOR and XNOR, with transistors switching live. |

New here? Open the page and follow **Start here**. Difficulty tags (Beginner / Intermediate / Deep dive) and tap-to-define glossary terms help you pick a path.

| Learn | For devs |
|---|---|
| ![Learn mode: 4-bit adder](docs/learn.png) | ![For devs: cache locality lab](docs/for-devs.png) |
| **Race: CPU vs GPU vs NPU** | **Transistor view: XOR** |
| ![Race](docs/race.png) | ![Transistor view](docs/transistor-view.png) |

## Run it

It's a single HTML file with no dependencies, no build step and no server.

```bash
git clone https://github.com/aparve08/chip-lab.git
open chip-lab/index.html        # or just double-click it
```

Saved chips and progress live in your browser's `localStorage`. Use **Build → Export / Import** to move them between devices.

## How it works

- **Gate-level simulator:** circuits are JSON (`nodes` + `wires`), evaluated in topological order and settled until stable, so feedback loops like latches work. Custom chips run as nested simulators.
- **Switch-level CMOS solver:** transistors join nets through union-find; a net connected to VDD is 1, to GND is 0, otherwise floating.
- **Zoom engine:** a stack of frames; each level derives its live values from its parent, so every level shows part of the same running calculation.
- **Rendering:** plain SVG and DOM, no libraries. Light and dark mode.

## A teaching model, not a real chip

Scales are shrunk (a 4×4 NPU, 32-lane GPU clusters, a 16×8 SRAM bank) and figures such as transistor counts, clock speed and memory latencies are typical round numbers. Each screen notes where real hardware does more, such as carry-lookahead adders, out-of-order cores and tensor cores.

## Credits

Created by **Arveend** ([AP Tensor Lab](https://github.com/aparve08)). Built with **Claude** (Anthropic) as a coding partner.

## License

[MIT](LICENSE)