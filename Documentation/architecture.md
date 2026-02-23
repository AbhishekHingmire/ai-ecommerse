# DRIP — AI Fashion Try-On SaaS
## Complete Functional UI/UX Architecture (MVP)

---

## Brand Identity First

**Name suggestion:** DRIP (or you pick — but the system below works for any name)

**Design Language:** Luxury-minimal. Think Zara meets Notion. Dark navy/charcoal base, cream/off-white text, single gold or electric-lime accent. Premium but not intimidating. Clean whitespace with editorial photography. Typography: a sharp serif display font (like Playfair Display or Cormorant) paired with a geometric sans for UI (like DM Sans or Sora — not Inter, not Roboto).

**The feeling you want every user to have:** "This feels expensive. It's fast. It actually works. I trust it."

**Core Design Rules across every page:**
- Max content width: 1280px, centered
- Generous padding — never cramped
- One CTA per screen — never confuse the user
- Micro-animations on every interactive element (hover lifts, smooth transitions, skeleton loaders)
- Mobile-first — fashion audience is 80%+ mobile

---

## Sitemap — All Pages

```
PUBLIC
├── / (Landing Page)
├── /explore (Browse Outfits)
├── /outfit/:id (Single Outfit Page)
├── /try-on (Try-On Studio) ← CORE PRODUCT
├── /blog (Blog Index)
├── /blog/:slug (Blog Post)
├── /about
├── /pricing (Phase 2)
└── /login & /signup

AUTHENTICATED
├── /dashboard (Saved Looks)
├── /history (Past Try-Ons)
├── /profile (Settings)
└── /upgrade (Phase 2)

ADMIN (internal)
├── /admin/outfits
├── /admin/blogs
└── /admin/analytics
```

---

## PAGE-BY-PAGE FUNCTIONAL WALKTHROUGH

---

### PAGE 1 — Landing Page ( / )

**Purpose:** Convert a cold visitor into someone who tries the product within 60 seconds.

**Emotional arc:** Intrigue → Trust → Excitement → Action

---

**Section 1: Hero**

Full-viewport. Dark background. Center-aligned.

Left side: Large editorial headline — something like:
*"Wear it before you buy it."*
Subheadline: "Try thousands of outfits on your photo. Instantly. Free."

Right side (or full-bleed behind): A looping before/after animation — a photo of a person, outfit overlays on them in sequence, different styles cycling. This is the product selling itself in 3 seconds.

Single CTA button: **"Try It Free — No Sign Up"**

This button is everything. Make it impossible to miss. Gold or lime on dark. Slightly oversized. Hover: it lifts with a shadow.

Small trust line below button: "3 free tries daily · No credit card · 10,000+ outfits"

---

**Section 2: How It Works**

3-step horizontal strip. Icon + short label + one-line description each.

Step 1 — Upload your photo (or use your webcam)
Step 2 — Browse & tap any outfit
Step 3 — Love it? Buy it in one click.

Keep it scannable. 15 seconds to read. No paragraphs.

---

**Section 3: Live Demo / Social Proof Strip**

A horizontally scrolling strip of real try-on result cards. Show 6–8 examples across different skin tones, body types, categories. This is critical — people need to see it works on people who look like them.

Each card: Before photo (small) → Arrow → After photo with outfit. Below: outfit name + "Buy This Look" link.

---

**Section 4: Category Selector**

4 big cards in a 2x2 grid (or horizontal scroll on mobile):
- Men's Ethnic Wear
- Western Casuals
- Women's Sarees & Lehengas
- Plus-Size Fashion

Each card: editorial photo, category name, outfit count ("240+ outfits"). Click → goes to /explore?category=X

---

**Section 5: SEO Blog Teaser**

Headline: *"Style Guides — Written for Real People"*
3 latest blog post cards. Thumbnail, title, read time. "Read More →"

