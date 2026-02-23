# DRIP — Complete SaaS MVP
# All Gemini Prompts: Every Page, Every Element, Every Interaction

---

## DESIGN SYSTEM (Include at top of EVERY prompt)

```
DESIGN SYSTEM — Copy this into every prompt verbatim:

Brand: DRIP — AI-powered fashion virtual try-on web app for Indian audience.
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

Fonts (Google Fonts — import in <head>):
- Cormorant Garamond (weights 300,400,500,600) — all headings, display text
- DM Sans (weights 300,400,500) — all body, UI, labels

font-display = Cormorant Garamond
font-sans = DM Sans

Rules:
- Every button has default / hover (lift + shadow) / active (press) states
- Cards: hover lifts 4px (translateY -4px), border transitions to gold
- All color transitions: duration-200 transition-colors
- All transform transitions: duration-300 transition-all
- Skeleton loaders: animated shimmer using @keyframes shimmer with gradient
- Smooth scroll on <html>
- No lorem ipsum — use real copy
- Max content width: max-w-7xl mx-auto
- Generous padding: py-24 desktop, py-16 mobile
- Mobile first, fully responsive at 375px and 1440px
```

---

## PAGE BUILD ORDER

| # | File Name | Page |
|---|-----------|------|
| 1 | landing.html | ✅ DONE — Landing Page |
| 2 | explore.html | Explore / Browse Outfits |
| 3 | outfit.html | Single Outfit Detail Page |
| 4 | tryon.html | Try-On Studio (Core Product) |
| 5 | blog-index.html | Blog Index |
| 6 | blog-post.html | Blog Post |
| 7 | auth.html | Login / Signup |
| 8 | dashboard.html | User Dashboard |
| 9 | components.html | All Popups, Modals, Toasts |

---

---

# PROMPT 2 — EXPLORE PAGE
**File: explore.html**

---

> Build a complete, production-ready, fully responsive **Explore / Browse Outfits page** for DRIP in a single HTML file using HTML5, Tailwind CSS (via CDN), and vanilla JavaScript.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## NAVBAR (same across all pages — reuse exactly)
> Sticky top navbar. Logo "DRIP" left in Cormorant Garamond gold tracking-widest. Center: Explore, Blog, About links (muted, gold on hover, underline slide animation). Right: "Try It Free" pill button (gold border, fills on hover) + Login text link (muted). Mobile: hamburger → full-screen overlay drawer with all links + "Try It Free" CTA gold filled button at bottom. Navbar transparent initially, blurred dark surface on scroll (JS scroll listener).
>
> ---
>
> ## PAGE HEADER
> Dark surface background `#13131A`. Padding py-16. Max-w-7xl centered.
> Left side: Breadcrumb "Home / Explore" in muted 12px DM Sans. Below: Page title "Explore Outfits" in Cormorant Garamond 48px. Below: Active filter chips strip — when filters are active, show chips like "Men's Ethnic ×" "Wedding ×" in gold border pill with × to remove. If no filters: show "Showing all 970+ outfits". Right side (desktop): Sort dropdown — styled custom select, dark surface, gold border on focus, options: Trending, Newest, Price: Low to High, Price: High to Low, Most Tried.
>
> ---
>
> ## LAYOUT — Two column: Filter sidebar left + Outfit grid right
>
> ### FILTER SIDEBAR (desktop: fixed 280px left column, mobile: hidden behind bottom sheet)
>
> Sidebar background: `#13131A`. Border right: `#2A2A35`. Sticky top-24. Height: calc(100vh - 6rem). Overflow-y auto. Padding p-6.
>
> **Filter sections (each collapsible — click section title toggles open/close with chevron rotate animation):**
>
> Section 1 — CATEGORY (default open)
> Checkboxes styled custom: hidden real checkbox, custom square `#2A2A35` bg, gold checkmark when checked, gold border when checked. Options:
> - Men's Ethnic Wear (240)
> - Western Casuals (380)
> - Women's Sarees & Lehengas (190)
> - Plus-Size Fashion (160)
>
> Section 2 — OCCASION (default open)
> Same checkbox style. Options: Wedding, Casual, Office, Festival, Date Night, Party
>
> Section 3 — COLOR (default open)
> Visual color swatches — 12 circular swatches in a 6-column grid. Colors: Black, White, Navy, Red, Green, Yellow, Pink, Orange, Purple, Brown, Grey, Beige. Click toggles selected state: gold ring around swatch. Multiple selectable.
>
> Section 4 — PRICE RANGE (default open)
> Custom dual-handle range slider. Track color `#2A2A35`, filled portion gold. Handles: white circle with gold border. Below slider: two price display boxes showing "₹0" and "₹5,000+" updating live as slider moves. Style with pure CSS + JS.
>
> Section 5 — BRAND (default collapsed)
> Checkbox list: Manyavar, FabIndia, W for Woman, Biba, H&M India, Zara India, Only, Vero Moda, Jack & Jones, Being Human.
>
> **Bottom of sidebar:** "Clear All Filters" link in muted, underline on hover. "Apply Filters" button (gold filled, full width, rounded-xl) — on mobile this closes the bottom sheet and applies.
>
> ---
>
> ### MOBILE FILTER TRIGGER
> Fixed bottom bar on mobile (hidden on desktop): Full width dark surface bar with "Filters" button left (filter icon + text) and Sort dropdown right. Tapping Filters opens a bottom sheet drawer sliding up from bottom with full filter sidebar content inside. Bottom sheet has drag handle at top, "Done" button at bottom. Background overlay darkens page behind it.
>
> ---
>
> ### OUTFIT GRID (right column, takes remaining width)
>
> Responsive grid: 3 columns desktop (lg:grid-cols-3), 2 columns tablet (md:grid-cols-2), 2 columns mobile (grid-cols-2). Gap: gap-4 mobile, gap-6 desktop.
>
> **Each outfit card:**
> - Background: `#13131A`
> - Border: `#2A2A35`, rounded-2xl, overflow-hidden
> - Hover: translateY -4px, border color transitions to `#C9A84C`, shadow deepens
> - Transition: all 300ms
>
> Card structure top to bottom:
> 1. Image container (aspect-ratio 3/4, overflow hidden): outfit image `https://picsum.photos/300/400?random=N` with object-cover. On hover: image scales to 1.05 (transition 700ms). Top-left: Category pill badge (gold border, gold text, 10px, uppercase). Top-right: Heart icon button (muted color, fills red on click — toggle saved state with JS, localStorage key `drip_saved`).
> 2. Card body (p-4):
>    - Brand name: DM Sans 11px muted uppercase tracking-wide
>    - Outfit name: Cormorant Garamond 18px primary, line-clamp-1
>    - Price: DM Sans 16px gold font-medium. If has discount: show original price struck through in muted smaller text next to it.
>    - Below price: Two buttons side by side:
>      - "Try On" button: gold border, gold text, rounded-full, text-xs px-3 py-1.5, flex-1. Hover: fills gold, text dark. **Clicking this navigates to tryon.html?outfit=N**
>      - "Buy Now" button: dark border muted text, rounded-full, text-xs px-3 py-1.5, flex-1. Hover: border gold, text gold. **Clicking opens affiliate URL in new tab**
>    - Bottom: "X people tried today" — muted 11px DM Sans with small fire emoji 🔥 if >50 people.
>
> **Show 24 outfit cards total** using picsum randoms 40–63. Vary the category pills, brands, prices (₹499–₹4,999), outfit names realistically (e.g., "Classic White Kurta", "Slim Fit Chinos", "Banarasi Silk Saree", "Oversized Graphic Tee").
>
> **Pagination / Load More:**
> Below the grid: centered "Load More Outfits" button (gold outlined, pill, px-10 py-3). On click: adds 8 more skeleton cards (shimmer animation) for 1.5 seconds, then replaces with 8 more picsum images (randoms 64–71). Show "Showing 32 of 970+ outfits" text in muted below button. After loading once, button text changes to "Load More (938 remaining)".
>
> ---
>
> ## EMPTY STATE (shown when filters return 0 results — trigger with a JS demo button)
> Centered in the grid area: Large muted icon (search with X), headline "No outfits found" in Cormorant Garamond, subtext "Try adjusting your filters or browse all styles." in muted DM Sans. "Clear Filters" gold button below.
>
> ---
>
> ## SKELETON LOADER STATE
> On initial page load, show 12 skeleton cards for 1 second before "loading" real cards. Skeleton card: same dimensions as outfit card, all elements replaced with shimmer rectangles (animated gradient from `#13131A` to `#2A2A35` to `#13131A`). After 1 second, fade in real cards.
>
> ---
>
> ## FOOTER (same across all pages — reuse exactly from landing.html)
> Dark bg, border-top. Logo + tagline left. Links grid center. Made in India + socials right. Copyright bottom center.
>
> ---
>
> ## JS BEHAVIORS
> 1. Navbar scroll effect (transparent → blurred surface)
> 2. Mobile hamburger menu open/close
> 3. Filter sidebar sections collapse/expand with chevron rotation
> 4. Color swatch multi-select toggle
> 5. Price range dual slider (update display values live)
> 6. Heart/save toggle (add/remove from localStorage array `drip_saved`)
> 7. Mobile filter bottom sheet open/close with overlay
> 8. Load More button: skeleton → real cards fade in
> 9. Active filter chip removal (click × removes that filter, updates result count)
> 10. Sort dropdown: reorders cards visually (by price low/high using card data attributes)
>
> Give each outfit card a `data-price`, `data-category`, `data-occasion` attribute for JS filtering/sorting to work.

