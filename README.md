# Start Page — Hacker/Cupertino Minimalist

> **PT‑BR & EN‑US** · Single‑file start page (HTML/CSS/JS) with hacker vibe, Cupertino polish, and local‑first features. Built as a live demo: how a **well‑crafted prompt** can produce a complete, production‑ready front‑end with **zero follow‑up edits**.


> **Access here:** · https://jorgediasdsg.github.io/startpage/
---

## 🧭 Visão Geral · Overview

**PT‑BR**
Esta é uma página inicial pessoal, de coluna única, responsiva e minimalista: fundo animado estilo “hacker” (rede de linhas e pontos seguindo o cursor), favoritos persistidos em `localStorage`, tarefas, Pomodoro configurável, relógio digital por fuso horário (IANA), embed do Spotify e **frase filosófica do dia**. Tudo isso com estética **Cupertino** (Apple‑like) e tema **Hacker** (preto + verde), além de temas claro/escuro.

**EN‑US**
This is a clean, single‑column, responsive personal start page: animated hacker background (line/point network reacting to the cursor), `localStorage` bookmarks, tasks, configurable Pomodoro, timezone‑aware clock (IANA), Spotify embed, and a **philosophical quote of the day**. The UI blends a **Cupertino** aesthetic with a **Hacker** (green on black) theme and optional light/dark modes.

---

## ✨ Features

* Animated background: particle/network grid attracted by the mouse pointer.
* Bookmarks (localStorage): name, URL, favicon auto‑resolved; modal UX for adding entries (clean header, no inline inputs).
* Greeting with name + region (timezone) from Settings.
* Digital clock honoring the selected IANA timezone.
* To‑do list with toggle and delete (persisted in localStorage).
* Pomodoro timer: work/short break/long break, with long break every N cycles; fully configurable.
* Spotify iframe (paste any track/album/playlist URL or URI; auto converts to `/embed/`).
* Philosophical quote of the day (deterministic, rotates daily).
* Themes: **Hacker**, **Cupertino Light**, **Cupertino Dark**.
* Single‑column layout, fluid and **mobile‑first**.

> **Nota técnica / Tech note:** Front‑end puro não consegue ler com segurança o `<title>` ou `<link rel="icon">` de sites de terceiros (CORS/SOP). A solução usa `https://<origin>/favicon.ico` com fallback `Google S2 Favicons`, e **sugere o nome pelo hostname**. Para obter o `<title>` exato e o favicon real, use um pequeno proxy (ex.: Cloudflare Worker) — prompt abaixo já inclui isso como opcional.

---

## 🚀 Deploy (GitHub Pages)

1. Crie um repositório público (por exemplo, `startpage`).
2. Faça upload de `index.html` na raiz e faça **Commit**.
3. Em **Settings → Pages**: `Deploy from a branch` → `main` / `/ (root)`.
4. Acesse: `https://SEU_USUARIO.github.io/startpage/`.

> Para publicar na raiz do domínio, use o repo especial `SEU_USUARIO.github.io`.

---

## 🛠️ Stack

* **Vanilla HTML/CSS/JS** (sem build step, sem dependências).
* `localStorage` para persistência local.
* Iframes (Spotify) com permissões adequadas.

---

## 🔐 Privacidade e Limites

* Todos os dados (favoritos, tarefas, configurações, tempos do Pomodoro) ficam **no seu navegador** via `localStorage`.
* O embed do Spotify carrega conteúdo do domínio do Spotify (sujeito às políticas da plataforma).

---

## 🧪 Como testar localmente

Abra `index.html` no navegador. Para editar temas e tempos do Pomodoro, clique na engrenagem (Configurações). Para adicionar favoritos, clique no botão **Adicionar** da seção “Favoritos”.

---

## 🧵 Contexto de uso

Utilizei este projeto para demonstrar a colegas como um **prompt bem estruturado** é capaz de gerar **todo o código** (UI, lógica e responsividade) **sem interações adicionais** — apenas colando o prompt uma única vez no ChatGPT.

