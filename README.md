# POUCH Shopify Theme

This repository contains a Shopify Online Store 2.0 theme based on Dawn and customized for the POUCH storefront.

The current home page is intentionally built around one active homepage section:

- `templates/index.json` renders `sections/pouch-homepage.liquid`
- `sections/header.liquid` and `sections/footer.liquid` provide the global site chrome
- `sections/header-group.json` and `sections/footer-group.json` configure announcement/footer content

## Home Page

The active home page lives in `sections/pouch-homepage.liquid`. It includes:

- Hero messaging for the POUCH brand
- Product solution grid for Immunity+, Hydration+, SkinRevive+, and WellDrip+
- Brand story and science sections
- Medical support proof point
- VarietyPack+ comparison table
- FAQs
- POUCH 101 article links

The home page uses Shopify-native routes and objects where possible. Page links should use Liquid page references with fallbacks, for example:

```liquid
{{ pages['about-us'].url | default: '/pages/about-us' }}
```

Avoid hardcoded `.html` page paths in rendered storefront links.

## Product Data

Homepage product cards can be configured from the `pouch-homepage` section schema. If no product is selected in the theme editor, the section falls back to these product handles:

- `immunity`
- `hydration`
- `skinrevive`
- `welldrip`

Ingredient naming is standardized in the section defaults, including `VitAlign` and `AquaMin`.

## Legacy Redesign Assets

The repository also contains an experimental redesign grid:

- `sections/pouch-redesign-grid.liquid`
- `snippets/pouch-redesign-card.liquid`
- `assets/pouch_*.png`

This redesign section is not rendered by the current home page template. It has been kept as a reusable/experimental section, but the active homepage should remain `pouch-homepage` unless the template is intentionally changed.

## Development

Use Shopify CLI for local development and validation.

```bash
shopify theme dev
shopify theme check
```

Before committing theme changes, run:

```bash
shopify theme check
```

The current theme check baseline is clean: all inspected files pass with no offenses.

## Notes For Future Edits

- Keep the home page to a single rendered primary experience unless a duplicate section is intentional.
- Do not add debug text or placeholder Dawn copy to rendered storefront sections.
- Prefer Shopify route helpers and resource URLs over hardcoded storefront paths.
- Keep homepage section numbering continuous.
- Make mobile behavior explicit when desktop interactions depend on hover.

## License

This theme is based on Shopify Dawn. See [LICENSE.md](LICENSE.md) for license details.
