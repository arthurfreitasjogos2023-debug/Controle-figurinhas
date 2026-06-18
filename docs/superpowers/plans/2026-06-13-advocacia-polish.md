# Advocacia Liberato Reis — Polish & Skills Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Refatorar `advocacia.html` aplicando todas as regras de ui-ux-pro-max e emil-design-eng: substituir emojis por SVG, corrigir animações, acessibilidade completa e microinterações polidas.

**Architecture:** Arquivo único `advocacia.html` com CSS vars consolidados, SVG icons inline, animações via `transform/opacity` apenas, IntersectionObserver para scroll reveal.

**Tech Stack:** HTML5, CSS3 (custom properties, @starting-style, clip-path), Vanilla JS (IntersectionObserver, RAF, Canvas API)

---

### Task 1: SVG Icons — substituir todos os emojis

**Files:**
- Modify: `advocacia.html` (seção `.svc-icon` e demais ícones decorativos)

- [ ] **Step 1: Substituir emojis dos 6 cards de serviço por SVGs inline**

Localizar cada `.svc-icon` e substituir o emoji pelo SVG correspondente:

```html
<!-- Aposentadoria (bank/building) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <path d="M3 21h18M3 10h18M5 6l7-3 7 3M4 10v11M8 10v11M12 10v11M16 10v11M20 10v11"/>
  </svg>
</div>

<!-- Revisão INSS (clipboard/doc) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <path d="M9 5H7a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2h-2M9 5a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2M9 5a2 2 0 0 0 2-2h2a2 2 0 0 0 2 2m-6 9 2 2 4-4"/>
  </svg>
</div>

<!-- BPC/LOAS (accessibility) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <circle cx="12" cy="5" r="1"/><path d="M9 20l1-5 2 2 2-2 1 5M5 9l7-1 7 1M9 14l1-5M15 14l-1-5"/>
  </svg>
</div>

<!-- Pensão por Morte (heart/dove) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
  </svg>
</div>

<!-- Auxílio Incapacidade (cross/medical) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <path d="M12 2a10 10 0 1 0 0 20A10 10 0 0 0 12 2zM8 12h8M12 8v8"/>
  </svg>
</div>

<!-- Planejamento (bar chart) -->
<div class="svc-icon" aria-hidden="true">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
    <line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/>
  </svg>
</div>
```

- [ ] **Step 2: Substituir ícone da foto-placeholder por SVG**

```html
<div class="photo-icon" aria-hidden="true">
  <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="color:var(--gold)">
    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/>
  </svg>
</div>
```

- [ ] **Step 3: Substituir ícones `.benefit-icon` por SVGs**

```html
<!-- Agilidade (zap) -->
<div class="benefit-icon" aria-hidden="true">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="color:var(--gold)">
    <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
  </svg>
</div>

<!-- Análise (search) -->
<div class="benefit-icon" aria-hidden="true">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="color:var(--gold)">
    <circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/>
  </svg>
</div>

<!-- Comunicação (message) -->
<div class="benefit-icon" aria-hidden="true">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="color:var(--gold)">
    <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
  </svg>
</div>

<!-- Sem custo (handshake) -->
<div class="benefit-icon" aria-hidden="true">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="color:var(--gold)">
    <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
  </svg>
</div>
```

- [ ] **Step 4: Adicionar CSS para `.svc-icon svg` e `.benefit-icon svg`**

```css
.svc-icon svg,.benefit-icon svg{
  width:24px;height:24px;
  stroke:var(--gold);
}
.photo-icon svg{stroke:var(--gold);}
```

- [ ] **Step 5: Commit**
```bash
git add advocacia.html
git commit -m "refactor: substituir emojis por SVG icons (ui-ux-pro-max no-emoji-icons)"
```

---

### Task 2: Animações — corrigir conforme emil-design-eng

**Files:**
- Modify: `advocacia.html` (bloco `<style>`)

- [ ] **Step 1: Corrigir `.reveal` — translateY menor, scale correto**

```css
/* ANTES */
.reveal{
  opacity:0;transform:translateY(28px);
  transition:opacity .6s var(--ease-out),transform .6s var(--ease-out);
}
/* DEPOIS — movimento sutil, nunca escala de 0 */
.reveal{
  opacity:0;
  transform:translateY(8px) scale(0.98);
  transition:opacity .45s var(--ease-out),transform .45s var(--ease-out);
}
.reveal.in{opacity:1;transform:translateY(0) scale(1);}
```

