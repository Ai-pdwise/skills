---
name: email-build-components
description: Complete HTML component library for the email build system. Contains production-ready code for all 23 reusable email modules — structure components (preheader, headers, footers), conversion components (CTA, stacked CTA, testimonial card, stats row, video thumbnail, objection callout, before/after, guarantee badge, urgency bar, pricing box), and design elevation components (hero overlay, side-by-side cards, step timeline, icon rows, pull quote stripe, Google reviews, signature block, trust pill). Read this file after Email_Build_PROMPT.md and Email_Build_SKILL.md when assembling an email.
---

# Email Build — COMPONENTS

Full HTML code for every reusable email component. Each component includes an editorial and/or branded variant where applicable. Replace placeholder values (wrapped in `{CURLY_BRACES}`) with actual brand tokens from the SKILL.md brand profile.

---

## 1. Preheader

Hidden text that shows in the inbox preview. The `&zwnj;&nbsp;` string pads out the preview so email clients don't pull body text.

```html
<div style="display: none; font-size: 1px; line-height: 1px; max-height: 0px; max-width: 0px; opacity: 0; overflow: hidden; mso-hide: all;">
  {PREHEADER_TEXT}
  &zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;
</div>
```

---

## 2. Header (Editorial)

Centred logo with light/dark mode swap. Logo links to website.

```html
<tr>
  <td align="center" style="padding: 0 0 40px 0;">
    <a href="{WEBSITE_URL}" target="_blank" style="text-decoration: none;">
      <img src="{LOGO_LIGHT_URL}" alt="{BRAND_NAME}" width="160" class="logo-light" style="display: block; width: 160px; max-width: 160px; height: auto;">
      <img src="{LOGO_DARK_URL}" alt="{BRAND_NAME}" width="160" class="logo-dark" style="display: none; width: 160px; max-width: 160px; height: auto;">
    </a>
  </td>
</tr>
```

---

## 3. Header (Branded)

Centred logo on white background. No dark mode swap needed.

```html
<tr>
  <td align="center" style="padding: 30px 40px 20px 40px; background-color: #ffffff;">
    <img src="{LOGO_URL}" alt="{BRAND_NAME}" width="200" style="display: block; border: 0;">
  </td>
</tr>
```

---

## 4. Footer (Editorial)

Minimal footer: small logo, legal links (• separated), copyright, address, view-in-browser.

```html
<!-- Divider -->
<tr>
  <td align="center" style="padding: 0 40px 40px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <tr>
        <td style="border-top: 1px solid #e2dfdd;"></td>
      </tr>
    </table>
  </td>
</tr>

<!-- Footer Logo -->
<tr>
  <td align="center" style="padding: 0 0 24px 0;">
    <a href="{WEBSITE_URL}" target="_blank" style="text-decoration: none;">
      <img src="{LOGO_FOOTER_LIGHT_URL}" alt="{BRAND_NAME}" width="80" class="logo-light" style="display: block; width: 80px; max-width: 80px; height: auto; opacity: 0.6;">
      <img src="{LOGO_FOOTER_DARK_URL}" alt="{BRAND_NAME}" width="80" class="logo-dark" style="display: none; width: 80px; max-width: 80px; height: auto; opacity: 0.6;">
    </a>
  </td>
</tr>

<!-- Footer Links -->
<tr>
  <td align="center" style="padding: 0 40px 16px 40px;">
    <p style="margin: 0; font-family: {FONT_STACK}; font-weight: 400; font-size: 12px; line-height: 1.5; color: #7a7876; white-space: nowrap;">
      <a href="{PRIVACY_URL}" target="_blank" style="color: #7a7876 !important; text-decoration: underline;">Privacy Policy</a>
      <span style="color: #7a7876;">&nbsp;&nbsp;•&nbsp;&nbsp;</span>
      <a href="{TERMS_URL}" target="_blank" style="color: #7a7876 !important; text-decoration: underline;">Terms & Conditions</a>
      <span style="color: #7a7876;">&nbsp;&nbsp;•&nbsp;&nbsp;</span>
      <a href="{{unsubscribe_link}}" target="_blank" style="color: #7a7876 !important; text-decoration: underline;">Unsubscribe</a>
    </p>
  </td>
</tr>

<!-- Copyright -->
<tr>
  <td align="center" style="padding: 0 40px 8px 40px;">
    <p style="margin: 0; font-family: {FONT_STACK}; font-weight: 400; font-size: 12px; line-height: 1.5; color: #7a7876;">
      © {YEAR} {BRAND_NAME}. All rights reserved.
    </p>
  </td>
</tr>

<!-- Address -->
<tr>
  <td align="center" style="padding: 0 40px 16px 40px;">
    <p style="margin: 0; font-family: {FONT_STACK}; font-weight: 400; font-size: 12px; line-height: 1.5; color: #7a7876;">
      <!--[if mso]><span style="color: #7a7876;"><![endif]-->
      <span style="color: #7a7876 !important; text-decoration: none !important;">{ADDRESS}</span>
      <!--[if mso]></span><![endif]-->
    </p>
  </td>
</tr>

<!-- View in Browser -->
<tr>
  <td align="center" style="padding: 0 40px 40px 40px;">
    <a href="{{email.viewInBrowser}}" target="_blank" style="font-family: {FONT_STACK}; font-weight: 400; font-size: 12px; line-height: 1.5; color: #7a7876; text-decoration: underline;">View this email in browser</a>
  </td>
</tr>
```

