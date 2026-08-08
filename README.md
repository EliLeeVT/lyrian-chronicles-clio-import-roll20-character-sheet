# Lyrian Chronicles Roll20 Sheet — Clio Import Fork

Fork of [Morrocker/LyrianChroniclesRoll20](https://github.com/Morrocker/LyrianChroniclesRoll20) with **JSON import** for Angel's Sword Clio tools:

| Tool | URL | Sheet side |
|------|-----|------------|
| Monster Autostat / Strategy Room | https://clio.angelssword.com/strategy-room/index.html | **NPC** |
| Character Builder | Clio character builder (`angelssword-character` export) | **PC** |

---

## Features

### NPC — Monster Autostat JSON
- Import panel at the **bottom** of the NPC sheet
- Maps name, rank, type, danger, size, main/sub stats, HP/RP, defenses, potency, initiative, speed
- Imports abilities → `repeating_npcabilities`
- Imports actions → `repeating_npcactions`
- **Always adds** universal attacks:
  - **Light Attack (1 AP)** — `1d20 + Focus` vs Evasion · `[2d4 + Power]` physical
  - **Heavy Attack (2 AP)** — `1d20 + Focus` vs Evasion · `[4d6 + Power × 2]` physical
  - **Precise Attack (2 AP)** — `1d20 + Focus × 2` vs Evasion · `[2d4 + Power]` physical · Pinpoint = Focus

### PC — Clio Character Builder JSON
- Import panel at the **bottom** of the Player sheet
- Accepts `"format": "angelssword-character"`
- Fills name, race/subrace, gender, spirit core, main/sub stats, HP/MP/RP, skill points
- Classes → `repeating_classes` (matches known class IDs when possible)
- Breakthroughs → `repeating_breakthroughs`
- Race/ancestry traits → Key Abilities
- Inventory → weapons / armors / misc (names & quantities)
- On-sheet checklist for fields the export does **not** fully cover (languages, burden, class ability text, etc.)

### UX polish
- Import panels sit at the **bottom** of each sheet (not in the header)
- Dark-mode-friendly import styling (avoids official `filter: invert()` on those panels)
- Extra dark-mode contrast rules for selects and value fields where CSS allows

---

## Install in Roll20 (Custom sheet)

Roll20 needs **both** HTML and CSS in separate tabs.

1. Campaign → **Settings** → **Game Settings**
2. Character Sheet Template → **Custom**
3. Paste:
   - **HTML** ← `LyrianChronicles.html`
   - **CSS** ← `LyrianChronicles.css`
4. Save → open a character (do **not** rely on the editor Preview tab alone)
5. **PC import:** scroll to bottom of the player sheet  
   **NPC import:** toggle **NPC Sheet**, scroll to bottom

Switching to this custom sheet does **not** wipe existing character data when attribute names match the official sheet.

---

## Sample files

| File | Use |
|------|-----|
| `sample-void-stalker.json` | NPC Autostat-style test monster |
| `sample-jammy-halek.json` | PC `angelssword-character` export (portrait stripped) |

---

## Repo layout

```
LyrianChronicles.html   # Layout + sheet workers (import logic)
LyrianChronicles.css    # Styles
sheet.json              # Sheet metadata
template.json           # Roll templates
macro.txt               # Optional macros
Assets/ Assets2/        # Local art references (live CSS uses hosted URLs)
sample-*.json           # Example imports
```

---

## Credit

- Original Roll20 sheet: **Morrocker**
- Clio / Strategy Room / Character Builder: **Angel's Sword** ([clio.angelssword.com](https://clio.angelssword.com))
- This fork: PC + NPC JSON import, universal NPC attacks, import UX

## License / upstream

MIT License for Roll20.
Follow whatever terms apply to the original [Morrocker/LyrianChroniclesRoll20](https://github.com/Morrocker/LyrianChroniclesRoll20) sheet and Angel's Sword materials. 
This fork is for personal/campaign use unless upstream allows broader redistribution.
