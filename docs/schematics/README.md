# Schematic Renders

Exported PNG or PDF images of each `.bdf` go here, so the design is viewable
on GitHub without Quartus installed.

Suggested naming, one file per schematic sheet:

```
top-level.png          Top-level block diagram
control-fsm.png        9-state control FSM
die-counter.png        Moore machine die counter
score-unit.png         7483 adders / 74163 registers / 7485 comparator
turn-counter.png       Turn counter and turns_9 decode
```

Export from Quartus: open the `.bdf`, then `File → Export…` and choose PNG.
For dense sheets, PDF stays legible when zoomed where PNG does not.
