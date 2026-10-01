# 🍵 Tea Store

A responsive tea e-commerce storefront rebuilt with **React, TypeScript, and Tailwind CSS**. 🌿 The project features product browsing, search, filters, sorting, a persistent shopping cart, coupon handling, product quick views, and checkout form submission.

🔗 **Live Demo:** https://teastore1110.netlify.app

## ✨ Features

* 🛍️ **Product Catalogue:** Preserves the original product IDs, names, and prices.
* 🛒 **Smart Shopping Cart:** Persists cart data in `localStorage`, tracks total quantity, supports quantity changes and item removal, and prevents adding sold-out products.
* 💰 **Accurate Pricing:** Uses catalogue prices for calculations and caps quantities at available stock.
* 🎟️ **Coupon System:** Validates coupon codes case-insensitively and recalculates discounts when the cart changes.
* 🔎 **Smart Search:** Includes debounced requests, stale-response protection, loading and empty states, and a clear-search control.
* 🎛️ **Filtering & Sorting:** Search, filters, and sorting work together without mutating the original product list.
* ❤️ **Product Quick View & Favourites:** Opens selected product details and stores favourites per product.
* 📍 **Pincode Validation:** Handles invalid-code rejections and prevents stale results from being displayed.
* 💳 **Checkout Integration:** Submits the checkout form using the existing action and `POST` method.
* 📱 **Responsive Design:** Features a green-and-cream theme, mobile navigation, accessible controls, visible focus states, and a cart drawer.
* 🪟 **Interactive Modals:** Quick-view and newsletter dialogs support Escape and outside-click dismissal.
* 📩 **Newsletter Popup:** Appears once after a 12-second delay, according to the current implementation.
* 🔐 **Safer User Input:** React escapes user-provided email and pincode text instead of inserting it as HTML.

## 🧰 Tech Stack

* ⚛️ React
* 📘 TypeScript
* 🎨 Tailwind CSS
* 🌐 HTML Form Submission
* 💾 Browser `localStorage`

## 🚀 Getting Started

### 📋 Prerequisites

* Node.js and npm installed
* Project dependencies available in the repository

### 📦 Install Dependencies

```bash
npm install
```

### ▶️ Start the Development Server

```bash
npm run dev
```

### 🧪 Run TypeScript Checks

```bash
npx tsc --noEmit
```

Use the project's configured type-check command if it differs.

### 🏗️ Create a Production Build

```bash
npm run build
```

The reported production build generates `dist/index.html`. Confirm the output against your current build configuration.

## 💳 Checkout Integration

The `#checkout-form` retains its existing action and `POST` method, along with the `items` and `coupon` fields.

The current `items` payload follows this structure:

```json
[
  {
    "id": "PRODUCT_ID",
    "qty": 1
  }
]
```

⚠️ **Backend Verification Required:** Confirm that the server expects an array of objects containing `id` and `qty` before deploying. Verify the expected `coupon` format and how checkout errors are reported.

## 💰 Pricing & Catalogue Notes

* ✅ Product IDs, names, and prices are intended to remain unchanged.
* 🚚 Free-shipping threshold: **₹499**, configured in `src/lib/pricing.ts`.
* 🧾 Cart calculations use catalogue prices.
* 🔢 The cart badge displays the total item quantity, not the number of distinct products.
* 📦 Product quantities cannot exceed available stock.
* 🚫 Sold-out products cannot be added to the cart.

## 🖼️ Images & Customer Reviews

* 🎨 SVG tin and box illustrations are used as placeholders because the original `images/pXXX.png` files were unavailable.
* ⭐ The customer rating is calculated from available product review data instead of displaying the inconsistent “4.9/5 by 10,000+ customers” claim.
* 📊 The reported review data gives an overall rating of approximately **4.7 from 470 reviews**.

Replace the placeholder illustrations with the original product photography when those assets become available.

## 🏷️ Sale Banner

The original countdown date was **1 November 2025**, which is in the past. The banner now hides after its target date has passed. Update the target date if the sale banner should appear again.

## ♿ Accessibility & UI Improvements

* 📱 Responsive layout and mobile navigation
* 🖱️ Real buttons and labelled form controls
* ⌨️ Visible keyboard-focus styles
* 🛒 Cart drawer with an empty state and free-shipping progress
* 🪟 Quick-view and newsletter modals with Escape and outside-click dismissal
* 👆 Add-to-cart buttons remain visible on touch devices
* 🧹 Removed jQuery, animate.css, Font Awesome, and the deprecated `<marquee>` element
* 🔗 Removed social icons without working destination links

## 🧪 Verification Status

According to the implementation report:

* ✅ TypeScript checking completed without type errors.
* ✅ `npm run build` completed successfully.
* ✅ The production build generated `dist/index.html`.
* ⚠️ Browser testing and interactive-flow verification have not yet been completed.

### 📝 Suggested Manual Test Checklist

* [ ] Open the storefront in a fresh browser session.
* [ ] Add products and verify prices and total quantity.
* [ ] Change quantities and remove items.
* [ ] Verify stock limits and sold-out product restrictions.
* [ ] Refresh the page and check cart and favourites persistence.
* [ ] Test valid, invalid, and differently cased coupon codes.
* [ ] Combine search, filters, and sorting.
* [ ] Test rapid searches for stale-response issues.
* [ ] Open quick views for multiple products.
* [ ] Test valid and invalid pincodes, including rejected API requests.
* [ ] Verify checkout method, action, `items` payload, and `coupon` field.
* [ ] Test newsletter timing, dismissal, and repeat visits.
* [ ] Check keyboard navigation, mobile layouts, and modal dismissal.
* [ ] Confirm the sale banner stays hidden while its target date is in the past.

## 🔧 Project Decisions to Confirm

1. 💳 **Checkout Payload:** Confirm the backend's expected `items` JSON schema.
2. 🚚 **Free Shipping:** Confirm the ₹499 threshold.
3. 🖼️ **Product Images:** Replace SVG placeholders if original images become available.
4. ⭐ **Review Data:** Confirm the source and calculation behind the approximately 4.7/470 rating.
5. 🏷️ **Sale Date:** Set a new target date if the sale banner should be displayed.
6. 📱 **Social Links:** Add verified Instagram, Facebook, and YouTube URLs before restoring those icons.

## 📜 Legal & Contact Details

The legal paragraph identified as **MV-LGL-07**, along with the original address, email, and phone details, has been retained in the application. Keep these values consistent with the approved source content.

---

🌱 **Explore the live storefront:** https://teastore1110.netlify.app

☕ *A modern, responsive tea-shopping experience built with a focus on usability, accessibility, and reliable cart functionality.*