This section has dual purpose: drives internal links for SEO, and gives first-time visitors content to explore if they're not ready to try-on yet.

---

**Section 6: Footer**

Logo + tagline left. Links: Explore, Blog, About, Affiliate Disclosure, Privacy Policy, Terms. Social icons. "Made in India 🇮🇳" — small but builds trust with Indian audience.

---

### PAGE 2 — Explore Page ( /explore )

**Purpose:** Browse the outfit catalog. Entry point from blog posts and homepage.

**Layout:** Filter sidebar (desktop) / bottom sheet filters (mobile) + outfit grid.

---

**Filter Panel (left sidebar / mobile bottom sheet):**

- Category: Men's Ethnic / Western / Women's / Plus-Size (checkbox)
- Occasion: Wedding, Casual, Office, Festival, Date Night
- Color: Visual color swatches (not dropdowns)
- Price Range: Slider ₹0 – ₹5,000+
- Brand: Checkboxes (only brands you've listed)
- Sort: Trending / Newest / Price Low-High / Most Tried

Filters update results instantly without page reload. No "Apply" button — live filtering feels premium.

---

**Outfit Grid:**

Masonry or uniform card grid. 3 columns desktop, 2 columns tablet, 1-2 mobile.

**Each outfit card contains:**
- Product image (clean white background OR model photo — consistent)
- Outfit name
- Brand name (small, muted)
- Price (prominent)
- Small "Try On" button — always visible, not just on hover
- Heart icon (save to wishlist — encourages soft sign-up)
- "X people tried this today" — social proof, builds FOMO

Hover state: card lifts slightly, Try On button glows.

**Top of page:** Breadcrumb + result count + active filter chips ("Showing 142 outfits · Men's Ethnic · Wedding")

---

### PAGE 3 — Single Outfit Page ( /outfit/:id )

**Purpose:** Deep product page. SEO-rich. Conversion page.

**Layout:** Two column. Left: outfit visuals. Right: details + CTAs.

---

**Left Column:**
- Primary product image (large)
- Thumbnail strip below (multiple angles if available)
- "View on Model" toggle — shows outfit on a model photo vs plain background
- Small tag: "This outfit has been tried 847 times"

---

**Right Column:**

Outfit name (large, serif font)
Brand name (linked)
Price (large, prominent)
Available sizes (S/M/L/XL/XXL — visual buttons, not dropdown)
Color variants if any

**Primary CTA: "Try This On Me →"** — full width, accent color
This immediately takes user to Try-On Studio with this outfit pre-loaded.

**Secondary CTA: "Buy Now"** — outlined button, opens affiliate link in new tab

Short description: fabric, occasion, style notes (2–3 lines max)

Delivery note: "Ships via [brand] · Usually 3–5 days"

---

**Below the fold:**

"Style This With" — 3 accessory/complementary outfit cards (cross-sell, more affiliate revenue)

"From the Blog" — 2 blog posts that mention or feature this outfit (internal linking gold for SEO)

"More from [Brand]" — 4 more outfit cards

Reviews section (Phase 2 — start empty or pull from affiliate source)

---

### PAGE 4 — Try-On Studio ( /try-on ) ← THE CORE PRODUCT

**Purpose:** The money page. This is the entire reason the app exists. It must feel magical.

**Design principle:** Minimal UI, maximum focus on the result. Everything else disappears.

---

**Studio Layout (Desktop — Two Panel):**

Left Panel (40% width): Your Photo
Right Panel (60% width): Result / Outfit Selection

**Left Panel — Upload Zone:**

On first visit, a clean upload box:
- Dashed border, rounded corners
- Large upload icon + text: "Upload your photo"
- Sub-text: "Best results: front-facing, good lighting, plain background"
- Two options below: "Upload Photo" button + "Use Camera" button
- Small note: "Your photo is never stored. Deleted after 24 hours."
  (This is important — privacy anxiety is real, address it upfront)

Once photo is uploaded:
- Photo preview fills the left panel
- "Change Photo" link in top corner (small, unobtrusive)
- Below photo: Try count indicator — "2 of 3 free tries used today"

---

**Right Panel — Outfit Selection + Result:**

**State 1 (No outfit selected yet):**
A scrollable outfit strip across the top — horizontally scrollable thumbnail cards of outfits. Pre-loaded with outfit from /outfit/:id if user came from there. Otherwise shows trending outfits.

Below the strip: Large empty state with dashed border and text:
"Select an outfit above to see how it looks on you →"

---

**State 2 (Outfit selected, generating):**
The result panel shows a skeleton loader / animated shimmer effect.
Overlay text (subtle): "Styling you..."
Duration: 3–8 seconds typically. Show a subtle progress bar.

Do NOT show a spinner. Spinners feel cheap. A shimmer skeleton with the rough shape of the result panel feels premium and intentional.

---

**State 3 (Result ready):**
The try-on result image fills the right panel. Smooth fade-in transition.

Below the result image — 3 action buttons in a row:
1. **"Love it — Buy Now"** → affiliate link (accent color, primary)
2. **"Save This Look"** → triggers soft sign-up modal if not logged in
3. **"Try Another Outfit"** → clears result, keeps photo

Small share icon in top-right of result: "Share my look" → generates a shareable link (viral loop — free marketing)

---

**State 4 (Try limit reached — 3/3 used):**

Don't block aggressively. Show a friendly overlay on the result panel:
"You've used your 3 free tries for today."
"Come back tomorrow — or sign up free to unlock more."

Two buttons: "Sign Up Free (Get 5 tries/day)" + "Come Back Tomorrow"

The sign-up hook here is natural — they're already invested (they've tried 3 looks), so conversion rate on this modal will be meaningfully higher than a cold sign-up wall.

