# Schematic Renders

Exported images of each `.bdf`, so the design is readable on GitHub without
Quartus installed. Each file is named after the source schematic in
[`../../src/`](../../src).

| Render | Source | Contents |
| --- | --- | --- |
| [`lab6.png`](lab6.png) | `lab6.bdf` | Top level — board I/O wired to every block |
| [`control2.png`](control2.png) | `control2.bdf` | Nine one-hot state flip-flops and their next-state logic |
| [`Moore.png`](Moore.png) | `Moore.bdf` | Die counter — three flip-flops, `roll_result[2..0]` and `roll_6` |
| [`scoreProcessingUnit.png`](scoreProcessingUnit.png) | `scoreProcessingUnit.bdf` | BCD score datapath — 74163 counters, 7483 adders, 74157 muxes, 7485 comparators |
| [`turn_counter.png`](turn_counter.png) | `turn_counter.bdf` | 74163 counter and the `turns_9` decode |
| [`lab2_sop1.png`](lab2_sop1.png) | `lab2_sop1.bdf` | Seven-segment decoder, sum-of-products form |

Images are full resolution (roughly 2700–3100 px wide) with colour depth
reduced, which costs nothing on line art and keeps each file under 210 KB.

To regenerate after editing a schematic: open the `.bdf` in Quartus, then
`File → Export…` and choose PNG.
