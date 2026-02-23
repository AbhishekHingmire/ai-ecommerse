# DRIP — Cart & Purchase Module Prompts
# Frontend simulation only (no backend, all localStorage)

---

## DESIGN SYSTEM (paste into every prompt)

```
DESIGN SYSTEM — Copy this into every prompt verbatim:

Brand: DRIP — AI-powered fashion virtual try-on web app.
Stack: Single HTML file, Tailwind CSS via CDN, vanilla JS only. No frameworks.

Colors (extend Tailwind config):
- brandBg: #0A0A0F
- brandSurface: #13131A
- brandBorder: #2A2A35
- brandPrimary: #F5F0E8
- brandMuted: #8A8A9A
- brandGold: #C9A84C
- brandGoldHover: #E2C06A
- brandSuccess: #4CAF82
- brandError: #E05A5A

Fonts: Cormorant Garamond (display, weights 300–600) + DM Sans (UI/body, weights 300–500)
font-display = Cormorant Garamond | font-sans = DM Sans

Rules:
- Every button: default / hover (lift + shadow) / active (press down) / loading states
- Cards: hover translateY -4px, border → gold on hover, transition-all 300ms
- Skeleton loaders: shimmer gradient #13131A → #2A2A35 → #13131A
- All data persisted in localStorage (no backend — frontend simulation only)
- Max content width: max-w-7xl mx-auto | Generous padding: py-24 desktop, py-16 mobile
- Smooth scroll on html | Mobile first | Fully responsive 375px and 1440px
- No lorem ipsum — real copy throughout
```

---

## NEW FILES IN BUILD ORDER

| # | File | Page |
|---|------|------|
| 10 | cart.html | Cart / Bag Page |
| 11 | checkout.html | Checkout Flow (3 steps) |
| 12 | order-success.html | Order Confirmation |
| 13 | orders.html | My Orders (in Dashboard) |

### localStorage Keys for this module
```
drip_cart        → array of {outfitId, name, brand, price, originalPrice, size, color, qty, image, affiliateUrl}
drip_orders      → array of {orderId, date, items[], total, status, deliveryDate}
drip_user        → {name, email, phone, address{}} (extends existing)
```

---

---

# PROMPT 10 — CART PAGE
**File: cart.html**

---