---

**Mobile Try-On Studio Layout:**

Stacked vertically instead of side-by-side.

Top: Photo upload / preview (40% of screen)
Middle: Horizontally scrollable outfit strip
Bottom: Result panel (fills remaining space)

Sticky bottom bar with: Try count + Buy Now button

The mobile experience must be pixel-perfect — this is where 70%+ of your users will be.

---

**Outfit Strip (inside Studio) — Detail:**

Each outfit thumbnail card:
- Small image (square crop)
- Price below
- Tapping it instantly triggers generation
- Active state: gold border around card to show "currently viewing"
- Infinite scroll or "Load More" — don't paginate here, it breaks flow

Filter pills above the strip: All / Ethnic / Casual / Festive — lets user quickly narrow outfits without leaving studio.

---

### PAGE 5 — Blog Index ( /blog )

**Purpose:** SEO traffic entry point. First impression for organic visitors.

**Layout:** Magazine-style editorial grid. Not a generic blog list.

---

**Hero area:** Featured post — large image, category tag, title, excerpt, "Read →"

**Below hero:** Category filter tabs: All / Ethnic Wear / Casuals / Style Tips / Seasonal Trends / Plus-Size

**Post grid:** 3 columns desktop, 2 tablet, 1 mobile.

Each card: Image (16:9 ratio, consistent), Category tag (colored pill), Title, 1-line excerpt, Read time, Date.

**Sidebar (desktop only):** 
- "Trending Looks This Week" — 4 outfit cards with Try On buttons
- "Most Read Posts" list
- Email subscribe box ("Get weekly style picks")

The sidebar outfit cards are a direct conversion bridge — reader came for content, sees outfits, tries them on.

---

### PAGE 6 — Blog Post ( /blog/:slug )

**Purpose:** Rank on Google. Convert reader to try-on user. Earn affiliate commission.

**This is your most important page for revenue.** Architecture it carefully.

---

**Layout:** Reading-optimized. Max 680px content width, centered. Generous line height.

**Top of post:**
- Category tag + estimated read time
- Title (large, serif — editorial feel)
- Featured image (full width)
- Author + date