---

---

# PROMPT 3 — SINGLE OUTFIT PAGE
**File: outfit.html**

---

> Build a complete, production-ready, fully responsive **Single Outfit Detail Page** for DRIP in a single HTML file using HTML5, Tailwind CSS (via CDN), and vanilla JavaScript.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## NAVBAR — same as all pages (see Prompt 2 navbar spec)
>
> ---
>
> ## BREADCRUMB BAR
> Full width, py-4, px-6 md:px-12. Background brandBg. Text: "Home / Explore / Men's Ethnic Wear / Classic Bandhgala Kurta Set" in muted 12px DM Sans. Each segment except last is a link (hover gold). Last segment (current page) in primary color.
>
> ---
>
> ## MAIN PRODUCT SECTION
> Two-column layout (desktop): Left 45% product images, Right 55% product details. Stacked on mobile.
>
> ### LEFT COLUMN — Product Images
>
> **Primary image display:** Large rounded-2xl image container, aspect-ratio 4/5. Image: `https://picsum.photos/500/625?random=80`. Object-cover. Border `#2A2A35`.
>
> Top-right corner of image: "847 people tried this" badge — dark surface/80 backdrop blur, gold text, DM Sans 12px, rounded-full px-3 py-1. Positioned absolute.
>
> Top-left: "New Arrival" tag (or "Trending" or "Sale") — gold background, dark text, 10px uppercase, rounded-br-xl, absolute top-0 left-0 px-3 py-1.5.
>
> **Thumbnail strip below primary image:** 4 thumbnails horizontal, each 80x100px rounded-xl border `#2A2A35`. Active thumbnail has gold border. Clicking thumbnail updates the primary image (JS). Use picsum randoms 80–83.
>
> **"View on Model" toggle:** Below thumbnails, a toggle switch (pill shape, dark bg, gold active state). Left label: "Product Only", Right label: "On Model". When toggled to "On Model": primary image switches to a different picsum image (random 90) with a smooth crossfade transition (opacity 0 → 1, 300ms).
>
> ---
>
> ### RIGHT COLUMN — Product Details
>
> **Brand name:** DM Sans 12px muted uppercase tracking-widest. Clickable (mock link).
>
> **Outfit name:** Cormorant Garamond 36px desktop / 28px mobile, primary color, font-weight 400. "Classic Bandhgala Kurta Set"
>
> **Rating row:** 5 gold stars (SVG), "4.8" in DM Sans, "(234 reviews)" in muted underline. Inline flex gap-2.
>
> **Price block:**
> - Main price: "₹2,499" — DM Sans 28px gold font-medium
> - Original: "₹3,999" struck through muted 18px
> - Savings badge: "Save ₹1,500 (37% off)" — green text, green border pill, 12px
>
> **Divider line** `#2A2A35`
>
> **Size selector:** Label "Select Size" DM Sans 13px muted uppercase. Size buttons in a row: XS / S / M / L / XL / XXL — each a square rounded-lg border `#2A2A35`, DM Sans 13px. Active/selected: gold border + gold text. Hover: gold border. One size pre-selected (M). "Size Guide" link in gold 12px to the right.
>
> **Color selector:** Label "Color" same style. 4 circular color swatches (black, ivory, navy, olive). Selected has gold ring. Clicking changes the primary image to a different picsum random.
>
> **Quantity selector:** Label "Quantity". Minus button — number display — Plus button. Styled: dark surface, gold border, rounded-xl. Number starts at 1, min 1 max 10.
>
> **Primary CTA: "✨ Try This On Me"** — Full width, gold filled, rounded-2xl, py-4, Cormorant Garamond 20px, font-medium. Hover: scale 1.02, gold glow shadow. **Clicking this navigates to tryon.html with outfit ID as URL param: tryon.html?outfit=80**
>
> **Secondary CTA: "Buy Now — ₹2,499"** — Full width outlined gold border, same height. Hover: fills gold. **Clicking opens affiliate link in new tab.**
>
> **Tertiary: Heart + "Save to Wishlist"** — text button, muted color, heart icon left. Clicking: heart fills red, text changes to "Saved ✓" in green. Toggle on/off (localStorage).
>
> **Delivery info block:** Small section with 3 rows, icon + text:
> - 🚚 "Free delivery on orders above ₹999"
> - 🔄 "Easy 7-day returns"
> - ✅ "Genuine product from Manyavar"
> Each row: icon gold, text muted 13px DM Sans.
>
> **Share row:** "Share:" label + 3 icon buttons (WhatsApp green, Instagram gradient, Copy Link). Clicking Copy Link: icon turns gold checkmark, small toast "Link copied!" appears bottom-right for 2 seconds.
>
> ---
>
> ## TABS SECTION (below main product, full width)
> 3 tabs: "Description" | "Details & Care" | "Reviews (234)". Tab bar: border-bottom `#2A2A35`. Active tab: gold underline, primary text. Inactive: muted. Tab switching: JS show/hide content panels with fade transition.
>
> **Description tab:** 3 paragraphs of realistic outfit description text. Mentions fabric (pure cotton), occasion (festive/wedding), fit (regular fit), origin (Jaipur, Rajasthan). DM Sans 14px muted, line-height relaxed.
>
> **Details & Care tab:** Two columns: left "Product Details" table (Brand, SKU, Fabric, Fit, Occasion, Country of Origin) — table with alternating row backgrounds `#13131A` / `#0A0A0F`. Right: "Care Instructions" with 4 bullet points (icons + text): Machine wash cold, Do not bleach, Iron on medium heat, Dry in shade.
>
> **Reviews tab:** 3 review cards. Each: Star rating (gold SVGs), reviewer name (initials avatar — gold circle, dark text), review date muted, review text. Bottom of reviews: "Load More Reviews" muted link.
>
> ---
>
> ## SECTION: "Style This With" (cross-sell)
> Background `#13131A`. Heading "Complete the Look" — Cormorant Garamond 32px, section label "PAIRS WELL WITH" in gold uppercase small above. 3 small outfit cards (same card design as Explore page but slightly smaller). Each has "Try With This" button instead of "Try On".
>
> ---
>
> ## SECTION: "From Our Style Blog"
> Background `#0A0A0F`. Heading "See It Styled" Cormorant Garamond 32px. 2 blog post cards side by side (stack mobile). Each: image, category pill, title, "Read & Try →" link in gold. These are internal links pointing to blog-post.html.
>
> ---
>
> ## SECTION: "More from Manyavar"
> Background `#13131A`. Heading "More from this Brand". 4 outfit cards in a horizontal scroll strip on mobile, 4-column grid on desktop. Same card design as Explore.
>
> ---
>
> ## RECENTLY VIEWED (bottom, before footer)
> Background `#0A0A0F`. "Recently Viewed" heading muted DM Sans 12px uppercase. Horizontally scrollable strip of 4 outfit cards (smaller version). On mobile: scroll snap. Populated from localStorage `drip_recent` array (JS: on page load, add this outfit to array, show previous ones).
>
> ---
>
> ## STICKY MOBILE BOTTOM BAR
> On mobile only (hidden md:hidden). Fixed bottom-0. Full width. Dark surface, border-top `#2A2A35`. Two buttons side by side: "✨ Try On" (gold filled flex-1) and "Buy Now" (outlined gold flex-1). py-3. Safe area bottom padding for iPhone notch: `padding-bottom: env(safe-area-inset-bottom)`.
>
> ---
>
> ## JS BEHAVIORS
> 1. Thumbnail click → update primary image with crossfade
> 2. View on Model toggle → swap image with crossfade
> 3. Color swatch click → swap image + update selected state
> 4. Size button selection → toggle active gold state
> 5. Quantity +/- buttons (min 1, max 10)
> 6. Heart toggle → localStorage save/unsave
> 7. Copy link → clipboard API + toast notification
> 8. Tab switching (Description / Details / Reviews)
> 9. Add to recently viewed → localStorage
> 10. Sticky bottom bar scrolls in from below on mobile after 200px scroll

