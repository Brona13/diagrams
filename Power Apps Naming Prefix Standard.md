# Power Apps Naming Prefix Standard (Modern-first)

This standard is **type-first** (prefix reflects what the control *is*), then the remainder of the name reflects the *purpose*.

Example pattern:

- `<prefix><Purpose><OptionalContext>`
- Examples: `btnSave`, `cmbAssignee`, `frmEditRequest`, `galRequests`, `tblOrders`

---

## App structure

| Control type | Prefix |
|---|---|
| Screen | `scr` |
| Component | `cmp` |

---

## Layout & grouping

| Control type | Prefix |
|---|---|
| Container (any) | `cnt` |
| Horizontal container | `cntH` |
| Vertical container | `cntV` |
| Group | `grp` |

---

## Data & forms

| Control type | Prefix |
|---|---|
| Form (Edit/Display) | `frm` |
| Data card | `crd` |
| Data card value control (inside card) | `dcv` |
| Gallery | `gal` |
| Table / Data table (table-like list UI) | `tbl` |
| List view / Details list (if used) | `lst` |

> Note: Use `tbl` for any “table-like” list experience, even if implemented as a gallery laid out like a table.

---

## Inputs (user entry)

| Control type | Prefix |
|---|---|
| Text input (single line) | `txt` |
| Text area / multi-line input | `txa` |
| Number input | `num` |
| Password input | `pwd` |
| Button | `btn` |
| Icon | `ico` |
| Link | `lnk` |
| Dropdown | `drp` |
| Combo box | `cmb` |
| Radio | `rad` |
| Checkbox | `chk` |
| Toggle | `tgl` |
| Slider | `sld` |
| Date picker | `dte` |
| Time picker | `tme` |
| Rating | `rte` |
| File / Attachment input | `att` |
| Pen input | `pen` |

### People Picker guidance
Prefer **ComboBox-based naming** instead of a special prefix:

- Prefer: `cmbAssignee`, `cmbRequester`, `cmbApprover`
- Avoid (unless strictly enforced): `ppkRequester`

If you do keep `ppk`, enforce: **`ppk*` is always a ComboBox** (or always a component), so it stays unambiguous.

---

## Display / text / visuals

| Control type | Prefix |
|---|---|
| Label | `lbl` |
| Helper / tooltip label | `hlp` |
| Badge / tag / pill | `bdg` |
| Separator / divider | `sep` |
| Shape / rectangle | `shp` |
| Image | `img` |
| Avatar / persona | `ava` |

---

## Feedback / state / progress

| Control type | Prefix |
|---|---|
| Spinner / loading indicator | `spn` |
| Progress bar | `prg` |
| Message bar / alert | `alt` |
| Notification area (custom container) | `ntf` |

---

## Navigation / structure controls

| Control type | Prefix |
|---|---|
| Tabs / tab list | `tab` |
| Navigation menu (custom container) | `nav` |
| Breadcrumb | `brd` |

---

## Media & device (often where classic may be required)

| Control type | Prefix |
|---|---|
| Camera | `cam` |
| Microphone | `mic` |
| Video | `vid` |
| Audio | `aud` |
| Barcode scanner | `bcs` |

---

## Timers & utility

| Control type | Prefix |
|---|---|
| Timer | `tmr` |

---

## Rules (keep it consistent)

1. **Prefix + Purpose**: `cmbAssignee`, `btnSubmit`, `frmEditRequest`
2. **Avoid role-only prefixes** (like `ppk`) unless you strictly enforce what control type it represents
3. **Use `tbl` for table-like lists** regardless of whether the UI is a modern Table, a gallery, or a classic data table fallback