**Within post content:**

Every outfit mentioned in the article has an **inline outfit card** — not just a link, an actual embedded mini-card with:
- Outfit image (small, right-aligned or centered)
- Name + price
- **"Try This On →"** button

This is your conversion layer inside content. Reader is reading "5 Best Kurtas for a Wedding" — they see Outfit #3, tap "Try This On" — goes directly to Try-On Studio with that outfit preloaded. This is the Lenskart loop.

**Right sidebar (sticky on desktop):**
- "Try These Looks" — 3 outfit cards from the post
- Stays visible as they scroll — constant conversion opportunity

**End of post:**
- "You might also like" — 3 related blog posts (reduces bounce rate)
- "Try all looks from this post" — CTA button that opens studio with all mentioned outfits pre-queued

---

### PAGE 7 — Dashboard ( /dashboard ) — Authenticated

**Purpose:** Personal style hub. Builds habit and return visits.

**Layout:** Clean, personal. Feels like their wardrobe.

---

**Top section:** Greeting + stats strip:
"Welcome back, [Name]" 
Stats: Outfits Tried: 47 | Saved Looks: 12 | Tries Left Today: 5

---

**Tabs:**
1. Saved Looks — grid of their saved try-on results (actual result images)
2. Wishlist — outfits they hearted without trying
3. History — past try-on sessions (outfit + their result image)

**Each saved look card:**
- Their try-on result image
- Outfit name + price
- "Buy Now" button
- "Try Again" (in case they want a fresh photo)
- Delete icon

**Empty states matter:** If Saved Looks is empty — don't show a blank page. Show: "You haven't saved any looks yet. Start exploring →" with 3 outfit suggestions.

---

### PAGE 8 — Login / Signup

**Purpose:** Minimal friction. Don't lose them here.

**Design:** Single centered card on dark background. Clean.

Sign up options in order:
1. Continue with Google (one-click, most users pick this)
2. Continue with Email (for users who prefer it)

No password required initially — magic link or OTP to email/phone.

Below form: "By signing up you agree to Terms · We never spam"

After sign-up: Redirect back to wherever they were (Try-On Studio, specific outfit, etc.) — not to a generic dashboard. This reduces post-signup drop-off dramatically.

---

## MICRO-INTERACTIONS & FEEL

These are what separate a ₹50K-looking product from a ₹5Cr-looking product:

**Page transitions:** Smooth fade between pages. Not instant jumps.

**Button states:** Every button has default / hover (lift + shadow) / active (press down) / loading (spinner inside button, text changes to "Generating...") states.

**Outfit card hover:** Card lifts 4px, shadow deepens, "Try On" button slides up from bottom of card.

**Try-on result reveal:** Fade in over 0.4s with a subtle scale from 0.97 to 1.0. Feels like a curtain being pulled back.

**Try count indicator:** When tries reduce, the number animates (count-down flip animation). Subtle but creates urgency.

**Save animation:** When user taps heart, heart fills with color + small burst particle effect. 0.3 seconds. Feels satisfying.

**Loading skeleton:** All content loads with shimmer placeholders — never blank white pages. Perceived performance is as important as actual performance.

**Error states:** If try-on API fails — don't show a red error. Show: "Hmm, let's try that again." with a retry button. Keep the tone warm.

---

## NAVIGATION

**Desktop Navbar (sticky):**
Logo left → Links center (Explore / Blog / About) → Right: Try Now button (accent) + Login

**Mobile Navbar:**
Logo left → Hamburger right → Drawer slides in from right with all links + prominent "Try Now" CTA at bottom of drawer

**The "Try Now" button is always visible.** On every page. It's your north star CTA.

---

## EMPTY STATES & ONBOARDING

**First-time user on Try-On Studio:**
A subtle onboarding tooltip sequence (3 steps max):
1. "Upload your photo here" (arrow pointing to upload zone)
2. "Pick any outfit from the strip above"
3. "Your result appears here — buy what you love"

