---
name: email-build-skill
description: Design system and technical reference for the email build system. Contains style types (editorial and branded), brand profiles with all colour/logo/URL tokens, spacing scale, dark mode CSS, head boilerplate, reset CSS, responsive CSS, GoHighLevel merge tags, the full component index, and Outlook/MSO compatibility notes. Read this file after Email_Build_PROMPT.md and before Email_Build_COMPONENTS.md when building any HTML email.
---

# Email Build — SKILL

Technical reference for building production-ready HTML emails. This file covers the design system, brand architecture, platform rules, and component index. Full HTML code for each component lives in `Email_Build_COMPONENTS.md`.

---

## 1. Style Types

Every client email falls into one of two style types. The user specifies which when briefing the brand.

### Editorial Style
Clean, minimal, text-forward. Feels like a personal email from a founder or strategist. White background, no coloured sections, generous whitespace. Content is left-aligned.

**Reference emails:** Pointdot (trillion, case studies)

| Token | Value |
|---|---|
| Container width | 560px |
| Background | `#ffffff` (wrapper AND container) |
| Wrapper padding | `40px 16px` |
| Content padding | `0 40px` (desktop), `0 24px` (mobile) |
| Text alignment | Left |
| Font stack | `'Aeonik Pro', 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif` |
| Body text | 16px / 1.6 / 400 weight / `#1e1e1e` |
| Bold text | 700 weight / `#1e1e1e` |
| Heading | 32px / 1.15 / 400 weight / `-0.02em` tracking / `#1e1e1e` |
| Subheading | 20px / 1.4 / 400 weight / `-0.02em` tracking / `#444342` |
| Label (uppercase) | 12px / 1.4 / 500 weight / `0.09em` tracking / `#7a7876` / uppercase |
| Footer text | 12–13px / 1.5 / 400 weight / `#7a7876` |
| Divider | `1px solid #e2dfdd` |
| CTA button | `#1e1e1e` bg, `#ffffff` text, 13px / 700 weight / `0.09em` tracking / uppercase / `16px 32px` padding / no border-radius |
| CTA hover | `background-color: {brand_accent}` (defined per client) |
| Link colour | `#7a7876` underline |
| Link hover | `{brand_accent}` |

### Branded Style
Visually rich, centre-aligned, uses the client's brand colour prominently in sections and the footer. Trust-focused with badges, review cards, and coloured CTA boxes.

**Reference emails:** The Back Clinic (welcome, what-to-expect)

| Token | Value |
|---|---|
| Container width | 600px |
| Outer background | `#f4f4f4` |
| Container background | `#ffffff` with `border-radius: 8px; overflow: hidden` |
| Wrapper padding | `20px 10px` |
| Content padding | `0 40px` |
| Text alignment | Centre |
| Font stack | `Arial, Helvetica, sans-serif` |
| Body text | 16px / 1.6 / `#5A6A7A` |
| Heading | 28px / 700 weight / 1.3 / `#1E2B3A` |
| Subheading | 20px / 700 weight / `{brand_primary}` |
| Card label | 11px / 600 weight / `0.5px` tracking / `{brand_primary}` / uppercase |
| Card title | 16px / 700 weight / `#1E2B3A` |
| Card body | 14px / 1.5 / `#5A6A7A` |
| Card background | `#f8fafa` with `border-radius: 8px` and `padding: 24px` |
| Trust badge | `{brand_primary_light}` bg / `border-radius: 20px` / `8px 16px` padding |
| CTA box | `{brand_primary}` bg / `#ffffff` text / `border-radius: 8px` / `padding: 24px` |
| Footer | `{brand_primary}` bg / `#ffffff` text / `padding: 24px 40px` |
| Bold accent | `#1E2B3A` (used for emphasised lines within `#5A6A7A` body text) |
| Divider | `1px solid #e8ecef` |

---

## 2. Brand Profile Template

When the user briefs a new client brand, capture these values. Everything else inherits from the style type above.

```
Brand name:        ___
Style type:        editorial | branded
Primary colour:    ___ (hex)
Secondary colour:  ___ (hex, optional)
Accent colour:     ___ (hex, for hover states / highlights — editorial only)
Primary light:     ___ (hex, tinted version of primary for badge backgrounds — branded only)
Logo URL (light):  ___
Logo URL (dark):   ___ (editorial only — for dark mode swap)
Logo URL (footer): ___ (if different size/version)
CTA text default:  ___ (e.g. "Book a Clarity Call", "Get Started")
CTA URL default:   ___
Signature name:    ___ (if emails come from a person)
Signature title:   ___
Signature photo:   ___ (URL)
Address:           ___
Privacy URL:       ___
Terms URL:         ___
Website URL:       ___
```

### Known Brand Profiles

