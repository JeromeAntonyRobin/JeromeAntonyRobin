# The Silis Chronicle: Genesis, Architecture, and Academic Groundwork

A comprehensive engineering history, commit archaeology, and academic milestone archive of **Silis**—from a homebrew Tkinter version control script to a standalone, zero-dependency RTL-to-GDSII silicon design cockpit.

---

## ⬡ Executive Timeline & Milestone Matrix

| Date / Period | Git Milestone & Hash | Raw Technical Reality | Academic & Community Traction |
| :--- | :--- | :--- | :--- |
| **Jan 11, 2026** | `3803695e` | **Initial Commit**: Repository initialized with GNU license. | The beginning of an open-hardware initiative. |
| **Jan 13–15, 2026** | `ef85450f`<br>`b10ce7ab` | **The Era of `DevCtrl` & `pocv1.py` → `pocv17.py`**: Invented a custom Tkinter version control system (`v1.py`) with built-in code editor, numpad remapping, custom superkeys, and a `promote` button to avoid Git complexities. Every iteration was a full-file clone. | **Easwari Engineering College** begins showing early interest during Month 1—despite Silis having zero place-and-route or backend flow at the time. |
| **Jan 18, 2026** | `3ff2327f` | **The PyQt6 Pivot**: `Transitioning from tkinter to PyQT`. Tkinter canvas limitations hit a wall; entire GUI re-architected on native Qt6 widgets. | Architecture shifts toward handling heavy graphical workloads (schematics, layouts). |
| **Jan 19–24, 2026** | `1998e874`<br>`45bd0362`<br>`af8769c1` | **Breaching Backend Territory**: `We are in PnR territory boiss!!` → `We doing PnR now broskies!` → `deeeep into PnR`. Birth of `pocpnrv*.py` series. Invented the **PDK Triangulation Engine** (matching `.lib`, `.lef`, `.tlef`) and **SiliconPeeker** (inverted Y-axis layout view with density heatmaps). | Word begins spreading among student VLSI networks in Chennai regarding an autonomous student-built ASIC GUI flow. |
| **Feb 6, 2026** | `ccfb18d5`<br>`4915c24e` | **Rapid Prototyping & Binary Bundling**: Fast iterations stabilizing `pocpnrv25.py` (3,100+ lines in a single file). | **CIT Chennai Showcase**: Showcased at the CIT VLSI Department event. Deep discussion with a veteran faculty member with Cadence experience; related how Cadence bifurcates Genus, Innovus, and Tempus, proposing Silis as a unified cockpit. CIT requests contributor access. |
| **Feb 8, 2026** | `2be58076` | **The RMKCET Convergence**: Showcased alongside co-developer **Eatheswar N** (studying at RMKCET). | **RMKCET Showcase**: Acting HOD of the VLSI Department extends an official invitation for a **week-long ASIC workshop in January 2027**. Connected with fellow student VLSI enthusiasts who became early alpha testers and bug hunters. |
| **Feb 9–10, 2026** | `817445c2`<br>`ea657cf5` | **`upto gds2 gen!!!!!!`** → `closer.`: Completed end-to-end flow integration via `gdstk` and `SSAForge` to output real physical GDSII stream files straight from the GUI cockpit. | Proved that the open-source toolchain could be unified and driven autonomously without manual Tcl scripting. |
| **Feb 11–27, 2026** | `ec5a7451`<br>`9bfdccbb` | **Installers, Icons, and 3D GDS**: `pocpnrv25 installer no openroad`, window icons, `Banger Terminal and GDS3D`. Contributor access intentionally kept closed to maintain single-author iteration speed. | Contributor requests politely deferred; the architecture was moving too fast for external PRs. |
| **Apr 14, 2026** | `e75d8799`<br>`6e5e2636`<br>`d4199bb1` | **The 20-Commit Pre-Workshop Blitz**: Pushed 15+ commits in 24 hours. Implemented `devcontainer.json`, headless X11 streaming, and lightweight Docker containers (`Lighten Dockerfile`) for GitHub Codespaces. | Engineering a foolproof zero-setup web environment so workshop attendees wouldn't hit local Linux build failures. |
| **Apr 15, 2026** | *N/A (IRL)* | **Workshop: "Basic ASIC Design Using Open Source Tools"**: Invited as official **Resource Person** by the Dept. of ECE, **Easwari Engineering College** (`siliswsinv.jpeg`). | Conducted hands-on instruction teaching peers how to design ASICs from RTL to layout using open-source tools. |
| **Jul 24, 2026** | `ac3d23bd` | **The Legendary Git Epiphany**: `i realised how git actually works`. Nuked 50 duplicate versions (`pocv1` through `pocpnrv30b3`, which had grown to 5,797 lines). **-69,675 lines deleted** in one commit. Renamed monolith to `silis.py`. | Transition from experimental hacker mode to professional software version control. |
| **Jul 26, 2026** | `902a9e82` | **The Ultimate Refactor**: `Ultimate Refactor!! 5000+ lines go poof`. Monolith split into clean subsystems: `core/`, `synthengine`, `pdk`, `layout`. | Foundation laid for modular C++ extensions and team-based engineering. |
| **Jul 30 – Aug 11, 2026** | `c3bf49c8`<br>`8ff2d8e1`<br>`80354b0a` | **Native C++ Performance Pivot**: Implemented `FastLayout`, `FastSchem`, and C-ports of routing engines bound via pybind11 to bypass Python GIL limitations. | Realized high-frequency 60 FPS viewport rendering on multi-million gate layouts. |
| **Nov 8–15, 2026** | `1397f032`<br>`28a16261`<br>`55721da7`<br>`d6c704ee` | **v0.1.1-pre Standalone AppImage**: Fully self-contained binary packaging bundling Python 3.12, PyQt6, Yosys, OpenROAD, OpenSTA, Magic, and SkyWater 130A/B PDK with OpenRAM macros. Strict host isolation (`PYTHONNOUSERSITE`). | Handed to the peer testing network (met at CIT & RMKCET) for real-world tapeout stress testing and bug hunting. |
| **Coming Jan 2027** | *Scheduled* | **Week-Long ASIC Tapeout Workshop at RMKCET**: Jerome Antony Robin & Eatheswar N returning to conduct a comprehensive hands-on silicon design workshop using production Silis. | Direct institutional adoption and peer-led semiconductor education in South India. |