* **Ferramenta utilizada / Tool used:** ChatGPT — **GPT‑5 Thinking**.
* **Data de geração / Generation date:** YYYY‑MM‑DD (preencha conforme sua execução).

---

## 🧰 Prompt‑Mestre (PT‑BR)

Cole o prompt abaixo **integralmente** no ChatGPT (**GPT‑5 Thinking**). Ele deve produzir um arquivo único `index.html` (ou, opcionalmente, 3 arquivos: `index.html`, `style.css`, `app.js`), seguindo as especificações.

```text
[OBJETIVO]
Gerar uma página inicial pessoal completa no estilo "hacker minimalista com polimento Cupertino". Deve ser totalmente funcional sem back‑end, preferencialmente em **um único arquivo** (`index.html`) contendo HTML, CSS e JS. Aceito também a opção de separar em 3 arquivos (HTML/CSS/JS), mantendo caminhos relativos.

[REQUISITOS DE UX/UI]
- Fundo animado: rede de pontos e linhas que reagem ao ponteiro do mouse (atração suave), com performance fluida e responsiva a `devicePixelRatio`.
- Tema principal: **Hacker** (preto + verde). Oferecer também **Cupertino Light** e **Cupertino Dark** via `data-theme` no `<html>` e variáveis CSS.
- Layout: **coluna única**, responsivo, mobile‑first, limpo e moderno (estética Cupertino). Cards com cantos arredondados, sombras suaves, tipografia do sistema.
- Header com: saudação “Olá, <NOME>”, região (fuso IANA) e relógio digital (HH:MM:SS) que respeite o fuso.

[FAVORITOS]
- Persistência em `localStorage`.
- A UI **não** deve mostrar inputs permanentes. Em vez disso, um botão “Adicionar” abre **modal** com 1 campo principal: URL.
- Nome do favorito: **usar título** do site quando possível. **Se for apenas front‑end**, usar o **hostname** como fallback (ex.: `github.com`).
- Ícone do favorito: usar **favicon real** do site. **Se for apenas front‑end**, tentar `https://<origin>/favicon.ico` com fallback `https://www.google.com/s2/favicons?domain=<host>&sz=64`.
- A lista deve exibir: favicon → nome clicável → botão de exclusão.

[TAREFAS]
- Lista de tarefas simples: adicionar, marcar como concluída, excluir. Persistência em `localStorage`.

[POMODORO]
- Estados: Foco (work), Descanso curto, Descanso longo.
- Configurações: duração de foco, pausa curta, pausa longa e “descanso longo a cada N sprints”. Persistência em `localStorage`.
- Exibir timer grande (MM:SS), status textual, e indicadores de ciclo.

[RELOGIO / REGIÃO]
- Campo de **Região (IANA)** em Configurações. O relógio deve usar `toLocaleTimeString` com `timeZone` = região definida.

[SPOTIFY]
- Campo para colar URL/URI do Spotify (track/album/playlist). Converter automaticamente para a URL `/embed/` e carregar em `<iframe>` com as permissões adequadas.

[FRASE DO DIA]
- Repositório interno de 10–40 frases breves (estoicismo/aforismos). Seleção determinística por dia (ex.: índice = `year*366 + dayOfYear` mod N).

[CONFIGURAÇÕES]
- Modal de Configurações com: Nome, Tema (Hacker/Cupertino Light/Cupertino Dark), Região (IANA), tempos do Pomodoro.
- Salvar em `localStorage`. Aplicar imediatamente ao salvar.

[ACESSIBILIDADE & DETALHES]
- Usar semântica básica, foco nos botões/inputs do modal, `aria-label` quando fizer sentido.
- Evitar dependências externas; usar vanilla JS.

[RESPONSIVIDADE]
- Mobile‑first, com tipografia e espaçamentos adaptáveis. Permitir scroll no mobile.

[OBSERVAÇÃO IMPORTANTE]
- **Sem back‑end**: não é possível fazer `fetch` do HTML de outros domínios para extrair `<title>`/favicon real por causa de CORS/SOP. Implementar fallback seguro: hostname para nome, `origin + '/favicon.ico'` e fallback `Google S2 Favicons` para ícone.
- **Opcional (se quiser demonstração completa)**: incluir no final um exemplo de **Cloudflare Worker**/Node mini‑proxy que, dado uma URL, retorne `{ title, icon }` (extraindo do HTML) e mostrar como integrar (desligado por padrão).

