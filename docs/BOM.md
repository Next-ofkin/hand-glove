# Parts and sourcing

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **candidate shopping list; no order or purchase recorded**

**Scope: one LEFT glove and one RIGHT glove.** Quantities below include both hands. Each glove needs its own controller, reader, IMU, harness and later battery. The target receiver and test tools are shared.

The owner will source parts, favour Nigerian suppliers where suitable and import exact specialist parts when necessary. Listings are leads, not supplier commitments. Confirm part number, board revision, dimensions, stock, price and delivery before payment.

## Stage A: tools and exact board selection

| Item | Quantity | Before buying |
| --- | --- | --- |
| Computer and suitable USB data cables | 1 computer, 2 data cables | One cable per bench controller; Feather 4062 uses Micro-USB; check the actual boards received |
| Digital multimeter | 1 | Needed for continuity, polarity and voltage checks |
| Breadboards and jumper leads | 2 bench sets | One labelled LEFT and one RIGHT; headers may still need soldering |
| Fine insulated stranded wire, heat-shrink, strain relief and removable connectors | Enough for 2 sample harnesses | Select routing and connector pin counts separately before the full harnesses |
| Measuring tape, paper joint templates and sewing supplies | 1 shared tool set, 2 hand templates | Establish sensor-zone positions and glove fit on both hands |
| Soldering equipment | Technician access initially | Buying a personal soldering station is optional |

## Stage B: first two bench circuits and fitted samples

| Candidate part | Initial pair quantity | Purpose / purchase gate |
| --- | --- | --- |
| [Adafruit Feather nRF52840 Express, 4062](https://www.adafruit.com/product/4062) | 2, one per glove | Confirm upload/recovery tooling and headers. Direct page showed out of stock on 7 November; confirm distributor stock |
| [Nordic nRF52840 Dongle, PCA10059](https://www.nordicsemi.com/Products/Development-hardware/nRF52840-Dongle) | 1 target shared receiver | Custom firmware must serve both gloves. No onboard debugger; plan programming/recovery access. Two-source performance needs testing |
| [Adafruit BNO085 breakout, 4754](https://www.adafruit.com/product/4754) | 2, one per hand | Proposed SPI wiring and left/right mounting transforms still need specification |
| [CD74HC4067 module at Nerdshed](https://nerdshed.com.ng/product/16-channel-multiplexer-module-cd74hc4067/) | 2, one per glove | Listing showed ₦1,500 each on 7 November; ₦3,000 for two before delivery, subject to confirmation |
| [Microchip MCP6002](https://www.microchip.com/en-us/product/MCP6002) or a reviewed equivalent | 2, one per reader | Proposed analog buffers; package, circuit and settling must be checked |
| Divider resistors, decoupling capacitors and prototype board | Assortment for 2 circuits | Values and quantities follow both sample layouts and the schematic |
| [Taiwan Alpha MB090-A03 dual-zone samples](https://www.taiwanalpha.com/en/products/141) | Up to 4 total, 2 per hand | RFQ first; verify variant, active zones and each hand's fit before ordering |
| [Flexpoint short single-zone samples](https://flexpoint.com/bend-sensor/) | Up to 6 total, 3 per hand | RFQ first; trial distal-joint and thumb-base geometry on both hands |
| Donor stretch gloves or index/thumb fabric sleeves | 2 fitted samples, LEFT and RIGHT | One sample on each hand; do not assume an identical fit |
| Conductive fabric or suitable contact patches | 6 isolated patches, 3 per glove | Thumb common, index contact and middle contact on each hand; insulated signal leads |

The initial sample counts cover both hands while keeping the first order limited. They do not establish that standard sensor geometry fits either hand. Bench circuits can be brought up individually, but keep two real sample assemblies available for the simultaneous-use gate. A cheaper local sensor can help learn the reader circuit without validating the final joint layout.

Use USB power first. Add a battery once the circuit works on the bench.

## Stage C: after both index/thumb samples pass together

| Item | Per glove | Pair total / purchase gate |
| --- | --- | --- |
| Baseline sensing layout | 16 channels: 12 ordinary-finger flexion, 2 thumb flexion, 2 thumb-base | 32 channels across both hands |
| Candidate physical sensors | 5 dual-zone strips plus 6 short sensors | 10 dual-zone plus 12 short, subject to fit; subtract only confirmed reusable samples |
| Optional finger spread | 4 additional channels, deferred | 8 extra, making 40 total; revise both readers before ordering |
| Protected single-cell LiPo | 1 suitable 3.7 V cell; 500 mAh initial candidate | 2 independent cells; capacity is not a runtime promise |
| Charging/power system | Board-supported charging first; one designed USB-C charging/power circuit in final pod | 2 independent charging paths, one per battery; final circuits replace development packaging |
| Haptic motor, if fitted | 1 coin motor plus rated driver, protection and decoupling | 2 motors and 2 driver sets, separately addressable |
| Harness and glove | 1 fitted textile and removable wiring harness | 2, independently sized and labelled LEFT / RIGHT |
| Wrist and hand covers | 1 wrist enclosure/cuff and 1 hand IMU cover | 2 wrist sets and 2 hand covers; check each fit |
| Compact PCB assemblies | 1 wrist controller/power/reader PCB plus 1 hand sensor PCB | 2 wrist and 2 sensor PCBs after validation; geometry may differ by hand |

Never connect two separate charger circuits to the same battery as an improvised upgrade. Confirm battery protection, charge-current compatibility and connector polarity from the actual parts.

## Nigerian sourcing leads

| Supplier / route | Useful for | Status |
| --- | --- | --- |
| [Hub360](https://hub360.cc/), Oshodi, Lagos | Standard electronics, boards, batteries, tools and consumables | Catalogue/source lead; exact glove parts need confirmation |
| [Nerdshed](https://nerdshed.com.ng/), Ikeja, Lagos | Selector module and general components | Selector listed; confirm remaining items individually |
| [Circuit Mall 2.2-inch flex sensor](https://circuitmall.ng/product/flex-sensor-2-2-inches/) | A possible basic sensor experiment | Listing found; price, stock and suitability need confirmation; not a joint-specific replacement |
| Local glove/textile sample maker | Breathable glove, fabric channels and cuff | Obtain a quote after measurements |
| [Damza Technologies](https://damzatechnologies.com/contact/), Yaba, Lagos | Enclosure printing from agreed CAD files | Quote required; no complete glove-build service assumed |

Specialist dual-zone/short sensors and the exact Nordic/IMU boards may need importing. No supplier has been contacted or paid as part of this update.

## Questions for sensor quotations

Request exact model and active sensing-zone dimensions, termination method, minimum bend radius, recommended mounting, repeatability/hysteresis information, recommended reading circuit, sample quantity, MOQ, lead time and delivery to Nigeria.

Ask whether custom geometry is needed before placing a full-glove order.

## Budget record

A complete naira total is not available. The earlier ₦40,000 basic-prototype target does not cover this design.

For each quote, record per-glove and pair quantities, currency, dated unit price, shipping, import charges, labour and actual landed cost in [BUILD-LOG.md](BUILD-LOG.md). Charge shared tools and the target receiver once; budget hand-specific electronics and fabrication twice. Do not simply double the earlier incomplete prototype estimate.

Manufacturer and supplier links are references. Recheck availability when ordering.
