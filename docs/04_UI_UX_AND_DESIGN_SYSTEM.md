# 04: UI/UX & Design System Guidelines

> **DOCUMENT STATUS: GENERIC TEMPLATE (AWAITING PROJECT IDEA)**  
> *When a project idea is chosen, this document will define the concrete visual tokens, color scheme, typography, and component states for the application.*

---

## 1. Design Philosophy: Intentional, Clean & Accessible
- **Content-First:** Prioritize data clarity and user workflow over decorative fluff.
- **Cognitive Clarity:** Users must instantly know where they are, what they can do, and what action just completed.
- **Anti-AI Design Slop:**
  - ❌ **No Neon Accents:** Avoid arbitrary neon green or cyan glow borders/badges.
  - ❌ **No Monospace Overload:** Use normal human UI fonts (Inter, Geis, Roboto) for UI text; reserve monospace strictly for code blocks and IDs.
  - ❌ **No Emoji Headings:** Ban 🚀, ⚡, 💥, 🤖 in product titles and navigation.
  - ❌ **No Decorative Clutter:** Avoid unnecessary glassmorphism, heavy shadows, or cards wrapped in cards.
  - ❌ **No Eyebrow Spams:** Don't put an uppercase tiny chip above every single heading.

---

## 2. Design Tokens & Color System

| Token | Semantic Role | Value (Light) | Value (Dark) |
|---|---|---|---|
| `background` | Main page canvas | `[REPLACE: #FFFFFF]` | `[REPLACE: #09090B]` |
| `foreground` | High-contrast body text | `[REPLACE: #09090B]` | `[REPLACE: #F4F4F5]` |
| `primary` | Core action & brand focus | `[REPLACE: #18181B]` | `[REPLACE: #FAFAFA]` |
| `primary-foreground`| Text on primary button | `[REPLACE: #FFFFFF]` | `[REPLACE: #18181B]` |
| `muted` | Subtle surface backgrounds | `[REPLACE: #F4F4F5]` | `[REPLACE: #27272A]` |
| `muted-foreground` | Secondary/helper text | `[REPLACE: #71717A]` | `[REPLACE: #A1A1AA]` |
| `border` | Dividers & card outlines | `[REPLACE: #E4E4E7]` | `[REPLACE: #27272A]` |
| `destructive` | Errors & destructive actions | `[REPLACE: #EF4444]` | `[REPLACE: #DC2626]` |

---

## 3. Typography Hierarchy

| Style | Desktop Size | Mobile Size | Weight | Line Height | Usage |
|---|---|---|---|---|---|
| **H1** | 30px - 32px | 24px - 26px | Semi-Bold (600) | 1.25 | Page titles |
| **H2** | 22px - 24px | 18px - 20px | Semi-Bold (600) | 1.3 | Section headers |
| **H3 / Card** | 16px - 18px | 16px | Medium (500) | 1.4 | Card headers, table titles |
| **Body** | 14px - 16px | 14px | Regular (400) | 1.5 | Primary paragraphs, labels |
| **Caption** | 12px - 13px | 12px | Regular (400) | 1.4 | Helper notes, timestamps |

---

## 4. Spacing, Radius & Elevation
- **Spacing Scale:** Strict 4px base (`4px`, `8px`, `12px`, `16px`, `24px`, `32px`, `48px`).
- **Corner Radius:** Subtle and consistent (`rounded-md`: 6px / `rounded-lg`: 8px). Avoid gigantic pill shapes everywhere.
- **Elevation / Shadows:** Flat borders (`1px solid var(--border)`) preferred; use subtle shadows (`0 1px 2px rgba(0,0,0,0.05)`) only for floating dropdowns and modals.

---

## 5. Standard Component Guidelines
- **Buttons:**
  - Distinct visual states: `default`, `hover`, `active`, `focus-visible`, `disabled`, and `loading` (spinner + disabled state).
  - Explicit action hierarchy: One primary button per view section; secondary actions use outline or ghost styles.
- **Forms & Inputs:**
  - Always pair inputs with visible `<label>`.
  - Inline error messages must show below the input with red border and `aria-invalid="true"`.
- **Tables & Lists:**
  - Clear header row, zebra or subtle bottom border, sticky header for long data.
  - Built-in empty state with clear call to action when no records exist.
- **Dialogs & Modals:**
  - Esc key closes dialog, focus is trapped inside, backdrop click closes unless destructive.

---

## 6. Accessibility & Responsiveness
- **Contrast:** Minimum 4.5:1 for normal text, 3:1 for large text and UI borders.
- **Keyboard Navigation:** Every interactive element must have a visible `focus-visible` ring.
- **Touch Targets:** Minimum 44x44px hit area on mobile devices.
