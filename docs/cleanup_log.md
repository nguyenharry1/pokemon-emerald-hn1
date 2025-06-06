# Unused Code Cleanup Log
Tracking removal of verified unused symbols using `nm`, `ripgrep`, and `make`.

---

## Branch: `cleanup/unused-symbols`
**Author:** @nguyenharry1  
**Started:** 2025-05-05

---

### 🔹 Removed Symbols

#### Symbol: `gUnusedBattleMainVar`
- **Declared in:** `include/battle.h`
- **Defined in:** `src/battle_main.c`
- **References:** None found via:
  - `nm pokemerald.elf | grep gUnusedBattleMainVar`
  - `rg gUnusedBattleMainVar`
- ✅ Confirmed unused
- 🛠 Removed from both header and source
- ✅ `make` succeeded post-removal

---

#### Symbol: `gUnusedBikeCameraAheadPanback`
- **Declared in:** `include/bike.h`
- **Defined in:** `src/field_camera.c`, `src/bike.c`
- **References:** Only used in conditionals that always evaluate the same way
  - `nm pokeemerald.elf | grep gUnusedBikeCameraAheadPanback`
  - `rg gUnusedBikeCameraAheadPanback`
- ✅ Confirmed static `FALSE` initializer and no mutations
- 🧹 Replaced all logic depending on this variable with constant branches
- 🛠 Removed from both header and source
- ✅ `make` succeeded post-removal

---

### 📌 Notes
- `nm` confirmed symbol was present in ELF before removal.
- `make` was rerun after the edit to ensure ROM integrity.
- Log will be updated per symbol for transparency and version control.
