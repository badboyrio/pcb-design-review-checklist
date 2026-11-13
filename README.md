# PCB Design Review Checklist (42 checks before fab)

A free, printable checklist for reviewing a printed circuit board before you send it to fabrication. It works for Altium Designer, KiCad, Cadence Allegro/OrCAD or any other EDA tool.

A clean DRC only proves the board follows your tool's rules. It does not prove the board works. These 42 checks catch the faults that cause respins: wrong part variants, floating strap pins, footprints that don't match the datasheet, planes with gaps under fast signals and output files that don't match the design.

Maintained by [Circuit Board Design](https://www.circuit-board-design.com), the PCB design division of [Electuni LLC](https://www.electuni.com). Full write-up with the reasoning behind each check: [PCB design review checklist: the checks we run before fab](https://www.circuit-board-design.com/blog/pcb-design-review-checklist-checks-we-run-before-fab-r7k2).

## How to use it

- Copy `CHECKLIST.md` into your project repo and tick items in a pull request, or import `checklist.csv` into a spreadsheet.
- Run it at three gates: schematic freeze (pass 1-2), after placement (pass 3), and before release (all passes on the final outputs).
- Rank every finding:
  - **Critical**: the board won't work, can't be built or is unsafe.
  - **Major**: it may work on the bench but will likely need a respin or rework.
  - **Minor**: style or documentation. Doesn't block the build.
- Release to fab only with zero open Critical and Major findings.

## The checklist

### Pass 1: Schematic intent

- [ ] **1.** Absolute maximum ratings hold on every active pin across the full input range, including startup and hot plug. *(Critical)*
- [ ] **2.** Power stage values (feedback divider, frequency resistor, inductor, output capacitance) match the datasheet equations. *(Critical)*
- [ ] **3.** Boot and strap pins select the intended mode at power-up. *(Critical)*
- [ ] **4.** Signal direction is correct on every interface, including isolators, level shifters and buffers. *(Critical)*
- [ ] **5.** No floating inputs. Enables, resets and unused inputs are tied the way the datasheet says. *(Major)*
- [ ] **6.** Pull-ups exist where needed and are sized for the bus speed. *(Major)*
- [ ] **7.** Power sequencing and reset timing meet the processor requirements. *(Major)*
- [ ] **8.** User-facing connectors have ESD protection. Power inputs have reverse polarity and overcurrent protection. *(Major)*
- [ ] **9.** The board can be programmed and debugged. Every rail has a test point. *(Major)*
- [ ] **10.** ERC is clean and every waived warning has a written reason. *(Major)*

### Pass 2: BOM and parts

- [ ] **11.** Full part numbers including suffixes match the variant the schematic needs. *(Critical)*
- [ ] **12.** Every BOM package matches its footprint. *(Critical)*
- [ ] **13.** No NRND or obsolete parts. *(Major)*
- [ ] **14.** Voltage, power and temperature ratings have margin. MLCC capacitance checked at real DC bias. *(Major)*
- [ ] **15.** DNP parts are marked the same way in schematic, BOM and assembly drawing. *(Major)*
- [ ] **16.** Common parts have stock and a second source. *(Minor)*

### Pass 3: Footprints and placement

- [ ] **17.** Footprints match the datasheet land pattern: pad size, pitch, pin 1 and thermal pad. *(Critical)*
- [ ] **18.** Connector orientation and mating side match the mechanical drawing or enclosure model. *(Critical)*
- [ ] **19.** Mounting holes, keepouts and component heights fit the enclosure. *(Major)*
- [ ] **20.** Decoupling capacitors sit close to their pins with short ground paths. *(Major)*
- [ ] **21.** Wireless modules have the antenna keepout their datasheet asks for. *(Major)*
- [ ] **22.** Hot parts have enough copper or thermal vias and sit away from heat-sensitive parts. *(Major)*
- [ ] **23.** Pin 1 and polarity marks are still visible after assembly. *(Minor)*

### Pass 4: Routing, power and return paths

- [ ] **24.** No unrouted nets, no orphan copper in pours, thermal relief on plane pads that get hand soldered. *(Critical)*
- [ ] **25.** Creepage and clearance on high-voltage nets meet the safety standard that applies. *(Critical)*
- [ ] **26.** Trace widths carry the real current at the ordered copper weight. *(Major)*
- [ ] **27.** The switching regulator hot loop is as tight as the layout guide shows. *(Major)*
- [ ] **28.** No fast signal crosses a gap in its reference plane. *(Major)*
- [ ] **29.** Controlled-impedance traces match the stackup the fab confirmed. *(Major)*
- [ ] **30.** Differential pairs are routed together and length-matched to the interface spec. *(Major)*
- [ ] **31.** Analog inputs, crystals and sensitive nodes are kept away from switch nodes and clocks. *(Major)*

### Pass 5: DFM and fab rules

- [ ] **32.** DRC runs with the fab's published rules, not the tool defaults. *(Critical)*
- [ ] **33.** Copper is clear of the board edge, slots and V-score lines. *(Major)*
- [ ] **34.** Solder mask dams exist between fine-pitch pads. Via tenting is a deliberate choice. *(Major)*
- [ ] **35.** Vias in pads are filled and capped, or moved out of the pad. *(Major)*
- [ ] **36.** Fiducials and panelization match what the assembler asks for. *(Minor)*

### Pass 6: Output files

- [ ] **37.** Gerbers open in a viewer with every layer present, unmirrored, outline on the right layer. *(Critical)*
- [ ] **38.** The drill file matches the board holes. Plated and non-plated holes are separate. *(Critical)*
- [ ] **39.** The fab drawing states stackup, material, finish, copper weight, impedance targets and tolerances. *(Major)*
- [ ] **40.** Pick-and-place has the right origin, rotation and side for every part. *(Major)*
- [ ] **41.** Netlist and BOM in the release match the schematic of record. *(Major)*
- [ ] **42.** The revision on copper or silkscreen matches file names and release notes. *(Minor)*

## Related guides

- [PCB design deliverables: the complete handoff package](https://www.circuit-board-design.com/blog/pcb-design-deliverables-complete-handoff-package-h4d8)
- [Moving Eagle boards to KiCad or Altium](https://www.circuit-board-design.com/blog/eagle-to-kicad-migration-moving-eagle-boards-to-kicad-or-altium-e7m4)
- [EVT, DVT and PVT explained for hardware startups](https://www.electuni.com/guides/evt-dvt-pvt)
- [Hardware product development timeline](https://www.electuni.com/guides/hardware-product-development-timeline)

## Want a second set of eyes?

Circuit Board Design offers a free quick check of your board before fab (checklist-level notes in 2 business days). See [design review](https://www.circuit-board-design.com/services/design-review).

## Contributing

Found a check that saved one of your boards? Open an issue or a pull request. Keep each item testable: one thing a reviewer can confirm as yes or no.

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it, adapt it, put it in your company's release process. Please keep a link back to this repo.
