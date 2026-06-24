# Eng Tools Vault

A single hub site that pulls together my engineering tools. Each tool lives in
its **own GitHub repo** and is hosted on **GitHub Pages**. The Vault embeds each
one in an iframe, so the whole thing behaves like one website — and any tool
**auto-updates the moment you push to its `main` branch** (GitHub Pages
rebuilds it automatically; the Vault shell never has to change).

Theme: **Blurprint** — Discord's look, tuned for white backgrounds.

---

## How it fits together

```
Eng-Tools-Vault (this repo)  ->  https://bijankle.github.io/Eng-Tools-Vault/
  index.html  = the hub (sidebar of tools + iframe stage)
        │
        ├─ iframe ─▶ https://bijankle.github.io/Pump-Curve/      (repo: Pump-Curve)
        ├─ iframe ─▶ https://bijankle.github.io/Slurry-Pump-Calc/
        ├─ iframe ─▶ https://bijankle.github.io/Pipe-Router/
        ├─ iframe ─▶ https://bijankle.github.io/PID-Checker/
        ├─ iframe ─▶ https://bijankle.github.io/Photo-Map/
        ├─ iframe ─▶ https://bijankle.github.io/PDF-Canvas/
        ├─ iframe ─▶ https://bijankle.github.io/Data-Extractor/
        └─ iframe ─▶ https://bijankle.github.io/Doc-Compare/
```

Nothing is copied or vendored in. The Vault just **links to** each tool's live
Pages URL, so each tool stays the single source of truth for itself.

---

## One-time setup

### 1. Turn on Pages for the Vault (this repo)
`Settings → Pages → Build and deployment → Source: Deploy from a branch →
Branch: main / (root) → Save`.
It goes live at `https://bijankle.github.io/Eng-Tools-Vault/`.

### 2. Turn on Pages for each tool repo
For **every** tool repo (Pump-Curve, Slurry-Pump-Calc, Pipe-Router,
PID-Checker, Photo-Map, PDF-Canvas, Data-Extractor, Doc-Compare):

1. Make sure the tool's working branch is merged into **`main`** (and `main` is
   the branch you'll keep pushing to).
2. `Settings → Pages → Source: Deploy from a branch → Branch: main / (root) →
   Save`.

That's it. From then on, **push to a tool's `main` → that tool updates** in the
Vault automatically. No action needed here.

> If a tool's entry HTML file isn't named `index.html`, either rename it to
> `index.html` or add a tiny `index.html` that redirects to it — Pages serves
> `index.html` by default.

---

## Adding / changing a tool

Everything is driven by the `APPS` array near the bottom of `index.html`.
Add a new tool by adding one entry:

```js
{
  slug:"my-tool",            // url + #channel name (lowercase-hyphen)
  repo:"My-Tool",            // GitHub repo name (used to build the Pages URL)
  name:"My Tool", ico:"🔧",
  group:"Documents & Data",  // which sidebar section it appears under
  desc:"Short one-liner shown on the card and toolbar.",
}
```

The Pages URL (`https://bijankle.github.io/<repo>/`) and repo link are derived
automatically from `repo`.

---

## Local preview

It's a single static file — just open `index.html` in a browser. (Embedded
tools will only load once their own Pages sites are enabled.)
