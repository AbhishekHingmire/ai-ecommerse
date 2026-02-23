# DRIP — Missing Pages Prompts
# 6 pages + 4 gap fixes

---

## DESIGN SYSTEM (paste into every prompt — same as before)
```
Brand: DRIP — AI-powered fashion virtual try-on web app.
Stack: Single HTML file, Tailwind CSS via CDN, vanilla JS only.
Colors: brandBg:#0A0A0F | brandSurface:#13131A | brandBorder:#2A2A35
brandPrimary:#F5F0E8 | brandMuted:#8A8A9A | brandGold:#C9A84C
brandGoldHover:#E2C06A | brandSuccess:#4CAF82 | brandError:#E05A5A
Fonts: Cormorant Garamond (display) + DM Sans (UI). Import via Google Fonts.
Rules: Button states (default/hover/active/loading). Cards hover lift -4px + gold border.
Shimmer skeleton loaders. localStorage for all data. max-w-7xl. Mobile first.
```

---

# PROMPT 14 — PRIVACY + TERMS + AFFILIATE DISCLOSURE
**Files: privacy.html, terms.html, affiliate-disclosure.html**
*(Build all 3 in one go — same template, different content)*

---

> Build 3 complete, production-ready legal pages for DRIP as separate HTML files. Same design shell for all 3 — only content differs. Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> ---
>
> ## SHARED PAGE SHELL (use for all 3 files)
>
> **Navbar:** Same as all DRIP pages (logo left, nav links center, Try It Free + Login right, mobile hamburger).
>
> **Page header:** Background `#13131A`. py-16. Max-w-3xl mx-auto px-6 text-center.
> - Page title (Cormorant Garamond 48px): varies per page
> - "Last updated: February 2025" — muted DM Sans 13px
> - Reading time estimate — muted 12px
>
> **Main layout:** Max-w-3xl mx-auto px-6 py-16. Two-column: content left (70%) + sticky Table of Contents sidebar right (30% desktop only, hidden mobile).
>
> **Table of Contents sidebar:** Surface card `#13131A` border `#2A2A35` rounded-2xl p-6 sticky top-24. "IN THIS DOCUMENT" gold uppercase 10px label. Numbered links to each section — muted DM Sans 13px, hover gold, active section highlights gold with left border (IntersectionObserver JS). Clicking smooth-scrolls to section.
>
> **Content styling:**
> - Section headings: Cormorant Garamond 26px primary, border-bottom `#2A2A35` pb-3 mb-6, mt-12
> - Body text: DM Sans 15px, `#8A8A9A` (muted), line-height 1.8
> - Highlighted blocks (important notes): Surface card `#13131A` border-left 4px gold, rounded-r-xl px-5 py-4 my-6. Text primary DM Sans 14px.
> - Bold terms: primary color, DM Sans font-medium
> - Lists: styled with gold bullet dot (custom CSS ::before)
> - Links within content: gold color, underline on hover
>
> **Footer:** Same as all pages.
>
> **Reading progress bar:** Fixed top of viewport, thin 2px gold bar filling 0→100% as user scrolls. z-50.
>
> **JS:** IntersectionObserver for TOC active state. Navbar scroll effect. Mobile hamburger. Reading progress bar width = scrollY / (documentHeight - viewportHeight) * 100%.
>
> ---
>
> ## FILE 1: privacy.html
> Title: "Privacy Policy"
>
> Sections (use as H2 anchors):
>
> 1. **What We Collect**
> We collect: email address (if you sign up), photos you upload for try-on (temporarily), usage data (pages visited, outfits tried), device type and browser. We do NOT collect: payment card details (handled by payment processors), government ID, or sensitive personal information.
>
> 2. **How Your Photos Are Used**
> Photos you upload to DRIP's try-on studio are used solely to generate your virtual try-on result. Photos are processed by our AI partner (Replicate.com) and are automatically deleted within 24 hours of upload. We never use your photos for training AI models, advertising, or any purpose other than generating your try-on result.
>
> 3. **Affiliate Links & Third Parties**
> DRIP earns commission from affiliate links to fashion retailers (Myntra, Amazon, Ajio, and others). Clicking these links may allow those retailers to set cookies on your device. We are not responsible for third-party privacy practices. DRIP does not sell your personal data to any third party.
>
> 4. **Cookies**
> We use essential cookies for session management and localStorage for saving your preferences, try-on history, and cart. We use analytics cookies (Google Analytics) to understand site usage. You can disable cookies in your browser settings.
>
> 5. **Your Rights**
> You can: request deletion of your account and data (email us), export your data, opt out of marketing emails (unsubscribe link in every email), request correction of inaccurate data.
>
> 6. **Data Security**
> All data is transmitted over HTTPS/SSL. We do not store payment information — all payments are processed by PCI-DSS compliant payment gateways.
>
> 7. **Children's Privacy**
> DRIP is not intended for users under 13 years of age. We do not knowingly collect data from children.
>
> 8. **Contact Us**
> privacy@drip.ai | Response within 48 hours.
>
> ---
>
> ## FILE 2: terms.html
> Title: "Terms of Service"
>
> Sections:
>
> 1. **Acceptance of Terms**
> By using DRIP, you agree to these terms. If you don't agree, please don't use the service.
>
> 2. **What DRIP Is**
> DRIP is an AI-powered virtual fashion try-on platform. We show you how outfits may look on your photo and provide affiliate links to purchase those outfits from third-party retailers. We are not a retailer ourselves — purchases are fulfilled by partner brands.
>
> 3. **User Responsibilities**
> You agree to: only upload photos of yourself or photos you have rights to use, not attempt to reverse-engineer or scrape the platform, not use the service for any unlawful purpose, not upload harmful, offensive, or illegal content.
>
> 4. **Try-On Results Disclaimer**
> AI try-on results are simulations and may not perfectly represent how a garment will look in reality. Results depend on photo quality, lighting, and body positioning. DRIP does not guarantee accuracy of try-on results.
>
> 5. **Affiliate Disclosure**
> DRIP participates in affiliate programs. We earn a commission when you purchase through our links. This commission comes from the retailer — it does not increase the price you pay. Our outfit recommendations are not influenced by commission rates.
>
> 6. **Intellectual Property**
> DRIP's brand, logo, design, and content are owned by DRIP. Outfit images and product content belong to their respective brands. User-uploaded photos remain your property.
>
> 7. **Limitation of Liability**
> DRIP is provided "as is". We are not liable for: inaccurate try-on results, issues with third-party purchases, or any indirect damages arising from use of the platform.
>
> 8. **Governing Law**
> These terms are governed by the laws of India. Disputes will be resolved in courts of competent jurisdiction in India.
>
> 9. **Changes to Terms**
> We may update these terms. Continued use after changes means acceptance.
>
> 10. **Contact**
> legal@drip.ai
>
> ---
>
> ## FILE 3: affiliate-disclosure.html
> Title: "Affiliate Disclosure"
> Subtitle (below title, muted): "We believe in complete transparency about how we earn."
>
> Sections:
>
> 1. **The Short Version**
> Highlighted block (gold border): "DRIP earns a small commission when you buy products through links on our site. This never increases the price you pay — the retailer pays us a percentage of the sale. Our recommendations are always based on quality and relevance, never on commission rates."
>
> 2. **How It Works**
> When you click "Buy Now" on any outfit on DRIP, you're taken to the retailer's website (Myntra, Amazon Fashion, Ajio, etc.) via a tracked affiliate link. If you complete a purchase within 24–48 hours, DRIP earns a commission of approximately 4–8% of the sale value.
>
> 3. **Our Affiliate Partners**
> Table (styled dark, alternating rows): Partner Name | Program | Commission Range | Cookie Duration
> Rows: Amazon Associates | Amazon | 4–8% | 24 hours
> Myntra Affiliate | Myntra | 5–7% | 30 days
> Ajio Affiliate | Ajio | 4–6% | 30 days
> Meesho Partner | Meesho | 3–5% | 7 days
>
> 4. **What This Means for You**
> Price you pay is identical whether you use our link or go directly. We never recommend poor-quality products just for commission. Try-on results are generated impartially — we show all outfits regardless of affiliate status. You can always buy directly from any brand's website.
>
> 5. **ASCI & Legal Compliance**
> This disclosure complies with the Advertising Standards Council of India (ASCI) guidelines for influencer and affiliate marketing, and with international FTC disclosure requirements.
>
> 6. **Questions?**
> contact@drip.ai

