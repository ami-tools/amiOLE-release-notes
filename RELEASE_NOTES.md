# ami.OLE — Release Notes

---

## Version 1.2.0 · 9 November 2026

ami.OLE 1.2 is a major update. It adds a full Settings window with design standards, a Content Manager, an Alignments window, a Compliance Report, an editable dropper library and a rebuilt Overlap tool. It also adds support for Revit 2027.

### What's New

**Revit 2027 support**
ami.OLE now installs and runs on Revit 2022, 2023, 2024, 2025, 2026 and 2027.

**Settings window and design standards**
- The **Settings** button on the General panel opens the new ami.OLE Settings window. Its tabs are Project, Environment, Catenary System, Droppers, Structures, Cantilevers & Brackets, Overlaps, Clearances & Compliance, Documentation, Import / Export, and Company & Support. Where it helps, you enter values straight on the same diagrams the Add Placeholder, Add Structures and Add Cantilever windows use.
- Pick a **design standard** at the top and every tab fills in. Built-in standards: **Generic** (the ami.OLE defaults, not tied to any railway authority), **PTA (WA)**, **TfNSW – Sydney Trains 1500 V DC**, **Queensland Rail – 25 kV AC**, **Metro Trains Melbourne** (unverified), **Network Rail – UK Master Series** and **Network Rail – UK Series 1**. Each standard's notes give the source of its values. Your company can add its own standards as files in a shared folder, and **Export standard...** saves the current values as a new one.
- Settings are **saved inside the Revit model** when you press OK or Apply, so everyone on the project uses the same values. Only values you change from the standard are stored, and **Reset tab to standard** removes them for one tab.
- Almost every setting is used by the commands: Add Placeholders, Add Structures, Add Cantilever, brackets, wires, documentation, compliance and imports all pick up the project's values. With an unchanged standard they behave as before.
- New projects start with your last chosen standard, or Generic. A model built with an earlier ami.OLE opens with PTA (WA), the values ami.OLE used before.

**Environment and project information**
- **Settings > Environment** holds the site conditions: ambient, conductor and reference temperatures, wind, importance level or consequence class, design life and corrosivity. Each standard fills them in for its capital city, and you can change them for your site. They are written to Project Information as "OLE …" parameters for title blocks and schedules.
- The Environment tab follows a design code (**AS/NZS**, **Eurocode (UK NA)** or **Eurocode**), so ami.OLE can be used outside Australia. Wind regions follow AS/NZS 1170.2:2021.
- The **Project** tab keeps project number, name, client and design stage in step with Revit's Project Information.

**Phase colours**
- Phase colours on the Project tab are applied through the **EXISTING**, **NEW**, **DEMOLISHED**, **MODIFIED** and **FUTURE** view filters in every view that uses them. ami.OLE creates missing filters when you press OK or Apply.
- New **Phase Modified** and **Phase Future** tick parameters mark existing elements that are altered, and future work modelled in the current phase. In PTA, Modified is green and Future is magenta.
- **Tags take the phase colour** of the mast, bracket or placeholder they tag. This happens on OK / Apply in Settings and when Cross Section, Multi Cross Section, Annotate Layout or Span / Versine places tags.

**Alignments window**
- **Manage Alignments** on the Alignment panel opens the Alignments window: track and chainage settings (gauge, high rail level datum, chainage format, chainage marker intervals) with every alignment in the model listed below.
- From the list you can import, rename, reimport, update placeholders, add or show / hide chainage markers, show an alignment in the view, or delete it. Import asks for the line and track, pre-filled from the file name.
- **Renaming a line** also renames every placeholder, structure, bracket and wire on it.
- After an alignment is reimported or edited, the window shows how many placeholders are now off it and **Update placeholders** moves them back with their structures.
- **High rail level datum** chooses whether the High Rail Level is measured from the Project Base Point, Survey Point or Internal Origin.
- Chainage markers follow the chainage format (Ch.14+300 or Ch.14300), including markers already in the model when you change it.
- The Import Alignment and Chainage Marker buttons have moved from the ribbon into this window.

**Droppers**
- Dropper data now lives in **Settings > Droppers** (the Load Dropper Data button has gone from the Wires panel). Load or reload the dropper lookup workbook there.
- Step through the spans to see each one drawn with its droppers, lengths and spacings, next to the dropper table. Hover a dropper for details.
- **Edit the tables:** double-click a cell to change a span, number of droppers, A, a dropper length or a spacing; add or delete spans. Changes are saved in the model on Apply or OK.
- **Export workbook...** saves the tables, with your edits, as a dropper lookup workbook based on your project's own template.
- Type the **encumbrance** at support A and B directly on the span drawing.
- Droppers and spans that break a rule are shown in red: too short, too many per span, longer than the encumbrance, missing values, duplicate or missing spans, or a dropper that would stop the contact wire hanging level.

**Compliance Report**
- The new **Compliance Report** button on the Reports panel checks the wire runs you pick against the design standard and writes an Excel workbook with Summary, Checks, Spans, Supports and Droppers sheets.
- It checks span length, adjacent span ratio, contact wire height, gradient and change of gradient, stagger on straight and curved track, track versine, droppers per span, shortest dropper and mast offset. Values close to a limit (5% by default) are warnings.
- Only limits set in your design standard are checked; the rest show as "Not checked".
- The **Elite Compliance** export (licensed feature) remains available for PTA (WA) projects.

**Lookup window**
Span, versine, stagger and contact wire height cells outside the design standard's limits are shown in red, including spans much longer or shorter than the span before them. Hover a red cell to see why.

