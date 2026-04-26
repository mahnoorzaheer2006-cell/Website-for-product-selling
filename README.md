# 🌿 LUMIÈRE ORGANICS — Cyber-Organic Luxury Skincare Store

A premium organic beauty e-commerce SPA (Single-Page Application) built with **React 18**, **Tailwind CSS**, and the **RESTful Table API** for real-time data. Features a pitch-black `#000000` + electric neon `#00FFFF` visual identity with pulsing borders, glowing buttons, and luxury Cormorant Garamond typography.

---

## ✅ Completed Features

### 🎨 Visual Identity
- Pitch Black `#000000` background with Electric Neon Blue `#00FFFF` accents
- Cormorant Garamond (luxury serif) + Inter (clean sans-serif) typography
- Pulsing neon borders on hover, glowing "Add to Cart" buttons
- Animated marquee strip, rotating decorative rings in hero
- Fully responsive — mobile-first layout for the Pakistani market

### 🏗️ Architecture
- **React 18** SPA bootstrapped in a single `index.html` with Babel JSX transpilation
- **Hash-based client-side router** (`/#/`, `/#/shop`, `/#/product/:id`, etc.)
- **Tailwind CSS** (CDN) with custom extended config for neon animations
- **RESTful Table API** for products, orders, brand settings, and customers

### 📄 Pages / Routes

| Route | Component | Description |
|-------|-----------|-------------|
| `/#/` | `HomePage` | Hero, marquee, featured products, category columns, stats |
| `/#/shop` | `ShopPage` | Full catalogue with search + category filter pills |
| `/#/shop?cat=Body+Scrubs` | `ShopPage` | Pre-filtered category view |
| `/#/product/:id` | `ProductDetailPage` | Auto-generated detail page per product |
| `/#/login` | `LoginPage` | Customer login / register |
| `/#/account` | `LoginPage` | Customer account (shows profile when logged in) |
| `/#/track` | `TrackPage` | Order tracking widget |
| `/#/checkout` | `CheckoutPage` | 3-step COD checkout flow |
| `/#/admin-portal` | `AdminPortalPage` | 🔒 Private admin gateway |
| `/#/admin-dashboard` | `AdminDashboardPage` | 🔒 Full admin command center |

### 🔐 Dual-Gate Login Architecture
- **Customer Gateway** (`/#/login`): Public registration / login with email + password (client-side hash stored in DB)
- **Admin Gateway** (`/#/admin-portal`): Private URL — NOT linked publicly
  - 3-attempt lockout with 30-second cooldown
  - No demo credentials shown
  - Hardcoded owner access: `mahnoorzaheer2707@gmail.com` / `myweb.pk`

### 🛠️ Admin Command Center (`/#/admin-dashboard`)
- **Brand Identity Manager**: Instantly update Site Name, Tagline, Phone, Email, Free Delivery Threshold → changes reflect globally
- **Product Lifecycle Management**:
  - Add product (title, category, PKR price, description, ingredients, image URL, stock, featured toggle)
  - Every new product automatically gets its own routable detail page (`/#/product/:id`)
  - Edit any product in-place
  - Permanently delete products
- **Live Order Audit**:
  - Overview table with all COD orders
  - Click any order to see full details: customer info, items, total, notes
  - Update order status with one click (Order Placed → Processing → Out for Delivery → Delivered / Cancelled)
  - Every status change is timestamped and appended to the status history log

### 🛒 Customer Journey
- Clickable product cards → dedicated Product Detail Page with:
  - High-res image, PKR pricing, full description
  - Organic ingredient chips
  - "You May Also Like" recommendations (same category)
  - Trust badges (100% Organic, Free Delivery*, COD)
- Slide-in Cart Drawer:
  - Quantity controls (+ / −)
  - Remove individual items
  - Subtotal + delivery fee (free above PKR 3,000)
- 3-Step COD Checkout:
  1. Cart Review
  2. Delivery Information (name, phone, city, address)
  3. Order Confirmation with order ID
- Order Tracking: Enter Order ID → see visual status timeline with timestamps

### 📦 Data & Tables

| Table | Purpose |
|-------|---------|
| `lumiere_products` | Product catalogue (12 pre-seeded products) |
| `lumiere_orders` | COD orders with status timeline |
| `lumiere_brand` | Global brand config (singleton: `id=brand_config`) |
| `lumiere_customers` | Registered customer accounts |

### 🌏 Pakistani Market Optimised
- All prices in PKR
- City selector covers 12 major Pakistani cities
- Cash on Delivery only
- Free delivery above PKR 3,000

---

## 🗂️ File Structure

```
index.html          ← Single React SPA (all components, router, state)
README.md           ← This file
```

All app logic lives in `index.html` as inline JSX (Babel transpiled) following a production-equivalent component tree:

```
App
├── Navbar
├── Pages (hash-routed)
│   ├── HomePage
│   │   ├── Hero Section
│   │   ├── Marquee Strip
│   │   ├── Featured Products (ProductCard[])
│   │   └── Category Columns (ProductCard[][])
│   ├── ShopPage (search + filter)
│   ├── ProductDetailPage (auto per product)
│   ├── LoginPage (login | register | track tabs)
│   ├── CheckoutPage (3-step COD)
│   ├── AdminPortalPage (🔒 lockout gate)
│   └── AdminDashboardPage
│       ├── Overview (stats + recent orders)
│       ├── Brand Identity Manager
│       ├── Product Manager (CRUD table + form)
│       └── Live Order Audit (timeline + status updater)
├── CartDrawer (slide-in)
├── Toast (notification)
└── Footer
```

---

## 🔑 Owner Admin Access

| Field | Value |
|-------|-------|
| Admin URL | `/#/admin-portal` |
| Email | `mahnoorzaheer2707@gmail.com` |
| Password | `myweb.pk` |

> ⚠️ Keep these credentials private. The admin URL is not linked anywhere on the public storefront.

---

## 🚀 Deployment

Go to the **Publish tab** to deploy and get your live URL. No build step required — the React app runs entirely in the browser via Babel + CDN.

---

## 🔭 Recommended Next Steps

1. **Real Authentication**: Integrate Firebase Auth or Supabase for password recovery via email
2. **Image Uploads**: Connect Cloudinary or Supabase Storage for direct image file uploads
3. **WhatsApp Notifications**: Auto-send order confirmation to the owner's WhatsApp via Twilio or WATI
4. **SMS/Email Receipts**: Send customers their order ID via SMS (Jazz/Zong) or email on checkout
5. **Analytics Dashboard**: Add Chart.js charts for revenue trends and top-selling products
6. **Product Variants**: Add size/quantity variants (e.g., 100ml / 200ml)
7. **Discount Codes**: Implement coupon code system at checkout
8. **Customer Reviews**: Add product review/rating system with star ratings