> Build a complete, production-ready, fully responsive **Shopping Cart page** for DRIP in a single HTML file using HTML5, Tailwind CSS CDN, vanilla JS. All data is stored and read from localStorage — no backend. Simulate all interactions at frontend only.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> On page load: read `drip_cart` from localStorage. If empty, show empty state. Pre-populate with 3 demo items on first load if `drip_cart` doesn't exist yet (so page always shows content for demo).
>
> Demo cart items to pre-populate:
> ```
> Item 1: Classic Bandhgala Kurta Set | Manyavar | ₹2,499 (was ₹3,999) | Size: M | Color: Navy | Qty: 1 | picsum?random=80
> Item 2: Slim Fit Chinos | H&M India | ₹1,299 (was ₹1,799) | Size: 32 | Color: Olive | Qty: 1 | picsum?random=42
> Item 3: Oversized Graphic Tee | Being Human | ₹799 | Size: L | Color: White | Qty: 2 | picsum?random=45
> ```
>
> ---
>
> ## NAVBAR — same as all pages
> Logo left. Center links. Right: Cart icon with item count badge (gold filled circle, dark number, absolute top-right of icon). Login/avatar. The cart count badge updates live as items are added/removed.
>
> ---
>
> ## PAGE HEADER
> Background `#13131A`. py-12. Max-w-7xl centered px-6.
> Left: "My Bag" Cormorant Garamond 40px. Below: "3 items" muted DM Sans 14px (updates live).
> Right: "Continue Shopping →" muted link → explore.html. And "✨ Try On More Outfits →" gold outlined pill → tryon.html.
>
> ---
>
> ## MAIN LAYOUT — Two column desktop (cart items left 65%, order summary right 35%). Stacked mobile (summary goes below items).
>
> ---
>
> ### LEFT COLUMN — Cart Items
>
> Each cart item is a card: Background `#13131A`. Border `#2A2A35`. Rounded-2xl. Padding p-5. Flex row gap-5. Hover: border gold subtle.
>
> **Card structure (left to right):**
>
> 1. Product image: 100px × 130px, rounded-xl, object-cover, border `#2A2A35`. picsum image for that item.
>
> 2. Product details (flex-1):
>    - Brand: DM Sans 11px muted uppercase tracking-wide
>    - Name: Cormorant Garamond 20px primary, hover → gold transition
>    - Attributes row: "Size: M" · "Color: Navy" — muted DM Sans 13px. Each attribute has a small "Change" link in gold 11px that opens an inline dropdown (JS) to change size/color. Changing updates localStorage.
>    - Price row: Current price gold 18px font-medium + Original struck-through muted 14px (if discounted) + Savings pill ("Save ₹1,500") green border green text 11px rounded-full.
>    - Action links row (bottom of details): "✨ Try On Again →" gold 12px link → tryon.html?outfit=N | "♡ Save for Later" muted 12px link → moves item to wishlist (localStorage) + removes from cart with fade-out | "🗑 Remove" muted 12px link → confirm inline (small "Remove this item?" overlay on the card with Yes/No buttons) → on confirm: card fades out and slides up (height animates to 0), cart count updates.
>
> 3. Quantity selector (right side, vertical center):
>    - Minus button (circle, border `#2A2A35`, muted −, hover gold) — qty 1 min: minus is disabled/muted
>    - Quantity number display: DM Sans 16px primary, min-width 32px text-center
>    - Plus button (circle, border `#2A2A35`, muted +, hover gold) — max 10
>    - Clicking +/−: updates qty in localStorage, recalculates all totals live (order summary updates with count-up animation on price change)
>
> **Between items:** thin divider `#2A2A35`.
>
> **Below all items:**
> - "← Continue Shopping" muted link left → explore.html
> - "Clear Bag" muted link right → custom confirm modal: "Remove all items from your bag?" Red "Clear Bag" + "Cancel" buttons. On confirm: all cards fade out → empty state appears.
>
> **"Saved for Later" section** (below cart items, separated by a label):
> Label "SAVED FOR LATER" gold uppercase 11px tracking-widest. If any items were saved for later (from wishlist or "Save for Later" action), show them in a compact horizontal scroll strip. Each: small card with image, name, price, "Move to Bag" gold button (adds back to cart).
>
> ---
>
> ### RIGHT COLUMN — Order Summary (sticky top-24 desktop)
>
> Surface card `#13131A`. Border `#2A2A35`. Rounded-2xl. Padding p-6.
>
> **Header:** "Order Summary" DM Sans 13px muted uppercase tracking-wide.
>
> **Price breakdown (each row: label left, value right, DM Sans 14px):**
> - Subtotal: ₹X,XXX (sum of all item prices × qty)
> - Discount: − ₹X,XXX (sum of all savings, in green)
> - Delivery: "FREE" in green (or ₹99 if subtotal < ₹999)
> - Divider line
> - **Total: ₹X,XXX** — DM Sans 20px gold font-medium + "Incl. all taxes" muted 11px below
>
> All values update live as cart changes (smooth count-up animation using JS).
>
> **Coupon code section:**
> "Have a coupon?" label muted 12px. Input + "Apply" button row. Input: dark surface, `#2A2A35` border, gold focus, rounded-xl, placeholder "Enter code". Apply button: gold outlined, rounded-xl.
> - Code "DRIP10" → applies 10% discount. Row animates in: "DRIP10 — 10% off applied ✓" green row + × to remove. Total recalculates.
> - Invalid code → input border red, shake animation, "Invalid coupon code" error below.
>
> **Delivery estimate:** "🚚 Estimated delivery: 3–5 business days" muted 13px icon + text row.
>
> **Primary CTA: "Proceed to Checkout →"** Full-width. Gold filled. Rounded-2xl. py-4. Cormorant Garamond 20px. Hover: scale 1.02, gold glow. Clicking → checkout.html. If cart is empty: button is disabled, muted, "Add items to proceed".
>
> **Trust signals below button** (3 rows, icon + text, muted 12px):
> - 🔒 "Secure checkout — SSL encrypted"
> - 🔄 "Easy 7-day returns on all orders"
> - ✅ "Authentic products from verified brands"
>
> **"Or continue with affiliate links"** section below trust signals: Thin divider. Muted 12px text: "Prefer to buy directly from the brand?" Then a vertical list of each cart item with a compact row: brand logo placeholder circle + item name + "Buy on [Brand] →" gold external link opening affiliate URL in new tab. This is the fallback affiliate conversion path.
>
> ---
>
> ## EMPTY STATE (when cart is empty)
> Centered in main content area. Large shopping bag SVG icon (gold outline, 80px). "Your bag is empty." Cormorant Garamond 36px. Muted subtext: "You haven't added any outfits yet. Try some on and find what you love." Two buttons: "Browse Outfits" (gold filled) → explore.html and "✨ Try On Outfits" (outlined gold) → tryon.html.
>
> ---
>
> ## FLOATING CART DRAWER (global component — inject into all pages)
>
> A slide-in drawer from the right side. Triggered by cart icon in navbar on ALL pages. Width 400px desktop, full-width mobile. Background `#13131A`. Border-left `#2A2A35`. Z-60. Overlay behind it.
>
> Drawer header: "My Bag (3)" Cormorant 24px + × close button.
>
> Compact cart item list (scrollable): Each item row: 60px image + name + size + price + qty +/− controls + × remove. Max-height: calc(100vh - 200px), overflow-y auto.
>
> Drawer footer (sticky bottom of drawer): Subtotal row. "View Full Bag" outlined gold button → cart.html. "Checkout →" gold filled button → checkout.html. Both full-width.
>
> Opening animation: translateX(100%) → translateX(0), 400ms ease-out. Closing: reverse. Overlay fades in/out.
>
> ---
>
> ## JS BEHAVIORS
> 1. Load cart from localStorage on page load (pre-populate demo items if empty)
> 2. Qty +/− → update localStorage → recalculate all totals live with animation
> 3. Remove item → inline confirm overlay → fade out + slide up → update count
> 4. Save for Later → move item from drip_cart to drip_wishlist → update both
> 5. Coupon code apply/remove → recalculate totals
> 6. Clear bag → confirm modal → clear localStorage drip_cart → empty state
> 7. Cart icon badge count → always reads from localStorage drip_cart.length
> 8. All price totals update with smooth count animation (requestAnimationFrame counter)
> 9. Cart drawer: open/close from navbar icon, update live, close on overlay click / ESC
> 10. "Proceed to Checkout" → save cart state → navigate to checkout.html