**Content Manager**
- The **Content Manager** button opens a window to browse your standard's families (Generic, PTA, UK Master Series...) and add them to the project. Add a standard by choosing the Revit file AMI supplies; it stays in the list.
- Families are grouped by category with Revit previews, catalog numbers (e.g. **076-618**) and descriptions. Search by name, description, type, catalog, allocation or drawing number.
- **Load into project** adds a type; **Place** (or double-click) lets you place it. **Load all of <standard>** loads every family of the standard in one step, with a progress panel and Stop button.

**Structures defaults**
- **Settings > Structures** shows the Add Structures screens for Single Mast, Portal Assembly, Drop Tube and Two Track Cantilever. Values you type there become the defaults in Add Structures, including **Default Structure Type**, **Default Footing Type** and **Include Footing**.
- Realistic input limits: mast heights 1000–15000 mm, boom lengths 2000–30000 mm, mast offsets up to 5000 mm, drop tube heights 300–4000 mm.
- **Min mast offset to track** has a default per standard; Add Structures won't accept a smaller offset and the Compliance Report flags masts closer than this.

**Cantilevers & Brackets defaults**
- **Default brackets by structure size:** Add Cantilever selects the top and bottom bracket for the chosen structure size.
- **Default cantilever by push / pull:** once Add Cantilever knows the placeholder's push / pull, it shows only matching cantilever types and selects the default. Your own picks are never replaced.

**Pantograph gauge**
- The Clearances & Compliance tab draws the pantograph gauge to scale: static and dynamic pantograph, passing electrical clearance and the catenary wire envelope.
- Pantograph sway is now lateral and vertical. On Apply, head width, passing clearance and sway are written to every placeholder type.

**Overlap tool rebuilt**
- Select the placeholder of **structure 1**, then **structure 2**, in the direction of travel (or press Esc after the first for a single structure). The window shows the overlap plan from **Settings > Overlaps**, with the chainage, contact wire height and structure numbers from your selection. Every value can be changed for this overlap.
- Each structure gets its two overlap placeholders and the selected placeholders move to the new construction phase, in one step.
- **The wire run is split for you:** the run on the higher-chainage side gets the next free wire run number, and every placeholder, cantilever, contact wire, in-span item and anchor beyond the overlap moves to it. The window shows how many before you click OK.
- **Contact wires are reconnected:** existing contact wires before and after the overlap are re-placed onto the overlap placeholders with droppers recalculated, and the overlap span gets two overlap wires of the default overlap type.
- Warnings show when the overlap span is outside the allowed range or the wire runs clash; OK stays greyed until fixed.
- The new **Settings > Overlaps** tab sets the overlap span lengths, contact wire lift, catenary heights, out-of-running stagger, default stagger sides and default overlap type, drawn to match the PTA system design.

### Bug Fixes
- **Portal placeholders** are positioned from the portal family's actual Mast Width.
- **Portal right mast offset** now gets the same default as the left mast.
- **Align Secondary** and **Relocate** put secondary placeholders on the primary's structure line on crossovers and angled tracks, and turn them parallel to the primary.
- **Add Structures** opens portals and Two Track Cantilevers with the default type and footing settings from Settings.
- The **Alignments window** stays in front of Revit after picking a file or answering a question.
- **Overlap** no longer crashes Revit when used a second time in a session, and no longer fails with "The parameter is read-only" when the wires beyond the overlap have droppers.

### Good to know
- Values marked as AMI defaults in the built-in standards (for example the Generic limits and environment conditions) are engineering assumptions. Check them against your project's design basis.
- The first time you press OK or Apply in Settings on an existing model, ami.OLE adds the Phase Modified / Phase Future parameters and the phase view filters. A model whose project base point and survey point are at different elevations may get new High Rail Level values if you choose Project Base Point as the datum.

---

## Version 1.1.1 · 29 June 2026

### Changes

**Production licensing**
ami.OLE now activates against the production licence. Use the licence key issued for ami.OLE.

---

## Version 1.1.0 · 26 June 2026

### Bug Fixes

**Overlap tool — fully fixed on Revit 2025 & 2026**
The Overlap command was crashing Revit 2025 and 2026 on and off across several releases. After extensive investigation, the true root cause was found: an incompatibility between Revit 2025/2026's .NET 8 runtime and how certain internal WPF exceptions are handled during element selection and dialog display. The fix is transparent — the tool works exactly as it always has on all supported Revit versions: click Overlap, click on a placeholder, and the dialog opens.

**Export Droppers no longer shows an error after saving**
Exporting droppers to Excel now completes cleanly. The spreadsheet opens automatically without triggering a false error message.

---

## Version 1.0.702 · 13 June 2026

### What's New

**Release Notes now accessible from the About window**
You can now read the latest release notes directly from ami.OLE. Click **Release Notes** in the About dialog and it will open in your browser.

---

## Version 1.0.696 · 13 June 2026

### Bug Fixes

**Licence key is now fully visible when entering it**
The licence key input field was cutting off part of the key, making it hard to read or verify. The field is now taller and displays your full key clearly.

---

## Version 1.0.695 · 13 June 2026

### What's New

**Change your licence key from the About window**
You can now update your licence key at any time directly from the About dialog. No more manually deleting files — just open About, click *Change Licence Key*, enter your new key, and you're done.

---

## Version 1.0.694 · 12 June 2026

### What's New

**Revit 2026 support**
ami.OLE now supports Revit 2026 alongside Revit 2022, 2023, 2024, and 2025.

**Floating licence keys**
Licence keys are no longer hardcoded per user. On first run, ami.OLE will prompt you to enter your Cryptolens licence key. The key is saved securely and you won't be asked again unless it becomes invalid or is removed.
