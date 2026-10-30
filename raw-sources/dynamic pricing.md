In the package section of the attached page, add pricing information with user selections for number of performers up to 4, time in increments of 30 mins, 1 hour, 2 hours and 3 hours+, and type of character being k-pop, impersonator, and princess. Use the logic from the below webpage.

[https://sophiasmagicalprincessparty.com/pricing/](https://sophiasmagicalprincessparty.com/pricing/)

Read a file, read a page

The page didn’t load well. Let me try a different approach to get the pricing logic.

Searched the web, read a page

The pricing page isn’t returning the actual dollar amounts via search. Let me now read the uploaded HTML file and build the pricing section based on standard industry pricing logic, matching the structure of Sophia’s site.

Ran 8 commands, edited a file, shared files

The pricing section has been fully replaced with an interactive calculator that matches the existing page’s aesthetic. Here’s what was built:

**Character Type** — toggle between Princess 👑, K-Pop Star 🎤, and Impersonator 🌟, each with its own premium pricing and tailored activity lists.

**Duration** — four buttons: 30 Min, 1 Hour, 2 Hours, and 3 Hours+ — with base rates scaling accordingly.

**Performers** — a stepper (1–4) that adds per-performer pricing to the total for each additional performer beyond the first.

**Live pricing logic:**

- Base rates: $150 / $225 / $350 / $500 for the four durations
- Additional performer rate: $100–$275 per extra (scales with duration)
- Character premium: Princess = no charge, K-Pop = +$50, Impersonator = +$75
- Total animates smoothly on every selection change

The result card on the right updates the package name, description, itemized breakdown, included features list, and total — all instantly as the user makes selections.

'''html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Sophia's Magical Princess Party — South Houston</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Cinzel:wght@400;500;600&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" />
<style>
  /* ── TOKENS ───────────────────────────────────────────── */
  :root {
    --gold:      #C9A96E;
    --gold-lt:   #E8D5A3;
    --rose:      #D4768A;
    --rose-lt:   #F2C4CF;
    --lavender:  #A88EC0;
    --sky:       #7EB8D4;
    --cream:     #FAF6F0;
    --ink:       #1A1118;
    --ink-soft:  #3D2B3A;
    --text:      #4A3A46;
 
    --ff-title:  'Cinzel', serif;
    --ff-serif:  'Cormorant Garamond', serif;
    --ff-sans:   'Jost', sans-serif;
 
    --ease-silk: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }
 
  /* ── RESET ────────────────────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--cream);
    color: var(--text);
    font-family: var(--ff-serif);
    font-size: 18px;
    line-height: 1.7;
    overflow-x: hidden;
  }
  img { display: block; max-width: 100%; }
  a  { color: inherit; text-decoration: none; }
 
  /* ── STAR / SPARKLE SVG DEFS ──────────────────────────── */
  .sparkle-field {
    position: absolute; inset: 0; pointer-events: none; overflow: hidden;
  }
  .sparkle-field svg { width: 100%; height: 100%; }
 
  /* ── UTILITY ──────────────────────────────────────────── */
  .visually-hidden { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0,0,0,0); }
  .gold-rule {
    display: flex; align-items: center; gap: 1rem;
    color: var(--gold); font-family: var(--ff-title); letter-spacing: 0.25em; font-size: 0.6rem; text-transform: uppercase;
  }
  .gold-rule::before, .gold-rule::after { content:''; flex:1; height:1px; background: linear-gradient(90deg, transparent, var(--gold-lt), transparent); }
 
  /* ── NAVIGATION ───────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    background: transparent;
    transition: background 0.4s var(--ease-silk), box-shadow 0.4s;
  }
  nav.scrolled {
    background: rgba(250,246,240,0.96);
    box-shadow: 0 1px 24px rgba(26,17,24,0.08);
    backdrop-filter: blur(8px);
  }
  .nav-logo {
    font-family: var(--ff-title);
    font-size: 1rem;
    letter-spacing: 0.15em;
    color: var(--ink);
    display: flex; align-items: center; gap: 0.6rem;
  }
  .nav-logo .crown { font-size: 1.2rem; }
  .nav-links {
    display: flex; gap: 2.4rem; list-style: none;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;
    letter-spacing: 0.18em; text-transform: uppercase;
  }
  .nav-links a {
    color: var(--ink-soft);
    position: relative;
    transition: color 0.25s;
  }
  .nav-links a::after {
    content:''; position: absolute; left:0; bottom:-3px; width:0; height:1px;
    background: var(--gold); transition: width 0.3s var(--ease-silk);
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-links a:hover::after { width: 100%; }
  .nav-cta {
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.18em; text-transform: uppercase;
    padding: 0.65rem 1.6rem;
    border: 1px solid var(--gold);
    color: var(--gold);
    transition: background 0.3s, color 0.3s;
    border-radius: 2px;
  }
  .nav-cta:hover { background: var(--gold); color: var(--cream); }
 
  /* ── HERO ─────────────────────────────────────────────── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    text-align: center;
    padding: 8rem 2rem 6rem;
    overflow: hidden;
  }
 
  /* layered gradient background */
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%,   rgba(212,118,138,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 60% 70% at 15% 60%,  rgba(168,142,192,0.14) 0%, transparent 65%),
      radial-gradient(ellipse 55% 50% at 85% 55%,  rgba(126,184,212,0.12) 0%, transparent 60%),
      linear-gradient(175deg, #FDF9F4 0%, #F7EEF5 50%, #EFF3F9 100%);
  }
  /* grain overlay */
  .hero-bg::after {
    content: '';
    position: absolute; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
    opacity: 0.6;
  }
 
  /* decorative arcs */
  .hero-arc {
    position: absolute; border-radius: 50%;
    border: 1px solid rgba(201,169,110,0.25);
    pointer-events: none;
  }
  .hero-arc-1 { width: 500px; height: 500px; top: 50%; left: 50%; transform: translate(-50%,-50%); }
  .hero-arc-2 { width: 720px; height: 720px; top: 50%; left: 50%; transform: translate(-50%,-50%); }
  .hero-arc-3 { width: 960px; height: 960px; top: 50%; left: 50%; transform: translate(-50%,-50%); opacity: 0.5; }
 
  .hero-eyebrow {
    font-family: var(--ff-sans); font-size: 0.65rem; font-weight: 400;
    letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1.6rem;
    opacity: 0; animation: fadeUp 0.8s 0.2s var(--ease-silk) forwards;
  }
  .hero-title {
    font-family: var(--ff-title);
    font-size: clamp(2.8rem, 7vw, 6rem);
    font-weight: 500;
    line-height: 1.12;
    color: var(--ink);
    letter-spacing: 0.02em;
    max-width: 820px;
    opacity: 0; animation: fadeUp 0.9s 0.35s var(--ease-silk) forwards;
  }
  .hero-title em {
    font-style: italic;
    background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 50%, var(--sky) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-subtitle {
    margin-top: 1.6rem;
    font-family: var(--ff-serif); font-size: 1.2rem; font-weight: 300;
    color: var(--text); max-width: 520px; line-height: 1.7;
    opacity: 0; animation: fadeUp 0.9s 0.5s var(--ease-silk) forwards;
  }
  .hero-ctas {
    display: flex; gap: 1.2rem; margin-top: 2.8rem; flex-wrap: wrap; justify-content: center;
    opacity: 0; animation: fadeUp 0.9s 0.65s var(--ease-silk) forwards;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    background: var(--gold);
    color: var(--cream);
    border-radius: 2px;
    transition: background 0.3s, transform 0.2s;
    box-shadow: 0 4px 24px rgba(201,169,110,0.35);
  }
  .btn-primary:hover { background: #b8935a; transform: translateY(-2px); }
  .btn-ghost {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    border: 1px solid rgba(201,169,110,0.5);
    color: var(--ink-soft);
    border-radius: 2px;
    transition: border-color 0.3s, color 0.3s, transform 0.2s;
  }
  .btn-ghost:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }
 
  .hero-phone {
    margin-top: 2rem;
    font-family: var(--ff-title);
    font-size: 1.4rem; letter-spacing: 0.08em;
    color: var(--rose);
    opacity: 0; animation: fadeUp 0.9s 0.8s var(--ease-silk) forwards;
  }
  .hero-phone small {
    display: block; font-family: var(--ff-sans); font-size: 0.6rem;
    letter-spacing: 0.25em; text-transform: uppercase; color: var(--text); margin-bottom: 0.3rem;
  }
 
  .hero-photo-strip {
    display: flex; gap: 1rem; margin-top: 3.5rem; justify-content: center;
    opacity: 0; animation: fadeUp 1s 0.9s var(--ease-silk) forwards;
  }
  .hero-photo-strip figure {
    width: 120px; height: 160px; overflow: hidden; border-radius: 60px;
    border: 2px solid rgba(201,169,110,0.4);
    flex-shrink: 0;
    box-shadow: 0 8px 32px rgba(26,17,24,0.12);
    transition: transform 0.4s var(--ease-silk);
  }
  .hero-photo-strip figure:nth-child(2) { margin-top: -20px; border-color: rgba(212,118,138,0.5); }
  .hero-photo-strip figure:nth-child(3) { margin-top: 10px;  border-color: rgba(168,142,192,0.5); }
  .hero-photo-strip figure:hover { transform: scale(1.05) translateY(-6px); }
  .hero-photo-strip img { width: 100%; height: 100%; object-fit: cover; }
 
  /* ── SINCE BADGE ──────────────────────────────────────── */
  .since-badge {
    position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold); opacity: 0.7; display: flex; align-items: center; gap: 0.5rem;
  }
  .since-badge span { display: inline-block; width: 24px; height: 1px; background: var(--gold-lt); }
 
  /* ── DIVIDER ──────────────────────────────────────────── */
  .section-divider {
    width: 100%; max-width: 1100px; margin: 0 auto;
    border: none; border-top: 1px solid rgba(201,169,110,0.2);
  }
 
  /* ── SECTION WRAPPER ──────────────────────────────────── */
  .section { padding: 7rem 2rem; }
  .section-inner { max-width: 1100px; margin: 0 auto; }
 
  .section-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem; display: block;
  }
  .section-heading {
    font-family: var(--ff-title);
    font-size: clamp(1.8rem, 4vw, 3rem);
    font-weight: 500;
    line-height: 1.18;
    color: var(--ink);
    letter-spacing: 0.02em;
    max-width: 560px;
  }
  .section-body {
    font-size: 1.05rem; line-height: 1.8; color: var(--text); max-width: 520px; margin-top: 1.2rem;
  }
 
  /* ── PILLARS (3-col) ──────────────────────────────────── */
  .pillars {
    display: grid; grid-template-columns: repeat(3,1fr); gap: 2px;
    margin-top: 5rem;
  }
  .pillar {
    padding: 3rem 2.4rem;
    background: white;
    position: relative;
    overflow: hidden;
    transition: transform 0.35s var(--ease-silk), box-shadow 0.35s;
  }
  .pillar::before {
    content:'';
    position: absolute; top:0; left:0; right:0; height:3px;
    background: linear-gradient(90deg, var(--rose), var(--lavender));
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.4s var(--ease-silk);
  }
  .pillar:hover::before { transform: scaleX(1); }
  .pillar:hover { transform: translateY(-6px); box-shadow: 0 16px 48px rgba(26,17,24,0.10); }
  .pillar-icon { font-size: 2rem; margin-bottom: 1.2rem; }
  .pillar-title {
    font-family: var(--ff-title); font-size: 1.05rem; letter-spacing: 0.05em;
    color: var(--ink); margin-bottom: 0.6rem;
  }
  .pillar-text { font-size: 0.95rem; color: var(--text); line-height: 1.75; }
 
  /* ── HOW IT WORKS ─────────────────────────────────────── */
  .how {
    background: linear-gradient(160deg, #F7EFF8 0%, #EEF4FA 100%);
    position: relative; overflow: hidden;
  }
  .how::before {
    content:'';
    position: absolute; top:-200px; right:-200px;
    width: 600px; height: 600px; border-radius: 50%;
    background: radial-gradient(circle, rgba(212,118,138,0.12), transparent 70%);
  }
  .how-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 5rem; align-items: center;
  }
  .how-steps { list-style: none; margin-top: 2.5rem; }
  .how-step {
    display: flex; gap: 2rem; align-items: flex-start;
    padding: 1.8rem 0; border-bottom: 1px solid rgba(201,169,110,0.2);
  }
  .how-step:last-child { border-bottom: none; }
  .step-num {
    font-family: var(--ff-title);
    font-size: 2.5rem; font-weight: 500; line-height: 1;
    color: rgba(201,169,110,0.35); flex-shrink: 0; min-width: 2.5rem; text-align: center;
  }
  .step-title {
    font-family: var(--ff-title); font-size: 1rem; color: var(--ink); margin-bottom: 0.3rem; letter-spacing: 0.04em;
  }
  .step-text { font-size: 0.9rem; color: var(--text); line-height: 1.7; }
  .how-visual {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;
  }
  .how-photo {
    border-radius: 4px; overflow: hidden;
    box-shadow: 0 8px 32px rgba(26,17,24,0.1);
    aspect-ratio: 3/4; background: #e8e0ec;
    position: relative;
  }
  .how-photo:nth-child(2) { margin-top: 2rem; }
  .how-photo img { width: 100%; height: 100%; object-fit: cover; }
  .how-photo-placeholder {
    position: absolute; inset: 0;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    gap: 0.5rem; color: rgba(60,40,60,0.3);
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
  }
  .how-photo-placeholder span { font-size: 2.5rem; }
  .call-highlight {
    margin-top: 3rem;
    padding: 2rem 2.5rem;
    background: white;
    border-left: 3px solid var(--gold);
    border-radius: 2px;
    box-shadow: 0 4px 20px rgba(26,17,24,0.06);
  }
  .call-highlight p { font-size: 0.9rem; color: var(--text); line-height: 1.7; margin-bottom: 0.8rem; }
  .call-number {
    font-family: var(--ff-title); font-size: 1.5rem; color: var(--rose); letter-spacing: 0.08em;
  }
 
  /* ── CHARACTERS ───────────────────────────────────────── */
  .characters-grid {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem; margin-top: 3.5rem;
  }
  .char-card {
    position: relative; overflow: hidden; border-radius: 4px;
    aspect-ratio: 3/4;
    background: #f0e8f0;
    cursor: pointer;
    box-shadow: 0 4px 16px rgba(26,17,24,0.08);
    transition: transform 0.4s var(--ease-silk), box-shadow 0.4s;
  }
  .char-card:hover { transform: translateY(-8px) scale(1.02); box-shadow: 0 20px 56px rgba(26,17,24,0.15); }
  .char-card::before {
    content:''; position: absolute; inset: 0; z-index: 1;
    background: linear-gradient(0deg, rgba(26,17,24,0.7) 0%, rgba(26,17,24,0.1) 60%, transparent 100%);
  }
  .char-color { position: absolute; inset:0; }
  .char-card:nth-child(1) .char-color { background: linear-gradient(160deg, #B5D4E8 0%, #7EB8D4 100%); }
  .char-card:nth-child(2) .char-color { background: linear-gradient(160deg, #F7C5D0 0%, #D4768A 100%); }
  .char-card:nth-child(3) .char-color { background: linear-gradient(160deg, #D0B8E8 0%, #A88EC0 100%); }
  .char-card:nth-child(4) .char-color { background: linear-gradient(160deg, #E8E0A0 0%, #C9A96E 100%); }
  .char-emoji { position: absolute; top: 50%; left: 50%; transform: translate(-50%,-60%); font-size: 4rem; z-index: 0; opacity: 0.4; }
  .char-info {
    position: absolute; bottom: 0; left: 0; right: 0; padding: 1.5rem;
    z-index: 2;
  }
  .char-name {
    font-family: var(--ff-title); font-size: 0.95rem; letter-spacing: 0.08em;
    color: white; display: block; margin-bottom: 0.2rem;
  }
  .char-desc { font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: rgba(255,255,255,0.7); }
 
  /* ── TESTIMONIALS ─────────────────────────────────────── */
  .testimonials { background: var(--ink); }
  .testimonials .section-label { color: var(--gold-lt); }
  .testimonials .section-heading { color: white; }
  .testi-grid {
    display: grid; grid-template-columns: repeat(3,1fr);
    gap: 1.5rem; margin-top: 3.5rem;
  }
  .testi-card {
    padding: 2.2rem;
    border: 1px solid rgba(201,169,110,0.2);
    border-radius: 2px;
    position: relative;
    transition: border-color 0.3s, background 0.3s;
  }
  .testi-card:hover { border-color: rgba(201,169,110,0.5); background: rgba(255,255,255,0.03); }
  .testi-quote {
    font-family: var(--ff-serif); font-size: 1.05rem; font-style: italic;
    color: rgba(255,255,255,0.85); line-height: 1.7; margin-bottom: 1.4rem;
  }
  .testi-quote::before { content: '\201C'; font-size: 2rem; color: var(--gold); line-height: 0; vertical-align: -0.5rem; margin-right: 0.2rem; }
  .testi-author {
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold);
  }
  .testi-stars { color: var(--gold); font-size: 0.8rem; margin-bottom: 0.8rem; letter-spacing: 0.1em; }
 
  /* ── PRICING CALCULATOR ───────────────────────────────── */
  .pricing-calculator {
    margin-top: 3.5rem;
    display: grid;
    grid-template-columns: 1fr 340px;
    gap: 2.5rem;
    align-items: start;
  }
 
  /* selector groups */
  .pc-group { margin-bottom: 2rem; }
  .pc-group-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem; display: block;
  }
  .pc-options {
    display: flex; flex-wrap: wrap; gap: 0.6rem;
  }
  .pc-btn {
    font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 400;
    letter-spacing: 0.12em; text-transform: uppercase;
    padding: 0.6rem 1.2rem;
    border: 1px solid rgba(201,169,110,0.35);
    background: white;
    color: var(--text);
    border-radius: 2px;
    cursor: pointer;
    transition: all 0.22s var(--ease-silk);
    position: relative;
    overflow: hidden;
  }
  .pc-btn::before {
    content:''; position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--rose), var(--lavender));
    opacity: 0; transition: opacity 0.22s;
  }
  .pc-btn span { position: relative; z-index: 1; }
  .pc-btn:hover { border-color: var(--rose); color: var(--rose); }
  .pc-btn.active {
    border-color: transparent;
    color: white;
    box-shadow: 0 4px 18px rgba(212,118,138,0.35);
  }
  .pc-btn.active::before { opacity: 1; }
 
  /* character type buttons - wider */
  .pc-char-btn { padding: 0.75rem 1.4rem; }
  .pc-char-icon { font-size: 1.1rem; display: block; margin-bottom: 0.25rem; }
 
  /* performer stepper */
  .pc-stepper {
    display: flex; align-items: center; gap: 1.2rem;
    margin-top: 0.4rem;
  }
  .pc-step-btn {
    width: 36px; height: 36px;
    border: 1px solid rgba(201,169,110,0.4);
    background: white; border-radius: 2px;
    font-size: 1.1rem; cursor: pointer; color: var(--gold);
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s; line-height: 1;
    font-family: var(--ff-sans);
  }
  .pc-step-btn:hover { background: var(--gold); color: white; border-color: var(--gold); }
  .pc-step-count {
    font-family: var(--ff-title); font-size: 1.8rem; color: var(--ink);
    min-width: 2rem; text-align: center;
  }
  .pc-step-label {
    font-family: var(--ff-sans); font-size: 0.72rem; color: var(--text);
    letter-spacing: 0.08em;
  }
 
  /* results card */
  .pc-result {
    position: sticky; top: 100px;
    background: var(--ink);
    border: 1px solid rgba(201,169,110,0.3);
    border-radius: 4px;
    padding: 2.4rem 2rem;
    color: white;
  }
  .pc-result-label {
    font-family: var(--ff-sans); font-size: 0.58rem; letter-spacing: 0.32em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem;
  }
  .pc-result-package {
    font-family: var(--ff-title); font-size: 1.25rem; letter-spacing: 0.04em;
    color: white; margin-bottom: 0.25rem; line-height: 1.3;
  }
  .pc-result-desc {
    font-family: var(--ff-sans); font-size: 0.75rem; color: rgba(255,255,255,0.5);
    margin-bottom: 1.8rem; line-height: 1.6;
  }
  .pc-price-row {
    display: flex; justify-content: space-between; align-items: baseline;
    padding: 0.7rem 0; border-bottom: 1px solid rgba(255,255,255,0.08);
  }
  .pc-price-row:last-of-type { border-bottom: none; }
  .pc-price-item {
    font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.08em; color: rgba(255,255,255,0.6);
  }
  .pc-price-val {
    font-family: var(--ff-serif); font-size: 1rem; color: rgba(255,255,255,0.85);
  }
  .pc-total-row {
    margin-top: 1.5rem;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(201,169,110,0.3);
    display: flex; justify-content: space-between; align-items: baseline;
  }
  .pc-total-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold);
  }
  .pc-total-price {
    font-family: var(--ff-title); font-size: 2.4rem; letter-spacing: 0.02em;
    background: linear-gradient(135deg, var(--gold-lt), var(--gold));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    transition: all 0.3s var(--ease-silk);
  }
  .pc-total-price.updating {
    transform: scale(0.92); opacity: 0.4;
  }
 
  .pc-features {
    list-style: none; margin-top: 1.8rem; margin-bottom: 1.8rem;
  }
  .pc-features li {
    display: flex; gap: 0.6rem; align-items: flex-start;
    font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.04em;
    color: rgba(255,255,255,0.65); padding: 0.35rem 0; line-height: 1.5;
  }
  .pc-features li::before { content: '✦'; color: var(--gold); font-size: 0.5rem; margin-top: 0.35rem; flex-shrink:0; }
 
  .pc-book-btn {
    display: block; width: 100%; text-align: center;
    font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1rem 1.5rem;
    background: linear-gradient(135deg, var(--rose), var(--lavender));
    color: white; border-radius: 2px;
    margin-top: 1.5rem;
    transition: opacity 0.2s, transform 0.2s;
    box-shadow: 0 4px 20px rgba(212,118,138,0.3);
  }
  .pc-book-btn:hover { opacity: 0.88; transform: translateY(-2px); }
 
  .pc-note {
    margin-top: 2.5rem; text-align: center;
    font-size: 0.85rem; color: var(--text); font-style: italic;
  }
 
  .pricing-note {
    margin-top: 2.5rem; text-align: center;
    font-size: 0.88rem; color: var(--text); font-style: italic;
  }
 
  @media (max-width: 860px) {
    .pricing-calculator { grid-template-columns: 1fr; }
    .pc-result { position: static; }
  }
 
  /* ── CTA BAND ─────────────────────────────────────────── */
  .cta-band {
    background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);
    padding: 6rem 2rem; text-align: center; position: relative; overflow: hidden;
  }
  .cta-band::before {
    content:''; position: absolute; inset:0;
    background: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.06'/%3E%3C/svg%3E");
    opacity: 0.5;
  }
  .cta-band * { position: relative; z-index: 1; }
  .cta-band .section-heading { color: white; max-width: 640px; margin: 0 auto; }
  .cta-band p { color: rgba(255,255,255,0.85); margin: 1.2rem auto 2.5rem; max-width: 480px; font-size: 1rem; }
  .cta-phone-big {
    font-family: var(--ff-title);
    font-size: clamp(2rem, 6vw, 4rem);
    color: white; letter-spacing: 0.06em;
    text-shadow: 0 2px 16px rgba(0,0,0,0.2);
    display: block; margin-bottom: 0.4rem;
  }
  .cta-phone-sub {
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: rgba(255,255,255,0.7); display: block; margin-bottom: 2rem;
  }
  .btn-white {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    background: white;
    color: var(--rose);
    border-radius: 2px;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 24px rgba(0,0,0,0.15);
  }
  .btn-white:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(0,0,0,0.2); }
 
  /* ── FOOTER ───────────────────────────────────────────── */
  footer {
    background: var(--ink);
    padding: 4rem 2rem 2rem;
    color: rgba(255,255,255,0.5);
    font-family: var(--ff-sans); font-size: 0.75rem;
  }
  .footer-inner {
    max-width: 1100px; margin: 0 auto;
    display: grid; grid-template-columns: 2fr 1fr 1fr;
    gap: 3rem; padding-bottom: 3rem;
    border-bottom: 1px solid rgba(201,169,110,0.15);
  }
  .footer-brand-name {
    font-family: var(--ff-title); font-size: 1.1rem; color: white;
    letter-spacing: 0.1em; margin-bottom: 0.8rem;
  }
  .footer-brand-tag { line-height: 1.7; max-width: 280px; }
  .footer-col-title {
    font-family: var(--ff-title); font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem;
  }
  .footer-links { list-style: none; line-height: 2.2; }
  .footer-links a { color: rgba(255,255,255,0.5); transition: color 0.25s; }
  .footer-links a:hover { color: var(--gold); }
  .footer-bottom {
    max-width: 1100px; margin: 2rem auto 0;
    display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;
    font-size: 0.65rem; letter-spacing: 0.1em;
  }
  .footer-disclaimer { max-width: 600px; line-height: 1.6; opacity: 0.5; }
 
  /* ── ANIMATIONS ───────────────────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes shimmer {
    0%   { opacity: 0.3; }
    50%  { opacity: 1; }
    100% { opacity: 0.3; }
  }
  .sparkle { animation: shimmer 2s infinite; }
  .sparkle:nth-child(2) { animation-delay: 0.4s; }
  .sparkle:nth-child(3) { animation-delay: 0.8s; }
  .sparkle:nth-child(4) { animation-delay: 1.2s; }
  .sparkle:nth-child(5) { animation-delay: 1.6s; }
 
  /* scroll reveal */
  .reveal {
    opacity: 0; transform: translateY(28px);
    transition: opacity 0.7s var(--ease-silk), transform 0.7s var(--ease-silk);
  }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
 
  /* ── MOBILE ───────────────────────────────────────────── */
  @media (max-width: 900px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { display: none; }
    .pillars { grid-template-columns: 1fr; gap: 2px; }
    .how-grid { grid-template-columns: 1fr; }
    .how-visual { display: none; }
    .characters-grid { grid-template-columns: repeat(2,1fr); }
    .testi-grid { grid-template-columns: 1fr; }
    .pricing-calculator { grid-template-columns: 1fr; }
    .footer-inner { grid-template-columns: 1fr; gap: 2rem; }
    .hero-photo-strip { display: none; }
  }
</style>
</head>
<body>
 
<!-- ══ NAVIGATION ══════════════════════════════════════════ -->
<nav id="nav">
  <a href="#" class="nav-logo">
    <span class="crown">✦</span>
    Sophia's Magical Princess Party
  </a>
  <ul class="nav-links" aria-label="Site navigation">
    <li><a href="#characters">Characters</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="#book" class="nav-cta">Book Now</a>
</nav>
 
<!-- ══ HERO ════════════════════════════════════════════════ -->
<section class="hero" id="top">
  <div class="hero-bg"></div>
  <div class="hero-arc hero-arc-1"></div>
  <div class="hero-arc hero-arc-2"></div>
  <div class="hero-arc hero-arc-3"></div>
 
  <!-- sparkle SVG layer -->
  <div class="sparkle-field" aria-hidden="true">
    <svg viewBox="0 0 1200 700" preserveAspectRatio="xMidYMid slice">
      <!-- 4-point star shape repeated -->
      <path class="sparkle" d="M200 120 L203 130 L213 133 L203 136 L200 146 L197 136 L187 133 L197 130Z" fill="#C9A96E" opacity="0.6"/>
      <path class="sparkle" d="M900 80  L903 90  L913 93  L903 96  L900 106 L897 96  L887 93  L897 90Z"  fill="#D4768A" opacity="0.5"/>
      <path class="sparkle" d="M1050 300 L1052 308 L1060 310 L1052 312 L1050 320 L1048 312 L1040 310 L1048 308Z" fill="#A88EC0" opacity="0.5"/>
      <path class="sparkle" d="M150 400 L152 408 L160 410 L152 412 L150 420 L148 412 L140 410 L148 408Z" fill="#7EB8D4" opacity="0.45"/>
      <path class="sparkle" d="M600 50  L602 58  L610 60  L602 62  L600 70  L598 62  L590 60  L598 58Z"  fill="#C9A96E" opacity="0.4"/>
      <circle cx="350" cy="600" r="2" fill="#D4768A" opacity="0.4"/>
      <circle cx="850" cy="550" r="2" fill="#C9A96E" opacity="0.35"/>
      <circle cx="100" cy="200" r="1.5" fill="#A88EC0" opacity="0.45"/>
      <circle cx="1100" cy="180" r="1.5" fill="#7EB8D4" opacity="0.4"/>
    </svg>
  </div>
 
  <p class="hero-eyebrow">South Houston's Premier Princess Experience</p>
  <h1 class="hero-title">Where Every Child Meets Their <em>Favorite Princess</em></h1>
  <p class="hero-subtitle">Professional actors in breathtaking, park-quality gowns bring the magic of beloved heroines directly to your child's celebration.</p>
 
  <div class="hero-ctas">
    <a href="#book" class="btn-primary">✦ &nbsp;Book a Princess</a>
    <a href="#characters" class="btn-ghost">Meet the Characters</a>
  </div>
 
  <p class="hero-phone">
    <small>Call to Schedule</small>
    (xxx) xxx-xxxx
  </p>
 
  <!-- photo strip: placeholder shapes representing real photos -->
  <div class="hero-photo-strip" aria-hidden="true">
    <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">👑</div>
    </figure>
    <figure style="background:linear-gradient(160deg,#F7C5D0,#D4768A)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">🌹</div>
    </figure>
    <figure style="background:linear-gradient(160deg,#D0B8E8,#A88EC0)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">✨</div>
    </figure>
  </div>
 
  <p class="since-badge"><span></span> Making Magic Real Since 2017 <span></span></p>
</section>
 
<!-- ══ PILLARS ══════════════════════════════════════════════ -->
<section class="section" id="about">
  <div class="section-inner">
    <div class="gold-rule reveal">What Makes Us Different</div>
    <div class="pillars">
      <div class="pillar reveal reveal-delay-1">
        <div class="pillar-icon">👗</div>
        <div class="pillar-title">Top-Quality Costumes</div>
        <p class="pillar-text">Every gown is crafted with the same eye-catching detail you'd expect at a world-class theme park — your guests will be speechless.</p>
      </div>
      <div class="pillar reveal reveal-delay-2">
        <div class="pillar-icon">🎭</div>
        <div class="pillar-title">World Class Performers</div>
        <p class="pillar-text">Our performers fully embody their characters. From their first hello to the royal farewell, you can expect a magical time.</p>
      </div>
      <div class="pillar reveal reveal-delay-3">
        <div class="pillar-icon">🎀</div>
        <div class="pillar-title">Unique Activities</div>
        <p class="pillar-text">Storytime, singalongs, royal decrees, and more! Each visit makes the birthday child feel like the hero of their own story.</p>
      </div>
    </div>
  </div>
</section>
 
<hr class="section-divider" />
 
<!-- ══ CHARACTERS ══════════════════════════════════════════ -->
<section class="section" id="characters">
  <div class="section-inner">
    <span class="section-label reveal">The Royal Court</span>
    <h2 class="section-heading reveal">Choose Your Princess</h2>
    <p class="section-body reveal">Ice queens, pixies, ocean adventurers and beyond! Our beloved heroines are ready to make your child's birthday unforgettable.</p>
 
    <div class="characters-grid">
      <div class="char-card reveal reveal-delay-1">
        <div class="char-color"></div>
        <div class="char-emoji">❄️</div>
        <div class="char-info">
          <span class="char-name">The Snow Queen</span>
          <span class="char-desc">Ice & Magic</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-2">
        <div class="char-color"></div>
        <div class="char-emoji">🌹</div>
        <div class="char-info">
          <span class="char-name">The Rose Princess</span>
          <span class="char-desc">Enchanted Tales</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-3">
        <div class="char-color"></div>
        <div class="char-emoji">🔮</div>
        <div class="char-info">
          <span class="char-name">The Lantern Princess</span>
          <span class="char-desc">Sun &amp; Adventure</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-3">
        <div class="char-color"></div>
        <div class="char-emoji">🌊</div>
        <div class="char-info">
          <span class="char-name">The Ocean Heroine</span>
          <span class="char-desc">Sea &amp; Song</span>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- ══ HOW IT WORKS ═════════════════════════════════════════ -->
<section class="section how" id="how">
  <div class="section-inner">
    <div class="how-grid">
      <div>
        <span class="section-label reveal">Simple &amp; Magical</span>
        <h2 class="section-heading reveal">How to Book Your Royal Visit</h2>
        <ol class="how-steps" aria-label="Booking steps">
          <li class="how-step reveal">
            <span class="step-num" aria-hidden="true">01</span>
            <div>
              <div class="step-title">Fill out the Booking Form</div>
              <p class="step-text">Reach out with the form below to contact our team.</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-1">
            <span class="step-num" aria-hidden="true">02</span>
            <div>
              <div class="step-title">Pick Your Date & Package</div>
              <p class="step-text">We'll get back with you to finalize your selection and answer any questions. You're on the schedule at this point!</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-2">
            <span class="step-num" aria-hidden="true">03</span>
            <div>
              <div class="step-title">Await the Arrival</div>
              <p class="step-text">On the day, your princess will arrive in full costume. Watch your child's eyes light up as the magic becomes real.</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-3">
            <span class="step-num" aria-hidden="true">04</span>
            <div>
              <div class="step-title">Memories Made</div>
              <p class="step-text">Photo moments, activities, and royal moments, your child will be talking about this birthday for years to come.</p>
            </div>
          </li>
        </ol>
 
        <div class="call-highlight reveal">
          <p>Still have questions? Feel free to call or text the number below. We'll get back to you as soon as possible to assist/</p>
          <div class="call-number">(xxx) xxx-xxxx</div>
        </div>
      </div>
 
      <div class="how-visual" aria-hidden="true">
        <div class="how-photo">
          <div class="how-photo-placeholder">
            <span>👸</span>
            Princess Visit
          </div>
        </div>
        <div class="how-photo">
          <div class="how-photo-placeholder">
            <span>🎂</span>
            Birthday Joy
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- ══ TESTIMONIALS ═════════════════════════════════════════ -->
<section class="section testimonials" id="testimonials">
  <div class="section-inner">
    <span class="section-label reveal">From Our Families</span>
    <h2 class="section-heading reveal" style="color:white;">What Parents Are Saying</h2>
 
    <div class="testi-grid">
      <div class="testi-card reveal reveal-delay-1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">They really know how to make the birthday kiddo feel special!</p>
        <p class="testi-author">Inshirah Barakat — Google</p>
      </div>
      <div class="testi-card reveal reveal-delay-2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Great third experience using Sophia's! Love how in character they always are and very interactive. Highly recommend!</p>
        <p class="testi-author">Jessica Lyne — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-3">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Rapunzel was kind, genuine, and my kiddo was absolutely delighted by the visit!</p>
        <p class="testi-author">Becca Popland — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Our little princess received the best personal video message from The Snow Queen! She absolutely loved it!</p>
        <p class="testi-author">Jimee Jensen-Caudle — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Hands down the best present I could have ever bought my granddaughter for her birthday!</p>
        <p class="testi-author">James Scurlock — Google</p>
      </div>
      <div class="testi-card reveal reveal-delay-3" style="display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;border-style:dashed;gap:0.5rem;">
        <div style="font-size:2rem;">⭐</div>
        <p style="color:rgba(255,255,255,0.5);font-size:0.8rem;font-family:var(--ff-sans);">Proudly serving South Houston families since 2017</p>
        <a href="#book" class="btn-white" style="margin-top:0.5rem;font-size:0.65rem;padding:0.8rem 1.6rem;">Leave a Review</a>
      </div>
    </div>
  </div>
</section>
 
<!-- ══ PRICING ══════════════════════════════════════════════ -->
<section class="section" id="pricing">
  <div class="section-inner">
    <span class="section-label reveal">Transparent &amp; Simple</span>
    <h2 class="section-heading reveal">Build Your Royal Package</h2>
    <p class="section-body reveal">Customize your perfect party by selecting your character type, duration, and number of performers — and see your price instantly.</p>
 
    <div class="pricing-calculator">
 
      <!-- LEFT: Selectors -->
      <div class="pc-selectors reveal">
 
        <!-- Character Type -->
        <div class="pc-group">
          <span class="pc-group-label">✦ &nbsp;Type of Character</span>
          <div class="pc-options">
            <button class="pc-btn pc-char-btn active" data-group="type" data-val="princess" onclick="pcSelect(this)">
              <span class="pc-char-icon">👑</span>
              <span>Princess</span>
            </button>
            <button class="pc-btn pc-char-btn" data-group="type" data-val="kpop" onclick="pcSelect(this)">
              <span class="pc-char-icon">🎤</span>
              <span>K-Pop Star</span>
            </button>
            <button class="pc-btn pc-char-btn" data-group="type" data-val="impersonator" onclick="pcSelect(this)">
              <span class="pc-char-icon">🌟</span>
              <span>Impersonator</span>
            </button>
          </div>
        </div>
 
        <!-- Duration -->
        <div class="pc-group">
          <span class="pc-group-label">✦ &nbsp;Duration</span>
          <div class="pc-options">
            <button class="pc-btn active" data-group="duration" data-val="30" onclick="pcSelect(this)"><span>30 Min</span></button>
            <button class="pc-btn" data-group="duration" data-val="60" onclick="pcSelect(this)"><span>1 Hour</span></button>
            <button class="pc-btn" data-group="duration" data-val="120" onclick="pcSelect(this)"><span>2 Hours</span></button>
          </div>
        </div>
 
        <!-- Number of Performers -->
        <div class="pc-group" id="pc-performer-group">
          <span class="pc-group-label">✦ &nbsp;Number of Performers</span>
          <div class="pc-stepper">
            <button class="pc-step-btn" onclick="pcStep(-1)">−</button>
            <span class="pc-step-count" id="pc-performer-count">1</span>
            <button class="pc-step-btn" onclick="pcStep(1)">+</button>
            <span class="pc-step-label">performer<span id="pc-plural"></span></span>
          </div>
        </div>
 
        <!-- What's included note -->
        <div style="margin-top:1rem; padding:1.5rem 1.8rem; background:white; border:1px solid rgba(201,169,110,0.2); border-radius:4px;">
          <div style="font-family:var(--ff-sans);font-size:0.6rem;letter-spacing:0.3em;text-transform:uppercase;color:var(--gold);margin-bottom:0.8rem;">✦ &nbsp;Good to Know</div>
          <ul style="list-style:none;font-size:0.88rem;color:var(--text);line-height:1.9;">
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;30-min visits omit the sing-along</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;Makeovers require 2 hrs for 6+ children</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;Travel fee may apply based on location</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;All performers are fully costumed &amp; in-character</li>
          </ul>
        </div>
      </div>
 
      <!-- RIGHT: Result Card -->
      <div class="pc-result reveal reveal-delay-2">
        <div class="pc-result-label">Your Estimate</div>
        <div class="pc-result-package" id="pc-package-name">The Royal Greeting</div>
        <div class="pc-result-desc" id="pc-package-desc">Princess · 30 Minutes · 1 Performer</div>
 
        <div class="pc-price-row">
          <span class="pc-price-item">Base rate</span>
          <span class="pc-price-val" id="pc-base-val">$150</span>
        </div>
        <div class="pc-price-row">
          <span class="pc-price-item">Additional performer(s)</span>
          <span class="pc-price-val" id="pc-add-performer-val">—</span>
        </div>
        <div class="pc-price-row">
          <span class="pc-price-item">Character premium</span>
          <span class="pc-price-val" id="pc-char-premium-val">Included</span>
        </div>
 
        <div class="pc-total-row">
          <span class="pc-total-label">Total Estimate</span>
          <span class="pc-total-price" id="pc-total">$150</span>
        </div>
 
        <ul class="pc-features" id="pc-features-list">
          <li>In-character princess actress</li>
          <li>Meet &amp; greet with birthday child</li>
          <li>Photo opportunities</li>
          <li>Royal birthday blessing</li>
        </ul>
 
        <a href="#book" class="pc-book-btn">Reserve This Package &rarr;</a>
 
        <p style="font-family:var(--ff-sans);font-size:0.65rem;color:rgba(255,255,255,0.35);text-align:center;margin-top:1rem;line-height:1.6;">
          Estimates are approximate. Final pricing confirmed during booking. Travel fees may apply.
        </p>
      </div>
 
    </div><!-- /.pricing-calculator -->
 
    <p class="pricing-note reveal">All packages include a fully costumed performer in character throughout your event. We proudly serve the South Houston area.</p>
  </div>
</section>
 
<script>
(function() {
  // ── PRICING DATA ─────────────────────────────────────────
  const BASE = { 30: 150, 60: 225, 120: 350 };
  const EXTRA_PERFORMER = { 30: 100, 60: 150, 120: 200 };
  const CHAR_PREMIUM = { princess: 0, kpop: 50, impersonator: 75 };
  const CHAR_PREMIUM_LABEL = { princess: 'Included', kpop: '+$50', impersonator: '+$75' };
 
  // Max performers per type
  const MAX_PERFORMERS = { princess: 4, kpop: 3, impersonator: 1 };
 
  const PACKAGE_NAMES = {
    princess: { 30: 'The Royal Greeting', 60: 'The Enchanted Party', 120: 'The Magical Kingdom' },
    kpop:     { 30: 'The Pop Showcase',   60: 'The Idol Experience', 120: 'The K-Pop Extravaganza' },
    impersonator: { 30: 'The Star Appearance', 60: 'The Celebrity Bash', 120: 'The Superstar Soirée' }
  };
 
  const FEATURES = {
    princess: {
      30:  ['In-character princess actress','Meet & greet with birthday child','Photo opportunities','Royal birthday blessing'],
      60:  ['Full character immersion','Storytime & singalong','Royal coronation ceremony','Photo opportunities','Personalized attention for birthday child'],
      120: ['Extended character experience','Full activity suite','Royal games & crafts','Coronation ceremony','Makeover activity (6+ children require 2 hrs)','Group singalong & dancing']
    },
    kpop: {
      30:  ['K-Pop idol in full costume','High-energy mini performance','Fan photo experience','Group song moment'],
      60:  ['Full K-Pop performance set','Dance-along with guests','Costume photo ops','Fan interaction time','Birthday song performance'],
      120: ['Extended idol experience','Multiple performance segments','Dance tutorial for guests','Group fan photo session','Personalized fan card signing','Birthday surprise moment']
    },
    impersonator: {
      30:  ['Celebrity look-alike in full costume','Meet & greet photo moment','In-character performance','Birthday recognition'],
      60:  ['Full celebrity character experience','Live performance/singing (if applicable)','Photo opportunities','Interactive fan moment','Personalized birthday greeting'],
      120: ['Extended celebrity appearance','Multiple performance moments','Guest interaction time','Costume photo experience','Games themed to the celebrity','Autographed keepsake']
    }
  };
 
  // State
  let state = { type: 'princess', duration: 30, performers: 1 };
 
  window.pcSelect = function(btn) {
    const group = btn.dataset.group;
    const val = btn.dataset.val;
    btn.closest('.pc-options').querySelectorAll('.pc-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    state[group] = group === 'duration' ? parseInt(val) : val;
 
    if (group === 'type') {
      const max = MAX_PERFORMERS[state.type];
      const performerGroup = document.getElementById('pc-performer-group');
 
      if (state.type === 'impersonator') {
        // Lock to 1 and hide the stepper
        state.performers = 1;
        performerGroup.style.display = 'none';
      } else {
        performerGroup.style.display = '';
        // Clamp performers to new max
        if (state.performers > max) state.performers = max;
      }
      document.getElementById('pc-performer-count').textContent = state.performers;
      document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : '';
    }
 
    updateCalc();
  };
 
  window.pcStep = function(dir) {
    const max = MAX_PERFORMERS[state.type];
    state.performers = Math.min(max, Math.max(1, state.performers + dir));
    document.getElementById('pc-performer-count').textContent = state.performers;
    document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : '';
    updateCalc();
  };
 
  function updateCalc() {
    const { type, duration, performers } = state;
 
    const base     = BASE[duration];
    const addPerf  = performers > 1 ? EXTRA_PERFORMER[duration] * (performers - 1) : 0;
    const charPrem = CHAR_PREMIUM[type];
    const total    = base + addPerf + charPrem;
 
    const totalEl = document.getElementById('pc-total');
    totalEl.classList.add('updating');
    setTimeout(() => {
      totalEl.textContent = '$' + total.toLocaleString();
      totalEl.classList.remove('updating');
    }, 180);
 
    const durLabel = duration === 30 ? '30 Minutes' : duration === 60 ? '1 Hour' : '2 Hours';
    const typeLabel = type === 'princess' ? 'Princess' : type === 'kpop' ? 'K-Pop Star' : 'Impersonator';
 
    document.getElementById('pc-package-name').textContent = PACKAGE_NAMES[type][duration];
    document.getElementById('pc-package-desc').textContent =
      typeLabel + ' · ' + durLabel + ' · ' + performers + ' Performer' + (performers > 1 ? 's' : '');
 
    document.getElementById('pc-base-val').textContent = '$' + base;
    document.getElementById('pc-add-performer-val').textContent = addPerf > 0 ? '$' + addPerf : '—';
    document.getElementById('pc-char-premium-val').textContent = CHAR_PREMIUM_LABEL[type];
 
    const ul = document.getElementById('pc-features-list');
    ul.innerHTML = FEATURES[type][duration].map(f => `<li>${f}</li>`).join('');
  }
})();
</script>
 
<!-- ══ FAQ ══════════════════════════════════════════════════ -->
<section class="section" id="faq" style="background:#F9F4F7;">
  <div class="section-inner">
    <span class="section-label reveal">Questions &amp; Answers</span>
    <h2 class="section-heading reveal">Frequently Asked</h2>
 
    <div style="margin-top:3rem;max-width:720px;" class="reveal">
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          What area do you serve? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We proudly serve the South Houston area and surrounding communities. Call us to confirm your specific location when booking.</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          How far in advance should I book? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We recommend booking 2–4 weeks in advance, especially for weekend dates which fill up quickly. Give us a call to check availability!</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Do you offer video messages? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Yes! Personalized video messages from your chosen princess are available as an add-on. Perfect for birthdays, holidays, or just a magical surprise.</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Are your performers background-checked? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Absolutely. The safety and comfort of your children is our top priority. All performers are vetted, professional, and experienced in working with children.</p>
      </details>
      <details style="padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Which characters are available? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We have a rotating roster of beloved heroine-inspired characters. Call us to find out which princesses are currently available for your date!</p>
      </details>
    </div>
  </div>
</section>
 
<!-- ══ CTA BAND ═════════════════════════════════════════════ -->
<section class="cta-band" id="book">
  <span class="section-label" style="color:rgba(255,255,255,0.7)">Ready to Create Magic?</span>
  <h2 class="section-heading" style="max-width:640px;margin:0.8rem auto 0;">Book Your Princess Today</h2>
  <p>The most magical birthday party your child has ever had is just one phone call away. We'd love to hear about your celebration!</p>
  <a class="cta-phone-big" href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a>
  <span class="cta-phone-sub">Monday – Saturday, 9am – 7pm</span>
  <a href="tel:xxxxxxxxxx" class="btn-white">✦ &nbsp;Call to Book Now</a>
</section>
 
<!-- ══ FOOTER ═══════════════════════════════════════════════ -->
<footer>
  <div class="footer-inner">
    <div>
      <div class="footer-brand-name">✦ Sophia's Magical Princess Party</div>
      <p class="footer-brand-tag">Bringing beloved heroine characters to life for children's celebrations across the South Houston area since 2017.</p>
    </div>
    <div>
      <div class="footer-col-title">Navigate</div>
      <ul class="footer-links">
        <li><a href="#characters">Characters</a></li>
        <li><a href="#how">How It Works</a></li>
        <li><a href="#pricing">Pricing</a></li>
        <li><a href="#testimonials">Reviews</a></li>
        <li><a href="#faq">FAQ</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">Contact</div>
      <ul class="footer-links">
        <li><a href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a></li>
        <li>South Houston, TX</li>
        <li>Mon–Sat, 9am–7pm</li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 Sophia's Magical Princess Party. All rights reserved.</span>
    <span class="footer-disclaimer">We offer unique original characters inspired by classic stories and fables. We are a private company unaffiliated with any major production company or theme park. Any similarity to trademarked characters is coincidental.</span>
  </div>
</footer>
 
<script>
  // ── NAV scroll effect
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  }, { passive: true });
 
  // ── Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
  }, { threshold: 0.12 });
  reveals.forEach(el => io.observe(el));
 
  // ── FAQ caret toggle
  document.querySelectorAll('details').forEach(d => {
    d.addEventListener('toggle', () => {
      const icon = d.querySelector('summary span');
      if (icon) icon.textContent = d.open ? '−' : '+';
    });
  });
</script>
</body>
</html>
'''

K-pop should have a max of 3 performers, impersonator is locked to 1 performers so user selection on count should be hidden when impersonator is selected. Max time is 2 hours for all options.

Read a file, edited a file, and 2 more tools

All three changes are in:

- **3 Hours+ removed** — duration options are now 30 Min, 1 Hour, and 2 Hours only, across all character types.
- **K-Pop capped at 3 performers** — the `+` button won’t go above 3 when K-Pop is selected. If a user has 4 set from Princess and then switches to K-Pop, it clamps down to 3 automatically.
- **Impersonator locked to 1 & stepper hidden** — switching to Impersonator hides the entire performer group, resets to 1, and it reappears when switching back to Princess or K-Pop.

'''html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Sophia's Magical Princess Party — South Houston</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Cinzel:wght@400;500;600&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" />
<style>
  /* ── TOKENS ───────────────────────────────────────────── */
  :root {
    --gold:      #C9A96E;
    --gold-lt:   #E8D5A3;
    --rose:      #D4768A;
    --rose-lt:   #F2C4CF;
    --lavender:  #A88EC0;
    --sky:       #7EB8D4;
    --cream:     #FAF6F0;
    --ink:       #1A1118;
    --ink-soft:  #3D2B3A;
    --text:      #4A3A46;

    --ff-title:  'Cinzel', serif;
    --ff-serif:  'Cormorant Garamond', serif;
    --ff-sans:   'Jost', sans-serif;

    --ease-silk: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  /* ── RESET ────────────────────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--cream);
    color: var(--text);
    font-family: var(--ff-serif);
    font-size: 18px;
    line-height: 1.7;
    overflow-x: hidden;
  }
  img { display: block; max-width: 100%; }
  a  { color: inherit; text-decoration: none; }

  /* ── STAR / SPARKLE SVG DEFS ──────────────────────────── */
  .sparkle-field {
    position: absolute; inset: 0; pointer-events: none; overflow: hidden;
  }
  .sparkle-field svg { width: 100%; height: 100%; }

  /* ── UTILITY ──────────────────────────────────────────── */
  .visually-hidden { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0,0,0,0); }
  .gold-rule {
    display: flex; align-items: center; gap: 1rem;
    color: var(--gold); font-family: var(--ff-title); letter-spacing: 0.25em; font-size: 0.6rem; text-transform: uppercase;
  }
  .gold-rule::before, .gold-rule::after { content:''; flex:1; height:1px; background: linear-gradient(90deg, transparent, var(--gold-lt), transparent); }

  /* ── NAVIGATION ───────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    background: transparent;
    transition: background 0.4s var(--ease-silk), box-shadow 0.4s;
  }
  nav.scrolled {
    background: rgba(250,246,240,0.96);
    box-shadow: 0 1px 24px rgba(26,17,24,0.08);
    backdrop-filter: blur(8px);
  }
  .nav-logo {
    font-family: var(--ff-title);
    font-size: 1rem;
    letter-spacing: 0.15em;
    color: var(--ink);
    display: flex; align-items: center; gap: 0.6rem;
  }
  .nav-logo .crown { font-size: 1.2rem; }
  .nav-links {
    display: flex; gap: 2.4rem; list-style: none;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;
    letter-spacing: 0.18em; text-transform: uppercase;
  }
  .nav-links a {
    color: var(--ink-soft);
    position: relative;
    transition: color 0.25s;
  }
  .nav-links a::after {
    content:''; position: absolute; left:0; bottom:-3px; width:0; height:1px;
    background: var(--gold); transition: width 0.3s var(--ease-silk);
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-links a:hover::after { width: 100%; }
  .nav-cta {
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.18em; text-transform: uppercase;
    padding: 0.65rem 1.6rem;
    border: 1px solid var(--gold);
    color: var(--gold);
    transition: background 0.3s, color 0.3s;
    border-radius: 2px;
  }
  .nav-cta:hover { background: var(--gold); color: var(--cream); }

  /* ── HERO ─────────────────────────────────────────────── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    text-align: center;
    padding: 8rem 2rem 6rem;
    overflow: hidden;
  }

  /* layered gradient background */
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%,   rgba(212,118,138,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 60% 70% at 15% 60%,  rgba(168,142,192,0.14) 0%, transparent 65%),
      radial-gradient(ellipse 55% 50% at 85% 55%,  rgba(126,184,212,0.12) 0%, transparent 60%),
      linear-gradient(175deg, #FDF9F4 0%, #F7EEF5 50%, #EFF3F9 100%);
  }
  /* grain overlay */
  .hero-bg::after {
    content: '';
    position: absolute; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
    opacity: 0.6;
  }

  /* decorative arcs */
  .hero-arc {
    position: absolute; border-radius: 50%;
    border: 1px solid rgba(201,169,110,0.25);
    pointer-events: none;
  }
  .hero-arc-1 { width: 500px; height: 500px; top: 50%; left: 50%; transform: translate(-50%,-50%); }
  .hero-arc-2 { width: 720px; height: 720px; top: 50%; left: 50%; transform: translate(-50%,-50%); }
  .hero-arc-3 { width: 960px; height: 960px; top: 50%; left: 50%; transform: translate(-50%,-50%); opacity: 0.5; }

  .hero-eyebrow {
    font-family: var(--ff-sans); font-size: 0.65rem; font-weight: 400;
    letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1.6rem;
    opacity: 0; animation: fadeUp 0.8s 0.2s var(--ease-silk) forwards;
  }
  .hero-title {
    font-family: var(--ff-title);
    font-size: clamp(2.8rem, 7vw, 6rem);
    font-weight: 500;
    line-height: 1.12;
    color: var(--ink);
    letter-spacing: 0.02em;
    max-width: 820px;
    opacity: 0; animation: fadeUp 0.9s 0.35s var(--ease-silk) forwards;
  }
  .hero-title em {
    font-style: italic;
    background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 50%, var(--sky) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-subtitle {
    margin-top: 1.6rem;
    font-family: var(--ff-serif); font-size: 1.2rem; font-weight: 300;
    color: var(--text); max-width: 520px; line-height: 1.7;
    opacity: 0; animation: fadeUp 0.9s 0.5s var(--ease-silk) forwards;
  }
  .hero-ctas {
    display: flex; gap: 1.2rem; margin-top: 2.8rem; flex-wrap: wrap; justify-content: center;
    opacity: 0; animation: fadeUp 0.9s 0.65s var(--ease-silk) forwards;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    background: var(--gold);
    color: var(--cream);
    border-radius: 2px;
    transition: background 0.3s, transform 0.2s;
    box-shadow: 0 4px 24px rgba(201,169,110,0.35);
  }
  .btn-primary:hover { background: #b8935a; transform: translateY(-2px); }
  .btn-ghost {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    border: 1px solid rgba(201,169,110,0.5);
    color: var(--ink-soft);
    border-radius: 2px;
    transition: border-color 0.3s, color 0.3s, transform 0.2s;
  }
  .btn-ghost:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }

  .hero-phone {
    margin-top: 2rem;
    font-family: var(--ff-title);
    font-size: 1.4rem; letter-spacing: 0.08em;
    color: var(--rose);
    opacity: 0; animation: fadeUp 0.9s 0.8s var(--ease-silk) forwards;
  }
  .hero-phone small {
    display: block; font-family: var(--ff-sans); font-size: 0.6rem;
    letter-spacing: 0.25em; text-transform: uppercase; color: var(--text); margin-bottom: 0.3rem;
  }

  .hero-photo-strip {
    display: flex; gap: 1rem; margin-top: 3.5rem; justify-content: center;
    opacity: 0; animation: fadeUp 1s 0.9s var(--ease-silk) forwards;
  }
  .hero-photo-strip figure {
    width: 120px; height: 160px; overflow: hidden; border-radius: 60px;
    border: 2px solid rgba(201,169,110,0.4);
    flex-shrink: 0;
    box-shadow: 0 8px 32px rgba(26,17,24,0.12);
    transition: transform 0.4s var(--ease-silk);
  }
  .hero-photo-strip figure:nth-child(2) { margin-top: -20px; border-color: rgba(212,118,138,0.5); }
  .hero-photo-strip figure:nth-child(3) { margin-top: 10px;  border-color: rgba(168,142,192,0.5); }
  .hero-photo-strip figure:hover { transform: scale(1.05) translateY(-6px); }
  .hero-photo-strip img { width: 100%; height: 100%; object-fit: cover; }

  /* ── SINCE BADGE ──────────────────────────────────────── */
  .since-badge {
    position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold); opacity: 0.7; display: flex; align-items: center; gap: 0.5rem;
  }
  .since-badge span { display: inline-block; width: 24px; height: 1px; background: var(--gold-lt); }

  /* ── DIVIDER ──────────────────────────────────────────── */
  .section-divider {
    width: 100%; max-width: 1100px; margin: 0 auto;
    border: none; border-top: 1px solid rgba(201,169,110,0.2);
  }

  /* ── SECTION WRAPPER ──────────────────────────────────── */
  .section { padding: 7rem 2rem; }
  .section-inner { max-width: 1100px; margin: 0 auto; }

  .section-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.35em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem; display: block;
  }
  .section-heading {
    font-family: var(--ff-title);
    font-size: clamp(1.8rem, 4vw, 3rem);
    font-weight: 500;
    line-height: 1.18;
    color: var(--ink);
    letter-spacing: 0.02em;
    max-width: 560px;
  }
  .section-body {
    font-size: 1.05rem; line-height: 1.8; color: var(--text); max-width: 520px; margin-top: 1.2rem;
  }

  /* ── PILLARS (3-col) ──────────────────────────────────── */
  .pillars {
    display: grid; grid-template-columns: repeat(3,1fr); gap: 2px;
    margin-top: 5rem;
  }
  .pillar {
    padding: 3rem 2.4rem;
    background: white;
    position: relative;
    overflow: hidden;
    transition: transform 0.35s var(--ease-silk), box-shadow 0.35s;
  }
  .pillar::before {
    content:'';
    position: absolute; top:0; left:0; right:0; height:3px;
    background: linear-gradient(90deg, var(--rose), var(--lavender));
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.4s var(--ease-silk);
  }
  .pillar:hover::before { transform: scaleX(1); }
  .pillar:hover { transform: translateY(-6px); box-shadow: 0 16px 48px rgba(26,17,24,0.10); }
  .pillar-icon { font-size: 2rem; margin-bottom: 1.2rem; }
  .pillar-title {
    font-family: var(--ff-title); font-size: 1.05rem; letter-spacing: 0.05em;
    color: var(--ink); margin-bottom: 0.6rem;
  }
  .pillar-text { font-size: 0.95rem; color: var(--text); line-height: 1.75; }

  /* ── HOW IT WORKS ─────────────────────────────────────── */
  .how {
    background: linear-gradient(160deg, #F7EFF8 0%, #EEF4FA 100%);
    position: relative; overflow: hidden;
  }
  .how::before {
    content:'';
    position: absolute; top:-200px; right:-200px;
    width: 600px; height: 600px; border-radius: 50%;
    background: radial-gradient(circle, rgba(212,118,138,0.12), transparent 70%);
  }
  .how-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 5rem; align-items: center;
  }
  .how-steps { list-style: none; margin-top: 2.5rem; }
  .how-step {
    display: flex; gap: 2rem; align-items: flex-start;
    padding: 1.8rem 0; border-bottom: 1px solid rgba(201,169,110,0.2);
  }
  .how-step:last-child { border-bottom: none; }
  .step-num {
    font-family: var(--ff-title);
    font-size: 2.5rem; font-weight: 500; line-height: 1;
    color: rgba(201,169,110,0.35); flex-shrink: 0; min-width: 2.5rem; text-align: center;
  }
  .step-title {
    font-family: var(--ff-title); font-size: 1rem; color: var(--ink); margin-bottom: 0.3rem; letter-spacing: 0.04em;
  }
  .step-text { font-size: 0.9rem; color: var(--text); line-height: 1.7; }
  .how-visual {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;
  }
  .how-photo {
    border-radius: 4px; overflow: hidden;
    box-shadow: 0 8px 32px rgba(26,17,24,0.1);
    aspect-ratio: 3/4; background: #e8e0ec;
    position: relative;
  }
  .how-photo:nth-child(2) { margin-top: 2rem; }
  .how-photo img { width: 100%; height: 100%; object-fit: cover; }
  .how-photo-placeholder {
    position: absolute; inset: 0;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    gap: 0.5rem; color: rgba(60,40,60,0.3);
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
  }
  .how-photo-placeholder span { font-size: 2.5rem; }
  .call-highlight {
    margin-top: 3rem;
    padding: 2rem 2.5rem;
    background: white;
    border-left: 3px solid var(--gold);
    border-radius: 2px;
    box-shadow: 0 4px 20px rgba(26,17,24,0.06);
  }
  .call-highlight p { font-size: 0.9rem; color: var(--text); line-height: 1.7; margin-bottom: 0.8rem; }
  .call-number {
    font-family: var(--ff-title); font-size: 1.5rem; color: var(--rose); letter-spacing: 0.08em;
  }

  /* ── CHARACTERS ───────────────────────────────────────── */
  .characters-grid {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem; margin-top: 3.5rem;
  }
  .char-card {
    position: relative; overflow: hidden; border-radius: 4px;
    aspect-ratio: 3/4;
    background: #f0e8f0;
    cursor: pointer;
    box-shadow: 0 4px 16px rgba(26,17,24,0.08);
    transition: transform 0.4s var(--ease-silk), box-shadow 0.4s;
  }
  .char-card:hover { transform: translateY(-8px) scale(1.02); box-shadow: 0 20px 56px rgba(26,17,24,0.15); }
  .char-card::before {
    content:''; position: absolute; inset: 0; z-index: 1;
    background: linear-gradient(0deg, rgba(26,17,24,0.7) 0%, rgba(26,17,24,0.1) 60%, transparent 100%);
  }
  .char-color { position: absolute; inset:0; }
  .char-card:nth-child(1) .char-color { background: linear-gradient(160deg, #B5D4E8 0%, #7EB8D4 100%); }
  .char-card:nth-child(2) .char-color { background: linear-gradient(160deg, #F7C5D0 0%, #D4768A 100%); }
  .char-card:nth-child(3) .char-color { background: linear-gradient(160deg, #D0B8E8 0%, #A88EC0 100%); }
  .char-card:nth-child(4) .char-color { background: linear-gradient(160deg, #E8E0A0 0%, #C9A96E 100%); }
  .char-emoji { position: absolute; top: 50%; left: 50%; transform: translate(-50%,-60%); font-size: 4rem; z-index: 0; opacity: 0.4; }
  .char-info {
    position: absolute; bottom: 0; left: 0; right: 0; padding: 1.5rem;
    z-index: 2;
  }
  .char-name {
    font-family: var(--ff-title); font-size: 0.95rem; letter-spacing: 0.08em;
    color: white; display: block; margin-bottom: 0.2rem;
  }
  .char-desc { font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: rgba(255,255,255,0.7); }

  /* ── TESTIMONIALS ─────────────────────────────────────── */
  .testimonials { background: var(--ink); }
  .testimonials .section-label { color: var(--gold-lt); }
  .testimonials .section-heading { color: white; }
  .testi-grid {
    display: grid; grid-template-columns: repeat(3,1fr);
    gap: 1.5rem; margin-top: 3.5rem;
  }
  .testi-card {
    padding: 2.2rem;
    border: 1px solid rgba(201,169,110,0.2);
    border-radius: 2px;
    position: relative;
    transition: border-color 0.3s, background 0.3s;
  }
  .testi-card:hover { border-color: rgba(201,169,110,0.5); background: rgba(255,255,255,0.03); }
  .testi-quote {
    font-family: var(--ff-serif); font-size: 1.05rem; font-style: italic;
    color: rgba(255,255,255,0.85); line-height: 1.7; margin-bottom: 1.4rem;
  }
  .testi-quote::before { content: '\201C'; font-size: 2rem; color: var(--gold); line-height: 0; vertical-align: -0.5rem; margin-right: 0.2rem; }
  .testi-author {
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold);
  }
  .testi-stars { color: var(--gold); font-size: 0.8rem; margin-bottom: 0.8rem; letter-spacing: 0.1em; }

  /* ── PRICING CALCULATOR ───────────────────────────────── */
  .pricing-calculator {
    margin-top: 3.5rem;
    display: grid;
    grid-template-columns: 1fr 340px;
    gap: 2.5rem;
    align-items: start;
  }

  /* selector groups */
  .pc-group { margin-bottom: 2rem; }
  .pc-group-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem; display: block;
  }
  .pc-options {
    display: flex; flex-wrap: wrap; gap: 0.6rem;
  }
  .pc-btn {
    font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 400;
    letter-spacing: 0.12em; text-transform: uppercase;
    padding: 0.6rem 1.2rem;
    border: 1px solid rgba(201,169,110,0.35);
    background: white;
    color: var(--text);
    border-radius: 2px;
    cursor: pointer;
    transition: all 0.22s var(--ease-silk);
    position: relative;
    overflow: hidden;
  }
  .pc-btn::before {
    content:''; position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--rose), var(--lavender));
    opacity: 0; transition: opacity 0.22s;
  }
  .pc-btn span { position: relative; z-index: 1; }
  .pc-btn:hover { border-color: var(--rose); color: var(--rose); }
  .pc-btn.active {
    border-color: transparent;
    color: white;
    box-shadow: 0 4px 18px rgba(212,118,138,0.35);
  }
  .pc-btn.active::before { opacity: 1; }

  /* character type buttons - wider */
  .pc-char-btn { padding: 0.75rem 1.4rem; }
  .pc-char-icon { font-size: 1.1rem; display: block; margin-bottom: 0.25rem; }

  /* performer stepper */
  .pc-stepper {
    display: flex; align-items: center; gap: 1.2rem;
    margin-top: 0.4rem;
  }
  .pc-step-btn {
    width: 36px; height: 36px;
    border: 1px solid rgba(201,169,110,0.4);
    background: white; border-radius: 2px;
    font-size: 1.1rem; cursor: pointer; color: var(--gold);
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s; line-height: 1;
    font-family: var(--ff-sans);
  }
  .pc-step-btn:hover { background: var(--gold); color: white; border-color: var(--gold); }
  .pc-step-count {
    font-family: var(--ff-title); font-size: 1.8rem; color: var(--ink);
    min-width: 2rem; text-align: center;
  }
  .pc-step-label {
    font-family: var(--ff-sans); font-size: 0.72rem; color: var(--text);
    letter-spacing: 0.08em;
  }

  /* results card */
  .pc-result {
    position: sticky; top: 100px;
    background: var(--ink);
    border: 1px solid rgba(201,169,110,0.3);
    border-radius: 4px;
    padding: 2.4rem 2rem;
    color: white;
  }
  .pc-result-label {
    font-family: var(--ff-sans); font-size: 0.58rem; letter-spacing: 0.32em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem;
  }
  .pc-result-package {
    font-family: var(--ff-title); font-size: 1.25rem; letter-spacing: 0.04em;
    color: white; margin-bottom: 0.25rem; line-height: 1.3;
  }
  .pc-result-desc {
    font-family: var(--ff-sans); font-size: 0.75rem; color: rgba(255,255,255,0.5);
    margin-bottom: 1.8rem; line-height: 1.6;
  }
  .pc-price-row {
    display: flex; justify-content: space-between; align-items: baseline;
    padding: 0.7rem 0; border-bottom: 1px solid rgba(255,255,255,0.08);
  }
  .pc-price-row:last-of-type { border-bottom: none; }
  .pc-price-item {
    font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.08em; color: rgba(255,255,255,0.6);
  }
  .pc-price-val {
    font-family: var(--ff-serif); font-size: 1rem; color: rgba(255,255,255,0.85);
  }
  .pc-total-row {
    margin-top: 1.5rem;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(201,169,110,0.3);
    display: flex; justify-content: space-between; align-items: baseline;
  }
  .pc-total-label {
    font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--gold);
  }
  .pc-total-price {
    font-family: var(--ff-title); font-size: 2.4rem; letter-spacing: 0.02em;
    background: linear-gradient(135deg, var(--gold-lt), var(--gold));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    transition: all 0.3s var(--ease-silk);
  }
  .pc-total-price.updating {
    transform: scale(0.92); opacity: 0.4;
  }

  .pc-features {
    list-style: none; margin-top: 1.8rem; margin-bottom: 1.8rem;
  }
  .pc-features li {
    display: flex; gap: 0.6rem; align-items: flex-start;
    font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.04em;
    color: rgba(255,255,255,0.65); padding: 0.35rem 0; line-height: 1.5;
  }
  .pc-features li::before { content: '✦'; color: var(--gold); font-size: 0.5rem; margin-top: 0.35rem; flex-shrink:0; }

  .pc-book-btn {
    display: block; width: 100%; text-align: center;
    font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1rem 1.5rem;
    background: linear-gradient(135deg, var(--rose), var(--lavender));
    color: white; border-radius: 2px;
    margin-top: 1.5rem;
    transition: opacity 0.2s, transform 0.2s;
    box-shadow: 0 4px 20px rgba(212,118,138,0.3);
  }
  .pc-book-btn:hover { opacity: 0.88; transform: translateY(-2px); }

  .pc-note {
    margin-top: 2.5rem; text-align: center;
    font-size: 0.85rem; color: var(--text); font-style: italic;
  }

  .pricing-note {
    margin-top: 2.5rem; text-align: center;
    font-size: 0.88rem; color: var(--text); font-style: italic;
  }

  @media (max-width: 860px) {
    .pricing-calculator { grid-template-columns: 1fr; }
    .pc-result { position: static; }
  }

  /* ── CTA BAND ─────────────────────────────────────────── */
  .cta-band {
    background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);
    padding: 6rem 2rem; text-align: center; position: relative; overflow: hidden;
  }
  .cta-band::before {
    content:''; position: absolute; inset:0;
    background: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.06'/%3E%3C/svg%3E");
    opacity: 0.5;
  }
  .cta-band * { position: relative; z-index: 1; }
  .cta-band .section-heading { color: white; max-width: 640px; margin: 0 auto; }
  .cta-band p { color: rgba(255,255,255,0.85); margin: 1.2rem auto 2.5rem; max-width: 480px; font-size: 1rem; }
  .cta-phone-big {
    font-family: var(--ff-title);
    font-size: clamp(2rem, 6vw, 4rem);
    color: white; letter-spacing: 0.06em;
    text-shadow: 0 2px 16px rgba(0,0,0,0.2);
    display: block; margin-bottom: 0.4rem;
  }
  .cta-phone-sub {
    font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: rgba(255,255,255,0.7); display: block; margin-bottom: 2rem;
  }
  .btn-white {
    display: inline-flex; align-items: center; gap: 0.6rem;
    font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.2em; text-transform: uppercase;
    padding: 1.1rem 2.4rem;
    background: white;
    color: var(--rose);
    border-radius: 2px;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 24px rgba(0,0,0,0.15);
  }
  .btn-white:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(0,0,0,0.2); }

  /* ── FOOTER ───────────────────────────────────────────── */
  footer {
    background: var(--ink);
    padding: 4rem 2rem 2rem;
    color: rgba(255,255,255,0.5);
    font-family: var(--ff-sans); font-size: 0.75rem;
  }
  .footer-inner {
    max-width: 1100px; margin: 0 auto;
    display: grid; grid-template-columns: 2fr 1fr 1fr;
    gap: 3rem; padding-bottom: 3rem;
    border-bottom: 1px solid rgba(201,169,110,0.15);
  }
  .footer-brand-name {
    font-family: var(--ff-title); font-size: 1.1rem; color: white;
    letter-spacing: 0.1em; margin-bottom: 0.8rem;
  }
  .footer-brand-tag { line-height: 1.7; max-width: 280px; }
  .footer-col-title {
    font-family: var(--ff-title); font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 1rem;
  }
  .footer-links { list-style: none; line-height: 2.2; }
  .footer-links a { color: rgba(255,255,255,0.5); transition: color 0.25s; }
  .footer-links a:hover { color: var(--gold); }
  .footer-bottom {
    max-width: 1100px; margin: 2rem auto 0;
    display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;
    font-size: 0.65rem; letter-spacing: 0.1em;
  }
  .footer-disclaimer { max-width: 600px; line-height: 1.6; opacity: 0.5; }

  /* ── ANIMATIONS ───────────────────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes shimmer {
    0%   { opacity: 0.3; }
    50%  { opacity: 1; }
    100% { opacity: 0.3; }
  }
  .sparkle { animation: shimmer 2s infinite; }
  .sparkle:nth-child(2) { animation-delay: 0.4s; }
  .sparkle:nth-child(3) { animation-delay: 0.8s; }
  .sparkle:nth-child(4) { animation-delay: 1.2s; }
  .sparkle:nth-child(5) { animation-delay: 1.6s; }

  /* scroll reveal */
  .reveal {
    opacity: 0; transform: translateY(28px);
    transition: opacity 0.7s var(--ease-silk), transform 0.7s var(--ease-silk);
  }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }

  /* ── MOBILE ───────────────────────────────────────────── */
  @media (max-width: 900px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { display: none; }
    .pillars { grid-template-columns: 1fr; gap: 2px; }
    .how-grid { grid-template-columns: 1fr; }
    .how-visual { display: none; }
    .characters-grid { grid-template-columns: repeat(2,1fr); }
    .testi-grid { grid-template-columns: 1fr; }
    .pricing-calculator { grid-template-columns: 1fr; }
    .footer-inner { grid-template-columns: 1fr; gap: 2rem; }
    .hero-photo-strip { display: none; }
  }
</style>
</head>
<body>

<!-- ══ NAVIGATION ══════════════════════════════════════════ -->
<nav id="nav">
  <a href="#" class="nav-logo">
    <span class="crown">✦</span>
    Sophia's Magical Princess Party
  </a>
  <ul class="nav-links" aria-label="Site navigation">
    <li><a href="#characters">Characters</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="#book" class="nav-cta">Book Now</a>
</nav>

<!-- ══ HERO ════════════════════════════════════════════════ -->
<section class="hero" id="top">
  <div class="hero-bg"></div>
  <div class="hero-arc hero-arc-1"></div>
  <div class="hero-arc hero-arc-2"></div>
  <div class="hero-arc hero-arc-3"></div>

  <!-- sparkle SVG layer -->
  <div class="sparkle-field" aria-hidden="true">
    <svg viewBox="0 0 1200 700" preserveAspectRatio="xMidYMid slice">
      <!-- 4-point star shape repeated -->
      <path class="sparkle" d="M200 120 L203 130 L213 133 L203 136 L200 146 L197 136 L187 133 L197 130Z" fill="#C9A96E" opacity="0.6"/>
      <path class="sparkle" d="M900 80  L903 90  L913 93  L903 96  L900 106 L897 96  L887 93  L897 90Z"  fill="#D4768A" opacity="0.5"/>
      <path class="sparkle" d="M1050 300 L1052 308 L1060 310 L1052 312 L1050 320 L1048 312 L1040 310 L1048 308Z" fill="#A88EC0" opacity="0.5"/>
      <path class="sparkle" d="M150 400 L152 408 L160 410 L152 412 L150 420 L148 412 L140 410 L148 408Z" fill="#7EB8D4" opacity="0.45"/>
      <path class="sparkle" d="M600 50  L602 58  L610 60  L602 62  L600 70  L598 62  L590 60  L598 58Z"  fill="#C9A96E" opacity="0.4"/>
      <circle cx="350" cy="600" r="2" fill="#D4768A" opacity="0.4"/>
      <circle cx="850" cy="550" r="2" fill="#C9A96E" opacity="0.35"/>
      <circle cx="100" cy="200" r="1.5" fill="#A88EC0" opacity="0.45"/>
      <circle cx="1100" cy="180" r="1.5" fill="#7EB8D4" opacity="0.4"/>
    </svg>
  </div>

  <p class="hero-eyebrow">South Houston's Premier Princess Experience</p>
  <h1 class="hero-title">Where Every Child Meets Their <em>Favorite Princess</em></h1>
  <p class="hero-subtitle">Professional actors in breathtaking, park-quality gowns bring the magic of beloved heroines directly to your child's celebration.</p>

  <div class="hero-ctas">
    <a href="#book" class="btn-primary">✦ &nbsp;Book a Princess</a>
    <a href="#characters" class="btn-ghost">Meet the Characters</a>
  </div>

  <p class="hero-phone">
    <small>Call to Schedule</small>
    (xxx) xxx-xxxx
  </p>

  <!-- photo strip: placeholder shapes representing real photos -->
  <div class="hero-photo-strip" aria-hidden="true">
    <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">👑</div>
    </figure>
    <figure style="background:linear-gradient(160deg,#F7C5D0,#D4768A)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">🌹</div>
    </figure>
    <figure style="background:linear-gradient(160deg,#D0B8E8,#A88EC0)">
      <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;">✨</div>
    </figure>
  </div>

  <p class="since-badge"><span></span> Making Magic Real Since 2017 <span></span></p>
</section>

<!-- ══ PILLARS ══════════════════════════════════════════════ -->
<section class="section" id="about">
  <div class="section-inner">
    <div class="gold-rule reveal">What Makes Us Different</div>
    <div class="pillars">
      <div class="pillar reveal reveal-delay-1">
        <div class="pillar-icon">👗</div>
        <div class="pillar-title">Top-Quality Costumes</div>
        <p class="pillar-text">Every gown is crafted with the same eye-catching detail you'd expect at a world-class theme park — your guests will be speechless.</p>
      </div>
      <div class="pillar reveal reveal-delay-2">
        <div class="pillar-icon">🎭</div>
        <div class="pillar-title">World Class Performers</div>
        <p class="pillar-text">Our performers fully embody their characters. From their first hello to the royal farewell, you can expect a magical time.</p>
      </div>
      <div class="pillar reveal reveal-delay-3">
        <div class="pillar-icon">🎀</div>
        <div class="pillar-title">Unique Activities</div>
        <p class="pillar-text">Storytime, singalongs, royal decrees, and more! Each visit makes the birthday child feel like the hero of their own story.</p>
      </div>
    </div>
  </div>
</section>

<hr class="section-divider" />

<!-- ══ CHARACTERS ══════════════════════════════════════════ -->
<section class="section" id="characters">
  <div class="section-inner">
    <span class="section-label reveal">The Royal Court</span>
    <h2 class="section-heading reveal">Choose Your Princess</h2>
    <p class="section-body reveal">Ice queens, pixies, ocean adventurers and beyond! Our beloved heroines are ready to make your child's birthday unforgettable.</p>

    <div class="characters-grid">
      <div class="char-card reveal reveal-delay-1">
        <div class="char-color"></div>
        <div class="char-emoji">❄️</div>
        <div class="char-info">
          <span class="char-name">The Snow Queen</span>
          <span class="char-desc">Ice & Magic</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-2">
        <div class="char-color"></div>
        <div class="char-emoji">🌹</div>
        <div class="char-info">
          <span class="char-name">The Rose Princess</span>
          <span class="char-desc">Enchanted Tales</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-3">
        <div class="char-color"></div>
        <div class="char-emoji">🔮</div>
        <div class="char-info">
          <span class="char-name">The Lantern Princess</span>
          <span class="char-desc">Sun &amp; Adventure</span>
        </div>
      </div>
      <div class="char-card reveal reveal-delay-3">
        <div class="char-color"></div>
        <div class="char-emoji">🌊</div>
        <div class="char-info">
          <span class="char-name">The Ocean Heroine</span>
          <span class="char-desc">Sea &amp; Song</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══ HOW IT WORKS ═════════════════════════════════════════ -->
<section class="section how" id="how">
  <div class="section-inner">
    <div class="how-grid">
      <div>
        <span class="section-label reveal">Simple &amp; Magical</span>
        <h2 class="section-heading reveal">How to Book Your Royal Visit</h2>
        <ol class="how-steps" aria-label="Booking steps">
          <li class="how-step reveal">
            <span class="step-num" aria-hidden="true">01</span>
            <div>
              <div class="step-title">Fill out the Booking Form</div>
              <p class="step-text">Reach out with the form below to contact our team.</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-1">
            <span class="step-num" aria-hidden="true">02</span>
            <div>
              <div class="step-title">Pick Your Date & Package</div>
              <p class="step-text">We'll get back with you to finalize your selection and answer any questions. You're on the schedule at this point!</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-2">
            <span class="step-num" aria-hidden="true">03</span>
            <div>
              <div class="step-title">Await the Arrival</div>
              <p class="step-text">On the day, your princess will arrive in full costume. Watch your child's eyes light up as the magic becomes real.</p>
            </div>
          </li>
          <li class="how-step reveal reveal-delay-3">
            <span class="step-num" aria-hidden="true">04</span>
            <div>
              <div class="step-title">Memories Made</div>
              <p class="step-text">Photo moments, activities, and royal moments, your child will be talking about this birthday for years to come.</p>
            </div>
          </li>
        </ol>

        <div class="call-highlight reveal">
          <p>Still have questions? Feel free to call or text the number below. We'll get back to you as soon as possible to assist/</p>
          <div class="call-number">(xxx) xxx-xxxx</div>
        </div>
      </div>

      <div class="how-visual" aria-hidden="true">
        <div class="how-photo">
          <div class="how-photo-placeholder">
            <span>👸</span>
            Princess Visit
          </div>
        </div>
        <div class="how-photo">
          <div class="how-photo-placeholder">
            <span>🎂</span>
            Birthday Joy
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══ TESTIMONIALS ═════════════════════════════════════════ -->
<section class="section testimonials" id="testimonials">
  <div class="section-inner">
    <span class="section-label reveal">From Our Families</span>
    <h2 class="section-heading reveal" style="color:white;">What Parents Are Saying</h2>

    <div class="testi-grid">
      <div class="testi-card reveal reveal-delay-1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">They really know how to make the birthday kiddo feel special!</p>
        <p class="testi-author">Inshirah Barakat — Google</p>
      </div>
      <div class="testi-card reveal reveal-delay-2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Great third experience using Sophia's! Love how in character they always are and very interactive. Highly recommend!</p>
        <p class="testi-author">Jessica Lyne — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-3">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Rapunzel was kind, genuine, and my kiddo was absolutely delighted by the visit!</p>
        <p class="testi-author">Becca Popland — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-1">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Our little princess received the best personal video message from The Snow Queen! She absolutely loved it!</p>
        <p class="testi-author">Jimee Jensen-Caudle — Facebook</p>
      </div>
      <div class="testi-card reveal reveal-delay-2">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">Hands down the best present I could have ever bought my granddaughter for her birthday!</p>
        <p class="testi-author">James Scurlock — Google</p>
      </div>
      <div class="testi-card reveal reveal-delay-3" style="display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;border-style:dashed;gap:0.5rem;">
        <div style="font-size:2rem;">⭐</div>
        <p style="color:rgba(255,255,255,0.5);font-size:0.8rem;font-family:var(--ff-sans);">Proudly serving South Houston families since 2017</p>
        <a href="#book" class="btn-white" style="margin-top:0.5rem;font-size:0.65rem;padding:0.8rem 1.6rem;">Leave a Review</a>
      </div>
    </div>
  </div>
</section>

<!-- ══ PRICING ══════════════════════════════════════════════ -->
<section class="section" id="pricing">
  <div class="section-inner">
    <span class="section-label reveal">Transparent &amp; Simple</span>
    <h2 class="section-heading reveal">Build Your Royal Package</h2>
    <p class="section-body reveal">Customize your perfect party by selecting your character type, duration, and number of performers — and see your price instantly.</p>

    <div class="pricing-calculator">

      <!-- LEFT: Selectors -->
      <div class="pc-selectors reveal">

        <!-- Character Type -->
        <div class="pc-group">
          <span class="pc-group-label">✦ &nbsp;Type of Character</span>
          <div class="pc-options">
            <button class="pc-btn pc-char-btn active" data-group="type" data-val="princess" onclick="pcSelect(this)">
              <span class="pc-char-icon">👑</span>
              <span>Princess</span>
            </button>
            <button class="pc-btn pc-char-btn" data-group="type" data-val="kpop" onclick="pcSelect(this)">
              <span class="pc-char-icon">🎤</span>
              <span>K-Pop Star</span>
            </button>
            <button class="pc-btn pc-char-btn" data-group="type" data-val="impersonator" onclick="pcSelect(this)">
              <span class="pc-char-icon">🌟</span>
              <span>Impersonator</span>
            </button>
          </div>
        </div>

        <!-- Duration -->
        <div class="pc-group">
          <span class="pc-group-label">✦ &nbsp;Duration</span>
          <div class="pc-options">
            <button class="pc-btn active" data-group="duration" data-val="30" onclick="pcSelect(this)"><span>30 Min</span></button>
            <button class="pc-btn" data-group="duration" data-val="60" onclick="pcSelect(this)"><span>1 Hour</span></button>
            <button class="pc-btn" data-group="duration" data-val="120" onclick="pcSelect(this)"><span>2 Hours</span></button>
          </div>
        </div>

        <!-- Number of Performers -->
        <div class="pc-group" id="pc-performer-group">
          <span class="pc-group-label">✦ &nbsp;Number of Performers</span>
          <div class="pc-stepper">
            <button class="pc-step-btn" onclick="pcStep(-1)">−</button>
            <span class="pc-step-count" id="pc-performer-count">1</span>
            <button class="pc-step-btn" onclick="pcStep(1)">+</button>
            <span class="pc-step-label">performer<span id="pc-plural"></span></span>
          </div>
        </div>

        <!-- What's included note -->
        <div style="margin-top:1rem; padding:1.5rem 1.8rem; background:white; border:1px solid rgba(201,169,110,0.2); border-radius:4px;">
          <div style="font-family:var(--ff-sans);font-size:0.6rem;letter-spacing:0.3em;text-transform:uppercase;color:var(--gold);margin-bottom:0.8rem;">✦ &nbsp;Good to Know</div>
          <ul style="list-style:none;font-size:0.88rem;color:var(--text);line-height:1.9;">
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;30-min visits omit the sing-along</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;Makeovers require 2 hrs for 6+ children</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;Travel fee may apply based on location</li>
            <li style="display:flex;gap:0.6rem;">✦ &nbsp;All performers are fully costumed &amp; in-character</li>
          </ul>
        </div>
      </div>

      <!-- RIGHT: Result Card -->
      <div class="pc-result reveal reveal-delay-2">
        <div class="pc-result-label">Your Estimate</div>
        <div class="pc-result-package" id="pc-package-name">The Royal Greeting</div>
        <div class="pc-result-desc" id="pc-package-desc">Princess · 30 Minutes · 1 Performer</div>

        <div class="pc-price-row">
          <span class="pc-price-item">Base rate</span>
          <span class="pc-price-val" id="pc-base-val">$150</span>
        </div>
        <div class="pc-price-row">
          <span class="pc-price-item">Additional performer(s)</span>
          <span class="pc-price-val" id="pc-add-performer-val">—</span>
        </div>
        <div class="pc-price-row">
          <span class="pc-price-item">Character premium</span>
          <span class="pc-price-val" id="pc-char-premium-val">Included</span>
        </div>

        <div class="pc-total-row">
          <span class="pc-total-label">Total Estimate</span>
          <span class="pc-total-price" id="pc-total">$150</span>
        </div>

        <ul class="pc-features" id="pc-features-list">
          <li>In-character princess actress</li>
          <li>Meet &amp; greet with birthday child</li>
          <li>Photo opportunities</li>
          <li>Royal birthday blessing</li>
        </ul>

        <a href="#book" class="pc-book-btn">Reserve This Package &rarr;</a>

        <p style="font-family:var(--ff-sans);font-size:0.65rem;color:rgba(255,255,255,0.35);text-align:center;margin-top:1rem;line-height:1.6;">
          Estimates are approximate. Final pricing confirmed during booking. Travel fees may apply.
        </p>
      </div>

    </div><!-- /.pricing-calculator -->

    <p class="pricing-note reveal">All packages include a fully costumed performer in character throughout your event. We proudly serve the South Houston area.</p>
  </div>
</section>

<script>
(function() {
  // ── PRICING DATA ─────────────────────────────────────────
  const BASE = { 30: 150, 60: 225, 120: 350 };
  const EXTRA_PERFORMER = { 30: 100, 60: 150, 120: 200 };
  const CHAR_PREMIUM = { princess: 0, kpop: 50, impersonator: 75 };
  const CHAR_PREMIUM_LABEL = { princess: 'Included', kpop: '+$50', impersonator: '+$75' };

  // Max performers per type
  const MAX_PERFORMERS = { princess: 4, kpop: 3, impersonator: 1 };

  const PACKAGE_NAMES = {
    princess: { 30: 'The Royal Greeting', 60: 'The Enchanted Party', 120: 'The Magical Kingdom' },
    kpop:     { 30: 'The Pop Showcase',   60: 'The Idol Experience', 120: 'The K-Pop Extravaganza' },
    impersonator: { 30: 'The Star Appearance', 60: 'The Celebrity Bash', 120: 'The Superstar Soirée' }
  };

  const FEATURES = {
    princess: {
      30:  ['In-character princess actress','Meet & greet with birthday child','Photo opportunities','Royal birthday blessing'],
      60:  ['Full character immersion','Storytime & singalong','Royal coronation ceremony','Photo opportunities','Personalized attention for birthday child'],
      120: ['Extended character experience','Full activity suite','Royal games & crafts','Coronation ceremony','Makeover activity (6+ children require 2 hrs)','Group singalong & dancing']
    },
    kpop: {
      30:  ['K-Pop idol in full costume','High-energy mini performance','Fan photo experience','Group song moment'],
      60:  ['Full K-Pop performance set','Dance-along with guests','Costume photo ops','Fan interaction time','Birthday song performance'],
      120: ['Extended idol experience','Multiple performance segments','Dance tutorial for guests','Group fan photo session','Personalized fan card signing','Birthday surprise moment']
    },
    impersonator: {
      30:  ['Celebrity look-alike in full costume','Meet & greet photo moment','In-character performance','Birthday recognition'],
      60:  ['Full celebrity character experience','Live performance/singing (if applicable)','Photo opportunities','Interactive fan moment','Personalized birthday greeting'],
      120: ['Extended celebrity appearance','Multiple performance moments','Guest interaction time','Costume photo experience','Games themed to the celebrity','Autographed keepsake']
    }
  };

  // State
  let state = { type: 'princess', duration: 30, performers: 1 };

  window.pcSelect = function(btn) {
    const group = btn.dataset.group;
    const val = btn.dataset.val;
    btn.closest('.pc-options').querySelectorAll('.pc-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    state[group] = group === 'duration' ? parseInt(val) : val;

    if (group === 'type') {
      const max = MAX_PERFORMERS[state.type];
      const performerGroup = document.getElementById('pc-performer-group');

      if (state.type === 'impersonator') {
        // Lock to 1 and hide the stepper
        state.performers = 1;
        performerGroup.style.display = 'none';
      } else {
        performerGroup.style.display = '';
        // Clamp performers to new max
        if (state.performers > max) state.performers = max;
      }
      document.getElementById('pc-performer-count').textContent = state.performers;
      document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : '';
    }

    updateCalc();
  };

  window.pcStep = function(dir) {
    const max = MAX_PERFORMERS[state.type];
    state.performers = Math.min(max, Math.max(1, state.performers + dir));
    document.getElementById('pc-performer-count').textContent = state.performers;
    document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : '';
    updateCalc();
  };

  function updateCalc() {
    const { type, duration, performers } = state;

    const base     = BASE[duration];
    const addPerf  = performers > 1 ? EXTRA_PERFORMER[duration] * (performers - 1) : 0;
    const charPrem = CHAR_PREMIUM[type];
    const total    = base + addPerf + charPrem;

    const totalEl = document.getElementById('pc-total');
    totalEl.classList.add('updating');
    setTimeout(() => {
      totalEl.textContent = '$' + total.toLocaleString();
      totalEl.classList.remove('updating');
    }, 180);

    const durLabel = duration === 30 ? '30 Minutes' : duration === 60 ? '1 Hour' : '2 Hours';
    const typeLabel = type === 'princess' ? 'Princess' : type === 'kpop' ? 'K-Pop Star' : 'Impersonator';

    document.getElementById('pc-package-name').textContent = PACKAGE_NAMES[type][duration];
    document.getElementById('pc-package-desc').textContent =
      typeLabel + ' · ' + durLabel + ' · ' + performers + ' Performer' + (performers > 1 ? 's' : '');

    document.getElementById('pc-base-val').textContent = '$' + base;
    document.getElementById('pc-add-performer-val').textContent = addPerf > 0 ? '$' + addPerf : '—';
    document.getElementById('pc-char-premium-val').textContent = CHAR_PREMIUM_LABEL[type];

    const ul = document.getElementById('pc-features-list');
    ul.innerHTML = FEATURES[type][duration].map(f => `<li>${f}</li>`).join('');
  }
})();
</script>

<!-- ══ FAQ ══════════════════════════════════════════════════ -->
<section class="section" id="faq" style="background:#F9F4F7;">
  <div class="section-inner">
    <span class="section-label reveal">Questions &amp; Answers</span>
    <h2 class="section-heading reveal">Frequently Asked</h2>

    <div style="margin-top:3rem;max-width:720px;" class="reveal">
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          What area do you serve? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We proudly serve the South Houston area and surrounding communities. Call us to confirm your specific location when booking.</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          How far in advance should I book? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We recommend booking 2–4 weeks in advance, especially for weekend dates which fill up quickly. Give us a call to check availability!</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Do you offer video messages? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Yes! Personalized video messages from your chosen princess are available as an add-on. Perfect for birthdays, holidays, or just a magical surprise.</p>
      </details>
      <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Are your performers background-checked? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Absolutely. The safety and comfort of your children is our top priority. All performers are vetted, professional, and experienced in working with children.</p>
      </details>
      <details style="padding:1.4rem 0;cursor:pointer;">
        <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;">
          Which characters are available? <span style="color:var(--gold);">+</span>
        </summary>
        <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We have a rotating roster of beloved heroine-inspired characters. Call us to find out which princesses are currently available for your date!</p>
      </details>
    </div>
  </div>
</section>

<!-- ══ CTA BAND ═════════════════════════════════════════════ -->
<section class="cta-band" id="book">
  <span class="section-label" style="color:rgba(255,255,255,0.7)">Ready to Create Magic?</span>
  <h2 class="section-heading" style="max-width:640px;margin:0.8rem auto 0;">Book Your Princess Today</h2>
  <p>The most magical birthday party your child has ever had is just one phone call away. We'd love to hear about your celebration!</p>
  <a class="cta-phone-big" href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a>
  <span class="cta-phone-sub">Monday – Saturday, 9am – 7pm</span>
  <a href="tel:xxxxxxxxxx" class="btn-white">✦ &nbsp;Call to Book Now</a>
</section>

<!-- ══ FOOTER ═══════════════════════════════════════════════ -->
<footer>
  <div class="footer-inner">
    <div>
      <div class="footer-brand-name">✦ Sophia's Magical Princess Party</div>
      <p class="footer-brand-tag">Bringing beloved heroine characters to life for children's celebrations across the South Houston area since 2017.</p>
    </div>
    <div>
      <div class="footer-col-title">Navigate</div>
      <ul class="footer-links">
        <li><a href="#characters">Characters</a></li>
        <li><a href="#how">How It Works</a></li>
        <li><a href="#pricing">Pricing</a></li>
        <li><a href="#testimonials">Reviews</a></li>
        <li><a href="#faq">FAQ</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">Contact</div>
      <ul class="footer-links">
        <li><a href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a></li>
        <li>South Houston, TX</li>
        <li>Mon–Sat, 9am–7pm</li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 Sophia's Magical Princess Party. All rights reserved.</span>
    <span class="footer-disclaimer">We offer unique original characters inspired by classic stories and fables. We are a private company unaffiliated with any major production company or theme park. Any similarity to trademarked characters is coincidental.</span>
  </div>
</footer>

<script>
  // ── NAV scroll effect
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  }, { passive: true });

  // ── Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
  }, { threshold: 0.12 });
  reveals.forEach(el => io.observe(el));

  // ── FAQ caret toggle
  document.querySelectorAll('details').forEach(d => {
    d.addEventListener('toggle', () => {
      const icon = d.querySelector('summary span');
      if (icon) icon.textContent = d.open ? '−' : '+';
    });
  });
</script>
</body>
</html>
'''