# Parts and sourcing

Updated: **7 November 2026 (Africa/Lagos)**  
Status: **candidate shopping list; no order or purchase recorded**

The owner will source parts, favour Nigerian suppliers where suitable and import exact specialist parts when necessary. Listings are leads, not supplier commitments. Confirm part number, board revision, dimensions, stock, price and delivery before payment.

## Stage A: tools and exact board selection

| Item | Quantity | Before buying |
| --- | --- | --- |
| Computer and suitable USB data cable | 1 each | The Feather 4062 uses Micro-USB for development; check the actual board received |
| Digital multimeter | 1 | Needed for continuity, polarity and voltage checks |
| Breadboard and jumper leads | 1 set | Temporary bench connections; headers may still need soldering |
| Fine insulated stranded wire, heat-shrink, strain relief and removable connectors | Small sample set | Select wire routing and connector pin counts before the full harness |
| Measuring tape, paper joint template and sewing supplies | 1 set | Establish sensor-zone positions and glove fit |
| Soldering equipment | Technician access initially | Buying a personal soldering station is optional |

## Stage B: first bench and fitted sample

| Candidate part | Initial quantity | Purpose / purchase gate |
| --- | --- | --- |
| [Adafruit Feather nRF52840 Express, 4062](https://www.adafruit.com/product/4062) | 1 | Development controller. Confirm upload/recovery tooling and headers. Direct page showed out of stock on 7 November; confirm distributor stock |
| [Nordic nRF52840 Dongle, PCA10059](https://www.nordicsemi.com/Products/Development-hardware/nRF52840-Dongle) | 1 | Custom receiver; matching firmware must be written. It has no onboard debugger, so plan programming/recovery access |
| [Adafruit BNO085 breakout, 4754](https://www.adafruit.com/product/4754) | 1 | Hand orientation sample; proposed SPI wiring is still to be specified |
| [CD74HC4067 module at Nerdshed](https://nerdshed.com.ng/product/16-channel-multiplexer-module-cd74hc4067/) | 1 | Sensor-channel selector; listing showed ₦1,500 on 7 November, subject to confirmation |
| [Microchip MCP6002](https://www.microchip.com/en-us/product/MCP6002) or a reviewed equivalent | 1 | Proposed analog buffer. Package, circuit and settling must be checked before purchase |
| Divider resistors, decoupling capacitors and prototype board | Small assortment | Values and quantities follow measured sample sensors and the schematic |
| [Taiwan Alpha MB090-A03 dual-zone samples](https://www.taiwanalpha.com/en/products/141) | Up to 2 samples | RFQ first; verify exact variant, active-zone spacing and fit |
| [Flexpoint short single-zone samples](https://flexpoint.com/bend-sensor/) | Up to 3 samples | RFQ first; request dimensions suitable for distal-joint and thumb trials |
| Donor stretch glove or index/thumb fabric sleeves | 1 fitted sample | Confirm comfort and sensor channels before making the final textile |
| Conductive fabric or suitable contact patches | Enough for 3 tips | Thumb common, index click and middle click; keep signal wiring insulated |

The initial sample counts are deliberately small. They are not a claim that these standard sensors fit the intended joints. A cheaper locally stocked sensor can help learn the reader circuit, but its measurements do not prove the final joint layout.

Use USB power first. Add a battery once the circuit works on the bench.

## Stage C: after the index/thumb wireless sample passes

| Item | Proposed full-build requirement |
| --- | --- |
| Baseline sensing layout | 16 channels: 12 ordinary-finger flexion, 2 thumb flexion and 2 thumb-base channels |
| Candidate physical sensor count | Five dual-zone strips plus six short sensors, subject to sample results; subtract only samples confirmed suitable for reuse |
| Optional finger spread | Four more channels, deferred; revise selector/reader design before ordering |
| Protected single-cell LiPo | One suitable 3.7 V cell; 500 mAh is an initial sizing candidate, not a runtime promise |
| Charging/power system | Use the development board's supported charging path initially; one designed USB-C charging/power circuit for the final pod |
| Haptic motor | One coin motor plus a correctly rated driver, protection and decoupling |
| Final harness and glove | Fine wiring, locking connectors, controlled sensor channels and detachable electronics |
| Wrist and hand covers | Printed shells, padded cuff and secure IMU mounting |
| Final compact PCB assembly | Controller/power/reader PCB and small hand sensor PCB, after the circuit is stable |

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

For each quote, record currency, dated unit price, quantity, shipping, import charges where applicable, labour and actual landed cost in [BUILD-LOG.md](BUILD-LOG.md). Avoid converting an incomplete foreign-currency subtotal into a finished-build price.

Manufacturer and supplier links are references. Recheck availability when ordering.