---

## 5. Footer (Branded)

Coloured background footer with logo, legal links, and unsubscribe.

```html
<tr>
  <td style="padding: 24px 40px; background-color: {BRAND_PRIMARY}; text-align: center;">
    <img src="{LOGO_URL}" alt="{BRAND_NAME}" width="160" style="display: inline-block; border: 0; margin-bottom: 16px;">
    <p style="margin: 0 0 8px 0; font-size: 12px; color: #ffffff;">
      © {YEAR} {BRAND_NAME}
    </p>
    <p style="margin: 0 0 8px 0; font-size: 12px; color: #ffffff;">
      <a href="{TERMS_URL}" style="color: #ffffff; text-decoration: underline;">Terms &amp; Conditions</a> &nbsp;|&nbsp;
      <a href="{PRIVACY_URL}" style="color: #ffffff; text-decoration: underline;">Privacy Policy</a>
    </p>
    <p style="margin: 0; font-size: 12px; color: #ffffff;">
      <a href="{{email.unsubscribe_link}}" style="color: #ffffff; text-decoration: underline;">Unsubscribe</a>
    </p>
  </td>
</tr>
```

---

## 6. CTA Button

### Editorial (left-aligned, black, uppercase)

```html
<tr>
  <td align="left" class="content-padding" style="padding: 0 40px 40px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0">
      <tr>
        <td align="left">
          <a href="{CTA_URL}" target="_blank" style="font-family: {FONT_STACK}; font-weight: 700; font-size: 13px; line-height: 1; letter-spacing: 0.09em; text-transform: uppercase; color: #ffffff; background-color: #1e1e1e; padding: 16px 32px; text-decoration: none; display: inline-block; white-space: nowrap;">
            ▸ {CTA_TEXT}
          </a>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

### Branded (centred, brand colour, rounded)

```html
<tr>
  <td align="center" style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0">
      <tr>
        <td align="center" style="background-color: {BRAND_PRIMARY}; border-radius: 6px;">
          <a href="{CTA_URL}" target="_blank" style="font-family: Arial, Helvetica, sans-serif; font-weight: 700; font-size: 16px; color: #ffffff; padding: 14px 32px; text-decoration: none; display: inline-block;">
            {CTA_TEXT}
          </a>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 7. Stacked CTA

Primary button with a softer secondary text link underneath. Gives the reader two commitment levels.

```html
<tr>
  <td align="{ALIGN}" class="content-padding" style="padding: 0 40px 40px 40px;">
    <!-- Primary Button -->
    <table role="presentation" cellspacing="0" cellpadding="0" border="0">
      <tr>
        <td align="{ALIGN}">
          <a href="{CTA_PRIMARY_URL}" target="_blank" style="font-family: {FONT_STACK}; font-weight: 700; font-size: 13px; line-height: 1; letter-spacing: 0.09em; text-transform: uppercase; color: #ffffff; background-color: {BUTTON_BG}; padding: 16px 32px; text-decoration: none; display: inline-block; white-space: nowrap;">
            {CTA_PRIMARY_TEXT}
          </a>
        </td>
      </tr>
    </table>
    <!-- Secondary Link -->
    <p style="margin: 12px 0 0 0; font-family: {FONT_STACK}; font-size: 14px; color: #7a7876;">
      or <a href="{CTA_SECONDARY_URL}" target="_blank" style="color: #7a7876; text-decoration: underline;">{CTA_SECONDARY_TEXT}</a>
    </p>
  </td>
</tr>
```