---

---

# PROMPT 4 — TRY-ON STUDIO
**File: tryon.html**

---

> Build a complete, production-ready, fully responsive **Try-On Studio page** for DRIP — this is the core product page. Single HTML file, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> **This page is an APP, not a content page. UI is minimal — maximum focus on the try-on experience. No footer on this page. Minimal navbar.**
>
> ---
>
> ## MINIMAL NAVBAR
> Same logo "DRIP" left gold. Right side only: Try count badge "2 / 3 tries used" (muted pill, gold number) + "Save Look" button (gold outlined, pill) + user avatar circle (if logged in — show initials, else show "Login" text link). No center links. No hamburger. Background: always blurred dark surface (not transparent). Border-bottom `#2A2A35`.
>
> ---
>
> ## PAGE LAYOUT
> Full viewport height minus navbar. Two-panel layout desktop (left 40% / right 60%). Single column stacked on mobile.
>
> ---
>
> ## LEFT PANEL — "Your Photo"
>
> Background `#13131A`. Border-right `#2A2A35` (desktop only). Full height. Flex column.
>
> **Panel header:** "Your Photo" label DM Sans 13px muted uppercase tracking-wide. Padding px-6 pt-6.
>
> ---
>
> ### STATE A — Empty (no photo uploaded yet)
>
> Centered upload zone, fills most of panel height. Dashed border `#2A2A35` rounded-2xl. Flex column center items.
>
> Content inside upload zone:
> - Large upload icon SVG (gold, 48px)
> - Headline: "Upload Your Photo" — Cormorant Garamond 24px primary
> - Subtext: "Front-facing, good lighting, plain background gives best results." — muted 13px DM Sans, text-center, max-w-xs
> - Two buttons stacked: "📁 Upload from Gallery" (gold filled, full width, rounded-xl) and "📸 Use Camera" (outlined gold, full width, rounded-xl). Gap between them: gap-3.
> - Small privacy note below: lock icon + "Your photo is never stored. Auto-deleted after 24 hours." — muted 11px DM Sans
>
> Drag and drop support: When user drags a file over the zone, border turns gold, background shifts to `rgba(201,168,76,0.05)`. "Drop your photo here" text appears.
>
> **Hidden `<input type="file" accept="image/*">` triggered by Upload button click.**
>
> Camera button: triggers `getUserMedia` — opens camera stream in a modal overlay (see camera modal spec below).
>
> ---
>
> ### STATE B — Photo loaded
>
> Photo fills the panel. Object-cover, rounded-2xl inside panel with padding p-4. Photo has subtle gold border.
>
> Top of panel (absolute overlay): "Change Photo" button — small, dark surface/80 backdrop, muted text, rounded-full, top-right of photo.
>
> Bottom of panel (absolute overlay): Try count indicator bar — "3 free tries · 2 used · 1 remaining". Gold progress bar (1/3 filled). Background dark surface/80 backdrop blur. Positioned bottom-4 left-4 right-4.
>
> ---
>
> ## RIGHT PANEL — "Outfit Studio"
>
> Background `#0A0A0F`. Full height. Flex column.
>
> **Panel header row:** "Choose an Outfit" label left. Filter pills scrollable horizontal right: "All" "Ethnic" "Casual" "Festive" "Office" — pill buttons, inactive: muted border muted text, active: gold border gold text. Padding px-6 pt-6. Gap gap-2.
>
> ---
>
> ### OUTFIT STRIP (horizontally scrollable, no scrollbar)
>
> Below header. Height: 130px. Padding px-6. Overflow-x auto, no scrollbar (no-scrollbar class). Flex row gap-3.
>
> Each outfit thumbnail card: width 90px, height 110px, rounded-xl, overflow-hidden, border `#2A2A35`, flex-shrink-0, cursor-pointer. Image object-cover. Price below image: DM Sans 10px gold.
>
> Active/selected state: gold border 2px, slight scale-105.
>
> On click: triggers try-on generation (STATE B → C in result area below).
>
> Show 12 outfit thumbnails (picsum 40–51). Pre-select outfit 40 if URL param `?outfit=40` is present.
>
> ---
>
> ### RESULT AREA (fills remaining height of right panel)
>
> ---
>
> #### RESULT STATE 1 — No outfit selected / no photo
> Large centered empty state. Icon: hanger SVG (gold 64px). Text: "Upload your photo and select an outfit to see the magic ✨" — Cormorant Garamond 22px primary text-center. Subtext muted 14px: "Your AI-generated try-on will appear here."
>
> ---
>
> #### RESULT STATE 2 — Generating (show after outfit selected + photo uploaded)
>
> Shimmer skeleton in the shape of a person/outfit — a centered rounded-2xl rectangle (matching photo aspect ratio) with the shimmer animation (gradient `#13131A → #2A2A35 → #13131A` animating left to right, 1.5s infinite). Inside skeleton: subtle centered text "Styling you..." in muted 13px with a blinking dot animation. Below skeleton: thin gold animated progress bar (0% → 100% over 4 seconds). This state lasts 3–5 seconds (simulate with setTimeout in JS).
>
> ---
>
> #### RESULT STATE 3 — Result ready
>
> The try-on result image appears with a smooth fade-in (opacity 0 → 1, scale 0.97 → 1.0, 400ms). Use a picsum image (random 100) as the mock result. Rounded-2xl, max height fills the panel.
>
> **Below result image — Action bar (3 buttons in a row):**
>
> Button 1 — "❤️ Love it — Buy Now" (gold filled, flex-1, rounded-xl py-3). Clicking: opens affiliate link in new tab + shows toast "Opening store..." bottom right.
>
> Button 2 — "🔖 Save This Look" (outlined gold, flex-1, rounded-xl py-3). Clicking: if logged in → saves to dashboard (localStorage), shows toast "Look saved! ✓" in green. If not logged in → triggers Save Modal (see below).
>
> Button 3 — "↗ Share" (dark border muted text, flex-1, rounded-xl py-3). Clicking: opens Share Modal (see below).
>
> **Above result image — top-right overlay:** "Try Another" text button (muted, small) — clicking resets result area to STATE 1 (keeps photo, clears outfit selection).
>
> ---
>
> #### RESULT STATE 4 — Try limit reached (3/3 used)
>
> After third try completes and user tries to select a 4th outfit: a soft overlay appears over the result panel (dark `#0A0A0F` at 90% opacity, backdrop blur), centered content:
> - Lock icon (gold, 48px)
> - Headline: "You've used your 3 free tries today." — Cormorant Garamond 28px
> - Subtext: "Sign up free to get 5 tries daily — forever." — muted DM Sans
> - "Sign Up Free →" button (gold filled, large, rounded-full)
> - "Come Back Tomorrow" link below (muted, underline)
>
> ---
>
> ## CAMERA MODAL
>
> Triggered by "Use Camera" button. Full-screen overlay (`z-50`). Dark background `#0A0A0F`. Centered camera viewfinder: rounded-2xl border gold. Below viewfinder: row of 3 buttons: "← Back" (muted outlined), large circular "Capture" button (white filled with gold ring — classic camera button), "🔄 Flip" (muted outlined). After capture: show preview of captured frame with "Use This Photo" (gold) and "Retake" (outlined) buttons.
>
> ---
>
> ## SAVE MODAL (triggered when not logged in + taps Save)
>
> Centered modal with dark overlay. Modal card: `#13131A` border `#2A2A35` rounded-2xl p-8 max-w-sm. Close × top-right.
> - Small preview of the try-on result (80px thumb) top center
> - Headline: "Save your look" Cormorant Garamond 28px
> - Subtext: "Create a free account to save and revisit all your try-on results."
> - "Continue with Google" button (white bg, dark text, Google SVG icon left, rounded-xl full-width)
> - Divider "or"
> - Email input (dark surface, gold focus border, placeholder "your@email.com") + "Send Magic Link" button (gold filled full-width)
> - Small text below: "Already have an account? Log in"
>
> ---
>
> ## SHARE MODAL
>
> Same modal shell (dark overlay, centered card). Close ×.
> - Try-on result image preview (rounded-xl, 200px tall, centered)
> - Headline "Share your look 🔥" Cormorant Garamond 24px
> - Subtext: "Let your friends see your new style"
> - Share buttons in 2x2 grid: WhatsApp (green bg), Instagram (gradient bg), Copy Link (dark surface), Download Image (dark surface). Each: icon + label, rounded-xl, py-3.
> - Clicking Copy Link: button turns gold "Copied ✓", small toast appears.
> - Clicking Download: simulates download (creates canvas blob of the result image and triggers download).
> - Below grid: small muted text "Shared looks include a DRIP watermark 💧"
>
> ---
>
> ## SIZE GUIDE MODAL (accessible from outfit strip — small "?" icon on each outfit)
>
> Centered modal. Headline "Size Guide" Cormorant Garamond. Table with rows: Size / Chest / Waist / Hip. Styled dark table alternating rows. "Find My Size" CTA button at bottom (gold). Close × top-right.
>
> ---
>
> ## JS BEHAVIORS (full list)
> 1. File upload → read as DataURL → display in left panel → switch to STATE B
> 2. Drag and drop photo onto upload zone
> 3. Camera modal open → getUserMedia stream → capture frame → use as photo
> 4. Outfit strip filter pills → filter visible outfit cards
> 5. Outfit thumbnail click → if photo loaded: trigger generation sequence (STATE 2 → 3 after timeout). If no photo: flash upload zone border gold + shake animation with tooltip "Upload your photo first!"
> 6. Try count tracker (localStorage `drip_tries` with date key — reset daily)
> 7. On 3rd try complete: result shows normally. On 4th attempt: show STATE 4 overlay
> 8. Save button → check login state (localStorage `drip_user`) → save or show modal
> 9. Share modal open/close
> 10. Camera modal open/close/capture
> 11. Toast notification system (bottom-right, slides in, auto-dismiss 3s, stacks multiple)
> 12. URL param reading: `?outfit=N` → pre-select that outfit in strip
> 13. "Try Another" button → reset to STATE 1

