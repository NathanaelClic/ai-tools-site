# AI Tools Weekly — Notas do Projeto

## URLs
- **Produção:** https://ai-tools-site.nathanael-4c1.workers.dev/
- **GitHub:** https://github.com/NathanaelClic/ai-tools-site
- **Beehiiv:** https://app.beehiiv.com (newsletter "Ferramentas de IA Semanais")

## Deploy
Automático via Cloudflare Pages — basta fazer `git push` que o site atualiza em ~2 min.

```bash
cd "C:\CLAUDE CODE\JOB\SITES\ai-tools-site"
git add .
git commit -m "descrição"
git push
```

## Pendências críticas (sem isso o site não gera renda)

### 1. Links de afiliado reais
Todos os links ainda têm `YOUR_AFFILIATE_ID`. Cadastrar e substituir:
- Jasper AI → jasper.ai/affiliate-program
- Copy.ai → copy.ai/affiliates (aprovação imediata, 45% comissão)
- Surfer SEO → surferseo.com/affiliate
- Writesonic → writesonic.com/affiliate
- SEMrush → semrush.com/lp/affiliate

Arquivos para atualizar:
- `src/pages/reviews/jasper-ai.astro`
- `src/pages/reviews/surfer-seo.astro`
- `src/pages/reviews/copy-ai.astro`
- `src/pages/compare/jasper-vs-copy-ai.astro`

### 2. Beehiiv embed ID
No painel Beehiiv → Grow → Forms → copiar embed ID.
Arquivo: `src/components/NewsletterForm.astro` — substituir `YOUR_BEEHIIV_EMBED_ID`

### 3. Domínio próprio
Comprar em Porkbun (~$10/ano), conectar no Cloudflare Pages.
Depois atualizar `siteUrl` em `src/layouts/Layout.astro`

### 4. Google Search Console
- Adicionar propriedade
- Submeter sitemap: `https://SEU-DOMINIO/sitemap-index.xml`

## Estrutura de pastas
```
src/
  components/
    Navbar.astro
    Footer.astro
    NewsletterForm.astro   ← trocar BEEHIIV_EMBED_ID
    HeroIllustration.astro
    ToolIcon.astro
  layouts/
    Layout.astro           ← trocar siteUrl quando tiver domínio
    ReviewLayout.astro
  pages/
    index.astro            ← Homepage EN
    pt/index.astro         ← Homepage PT-BR
    reviews/
      index.astro
      jasper-ai.astro      ← trocar affiliateUrl
      surfer-seo.astro     ← trocar affiliateUrl
      copy-ai.astro        ← trocar affiliateUrl
    compare/
      index.astro
      jasper-vs-copy-ai.astro
    blog/
      index.astro
      best-ai-writing-tools-2025.astro
      how-to-make-money-with-ai-tools.astro
  styles/
    global.css
```