---

## 8. Testimonial Card

Quote with attribution. Optional star rating and photo.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color: #f8fafa; border-radius: 8px;">
      <tr>
        <td style="padding: 24px;">
          <!-- Star Rating (optional) -->
          <p style="margin: 0 0 12px 0; font-size: 18px; color: #FBBC04; letter-spacing: 1px;">★★★★★</p>
          <!-- Quote -->
          <p style="margin: 0 0 16px 0; font-family: {FONT_STACK}; font-size: 15px; font-style: italic; line-height: 1.6; color: {TEXT_COLOR};">
            "{TESTIMONIAL_QUOTE}"
          </p>
          <!-- Attribution -->
          <table role="presentation" cellspacing="0" cellpadding="0" border="0">
            <tr>
              <!-- Photo (optional — remove this td if no photo) -->
              <td valign="middle" style="padding-right: 12px;">
                <img src="{TESTIMONIAL_PHOTO_URL}" alt="{TESTIMONIAL_NAME}" width="40" height="40" style="display: block; width: 40px; height: 40px; border-radius: 50%; object-fit: cover;">
              </td>
              <td valign="middle">
                <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; font-weight: 700; color: {HEADING_COLOR};">
                  {TESTIMONIAL_NAME}
                </p>
                <p style="margin: 2px 0 0 0; font-family: {FONT_STACK}; font-size: 13px; color: #7a7876;">
                  {TESTIMONIAL_TITLE}
                </p>
              </td>
            </tr>
          </table>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 9. Stats / Metrics Row

2–4 key numbers displayed horizontally. Adjust column count and widths as needed.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <tr>
        <td width="33%" align="center" valign="top" style="padding: 16px 8px;">
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 28px; font-weight: 700; color: {ACCENT_COLOR}; line-height: 1.2;">
            {STAT_1_NUMBER}
          </p>
          <p style="margin: 6px 0 0 0; font-family: {FONT_STACK}; font-size: 13px; color: #7a7876; line-height: 1.4;">
            {STAT_1_LABEL}
          </p>
        </td>
        <td width="33%" align="center" valign="top" style="padding: 16px 8px; border-left: 1px solid #e2dfdd;">
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 28px; font-weight: 700; color: {ACCENT_COLOR}; line-height: 1.2;">
            {STAT_2_NUMBER}
          </p>
          <p style="margin: 6px 0 0 0; font-family: {FONT_STACK}; font-size: 13px; color: #7a7876; line-height: 1.4;">
            {STAT_2_LABEL}
          </p>
        </td>
        <td width="33%" align="center" valign="top" style="padding: 16px 8px; border-left: 1px solid #e2dfdd;">
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 28px; font-weight: 700; color: {ACCENT_COLOR}; line-height: 1.2;">
            {STAT_3_NUMBER}
          </p>
          <p style="margin: 6px 0 0 0; font-family: {FONT_STACK}; font-size: 13px; color: #7a7876; line-height: 1.4;">
            {STAT_3_LABEL}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 10. Video Thumbnail with Play Button

An image that looks like a video player with a centred play button overlay. The entire thing links to the video URL. Uses a table overlay technique for maximum compatibility.