---

---

# PROMPT 15 — ABOUT PAGE
**File: about.html**

---

> Build a complete, production-ready, fully responsive **About page** for DRIP in a single HTML file. Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This page should feel editorial and personal — not corporate. It's a brand story page, not a features page. It should build trust and make people root for DRIP.
>
> ---
>
> ## NAVBAR — same as all pages
>
> ---
>
> ## SECTION 1 — HERO (Mission statement)
> Full-width. Background `#0A0A0F` with subtle radial gold glow center. py-32. Text center. Max-w-3xl mx-auto.
>
> Small label: "OUR STORY" gold uppercase tracking-widest 11px.
> Headline: "We built DRIP because returning clothes is the worst." Cormorant Garamond 56px desktop / 36px mobile. Primary color. Font-weight 300.
> Subtext: "₹40,000 crore worth of fashion is returned in India every year. Most of it because 'it didn't look right on me.' We built the solution." — muted DM Sans 18px font-light. Max-w-xl mx-auto.
>
> Thin gold divider line (50px wide, centered) below subtext.
>
> ---
>
> ## SECTION 2 — THE PROBLEM WE SOLVE
> Background `#13131A`. py-24. Max-w-7xl mx-auto px-6.
>
> Two-column: Left text, right 2x2 stat grid.
>
> Left: Label "THE PROBLEM" gold uppercase. Headline "Online fashion is broken for Indian shoppers." Cormorant 36px. 3 paragraphs of editorial copy about the pain of buying clothes online without trying them — wrong fit, misleading photos, different look on your body type. Return anxiety. Money stuck. Muted DM Sans 15px, line-height 1.8.
>
> Right — 4 stat cards in 2x2 grid. Each: surface card `#0A0A0F` border `#2A2A35` rounded-2xl p-6 text-center.
> - "40%" gold Cormorant 48px + "of online fashion purchases are returned" muted DM Sans 14px
> - "₹40,000 Cr" gold Cormorant 48px + "lost annually to fashion returns in India" muted 14px
> - "67%" gold 48px + "of shoppers abandon carts due to size/fit uncertainty" muted 14px
> - "3.2×" gold 48px + "higher conversion when customers can virtually try on" muted 14px
>
> ---
>
> ## SECTION 3 — HOW WE THINK ABOUT IT
> Background `#0A0A0F`. py-24. Max-w-3xl mx-auto px-6. Text center.
>
> Label "OUR PHILOSOPHY" gold uppercase.
> Headline "Try before you buy. Always." Cormorant 44px.
>
> 3 principle cards horizontal (stack mobile). Each: surface `#13131A` border `#2A2A35` rounded-2xl p-8.
> - Icon (gold SVG) + Principle name (Cormorant 22px) + 2-sentence description (muted DM Sans 14px)
> - Principle 1: "Honesty First" — eye/vision icon — "Our try-on shows you reality, not fantasy. We show results across all body types and skin tones."
> - Principle 2: "Zero Pressure" — open hands icon — "No account needed to start. No credit card. No dark patterns. Just try."
> - Principle 3: "Indian-First" — India map icon — "Built for Indian body types, Indian skin tones, Indian brands, Indian occasions."
>
> ---
>
> ## SECTION 4 — THE TECHNOLOGY
> Background `#13131A`. py-24. Max-w-7xl mx-auto px-6. Two-column (image left, text right).
>
> Left: Abstract tech visual — a surface card `#0A0A0F` with a centered animation: CSS-only flowing gradient (gold and dark shifting slowly). Rounded-2xl. Height 400px. Inside: "IDM-VTON" small label + "Powered by state-of-the-art computer vision" muted text centered.
>
> Right: Label "THE TECH" gold uppercase. Headline "AI that actually works." Cormorant 36px.
> 3 rows, each: gold dot + bold term + description:
> - "Computer Vision" — We use IDM-VTON, an open-source state-of-the-art virtual try-on model fine-tuned on Indian fashion data.
> - "Privacy by Design" — Your photo is processed in memory and deleted within 24 hours. We never store or use your face data.
> - "Accuracy Across Skin Tones" — Our model is tested extensively across the full spectrum of Indian skin tones and body types before going live.
>
> ---
>
> ## SECTION 5 — BUILT IN INDIA
> Background `#0A0A0F`. py-24. Text center. Max-w-3xl mx-auto px-6.
>
> Large "🇮🇳" emoji. Headline "Made with ❤️ in India." Cormorant 44px.
> Copy: "DRIP is an Indian startup, built for Indian fashion lovers. We understand the difference between a Banarasi silk and a Kanjivaram, between a Pathani and a Sherwani. We're not a Western app localised for India — we're India-first from day one."
>
> Below: Two outlined gold pills: "Bengaluru, Karnataka" and "Est. 2025"
>
> ---
>
> ## SECTION 6 — TEAM (placeholder)
> Background `#13131A`. py-24. Max-w-7xl mx-auto px-6.
>
> Label "THE TEAM" gold uppercase. Headline "Small team. Big mission." Cormorant 36px.
>
> 3 team placeholder cards in a row (stack mobile). Each: surface `#0A0A0F` border `#2A2A35` rounded-2xl p-6 text-center. Gold circle avatar (80px, initials). Name Cormorant 20px. Role muted DM Sans 13px. Short one-line bio muted 12px. LinkedIn icon link (muted, gold on hover).
> - "RS" — "Rahul S." — "Founder & CEO" — "Previously built e-com products used by 2M+ users."
> - "AP" — "Ananya P." — "Head of Design" — "5 years of UX at India's leading fashion brands."
> - "VK" — "Vikram K." — "ML Engineer" — "Computer vision researcher with 3 published papers."
>
> Below team: "We're building the team. Join us →" — muted link with arrow. Clicking: smooth scroll to contact section.
>
> ---
>
> ## SECTION 7 — PRESS & RECOGNITION (placeholder)
> Background `#0A0A0F`. py-16. Max-w-7xl mx-auto px-6. Text center.
>
> "AS FEATURED IN" label muted uppercase 11px. Row of 5 placeholder press logo boxes (surface `#13131A` border `#2A2A35` rounded-xl px-6 py-3 muted text DM Sans 14px): "YourStory" / "Inc42" / "The Ken" / "TechCrunch India" / "Economic Times". Grayscale appearance (opacity 0.5), gold on hover. Filter: grayscale(100%) on default, grayscale(0%) on hover.
>
> ---
>
> ## SECTION 8 — CONTACT / CTA
> Background `#13131A`. py-24. Max-w-3xl mx-auto px-6. Text center.
>
> Headline "Get in touch." Cormorant 44px.
>
> 3 contact cards in a row (stack mobile), each: outlined gold border rounded-2xl p-6:
> - "General Inquiries" — hello@drip.ai — copy icon
> - "Press & Media" — press@drip.ai — copy icon
> - "Partnerships & Brands" — brands@drip.ai — copy icon
>
> Clicking copy icon: copies email + toast "Copied!"
>
> Below: Big gold CTA "Try DRIP Free →" → tryon.html
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS: Navbar scroll. Mobile hamburger. Copy email buttons + toast. IntersectionObserver: fade-up animation on each section as it enters viewport (translateY 30px → 0, opacity 0 → 1, 600ms ease-out).

