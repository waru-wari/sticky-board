# Venio CRM — Homepage Project

Single-file HTML project สำหรับ Venio CRM landing page โดย Gofive.

## Files

```
venio-home.html      ← ไฟล์หลัก (production)
venio-home-v2.html   ← draft เก่า ไม่ใช้แล้ว
fonts/               ← Gofive font files (woff2)
asset/logo/          ← Venio logo SVGs
```

## Stack

- Vanilla HTML + CSS (single file, no build step)
- ไม่มี framework, ไม่มี Tailwind
- Dev server: `npx serve -p 4200 .` → เปิด `http://localhost:4200/venio-home.html`

## Design System

### Font — Gofive (local woff2)

| Weight | File | CSS |
|--------|------|-----|
| 400 | `fonts/Gofive-Text.woff2` | regular body |
| 500 | `fonts/Gofive-Medium.woff2` | medium |
| 600 | `fonts/Gofive-Semi_Bold.woff2` | semi-bold descriptions |
| 700 | `fonts/Gofive-Bold.woff2` | bold headers |

ห้ามใช้ Google Fonts หรือ font อื่น ทุก element ใช้ "Gofive" เท่านั้น

### Typography Rules

- **14px** (`--fs-300`, weight 600) — eyebrow, label (ไม่ uppercase ไม่ letter-spacing)
- **16px** (`--fs-400`, weight 600) — description, subheader, body text
- **Header** — weight 700 (Bold), ขนาดปรับตาม context ด้วย `clamp()`

### Color Tokens

**Natural (Gofive DS):**

```css
--bg:           #FFFFFF   /* White (1) */
--bg-alt:       #F6F6F8   /* Soft Cloud (2) — section bg */
--bg-dark:      #1C1C22   /* Charcoal (12) — dark CTA sections */
--ink:          #1C1C22   /* primary text */
--ink-soft:     #525260   /* Lead (10) — muted descriptions */
--ink-faint:    #838395   /* Porpoise (8) — smallest labels */
--on-dark-soft: #A5A5B6   /* Pewter (7) — text on dark bg */
--line:         #ECECF1   /* Cloud (3) — borders */
--line-strong:  #D2D2DA   /* Silver (5) */
```

**Accent (Venio Brand):**

```css
--brand:        #116DFC   /* Bluetiful — primary */
--brand-dark:   #035CE6   /* Cobalt — hover state */
--brand-ink:    #035CE6   /* Cobalt — brand text on light */
--brand-wash:   #E7F0FF   /* Zircon — subtle tint */
--brand-ghost:  #F5F9FF   /* Ghost White — lightest */
```

**Status:**

```css
--success:      #21CE9B
--error:        #DE3A45
--notification: #F02848
```

### Logo (asset/logo/)

| File | ใช้เมื่อ |
|------|---------|
| `Logo-1.svg` | V mark อย่างเดียว, gradient (light bg) |
| `Logo-2.svg` | Full wordmark, all white (dark bg) |
| `Logo-3.svg` | Full wordmark, V gradient + white text (dark bg) |

**สำหรับ light background header/footer:** inline SVG จาก Logo-3 — **ทุก path ใช้ `fill="url(#hdr-grad)"` เหมือนกันหมด** (V + enio) ไม่เปลี่ยน text เป็น `var(--ink)` — ผลลัพธ์คือ wordmark gradient ฟ้าทั้งคำ
- CSS: `.brand-logo { height:28px; width:auto; }`
- ไม่มี `<span class="brand-name">` แยก

### Buttons

```css
--r-btn: 10px   /* round radius — ไม่ใช่ pill */
```

**Sizes (Figma spec):**
| Class | Height | Padding |
|-------|--------|---------|
| `.btn` (base/Large) | 44px | `0 16px` |
| `.btn--md` | 40px | — |
| `.btn--sm` | 36px | `0 14px`, 14px font |
| `.btn--xs` | 32px | `0 12px`, 14px font |
| `.btn--block` | auto, min 44px | full width |

**Variants:**
- Primary: `background: var(--brand)`, white text
- Secondary default: `color: var(--ink-soft)`, `border: var(--line-mid)` (#DFDFE8), transparent bg
- Secondary hover: เพิ่มแค่ `background: var(--bg-alt)` — border/text คงเดิม
- ห้ามใช้ `border-radius: 999px` กับ button

### Radius System

```css
--r-card: 14px   /* cards */
--r-sm:   8px    /* small elements, badges */
--r-btn:  10px   /* buttons */
--r-pill: 999px  /* lang toggle เท่านั้น */
```

## Navigation (ตาม veniocrm.com)

โครงสร้าง desktop nav:

```
[Logo] Features▾  Solutions▾  Pricing  Blog  About▾  Contact Us  |  TH  EN  |  Login  [เริ่มใช้ฟรี 14 วัน]
```

Dropdown items:
- **Features**: CRM, Sales Assistant, Marketing, Mobility
- **Solutions**: B2B Business, Service Business, Agriculture Business, Channel Management
- **About**: About Us, Partners

CTA button text: `เริ่มใช้ฟรี 14 วัน`

## i18n

ทุก text element รองรับ EN/TH ผ่าน `data-i18n`, `data-en="..."`, `data-th="..."` attributes
