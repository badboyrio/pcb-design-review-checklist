# PCB design review checklist

Project: ______  Revision: ______  Reviewer: ______  Date: ______


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

Source: https://github.com/badboyrio/pcb-design-review-checklist (CC BY 4.0)