---

---

# PROMPT 16 — PROFILE SETTINGS
**File: profile-settings.html**

---

> Build a complete, production-ready, fully responsive **Profile Settings page** for DRIP in a single HTML file. All data read/written from localStorage drip_user. Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> Redirect to auth.html on page load if drip_user is null (not logged in).
>
> ---
>
> ## NAVBAR — same as all pages (with user avatar dropdown)
>
> ---
>
> ## PAGE HEADER
> Background `#13131A`. py-12. Max-w-7xl centered px-6.
> Breadcrumb: "Account / Profile Settings" muted 12px.
> "Account Settings" Cormorant Garamond 40px.
>
> ---
>
> ## LAYOUT — Two column: Left nav (sidebar 280px) + Right content. Stacked mobile.
>
> ### SETTINGS SIDEBAR (left)
> Surface `#13131A` border `#2A2A35` rounded-2xl p-4 sticky top-24.
>
> User card at top: Gold avatar (56px, initials from drip_user.name). Name Cormorant 20px. Email muted 13px. Small "Verified ✓" green badge.
>
> Navigation links (each: full-width, rounded-xl py-3 px-4, hover surface bg `#2A2A35`, active: gold border-left 3px + gold text):
> - 👤 Profile Info (default active)
> - 🔒 Security & Login
> - 🔔 Notifications
> - 🎨 Style Preferences
> - 📍 Saved Addresses
> - 🛍 My Orders → orders.html
> - ❌ Danger Zone
>
> Clicking each: JS shows/hides corresponding content panel on the right with fade transition.
>
> ---
>
> ### CONTENT PANELS (right)
>
> #### PANEL 1 — Profile Info (default visible)
>
> Section heading "Profile Information" Cormorant 28px. Subtext "Update your personal details." muted 14px.
>
> Profile photo section: Current avatar (80px gold circle, initials). "Change Photo" button (outlined gold small) + "Remove" muted link. Clicking Change Photo: hidden file input triggers, photo preview updates to uploaded image (FileReader API), save button activates.
>
> Form grid (2-col desktop, 1-col mobile):
> - Full Name (pre-filled from localStorage)
> - Display Name (optional, "How should we call you?")
> - Email (pre-filled, gold "Verified ✓" badge inline right of input)
> - Phone (+91 prefix, pre-filled if exists)
> - Date of Birth (date input, styled custom)
> - Gender (custom radio pills: Male / Female / Non-binary / Prefer not to say)
> - City (text input)
> - State (custom select, all Indian states)
>
> All inputs: dark surface, `#2A2A35` border, gold focus border + glow, rounded-xl, DM Sans 14px.
>
> "Save Changes" gold filled button right-aligned. On click: validates, saves to localStorage drip_user, shows inline success toast "Profile updated ✓" green. Button enters loading state (spinner, "Saving...") for 1 second, then success.
>
> "Last updated: Jan 15, 2025" muted 12px below button.
>
> ---
>
> #### PANEL 2 — Security & Login (hidden)
>
> "Security & Login" Cormorant 28px.
>
> **Connected Accounts:** "Google" row — Google icon + "Connected as rahul@gmail.com" + green "Active" badge + "Disconnect" muted link (clicking: confirm modal "This will log you out. Continue?" — red confirm button).
>
> **Magic Link Email:** Current email display + "Change Email" gold link. Clicking: inline form slides down with new email input + "Send Verification →" button. Note: "A verification link will be sent to both addresses."
>
> **Active Sessions:** "Logged in devices" label. Table with 2 rows:
> - "This device — Chrome, Windows — Mumbai, India — Active now" + no action
> - "Mobile — Safari, iPhone — Delhi, India — 3 days ago" + "Log Out" red text button
> "Log Out All Other Devices" outlined red button below table.
>
> ---
>
> #### PANEL 3 — Notifications (hidden)
>
> "Notification Preferences" Cormorant 28px.
>
> Each row: label left (DM Sans 14px primary) + description below (muted 12px) + toggle switch right (custom CSS pill toggle, gold when on, `#2A2A35` when off). Gap between rows: border-bottom `#2A2A35`.
>
> Rows:
> - "Order Updates" / "Shipping, delivery, and status changes" — ON by default
> - "New Outfit Drops" / "Fresh outfits in your preferred categories" — ON
> - "Style Tips Emails" / "Weekly newsletter with fashion guides" — ON
> - "Try-On Reminders" / "Reminder when you have free tries available" — OFF
> - "Promotional Offers" / "Discount codes and special sales" — OFF
> - "WhatsApp Notifications" / "Order updates on WhatsApp" — OFF. Clicking ON: shows phone number input if not set.
>
> "Save Preferences" gold filled button. On save: 1 second loading → toast "Preferences saved ✓".
>
> ---
>
> #### PANEL 4 — Style Preferences (hidden)
>
> "Your Style Preferences" Cormorant 28px. Subtext "We use these to personalise your outfit recommendations." muted.
>
> **Preferred Categories:** Multi-select pill grid. Pills: Men's Ethnic / Western Casuals / Women's Sarees / Lehengas / Plus-Size / Fusion / Formal / Streetwear / Athleisure. Active: gold bg dark text. Inactive: dark border muted text. Toggle on click.
>
> **Occasions:** Same pill style. Wedding Guest / Daily Casual / Office / Festival / Date Night / Party / Travel.
>
> **Budget Range:** Custom dual-handle slider. "₹0" to "₹10,000+". Gold track. Show selected range: "₹500 — ₹3,000" below slider updating live.
>
> **Preferred Brands:** Checkboxes (same style as Explore filter). Top 10 Indian brands listed.
>
> **Size Preferences:** Two rows: "Top Size" (XS/S/M/L/XL/XXL pill selector) + "Bottom Size" (28/30/32/34/36 pill selector).
>
> "Save Preferences" gold button. Saves to localStorage drip_user.preferences.
>
> ---
>
> #### PANEL 5 — Saved Addresses (hidden)
>
> "Saved Addresses" Cormorant 28px.
>
> Existing address cards (read from drip_user.addresses[]): Each: surface card `#0A0A0F` border `#2A2A35` rounded-2xl p-5. Radio button left (selecting sets as default). Address content: Name bold, address lines, phone, "Default" green badge if default. "Edit" gold link + "Delete" muted link per card. Edit: expands inline form (same fields as checkout delivery form). Delete: confirm then removes from array.
>
> "+ Add New Address" outlined gold button full-width rounded-2xl dashed border. Clicking: new address form slides in below. Form: same fields as checkout. "Save Address" gold filled + "Cancel" muted. On save: pushes to drip_user.addresses[], re-renders list.
>
> Max 5 addresses. If 5 exist: "Add New Address" button is disabled + tooltip "Maximum 5 addresses saved."
>
> ---
>
> #### PANEL 6 — Danger Zone (hidden)
>
> "Danger Zone" Cormorant 28px brandError color.
>
> Red-tinted card: `rgba(224, 90, 90, 0.05)` background, border `rgba(224, 90, 90, 0.3)`, rounded-2xl p-6.
>
> Row 1: "Download My Data" — "Export all your data including orders, saved looks, and profile info." — "Download Data" outlined muted button. On click: generates JSON blob of all localStorage drip_* keys and triggers download as `DRIP-data-export.json`.
>
> Divider.
>
> Row 2: "Delete My Account" — "This permanently deletes your account, all saved looks, orders history, and profile data. This cannot be undone." — "Delete Account" red outlined button. On click: confirm modal: type "DELETE" in an input to enable the confirm button. On confirm: clears all drip_* localStorage keys, toast "Account deleted." red, redirect to landing.html after 2 seconds.
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS BEHAVIORS
> 1. Settings sidebar nav: click → fade content panel switch
> 2. Profile photo upload: FileReader → preview avatar
> 3. All form saves: validate → 1s loading → toast → localStorage update
> 4. Toggle switches: custom CSS + JS click handler
> 5. Disconnect Google: confirm modal
> 6. Log out other sessions: confirm → toast
> 7. Address CRUD: add/edit (inline form expand) / delete (confirm)
> 8. Style preference pills multi-select
> 9. Budget range dual slider live update
> 10. Data download: JSON blob + trigger download
> 11. Delete account: type "DELETE" gates confirm button + full clear + redirect