---

---

# PROMPT 5 — BLOG INDEX
**File: blog-index.html**

---

> Build a complete, production-ready, fully responsive **Blog Index page** for DRIP in a single HTML file using HTML5, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## NAVBAR — same as all pages
>
> ---
>
> ## HERO / PAGE HEADER
> Background `#13131A`. Border-bottom `#2A2A35`. py-20. Max-w-7xl centered. Text center.
> - Label: "STYLE GUIDES & FASHION TIPS" gold uppercase tracking-widest 11px
> - Headline: "Dress better. Every day." Cormorant Garamond 56px desktop / 40px mobile
> - Subtext: "Expert style guides, outfit ideas, and fashion tips curated for the Indian wardrobe." muted DM Sans 16px. Max-w-xl mx-auto.
> - Search bar below: Wide search input (dark surface border `#2A2A35`, gold focus border, rounded-full, px-6 py-3, placeholder "Search articles... e.g. kurta for wedding") with search icon inside right side. On focus: subtle gold glow. Clicking search icon or pressing Enter: filters visible posts by title (JS).
>
> ---
>
> ## FEATURED POST (hero blog card)
>
> Full-width card below header. Max-w-7xl mx-auto px-6. Two-column layout: left 55% image, right 45% content. Mobile: stacked (image top).
>
> Left: Large image `https://picsum.photos/700/450?random=50` rounded-2xl object-cover. "Featured" gold badge absolute top-4 left-4.
>
> Right: Padding pl-8 (desktop). Category pill "Wedding Season" gold border. Title: "The Complete Guide to Men's Wedding Outfits in India 2025" — Cormorant Garamond 36px primary. Excerpt: 2 sentences. Muted DM Sans 15px. Author row: initials avatar (gold circle, dark text) + "By DRIP Editorial" + "·" + "8 min read" + date "Dec 2024". "Read the Full Guide →" gold link with arrow. Below: row of 4 outfit thumbnail cards (80px square, rounded-lg, gold border) labeled "4 outfits to try from this article" — each has a small "Try On" button on hover.
>
> ---
>
> ## CATEGORY FILTER TABS
> Full width. Border-bottom `#2A2A35`. Horizontally scrollable on mobile (no scrollbar). Tabs: All / Men's Style / Women's Style / Ethnic Wear / Western / Seasonal / Sustainability. Active tab: gold underline + gold text. Inactive: muted. Clicking tab: filters post grid (JS data attributes).
>
> ---
>
> ## MAIN CONTENT — Two column: Post grid left + Sidebar right
>
> Max-w-7xl mx-auto px-6. Grid: left takes 65% desktop, sidebar 35%. Full width stacked mobile (sidebar goes below posts on mobile).
>
> ### POST GRID (left)
>
> Regular card grid: 2 columns desktop, 1 column mobile. Gap-8.
>
> Show 6 blog post cards. Each card:
> - Image top: `https://picsum.photos/400/240?random=N` full-width, rounded-t-2xl, 220px height, object-cover. Hover: image scales 1.03 (overflow hidden on card). Category pill badge absolute top-4 left-4.
> - Card body: `#13131A` border `#2A2A35` border (no top border — image is flush), rounded-b-2xl, p-6.
> - Category pill (again below image — color coded: Wedding=gold, Casual=green, Office=blue-ish `#5A8AB0`, Festival=orange `#E2924C`).
> - Title: Cormorant Garamond 22px primary, line-clamp-2, hover turns gold transition.
> - Excerpt: muted DM Sans 14px line-clamp-2.
> - Footer row: Author initials avatar + name (muted 12px) + read time (muted 12px) + small "🔥 Trending" badge if applicable.
> - "Read More →" gold link bottom-right.
> - Outfit strip below article meta: "Try looks from this article →" — tiny horizontal strip of 2–3 outfit squares (50px, rounded-lg) with a subtle "Try On" tooltip on hover. **Clicking any outfit square navigates to tryon.html?outfit=N.** This is the key conversion element — it's what bridges content to try-on.
>
> Use these blog titles and categories:
> 1. "5 Kurta Styles Every Indian Man Needs" — Men's Style
> 2. "How to Style a White Saree for Modern Occasions" — Women's Style
> 3. "Best Outfits for a Beach Wedding Guest (Men)" — Wedding Season
> 4. "Office-Ready Western Casuals Under ₹2,000" — Western
> 5. "Plus-Size Fashion: Your Summer Style Guide" — Sustainability
> 6. "Navratri 2025: Colour Schedule & Outfit Ideas" — Seasonal
>
> **Load More Posts:** Below grid, centered "Load More Articles" outlined gold pill button. On click: shows 3 skeleton loaders, then fades in 3 more posts.
>
> ---
>
> ### SIDEBAR (right, sticky top-24)
>
> **Widget 1 — Try Outfits Now (conversion widget)**
> Surface card `#13131A` border `#2A2A35` rounded-2xl p-6. Label "TRENDING LOOKS THIS WEEK" gold uppercase 10px. 3 outfit cards vertical list (compact): 60px square image left + name + price right + "Try On →" gold link. Divider between each. Bottom: "See All Outfits →" muted link.
>
> **Widget 2 — Most Read**
> Same card shell. "MOST READ" label. Numbered list 1–5: number (gold, large Cormorant), title (primary DM Sans 14px), read time (muted 11px). Hover: title turns gold.
>
> **Widget 3 — Email Subscribe**
> Same card shell. "GET WEEKLY STYLE PICKS" gold label. Headline: "Look good, every week." Cormorant 20px. Subtext: "Style tips + new outfit drops, every Monday." muted 13px. Email input (dark surface, gold focus border, rounded-xl, full-width). "Subscribe →" gold filled button full-width. Below: "No spam. Unsubscribe anytime." muted 11px. On submit: button text changes to "Subscribed ✓" green, input disabled.
>
> **Widget 4 — Tags Cloud**
> Label "EXPLORE TOPICS". Flex wrap of tag pills: gold outlined rounded-full px-3 py-1 text-xs. Tags: Wedding, Kurta, Ethnic, Casual, Summer, Winter, Budget Style, Luxury, Plus Size, Office Wear, Festive, Saree, Denim, Sneakers. Hover: fills gold, text dark.
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS BEHAVIORS
> 1. Category tab filter (show/hide cards by data-category attribute)
> 2. Search input: filters post cards by title text (live filtering as user types)
> 3. Load More Posts: skeleton → fade in
> 4. Email subscribe: button state change
> 5. Tag pills click: same as category tab filter