[ENTREGA]
- Código limpo, comentado onde for crítico. Nomes de funções e variáveis legíveis. Sem frameworks. Estilo minimalista.
- Se separar arquivos, usar caminhos relativos e instruções rápidas para GitHub Pages.
```

---

## 🔁 Master Prompt (EN‑US)

Paste this **as‑is** into ChatGPT (**GPT‑5 Thinking**) to generate a single‑file `index.html` (or optionally 3 files). It encodes all requirements above in English.

```text
[GOAL]
Produce a complete personal start page with a “hacker vibe + Cupertino polish,” entirely front‑end (no backend). Prefer a **single file** (`index.html`) containing HTML/CSS/JS. Optionally support a 3‑file split (HTML/CSS/JS) with relative paths.

[UX/UI]
- Animated background: mouse‑reactive point/line network; DPI‑aware and performant.
- Primary theme: **Hacker** (black+green). Also provide **Cupertino Light** and **Cupertino Dark** via `<html data-theme>` and CSS custom props.
- Layout: **single column**, mobile‑first, clean and modern. Rounded cards, soft shadows, system font.
- Header: greeting “Olá, <NAME>”, region (IANA timezone), and a digital clock (HH:MM:SS) honoring the selected timezone.

[BOOKMARKS]
- Persist in `localStorage`.
- No always‑visible inputs. Use an **Add** button that opens a **modal** with a single URL field.
- Bookmark name: use **page title** when possible. **If front‑end only**, fall back to the **hostname** (e.g., `github.com`).
- Bookmark icon: use the **real favicon**. **If front‑end only**, try `https://<origin>/favicon.ico` and fall back to `https://www.google.com/s2/favicons?domain=<host>&sz=64`.
- Render each entry as: favicon → clickable name → delete button.

[TASKS]
- Simple to‑do list: add, toggle, delete. Persist via `localStorage`.

[POMODORO]
- States: Work, Short break, Long break.
- Configs: work minutes, short break, long break, and “long break every N sprints.” Persist in `localStorage`.
- Show a large MM:SS timer, textual status, and cycle dots.

[CLOCK / REGION]
- Config field for **Region (IANA)**. Clock must use `toLocaleTimeString` with `timeZone` = region.

[SPOTIFY]
- Field to paste a Spotify URL/URI (track/album/playlist). Convert to `/embed/` URL and load in `<iframe>` with proper allow attributes.

[QUOTE OF THE DAY]
- Internal set of 10–40 short quotes. Deterministic selection by day (e.g., `year*366 + dayOfYear` mod N).

[SETTINGS]
- Settings modal: Name, Theme (Hacker/Cupertino Light/Cupertino Dark), Region (IANA), Pomodoro timings.
- Save to `localStorage`. Apply immediately on save.

[ACCESSIBILITY & DETAILS]
- Basic semantics, focus handling in modals, `aria-label` where useful.
- No external deps; vanilla JS only.

[RESPONSIVENESS]
- Mobile‑first. Allow scrolling on mobile.

[IMPORTANT]
- **No backend**: due to CORS/SOP, you cannot fetch arbitrary pages to extract `<title>`/favicon. Implement safe fallbacks: hostname for name, `origin + '/favicon.ico'` and Google S2 for icons.
- **Optional**: include a minimal **Cloudflare Worker**/Node proxy example returning `{ title, icon }` for a given URL and demonstrate how to plug it in (disabled by default).

[DELIVERABLE]
- Clean, well‑named code. Minimalist visual style. If split into 3 files, use relative paths and include quick GitHub Pages instructions.
```

---

## 🧾 Licença

MIT — faça bom uso, melhore e compartilhe.

---

## 🙌 Créditos

* Design & implementação: você (com assistência de IA).
* Modelo utilizado: **ChatGPT — GPT‑5 Thinking**.