---

---

# PROMPT 17 — 404 ERROR PAGE
**File: 404.html**

---

> Build a complete, production-ready, fully responsive **404 Error page** for DRIP in a single HTML file. Tailwind CSS CDN, vanilla JS.
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> This page should feel on-brand, charming, and turn a frustrating moment into a conversion opportunity. Fashion-themed copy throughout.
>
> ---
>
> ## NAVBAR — same as all pages
>
> ---
>
> ## MAIN CONTENT (full viewport height minus navbar, flex column center)
>
> Background `#0A0A0F` with very subtle radial gradient gold glow centered.
>
> **"404" display:** Cormorant Garamond, font-size clamp(120px, 20vw, 200px). Font-weight 300. Color: transparent with background-clip text — gradient from `#C9A84C` to `#2A2A35`. Displays as a large elegant gold-fading number.
>
> **Headline below:** "This outfit went out of stock." Cormorant Garamond 32px primary. (Fashion pun for 404)
>
> **Subtext:** "The page you're looking for doesn't exist or has been moved. But we've got 10,000+ outfits that definitely do." Muted DM Sans 15px. Max-w-md text-center.
>
> **Two CTA buttons (side by side, stack mobile):**
> - "Browse Outfits →" gold filled large pill → explore.html
> - "✨ Try Something On" gold outlined large pill → tryon.html
>
> **"You might like these" section below buttons:**
> Label: "While you're here, try these →" muted 13px.
> 3 outfit cards (compact, same design as Explore page cards, randomly picked from picsum 40–60). Each has "Try On" button. Horizontal row, gap-6.
>
> **Animated element:** A CSS-animated hanger SVG (gold outline, 60px) that gently swings on a pendulum (CSS transform-origin top center, rotate -15deg → 15deg → -15deg, 2s ease-in-out infinite). Positioned above the 404 text.
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS: Navbar scroll. Mobile hamburger. No other JS needed.

