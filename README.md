/* ========== CSS Reset (Modern) ========== */
*,
*::before,
*::after {
  box-sizing: border-box;
}
html {
  -webkit-text-size-adjust: 100%;
}
body, h1, h2, h3, h4, h5, h6, p, figure, blockquote, dl, dd {
  margin: 0;
}
ul[role="list"], ol[role="list"] {
  list-style: none;
  padding: 0;
  margin: 0;
}
img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}
input, button, textarea, select {
  font: inherit;
}
:root {
  /* ========== Theme ========== */
  --bg: #0f1115;
  --surface: #151821;
  --text: #e6e7eb;
  --muted: #a7adba;
  --primary: #4f7cff;
  --primary-contrast: #ffffff;
  --accent: #11c0b4;
  --danger: #ff5a5f;

  /* ========== Layout ========== */
  --max-w: 1100px;
  --radius: 12px;
  --shadow-sm: 0 4px 12px rgba(0,0,0,0.15);
  --shadow-md: 0 10px 30px rgba(0,0,0,0.18);

  /* ========== Typography ========== */
  --font-sans: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji";
  --font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;

  --fs-0: clamp(0.85rem, 0.8rem + 0.2vw, 0.95rem);
  --fs-1: clamp(1rem, 0.95rem + 0.3vw, 1.125rem);
  --fs-2: clamp(1.25rem, 1.1rem + 0.6vw, 1.5rem);
  --fs-3: clamp(1.6rem, 1.35rem + 1vw, 2rem);
  --fs-4: clamp(2.2rem, 1.8rem + 1.6vw, 2.8rem);

  /* Spacing scale */
  --space-1: 6px;
  --space-2: 10px;
  --space-3: 16px;
  --space-4: 24px;
  --space-5: 36px;
  --space-6: 52px;
}

@media (prefers-color-scheme: light) {
  :root {
    --bg: #ffffff;
    --surface: #f6f7fb;
    --text: #1a1d27;
    --muted: #5b6270;
    --primary: #2f6aff;
    --accent: #0aaea2;
  }
}

/* ========== Base ========== */
html, body {
  height: 100%;
}
body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--font-sans);
  font-size: var(--fs-1);
  line-height: 1.6;
}

/* ========== Container ========== */
.container {
  width: min(100% - 2rem, var(--max-w));
  margin-inline: auto;
}

/* ========== Headers & Text ========== */
h1 { font-size: var(--fs-4); line-height: 1.15; letter-spacing: -0.02em; }
h2 { font-size: var(--fs-3); line-height: 1.2; letter-spacing: -0.01em; }
h3 { font-size: var(--fs-2); line-height: 1.25; }
h4 { font-size: var(--fs-1); line-height: 1.35; }
p  { font-size: var(--fs-1); color: var(--text); }
.small { font-size: var(--fs-0); color: var(--muted); }

/* ========== Links ========== */
a {
  color: var(--primary);
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}

/* ========== Buttons ========== */
.button {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 16px;
  border-radius: var(--radius);
  border: 1px solid transparent;
  background: var(--primary);
  color: var(--primary-contrast);
  box-shadow: var(--shadow-sm);
  transition: transform 120ms ease, filter 140ms ease, box-shadow 140ms ease;
}
.button:hover { filter: brightness(1.05); box-shadow: var(--shadow-md); }
.button:active { transform: translateY(1px) scale(0.99); }
.button.outline {
  background: transparent;
  color: var(--primary);
  border-color: currentColor;
}

/* ========== Cards ========== */
.card {
  background: var(--surface);
  border: 1px solid color-mix(in oklab, var(--surface), #000 10%);
  border-radius: var(--radius);
  padding: var(--space-4);
  box-shadow: var(--shadow-sm);
}
.card + .card { margin-top: var(--space-3); }

/* ========== Navigation ========== */
.nav {
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: saturate(180%) blur(10px);
  background: color-mix(in oklab, var(--bg), #000 10%);
  border-bottom: 1px solid color-mix(in oklab, var(--surface), #000 15%);
}
.nav .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-block: var(--space-3);
}
.nav a { color: var(--text); }
.nav .brand { font-weight: 700; letter-spacing: -0.02em; }

/* ========== Grid & Layout ========== */
.grid {
  display: grid;
  gap: var(--space-3);
}
.grid.cols-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
.grid.cols-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
.grid.cols-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); }
@media (max-width: 900px) {
  .grid.cols-3, .grid.cols-4 { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .grid.cols-2, .grid.cols-3, .grid.cols-4 { grid-template-columns: 1fr; }
}

/* ========== Forms ========== */
.label { display: block; font-weight: 600; margin-bottom: 6px; }
.input,
.textarea,
.select {
  width: 100%;
  padding: 10px 12px;
  border-radius: 10px;
  border: 1px solid color-mix(in oklab, var(--surface), #000 20%);
  background: color-mix(in oklab, var(--surface), #fff 5%);
  color: var(--text);
  outline: none;
  transition: border-color 140ms ease, box-shadow 140ms ease;
}
.input:focus,
.textarea:focus,
.select:focus {
  border-color: var(--primary);
  box-shadow: 0 0 0 3px color-mix(in oklab, var(--primary), #fff 75%);
}
.helper { color: var(--muted); font-size: var(--fs-0); margin-top: 6px; }

/* ========== Tables ========== */
.table {
  width: 100%;
  border-collapse: collapse;
  font-size: var(--fs-0);
}
.table th, .table td {
  text-align: left;
  padding: 12px 14px;
  border-bottom: 1px solid color-mix(in oklab, var(--surface), #000 20%);
}
.table thead th {
  font-weight: 700;
  color: var(--muted);
}

/* ========== Code blocks ========== */
.code {
  font-family: var(--font-mono);
  font-size: 0.95em;
  background: color-mix(in oklab, var(--surface), #000 10%);
  border: 1px solid color-mix(in oklab, var(--surface), #000 25%);
  border-radius: 10px;
  padding: 12px 14px;
  overflow-x: auto;
}

/* ========== Utilities ========== */
.stack > * + * { margin-top: var(--space-3); }
.cluster {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  flex-wrap: wrap;
}
.center {
  display: grid;
  place-items: center;
}
.hidden { display: none !important; }
.muted { color: var(--muted); }
.mt-1 { margin-top: var(--space-1); }
.mt-2 { margin-top: var(--space-2); }
.mt-3 { margin-top: var(--space-3); }
.mt-4 { margin-top: var(--space-4); }
.mt-5 { margin-top: var(--space-5); }

/* ========== Hero ========== */
.hero {
  padding-block: var(--space-6);
  background: linear-gradient(180deg, color-mix(in oklab, var(--bg), var(--primary) 6%), var(--bg));
}
.hero .title { font-size: var(--fs-4); }
.hero .subtitle { color: var(--muted); max-width: 70ch; }

/* ========== Footer ========== */
.footer {
  margin-top: var(--space-6);
  padding-block: var(--space-5);
  border-top: 1px solid color-mix(in oklab, var(--surface), #000 10%);
  color: var(--muted);
}

/* ========== Motion preferences ========== */
@media (prefers-reduced-motion: reduce) {
  * { animation-duration: 0.001ms !important; animation-iteration-count: 1 !important; transition-duration: 0.001ms !important; }
}

/* ========== Dark mode toggle hook ========== */
/* Add class="theme-light" on <html> to force light; class="theme-dark" to force dark */
html.theme-light { color-scheme: light; }
html.theme-dark { color-scheme: dark; }