---

## ⬡ Detailed Phase Breakdown

### Phase 1: Homebrew Version Control & The Tkinter Genesis (Jan 11 – Jan 18, 2026)
Before adopting standard Git branches, development was governed by an in-house tool named **`DevCtrl`** (`v1.py`). Because managing Git branches was cumbersome, `DevCtrl` served as a custom IDE wrapper:
- Provided an embedded text editor with line numbering and syntax tagging.
- Automated numpad keycode translation (`bridge_numpad`) for hardware developer keyboards.
- Embedded a two-phase "superkey" trigger system (similar to Vim leader keys) allowing instant focus switching between project trees, editors, terminals, and scratchpads.
- Managed sequential script copies (`pocv1.py` through `pocv17.py`) inside `dev_JeromeAntonyRobin/`.

Even in this nascent phase, when the tool was purely a frontend code editor and basic image-based schematic zoomer (`ZoomableSchematic`), faculty at **Easwari Engineering College** noted the project and began tracking its trajectory.

### Phase 2: The Physical Design Breakthrough (Jan 19 – Jan 24, 2026)
Recognizing that Tkinter could not support hardware-accelerated layouts, the entire UI was rewritten in **PyQt6** (`3ff2327f`). With this shift came the `pocpnrv*.py` series:
- **PDK Triangulation**: The EDA industry often suffers from disorganized PDK folders. Silis introduced automatic directory scanning that verified the simultaneous presence of timing libraries (`.lib`), physical macros (`.lef`), and technology rules (`.tlef`) before declaring a PDK valid.
- **SiliconPeeker**: Created an inverted Cartesian coordinate canvas (`scale(1, -1)`) that accurately mapped semiconductor silicon geometry, complete with auto-fitting die boundaries and density grids.

### Phase 3: The Academic Circuit & The First GDSII (Feb 6 – Feb 27, 2026)
By February, `pocpnrv25.py` had grown to over 3,100 lines, integrating `gdstk` and `SSAForge` (Static Timing & Synthesis Alias Forge):
- **CIT Chennai (Feb 6)**: During their VLSI department event, Silis was showcased to academic faculty. A discussion with an ex-Cadence engineer highlighted the friction of commercial workflows (where engineers must context-switch between Genus for synthesis, Innovus for PnR, and Tempus for signoff). The concept of a single, unified open-source cockpit resonated immediately, prompting faculty to offer student contributors.
- **RMKCET (Feb 8)**: Showcased alongside co-developer Eatheswar N. The acting HOD of VLSI recognized the educational and practical value of the platform, extending an official invitation for a **full-week workshop in January 2027**. A core circle of student VLSI enthusiasts was assembled to serve as dedicated alpha testers.
- **GDSII Milestone (Feb 9)**: Commit `817445c2` (`upto gds2 gen!!!!!!`) marked the first time the automated pipeline successfully ingested Verilog and emitted a verified GDSII stream file.

### Phase 4: Instructional Deployment at Easwari (Apr 14 – Apr 15, 2026)
Invited to lead an official workshop at Easwari Engineering College on **"Basic ASIC Design Using Open Source Tools"** (April 15, 2026; `siliswsinv.jpeg`), a major technical challenge arose: ensuring dozens of student laptops could run heavy EDA tools without getting bogged down in missing shared libraries or compilation errors.
- On April 14, in a 24-hour sprint of 15+ commits, a fully containerized cloud environment was engineered using Docker and GitHub Codespaces.
- Stripped heavy compile stages into runtime scripts (`Lighten Dockerfile`), configured virtual X11 displays, and enabled students to run full synthesis-to-layout flows in a browser tab.

### Phase 5: The "Git Realization" & Architecture Restructuring (Jul 24 – Aug 11, 2026)
On July 24, 2026, the famous commit `ac3d23bd` (`i realised how git actually works`) was pushed:
- **-69,675 lines of code** were purged in a single commit, eliminating 50 individual POC files, `todo.txt`, and `complaints.txt`.
- The top-level script was stabilized as `silis.py`.
- Two days later (`902a9e82`), the monolithic 5,000-line script was dismantled into modular subsystems (`core/`, `synthengine/`, `pdk/`, `layout/`).
- Recognizing Python's performance ceiling when rendering complex multi-layer DEFs, key routing and layout engines were ported to C++ and bound via `pybind11`, delivering sustained 60 FPS viewport rendering.

### Phase 6: Standalone AppImage & Future Horizons (Nov 2026 – Jan 2027)
In November 2026, Silis reached production-grade distribution (`v0.1.1-pre`):
- Packaged as a standalone Linux x86_64 AppImage bundling Python 3.12, PyQt6, Yosys, OpenROAD, OpenSTA, Magic VLSI, and the SkyWater 130nm PDK (A and B variants with OpenRAM macros).
- Engineered with strict host environment isolation (`PYTHONNOUSERSITE`, embedded shared libraries) to guarantee zero-setup, deterministic execution on any Linux distribution.
- Distributed to the trusted RMKCET/CIT testing group in preparation for the **January 2027 Week-Long ASIC Tapeout Workshop**.