---

---

# PROMPT 18 — SEARCH RESULTS PAGE
**File: search-results.html**

---

> Build a complete, production-ready, fully responsive **Search Results page** for DRIP in a single HTML file. Tailwind CSS CDN, vanilla JS. All data simulated (no backend).
>
> [PASTE FULL DESIGN SYSTEM BLOCK HERE]
>
> On page load: read query from URL param `?q=` and display it. If no param: show a search-focused landing state (trending searches + recent).
>
> ---
>
> ## NAVBAR — same as all pages. Search bar in navbar is always visible (not just on explore).
> On this page: navbar search bar is pre-filled with the query from ?q= URL param. Submitting a new search: updates URL param + re-filters results.
>
> ---
>
> ## SEARCH HEADER
> Background `#13131A`. py-12. Max-w-7xl mx-auto px-6.
>
> Large search bar (hero size): Dark surface input, gold focus border, rounded-2xl, py-4 px-6, DM Sans 16px. Search icon inside left (gold). Clear × inside right. Pre-filled with query. Below: "Showing 24 results for 'white kurta'" muted DM Sans 14px. If no results: "No results for 'xyz'" with suggestions.
>
> **Trending searches strip (shown below search bar always):**
> Label "Trending:" muted 12px. Horizontal scroll of pill tags: "Wedding Kurta 🔥" / "White Saree" / "Office Casuals" / "Navratri Outfit" / "Slim Fit Jeans" / "Bandhgala". Clicking a tag: updates search bar + filters results.
>
> **Recent searches (shown if localStorage drip_searches has entries):**
> Label "Your recent searches:" muted 12px. Horizontal pills with × to remove each. Clicking: runs that search.
>
> ---
>
> ## RESULTS TABS
> Border-bottom `#2A2A35`. Two tabs: "Outfits (18)" and "Style Guides (6)". Same gold underline active tab style. Tab counts update based on results.
>
> ---
>
> ## OUTFITS TAB (default active)
>
> Same filter sidebar + grid layout as explore.html. Filters are pre-applied based on the search context (if search is "wedding kurta", category "Men's Ethnic" is auto-checked).
>
> Grid: same outfit cards as explore.html.
>
> Show 18 simulated outfit cards matching the demo query "white kurta". Outfit names, brands, prices similar to explore.html.
>
> **Relevance indicator on each card:** Small "95% match" or "87% match" green text below outfit name. Simulated — just hardcode varying percentages.
>
> **"Sort by relevance" as default sort option** (in addition to Trending, Newest, Price).
>
> ---
>
> ## STYLE GUIDES TAB (hidden by default)
>
> Same blog post cards as blog-index.html. Show 6 cards. Each has the outfit conversion strip below ("Try looks from this article →").
>
> ---
>
> ## EMPTY STATE (shown when 0 results — trigger with search query "xxxxxxx")
>
> Centered content: Search with × icon (gold, 64px). "'xxxxxxx' — We couldn't find that." Cormorant 28px. "Try these instead:" muted DM Sans 14px. Trending searches pills (same as header strip). Below: "Or browse all outfits →" gold link.
>
> **"Did you mean...?" suggestion row:** If query is close to a known term (simple JS distance check on hardcoded array), show "Did you mean: 'white kurta'?" gold link.
>
> ---
>
> ## FOOTER — same as all pages
>
> ---
>
> ## JS BEHAVIORS
> 1. Read ?q= URL param on load → pre-fill search bar + filter results
> 2. Search bar submit → update URL param (history.pushState) + re-filter
> 3. Tab switching (Outfits / Style Guides)
> 4. Trending tag click → update search
> 5. Recent searches: save to drip_searches localStorage on each search, show as pills, × to remove
> 6. "Did you mean" simple fuzzy match against hardcoded popular terms array
> 7. All filters + sort work same as explore.html (reuse logic)