- [ ] **Step 2: Corrigir botões — active scale + cursor + touch-action**

```css
.btn-primary,.btn-outline,.nav-cta{
  cursor:pointer;
  touch-action:manipulation;
}
.btn-primary:active{transform:scale(0.97);}
.btn-outline:active{transform:scale(0.97);}
.nav-cta:active{transform:scale(0.97);}
```

- [ ] **Step 3: Corrigir `.faq-q` — cursor e touch-action**

```css
.faq-q{cursor:pointer;touch-action:manipulation;}
```

- [ ] **Step 4: Corrigir `.step:hover .step-num` — gated em hover media query**

```css
/* Remover do bloco geral, colocar em media query */
@media(hover:hover) and (pointer:fine){
  .step:hover .step-num{
    background:var(--gold);color:var(--navy);border-color:var(--gold);
  }
}
```

- [ ] **Step 5: Corrigir `.whatsapp-btn` — exit mais rápido que enter**

```css
/* O pulse já existe, adicionar hover correto */
@media(hover:hover) and (pointer:fine){
  .whatsapp-btn:hover{
    transform:scale(1.08);
    transition:transform .18s var(--ease-out);
  }
}
.whatsapp-btn:active{
  transform:scale(0.95);
  transition:transform .1s var(--ease-out);
}
```

- [ ] **Step 6: Corrigir stagger do scroll reveal no JS — 30-80ms range**

```js
/* ANTES: Math.min(bIdx++*55,360) — muito lento (até 360ms) */
/* DEPOIS: max 240ms, gaps de 40ms */
var d = batch ? Math.min(bIdx++ * 40, 240) : 0;
```

- [ ] **Step 7: Commit**
```bash
git add advocacia.html
git commit -m "fix: corrigir animações conforme emil-design-eng (scale, stagger, easing, active states)"
```

---

### Task 3: Acessibilidade — skip link, contraste, aria

**Files:**
- Modify: `advocacia.html` (antes da tag `<nav>` e CSS)

- [ ] **Step 1: Adicionar skip link no topo do body**

```html
<!-- Primeiro filho do body, antes do #progress -->
<a href="#main-content" class="skip-link">Pular para o conteúdo principal</a>
```

```css
.skip-link{
  position:absolute;top:-100px;left:1rem;
  background:var(--gold);color:var(--navy);
  padding:.5rem 1rem;border-radius:4px;
  font-weight:700;font-size:.9rem;
  text-decoration:none;z-index:10000;
  transition:top .2s var(--ease-out);
}
.skip-link:focus{top:1rem;}
```

- [ ] **Step 2: Adicionar `id="main-content"` na primeira section após nav**

```html
<!-- No <section id="hero"> adicionar role e id -->
<section id="hero" role="main">
  <!-- Adicionar id invisível para o skip link -->
  <span id="main-content" tabindex="-1" style="position:absolute;top:0;"></span>
  ...
</section>
```

- [ ] **Step 3: Verificar todos os botões do nav-cta têm texto visível**

O botão `.nav-cta` já tem texto "Consulta Grátis" — OK.
Verificar que `.hamburger` tem `aria-label="Abrir menu"` — já existe.

- [ ] **Step 4: Adicionar `role="list"` em `.nav-links`**

```html
<ul class="nav-links" role="list">
```

- [ ] **Step 5: Adicionar `lang` e `dir` no html tag (já existe lang, confirmar)**

```html
<html lang="pt-BR" dir="ltr">
```

- [ ] **Step 6: Commit**
```bash
git add advocacia.html
git commit -m "feat: adicionar skip link e melhorias de acessibilidade (ui-ux-pro-max a11y)"
```

---

### Task 4: Performance — touch-action, font-display, CLS

**Files:**
- Modify: `advocacia.html` (CSS e head)

- [ ] **Step 1: Adicionar `touch-action: manipulation` em todos os elementos interativos**

```css
/* Adicionar ao bloco existente de botões */
a,button,.faq-q,.svc-card,.nav-cta{
  touch-action:manipulation;
}
```

- [ ] **Step 2: Reservar espaço para `.testi-track` evitando CLS**

