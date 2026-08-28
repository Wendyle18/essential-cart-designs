# Essential Cart Drawer: Skeuomorphic Silver Glass

A CSS-only visual treatment for the Essential Cart Drawer. The implementation transforms the existing drawer into a polished silver-glass interface with tactile controls, layered depth, soft highlights, and responsive behavior without moxqdifying the generated HTML.

## Visual presentation

### Animated walkthrough

<p align="center">
  <a href="https://drive.google.com/file/d/1gUBtw1I9POgR8I8P6rAmVuOJx3cFwfY9/view?usp=sharing">
    <img width="936" alt="Animated walkthrough of the Essential Cart Drawer skeuomorphic design" src="https://drive.google.com/uc?export=view&id=1gUBtw1I9POgR8I8P6rAmVuOJx3cFwfY9" />
  </a>
</p>

If the animation does not load inside GitHub's image proxy, [open the GIF presentation in Google Drive](https://drive.google.com/file/d/1gUBtw1I9POgR8I8P6rAmVuOJx3cFwfY9/view?usp=sharing).

### Full cart drawer

<p align="center">
  <img width="936" height="1575" alt="Summer Essentials storefront showing the skeuomorphic Essential Cart Drawer" src="https://github.com/user-attachments/assets/e3130e26-71ad-4670-ae02-4cd31639af9e" />
</p>

## Design direction

The drawer uses a cold-luxury, silver skeuomorphic language inspired by precision hardware and translucent interface materials. It combines:

- Frosted surfaces with layered translucent fills
- Bright edge highlights and restrained blue-gray shadows
- Recessed tracks and tactile raised controls
- Consistent rounded geometry across cards and inputs
- A muted slate accent for progress, selected states, and checkout actions
- Compact spacing that preserves the cart's information hierarchy

This is a web-based glass and skeuomorphic treatment built with CSS. It is not an implementation of Apple's native Liquid Glass material.

## Implementation principles

| Constraint | Implementation |
| --- | --- |
| Existing HTML cannot be edited | All styling is applied through CSS selectors only |
| Generated utility classes may change | Selectors use the stable drawer root and `data-essential-cart-element` attributes |
| App styles have high specificity | The repeated `#cart-drawer` root intentionally wins the cascade |
| `!important` should be avoided | Specificity is used first; narrow exceptions are reserved for inline styles |
| The drawer must remain responsive | Mobile rules retain a full-width drawer with stable inner spacing |
| Blur may be unavailable or undesirable | Solid-surface and reduced-transparency fallbacks are included |

## Styled surfaces

- Drawer shell, header, title, and close control
- Reward goal card, progress track, fill, and milestone
- Product line items, images, prices, quantity controls, and remove actions
- Recommended-product upsell module and navigation
- Discount-code and order-note disclosures
- Subtotal, agreement control, and secure checkout action
- Third-party loyalty card treatment
- Keyboard focus, reduced-motion, and reduced-transparency states

## Installation

1. Add [`skeuomorphism-cart-drawer.css`](./skeuomorphism-cart-drawer.css) to the storefront's theme or custom CSS area.
2. Ensure it loads after Essential Cart Drawer's generated stylesheet.
3. Keep the existing `#cart-drawer` root and `data-essential-cart-element` attributes unchanged.
4. Clear the storefront cache and test the drawer with multiple products, discounts, and quantities.

No HTML or JavaScript changes are required.

## Design tokens

The main material settings are defined near the top of the stylesheet as CSS custom properties:

```css
--ec-glass-shell: rgba(237, 242, 249, 0.76);
--ec-glass-surface: rgba(252, 253, 255, 0.48);
--ec-glass-highlight: rgba(255, 255, 255, 0.92);
--ec-text: #111827;
--ec-text-muted: #687386;
--ec-accent: #64748b;
--ec-radius: 22px;
--ec-radius-control: 16px;
```

Adjust these tokens to refine the palette while keeping the component rules and hierarchy intact.

## Specificity strategy

Essential Cart Drawer can generate utility selectors with unusually high specificity. The repeated root selector is intentional:

```css
#cart-drawer#cart-drawer#cart-drawer#cart-drawer#cart-drawer#cart-drawer#cart-drawer.essential-cart-drawer-container
```

It keeps overrides scoped to the cart drawer and reduces the need for blanket `!important` declarations. Avoid replacing stable selectors with generated classes such as `.x1ghz6dp`, because those class names may change between builds.

## Accessibility and compatibility

- Visible `:focus-visible` outlines support keyboard navigation.
- `prefers-reduced-motion` shortens decorative transitions.
- `prefers-reduced-transparency` replaces translucent materials with solid surfaces.
- A no-`backdrop-filter` fallback keeps text and controls readable.
- Dynamic viewport units prevent mobile browser chrome from destabilizing the drawer height.

The material effect is intended for current versions of Chrome, Safari, Edge, and Firefox. Browsers without backdrop blur receive the solid fallback treatment.

## Files

- [`skeuomorphism-cart-drawer.css`](./skeuomorphism-cart-drawer.css): production CSS implementation
- [`review-follow-up-template.html`](./review-follow-up-template.html): local visual-review template