```html
<tr>
  <td align="center" style="padding: 0 40px 30px 40px;">
    <a href="{VIDEO_URL}" target="_blank" style="text-decoration: none;">
      <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
          <td align="center" style="position: relative; background-image: url('{VIDEO_THUMBNAIL_URL}'); background-size: cover; background-position: center; border-radius: 8px; overflow: hidden;">
            <!--[if mso]>
            <v:rect xmlns:v="urn:schemas-microsoft-com:vml" fill="true" stroke="false" style="width:480px;height:270px;">
              <v:fill type="frame" src="{VIDEO_THUMBNAIL_URL}" />
              <v:textbox inset="0,0,0,0">
            <![endif]-->
            <div style="background-image: url('{VIDEO_THUMBNAIL_URL}'); background-size: cover; background-position: center; width: 100%; height: 270px; display: table; border-radius: 8px;">
              <div style="display: table-cell; vertical-align: middle; text-align: center; background: rgba(0,0,0,0.3);">
                <!-- Play Button Circle -->
                <table role="presentation" cellspacing="0" cellpadding="0" border="0" align="center">
                  <tr>
                    <td align="center" valign="middle" style="width: 64px; height: 64px; background-color: rgba(255,255,255,0.9); border-radius: 50%;">
                      <span style="font-size: 28px; color: #1e1e1e; margin-left: 4px;">▶</span>
                    </td>
                  </tr>
                </table>
              </div>
            </div>
            <!--[if mso]>
              </v:textbox>
            </v:rect>
            <![endif]-->
          </td>
        </tr>
      </table>
    </a>
    <!-- Optional caption -->
    <p style="margin: 10px 0 0 0; font-family: {FONT_STACK}; font-size: 13px; color: #7a7876;">
      {VIDEO_CAPTION}
    </p>
  </td>
</tr>
```

---

## 11. Objection-Handling Callout Box

Addresses a common hesitation directly. Uses a left accent border for visual weight.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <tr>
        <td style="border-left: 4px solid {ACCENT_COLOR}; padding: 16px 20px; background-color: #f8fafa;">
          <p style="margin: 0 0 6px 0; font-family: {FONT_STACK}; font-size: 14px; font-weight: 700; color: {HEADING_COLOR};">
            {OBJECTION_HEADING}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 15px; line-height: 1.6; color: {TEXT_COLOR};">
            {OBJECTION_RESPONSE}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Example usage:**
- Heading: "Worried it won't work for your industry?"
- Response: "We've built systems across 40+ verticals — from pilates studios to property inspection firms. The framework adapts; the results are consistent."

---

## 12. Before / After Comparison

Two-column block showing a transformation. Works for results, process changes, lifestyle shifts.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <tr>
        <!-- Before -->
        <td width="48%" valign="top" style="background-color: #fdf5f5; border-radius: 8px; padding: 20px; text-align: center;">
          <p style="margin: 0 0 8px 0; font-family: {FONT_STACK}; font-size: 11px; font-weight: 600; letter-spacing: 0.5px; color: #c0392b; text-transform: uppercase;">
            Before
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {BEFORE_TEXT}
          </p>
        </td>
        <!-- Spacer -->
        <td width="4%"></td>
        <!-- After -->
        <td width="48%" valign="top" style="background-color: #f0faf5; border-radius: 8px; padding: 20px; text-align: center;">
          <p style="margin: 0 0 8px 0; font-family: {FONT_STACK}; font-size: 11px; font-weight: 600; letter-spacing: 0.5px; color: #27ae60; text-transform: uppercase;">
            After
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {AFTER_TEXT}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 13. Guarantee / Risk-Reversal Badge

Trust-building module. Centred badge with a shield/checkmark and guarantee text.