---

---

# COMPLETE localStorage REFERENCE (updated — use this in all pages)

```javascript
drip_user: {
  name: string,
  email: string,
  phone: string,
  avatar: string (base64 or null),
  dob: string,
  gender: string,
  city: string,
  state: string,
  addresses: [{id, name, line1, line2, city, state, pin, phone, isDefault}],
  preferences: {
    categories: [],
    occasions: [],
    budgetMin: 0,
    budgetMax: 10000,
    brands: [],
    topSize: string,
    bottomSize: string
  },
  notifications: {
    orderUpdates: true,
    newDrops: true,
    styleEmails: true,
    reminders: false,
    promos: false,
    whatsapp: false
  },
  createdAt: string
}

drip_saved:    [{outfitId, resultImg, outfitName, brand, price, savedAt}]
drip_wishlist: [outfitId, ...]
drip_cart:     [{outfitId, name, brand, price, originalPrice, size, color, qty, image, affiliateUrl}]
drip_orders:   [{orderId, date, items[], subtotal, discount, delivery, coupon, total, status, address{}, payment{}, deliveryDate, timeline[]}]
drip_tries:    {date: "YYYY-MM-DD", count: number}
drip_recent:   [outfitId, ...]  (max 10, FIFO)
drip_history:  [{outfitId, resultImg, timestamp}]  (max 50, FIFO)
drip_searches: [string, ...]  (max 10, FIFO)
```

