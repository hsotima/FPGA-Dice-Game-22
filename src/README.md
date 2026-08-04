# Source Files

Schematic-entry sources for the "22" dice game, targeting an Intel MAX 10
`10M50DAF484C7G` on the Terasic DE10-Lite. Built with Quartus Prime 19.1
Lite Edition.

## Design hierarchy

`lab6.bdf` is the top level. It wires the board I/O to four functional blocks
and one shared decoder:

| File | Role |
| --- | --- |
| `lab6.bdf` | **Top level.** Connects `CLOCK_50`, `KEY[1..0]`, `SW[3..0]`, `HEX0/1/4/5` and `LEDR[9..0]` to the blocks below. |
| `control2.bdf` | Control FSM — nine states `S0`–`S8`, one-hot encoded. Consumes `roll`, `accept`, `reject`, `roll_6`, the score comparator flags and `turns_9`; drives `load`, `roll_en`, `turns_inc`, `win`, `lose_22`, `lose_turns`, `ready_to_roll`. |
| `Moore.bdf` | Die counter — a Moore machine cycling `roll_result[2..0]` at clock rate while the roll button is held. Also raises `roll_6`. |
| `scoreProcessingUnit.bdf` | Score datapath — BCD `tens`/`ones` accumulation using 7483 adders, 7485 comparators, 74163 counters and 74157 multiplexers. Produces `score_lt22`, `score_eq22`, `score_gt22`. |
| `turn_counter.bdf` | Turn counter built on a 74163, asserting `turns_9` on the final turn. |
| `lab2_sop1.bdf` | Seven-segment decoder, sum-of-products form. Reused from an earlier lab and instantiated by several blocks. |
| `lab6.qpf` | Quartus project file. |

Rendered views of each schematic are in [`../docs/schematics/`](../docs/schematics/).

## Building

```
1. Open lab6.qpf in Quartus Prime 19.1 or later.
2. Processing → Start Compilation   (Ctrl+L)
3. Tools → Programmer
4. Hardware Setup… → USB-Blaster [USB-x]
5. Select the .sof under output_files/ and click Start.
```

## Pin assignments

> **Note:** the project's `.qsf` is not committed, so **pin assignments are not
> included**. A fresh clone will compile but will not program to the board
> correctly until the DE10-Lite pins are assigned for `CLOCK_50`, `KEY[1..0]`,
> `SW[3..0]`, `HEX0`, `HEX1`, `HEX4`, `HEX5` and `LEDR[9..0]`.
>
> Use Assignments → Pin Planner, or import the pin assignments from the
> DE10-Lite system CD. The pin table is in the Terasic DE10-Lite user manual.

## A note on `.bdf`

`.bdf` is a Quartus-proprietary schematic format. GitHub renders it as an
unreadable text blob, so the files here are for opening in Quartus rather than
for reading on the web — see the exported renders in `docs/schematics/` for
anything you want to actually look at.