Dismiss: "Got it" button OR auto-dismiss after they complete first try.

Don't over-onboard. 3 steps max. Users learn by doing.

---

## COLOR SYSTEM (Tailwind-compatible)

```
Background:    #0A0A0F  (near black — premium, not harsh)
Surface:       #13131A  (cards, panels)
Border:        #2A2A35  (subtle separators)
Text Primary:  #F5F0E8  (warm off-white — easier on eyes than pure white)
Text Muted:    #8A8A9A  (secondary labels)
Accent:        #C9A84C  (gold — luxury signal)
Accent Hover:  #E2C06A  (lighter gold on hover)
Success:       #4CAF82  (green — purchase confirmed, saved)
Error:         #E05A5A  (soft red — never harsh)
```

All colors defined as Tailwind CSS variables. Consistent across every component.

---

## TYPOGRAPHY SYSTEM

```
Display (hero headlines):   Cormorant Garamond — Serif, elegant, editorial
UI / Body:                  DM Sans — Clean, readable, modern
Monospace (prices, counts): DM Mono — Makes numbers feel precise
```

Font sizes follow Tailwind scale strictly. No random pixel values.

---

## RESPONSIVE BREAKPOINTS

```
Mobile:   < 640px   — Single column, bottom nav, full-screen studio
Tablet:   640–1024px — 2 col grid, sidebar collapses
Desktop:  > 1024px  — Full 2-panel studio, sidebar visible
```

Mobile is designed first. Desktop is the enhancement.

---

## USER JOURNEY — END TO END

This is how a first-time user experiences the product:

**1. Discovers via Google** — searches "best kurta for wedding guest men"
→ Lands on your blog post

**2. Reads 30% of article** — sees inline outfit card with "Try This On →"
→ Clicks it, lands in Try-On Studio with outfit pre-loaded

**3. Try-On Studio** — sees upload prompt
→ Uploads selfie or photo from gallery (mobile: camera roll)
→ Taps outfit → 5 second wait → Result appears

**4. Reaction** — "Oh wow this actually works"
→ Taps "Save This Look" → Soft sign-up modal appears
→ Signs up with Google in 2 taps

**5. Tries 2 more outfits** — count goes 1/3 → 2/3 → 3/3

**6. Hits limit** — "Come back tomorrow or sign up for 5 tries/day"
→ Already signed up, gets 5/day unlocked

**7. Day 2** — Email/notification: "Your saved looks are waiting"
→ Returns, tries more, eventually clicks "Buy Now"
→ You earn affiliate commission

**8. Week 3** — Becomes habitual user
→ Shares a look on WhatsApp (viral loop)
→ Friend clicks shared link → lands on Try-On Studio
→ New user acquired at zero cost

**This is the loop. Everything in the architecture serves this loop.**

---

## WHAT TO BUILD IN WHAT ORDER (MVP Priority)

**Week 1–2 (Core):**
- Landing page (hero + how it works + category cards)
- Try-On Studio (upload + API integration + result display)
- Basic outfit catalog (50 items, manually added)

**Week 3–4 (Commerce):**
- Single outfit page with affiliate links
- Explore/browse page with filters
- Basic blog (3–5 posts minimum before launch)

**Week 5–6 (Retention):**
- Login/signup (Google OAuth)
- Save looks / wishlist
- Dashboard (saved looks tab only)

**Post-launch:**
- Blog index + more posts (ongoing)
- Mobile optimization polish
- Analytics + conversion tracking
- Email capture and drip sequence

---

## WHAT NOT TO BUILD IN MVP

- Reviews / ratings system
- Social feed / following
- Pricing / subscription (affiliate first)
- Multiple photo upload
- Video try-on
- Brand dashboard / portal
- Recommendations AI

Ship lean. Validate the loop. Then build.