---

---

# PROMPT 11 — CHECKOUT PAGE
**File: checkout.html**

---

> Build a complete, production-ready, fully responsive **Checkout page** for DRIP in a single HTML file. 3-step checkout flow simulated entirely at frontend using vanilla JS and localStorage. No backend, no payment processing — simulate all states.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## MINIMAL NAVBAR (checkout mode)
> Logo "DRIP" left gold. Center: Step progress indicator (see below). Right: "🔒 Secure Checkout" muted 12px with lock icon. No other nav links — minimize distractions during checkout.
>
> ---
>
> ## STEP PROGRESS INDICATOR (also in navbar center)
> 3 steps connected by a line:
> - Step 1: "Delivery" — circle with "1"
> - Step 2: "Payment" — circle with "2"
> - Step 3: "Review" — circle with "3"
>
> Active step: gold filled circle, gold text below. Completed step: gold circle with ✓ checkmark, muted line turns gold. Upcoming step: muted circle, muted text.
>
> Connecting line between circles: background `#2A2A35`, fills gold as steps complete (width animation).
>
> Also shown large below navbar for mobile (horizontal centered, same design but bigger).
>
> ---
>
> ## MAIN LAYOUT — Same two-column as cart: form left (65%), order summary right (35%). Stacked mobile.
>
> Order summary (right column): Same as cart page order summary — sticky, shows items, totals, coupon. Read from localStorage `drip_cart`. Non-editable here (no qty changes). At bottom: "← Edit Bag" muted link → cart.html.
>
> ---
>
> ## STEP 1 — DELIVERY DETAILS (default visible)
>
> Section heading: "01 — Delivery Details" Cormorant Garamond 28px gold.
>
> **Saved addresses block** (shown if localStorage `drip_user.addresses` has entries):
> "Your saved addresses" label. Address cards in a 2-column grid. Each: surface card, border `#2A2A35` rounded-xl p-4. Radio button top-right (gold when selected). Address text: Name (bold DM Sans 14px), full address, phone. "Edit" + "Delete" small links muted.
> "Add New Address +" outlined gold pill button → expands the address form below.
> If no saved addresses: skip straight to form.
>
> **Address form (always shown if no saved addresses, otherwise collapsible):**
>
> Form fields in 2-column grid (single column mobile):
> - Full Name* | Phone Number*
> - Email Address* | (empty or alternate field)
> - Address Line 1* (full width span-2): placeholder "House no., Building, Street name"
> - Address Line 2 (full width span-2): placeholder "Locality, Area (optional)"
> - City* | State* (custom styled select: same dark surface, gold focus, options: all Indian states)
> - PIN Code* | Country (prefilled "India", disabled)
>
> All inputs: dark surface `#13131A`, border `#2A2A35`, rounded-xl, gold focus border + glow, DM Sans 14px. Label above each: DM Sans 11px muted uppercase. Required fields marked with gold *.
>
> **Save address checkbox:** Custom checkbox (gold checkmark on dark) "Save this address for future orders". Default checked.
>
> **Delivery options** (below address form):
> Label "CHOOSE DELIVERY" gold uppercase 11px.
> 3 option cards in a row (stack mobile), each: border `#2A2A35` rounded-xl p-4 cursor-pointer. Selected: gold border.
> - "Standard Delivery" — 5–7 days — FREE (green) — if order > ₹999
> - "Express Delivery" — 2–3 days — ₹149 — adds to total live
> - "Same Day" — Today by 9 PM — ₹299 — "Available in select cities" muted badge
>
> Default selected: Standard Delivery.
>
> **"Continue to Payment →"** gold filled full-width py-4 Cormorant 20px button. On click: JS validates all required fields (inline errors on each empty/invalid field — red border, shake, error text below). If valid: step 1 fades out, step 2 fades in, progress indicator advances. Save address data to localStorage `drip_user.address`.
>
> ---
>
> ## STEP 2 — PAYMENT (hidden initially, shown after step 1)
>
> Section heading: "02 — Payment" Cormorant Garamond 28px gold.
>
> Delivery summary bar (thin card): shows selected address summary + "Change" gold link → goes back to step 1.
>
> **Payment method selector:**
>
> 4 method cards (stack vertically), each: border `#2A2A35` rounded-xl p-4, flex row, radio left, icon + label + description right. Selected: gold border, gold radio fill.
>
> Method 1 — UPI (default selected):
> - Icon: UPI logo placeholder (colored circle "UPI" text)
> - Label: "UPI" DM Sans 14px bold
> - Sub: "Google Pay, PhonePe, Paytm, BHIM" muted 12px
> - **Expanded panel (shown when selected):** UPI ID input (dark surface, gold focus, placeholder "yourname@upi" or "9876543210@ybl"). "Verify & Pay" button gold filled — clicking: loading state 2 seconds → success animation (see payment simulation below).
>
> Method 2 — Card:
> - Icon: credit card SVG gold
> - Label: "Credit / Debit Card"
> - Sub: "Visa, Mastercard, RuPay"
> - **Expanded panel:** Card number input (auto-formats as 4-4-4-4 with JS), Expiry MM/YY, CVV (masked), Name on card. Card type icon auto-detects (Visa/MC) from first digits and shows icon in input right side.
>
> Method 3 — Net Banking:
> - Icon: bank SVG
> - **Expanded panel:** Dropdown to select bank (styled custom select with top 8 Indian banks: SBI, HDFC, ICICI, Axis, Kotak, PNB, BoB, Canara). "Proceed to Net Banking →" gold button → shows bank redirect simulation.
>
> Method 4 — Cash on Delivery:
> - Icon: cash/wallet SVG
> - Sub: "Pay when your order arrives · ₹29 COD fee" — fee added to total
> - No expanded panel needed — just selecting this is enough.
>
> **"Pay ₹X,XXX →"** gold filled full-width py-4 Cormorant 20px button (amount shows actual total from localStorage). On click → payment simulation (see below).
>
> **"← Back to Delivery"** muted text link left → animates back to step 1.
>
> ---
>
> ## PAYMENT SIMULATION (frontend only — full animation sequence)
>
> On clicking "Pay" / "Verify & Pay":
>
> 1. Button enters loading state: spinner inside, text "Processing..." — 2 seconds
> 2. Full-screen payment processing overlay appears (z-60): dark background, centered content:
>    - Animated spinner (gold, large, smooth CSS rotation)
>    - "Processing your payment..." Cormorant Garamond 28px
>    - "Please do not close this window." muted 14px
>    - Thin gold progress bar animating 0→100% over 3 seconds
> 3. After 3 seconds: overlay content transitions to success:
>    - Large green checkmark circle (scale-in bounce animation — scale 0 → 1.2 → 1.0)
>    - "Payment Successful! 🎉" Cormorant Garamond 32px gold
>    - "₹X,XXX paid via UPI" muted
>    - Auto-redirect countdown: "Redirecting to your order in 3..." (JS countdown 3→2→1)
>    - After 3 seconds → navigates to order-success.html
>    - Before navigating: saves order to localStorage `drip_orders` array and clears `drip_cart`
>
> **Payment failure simulation (for demo):** If user types "FAIL" in UPI ID or card number "4000 0000 0000 0000":
> - Overlay shows error state: red × circle (same bounce animation), "Payment Failed" red Cormorant 28px, "Your payment could not be processed. Please try again or use a different method." muted. "Try Again" gold button → closes overlay, back to payment form. "Use Different Method" muted link.
>
> ---
>
> ## STEP 3 — REVIEW ORDER (shown BEFORE payment button — between step 2 method selection and pay button)
>
> Actually implement this as a confirmation step before submitting payment. When user has filled payment details and clicks "Review Order →" (instead of directly paying):
>
> Section heading: "03 — Review Your Order" Cormorant Garamond 28px gold.
>
> **Order items review:** Compact list of cart items with image, name, size, qty, price. Read-only.
>
> **Delivery summary:** Address block read-only. Delivery method + estimated date.
>
> **Payment summary:** "Paying via UPI (user@upi)" or selected method. Amount.
>
> **Price summary:** Subtotal, discount, delivery, coupon, **Total bold gold.**
>
> **Terms checkbox:** Custom gold checkbox "I agree to DRIP's Terms of Service and Return Policy." Must be checked to enable pay button (JS). Unchecked: pay button disabled + muted. Checked: pay button activates gold.
>
> **"Confirm & Pay ₹X,XXX →"** gold filled full-width py-5 Cormorant 22px. → triggers payment simulation.
>
> **"← Edit Payment"** muted link → back to step 2.
>
> ---
>
> ## JS BEHAVIORS
> 1. Multi-step form: fade transition between steps, progress indicator advances
> 2. Step 1 form validation: inline errors per field, scroll to first error on submit
> 3. "Save address" → push to localStorage drip_user.addresses array
> 4. Saved address selection (radio) → pre-fills form fields
> 5. Delivery option select → recalculate total in order summary live
> 6. COD selection → add ₹29 fee to total live
> 7. Card number auto-format (XXXX XXXX XXXX XXXX)
> 8. Card type detection (Visa: starts 4, MC: starts 5) → show icon in field
> 9. CVV field: masked (type=password behavior)
> 10. Payment simulation sequence (full overlay, success/fail states)
> 11. Terms checkbox gates pay button enabled/disabled state
> 12. On successful payment: generate order object → push to drip_orders → clear drip_cart → navigate to order-success.html
> 13. "FAIL" keyword in UPI / card number triggers failure simulation