```html
<tr>
  <td align="center" style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" style="background-color: #f8fafa; border-radius: 8px; border: 1px solid #e2dfdd;">
      <tr>
        <td style="padding: 20px 28px;" align="center">
          <p style="margin: 0 0 8px 0; font-size: 24px;">🛡️</p>
          <p style="margin: 0 0 6px 0; font-family: {FONT_STACK}; font-size: 15px; font-weight: 700; color: {HEADING_COLOR};">
            {GUARANTEE_HEADLINE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: #7a7876;">
            {GUARANTEE_DETAIL}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Example:** Headline: "No Risk, No Obligation" / Detail: "Your first two consultations are completely free. You only pay if you choose to proceed with treatment."

---

## 14. Urgency Bar

Full-width strip with an expiry notice. Use sparingly and honestly — fake urgency damages trust.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color: {BRAND_PRIMARY}; border-radius: 8px;">
      <tr>
        <td style="padding: 16px 24px;" align="center">
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 15px; font-weight: 600; color: #ffffff;">
            ⏳ {URGENCY_TEXT}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Example:** "This offer expires in 5 days — book your free consultation before Friday."

---

## 15. Pricing / Offer Highlight Box

Featured offer with optional original price (struck through), sale price, and CTA.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color: #f8fafa; border-radius: 8px; border: 2px solid {ACCENT_COLOR};">
      <tr>
        <td style="padding: 28px;" align="center">
          <p style="margin: 0 0 8px 0; font-family: {FONT_STACK}; font-size: 11px; font-weight: 600; letter-spacing: 0.5px; color: {ACCENT_COLOR}; text-transform: uppercase;">
            {OFFER_LABEL}
          </p>
          <p style="margin: 0 0 4px 0; font-family: {FONT_STACK}; font-size: 14px; color: #7a7876;">
            <s>{ORIGINAL_PRICE}</s>
          </p>
          <p style="margin: 0 0 12px 0; font-family: {FONT_STACK}; font-size: 32px; font-weight: 700; color: {HEADING_COLOR};">
            {SALE_PRICE}
          </p>
          <p style="margin: 0 0 20px 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {OFFER_DESCRIPTION}
          </p>
          <!-- Inline CTA -->
          <table role="presentation" cellspacing="0" cellpadding="0" border="0">
            <tr>
              <td align="center" style="background-color: {BUTTON_BG}; border-radius: 6px;">
                <a href="{CTA_URL}" target="_blank" style="font-family: {FONT_STACK}; font-weight: 700; font-size: 15px; color: #ffffff; padding: 14px 28px; text-decoration: none; display: inline-block;">
                  {CTA_TEXT}
                </a>
              </td>
            </tr>
          </table>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 16. Hero Image with Text Overlay

Full-width background image with centred text. Includes VML fallback for Outlook.

```html
<tr>
  <td align="center" style="padding: 0 0 40px 0;">
    <!--[if mso]>
    <v:rect xmlns:v="urn:schemas-microsoft-com:vml" fill="true" stroke="false" style="width:560px;height:280px;">
      <v:fill type="frame" src="{HERO_IMAGE_URL}" />
      <v:textbox inset="0,0,0,0">
    <![endif]-->
    <div style="background-image: url('{HERO_IMAGE_URL}'); background-size: cover; background-position: center; width: 100%; max-width: 560px; height: 280px; display: table;">
      <div style="display: table-cell; vertical-align: middle; text-align: center; padding: 40px; background: linear-gradient(to bottom, rgba(0,0,0,0.25) 0%, rgba(0,0,0,0.45) 50%, rgba(0,0,0,0.25) 100%);">
        <p style="margin: 0; font-family: {FONT_STACK}; font-weight: 500; font-size: 28px; line-height: 1.3; letter-spacing: -0.02em; color: #ffffff; text-shadow: 0 2px 4px rgba(0,0,0,0.5);">
          {HERO_TEXT}
        </p>
      </div>
    </div>
    <!--[if mso]>
      </v:textbox>
    </v:rect>
    <![endif]-->
  </td>
