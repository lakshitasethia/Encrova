# Unstructured.io — Landing Page Design Study

A comprehensive visual and technical analysis of the [unstructured.io](https://unstructured.io/) landing page, documenting its design system, gradient transitions, typography, color palette, and interactive elements.

---

## 1. Page Architecture — The Scroll Journey

The page follows a **three-act narrative structure** through background treatment:

````carousel
![Hero Section — Sky & Clouds (top of page)](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/hero_section.png)
<!-- slide -->
![Hero Video — Product demo in cinematic desk scene](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/hero_video.png)
<!-- slide -->
![Light Section — Pale blue/mint content area (~8400px)](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/light_section.png)
<!-- slide -->
![Transition Point — Light cards floating on dark starry sky (~9600px)](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/transition_point.png)
<!-- slide -->
![Dark Starry — Full immersion with content cards (~11400px)](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/dark_starry.png)
<!-- slide -->
![Footer — Dark starry sky continues to end](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/footer_section.png)
````

### Section Map (approximate scroll positions)

| Scroll Position | Section | Background |
|---|---|---|
| 0–500px | **Hero** — Headline + sky with clouds | Cyan sky `#87CEEB` gradient with floating cloud images |
| 500–1400px | **Hero Video** — Product demo on desk | Cinematic photo of a monitor on a desk (dark office scene) |
| 1400–2200px | **Trust Logos** — Enterprise customers | White/light background |
| 2200–3400px | **RAG Pipeline Diagram** — Interactive flow | Light cool gray `#F0F0F0` |
| 3400–5000px | **Features** — Accuracy, Document Types | Light lavender-blue `#E8ECF4` with gradient wash |
| 5000–6200px | **Testimonials** — Customer quotes | Clean white on cards |
| 6200–7400px | **Build vs Buy** — Video + copy | Pale blue-gray `#E2E8F0` |
| 7400–8800px | **UI & API Cards** — Interface options | Very pale mint `#EAF5F0` → lavender `#E8E0F0` |
| **8800–9600px** | **⚡ TRANSITION ZONE** | **Gradient shifts from light to deep navy starry sky** |
| 9600–10400px | **Partner Cards** — Databricks, IBM, etc. | Deep navy starry sky with white content cards |
| 10400–11000px | **Partners Text** + View Partners CTA | Starry sky background continues |
| 11000–11800px | **Ready for Demo** — CTA + workflow diagram | Starry sky with floating white/gradient cards |
| 11800–12400px | **Scrolling Marquee** — "Simplify Workflows ✦ Designed To Scale ✦ Built To Connect" | Full starry immersion |
| 12400–13200px | **Footer** — Newsletter, links, compliance | Dark navy `#0B1026` solid, no stars |

---

## 2. The Gradient Transition — Light to Starry (The Key Effect)

> [!IMPORTANT]
> This is the signature design move of the page. The transition happens at approximately **8800–9600px scroll depth**.

### How It Works

The page uses a **layered background system** with a fixed/absolute-positioned starry sky image underneath the entire page. The light sections are rendered as **opaque content containers that sit on top**, masking the starry sky below.

**The "reveal" technique:**

```
┌─────────────────────────────────────────┐
│  FIXED LAYER: Starry night sky image    │  ← Always present, behind everything
│  (deep navy #0B1A3E → #0B1026)         │
├─────────────────────────────────────────┤
│  CONTENT LAYER (scrolls normally):      │
│  ┌───────────────────────────────────┐  │
│  │  White/light sections with        │  │  ← These MASK the starry sky
│  │  bg-white or bg-primary-light     │  │
│  │  (opaque backgrounds)             │  │
│  └───────────────────────────────────┘  │
│                                         │
│  ← GAP: No opaque bg → stars show!  →  │  ← The "transition zone"
│                                         │
│  ┌───────────────────────────────────┐  │
│  │  Dark sections (transparent bg)   │  │  ← Content floats on stars
│  │  White text on starry sky         │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

### Visual Progression

1. **Light phase (0–8800px):** Content sections have opaque pale backgrounds (`bg-white`, pale lavender/mint gradients) that completely cover the starry sky beneath.

2. **Transition zone (~8800–9600px):** The last light-background section (UI & API cards) ends. There's a gap where no opaque container exists — the **starry sky gradually becomes visible** between the cards and the next section.

3. **Dark phase (9600px–end):** Content cards float on the starry background with transparent wrappers. White text and bordered cards sit directly over the stars. The background deepens progressively from a luminous navy with bright stars to a solid deep navy at the footer.

### CSS Implementation Details

The starry sky background is applied as a **full-screen fixed image** with classes like:
- `bg-primary-black` (the base dark color)
- A star-field image/SVG layered on top via `background-image` or a dedicated `<div>` with `position: fixed`
- The stars appear to twinkle — likely a subtle CSS animation or multiple star layers with different opacities

---

## 3. Color Palette

### Primary Colors

| Swatch | Name | Hex (approx) | Usage |
|---|---|---|---|
| 🟡 | **Accent Yellow** | `#F5E642` / `#FAEF6B` | CTA buttons ("Book A Demo"), nav highlights |
| 🟢 | **Accent Green/Mint** | `#86EFAC` / `#6EEAA0` | Primary action buttons ("Explore UI"), status indicators, code highlights |
| 🩷 | **Accent Pink/Magenta** | `#F0A0D0` / `#E879A8` | Secondary CTAs ("Contact Sales", "Explore API"), code block backgrounds |
| 🔵 | **Accent Blue** | `#7DD3FC` | Partner card (IBM), link highlights |

### Background Colors

| Swatch | Name | Hex (approx) | Usage |
|---|---|---|---|
| ⬛ | **Primary Black/Navy** | `#0B1026` → `#0B1A3E` | Navbar, dark sections, footer |
| ⬜ | **Primary Light** | `#F0F2F8` / `#EEF0F6` | Light section backgrounds |
| 🩵 | **Sky Blue** | `#87CEEB` | Hero sky gradient |
| 🔲 | **Card White** | `#FFFFFF` / `#F8F8F8` | Content cards |

### Navbar Tab Colors (a unique touch)

The nav items each have a **distinct pastel/vibrant background**:
- **Product:** `#A78BFA` (lavender/purple)
- **Problems We Solve:** `#60A5FA` (sky blue)
- **Resources:** `#34D399` (mint green)
- **Pricing:** `#FBBF24` (amber)
- **Partners:** `#F87171` (salmon red)

> [!TIP]
> The multi-colored nav tabs are a bold brand choice — each nav item has its own distinct color, creating a playful, "color-coded" navigation experience that feels like file tabs or sticky notes.

---

## 4. Typography

### Font Family

**Inter Tight** — loaded in weights 500 (Medium), 700 (Bold), and 800 (Extra Bold).

This is a narrow, geometric sans-serif from the Inter family, specifically designed for tight-fitting display text. It gives the page a modern, compressed, high-density editorial feel.

```css
font-family: "Inter Tight", sans-serif;
```

### Type Scale

| Element | Weight | Size (approx) | Style | Example |
|---|---|---|---|---|
| **Hero H1** | 800 (Extra Bold) | ~80–100px | Normal, tight tracking | "GenAI-Ready Data Starts Here" |
| **Section H2** | 800 (Extra Bold) | ~56–72px | Tight leading, dramatic | "Data delivered to your doorstep." |
| **Section H3** | 700 (Bold) | ~36–48px | — | "Interface options for everyone." |
| **Card Titles** | 700 (Bold) | ~24–28px | — | "UI", "API" |
| **Body Text** | 500 (Medium) | ~16–18px | Relaxed line height | Paragraph copy |
| **Nav Items** | 500 (Medium) | ~14–15px | — | "Product", "Pricing" |
| **Labels/Tags** | 500 (Medium) | ~12–14px | Bordered pill shape | "UI & API", "Try It Out Now" |
| **Marquee Text** | 800 (Extra Bold) | ~80–120px | ALL CAPS or Title Case, scrolling | "Simplify Workflows ✦ Designed To Scale" |

### Key Typographic Techniques

- **Huge, bold, punchy headlines** — The hero and section headings are extremely large and extra bold, creating visual impact
- **Serif accent in the "Build" section** — The phrase *"Just because you can build it, doesn't mean you should."* uses a **serif/italic font** (likely a display serif like a Playfair or similar), creating an editorial contrast
- **Tight tracking on headlines** — Letters are packed close together for density
- **Generous whitespace between sections** — Large padding (100–200px) between content blocks lets each section breathe

---

## 5. Video Implementation

### Hero Video
The hero section features a **product demo video** embedded in a cinematic photo of a desktop monitor setup:

![Hero Video — Product demo on monitor](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/hero_video.png)

- The video shows a **workflow builder UI** with Source → Partitioner → pipeline nodes
- It's wrapped in a **faux macOS window chrome** (red/yellow/green dots top-left)
- The video is embedded within a **desk photo** showing a real monitor, plant, coffee mug, mouse — creates a lifestyle/editorial feel
- Controls: **Pause (⏸) and Mute (🔇)** buttons in bottom-right corner
- Autoplay with muted audio

### Build vs Buy Video
Around the 7200px mark, there's a second video component:
- Housed in a macOS-style window frame (red/yellow/green dots)
- Shows a **data pipeline animation** with Storage → Custom Code/LangChain → Vector Storage flow
- Also has pause/mute controls

---

## 6. Interactive & Visual Elements

### Cards & Containers

The site uses a distinctive **card design** with:
- **Dotted/dashed borders** — Not solid borders, but `border-style: dashed` or dotted borders creating a blueprint/technical drawing feel
- **Slight rounded corners** — `border-radius: 8–12px`
- **White backgrounds** on dark sections — Cards float on the starry sky
- **Shadow effects** — Subtle box-shadows for depth

### Partner Cards Carousel

![Partner Cards — Color-coded brand integration](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/partner_cards.png)

Each partner has a **uniquely colored card** matching their brand:
- **Databricks:** Red `#EF4444`
- **Teradata:** Amber/Gold `#F59E0B`
- **IBM:** Sky Blue `#38BDF8`
- **NVIDIA:** Mint Green `#34D399`
- **MongoDB:** Red (same red family)

Cards are arranged in a **horizontal scrolling carousel** with arrow navigation (← →).

### Scrolling Marquee

![Scrolling Marquee — "Simplify Workflows ✦ Designed To Scale ✦ Built To Connect"](/Users/lakshitasethia/.gemini/antigravity-ide/brain/ee50858d-d572-4100-a14f-a9a58ce4f382/marquee_footer.png)

- Infinite horizontal scroll animation
- Extra Bold weight, massive font size (~100–120px)
- White text on starry background
- Separated by `✦` cross/plus symbols in mint/cyan
- CSS `animation: scroll linear infinite` or `@keyframes marquee`

### Logo/Brand Treatment

The "UNSTRUCTURED" logo is rendered as a **stacked monospace text block**:
```
U N S T
R U C T
U R E D
```
- Monospaced, letter-spaced characters
- Each letter on the grid, creating a 4×3 matrix
- White on dark, black on light

### Buttons & CTAs

Two button styles:
1. **Primary (Yellow):** `Book A Demo` — Solid yellow `#F5E642` background, black text, with an arrow icon (→⃝)
2. **Secondary (Pink):** `Contact Sales`, `For Developers` — Pink/magenta `#E879A8` background, black text, with eye icon (👀) or arrow
3. **Tertiary (Green/Mint):** `Explore UI`, pill-shaped — Green `#6EEAA0` background, black text
4. **Ghost/Outlined:** Various CTAs with border-only treatment and arrow icons

All buttons use **rounded corners** (pill/rounded-full on some, 8px radius on others) and include a **circle-arrow icon** (→ inside a circle).

---

## 7. Special Effects & Animations

| Effect | Location | Description |
|---|---|---|
| **Cloud parallax** | Hero (0–500px) | Floating cloud images create depth as page loads |
| **Marquee ticker** | Top bar | "Read More: Unstructured Leads in Document Parsing Quality" scrolls infinitely |
| **Video autoplay** | Hero + Build section | Muted autoplay with pause/mute controls |
| **Card hover states** | Partner cards, nav items | Likely scale/shadow transitions on hover |
| **Starfield twinkle** | Dark section (9600px+) | Stars appear at varying brightness/sizes, possibly animated |
| **Infinite scroll marquee** | Pre-footer (~12000px) | "Simplify Workflows ✦ Designed To Scale" scrolls continuously |
| **Cookie consent banner** | Bottom overlay | Slides up from bottom on first visit |

---

## 8. Footer Design

The footer sits on the **deepest part of the dark background** and contains:

- **Compliance bar:** FedRAMP High Certified, HIPAA Compliant, GDPR, SOC 2 Type II logos
- **Newsletter signup:** Email input + "Subscribe" button (cream/yellow background)
- **Quick Links grid:** 3-column layout — Homepage, Product, Problems We Solve, Pricing, Resources, Benchmarks, Careers, Blog, Webinars & Events, Press, Partners, Insights, Tutorials, Government, Docs
- **Social icons:** Slack, GitHub, Discord, LinkedIn, X (Twitter), YouTube — rendered in bordered card containers
- **Legal bar:** Privacy Policy, Cookie Notice, Your Privacy Choices toggle, Copyright ©2026

---

## 9. Summary — Key Design Takeaways

> [!NOTE]
> **The signature design technique** is the "light-to-starry" reveal — the starry sky background is always there underneath, but gets progressively uncovered as light-colored content sections end.

1. **Layered parallax background:** Fixed starry sky sits behind scrollable opaque content — creates a cinematic "reveal"
2. **Bold, oversized typography:** Inter Tight at Extra Bold, used at massive sizes for maximum punch
3. **Multi-color accent system:** Yellow, green, pink, blue used as accent colors — each with a specific function (primary CTA, secondary CTA, highlights, partner badges)
4. **Playful nav tabs:** Each nav item has its own color — feels like colored sticky tabs
5. **Dashed/dotted borders:** Cards and containers use dashed borders for a technical/blueprint aesthetic
6. **Video-forward storytelling:** Product demos embedded in lifestyle photography
7. **Generous whitespace:** Huge vertical padding between sections allows each to breathe
8. **Infinite marquee:** A classic web effect used at massive scale for visual drama at the bottom