```css
.testi-track-wrap{
  min-height:200px; /* reserva espaço antes dos cards carregarem via JS */
}
```

- [ ] **Step 3: Adicionar `will-change: transform` apenas nos elementos que animam continuamente**

```css
.testi-track{will-change:transform;}
#hero-canvas{will-change:transform;}
```

- [ ] **Step 4: Throttle no evento de scroll (já existe passive, confirmar debounce)**

```js
/* No listener de scroll do progress bar, throttle com RAF */
var ticking=false;
window.addEventListener('scroll',function(){
  if(!ticking){
    requestAnimationFrame(function(){
      var s=window.scrollY,h=document.body.scrollHeight-window.innerHeight;
      prog.style.width=(h>0?(s/h*100):0)+'%';
      navEl.classList.toggle('scrolled',window.scrollY>60);
      ticking=false;
    });
    ticking=true;
  }
},{passive:true});
```

- [ ] **Step 5: Commit**
```bash
git add advocacia.html
git commit -m "perf: touch-action, CLS reserve, throttle scroll com RAF"
```

---

### Task 5: CSS — substituir `transition: all` e vars semânticas

**Files:**
- Modify: `advocacia.html` (bloco `<style>`)

- [ ] **Step 1: Auditar e corrigir qualquer `transition: all`**

Procurar por `transition:all` ou `transition: all` no CSS e substituir por propriedades específicas:

```css
/* NUNCA */
transition: all 0.3s ease;

/* SEMPRE especificar */
transition: transform 200ms var(--ease-out), opacity 200ms var(--ease-out);
```

- [ ] **Step 2: Adicionar var `--z-nav`, `--z-modal`, `--z-toast` para z-index gerenciado**

```css
:root{
  /* ... vars existentes ... */
  --z-base:0;
  --z-card:10;
  --z-sticky:100;
  --z-nav:1000;
  --z-modal:9000;
  --z-toast:9999;
}
/* Substituir z-index hardcoded */
nav{z-index:var(--z-nav);}
.mobile-menu{z-index:calc(var(--z-nav) - 1);}
.whatsapp-btn{z-index:var(--z-sticky);}
#progress{z-index:var(--z-toast);}
```

- [ ] **Step 3: Commit**
```bash
git add advocacia.html
git commit -m "refactor: remover transition:all, adicionar z-index vars semânticas"
```

---

### Task 6: Microinterações finais — hover e svc-arrow

**Files:**
- Modify: `advocacia.html`

- [ ] **Step 1: Adicionar hover na `.svc-arrow` com clip-path reveal**

```css
.svc-arrow{
  position:relative;
  overflow:hidden;
}
.svc-arrow::after{
  content:'→';
  position:absolute;right:0;
  transform:translateX(0);
  transition:transform .2s var(--ease-out);
}
@media(hover:hover) and (pointer:fine){
  .svc-card:hover .svc-arrow{
    color:var(--gold-light);
  }
}
```

- [ ] **Step 2: Adicionar transição suave na `.nav-links a` com underline animado**

```css
.nav-links a{
  position:relative;
}
.nav-links a::after{
  content:'';
  position:absolute;bottom:-4px;left:0;right:0;
  height:1px;background:var(--gold);
  transform:scaleX(0);transform-origin:left;
  transition:transform .2s var(--ease-out);
}
@media(hover:hover) and (pointer:fine){
  .nav-links a:hover::after{transform:scaleX(1);}
}
```

- [ ] **Step 3: Adicionar `@starting-style` para entrada da nav mobile**

```css
.mobile-menu{
  transition:opacity .3s var(--ease-out);
}
```

- [ ] **Step 4: Commit**
```bash
git add advocacia.html
git commit -m "polish: svc-arrow hover, nav underline animado, microinterações finais"
```

---

## Verificação Final

Após todas as tasks, checar:
- [ ] Nenhum emoji no HTML (buscar por regex `[\u{1F300}-\u{1FFFF}]`)
- [ ] Nenhum `transition: all` no CSS
- [ ] Todos os botões têm `cursor:pointer` e `touch-action:manipulation`
- [ ] Skip link funciona com Tab
- [ ] `@media(prefers-reduced-motion:reduce)` presente e testado
- [ ] Stagger máximo 240ms (40ms × 6 itens)
- [ ] `:active` em todos os elementos clicáveis