---

---

# PROMPT 12 — ORDER SUCCESS / CONFIRMATION
**File: order-success.html**

---

> Build a complete, production-ready, fully responsive **Order Confirmation page** for DRIP in a single HTML file. All data read from localStorage `drip_orders` last entry. Single HTML file, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This page should feel celebratory and premium — the user just bought something they tried on. Reinforce the decision and drive next actions.
>
> ---
>
> ## NAVBAR — minimal (same as checkout navbar, no links, just logo + "🔒 Secure" right)
>
> ---
>
> ## HERO — SUCCESS CELEBRATION SECTION
> Full-width. Background: radial gradient from `rgba(74,175,130,0.08)` (green glow) centered, on `#0A0A0F`. py-20. Text center.
>
> **Animated checkmark:** Large circle (120px) with green border, white checkmark SVG inside. On page load: circle scales in (scale 0 → 1.0, 600ms ease-out with a slight overshoot bounce — cubic-bezier), then checkmark draws itself (SVG stroke-dasharray animation, 400ms delay). After that: subtle continuous pulse glow animation (box-shadow green 0→20px→0, 2s infinite).
>
> **Headline:** "Order Confirmed! 🎉" — Cormorant Garamond 52px desktop / 36px mobile. Primary color. Appears with fade-up animation (translateY 20px → 0, opacity 0 → 1, 300ms delay after checkmark).
>
> **Sub:** "Thank you, Rahul! Your order is on its way." muted DM Sans 18px.
>
> **Order ID row:** "Order #DRP-2025-08471" — DM Sans 13px muted. Copy icon next to it — clicking copies to clipboard + brief gold flash.
>
> **Estimated delivery:** "📦 Expected by Thursday, Feb 27, 2025" — surface card inline pill, gold border, DM Sans 14px.
>
> ---
>
> ## ORDER DETAILS CARD
> Max-w-2xl mx-auto px-6. Surface card `#13131A`. Border gold (celebration state). Rounded-2xl. p-8.
>
> **Card header:** "Your Order" DM Sans 13px muted uppercase + Order ID right.
>
> **Items list:** Each item row: 70px image rounded-xl + details (name Cormorant 18px, brand+size+color muted 12px, qty) + price right gold. Divider between items.
>
> **Price summary block:** Same rows as checkout review (Subtotal / Discount / Delivery / Total). Total row: larger, gold, bold.
>
> **Delivery details block:** Divider. "Delivering to:" label muted uppercase 11px. Address card: name, address, phone in DM Sans 14px muted/primary. "Change address" muted 12px (disabled on confirmation — just visual).
>
> **Payment block:** "Paid via:" label. Payment method used + amount in green "✓ ₹X,XXX Paid" with checkmark.
>
> ---
>
> ## ORDER TRACKING TIMELINE (below details card)
> Max-w-2xl mx-auto px-6. "Track Your Order" Cormorant 28px heading.
>
> Vertical timeline (left line connecting circles):
>
> Step 1 — ✓ "Order Placed" — gold circle filled ✓ — "Today, just now" gold text — completed
> Step 2 — ✓ "Payment Confirmed" — gold circle filled ✓ — "Today, just now" — completed
> Step 3 — ⏳ "Being Packed" — animated pulsing circle (gold border, pulsing CSS animation) — "Estimated: Tomorrow" muted — IN PROGRESS
> Step 4 — ○ "Shipped" — empty muted circle — "Est. Feb 25" muted — upcoming
> Step 5 — ○ "Out for Delivery" — empty muted circle — "Est. Feb 27" muted — upcoming
> Step 6 — ○ "Delivered" — empty muted circle — "Est. Feb 27" muted — upcoming
>
> Connecting vertical line: `#2A2A35`, sections between completed steps turn gold.
>
> "Get SMS updates" toggle (custom gold toggle switch): "Receive delivery updates on your phone." Clicking: shows success toast "SMS alerts enabled ✓".
>
> ---
>
> ## "WHAT'S NEXT?" SECTION
> Background `#13131A`. Max-w-7xl mx-auto px-6 py-16.
> Heading: "While you wait..." Cormorant Garamond 36px centered.
>
> 3 action cards in a row (stack mobile):
>
> Card 1 — "Try More Outfits"
> Hanger icon gold. "You have 5 tries left today." DM Sans 14px muted. "✨ Try On Now →" gold button → tryon.html. Background surface.
>
> Card 2 — "Share Your Look"
> Share icon gold. "Show your friends what you're wearing." DM Sans 14px muted. Row of share buttons: WhatsApp (green), Instagram (gradient), Copy link (dark). **Clicking WhatsApp:** opens `https://wa.me/?text=I just ordered this outfit from DRIP! Try it on yourself: [URL]` — pre-filled share text.
>
> Card 3 — "Write a Review" (available after delivery — locked state with lock icon and "Available after delivery" muted text overlay)
> Star rating icon gold. Greyed out. "Leave a review after your order arrives." Subtle dashed border `#2A2A35`.
>
> ---
>
> ## "YOU MIGHT ALSO LIKE" — OUTFIT RECOMMENDATIONS
> Background `#0A0A0F`. Heading "Complete Your Wardrobe" Cormorant 32px. Subtext "Pairs perfectly with what you just bought." muted.
>
> 4 outfit cards (same as Explore page cards). Add to cart button on each (instead of / in addition to Try On). Clicking "Add to Bag": adds to `drip_cart` localStorage + shows cart drawer + toast "Added to bag!".
>
> ---
>
> ## EMAIL CONFIRMATION BANNER
> Thin banner: background `rgba(74,175,130,0.1)`, border-top border-bottom `#4CAF82/30`. py-4. Text center: "📧 Order confirmation sent to rahul@gmail.com" DM Sans 14px muted. "Resend email" gold link right → toast "Email resent ✓".
>
> ---
>
> ## JS BEHAVIORS
> 1. Page load: read last order from drip_orders localStorage → populate all order details
> 2. Animated checkmark sequence (scale + stroke draw) on page load
> 3. Staggered fade-up animations for each section (IntersectionObserver or sequential setTimeout)
> 4. Copy order ID → clipboard + flash gold
> 5. SMS toggle → toast
> 6. Share buttons (WhatsApp pre-filled link, Copy link)
> 7. "Add to Bag" on recommendation cards → push to drip_cart → open cart drawer + toast
> 8. Resend email → toast
> 9. If drip_orders is empty (user navigated directly) → show friendly "No recent order found" message with "Continue Shopping →" button

