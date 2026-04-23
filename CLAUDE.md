# Project: Auth Pages (Login & Register)

## Overview

Dark-themed e-commerce dashboard with authentication system using Tailwind CSS and Lucide icons. No framework — pure HTML/CSS/JS (except charts.html which uses React + Recharts).

---

## Pages

### home.html (Trang chủ / Home)

**Purpose:** Main landing page with dashboard overview, navigation sidebar, KPIs, mini charts, product table, about & contact sections.

**Stack:** Tailwind CSS via CDN, Lucide Icons via CDN, Google Fonts (Poppins + Inter), No framework.

**Layout:**
- **Top Horizontal Sidebar (sticky):** Logo + 5 nav items (Home, Products, Reports, About, Contact) + notification bell + user menu
- **Header:** Page title, period filter dropdown (7d/30d/12m), refresh button, export button
- **Filter Tags:** Category filter chips (Tất cả, Điện tử, Thời trang, Nhà cửa, Làm đẹp, Thể thao)
- **KPI Row:** 5 stat cards — Doanh thu, Đơn hàng, Sản phẩm, Khách hàng, Tỷ lệ chuyển đổi
- **Charts Row:** 3 cards — Revenue 7-day bar chart, Orders 7-day bar chart, Top categories progress bars
- **Products Table:** Best-selling products with search, category badges, revenue/sales/stock/growth columns
- **Info Row:** About section (stats) + Contact section (email/phone/address cards)
- **Footer:** Logo, copyright, login/register links

**Actions:**
- Filter by period (7d / 30d / 12m)
- Filter by category
- Search products
- Refresh data (animated icon)
- Export report (navigates to charts.html)
- Navigate between pages via sidebar

**Design:** Follows the same color palette, typography, card styling, and icon library as the rest of the project. Active nav item highlighted with primary color.

---

### products.html (Products)

**Purpose:** Product listing page with search, filter, pagination, cart, and product detail modal.

**Stack:** Tailwind CSS via CDN, Lucide Icons via CDN, Google Fonts (Poppins + Inter), No framework.

**Language:** English (100%)

**Layout:**
- **Top Horizontal Sidebar (sticky):** Logo + 5 nav items + cart icon (with badge) + logout button + user badge
- **Header:** Page title, refresh button
- **Search Bar:** Full-width text input with search icon
- **Category Filters:** Scrollable chip row (All, Electronics, Fashion, Home & Living, Beauty, Sports) + sort dropdown
- **Product Grid:** Responsive 2→3→4→5 column grid of product cards (10 per page)
- **Pagination:** Page buttons with prev/next, ellipsis for large page counts
- **Footer:** Logo + copyright + links
- **Product Detail Modal:** Full info overlay (image, badge, name, rating, price, description, stats, add-to-cart)
- **Cart Sidebar:** Slide-in from right (item list, qty controls, remove, total, checkout)

**Mock Data:** 15 products across 5 categories with realistic prices, icons, descriptions, ratings, and stock.

**Actions:**
- Search products (live filter by name/category/description)
- Filter by category (chip buttons)
- Sort by: Default, Price Low→High, Price High→Low, Best Sellers, Name A→Z
- View product detail (modal with full info)
- Add to cart (with toast notification, persists to localStorage)
- Cart management: qty +/-, remove item
- Checkout (clears cart, shows total)
- Pagination (10 items/page)
- Refresh (animated icon + toast)

**Cart Storage:** `localStorage.setItem('cart', JSON.stringify([{id, qty}]))`

---

### charts.html

**Purpose:** E-commerce analytics dashboard showing revenue, business results, and marketing metrics.

**Stack:** React 18 + Recharts 2.10.3 (via CDN), Tailwind CSS, Lucide icons, Babel for JSX.

**Tabs:**
| Tab | Content |
|---|---|
| **Overview** | KPI cards + Revenue vs Target bar chart + Category pie chart + Daily sales area chart + Top products table |
| **Revenue** | Revenue KPIs + Monthly revenue/orders line+bar combo chart + Full monthly breakdown table |
| **Marketing** | Marketing KPIs + ROI horizontal bar chart + Spend vs Revenue chart + Channels performance table |

**Mock Data:** 12 months of revenue/orders/visitors, 6 marketing channels (Google Ads, Facebook Ads, Email, SEO, Influencer, Affiliates), 8 top products, daily sales for the week.

**Libraries (CDN):**
- `https://unpkg.com/react@18/umd/react.production.min.js`
- `https://unpkg.com/react-dom@18/umd/react-dom.production.min.js`
- `https://unpkg.com/recharts@2.10.3/umd/Recharts.js`
- `https://unpkg.com/@babel/standalone/babel.min.js`

**Features:** Period selector (7d / 30d / 12m), Export button, responsive grid layout, custom Recharts tooltips, data tables with hover states and totals footer.

