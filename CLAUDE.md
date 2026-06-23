# Venio CRM — Project Guide

Single-file HTML project สำหรับ Venio CRM landing page โดย Gofive.

## Files

```
venio-home.html        ← homepage (production)
venio-uob.html         ← UOB partnership page
venio-home-v2.html     ← draft เก่า ไม่ใช้แล้ว
register/uob.html      ← UOB registration form
fonts/                 ← Gofive font files (woff2)
asset/logo/            ← Venio logo SVGs
DESIGN.md              ← Design system reference (อ่านก่อนแตะ UI)
```

## Stack

- Vanilla HTML + CSS (single file, no build step)
- ไม่มี framework, ไม่มี Tailwind
- Dev server: `npx serve -p 4200 .` → เปิด `http://localhost:4200/venio-home.html`

> Design system รายละเอียดเต็มอยู่ใน `DESIGN.md`

## Critical Rules

### Buttons
- **ห้ามสร้าง custom button class** เช่น `.btn-submit` — ใช้ DS classes เท่านั้น
- Primary full-width: `class="btn btn--block"`
- อ่าน sizing/variant เพิ่มเติมใน DESIGN.md

### Fields (register pages)
- **Border: `1px`** — ห้ามใช้ `1.5px`
- **Fixed height: `48px`** — ห้ามใช้ padding แทน height
- **Equal columns:** `grid-template-columns: 1fr 1fr` + `min-width: 0`
- **อย่าเปลี่ยน field pairing** เพื่อแก้ปัญหา visual — แก้ CSS เท่านั้น
- **Picker UI:** option > 4 ตัว → ใช้ `<select>` ไม่ใช้ chip/card picker

### Page Background
- ใช้ subtle gradient เดียวกันทุกหน้า: `linear-gradient(160deg, #F2F8FF 0%, #fff 50%)`
- ห้ามใช้สีเข้มกว่า `#F2F8FF` เป็น gradient start

### Icons / Buttons with arrows
- **ห้ามใส่ box/frame รอบ icon** — ไม่มี background, ไม่มี border-radius บน icon container
- Arrow icon แสดงเปล่าๆ ไม่มีกล่อง

### Content
- **ห้ามเปลี่ยนหรือตัด text content เดิม** (headings, taglines, descriptions) เมื่อทำ visual upgrade — CSS/structure only

## Navigation (ตาม veniocrm.com)

```
[Logo] Features▾  Solutions▾  Pricing  Blog  About▾  Contact Us  |  TH  EN  |  Login  [เริ่มใช้ฟรี 14 วัน]
```

Dropdown items:
- **Features**: CRM, Sales Assistant, Marketing, Mobility
- **Solutions**: B2B Business, Service Business, Agriculture Business, Channel Management
- **About**: About Us, Partners

## i18n

ทุก text element รองรับ EN/TH ผ่าน `data-i18n`, `data-en="..."`, `data-th="..."` attributes

## Register Pages (`register/`)

### Form Layout — `register/uob.html`

**นิติบุคคล:**
```
[ชื่อ-นามสกุล ผู้ติดต่อ              — full width]
[ชื่อนิติบุคคล    ] [เลขทะเบียนนิติบุคคล]
[อีเมล            ] [🇹🇭 +66 ∨ | เบอร์โทร]
[จำนวนผู้ใช้ ∨    ] [                    ]  ← half width
```

**บุคคลธรรมดา:**
```
[ชื่อ             ] [นามสกุล             ]
[อีเมล            ] [🇹🇭 +66 ∨ | เบอร์โทร]
[จำนวนผู้ใช้ ∨    ] [                    ]  ← half width
```

### Tab Selector

ใช้ pill chip (`border-radius: 999px`) ไม่ใช่ full-width button tabs — size compact `padding: 6px 14px`

### Phone Country Dropdown

DS-spec: white card, `border-radius: 10px`, shadow `0 0 12px rgba(0,0,0,.12)`, hover `var(--brand)` blue
