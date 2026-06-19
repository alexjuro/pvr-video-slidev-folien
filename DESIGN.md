---
name: Informatics Creative Portfolio
colors:
  surface: '#f7f9fb'
  surface-dim: '#d8dadc'
  surface-bright: '#f7f9fb'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f4f6'
  surface-container: '#eceef0'
  surface-container-high: '#e6e8ea'
  surface-container-highest: '#e0e3e5'
  on-surface: '#191c1e'
  on-surface-variant: '#44474e'
  inverse-surface: '#2d3133'
  inverse-on-surface: '#eff1f3'
  outline: '#74777f'
  outline-variant: '#c4c6cf'
  surface-tint: '#4a5f85'
  primary: '#000f27'
  on-primary: '#ffffff'
  primary-container: '#0b2447'
  on-primary-container: '#778cb5'
  inverse-primary: '#b1c7f3'
  secondary: '#855300'
  on-secondary: '#ffffff'
  secondary-container: '#fea619'
  on-secondary-container: '#684000'
  tertiary: '#00120f'
  on-tertiary: '#ffffff'
  tertiary-container: '#002a25'
  on-tertiary-container: '#009d8d'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#d6e3ff'
  primary-fixed-dim: '#b1c7f3'
  on-primary-fixed: '#011b3e'
  on-primary-fixed-variant: '#32476c'
  secondary-fixed: '#ffddb8'
  secondary-fixed-dim: '#ffb95f'
  on-secondary-fixed: '#2a1700'
  on-secondary-fixed-variant: '#653e00'
  tertiary-fixed: '#71f8e4'
  tertiary-fixed-dim: '#4fdbc8'
  on-tertiary-fixed: '#00201c'
  on-tertiary-fixed-variant: '#005048'
  background: '#f7f9fb'
  on-background: '#191c1e'
  surface-variant: '#e0e3e5'
typography:
  headline-xl:
    fontFamily: Playfair Display
    fontSize: 48px
    fontWeight: '700'
    lineHeight: '1.2'
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Playfair Display
    fontSize: 32px
    fontWeight: '600'
    lineHeight: '1.3'
  headline-lg-mobile:
    fontFamily: Playfair Display
    fontSize: 28px
    fontWeight: '600'
    lineHeight: '1.3'
  headline-md:
    fontFamily: Playfair Display
    fontSize: 24px
    fontWeight: '600'
    lineHeight: '1.4'
  body-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.6'
  label-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '600'
    lineHeight: '1.2'
    letterSpacing: 0.05em
  label-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '500'
    lineHeight: '1.2'
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  unit: 8px
  container-max: 1280px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 64px
---

## Brand & Style
The design system bridges the gap between technical rigor and creative expression. It is tailored for high-level informatics professionals who need to demonstrate both data precision and visionary thinking. The personality is **Sophisticated, Warm, and Intellectual**.

The style utilizes **Soft Minimalism** mixed with **Glassmorphism**. By moving away from sterile, flat blocks toward layered, translucent surfaces and organic background blurs, the interface feels inviting and premium. The goal is to evoke a sense of "curated expertise" rather than "automated data."

## Colors
The palette is anchored by a deep professional navy, but softened through the strategic use of warm amber and sophisticated teal.

- **Primary (Navy):** Used for core branding, deep text, and structural anchors.
- **Secondary (Amber):** Used sparingly as a "warmth" trigger—highlights, call-to-actions, and active states.
- **Tertiary (Teal):** Used for data visualization elements and subtle interactive accents to provide a creative edge.
- **Background Strategy:** Avoid solid fills. Use soft linear gradients (e.g., Navy to a slightly lighter tint) and layered surface tiers to create depth.

## Typography
This design system employs a high-contrast typographic pairing to signal both heritage and modernity.

- **Headlines:** Playfair Display provides an editorial, premium feel. It should be used for page titles and major section headers.
- **Body & UI:** Inter ensures maximum readability for complex informatics data and long-form professional descriptions.
- **Styling Note:** Headlines benefit from slightly tighter letter-spacing to feel more "designed." Labels should use increased tracking and uppercase styling when used for small navigation elements or categories.

## Layout & Spacing
The layout follows a **Fluid Grid** model with generous white space to allow the "creative" elements room to breathe.

- **Grid:** A 12-column system for desktop, collapsing to 4 columns for mobile.
- **Rhythm:** Spacing follows an 8px base unit. Use larger vertical gaps (80px–120px) between major sections to emphasize the "portfolio" editorial feel.
- **Fluidity:** Incorporate "organic" offsets—elements should not always be perfectly flush with the grid; subtle 16px-32px shifts in image placement or background decorations can enhance the creative narrative.

## Elevation & Depth
Depth is communicated through **Glassmorphism and Ambient Shadows** rather than stark borders.

- **Surface Layers:** Main content areas sit on semi-transparent glass cards (White @ 70% opacity) with a `20px` backdrop blur. 
- **Shadows:** Use highly diffused shadows with a hint of the Primary Navy color (e.g., `box-shadow: 0 20px 40px rgba(11, 36, 71, 0.08)`).
- **Interactive Depth:** On hover, elements should "lift" by increasing shadow spread and slightly decreasing the backdrop-blur transparency to feel more tactile.

## Shapes
The shape language is purposefully soft to counteract the clinical nature of informatics. 

- **Corners:** Standard UI elements (cards, inputs) use a 16px (`rounded-lg`) radius. 
- **Large Containers:** Use 24px (`rounded-xl`) for main portfolio item containers.
- **Fluid Elements:** Incorporate "blob" or "organic" SVG shapes in the background with low-opacity gradients of Teal and Amber to break the rigidity of the grid.

## Components
Consistent execution across components reinforces the "Warm Professional" aesthetic.

- **Buttons:** Primary buttons use a subtle gradient of Primary Navy to a slightly lighter blue. Secondary buttons should be glass-styled with a Teal border.
- **Chips/Tags:** Use rounded-pill shapes with soft Tertiary (Teal) or Secondary (Amber) backgrounds at 10% opacity and dark text for categorizing skills or tools.
- **Cards:** Portfolio cards must feature the 16px corner radius, a subtle ambient shadow, and a glassmorphism header area.
- **Input Fields:** Maintain high contrast for focus states using a 2px Teal border, but keep the default state soft with a light grey-blue stroke.
- **Data Viz:** Charts should utilize the Teal and Amber accents against the Navy background for maximum "creative" impact without losing professional clarity.