**Pointdot** (editorial)
- Primary: `#1e1e1e`
- Accent: `#a78423`
- Logo light: `https://assets.cdn.filesafe.space/gMGCFsfRwgCmewdPK2pI/media/69b5417bbfc81f5e8e0ee206.png` (160px header)
- Logo dark: `https://assets.cdn.filesafe.space/gMGCFsfRwgCmewdPK2pI/media/69b5417beba4874f5c42de52.png`
- Logo footer light: `https://assets.cdn.filesafe.space/gMGCFsfRwgCmewdPK2pI/media/69b5417bbfc81f0cce0ee205.png` (80px, 0.6 opacity)
- Logo footer dark: `https://assets.cdn.filesafe.space/gMGCFsfRwgCmewdPK2pI/media/69b5417b277ba0f9a7f0629e.png`
- CTA: `▸ Book a Clarity Call` → `https://link.pdwise.com.au/widget/bookings/pointdotclaritycall`
- Signature: Dimitri Galanis / Founder & Director / `https://assets.cdn.filesafe.space/gMGCFsfRwgCmewdPK2pI/media/69b5551dcab7f7443dcea05a.jpg`
- Address: 106 Homer Street, Earlwood NSW 2206
- Privacy: `https://pointdot.com.au/privacy-policy`
- Terms: `https://www.pointdot.com.au/terms-conditions/`
- Website: `https://pointdot.com.au`

**The Back Clinic** (branded)
- Primary: `#2b9f6d`
- Primary light: `#E8F8F3`
- Accent text: `#22C997` (subheadings, card labels)
- Dark text: `#1E2B3A`
- Body text: `#5A6A7A`
- Logo: `https://assets.cdn.filesafe.space/J6rqbJwJU4JpVps6tlVP/media/6912c50a96d06ae4d75fe653.png` (200px header, 160px footer)
- CTA: contextual (no single default)
- Bankstown Reviews: 4.8 ★ / 220+ reviews / `https://share.google/DaAuSO4bJAwFHQL4Y`
- Rockdale Reviews: 4.9 ★ / 175+ reviews / `https://share.google/mxTJQdRiUaKQ360jo`
- Privacy: `https://offer.thebackclinic.net.au/privacy-policy/`
- Terms: `https://offer.thebackclinic.net.au/terms-and-conditions/`

---

## 3. Spacing Scale

Use these values consistently. Do not invent spacing values.

| Use | Value |
|---|---|
| Between paragraphs in body copy | `20px` bottom padding on `<td>` |
| Between sections / modules | `30–40px` bottom padding on `<td>` |
| After bold subhead before paragraph | `8px` bottom padding on subhead `<td>` |
| After heading | `16–20px` bottom margin or padding |
| Card internal padding | `24px` |
| Side-by-side card gap | `4%` width spacer `<td>` |
| Before CTA button | `32px` bottom padding on preceding `<td>` |
| After CTA button | `40px` bottom padding on CTA `<td>` |
| Signature to divider | `48px` bottom padding on signature `<td>` |
| Divider to footer logo | `40px` bottom padding on divider `<td>` |
| Footer items stacking | `8–16px` between each footer row |

---

## 4. Dark Mode Protection (Always Include)

This CSS block goes inside `<style>` in the `<head>`. It prevents email clients from inverting colours. Replace colour values with the brand's actual tokens.

```css
/* Dark Mode Prevention */
:root {
  color-scheme: light;
  supported-color-schemes: light;
}

@media (prefers-color-scheme: dark) {
  body, table, td { background-color: #ffffff !important; }
  h1, h2, h3, h4, h5, h6, p, td, div, span { color: #1e1e1e !important; }
  a { color: #7a7876 !important; }
  .logo-light { display: none !important; }
  .logo-dark { display: block !important; }
}

/* Gmail / Outlook App Dark Mode */
[data-ogsc] body, [data-ogsc] table, [data-ogsc] td { background-color: #ffffff !important; }
[data-ogsc] p, [data-ogsc] td, [data-ogsc] div { color: #1e1e1e !important; }
[data-ogsc] a { color: #7a7876 !important; }
[data-ogsc] .logo-light { display: none !important; }
[data-ogsc] .logo-dark { display: block !important; }

[data-ogsb] body, [data-ogsb] table, [data-ogsb] td { background-color: #ffffff !important; }
[data-ogsb] p { color: #1e1e1e !important; }
[data-ogsb] a { color: #7a7876 !important; }
[data-ogsb] .logo-light { display: none !important; }
[data-ogsb] .logo-dark { display: block !important; }
```

Also include these meta tags in `<head>`:
```html
<meta name="color-scheme" content="light">
<meta name="supported-color-schemes" content="light">
```

