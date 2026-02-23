# Altium Test Files

Test repository containing Altium Designer project files for Circuitly integration testing.

## Projects

### STM32_PCB_Design/

STM32-based PCB design project.

**Files:**
- `STM32_PCB_Design.PrjPcb` - Project file
- `Sheet1.SchDoc` - Schematic document
- `PCB1.PcbDoc` - PCB layout
- `Mount_components.BomDoc` - Bill of materials

**Source:** [akhilaprabodha/Altium-STM32-PCB](https://github.com/akhilaprabodha/Altium-STM32-PCB) (Altium Designer 24.x)

**Notes:** The original repository names the SchDoc and PcbDoc files `STM32_PCB_Design.SchDoc` and `STM32_PCB_Design.PcbDoc`, but the PrjPcb internally references them as `Sheet1.SchDoc` and `PCB1.PcbDoc`. We use the PrjPcb-referenced names here so the project file correctly resolves its documents.

### digispark/

Digispark ATTiny85 USB development board clone.

**Files:**
- `ATTiny85.PrjPcb` - Project file
- `ATTiny85.SchDoc` - Schematic document
- `ATTiny85.PcbDoc` - PCB layout
- `ATTiny85.BomDoc` - Bill of materials
- `History.SchDoc` - Revision history document

**Source:** [yasir-shahzad/Digispark-ATTINY85](https://github.com/yasir-shahzad/Digispark-ATTINY85) (Altium Designer 24.x, GPL v3)

**Notes:** The PrjPcb also references `ATTiny85.IntLib` (integrated library) and `ATTiny85.OutJob` (output job), but these files are not present in the original source repository. IntLib files are compiled artifacts generated from source libraries.

## Key Observations

- Altium .SchDoc files embed complete symbol graphics (arcs, lines, rectangles, etc.) inline for each component. No external .SchLib files are needed to render existing schematics.
- Altium .PcbDoc files similarly embed complete footprint data (pads, tracks, regions) for all placed components.
- The `LIBREFERENCE` and `SOURCELIBRARYNAME` properties on components are provenance metadata linking back to the original library, not rendering dependencies.