---

### login.html

**Purpose:** User sign-in page.

**Fields:**
- Email Address (text input, optional)
- Password (password input, optional, with show/hide toggle)
- Remember me (checkbox)
- Forgot password? (link)

**Actions:**
- Sign In button (CTA, primary color `#DF6B33`)
- Social login: Google, GitHub, Facebook
- Navigate to register page ("Sign up free")

**Social Login:** Google (SVG), GitHub (SVG), Facebook (SVG) — icon-only on mobile, icon + label on tablet/PC.

---

### register.html

**Purpose:** User account creation page.

**Fields:**
| Field | Required | Input Type | Icon |
|---|---|---|---|
| Full Name | **Yes** (`*`) | text | `user` |
| Email Address | No | email | `mail` |
| Password | No | password | `lock` |
| Gender | No | select dropdown | `gender` |
| Phone Number | No | tel | `phone` |
| Address | No | text | `map-pin` |

**Actions:**
- Create Account button (CTA, primary color `#DF6B33`)
- Social login: Google, GitHub, Facebook
- Navigate back to login page ("Sign in")

---

## Design System

### Color Palette

| Token | Hex | Usage |
|---|---|---|
| `dark-bg` | `#090A14` | Page background |
| `dark-card` | `#111827` | Card / form container |
| `dark-border` | `#1F2937` | Input borders, dividers |
| `primary` | `#DF6B33` | CTA buttons, links, accent |
| `primaryHover` | `#C45A28` | CTA hover state |

### Typography

| Role | Font | Weight |
|---|---|---|
| Headings / Titles | **Poppins** | 700, 800 |
| Body / Labels / Inputs | **Inter** | 400, 500, 600 |

CDN: `https://fonts.googleapis.com/css2?family=Poppins:wght@700;800&family=Inter:wght@400;500;600&display=swap`

### Icon Library

**Lucide Icons** — CDN: `https://unpkg.com/lucide@latest/dist/umd/lucide.js`

Load with `lucide.createIcons()`. Re-run after dynamically changing icon names (e.g., password toggle).

### Input Styling

- Background: `#090A14` (`bg-dark-bg`)
- Border: `#1F2937` (`border-dark-border`)
- Focus: border `#DF6B33` + `ring-1 ring-primary`
- Border radius: `rounded-xl`
- Padding: `py-3 pl-10 pr-4` (icon on left, toggle on right when needed)
- Placeholder color: `placeholder-gray-500`

### Card Styling

- Background: `#111827` (`bg-dark-card`)
- Border: `#1F2937` (`border-dark-border`)
- Border radius: `rounded-2xl`
- Padding: `p-6` mobile, `sm:p-8` tablet+
- Shadow: `shadow-2xl shadow-black/50`

### Button Styling

- **CTA (primary):** `bg-primary hover:bg-primaryHover`, text white, `shadow-lg shadow-primary/20`, `rounded-xl`
- **Social:** `bg-dark-bg border border-dark-border hover:border-gray-600`, `rounded-xl`, icon + optional label

### Responsive Strategy

- Container max-width: `max-w-md`
- Social buttons: label hidden on mobile (`hidden sm:inline`), icon always visible
- Card padding: `p-6` → `sm:p-8`

---

## Language

All pages use **English (100%)** for all UI text, labels, buttons, and content.

---

## General Rules for Future Pages

1. **Theme & Colors:** Always use the color tokens above. Do not introduce new colors without good reason.
2. **Fonts:** Poppins for headings (bold/extrabold), Inter for body text.
3. **Responsive:** Design mobile-first. Test on mobile, tablet, and desktop.
4. **Icons:** Use Lucide icons via CDN. Keep icons consistent with the rest of the UI.
5. **Input Validation:** Mark required fields with `*` (color `#DF6B33`). Use HTML5 `required` attribute.
6. **Page Navigation:** Provide clear links between related pages (e.g., login ↔ register). Use `href="login.html"` / `href="register.html"` instead of `#`.
7. **Accessibility:** All inputs must have `<label>` with `for` attribute matching input `id`. Use semantic HTML (`<button>`, `<a>`, `<input>`).
8. **Dark Theme Only:** No light theme variants unless explicitly requested.

---

## Stack

### home.html / products.html / login.html / register.html
- Tailwind CSS via CDN (`https://cdn.tailwindcss.com`)
- Lucide Icons via CDN
- Google Fonts (Poppins + Inter)
- No build tools, no framework

### charts.html
- React 18 + ReactDOM 18 (CDN)
- Recharts 2.10.3 (CDN)
- Babel Standalone (CDN, JSX transform)
- Tailwind CSS via CDN
- Lucide Icons via CDN
- Google Fonts (Poppins + Inter)