---

---

# PROMPT 13 — MY ORDERS PAGE
**File: orders.html**

---

> Build a complete, production-ready, fully responsive **My Orders page** for DRIP in a single HTML file. All data from localStorage `drip_orders`. Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This page is typically accessed from the user dashboard or account dropdown. Shows all past and active orders.
>
> ---
>
> ## NAVBAR — same as all pages (with user avatar dropdown)
>
> ---
>
> ## PAGE HEADER
> Background `#13131A`. py-12. Max-w-7xl centered px-6.
> Breadcrumb: "Account / My Orders" muted 12px.
> "My Orders" Cormorant Garamond 40px. Below: "Showing 3 orders" muted DM Sans 14px.
>
> Right: Search orders input (dark surface, gold focus, rounded-full, placeholder "Search by order ID or product..."). Filter dropdown: "All Orders" / "Active" / "Delivered" / "Cancelled" — styled custom select.
>
> ---
>
> ## PRE-POPULATED DEMO ORDERS
> Generate these 3 orders in localStorage `drip_orders` on first load if empty:
>
> ```
> Order 1: #DRP-2025-08471 | Feb 23, 2025 | Status: "Being Packed" | Items: 3 | Total: ₹4,597 | EDD: Feb 27
> Order 2: #DRP-2025-07234 | Feb 10, 2025 | Status: "Delivered" | Items: 1 | Total: ₹2,499 | Delivered: Feb 15
> Order 3: #DRP-2025-05891 | Jan 28, 2025 | Status: "Cancelled" | Items: 2 | Total: ₹3,298 | Cancelled: Jan 29
> ```
>
> ---
>
> ## ORDER CARDS LIST (vertical stack, gap-6)
>
> Each order is an expandable card:
>
> ### COLLAPSED STATE (default)
>
> Card: `#13131A` border `#2A2A35` rounded-2xl p-6. Hover: border gold subtle.
>
> **Top row:**
> - Left: Order ID in DM Sans 14px gold + Date muted 13px below
> - Center: Status badge pill:
>   - "Being Packed" → gold border gold text + pulsing dot animation
>   - "Shipped" → blue `#5A8AB0` border + text
>   - "Out for Delivery" → orange `#E2924C` border + text
>   - "Delivered" → green border + text + ✓
>   - "Cancelled" → red border + muted text
>   - "Return Requested" → orange border
> - Right: Total "₹4,597" DM Sans 16px gold + "3 items" muted 12px below
>
> **Second row (items preview):** Horizontal strip of item images (60px circles, overlapping slightly like a stack — 3 shown, if more: "+N more" circle). Below images: first item name muted 12px truncated.
>
> **Bottom row (action buttons — context-sensitive per status):**
>
> For "Being Packed" / "Shipped":
> - "Track Order" gold outlined pill → expands card to tracking view
> - "Cancel Order" muted outlined pill → opens confirm modal
>
> For "Delivered":
> - "View Details" gold outlined pill → expands card
> - "Buy Again" gold filled pill → adds all items to cart + toast
> - "Return / Exchange" muted outlined pill → opens return flow modal
>
> For "Cancelled":
> - "View Details" muted outlined pill → expands card
> - "Reorder" gold outlined pill → adds items back to cart + toast
>
> **Expand arrow** far right (chevron, rotates 180° when expanded).
>
> ---
>
> ### EXPANDED STATE (clicking anywhere on card toggles — smooth height animation using max-height transition)
>
> **Order items list:** Full details for each item (same as order-success.html items list). Image + name + brand + size + color + qty + price.
>
> **Delivery timeline:** Same vertical timeline as order-success.html, but stages filled per actual order status.
>
> **Delivery address block:** "Shipped to:" label + address muted.
>
> **Payment block:** "Paid via UPI · ₹X,XXX" with green checkmark.
>
> **Invoice row:** "📄 Download Invoice" muted link — clicking: generates a simple text-based invoice blob and triggers download as `DRIP-Invoice-{orderId}.txt`.
>
> ---
>
> ## CANCEL ORDER MODAL
>
> Triggered by "Cancel Order" button. Centered modal (dark overlay, surface card).
>
> Headline: "Cancel this order?" Cormorant 28px.
>
> Order summary (compact): order ID + items + total.
>
> "Reason for cancellation" — required dropdown: Ordered by mistake / Wrong size/color / Found better price / Delivery too slow / Other.
>
> "Additional notes" textarea optional.
>
> Refund info: "💳 ₹X,XXX will be refunded to your original payment method within 5–7 business days." muted 13px in green box.
>
> Buttons: "Yes, Cancel Order" (red filled) + "Keep My Order" (outlined muted). On confirm: order status updates to "Cancelled" in localStorage, card re-renders with cancelled status, toast "Order cancelled. Refund initiated." red.
>
> ---
>
> ## RETURN / EXCHANGE MODAL
>
> Headline: "Return or Exchange?" Cormorant 28px.
>
> Two large option cards: "Return for Refund" (red tint border) and "Exchange for Different Size" (gold border). Clicking selects one.
>
> If Return: show items checklist (which items to return), reason dropdown, "Submit Return Request" gold button.
>
> If Exchange: show size selector for each item, "Request Exchange" gold button.
>
> On submit: toast "Return request submitted! Our team will contact you within 24 hours." + status updates to "Return Requested".
>
> ---
>
> ## EMPTY STATE
> Bag icon gold 64px. "No orders yet." Cormorant 32px. Muted subtext "When you place your first order, it will appear here." "Start Shopping →" gold button → explore.html. "✨ Try On Outfits →" outlined gold → tryon.html.
>
> ---
>
> ## JS BEHAVIORS
> 1. Load orders from localStorage on page load (pre-populate demos if empty)
> 2. Card expand/collapse with max-height CSS transition (smooth accordion)
> 3. Status filter dropdown → show/hide cards by status (JS)
> 4. Search input → filter cards by order ID or item name (live)
> 5. Cancel order modal: open, reason required validation, confirm → update localStorage status → re-render card
> 6. Return modal: open, mode selection (return/exchange), submit → update status + toast
> 7. Buy Again / Reorder → push items to drip_cart → open cart drawer + toast "X items added to bag"
> 8. Expand arrow chevron rotation (180deg CSS transform transition)
> 9. Invoice download: generate text blob → trigger download
> 10. Redirect to auth.html if drip_user is null (not logged in)

---

---

# NAVIGATION MAP UPDATE (add to existing map)

```
cart.html
  → explore.html (Continue Shopping)
  → tryon.html (Try On More)
  → checkout.html (Proceed to Checkout)
  → outfit.html (item name click)

checkout.html
  → cart.html (Edit Bag)
  → order-success.html (after payment simulation)

order-success.html
  → tryon.html (Try More Outfits CTA)
  → explore.html (recommendation cards)
  → orders.html (View All Orders link)

orders.html
  → explore.html (empty state)
  → tryon.html (empty state)
  → cart.html (Buy Again → add to cart → open drawer)
```

# CART DRAWER NOTE
The floating cart drawer (from cart.html prompt) should be injected into ALL pages:
explore.html, outfit.html, tryon.html, blog-post.html, dashboard.html.
It is triggered by the cart icon in the navbar on every page.
Shared JS function: `openCartDrawer()` / `closeCartDrawer()`.
Cart count badge on navbar icon always reflects `JSON.parse(localStorage.getItem('drip_cart') || '[]').length`.