</tr>
```

---

## 17. Side-by-Side Cards

Two equal-width cards. Use for 2-item comparisons (consultations, plans, options). Do not use for 3+ items — use the Step Timeline instead.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellpadding="0" cellspacing="0" border="0" width="100%">
      <tr>
        <!-- Card 1 -->
        <td width="48%" valign="top" style="background-color: #f8fafa; border-radius: 8px; padding: 24px; text-align: center;">
          <p style="margin: 0 0 12px 0; font-family: {FONT_STACK}; font-size: 11px; font-weight: 600; letter-spacing: 0.5px; color: {ACCENT_COLOR}; text-transform: uppercase;">
            {CARD_1_LABEL}
          </p>
          <p style="margin: 0 0 12px 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
            {CARD_1_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {CARD_1_BODY}
          </p>
        </td>
        <!-- Spacer -->
        <td width="4%"></td>
        <!-- Card 2 -->
        <td width="48%" valign="top" style="background-color: #f8fafa; border-radius: 8px; padding: 24px; text-align: center;">
          <p style="margin: 0 0 12px 0; font-family: {FONT_STACK}; font-size: 11px; font-weight: 600; letter-spacing: 0.5px; color: {ACCENT_COLOR}; text-transform: uppercase;">
            {CARD_2_LABEL}
          </p>
          <p style="margin: 0 0 12px 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
            {CARD_2_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {CARD_2_BODY}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 18. Numbered Step Timeline

Vertical 1 → 2 → 3 process. Use for 3+ steps. Each step has a numbered circle, title, and description.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <!-- Step 1 -->
      <tr>
        <td width="48" valign="top" style="padding: 0 16px 24px 0;">
          <table role="presentation" cellspacing="0" cellpadding="0" border="0">
            <tr>
              <td align="center" valign="middle" style="width: 36px; height: 36px; background-color: {ACCENT_COLOR}; border-radius: 50%;">
                <p style="margin: 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: #ffffff;">1</p>
              </td>
            </tr>
          </table>
        </td>
        <td valign="top" style="padding: 0 0 24px 0;">
          <p style="margin: 0 0 4px 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
            {STEP_1_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 15px; line-height: 1.6; color: {TEXT_COLOR};">
            {STEP_1_DESCRIPTION}
          </p>
        </td>
      </tr>
      <!-- Step 2 -->
      <tr>
        <td width="48" valign="top" style="padding: 0 16px 24px 0;">
          <table role="presentation" cellspacing="0" cellpadding="0" border="0">
            <tr>
              <td align="center" valign="middle" style="width: 36px; height: 36px; background-color: {ACCENT_COLOR}; border-radius: 50%;">
                <p style="margin: 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: #ffffff;">2</p>
              </td>
            </tr>
          </table>
        </td>
        <td valign="top" style="padding: 0 0 24px 0;">
          <p style="margin: 0 0 4px 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
            {STEP_2_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 15px; line-height: 1.6; color: {TEXT_COLOR};">
            {STEP_2_DESCRIPTION}
          </p>
        </td>
      </tr>
      <!-- Step 3 -->
      <tr>
        <td width="48" valign="top" style="padding: 0 16px 0 0;">
          <table role="presentation" cellspacing="0" cellpadding="0" border="0">
            <tr>
              <td align="center" valign="middle" style="width: 36px; height: 36px; background-color: {ACCENT_COLOR}; border-radius: 50%;">
                <p style="margin: 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: #ffffff;">3</p>
              </td>
            </tr>
          </table>
        </td>
        <td valign="top" style="padding: 0;">
          <p style="margin: 0 0 4px 0; font-family: {FONT_STACK}; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
            {STEP_3_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 15px; line-height: 1.6; color: {TEXT_COLOR};">
            {STEP_3_DESCRIPTION}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

Add or remove `<tr>` step rows as needed. Keep the same structure for each.

---

## 19. Icon + Text Feature Rows

Service or benefit highlights. Uses emoji as the "icon" for maximum compatibility. Stack as many rows as needed.

```html
<tr>
  <td style="padding: 0 40px 30px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
      <!-- Row 1 -->
      <tr>
        <td width="40" valign="top" style="padding: 0 12px 20px 0;">
          <p style="margin: 0; font-size: 22px;">{ICON_1}</p>
        </td>
        <td valign="top" style="padding: 0 0 20px 0;">
          <p style="margin: 0 0 2px 0; font-family: {FONT_STACK}; font-size: 15px; font-weight: 700; color: {HEADING_COLOR};">
            {FEATURE_1_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {FEATURE_1_DESC}
          </p>
        </td>
      </tr>
      <!-- Row 2 -->
      <tr>
        <td width="40" valign="top" style="padding: 0 12px 20px 0;">
          <p style="margin: 0; font-size: 22px;">{ICON_2}</p>
        </td>
        <td valign="top" style="padding: 0 0 20px 0;">
          <p style="margin: 0 0 2px 0; font-family: {FONT_STACK}; font-size: 15px; font-weight: 700; color: {HEADING_COLOR};">
            {FEATURE_2_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {FEATURE_2_DESC}
          </p>
        </td>
      </tr>
      <!-- Row 3 -->
      <tr>
        <td width="40" valign="top" style="padding: 0 12px 0 0;">
          <p style="margin: 0; font-size: 22px;">{ICON_3}</p>
        </td>
        <td valign="top" style="padding: 0;">
          <p style="margin: 0 0 2px 0; font-family: {FONT_STACK}; font-size: 15px; font-weight: 700; color: {HEADING_COLOR};">
            {FEATURE_3_TITLE}
          </p>
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 14px; line-height: 1.5; color: {TEXT_COLOR};">
            {FEATURE_3_DESC}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 20. Pull Quote / Highlight Stripe

Full-width coloured band with a key statement. Use to break up long emails or emphasise a single point.

```html
<tr>
  <td style="padding: 0 0 30px 0;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color: {STRIPE_BG_COLOR};">
      <tr>
        <td style="padding: 28px 40px;" align="center">
          <p style="margin: 0; font-family: {FONT_STACK}; font-size: 18px; font-weight: 500; line-height: 1.5; color: {STRIPE_TEXT_COLOR}; letter-spacing: -0.01em;">
            {PULL_QUOTE_TEXT}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Colour suggestions:**
- Editorial: `#1e1e1e` bg / `#ffffff` text (inverted)
- Branded: `{BRAND_PRIMARY}` bg / `#ffffff` text
- Subtle: `#f8fafa` bg / `{HEADING_COLOR}` text

---

## 21. Google Review / Trust Badges

Star ratings with review count and link. Based on The Back Clinic pattern. Repeat the inner table for each location.

```html
<tr>
  <td style="padding: 20px 40px; background-color: #f8fafa; text-align: center; border-top: 1px solid #e8ecef;">
    <p style="margin: 0 0 6px 0; font-size: 16px; font-weight: 700; color: {HEADING_COLOR};">
      {TRUST_HEADLINE}
    </p>
    <p style="margin: 0 0 20px 0; font-size: 14px; color: {TEXT_COLOR};">
      {TRUST_SUBLINE}
    </p>
    
    <!-- Review Badge (repeat for each location) -->
    <table role="presentation" cellpadding="0" cellspacing="0" border="0" align="center" style="background-color: #ffffff; border: 1px solid #e8ecef; border-radius: 6px; padding: 12px 20px; margin-bottom: 12px;">
      <tr>
        <td valign="middle" style="padding-right: 8px;">
          <img src="https://www.google.com/favicon.ico" alt="Google" width="24" height="24" style="display: block; border: 0;">
        </td>
        <td valign="middle" style="padding-right: 6px;">
          <span style="font-size: 20px; font-weight: 700; color: {HEADING_COLOR};">{RATING}</span>
        </td>
        <td valign="middle" style="padding-right: 10px;">
          <span style="font-size: 18px; color: #FBBC04; letter-spacing: 1px;">★★★★★</span>
        </td>
        <td valign="middle" style="padding-right: 12px;">
          <span style="font-size: 14px; font-weight: 600; color: {HEADING_COLOR};">{LOCATION_NAME}</span>
        </td>
        <td valign="middle">
          <a href="{REVIEWS_URL}" target="_blank" style="font-size: 13px; color: #5A6A7A; text-decoration: underline;">Read {REVIEW_COUNT}+ reviews</a>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 22. Signature Block

Circular photo with name and title. Used when the email is from a specific person.

```html
<tr>
  <td align="left" class="content-padding" style="padding: 0 40px 48px 40px;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0">
      <tr>
        <td valign="middle" style="padding-right: 16px;">
          <img src="{SIGNATURE_PHOTO_URL}" alt="{SIGNATURE_NAME}" width="56" height="56" style="display: block; width: 56px; height: 56px; border-radius: 50%; object-fit: cover;">
        </td>
        <td valign="middle">
          <p style="margin: 0; font-family: {FONT_STACK}; font-weight: 500; font-size: 16px; line-height: 1.4; color: {HEADING_COLOR};">
            {SIGNATURE_NAME}
          </p>
          <p style="margin: 2px 0 0 0; font-family: {FONT_STACK}; font-weight: 400; font-size: 14px; line-height: 1.4; color: #7a7876;">
            {SIGNATURE_TITLE}
          </p>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

---

## 23. Trust Badge Pill

Small rounded badge placed above a heading. Used for social proof or key selling points.

```html
<table role="presentation" cellpadding="0" cellspacing="0" border="0" align="center" style="margin-bottom: 16px;">
  <tr>
    <td style="background-color: {BADGE_BG}; border-radius: 20px; padding: 8px 16px;">
      <span style="font-size: 13px; font-weight: 600; color: {HEADING_COLOR};">
        {BADGE_TEXT}
      </span>
    </td>
  </tr>
</table>
```

**Examples:**
- "✓ 4.9 Star Rating Across 400+ Google Reviews"
- "✓ Free First & Second Consultations"
- "✓ Trusted by 500+ Australian Businesses"
