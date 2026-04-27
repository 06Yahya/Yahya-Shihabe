# Cal.com Booking Embed Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Embed a live Cal.com booking widget at the bottom of index.html and wire all three "Boka samtal" buttons to scroll to it.

**Architecture:** Single-file static site (index.html only). Three anchor buttons change from external-link to scroll-anchor. New `#boka` section added after the existing `#kontakt` CTA section containing the Cal.com inline widget. Cal.com embed JS added before `</body>`.

**Tech Stack:** HTML, Cal.com embed JS (loaded from app.cal.com CDN)

---

### Task 1: Fix nav-cta button

**Files:**
- Modify: `index.html:220-223`

- [ ] **Step 1: Edit nav-cta button**

In `index.html`, find line 220. Change the `<a>` tag from:
```html
<a id="nav-cta" href="#BOOKING" target="_blank" rel="noopener noreferrer"
   class="btn-cta btn-cta-sm">
  Boka samtal
</a>
```
To:
```html
<a id="nav-cta" href="#boka"
   class="btn-cta btn-cta-sm">
  Boka samtal
</a>
```

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "fix: nav-cta button scrolls to #boka section"
```

---

### Task 2: Fix hero-cta button

**Files:**
- Modify: `index.html:257-266`

- [ ] **Step 1: Edit hero-cta button**

Find line 257. Change the `<a>` tag from:
```html
<a id="hero-cta" href="#BOOKING" target="_blank" rel="noopener noreferrer"
   class="btn-cta btn-cta-lg">
```
To:
```html
<a id="hero-cta" href="#boka"
   class="btn-cta btn-cta-lg">
```

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "fix: hero-cta button scrolls to #boka section"
```

---

### Task 3: Fix final-cta button

**Files:**
- Modify: `index.html:701-705`

- [ ] **Step 1: Edit final-cta button**

Find line 701. Change the `<a>` tag from:
```html
<a id="final-cta" href="#BOOKING" target="_blank" rel="noopener noreferrer"
   class="inline-flex items-center gap-2 bg-white text-forest-dark font-semibold
          px-9 py-4 rounded-full text-base cursor-pointer
          hover:bg-cream transition-colors duration-200"
   style="font-family: 'Inter', sans-serif;">
```
To:
```html
<a id="final-cta" href="#boka"
   class="inline-flex items-center gap-2 bg-white text-forest-dark font-semibold
          px-9 py-4 rounded-full text-base cursor-pointer
          hover:bg-cream transition-colors duration-200"
   style="font-family: 'Inter', sans-serif;">
```

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "fix: final-cta button scrolls to #boka section"
```

---

### Task 4: Remove BOOKING_URL JS swap

**Files:**
- Modify: `index.html:744-750`

- [ ] **Step 1: Delete booking URL swap block**

Find the `<script>` block starting at line 743. Remove these lines only (leave the scroll reveal and nav scroll scripts intact):
```js
  // ── Booking URL ─────────────────────────────────────────
  // Change THIS one string when you have your Google Calendar URL:
  const BOOKING_URL = 'https://calendar.app.google/REPLACE_ME';

  document.querySelectorAll('[href="#BOOKING"]').forEach(el => {
    el.href = BOOKING_URL;
  });
```

The remaining script block should start directly with `// ── Scroll reveal`.

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "chore: remove unused BOOKING_URL JS swap"
```

---

### Task 5: Add booking section with Cal.com widget

**Files:**
- Modify: `index.html:718` (after `</main>`, before `</main>` closing — insert new section before it)

- [ ] **Step 1: Add #boka section**

Find line 718 (`</main>`). Insert the following block immediately before it (i.e., between the closing `</section>` of `#kontakt` at line 716 and `</main>` at line 718):

```html
<!-- ===================================================
     BOKA — Cal.com inline widget
==================================================== -->
<section id="boka" class="py-20 px-5 sm:px-8 bg-cream">
  <div class="max-w-3xl mx-auto">
    <div class="reveal text-center mb-10">
      <p class="text-sm text-muted uppercase tracking-[0.14em] font-bold mb-3">Välj en tid</p>
      <h2 class="font-display font-semibold text-forest-dark leading-tight tracking-[-0.015em]"
          style="font-size: clamp(1.75rem, 3.5vw, 2.5rem);">
        Boka ett gratis samtal.
      </h2>
    </div>
    <div id="cal-booking" style="min-height:600px;"></div>
  </div>
</section>
```

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "feat: add #boka section with Cal.com widget container"
```

---

### Task 6: Add Cal.com embed script

**Files:**
- Modify: `index.html:773` (before `</body>`)

- [ ] **Step 1: Add Cal.com embed script**

Find line 773 (`</body>`). Insert the following block immediately before it:

```html
<!-- Cal.com inline embed -->
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

- [ ] **Step 2: Verify in browser**

Open `index.html` in a browser (or check the Cloudflare Pages deployment). Verify:
1. Clicking any "Boka samtal" button scrolls to the booking section at the bottom.
2. Cal.com widget renders with available time slots.
3. Selecting a time slot shows the booking form.
4. Widget uses green brand color (`#2D5F4E`).

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: embed Cal.com booking widget (yahya-shihabe/30min)"
```
