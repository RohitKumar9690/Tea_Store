# React + Tailwind Store

A responsive storefront rebuilt with React, TypeScript, and Tailwind CSS. The project includes product browsing, search, filters, sorting, a persistent cart, coupon handling, product quick views, and checkout form submission.

## Features

- **Product catalogue:** Preserves the original product IDs, names, and prices.
- **Cart:** Persists cart data in `localStorage`, tracks total quantity, supports quantity changes and item removal, and prevents adding sold-out products.
- **Pricing:** Uses catalogue prices rather than parsing displayed text. Quantity is capped at available stock.
- **Coupons:** Validates codes case-insensitively and recalculates discounts when the cart changes.
- **Search:** Debounced requests, stale-response protection, loading/empty states, and a clear-search control.
- **Filtering and sorting:** Search, filters, and sorting work together without mutating the original product list.
- **Product quick view and favourites:** Opens the selected product and stores favourites per product.
- **Pincode validation:** Handles invalid-code rejections and avoids displaying stale results.
- **Checkout:** Submits the checkout form using the existing action and `POST` method.
- **Responsive UI:** Green-and-cream theme, mobile navigation, accessible controls, visible focus states, and a cart drawer.
- **Modals:** Quick view and newsletter dialogs support Escape and outside-click dismissal.
- **Newsletter prompt:** Appears once after a 12-second delay, according to the current implementation.
- **Safety and correctness:** React escapes user-provided email and pincode text instead of inserting it as HTML.

## Tech Stack

- React
- TypeScript
- Tailwind CSS
- HTML form submission
- Browser `localStorage`

## Getting Started

### Prerequisites

- Node.js and npm installed
- The project dependencies available in the repository

### Install dependencies

```bash
npm install
```

### Start the development server

```bash
npm run dev
```

### Run TypeScript checks

Use the project's configured type-check command. If `tsc` is configured directly, run:

```bash
npx tsc --noEmit
```

### Create a production build

```bash
npm run build
```

The reported production build produces a single file at `dist/index.html`. Confirm the output against your current build configuration.

## Checkout Integration

The `#checkout-form` retains its existing action and `POST` method, along with the `items` and `coupon` fields.

The `items` field currently sends JSON in this shape:

```json
[
  {
    "id": "PRODUCT_ID",
    "qty": 1
  }
]
```

**Backend verification required:** The original implementation did not specify the `items` payload format. Confirm that the server expects an array of objects with `id` and `qty` fields before deploying. Also verify how the backend expects the `coupon` field and how it reports checkout errors.

## Pricing and Catalogue Notes

- Product IDs, names, and prices are intended to remain unchanged.
- The free-shipping threshold is set to **₹499** in `src/lib/pricing.ts`, matching the advertised banner rather than the previous ₹599 cart threshold.
- The cart uses catalogue prices for calculations.
- The cart badge represents total item quantity, not the number of distinct products.
- Product quantity cannot exceed the available stock.
- Sold-out products cannot be added to the cart.

## Images and Reviews

- The original `images/pXXX.png` files were unavailable in the project, so SVG tin and box illustrations are used as placeholders.
- The customer rating is calculated from the available product review data instead of displaying the inconsistent “4.9/5 by 10,000+ customers” claim. The reported data gives an overall rating of approximately **4.7 from 470 reviews**.

Replace placeholder illustrations with the intended product photography when the image assets are available.

## Sale Banner

The original countdown date was **1 November 2025**, which is in the past. The banner now hides after its target date has passed, so it will not appear unless the target date is updated.

## Accessibility and UI

- Responsive layout and mobile navigation
- Real buttons and labelled form controls
- Visible keyboard-focus styles
- Cart drawer with an empty state and free-shipping progress
- Quick-view and newsletter modals that close with Escape or outside clicks
- Add-to-cart buttons remain visible on touch devices
- Removed jQuery, animate.css, Font Awesome, and the deprecated `<marquee>` element
- Social icons without working destination links were removed

## Verification Status

The implementation report states that:

- TypeScript checking completed without type errors.
- `npm run build` completed successfully.
- The production build generated `dist/index.html`.

**Not yet verified:** The page has not been opened in a browser, and interactive flows have not been clicked through. Run a manual smoke test before release.

### Suggested Manual Test Checklist

- [ ] Open the storefront in a fresh browser session with no existing cart data.
- [ ] Add products to the cart and confirm prices and total quantity.
- [ ] Increase/decrease quantities and remove individual items.
- [ ] Confirm sold-out products cannot be added and stock limits are respected.
- [ ] Refresh the page and verify cart and favourites persistence.
- [ ] Test valid, invalid, and differently cased coupon codes.
- [ ] Combine search, filters, and sorting.
- [ ] Submit short and long searches quickly to check stale responses are ignored.
- [ ] Open quick view for several products and verify the correct details appear.
- [ ] Test valid and invalid pincodes, including rejected API requests.
- [ ] Verify the checkout request method, action, `items` payload, and `coupon` field against the backend.
- [ ] Test newsletter modal timing, dismissal, and repeat-visit behaviour.
- [ ] Check keyboard navigation, Escape dismissal, mobile layout, and visible focus.
- [ ] Confirm the sale banner remains hidden while its target date is in the past.

## Project Decisions to Confirm

1. **Checkout payload:** Confirm the backend's expected `items` JSON schema.
2. **Free shipping:** Confirm that ₹499 is the intended threshold.
3. **Product images:** Replace SVG placeholders if the original product images become available.
4. **Review data:** Confirm the source and calculation used for the approximately 4.7/470 rating.
5. **Sale date:** Set a new target date if a sale banner should be displayed.
6. **Social links:** Add verified Instagram, Facebook, and YouTube URLs before restoring those icons.

## Legal and Contact Details

The legal paragraph identified as **MV-LGL-07**, along with the original address, email, and phone details, has been retained in the application. Keep those values consistent with the approved source content.
