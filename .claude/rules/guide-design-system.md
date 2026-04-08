# Design System dos Guias — Regras Obrigatórias

> Aplica-se a **todos os guias** em `guias/*.html`. Sem exceção.

## Estética Geral

- **Modo:** Light mode exclusivamente (nunca dark)
- **Inspiração:** Apple + sinapse.club — clean, espaçado, tipografia tight
- **Fonte:** System font stack (`-apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Inter', system-ui, sans-serif`)
- **CSS:** Sempre `<link rel="stylesheet" href="../assets/css/guide.css">` — nunca CSS inline completo, apenas overrides pontuais via `<style>`

## Idioma

- **Todo o conteúdo em PT-BR com acentuação correta e completa**
- Revisar obrigatoriamente: ã, ão, ç, é, ê, í, ó, ô, ú, à — nunca omitir acentos
- Termos técnicos, nomes próprios e citações em inglês permanecem em inglês
- Verificar antes de publicar: "não", "você", "é", "está", "também", "já", "além", "até", "através", "próprio", "crítico", "público", "página", "lançamento", "operação", "solução", "informações"

## Estrutura Obrigatória do HTML

```html
<body class="guide-theme-claude">
  <article class="guide claude-shell">
    <header class="guide-section claude-hero fade-in">
      <!-- Hero -->
    </header>
    <section class="guide-section fade-in fade-in-d1">
      <!-- CTA topo: guide-badge SINAPSE + claude-card-title + claude-card-copy -->
    </section>
    <section class="guide-section claude-section fade-in fade-in-d1">
      <!-- Seção 00 -->
    </section>
    <hr class="guide-divider">
    <!-- ... seções 01-N ... -->
    <section class="guide-section fade-in fade-in-d4">
      <!-- CTA final -->
    </section>
    <footer class="guide-footer fade-in fade-in-d4">
      <p>Criado por <span class="guide-author">Caio Imori</span></p>
      <p style="margin-top: 8px;">Descrição curta do guia.</p>
    </footer>
  </article>
</body>
```

## Hero — Estrutura Exata

```html
<header class="guide-section claude-hero fade-in">
  <div class="claude-kicker-row">
    <span class="guide-badge">Tipo do guia</span>
    <span class="claude-meta-pill">Título curto // Mês Ano</span>
  </div>

  <div class="claude-hero-grid">
    <div>
      <p class="claude-overline">Categoria // Subtítulo</p>
      <h1 class="guide-hero-title claude-headline">Título principal do guia</h1>
      <p class="guide-subtitle claude-subtitle">Subtítulo explicativo.</p>
      <div class="claude-actions">
        <a href="..." class="guide-cta" style="background: #1a1a1a; color: #ffffff !important;">CTA primário</a>
        <a href="..." class="guide-cta-secondary">CTA secundário</a>
      </div>
    </div>
    <aside class="claude-panel">
      <div>
        <span class="claude-meta-pill">Label</span>
        <h2 class="claude-panel-title" style="margin-top: 18px;">Título do panel</h2>
        <p class="claude-panel-copy">Texto do panel.</p>
      </div>
      <ul class="claude-facts">
        <li><strong>Label:</strong> valor</li>
      </ul>
    </aside>
  </div>

  <div class="claude-stats">
    <div class="claude-stat">
      <span class="claude-stat-label">Label</span>
      <span class="claude-stat-value">Valor</span>
      <p>Descrição curta de uma linha.</p>
    </div>
    <!-- 4 stats no total -->
  </div>
</header>
```

## Seções de Conteúdo — Estrutura Exata

```html
<section class="guide-section claude-section fade-in fade-in-d1">
  <div class="claude-section-title-wrap">
    <div class="claude-section-index">00</div>
    <div>
      <h2 class="claude-section-title">Título da seção</h2>
      <p class="claude-section-intro">Subtítulo introdutório da seção.</p>
    </div>
  </div>
  <!-- conteúdo da seção -->
</section>
```

**IMPORTANTE:** O `claude-section-index` e o `<div>` com título/intro são filhos diretos do `claude-section-title-wrap` — nunca soltos sem o div wrapper.

## CTAs — Estrutura Exata

```html
<div class="claude-cta-block">
  <span class="guide-badge">SINAPSE</span>
  <h2 class="claude-card-title" style="margin-top: 12px;">Headline do CTA</h2>
  <p class="claude-card-copy mt-24">Texto de suporte.</p>
  <div class="claude-actions mt-24">
    <a href="https://sinapse.club" target="_blank" rel="noopener" class="guide-cta"
       style="background: #1a1a1a; color: #ffffff !important;">Label do botão</a>
  </div>
</div>
```

- **CTA topo:** sutil, antes da primeira seção de conteúdo
- **CTA final:** forte, após a última seção — com `Entrar no SINAPSE` como label
- Ambos linkam para `https://sinapse.club`

## Classes CSS — Referência Rápida

| Elemento | Classe Correta |
|----------|---------------|
| Badge/pill de label | `guide-badge` |
| Título h1 | `guide-hero-title claude-headline` |
| Subtítulo hero | `guide-subtitle claude-subtitle` |
| Overline acima do h1 | `claude-overline` |
| Stat box | `claude-stat` (não `claude-stat-box`) |
| Stat label (vem ANTES do value) | `claude-stat-label` |
| Stat valor | `claude-stat-value` |
| Título de card/surface | `claude-card-title` |
| Parágrafo de card/surface | `claude-card-copy` |
| Lista com bullets em surface | `claude-checklist` (não `claude-check-list`) |
| Step title | `claude-step-title` (em `<strong>`) |
| Step copy | `claude-step-copy` (em `<p>`) |
| Nota/callout | `claude-note` → `<p class="mb-0">` interno |
| Tabela | `claude-compact-table` dentro de `claude-surface` |
| Source list | `claude-source-list` dentro de `claude-surface` |
| Espaçamento interno | `mt-24` e `mb-0` |
| Botão primário | `guide-cta` com inline style `background: #1a1a1a; color: #ffffff !important;` |
| Botão secundário | `guide-cta-secondary` |

## Componentes Disponíveis

- `claude-split-grid` — 2 colunas (50/50)
- `claude-card-grid` — 3 colunas de cards
- `claude-surface` — card branco com borda sutil
- `claude-surface claude-surface-accent` — card com gradiente de destaque
- `claude-check-item` — card de feature com estilo de checklist
- `claude-step-list` — lista numerada com contador decorativo
- `claude-note` — callout/tip em destaque
- `claude-compact-table` — tabela compacta sem bordas pesadas
- `guide-code-block` — bloco de código com fonte mono
- `claude-inline-code` — código inline

## Fade-in e Animações

- Hero: `fade-in` (sem delay)
- CTA topo + seção 00-01: `fade-in fade-in-d1`
- Seções 02-03: `fade-in fade-in-d2`
- Seções 04-05: `fade-in fade-in-d3`
- Seções finais + CTA final + footer: `fade-in fade-in-d4`

## O Que Nunca Fazer

- Usar `claude-badge` — o correto é `guide-badge`
- Colocar o h1 fora do `claude-hero-grid`
- Usar `claude-stat-box` — o correto é `claude-stat`
- Usar `claude-hero-title` sem `guide-hero-title` (precisam das duas classes)
- Omitir o `<div>` wrapper dentro do `claude-section-title-wrap`
- Tabela solta sem wrapper `claude-surface`
- Source list solta sem wrapper `claude-surface`
- Usar `<h3>` sem a classe `claude-card-title`
- Usar `<p>` em card sem a classe `claude-card-copy`
- Omitir acentos do PT-BR no conteúdo textual