---

# COMPLETE FILE LIST — ALL 19 FILES

```
CORE (13)                        STATUS
landing.html                     ✅ Built
explore.html                     ✅ Prompted
outfit.html                      ✅ Prompted
tryon.html                       ✅ Prompted
blog-index.html                  ✅ Prompted
blog-post.html                   ✅ Prompted
auth.html                        ✅ Prompted
dashboard.html                   ✅ Prompted
components.html                  ✅ Prompted
cart.html                        ✅ Prompted
checkout.html                    ✅ Prompted
order-success.html               ✅ Prompted
orders.html                      ✅ Prompted

MISSING — NOW PROMPTED (6)       STATUS
privacy.html                     ✅ Prompted (Prompt 14)
terms.html                       ✅ Prompted (Prompt 14)
affiliate-disclosure.html        ✅ Prompted (Prompt 14)
about.html                       ✅ Prompted (Prompt 15)
profile-settings.html            ✅ Prompted (Prompt 16)
404.html                         ✅ Prompted (Prompt 17)
search-results.html              ✅ Prompted (Prompt 18)

TOTAL: 20 files (3 in 1 prompt = 18 prompts total)
```

---

# 4 GAP FIXES FOR ALREADY-PROMPTED PAGES

When building pages 2 (explore.html) and 3 (outfit.html), add these to your Gemini prompts:

**Gap Fix 1 — Add "Add to Bag" button to explore.html outfit cards:**
Add a 3rd button to each outfit card action row (after "Try On" and "Buy Now"):
"🛍 Add to Bag" — dark surface bg, gold border, rounded-full, text-xs, px-3 py-1.5.
On click: push item to drip_cart localStorage + open floating cart drawer + show toast "Added to bag!".

**Gap Fix 2 — Add "Add to Bag" to outfit.html CTA row:**
Below the "Try This On Me" and "Buy Now" buttons, add:
"🛍 Add to Bag — ₹X,XXX" — outlined gold full-width rounded-2xl. Same localStorage + drawer + toast behavior.

**Gap Fix 3 — Add cart icon to navbar in prompts 2–9:**
In navbar right side, before Login/avatar, add: shopping bag SVG icon (muted, gold on hover) with live count badge (gold circle, reads drip_cart.length). Clicking opens floating cart drawer.

**Gap Fix 4 — Add "Add to Bag" to tryon.html result action bar:**
4th button in the result action row: "🛍 Add to Bag" (dark surface, gold border, flex-1, rounded-xl py-3). On click: adds current outfit to drip_cart + opens cart drawer + toast.
