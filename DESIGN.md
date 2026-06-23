# Venio CRM — Design System Reference

Gofive Design System สำหรับ Venio CRM project ทุกไฟล์

---

## Font — Gofive (local woff2)

| Weight | File | ใช้กับ |
|--------|------|--------|
| 400 | `fonts/Gofive-Text.woff2` | body text |
| 500 | `fonts/Gofive-Medium.woff2` | medium labels |
| 600 | `fonts/Gofive-Semi_Bold.woff2` | descriptions, subheaders |
| 700 | `fonts/Gofive-Bold.woff2` | headings |

**ห้ามใช้ Google Fonts หรือ font อื่น** — ทุก element ใช้ `"Gofive"` เท่านั้น

### Typography Scale

| Token | Size | Weight | ใช้กับ |
|-------|------|--------|--------|
| `--fs-300` | 14px | 600 | eyebrow, label (ไม่ uppercase ไม่ letter-spacing) |
| `--fs-400` | 16px | 600 | description, subheader, body text |
| Header | clamp() | 700 | headings, ปรับขนาดตาม context |

---

## Color Tokens

### Natural (Gofive DS)

```css
--bg:           #FFFFFF   /* White (1) — page background */
--bg-alt:       #F6F6F8   /* Soft Cloud (2) — section bg */
--bg-dark:      #1C1C22   /* Charcoal (12) — dark CTA sections, footer */
--ink:          #1C1C22   /* primary text */
--ink-soft:     #525260   /* Lead (10) — muted descriptions */
--ink-faint:    #838395   /* Porpoise (8) — smallest labels, icons */
--on-dark-soft: #A5A5B6   /* Pewter (7) — text on dark bg */
--line:         #ECECF1   /* Cloud (3) — dividers, light borders */
--line-mid:     #DFDFE8   /* secondary borders */
--line-strong:  #D2D2DA   /* Silver (5) — field borders */
```

### Accent (Venio Brand)

```css
--brand:        #116DFC   /* Bluetiful — primary CTA, active states */
--brand-dark:   #035CE6   /* Cobalt — hover state */
--brand-ink:    #035CE6   /* Cobalt — brand text on light bg */
--brand-wash:   #E7F0FF   /* Zircon — subtle tint bg */
--brand-ghost:  #F5F9FF   /* Ghost White — lightest tint */
```

### Status

```css
--success:      #21CE9B
--error:        #DE3A45
--notification: #F02848
```

### Brand Gradient (text)

```css
background: linear-gradient(90deg, #0BB8F2, #116DFC);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
```
ใช้กับ `.accent` class — headline สำคัญ, ✦ symbol

---

## Page Background

```css
background: linear-gradient(160deg, #F2F8FF 0%, #fff 50%);
```
ใช้กับทุกหน้า — ห้ามเข้มกว่า `#F2F8FF` เป็น gradient start

---

## Radius System

```css
--r-card: 14px    /* cards ทั่วไป */
--r-sm:   8px     /* small elements, badges, focus rings */
--r-btn:  10px    /* buttons */
--r-pill: 999px   /* lang toggle, tab chips เท่านั้น */
```

**ห้ามใช้ `border-radius: 999px` กับ button** — ใช้ `--r-btn: 10px`

---

## Buttons

```css
/* Base */
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  height: 44px; padding: 0 16px;
  border: none; border-radius: var(--r-btn); /* 10px */
  font-family: var(--font); font-size: 16px; font-weight: 600;
  cursor: pointer; transition: background .2s ease;
}

/* Sizes */
.btn--md  { height: 40px; }
.btn--sm  { height: 36px; padding: 0 14px; font-size: 14px; }
.btn--xs  { height: 32px; padding: 0 12px; font-size: 14px; }
.btn--block { width: 100%; min-height: 44px; }
```

### Variants

| Variant | Background | Text | Border |
|---------|-----------|------|--------|
| Primary | `var(--brand)` | `#fff` | none |
| Primary hover | `var(--brand-dark)` | — | — |
| Secondary | transparent | `var(--ink-soft)` | `1px solid #DFDFE8` |
| Secondary hover | `var(--bg-alt)` | คงเดิม | คงเดิม |

**ห้ามสร้าง custom button class** — ใช้ `.btn`, `.btn--block`, `.btn--primary` เสมอ

### Icon ใน Button

ห้ามใส่ box/frame รอบ icon — ไม่มี `background`, ไม่มี `border-radius` บน icon container
Arrow icon แสดงเปล่าๆ ไม่มีกล่อง

---

## Form Fields

```css
.field {
  display: flex; align-items: center; gap: 8px;
  height: 48px; /* fixed — ห้ามใช้ padding แทน */
  border: 1px solid var(--line-strong); /* 1px เท่านั้น ห้าม 1.5px */
  border-radius: var(--r-field); /* 12px */
  padding: 0 14px;
  background: #fff;
}
.field:focus-within {
  border-color: var(--brand);
  box-shadow: 0 0 0 3px rgba(17,109,252,.08);
}
```

### Field Layout Rules

- **Equal columns:** `grid-template-columns: 1fr 1fr` + `min-width: 0` บน `.field`
- **Half-width field:** ใช้ grid 1fr 1fr + `<div></div>` เป็น empty cell
- **อย่าเปลี่ยน field pairing** เพื่อแก้ปัญหา visual — แก้ CSS เท่านั้น
- **Picker:** option > 4 ตัว → `<select>` dropdown ไม่ใช้ chip/card picker

---

## Phone Country Dropdown (DS-spec)

```css
/* Trigger */
.phone-prefix {
  display: flex; align-items: center; gap: 5px;
  padding-right: 10px;
  border-right: 1px solid var(--line); /* 1px */
  cursor: pointer; position: relative;
}

/* Dropdown card */
.phone-dropdown {
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 0 12px rgba(0,0,0,.12);
  padding: 8px;
}

/* Option */
.phone-dropdown-option:hover,
.phone-dropdown-option.selected {
  background: var(--brand); color: #fff;
}
```

---

## Tab / Chip Selector

```css
.type-tab {
  padding: 6px 14px;
  border-radius: 999px; /* pill */
  border: 1px solid var(--line-mid);
  font-size: 13px; font-weight: 600;
}
.type-tab.active {
  background: var(--brand-ghost);
  border-color: var(--brand);
  color: var(--brand);
}
```

---

## Logo (asset/logo/)

| File | ใช้เมื่อ |
|------|---------|
| `Logo-1.svg` | V mark อย่างเดียว, gradient (light bg) |
| `Logo-2.svg` | Full wordmark, all white (dark bg) |
| `Logo-3.svg` | Full wordmark, V gradient + white text (dark bg) |

**Light background header/footer:** inline SVG จาก Logo-3 — ทุก path ใช้ `fill="url(#hdr-grad)"` เหมือนกันหมด (V + enio) → wordmark gradient ฟ้าทั้งคำ

```css
.brand-logo { height: 28px; width: auto; }
```
ไม่มี `<span class="brand-name">` แยก

---

## Icon Style

- ใช้ Lucide / Heroicons stroke style
- `stroke-width: 1.5px`, `fill: none`
- สี: `currentColor` หรือ `var(--ink-faint)` สำหรับ UI icons
- ห้ามใช้ emoji เป็น icon (ยกเว้น flag emoji ใน phone dropdown)
