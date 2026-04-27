# Cal.com Booking Embed — Design Spec
Date: 2026-04-28

## Goal
Replace non-functional "Boka samtal" buttons with a working Cal.com inline booking widget embedded at the bottom of the landing page. No external redirect — visitors book without leaving the site.

## Booking Service
- Provider: Cal.com (free, no client account required)
- Cal link: `yahya-shihabe/30min`
- Availability managed by Yahya via Cal.com dashboard, synced to calendar

## Changes to index.html

### 1. Button behavior
Three existing buttons use `href="#BOOKING" target="_blank"`. Change all to `href="#boka"` (anchor scroll, no new tab).

Affected elements:
- `#nav-cta` (nav bar)
- `#hero-cta` (hero section)
- `#final-cta` (footer CTA section)

### 2. Remove BOOKING_URL JS swap
Delete the script block at bottom of file:
```js
const BOOKING_URL = 'https://calendar.app.google/REPLACE_ME';
document.querySelectorAll('[href="#BOOKING"]').forEach(el => {
  el.href = BOOKING_URL;
});
```

### 3. Booking section
Existing "Boka ett samtal" section already has heading and calendar icon. Add `id="boka"` to the section element for anchor targeting. Replace placeholder content below the heading with the Cal.com inline widget div:
```html
<div id="cal-booking" style="min-height:600px;"></div>
```

### 4. Cal.com embed script
Add before closing `</body>`:
```html
<script type="text/javascript">
(function (C, A, L) {
  let p = function (a, ar) { a.q.push(ar); };
  let d = C.document;
  C.Cal = C.Cal || function () {
    let cal = C.Cal; let ar = arguments;
    if (!cal.loaded) {
      cal.ns = {}; cal.q = cal.q || [];
      d.head.appendChild(d.createElement("script")).src = A;
      cal.loaded = true;
    }
    if (ar[0] === L) {
      const api = function () { p(api, arguments); };
      const namespace = ar[1];
      api.q = api.q || [];
      typeof namespace === "string"
        ? (cal.ns[namespace] = api) && p(api, ar)
        : p(cal, ar);
      return;
    }
    p(cal, ar);
  };
})(window, "https://app.cal.com/embed/embed.js", "init");

Cal("init", { origin: "https://cal.com" });
Cal("inline", {
  elementOrSelector: "#cal-booking",
  calLink: "yahya-shihabe/30min",
});
Cal("ui", {
  theme: "light",
  styles: { branding: { brandColor: "#2D5F4E" } },
});
</script>
```

Brand color `#2D5F4E` matches site's forest green.

## Out of Scope
- Multiple event durations (one 30-min type is sufficient for now)
- Custom domain for Cal.com
- Cal.com → CRM integration