---

---

# PROMPT 6 — BLOG POST
**File: blog-post.html**

---

> Build a complete, production-ready, fully responsive **Blog Post page** for DRIP in a single HTML file using HTML5, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> Use this post as the demo content:
> **Title:** "5 Kurta Styles Every Indian Man Needs in His Wardrobe (2025)"
> **Category:** Men's Style | **Read time:** 7 min | **Date:** January 15, 2025
>
> ---
>
> ## NAVBAR — same as all pages
>
> ---
>
> ## POST HEADER
> Max-w-3xl mx-auto px-6 pt-16 pb-8. Center-left aligned.
> - Breadcrumb: "Blog / Men's Style" muted 12px
> - Category pill: "Men's Style" gold border gold text rounded-full 10px uppercase
> - Headline: Full post title — Cormorant Garamond 48px desktop / 32px mobile, primary, line-height 1.15
> - Subheading/deck: "Whether you're heading to a wedding or just want to elevate your daily look, these five kurta styles will transform your wardrobe." — muted DM Sans 18px font-light
> - Author row: gold initials avatar + "By DRIP Editorial" DM Sans 14px + "·" + "January 15, 2025" + "·" + "7 min read" + "·" + "🔥 12.4k reads"
> - Social share row: "Share:" label + WhatsApp / Twitter / Copy Link icon buttons (muted, gold on hover)
> - Hero image: `https://picsum.photos/900/500?random=60` full-width rounded-2xl mt-8. Caption below in muted italic 13px: "A curated selection of the best kurta styles for 2025."
>
> ---
>
> ## MAIN CONTENT LAYOUT
> Two-column desktop: Article content (max-w-2xl) left, Sticky sidebar right (300px). Single column mobile.
>
> ---
>
> ### ARTICLE CONTENT (left)
>
> Reading-optimized. font-size 16px, line-height 1.8, color brandPrimary, DM Sans.
>
> **Table of Contents block** (top of article): Surface card `#13131A` border `#2A2A35` rounded-xl p-5. "In this article:" DM Sans 12px muted uppercase. Numbered links to each section (smooth scroll). Gold on hover.
>
> **Article body — 5 sections:**
>
> Each section follows this pattern:
> - Section number + headline: "01 — The Classic Straight-Cut Kurta" — Cormorant Garamond 28px gold/primary
> - 2 paragraphs of body text (realistic fashion copy about that kurta style)
> - **INLINE OUTFIT CARD** — this is the key conversion element. A card styled as an editorial callout: surface bg `#13131A`, border gold, rounded-2xl, p-4, flex row. Left: outfit image 100px square rounded-xl. Right: Outfit name (Cormorant 18px), Brand (muted 12px), Price (gold 16px), then two buttons: "✨ Try This On →" (gold filled, small, rounded-full) and "Buy Now" (outlined, small). **"Try This On" clicking navigates to tryon.html?outfit=N.** The card should feel like a natural part of the editorial content, not an ad. Use outfit images picsum randoms 40–44 for the 5 sections.
> - Continue with 1 more paragraph after the card
>
> **Between sections 2 and 3:** A pull quote block: left gold border (4px), bg `rgba(201,168,76,0.05)`, rounded-r-xl, px-6 py-4. Quote text in Cormorant Garamond 22px italic primary: "The kurta is not just clothing — it's a cultural statement, elevated for the modern Indian man." No attribution needed.
>
> **After section 5:** "Try All Looks From This Article →" — full-width gold filled CTA button, large, rounded-2xl. Clicking: navigates to tryon.html. This is the post's final conversion push.
>
> **Article footer:** Divider line. Tags row: "Tagged:" + pill tags (Wedding, Kurta, Men's Style, Indian Fashion). Social share row (same as header). Author bio card: surface card, gold avatar large, "DRIP Editorial" name, 2-sentence bio. "More from this author →" gold link.
>
> ---
>
> ### STICKY SIDEBAR (right, desktop only)
>
> **Widget 1 — Try Outfits from This Article**
> "TRY LOOKS FROM THIS ARTICLE" gold label 10px uppercase. 5 outfit thumbnails (one per section): 3-column mini grid. Each 70px square rounded-xl border `#2A2A35`. Hover: gold border + small tooltip with outfit name. Below grid: "Try All 5 Looks →" gold filled button full-width → tryon.html. This widget is the primary revenue driver for blog posts.
>
> **Widget 2 — Table of Contents (sticky)**
> Same as inline TOC. Highlights current section as user scrolls (JS IntersectionObserver). Current section: gold text, gold left border.
>
> **Widget 3 — Related Posts**
> 3 compact post cards: small image left (60px rounded-lg) + title right (14px Cormorant) + read time muted 11px. Title hover gold.
>
> **Widget 4 — Newsletter subscribe** (same as blog index sidebar widget 3)
>
> ---
>
> ## RELATED POSTS SECTION (below article, full width)
> Background `#13131A`. "You Might Also Like" Cormorant 32px. 3 blog post cards (same as blog-index grid cards). Mobile: horizontal scroll snap strip.
>
> ---
>
> ## COMMENTS SECTION
> Background `#0A0A0F`. "Join the conversation" Cormorant 28px. Comment count: "24 comments" muted.
>
> **Comment form:** Surface card, rounded-2xl, p-6. Name input + Email input (side by side desktop, stacked mobile) + Textarea (Comment, 4 rows). All inputs: dark surface bg, border `#2A2A35`, gold focus border, rounded-xl. "Post Comment" gold filled button right-aligned. On submit: form clears + new comment appears at top of list with fade-in.
>
> **3 existing comments:** Each: initials avatar (random muted colors) + name bold + date muted + body text + "Reply ↩" muted link (clicking: shows inline reply textarea below that comment). Nested reply example under comment 1 showing 1 reply (slightly indented, smaller avatar).
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS BEHAVIORS
> 1. Smooth scroll from TOC links to sections
> 2. IntersectionObserver: highlight current section in sidebar TOC
> 3. Reading progress bar: thin gold line at very top of viewport (fixed, z-50) that fills from 0–100% as user scrolls through article
> 4. Social share buttons: Copy Link copies URL + toast
> 5. Comment form submit: append new comment to list with animation
> 6. Reply button: show/hide inline reply textarea with animation
> 7. Inline outfit card "Try This On" → navigate to tryon.html with param

---

---

# PROMPT 7 — LOGIN / SIGNUP
**File: auth.html**

---

> Build a complete, production-ready, fully responsive **Login / Signup page** for DRIP in a single HTML file using HTML5, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This is a split-screen page. Simple, premium, no clutter.
>
> ---
>
> ## LAYOUT — Two column (desktop) / Single column (mobile)
>
> **Left panel (50% desktop, hidden mobile):** Full height. Background: a fashion editorial image `https://picsum.photos/700/900?random=70` as background-image, object-cover. Dark gradient overlay from left (70% opacity) to transparent right. Over the image:
> - "DRIP" logo top-left in Cormorant Garamond gold 32px tracking-widest
> - Bottom-left (absolute): Testimonial card — surface card `#13131A` opacity-90 backdrop-blur, rounded-2xl p-6 max-w-xs. Gold quote mark large. Quote text: "I tried 12 kurtas in 5 minutes and found the perfect one for my cousin's wedding. This is genius." — Cormorant Garamond 18px italic. Below: initials avatar + "Rahul M., Delhi" + 5 gold stars.
>
> **Right panel (50% desktop, 100% mobile):** Background `#0A0A0F`. Flex column center. Max-w-sm mx-auto px-6. Full height.
>
> ---
>
> ## AUTH FORM PANEL (right side)
>
> **Logo (mobile only):** "DRIP" Cormorant gold top-center on mobile, hidden on desktop.
>
> **Mode toggle tabs:** Two tabs — "Sign Up" and "Log In". Pill-style toggle: active tab gold bg dark text, inactive transparent muted text. Switching tabs: JS shows/hides respective form with fade transition.
>
> ---
>
> ### SIGN UP FORM (default visible)
>
> Headline: "Create your account" Cormorant Garamond 32px
> Subtext: "Start trying outfits for free. No credit card needed." muted DM Sans 14px
>
> **Social sign up (primary method):**
> "Continue with Google" button — white background, #1a1a1a text, Google SVG icon (colored) left, DM Sans 15px font-medium, rounded-xl full-width py-3.5. Hover: slight lift.
>
> Divider: "— or sign up with email —" muted 12px centered.
>
> **Email form:**
> - Full Name input: label "Full Name" 12px muted above, dark surface input, gold focus border, rounded-xl, placeholder "Rahul Sharma"
> - Email input: label "Email Address", placeholder "rahul@gmail.com"
> - Phone (optional): label "Phone (optional)" muted label, placeholder "+91 98765 43210"
> - "Send Magic Link →" gold filled button full-width py-3.5 rounded-xl. (No password — magic link/OTP auth)
>
> **Form validation (JS):**
> - Empty name: input border turns red, shake animation, error text "Please enter your name" in brandError below input
> - Invalid email: same pattern
> - Valid submit: button text changes to "✓ Magic link sent!" green, input fields fade out, success state appears (see below)
>
> **Success state (after submit):**
> Form disappears with fade-out. Success card fades in: email icon (gold, 48px), "Check your inbox!" Cormorant 28px, "We've sent a magic link to rahul@gmail.com. Click it to sign in — no password needed." muted DM Sans. "Resend link" muted link (active after 30s countdown shown in gray).
>
> Terms text below form: "By signing up you agree to our Terms of Service and Privacy Policy." muted 11px, links in gold underline.
>
> ---
>
> ### LOG IN FORM (hidden by default, shown when "Log In" tab clicked)
>
> Headline: "Welcome back" Cormorant Garamond 32px
> Subtext: "Sign in to access your saved looks and style history." muted DM Sans 14px
>
> "Continue with Google" button (same as signup)
>
> Divider "— or sign in with email —"
>
> Email input (same style). "Send Magic Link →" button (same).
>
> "Don't have an account? Sign up free →" link below form in gold.
>
> ---
>
> ## FLOATING BACK LINK
> Top-left on mobile (desktop it's inside left panel): "← Back to DRIP" muted link. Clicking goes to landing.html.
>
> ---
>
> ## JS BEHAVIORS
> 1. Tab toggle (Sign Up ↔ Log In) with fade transition
> 2. Google button: mock — shows "Redirecting to Google..." toast then after 1.5s sets localStorage `drip_user = {name: "Test User", email: "test@gmail.com"}` and redirects to dashboard.html
> 3. Email form validation (real-time: validate on blur, on submit)
> 4. Success state after email submit
> 5. Resend countdown timer (30 seconds, updates every second)
> 6. Auto-redirect if already logged in (check localStorage `drip_user` on load → redirect to dashboard.html)

---

---

# PROMPT 8 — USER DASHBOARD
**File: dashboard.html**

---

> Build a complete, production-ready, fully responsive **User Dashboard page** for DRIP in a single HTML file using HTML5, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## NAVBAR — same pattern but add user menu
> Logo left. Center links same. Right: "Try It Free" button + user avatar button (gold circle, user initials "RS", clicking opens user dropdown menu).
>
> **User dropdown menu:** Absolute dropdown from avatar. Surface card `#13131A` border `#2A2A35` rounded-2xl shadow-2xl p-2 min-w-48. Items: "My Dashboard" (active, gold), "Saved Looks", "Settings", divider, "Log Out" (red text on hover). Close on click outside (JS).
>
> ---
>
> ## DASHBOARD HEADER
> Background `#13131A`. py-12. Max-w-7xl centered. px-6.
> Left: "Welcome back, Rahul 👋" Cormorant Garamond 36px. Below: "You've tried 23 outfits and saved 7 looks." muted DM Sans 14px.
> Right: Stats strip — 3 stat cards inline: "23 Tried" / "7 Saved" / "5/5 tries left today" — each: number in Cormorant Garamond 28px gold, label in muted DM Sans 11px uppercase. Divider between each.
>
> **Daily tries progress bar:** Below stats. "Daily Tries: 0 of 5 used" label. Gold progress bar (0% wide). Thin, full-width, rounded-full. Background `#2A2A35`.
>
> ---
>
> ## DASHBOARD TABS
> Border-bottom `#2A2A35`. 3 tabs: "Saved Looks (7)" | "Wishlist (12)" | "Try-On History (23)". Same tab style as blog index. Active = gold underline.
>
> ---
>
> ### TAB 1 — SAVED LOOKS (default active)
>
> Masonry-style grid or uniform 3-col grid. Gap-6. 7 saved look cards.
>
> Each saved look card: Background `#13131A`. Border `#2A2A35`. Rounded-2xl. Overflow hidden. Hover: border gold, lift.
>
> Card structure:
> - Try-on result image (aspect 3/4, picsum randoms 100–106, object-cover)
> - Overlay on hover: two action buttons slide up from bottom (translateY animation): "🛒 Buy Now" (gold filled) and "✨ Try Again" (outlined gold)
> - Card footer (always visible): Outfit name (Cormorant 16px), Brand + Price (muted 12px + gold 14px), Date saved (muted 11px), Delete icon top-right (trash icon, muted, red on hover — clicking removes card with fade-out animation)
>
> **Empty state** (shown if array is empty via JS clear button for demo): Hanger icon gold 64px centered. "No saved looks yet." Cormorant 24px. "Go try some outfits!" DM Sans muted. "Browse Outfits →" gold button.
>
> ---
>
> ### TAB 2 — WISHLIST (hidden by default)
>
> Same grid structure. 12 outfit cards (same as Explore page cards). Difference: no "result image" — shows product image. Heart icon top-right pre-filled red (saved). Clicking heart: removes from wishlist with confirmation ("Remove from wishlist?" appears as inline card overlay with Yes/No).
>
> **"Try All Wishlisted" CTA** above grid: gold outlined button "Try On All Wishlisted Outfits →" → tryon.html.
>
> ---
>
> ### TAB 3 — TRY-ON HISTORY (hidden by default)
>
> Timeline layout. Each session is a row:
> - Date header (e.g., "Today", "Yesterday", "Jan 12, 2025") — muted DM Sans 12px uppercase, full-width border-bottom
> - Under each date: horizontal scroll of try-on session cards (or grid on desktop)
>
> Each history card: smaller than saved looks (200px wide). Try-on result thumbnail (picsum). Outfit name. "Tried at 3:42 PM" muted 11px. Two buttons: "Save This Look" (outlined gold tiny) + "Buy Now" (muted outlined tiny).
>
> "Clear History" link bottom-right of tab — muted, clicking shows a confirm dialog (custom modal, not browser default): "Clear all history? This can't be undone." with "Clear All" red button + "Cancel" muted button.
>
> ---
>
> ## SIDEBAR (desktop only, 280px right)
> Sticky. Padding p-6.
>
> **Widget 1 — Profile Card**
> Surface card `#13131A`. Gold avatar large (64px circle, initials "RS"). Name "Rahul Sharma" Cormorant 22px. Email muted DM Sans 13px. "Edit Profile →" gold link. Divider. Member since: "January 2025" muted 12px.
>
> **Widget 2 — Style Preferences**
> "YOUR STYLE" gold label 10px. 3 preference pills (editable): "Men's Ethnic", "Wedding Guest", "Budget: ₹500–₹3,000". "Edit Preferences →" muted link. Below: "Based on your style, try these →" 3 small outfit thumbnails with Try On links.
>
> **Widget 3 — Invite Friends**
> Dashed gold border card. "Invite a friend, both get 10 extra tries!" gold headline 16px Cormorant. Referral link input (readonly, user's unique link). "Copy Link" gold button. Share via WhatsApp green button.
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS BEHAVIORS
> 1. Tab switching (3 tabs) with content fade
> 2. User dropdown menu open/close
> 3. Delete saved look → fade out card, update count in tab label
> 4. Remove from wishlist → confirm overlay → fade out
> 5. Clear history → custom confirm modal
> 6. Copy referral link → clipboard + toast
> 7. Load user data from localStorage (`drip_saved`, `drip_user`) on page load
> 8. Redirect to auth.html if not logged in (check localStorage)
> 9. Progress bar width = (tries_used / 5) * 100%

---

---

# PROMPT 9 — GLOBAL COMPONENTS & TOAST SYSTEM
**File: components.html**

---

> Build a **Components Demo page** for DRIP that showcases all reusable UI components used across the app. Single HTML file, Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This page is for your own development reference. It shows every component isolated so you can copy them into other pages easily.
>
> ---
>
> Display each component in a labeled section with a dark surface card wrapper. Section label: component name in gold uppercase. Each component is interactive (fully functional).
>
> ---
>
> ## COMPONENT 1 — Toast Notification System
>
> The toast system used across ALL pages. Implement as a reusable JS class `DripToast`.
>
> Toast container: fixed bottom-right (bottom-6 right-6), z-50, flex column gap-3.
>
> Each toast: Surface card `#13131A` border `#2A2A35` rounded-2xl px-5 py-4 shadow-2xl. Min-width 280px. Flex row: icon left (colored per type) + message text + × close button right.
>
> 4 types:
> - **success**: green checkmark icon, left border green
> - **error**: red × icon, left border brandError
> - **info**: gold info icon, left border gold
> - **warning**: orange ⚠ icon, left border orange
>
> Animation: slides in from right (translateX 100% → 0) with ease-out 300ms. Auto-dismisses after 3 seconds with fade-out. Multiple toasts stack vertically. Dismiss on × click.
>
> Demo buttons: "Show Success" / "Show Error" / "Show Info" / "Show Warning"
>
> ---
>
> ## COMPONENT 2 — Modal System
>
> Reusable modal: dark overlay (bg-black/60 backdrop-blur-sm), centered card (surface `#13131A` border rounded-2xl max-w-md w-full mx-4 p-8), close × top-right, ESC key closes, click outside closes.
>
> Open/close with smooth fade + scale animation (scale 0.95 → 1.0 on open).
>
> Demo button: "Open Modal"
>
> ---
>
> ## COMPONENT 3 — Confirm Dialog
>
> Smaller modal variant for confirmations. "Are you sure?" Cormorant 24px. Subtext muted. Two buttons: "Confirm" (red filled) + "Cancel" (muted outlined).
>
> ---
>
> ## COMPONENT 4 — Outfit Card (all variants)
>
> Show the outfit card in 3 sizes: Standard (Explore page), Compact (sidebar widget), Mini (inline strips).
>
> ---
>
> ## COMPONENT 5 — Button System
>
> Show all button variants in a row:
> - Primary (gold filled)
> - Secondary (gold outlined)
> - Ghost (transparent, muted text)
> - Danger (red filled)
> - Icon button (circle, icon only)
> - Loading state (spinner inside button, text "Loading...")
> - Disabled state
>
> All with proper hover/active/focus states.
>
> ---
>
> ## COMPONENT 6 — Form Inputs
>
> Text input (default, focus, error, success states). Textarea. Custom select dropdown. Custom checkbox. Custom radio buttons. Range slider. All styled to design system.
>
> ---
>
> ## COMPONENT 7 — Skeleton Loaders
>
> Card skeleton (outfit card shape). Text skeleton (3 lines, varying width). Image skeleton. All with shimmer animation.
>
> ---
>
> ## COMPONENT 8 — Avatar System
>
> Gold circle avatars in sizes: sm (32px), md (40px), lg (64px). With initials. With image. With online indicator dot (green).
>
> ---
>
> ## COMPONENT 9 — Badge / Pill System
>
> All badge variants: gold border, gold filled, green (success), red (error), muted. Category tags. "New" tag. "Trending 🔥" tag.
>
> ---
>
> ## COMPONENT 10 — Progress Bar
>
> Linear progress bar (daily tries). With animated fill. With label. Thin variant (1px) and standard (6px).

---

---

# QUICK REFERENCE — SHARED ELEMENTS

## Inter-page Navigation Map
```
landing.html
  → explore.html (Explore link, category cards)
  → tryon.html (all CTAs)
  → blog-index.html (blog section)
  → auth.html (Login link)

explore.html
  → outfit.html (clicking any card)
  → tryon.html ("Try On" button on cards)
  → auth.html (Login link)

outfit.html
  → tryon.html ("Try This On Me" CTA)
  → explore.html (More from brand section)
  → blog-post.html (From our blog section)

tryon.html
  → auth.html (Save button if not logged in)
  → external affiliate (Buy Now)
  → explore.html (browse more)

blog-index.html
  → blog-post.html (any post card)
  → tryon.html (outfit strip in cards)

blog-post.html
  → tryon.html (inline outfit cards, final CTA)
  → explore.html (related outfits)

auth.html
  → dashboard.html (after login)
  → landing.html (back link)

dashboard.html
  → tryon.html (Try Again, Try All)
  → explore.html (Browse Outfits empty state)
```

## localStorage Keys (consistent across all pages)
```
drip_user         → {name, email} or null (logged in state)
drip_saved        → array of outfit IDs (saved looks)
drip_wishlist     → array of outfit IDs (wishlist)
drip_tries        → {date: "2025-01-15", count: 2} (daily try count)
drip_recent       → array of outfit IDs (recently viewed)
drip_history      → array of {outfitId, resultImg, timestamp}
```

## URL Params (consistent)
```
tryon.html?outfit=N    → pre-loads outfit N in studio
explore.html?category=X → pre-filters category X
explore.html?occasion=X → pre-filters occasion X
```
