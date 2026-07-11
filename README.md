# legionforge.github.io

Source for the public marketing site at **[legionforge.org](https://legionforge.org/)**.

This is the mission landing + per-product landing pages for the LegionForge ecosystem. The documentation site lives separately at [docs.legionforge.org](https://docs.legionforge.org/) — source in [LegionForge/docs](https://github.com/LegionForge/docs).

## Layout

```
_config.yml             Jekyll config + site-wide product data
_layouts/
  default.html          Page shell — nav, footer, head metadata
  product.html          Product page template — hero + content + related grid
_includes/
  nav.html              Sticky top nav
  footer.html           Multi-column site footer
assets/css/site.css     All brand tokens + component styles

# Pages (one markdown file per URL)
index.md                /             Mission landing
framework.md            /framework/   LegionForge framework
guardian.md             /guardian/    Guardian security sidecar
jeli.md                 /jeli/        Jeli sovereign memory
adhd-os.md              /adhd-os/     ADHD-OS personal assistant
convobox.md             /convobox/    Voice frontend for CLI coding agents
briarios.md             /briarios/    Parallel agent orchestration meta-layer
intelligence-delivery-network.md  /intelligence-delivery-network/  LLM routing research
idn-analyzer.md         /idn-analyzer/  Offline prompt profiler
llm-valet.md            /llm-valet/   LLM lifecycle manager
mcp-probe.md            /mcp-probe/   MCP advisor
headroom.md             /headroom/    System stability monitor
hermes-tool-test-suite.md  /hermes-tool-test-suite/
dev-rig.md              /dev-rig/     Shared CI substrate
security.md             /security/    Org-level security posture
about.md                /about/       Org, license, contact

CNAME                   legionforge.org
LICENSE                 AGPL-3.0
```

## Adding a new product page

1. Add the product entry to `_config.yml` under `products:`. This makes it appear in the home page grid and footer automatically.
2. Create `<product-id>.md` at the repo root with frontmatter:
   ```yaml
   ---
   layout: product
   title: Product Name
   tagline: One-line pitch
   description: One-paragraph description for SEO
   permalink: /<product-id>/
   category: framework | security | tool | app
   product_id: <product-id>
   repo: <github-repo-name>
   docs_path: <path-on-docs-site>   # optional
   ---
   ```
3. Write the body content in markdown. The product layout adds the hero, related-products band, and shared chrome automatically.

## Local development

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://127.0.0.1:4000/>.

If you don't have Ruby / Bundler set up, GitHub Pages will build on push. Iteration cycle is push → wait ~30s → refresh.

## Deploy

Pushes to `main` trigger GitHub Pages' default Jekyll build and deploy. Custom domain via the `CNAME` file in the repo root and the apex DNS at Namecheap.

## License

Site prose is AGPL-3.0 (matching the framework). The brand mark, name, and color palette follow the [brand guidelines](https://docs.legionforge.org/contribute/brand/).