For **branded style** emails that don't use a dark logo swap, you can omit the `.logo-light` / `.logo-dark` rules but still keep the background and text colour protections.

---

## 5. Head Boilerplate

Every email starts with this. Adjust `<title>` per email.

```html
<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="x-apple-disable-message-reformatting">
  <meta name="format-detection" content="telephone=no, date=no, address=no, email=no">
  <meta name="color-scheme" content="light">
  <meta name="supported-color-schemes" content="light">
  <title>{EMAIL_TITLE}</title>
  <!--[if mso]>
  <noscript>
    <xml>
      <o:OfficeDocumentSettings>
        <o:PixelsPerInch>96</o:PixelsPerInch>
      </o:OfficeDocumentSettings>
    </xml>
  </noscript>
  <![endif]-->
  <style>
    /* [INSERT: Reset CSS, typography classes, dark mode block, responsive media query] */
  </style>
</head>
```

---

## 6. Reset CSS (Always Include)

```css
body, table, td, a { -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
img { -ms-interpolation-mode: bicubic; border: 0; height: auto; line-height: 100%; outline: none; text-decoration: none; }
body { height: 100% !important; margin: 0 !important; padding: 0 !important; width: 100% !important; }
a[x-apple-data-detectors] { color: inherit !important; text-decoration: none !important; font-size: inherit !important; font-family: inherit !important; font-weight: inherit !important; line-height: inherit !important; }
```

---

## 7. Responsive CSS (Always Include)

```css
@media screen and (max-width: 600px) {
  .email-container {
    width: 100% !important;
    max-width: 100% !important;
  }
  .content-padding {
    padding-left: 24px !important;
    padding-right: 24px !important;
  }
}
```

---

## 8. GoHighLevel Merge Tags

| Tag | Use |
|---|---|
| `{{contact.first_name}}` | Personalised greeting |
| `{{contact.last_name}}` | Full name if needed |
| `{{contact.email}}` | Recipient email |
| `{{contact.phone}}` | Phone number |
| `{{unsubscribe_link}}` | Unsubscribe URL (primary format) |
| `{{email.unsubscribe_link}}` | Unsubscribe URL (alternate format — both work) |
| `{{email.viewInBrowser}}` | View in browser link |

---

## 9. Component Index

Full HTML for every component is in `Email_Build_COMPONENTS.md`. Here is the menu for quick reference:

### Structure Components
1. **Preheader** — hidden preheader text with whitespace padding
2. **Header (Editorial)** — centred logo with dark mode light/dark swap
3. **Header (Branded)** — centred logo on white background
4. **Footer (Editorial)** — logo, links (• separated), copyright, address, view-in-browser
5. **Footer (Branded)** — coloured background footer with logo, links, unsubscribe

### Conversion Components
6. **CTA Button** — primary action button (editorial: left-aligned black, branded: centred coloured)
7. **Stacked CTA** — primary button + secondary text link underneath
8. **Testimonial Card** — quote + name + optional photo + star rating
9. **Stats / Metrics Row** — 2–4 key numbers in a horizontal row
10. **Video Thumbnail** — image with play button overlay, linked to video URL
11. **Objection-Handling Callout** — addresses a common hesitation in a highlighted box
12. **Before / After Comparison** — two-column block showing transformation
13. **Guarantee / Risk-Reversal Badge** — trust symbol with guarantee text
14. **Urgency Bar** — expiry notice or countdown-style strip
15. **Pricing / Offer Highlight Box** — featured offer with price and CTA

### Design Elevation Components
16. **Hero Image with Text Overlay** — background image with centred text (VML fallback for Outlook)
17. **Side-by-Side Cards** — two equal-width cards (for 2-item comparisons, consultation steps, etc.)
18. **Numbered Step Timeline** — vertical 1 → 2 → 3 process (for 3+ steps)
19. **Icon + Text Feature Rows** — service or benefit highlights with emoji/icon and description
20. **Pull Quote / Highlight Stripe** — full-width coloured band with a key quote or statement
21. **Google Review / Trust Badges** — star ratings with review counts and links (Back Clinic pattern)
22. **Signature Block** — circular photo + name + title (editorial pattern)
23. **Trust Badge Pill** — small rounded badge above heading (e.g. "✓ 4.9 Star Rating")

---

## 10. Outlook / MSO Notes

- Background images require VML wrapping. See the Hero Image component in COMPONENTS.md for the full pattern.
- Addresses should be wrapped in MSO conditional spans to prevent Outlook from auto-linking them.
- Border-radius does not work in Outlook — the email will degrade gracefully to square corners.
- `max-width` does not work in MSO — use a fixed `width` attribute on the container table, plus a `max-width` inline style for modern clients.
- Avoid `margin` on block elements in Outlook — use `padding` on `<td>` elements instead.
