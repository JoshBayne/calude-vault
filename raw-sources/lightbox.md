Use the attached html file as a design template in regards to look and feel of the CSS. Create a new page that will be used as a method of presenting all characters that the company offers. The company offers a total of 23 characters, with potential for more.

Some characters have alternate outfits, add code that when users click or tap on an image, a lightbox opens that allows different photos to be viewed simultaneously with labels. Add code to have variant outfits labeled, with CSS added and notated that allows certain outfits to be highlighted to drive sales.

Images will be hosted on the imgbb.com platform, so code should be optimized to use that as a CDN.

Reminder, this company is a children's entertainment company, but we are marketing to the parents.

It looks like the file didn’t come through — the uploads folder is empty. Could you re-attach the HTML template file? Once I can read the CSS and design style from it, I’ll build the characters page to match that look and feel precisely.

'''html
<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1.0" /> <title>Sophia's Magical Princess Party — South Houston</title> <link rel="preconnect" href="https://fonts.googleapis.com" /> <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin /> <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Cinzel:wght@400;500;600&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" /> <style> /* ── TOKENS ───────────────────────────────────────────── */ :root { --gold: #C9A96E; --gold-lt: #E8D5A3; --rose: #D4768A; --rose-lt: #F2C4CF; --lavender: #A88EC0; --sky: #7EB8D4; --cream: #FAF6F0; --ink: #1A1118; --ink-soft: #3D2B3A; --text: #4A3A46; --ff-title: 'Cinzel', serif; --ff-serif: 'Cormorant Garamond', serif; --ff-sans: 'Jost', sans-serif; --ease-silk: cubic-bezier(0.25, 0.46, 0.45, 0.94); } /* ── RESET ────────────────────────────────────────────── */ *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; } html { scroll-behavior: smooth; } body { background: var(--cream); color: var(--text); font-family: var(--ff-serif); font-size: 18px; line-height: 1.7; overflow-x: hidden; } img { display: block; max-width: 100%; } a { color: inherit; text-decoration: none; } /* ── STAR / SPARKLE SVG DEFS ──────────────────────────── */ .sparkle-field { position: absolute; inset: 0; pointer-events: none; overflow: hidden; } .sparkle-field svg { width: 100%; height: 100%; } /* ── UTILITY ──────────────────────────────────────────── */ .visually-hidden { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0,0,0,0); } .gold-rule { display: flex; align-items: center; gap: 1rem; color: var(--gold); font-family: var(--ff-title); letter-spacing: 0.25em; font-size: 0.6rem; text-transform: uppercase; } .gold-rule::before, .gold-rule::after { content:''; flex:1; height:1px; background: linear-gradient(90deg, transparent, var(--gold-lt), transparent); } /* ── NAVIGATION ───────────────────────────────────────── */ nav { position: fixed; top: 0; left: 0; right: 0; z-index: 100; display: flex; align-items: center; justify-content: space-between; padding: 1.2rem 4rem; background: transparent; transition: background 0.4s var(--ease-silk), box-shadow 0.4s; } nav.scrolled { background: rgba(250,246,240,0.96); box-shadow: 0 1px 24px rgba(26,17,24,0.08); backdrop-filter: blur(8px); } .nav-logo { font-family: var(--ff-title); font-size: 1rem; letter-spacing: 0.15em; color: var(--ink); display: flex; align-items: center; gap: 0.6rem; } .nav-logo .crown { font-size: 1.2rem; } .nav-links { display: flex; gap: 2.4rem; list-style: none; font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400; letter-spacing: 0.18em; text-transform: uppercase; } .nav-links a { color: var(--ink-soft); position: relative; transition: color 0.25s; } .nav-links a::after { content:''; position: absolute; left:0; bottom:-3px; width:0; height:1px; background: var(--gold); transition: width 0.3s var(--ease-silk); } .nav-links a:hover { color: var(--gold); } .nav-links a:hover::after { width: 100%; } .nav-cta { font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500; letter-spacing: 0.18em; text-transform: uppercase; padding: 0.65rem 1.6rem; border: 1px solid var(--gold); color: var(--gold); transition: background 0.3s, color 0.3s; border-radius: 2px; } .nav-cta:hover { background: var(--gold); color: var(--cream); } /* ── HERO ─────────────────────────────────────────────── */ .hero { position: relative; min-height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 8rem 2rem 6rem; overflow: hidden; } /* layered gradient background */ .hero-bg { position: absolute; inset: 0; background: radial-gradient(ellipse 80% 60% at 50% 0%, rgba(212,118,138,0.18) 0%, transparent 70%), radial-gradient(ellipse 60% 70% at 15% 60%, rgba(168,142,192,0.14) 0%, transparent 65%), radial-gradient(ellipse 55% 50% at 85% 55%, rgba(126,184,212,0.12) 0%, transparent 60%), linear-gradient(175deg, #FDF9F4 0%, #F7EEF5 50%, #EFF3F9 100%); } /* grain overlay */ .hero-bg::after { content: ''; position: absolute; inset: 0; background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E"); opacity: 0.6; } /* decorative arcs */ .hero-arc { position: absolute; border-radius: 50%; border: 1px solid rgba(201,169,110,0.25); pointer-events: none; } .hero-arc-1 { width: 500px; height: 500px; top: 50%; left: 50%; transform: translate(-50%,-50%); } .hero-arc-2 { width: 720px; height: 720px; top: 50%; left: 50%; transform: translate(-50%,-50%); } .hero-arc-3 { width: 960px; height: 960px; top: 50%; left: 50%; transform: translate(-50%,-50%); opacity: 0.5; } .hero-eyebrow { font-family: var(--ff-sans); font-size: 0.65rem; font-weight: 400; letter-spacing: 0.35em; text-transform: uppercase; color: var(--gold); margin-bottom: 1.6rem; opacity: 0; animation: fadeUp 0.8s 0.2s var(--ease-silk) forwards; } .hero-title { font-family: var(--ff-title); font-size: clamp(2rem, 6vw, 5rem); font-weight: 500; line-height: 1.12; color: var(--ink); letter-spacing: 0.02em; max-width: 820px; opacity: 0; animation: fadeUp 0.9s 0.35s var(--ease-silk) forwards; } .hero-title em { font-style: italic; background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 50%, var(--sky) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; } .hero-subtitle { margin-top: 1.6rem; font-family: var(--ff-serif); font-size: 1.2rem; font-weight: 300; color: var(--text); max-width: 520px; line-height: 1.7; opacity: 0; animation: fadeUp 0.9s 0.5s var(--ease-silk) forwards; } .hero-ctas { display: flex; gap: 1.2rem; margin-top: 2.8rem; flex-wrap: wrap; justify-content: center; opacity: 0; animation: fadeUp 0.9s 0.65s var(--ease-silk) forwards; } .btn-primary { display: inline-flex; align-items: center; gap: 0.6rem; font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500; letter-spacing: 0.2em; text-transform: uppercase; padding: 1.1rem 2.4rem; background: var(--gold); color: var(--cream); border-radius: 2px; transition: background 0.3s, transform 0.2s; box-shadow: 0 4px 24px rgba(201,169,110,0.35); } .btn-primary:hover { background: #b8935a; transform: translateY(-2px); } .btn-ghost { display: inline-flex; align-items: center; gap: 0.6rem; font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400; letter-spacing: 0.2em; text-transform: uppercase; padding: 1.1rem 2.4rem; border: 1px solid rgba(201,169,110,0.5); color: var(--ink-soft); border-radius: 2px; transition: border-color 0.3s, color 0.3s, transform 0.2s; } .btn-ghost:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); } .hero-phone { margin-top: 2rem; font-family: var(--ff-title); font-size: 1.4rem; letter-spacing: 0.08em; color: var(--rose); opacity: 0; animation: fadeUp 0.9s 0.8s var(--ease-silk) forwards; } .hero-phone small { display: block; font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.25em; text-transform: uppercase; color: var(--text); margin-bottom: 0.3rem; } .hero-photo-strip { display: flex; gap: 1rem; margin-top: 3.5rem; justify-content: center; opacity: 0; animation: fadeUp 1s 0.9s var(--ease-silk) forwards; } .hero-photo-strip figure { width: 180px; height: 230px; overflow: hidden; border-radius: 80px; border: 2px solid rgba(201,169,110,0.4); flex-shrink: 0; box-shadow: 0 8px 32px rgba(26,17,24,0.12); transition: transform 0.4s var(--ease-silk); } .hero-photo-strip figure:nth-child(2) { margin-top: -20px; border-color: rgba(212,118,138,0.5); } .hero-photo-strip figure:nth-child(3) { margin-top: 10px; border-color: rgba(168,142,192,0.5); } .hero-photo-strip figure:hover { transform: scale(1.05) translateY(-6px); } .hero-photo-strip img { width: 100%; height: 100%; object-fit: cover; } .pillar-photo-strip figure { width: 160px; height: 120px; overflow: hidden; border-radius: 60px; border: 2px solid rgba(201,169,110,0.4); flex-shrink: 0; box-shadow: 0 8px 32px rgba(26,17,24,0.12); transition: transform 0.4s var(--ease-silk); margin-top: 10px; } .pillar-photo-strip figure:hover { transform: scale(1.05) translateY(-6px); } .pillar-photo-strip img { width: 100%; height: 100%; } /* ── SINCE BADGE ──────────────────────────────────────── */ .since-badge { position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%); font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase; color: var(--gold); opacity: 0.7; display: flex; align-items: center; gap: 0.5rem; } .since-badge span { display: inline-block; width: 24px; height: 1px; background: var(--gold-lt); } /* ── DIVIDER ──────────────────────────────────────────── */ .section-divider { width: 100%; max-width: 1100px; margin: 0 auto; border: none; border-top: 1px solid rgba(201,169,110,0.2); } /* ── SECTION WRAPPER ──────────────────────────────────── */ .section { padding: 7rem 2rem; } .section-inner { max-width: 1100px; margin: 0 auto; } .section-label { font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.35em; text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; display: block; } .section-heading { font-family: var(--ff-title); font-size: clamp(1.8rem, 4vw, 3rem); font-weight: 500; line-height: 1.18; color: var(--ink); letter-spacing: 0.02em; max-width: 560px; } .section-body { font-size: 1.05rem; line-height: 1.8; color: var(--text); max-width: 520px; margin-top: 1.2rem; } /* ── PILLARS (3-col) ──────────────────────────────────── */ .pillars { display: grid; grid-template-columns: repeat(3,1fr); gap: 2px; margin-top: 5rem; } .pillar { padding: 3rem 2.4rem; background: white; position: relative; overflow: hidden; transition: transform 0.35s var(--ease-silk), box-shadow 0.35s; } .pillar::before { content:''; position: absolute; top:0; left:0; right:0; height:3px; background: linear-gradient(90deg, var(--rose), var(--lavender)); transform: scaleX(0); transform-origin: left; transition: transform 0.4s var(--ease-silk); } .pillar:hover::before { transform: scaleX(1); } .pillar:hover { transform: translateY(-6px); box-shadow: 0 16px 48px rgba(26,17,24,0.10); } .pillar-icon { font-size: 2rem; margin-bottom: 1.2rem; } .pillar-title { font-family: var(--ff-title); font-size: 1.05rem; letter-spacing: 0.05em; color: var(--ink); margin-bottom: 0.6rem; } .pillar-text { font-size: 0.95rem; color: var(--text); line-height: 1.75; } /* ── HOW IT WORKS ─────────────────────────────────────── */ .how { background: linear-gradient(160deg, #F7EFF8 0%, #EEF4FA 100%); position: relative; overflow: hidden; } .how::before { content:''; position: absolute; top:-200px; right:-200px; width: 600px; height: 600px; border-radius: 50%; background: radial-gradient(circle, rgba(212,118,138,0.12), transparent 70%); } .how-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; } .how-steps { list-style: none; margin-top: 2.5rem; } .how-step { display: flex; gap: 2rem; align-items: flex-start; padding: 1.8rem 0; border-bottom: 1px solid rgba(201,169,110,0.2); } .how-step:last-child { border-bottom: none; } .step-num { font-family: var(--ff-title); font-size: 2.5rem; font-weight: 500; line-height: 1; color: rgba(201,169,110,0.35); flex-shrink: 0; min-width: 2.5rem; text-align: center; } .step-title { font-family: var(--ff-title); font-size: 1rem; color: var(--ink); margin-bottom: 0.3rem; letter-spacing: 0.04em; } .step-text { font-size: 0.9rem; color: var(--text); line-height: 1.7; } .how-visual { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; } .how-photo { border-radius: 4px; overflow: hidden; box-shadow: 0 8px 32px rgba(26,17,24,0.1); aspect-ratio: 3/4; background: #e8e0ec; position: relative; } .how-photo:nth-child(2) { margin-top: 2rem; } .how-photo img { width: 100%; height: 100%; object-fit: cover; } .how-photo-placeholder { position: absolute; inset: 0; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 0.5rem; color: rgba(60,40,60,0.3); font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase; } .how-photo-placeholder span { font-size: 2.5rem; } .call-highlight { margin-top: 3rem; padding: 2rem 2.5rem; background: white; border-left: 3px solid var(--gold); border-radius: 2px; box-shadow: 0 4px 20px rgba(26,17,24,0.06); } .call-highlight p { font-size: 0.9rem; color: var(--text); line-height: 1.7; margin-bottom: 0.8rem; } .call-number { font-family: var(--ff-title); font-size: 1.5rem; color: var(--rose); letter-spacing: 0.08em; } /* ── CHARACTERS ───────────────────────────────────────── */ .characters-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.5rem; margin-top: 3.5rem; } .char-card { position: relative; overflow: hidden; border-radius: 4px; aspect-ratio: 3/4; background: #f0e8f0; cursor: pointer; box-shadow: 0 4px 16px rgba(26,17,24,0.08); transition: transform 0.4s var(--ease-silk), box-shadow 0.4s; display: flex; } .char-card:hover { transform: translateY(-8px) scale(1.02); box-shadow: 0 20px 56px rgba(26,17,24,0.15); } .char-card::before { content:''; position: absolute; inset: 0; z-index: 1; background: linear-gradient(0deg, rgba(26,17,24,0.7) 0%, rgba(26,17,24,0.1) 60%, transparent 100%); } .char-card img { height: 100%; } .char-color { position: absolute; inset:0; } .char-card:nth-child(1) .char-color { background: linear-gradient(160deg, #B5D4E8 0%, #7EB8D4 100%); } .char-card:nth-child(2) .char-color { background: linear-gradient(160deg, #F7C5D0 0%, #D4768A 100%); } .char-card:nth-child(3) .char-color { background: linear-gradient(160deg, #D0B8E8 0%, #A88EC0 100%); } .char-card:nth-child(4) .char-color { background: linear-gradient(160deg, #E8E0A0 0%, #C9A96E 100%); } .char-emoji { position: absolute; top: 50%; left: 50%; transform: translate(-50%,-60%); font-size: 4rem; z-index: 0; opacity: 0.4; } .char-info { position: absolute; bottom: 0; left: 0; right: 0; padding: 1.5rem; z-index: 2; } .char-name { font-family: var(--ff-title); font-size: 0.95rem; letter-spacing: 0.08em; color: white; display: block; margin-bottom: 0.2rem; } .char-desc { font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: rgba(255,255,255,0.7); } /* ── TESTIMONIALS ─────────────────────────────────────── */ .testimonials { background: var(--ink); } .testimonials .section-label { color: var(--gold-lt); } .testimonials .section-heading { color: white; } .testi-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; margin-top: 3.5rem; } .testi-card { padding: 2.2rem; border: 1px solid rgba(201,169,110,0.2); border-radius: 2px; position: relative; transition: border-color 0.3s, background 0.3s; } .testi-card:hover { border-color: rgba(201,169,110,0.5); background: rgba(255,255,255,0.03); } .testi-quote { font-family: var(--ff-serif); font-size: 1.05rem; font-style: italic; color: rgba(255,255,255,0.85); line-height: 1.7; margin-bottom: 1.4rem; } .testi-quote::before { content: '\201C'; font-size: 2rem; color: var(--gold); line-height: 0; vertical-align: -0.5rem; margin-right: 0.2rem; } .testi-author { font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold); } .testi-stars { color: var(--gold); font-size: 0.8rem; margin-bottom: 0.8rem; letter-spacing: 0.1em; } /* ── PRICING CALCULATOR ───────────────────────────────── */ .pricing-calculator { margin-top: 3.5rem; display: grid; grid-template-columns: 1fr 340px; gap: 2.5rem; align-items: start; } /* selector groups */ .pc-group { margin-bottom: 2rem; } .pc-group-label { font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; display: block; } .pc-options { display: flex; flex-wrap: wrap; gap: 0.6rem; } .pc-btn { font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 400; letter-spacing: 0.12em; text-transform: uppercase; padding: 0.6rem 1.2rem; border: 1px solid rgba(201,169,110,0.35); background: white; color: var(--text); border-radius: 2px; cursor: pointer; transition: all 0.22s var(--ease-silk); position: relative; overflow: hidden; } .pc-btn::before { content:''; position: absolute; inset: 0; background: linear-gradient(135deg, var(--rose), var(--lavender)); opacity: 0; transition: opacity 0.22s; } .pc-btn span { position: relative; z-index: 1; } .pc-btn:hover { border-color: var(--rose); color: var(--rose); } .pc-btn.active { border-color: transparent; color: white; box-shadow: 0 4px 18px rgba(212,118,138,0.35); } .pc-btn.active::before { opacity: 1; } /* character type buttons - wider */ .pc-char-btn { padding: 0.75rem 1.4rem; } .pc-char-icon { font-size: 1.1rem; display: block; margin-bottom: 0.25rem; } /* performer stepper */ .pc-stepper { display: flex; align-items: center; gap: 1.2rem; margin-top: 0.4rem; } .pc-step-btn { width: 36px; height: 36px; border: 1px solid rgba(201,169,110,0.4); background: white; border-radius: 2px; font-size: 1.1rem; cursor: pointer; color: var(--gold); display: flex; align-items: center; justify-content: center; transition: all 0.2s; line-height: 1; font-family: var(--ff-sans); } .pc-step-btn:hover { background: var(--gold); color: white; border-color: var(--gold); } .pc-step-count { font-family: var(--ff-title); font-size: 1.8rem; color: var(--ink); min-width: 2rem; text-align: center; } .pc-step-label { font-family: var(--ff-sans); font-size: 0.72rem; color: var(--text); letter-spacing: 0.08em; } /* results card */ .pc-result { position: sticky; top: 100px; background: var(--ink); border: 1px solid rgba(201,169,110,0.3); border-radius: 4px; padding: 2.4rem 2rem; color: white; } .pc-result-label { font-family: var(--ff-sans); font-size: 0.58rem; letter-spacing: 0.32em; text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; } .pc-result-package { font-family: var(--ff-title); font-size: 1.25rem; letter-spacing: 0.04em; color: white; margin-bottom: 0.25rem; line-height: 1.3; } .pc-result-desc { font-family: var(--ff-sans); font-size: 0.75rem; color: rgba(255,255,255,0.5); margin-bottom: 1.8rem; line-height: 1.6; } .pc-price-row { display: flex; justify-content: space-between; align-items: baseline; padding: 0.7rem 0; border-bottom: 1px solid rgba(255,255,255,0.08); } .pc-price-row:last-of-type { border-bottom: none; } .pc-price-item { font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.08em; color: rgba(255,255,255,0.6); } .pc-price-val { font-family: var(--ff-serif); font-size: 1rem; color: rgba(255,255,255,0.85); } .pc-total-row { margin-top: 1.5rem; padding-top: 1.5rem; border-top: 1px solid rgba(201,169,110,0.3); display: flex; justify-content: space-between; align-items: baseline; } .pc-total-label { font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.3em; text-transform: uppercase; color: var(--gold); } .pc-total-price { font-family: var(--ff-title); font-size: 2.4rem; letter-spacing: 0.02em; background: linear-gradient(135deg, var(--gold-lt), var(--gold)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; transition: all 0.3s var(--ease-silk); } .pc-total-price.updating { transform: scale(0.92); opacity: 0.4; } .pc-features { list-style: none; margin-top: 1.8rem; margin-bottom: 1.8rem; } .pc-features li { display: flex; gap: 0.6rem; align-items: flex-start; font-family: var(--ff-sans); font-size: 0.72rem; letter-spacing: 0.04em; color: rgba(255,255,255,0.65); padding: 0.35rem 0; line-height: 1.5; } .pc-features li::before { content: '✦'; color: var(--gold); font-size: 0.5rem; margin-top: 0.35rem; flex-shrink:0; } .pc-book-btn { display: block; width: 100%; text-align: center; font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 500; letter-spacing: 0.2em; text-transform: uppercase; padding: 1rem 1.5rem; background: linear-gradient(135deg, var(--rose), var(--lavender)); color: white; border-radius: 2px; margin-top: 1.5rem; transition: opacity 0.2s, transform 0.2s; box-shadow: 0 4px 20px rgba(212,118,138,0.3); } .pc-book-btn:hover { opacity: 0.88; transform: translateY(-2px); } .pc-note { margin-top: 2.5rem; text-align: center; font-size: 0.85rem; color: var(--text); font-style: italic; } .pricing-note { margin-top: 2.5rem; text-align: center; font-size: 0.88rem; color: var(--text); font-style: italic; } @media (max-width: 860px) { .pricing-calculator { grid-template-columns: 1fr; } .pc-result { position: static; } } /* ── CTA BAND ─────────────────────────────────────────── */ .cta-band { background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%); padding: 6rem 2rem; text-align: center; position: relative; overflow: hidden; } .cta-band::before { content:''; position: absolute; inset:0; background: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.06'/%3E%3C/svg%3E"); opacity: 0.5; } .cta-band * { position: relative; z-index: 1; } .cta-band .section-heading { color: white; max-width: 640px; margin: 0 auto; } .cta-band p { color: rgba(255,255,255,0.85); margin: 1.2rem auto 2.5rem; max-width: 480px; font-size: 1rem; } .cta-phone-big { font-family: var(--ff-title); font-size: clamp(2rem, 6vw, 4rem); color: white; letter-spacing: 0.06em; text-shadow: 0 2px 16px rgba(0,0,0,0.2); display: block; margin-bottom: 0.4rem; } .cta-phone-sub { font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.3em; text-transform: uppercase; color: rgba(255,255,255,0.7); display: block; margin-bottom: 2rem; } .btn-white { display: inline-flex; align-items: center; gap: 0.6rem; font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500; letter-spacing: 0.2em; text-transform: uppercase; padding: 1.1rem 2.4rem; background: white; color: var(--rose); border-radius: 2px; transition: transform 0.2s, box-shadow 0.2s; box-shadow: 0 4px 24px rgba(0,0,0,0.15); } .btn-white:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(0,0,0,0.2); } /* ── FOOTER ───────────────────────────────────────────── */ footer { background: var(--ink); padding: 4rem 2rem 2rem; color: rgba(255,255,255,0.5); font-family: var(--ff-sans); font-size: 0.75rem; } .footer-inner { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 3rem; padding-bottom: 3rem; border-bottom: 1px solid rgba(201,169,110,0.15); } .footer-brand-name { font-family: var(--ff-title); font-size: 1.1rem; color: white; letter-spacing: 0.1em; margin-bottom: 0.8rem; } .footer-brand-tag { line-height: 1.7; max-width: 280px; } .footer-socials { line-height: 1.7; max-width: 280px; color: white } .footer-col-title { font-family: var(--ff-title); font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; } .footer-links { list-style: none; line-height: 2.2; } .footer-links a { color: rgba(255,255,255,0.5); transition: color 0.25s; } .footer-links a:hover { color: var(--gold); } .footer-bottom { max-width: 1100px; margin: 2rem auto 0; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem; font-size: 0.65rem; letter-spacing: 0.1em; } .footer-disclaimer { max-width: 600px; line-height: 1.6; opacity: 0.5; } /* ── ANIMATIONS ───────────────────────────────────────── */ @keyframes fadeUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } } @keyframes shimmer { 0% { opacity: 0.3; } 50% { opacity: 1; } 100% { opacity: 0.3; } } .sparkle { animation: shimmer 2s infinite; } .sparkle:nth-child(2) { animation-delay: 0.4s; } .sparkle:nth-child(3) { animation-delay: 0.8s; } .sparkle:nth-child(4) { animation-delay: 1.2s; } .sparkle:nth-child(5) { animation-delay: 1.6s; } /* scroll reveal */ .reveal { opacity: 0; transform: translateY(28px); transition: opacity 0.7s var(--ease-silk), transform 0.7s var(--ease-silk); } .reveal.visible { opacity: 1; transform: none; } .reveal-delay-1 { transition-delay: 0.1s; } .reveal-delay-2 { transition-delay: 0.2s; } .reveal-delay-3 { transition-delay: 0.3s; } /* ── MOBILE ───────────────────────────────────────────── */ @media (max-width: 900px) { nav { padding: 1.2rem 1.5rem; } .nav-links { display: none; } .pillars { grid-template-columns: 1fr; gap: 2px; } .how-grid { grid-template-columns: 1fr; } .how-visual { display: none; } .characters-grid { grid-template-columns: repeat(2,1fr); } .testi-grid { grid-template-columns: 1fr; } .pricing-calculator { grid-template-columns: 1fr; } .footer-inner { grid-template-columns: 1fr; gap: 2rem; } .hero-photo-strip { display: none; } } </style> </head> <body> <!-- ══ NAVIGATION ══════════════════════════════════════════ --> <nav id="nav"> <a href="#" class="nav-logo"> <span class="crown">✦</span> Sophia's Magical Princess Party </a> <ul class="nav-links" aria-label="Site navigation"> <li><a href="#characters">Characters</a></li> <li><a href="#how">How It Works</a></li> <li><a href="#pricing">Pricing</a></li> <li><a href="#testimonials">Reviews</a></li> <li><a href="#faq">FAQ</a></li> </ul> <a href="#book" class="nav-cta">Book Now</a> </nav> <!-- ══ HERO ════════════════════════════════════════════════ --> <section class="hero" id="top"> <div class="hero-bg"></div> <div class="hero-arc hero-arc-1"></div> <div class="hero-arc hero-arc-2"></div> <div class="hero-arc hero-arc-3"></div> <!-- sparkle SVG layer --> <div class="sparkle-field" aria-hidden="true"> <svg viewBox="0 0 1200 700" preserveAspectRatio="xMidYMid slice"> <!-- 4-point star shape repeated --> <path class="sparkle" d="M200 120 L203 130 L213 133 L203 136 L200 146 L197 136 L187 133 L197 130Z" fill="#C9A96E" opacity="0.6"/> <path class="sparkle" d="M900 80 L903 90 L913 93 L903 96 L900 106 L897 96 L887 93 L897 90Z" fill="#D4768A" opacity="0.5"/> <path class="sparkle" d="M1050 300 L1052 308 L1060 310 L1052 312 L1050 320 L1048 312 L1040 310 L1048 308Z" fill="#A88EC0" opacity="0.5"/> <path class="sparkle" d="M150 400 L152 408 L160 410 L152 412 L150 420 L148 412 L140 410 L148 408Z" fill="#7EB8D4" opacity="0.45"/> <path class="sparkle" d="M600 50 L602 58 L610 60 L602 62 L600 70 L598 62 L590 60 L598 58Z" fill="#C9A96E" opacity="0.4"/> <circle cx="350" cy="600" r="2" fill="#D4768A" opacity="0.4"/> <circle cx="850" cy="550" r="2" fill="#C9A96E" opacity="0.35"/> <circle cx="100" cy="200" r="1.5" fill="#A88EC0" opacity="0.45"/> <circle cx="1100" cy="180" r="1.5" fill="#7EB8D4" opacity="0.4"/> </svg> </div> <p class="hero-eyebrow">South Houston's Premier Princess Experience</p> <h1 class="hero-title">Where Every Child Meets Their <em>Favorite Princess</em></h1> <p class="hero-subtitle">Professional actors in breathtaking, park-quality gowns bring the magic of beloved heroines directly to your child's celebration.</p> <div class="hero-ctas"> <a href="#book" class="btn-primary">✦ &nbsp;Book a Princess</a> <a href="#characters" class="btn-ghost">Meet the Characters</a> </div> <!-- photo strip: placeholder shapes representing real photos --> <div class="hero-photo-strip" aria-hidden="true"> <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img class="hero-photo-strip-img" src="https://i.ibb.co/Zydr7g7/IMG-0587.png"> </div> </figure> <figure style="background:linear-gradient(160deg,#F7C5D0,#D4768A)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img class="hero-photo-strip-img" src="https://i.ibb.co/W48dg0NR/40423367-1-A5-E-4-DF2-B76-C-D106-B30-EB9-EC.jpg"> </div> </figure> <figure style="background:linear-gradient(160deg,#D0B8E8,#A88EC0)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img class="hero-photo-strip-img" src="https://i.ibb.co/fVbZT1s1/7901-F55-C-362-C-412-F-AEE1-3535-D64-B4892.jpg"> </div> </figure> </div> <p class="since-badge"><span></span> Making Magic Real Since 2017 <span></span></p> </section> <!-- ══ PILLARS ══════════════════════════════════════════════ --> <section class="section" id="about"> <div class="section-inner"> <div class="gold-rule reveal">What Makes Us Different</div> <div class="pillars"> <div class="pillar reveal reveal-delay-1"> <!-- <div class="pillar-icon">👗</div> --> <div class="pillar-title">Top-Quality Costumes</div> <p class="pillar-text">Every gown is crafted with the same eye-catching detail you'd expect at a world-class theme park — your guests will be speechless.</p> <div class="pillar-photo-strip"> <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img class="pillar-photo-strip-img" src="https://i.ibb.co/2vtDjjM/scottish-princess-photos.jpg"> </div> </figure> </div> </div> <div class="pillar reveal reveal-delay-2"> <!-- <div class="pillar-icon">🎭</div> --> <div class="pillar-title">World Class Performers</div> <p class="pillar-text">Our performers fully embody their characters. From their first hello to the royal farewell, you can expect a magical time.</p> <div class="pillar-photo-strip"> <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img class="pillar-photo-strip-img" style="height: auto;" src="https://i.ibb.co/TMbhsVpy/Picsart-25-10-19-23-35-55-265.jpg"> </div> </figure> </div> </div> <div class="pillar reveal reveal-delay-3"> <!-- <div class="pillar-icon">🎀</div> --> <div class="pillar-title">Unique Activities</div> <p class="pillar-text">Storytime, singalongs, royal decrees, and more! Each visit makes the birthday child feel like the hero of their own story.</p> <div class="pillar-photo-strip"> <figure style="background:linear-gradient(160deg,#B5D4E8,#7EB8D4)"> <div style="height:100%;display:flex;align-items:center;justify-content:center;font-size:3rem;"> <img src="https://i.ibb.co/DgQV8Dmb/Picsart-25-10-06-15-42-26-667.jpg"> </div> </figure> </div> </div> </div> </div> </section> <hr class="section-divider" /> <!-- ══ CHARACTERS ══════════════════════════════════════════ --> <section class="section" id="characters"> <div class="section-inner"> <span class="section-label reveal">The Royal Court</span> <h2 class="section-heading reveal">Choose Your Character</h2> <p class="section-body reveal">Ice queens, pixies, ocean adventurers and beyond! Our beloved heroines are ready to make your child's birthday unforgettable.</p> <div class="characters-grid"> <div class="char-card reveal reveal-delay-1"> <!-- <div class="char-color"></div> --> <div class="char-info"> <span class="char-name">The Little Mermaid</span> <span class="char-desc">Sea & Song</span> </div> <img src="https://i.ibb.co/S4HWFbgG/AF2-A0-F5-D-F9-E3-419-A-9-BB9-AFCA61288104.jpg"> </div> <div class="char-card reveal reveal-delay-2"> <!-- <div class="char-color"></div> --> <div class="char-info"> <span class="char-name">The Bayou Princess</span> <span class="char-desc">Evening Star Wishes</span> </div> <img src="https://i.ibb.co/TqrmSGnF/Picsart-25-07-27-20-26-26-951.jpg"> </div> <div class="char-card reveal reveal-delay-3"> <!-- <div class="char-color"></div> --> <div class="char-info"> <span class="char-name">Popstar Impersonator</span> <span class="char-desc">Fearless & Bejeweled</span> </div> <img src="https://i.ibb.co/tTmZkvpm/Screenshot-20251112-151813-Instagram.jpg"> </div> <div class="char-card reveal reveal-delay-3"> <!-- <div class="char-color"></div> --> <div class="char-info"> <span class="char-name">Tinkerbell</span> <span class="char-desc">Faith, Trust & Pixiedust</span> </div> <img src="https://i.ibb.co/VWVkr5SF/Screenshot-20260407-204932-Gallery.jpg"> </div> </div> </div> </section> <!-- ══ HOW IT WORKS ═════════════════════════════════════════ --> <section class="section how" id="how"> <div class="section-inner"> <div class="how-grid"> <div> <span class="section-label reveal">Simple &amp; Magical</span> <h2 class="section-heading reveal">How to Book Your Royal Visit</h2> <ol class="how-steps" aria-label="Booking steps"> <li class="how-step reveal"> <span class="step-num" aria-hidden="true">01</span> <div> <div class="step-title">Fill out the Booking Form</div> <p class="step-text">Reach out with the form below to contact our team.</p> </div> </li> <li class="how-step reveal reveal-delay-1"> <span class="step-num" aria-hidden="true">02</span> <div> <div class="step-title">Pick Your Date & Package</div> <p class="step-text">We'll get back with you to finalize your selection and answer any questions. You're on the schedule at this point!</p> </div> </li> <li class="how-step reveal reveal-delay-2"> <span class="step-num" aria-hidden="true">03</span> <div> <div class="step-title">Await the Arrival</div> <p class="step-text">On the day, your princess will arrive in full costume. Watch your child's eyes light up as the magic becomes real.</p> </div> </li> <li class="how-step reveal reveal-delay-3"> <span class="step-num" aria-hidden="true">04</span> <div> <div class="step-title">Memories Made</div> <p class="step-text">Photo moments, activities, and royal moments, your child will be talking about this birthday for years to come.</p> </div> </li> </ol> <div class="call-highlight reveal"> <p>Still have questions? Feel free to call or text the number below. We'll get back to you as soon as possible to assist/</p> <div class="call-number">(xxx) xxx-xxxx</div> </div> </div> <div class="how-visual" aria-hidden="true"> <div class="how-photo"> <img src="https://i.ibb.co/Z6whK0cm/Picsart-26-03-14-20-37-39-493.jpg"> </div> <div class="how-photo"> <img src="https://i.ibb.co/fYZNSNRL/Picsart-26-03-14-20-51-35-508.jpg"> </div> </div> </div> </div> </section> <!-- ══ TESTIMONIALS ═════════════════════════════════════════ --> <section class="section testimonials" id="testimonials"> <div class="section-inner"> <span class="section-label reveal">From Our Families</span> <h2 class="section-heading reveal" style="color:white;">What People Are Saying</h2> <div class="testi-grid"> <div class="testi-card reveal reveal-delay-1"> <div class="testi-stars">★★★★★</div> <p class="testi-quote">They really know how to make the birthday kiddo feel special!</p> <p class="testi-author">Inshirah Barakat — Google</p> </div> <div class="testi-card reveal reveal-delay-2"> <div class="testi-stars">★★★★★</div> <p class="testi-quote">Great third experience using Sophia's! Love how in character they always are and very interactive. Highly recommend!</p> <p class="testi-author">Jessica Lyne — Facebook</p> </div> <div class="testi-card reveal reveal-delay-3"> <div class="testi-stars">★★★★★</div> <p class="testi-quote">Rapunzel was kind, genuine, and my kiddo was absolutely delighted by the visit!</p> <p class="testi-author">Becca Popland — Facebook</p> </div> <div class="testi-card reveal reveal-delay-1"> <div class="testi-stars">★★★★★</div> <p class="testi-quote">Our little princess received the best personal video message from The Snow Queen! She absolutely loved it!</p> <p class="testi-author">Jimee Jensen-Caudle — Facebook</p> </div> <div class="testi-card reveal reveal-delay-2"> <div class="testi-stars">★★★★★</div> <p class="testi-quote">Hands down the best present I could have ever bought my granddaughter for her birthday!</p> <p class="testi-author">James Scurlock — Google</p> </div> <div class="testi-card reveal reveal-delay-3" style="display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;border-style:dashed;gap:0.5rem;"> <div style="font-size:2rem;">⭐</div> <p style="color:rgba(255,255,255,0.5);font-size:0.8rem;font-family:var(--ff-sans);">Proudly serving South Houston families since 2017</p> <a href="#book" class="btn-white" style="margin-top:0.5rem;font-size:0.65rem;padding:0.8rem 1.6rem;">Leave a Review</a> </div> </div> </div> </section> <!-- ══ PRICING ══════════════════════════════════════════════ --> <section class="section" id="pricing"> <div class="section-inner"> <span class="section-label reveal">Transparent &amp; Simple</span> <h2 class="section-heading reveal">Build Your Royal Package</h2> <p class="section-body reveal">Customize your perfect party by selecting your character type, duration, and number of performers — and see your price instantly.</p> <div class="pricing-calculator"> <!-- LEFT: Selectors --> <div class="pc-selectors reveal"> <!-- Character Type --> <div class="pc-group"> <span class="pc-group-label">✦ &nbsp;Type of Character</span> <div class="pc-options"> <button class="pc-btn pc-char-btn active" data-group="type" data-val="princess" onclick="pcSelect(this)"> <span class="pc-char-icon">👑</span> <span>Princess</span> </button> <button class="pc-btn pc-char-btn" data-group="type" data-val="kpop" onclick="pcSelect(this)"> <span class="pc-char-icon">🎤</span> <span>K-Pop Star</span> </button> <button class="pc-btn pc-char-btn" data-group="type" data-val="impersonator" onclick="pcSelect(this)"> <span class="pc-char-icon">🌟</span> <span>Impersonator</span> </button> </div> </div> <!-- Duration --> <div class="pc-group"> <span class="pc-group-label">✦ &nbsp;Duration</span> <div class="pc-options"> <button class="pc-btn active" data-group="duration" data-val="60" onclick="pcSelect(this)"><span>1 Hour</span></button> <button class="pc-btn" data-group="duration" data-val="120" onclick="pcSelect(this)"><span>2 Hours</span></button> <button class="pc-btn" data-group="duration" data-val="30" onclick="pcSelect(this)"><span>30 Min</span></button> </div> </div> <!-- Number of Performers --> <div class="pc-group" id="pc-performer-group"> <span class="pc-group-label">✦ &nbsp;Number of Performers</span> <div class="pc-stepper"> <button class="pc-step-btn" onclick="pcStep(-1)">−</button> <span class="pc-step-count" id="pc-performer-count">1</span> <button class="pc-step-btn" onclick="pcStep(1)">+</button> <span class="pc-step-label">performer<span id="pc-plural"></span></span> </div> </div> <!-- What's included note --> <div style="margin-top:1rem; padding:1.5rem 1.8rem; background:white; border:1px solid rgba(201,169,110,0.2); border-radius:4px;"> <div style="font-family:var(--ff-sans);font-size:0.6rem;letter-spacing:0.3em;text-transform:uppercase;color:var(--gold);margin-bottom:0.8rem;">✦ &nbsp;Good to Know</div> <ul style="list-style:none;font-size:0.88rem;color:var(--text);line-height:1.9;"> <li style="display:flex;gap:0.6rem;">✦ &nbsp;30-min visits omit the sing-along</li> <li style="display:flex;gap:0.6rem;">✦ &nbsp;Makeovers require 2 hrs for 6+ children</li> <li style="display:flex;gap:0.6rem;">✦ &nbsp;Travel fee may apply based on location</li> <li style="display:flex;gap:0.6rem;">✦ &nbsp;All performers are fully costumed &amp; in-character</li> </ul> </div> </div> <!-- RIGHT: Result Card --> <div class="pc-result reveal reveal-delay-2"> <div class="pc-result-label">Your Estimate</div> <div class="pc-result-package" id="pc-package-name">The Royal Greeting</div> <div class="pc-result-desc" id="pc-package-desc">Princess · 30 Minutes · 1 Performer</div> <div class="pc-price-row"> <span class="pc-price-item">Base rate</span> <span class="pc-price-val" id="pc-base-val">$195</span> </div> <div class="pc-price-row"> <span class="pc-price-item">Additional performer(s)</span> <span class="pc-price-val" id="pc-add-performer-val">—</span> </div> <div class="pc-price-row"> <span class="pc-price-item">Character premium</span> <span class="pc-price-val" id="pc-char-premium-val">Included</span> </div> <div class="pc-total-row"> <span class="pc-total-label">Total Estimate</span> <span class="pc-total-price" id="pc-total">$195</span> </div> <ul class="pc-features" id="pc-features-list"> <li>In-character princess actress</li> <li>Meet &amp; greet with birthday child</li> <li>Photo opportunities</li> <li>Royal birthday blessing</li> </ul> <a href="#book" class="pc-book-btn">Continue Inquiry &rarr;</a> <p style="font-family:var(--ff-sans);font-size:0.65rem;color:rgba(255,255,255,0.35);text-align:center;margin-top:1rem;line-height:1.6;"> Estimates are approximate. Final pricing confirmed during booking. Travel fees may apply. </p> </div> </div><!-- /.pricing-calculator --> <p class="pricing-note reveal">All packages include a fully costumed performer in character throughout your event. We proudly serve the South Houston area.</p> </div> </section> <script> (function() { // ── PRICING DATA ───────────────────────────────────────── const BASE = { 60: 195, 120: 295, 30: 165}; const EXTRA_PERFORMER = { 30: 100, 60: 100, 120: 100 }; const CHAR_PREMIUM = { princess: 0, kpop: 30, impersonator: 55 }; const CHAR_PREMIUM_LABEL = { princess: 'Included', kpop: '+$30', impersonator: '+$55' }; // Max performers per type const MAX_PERFORMERS = { princess: 4, kpop: 3, impersonator: 1 }; const PACKAGE_NAMES = { princess: { 30: 'The Royal Greeting', 60: 'The Enchanted Party', 120: 'The Magical Kingdom' }, kpop: { 30: 'The Pop Showcase', 60: 'The Idol Experience', 120: 'The K-Pop Extravaganza' }, impersonator: { 30: 'The Star Appearance', 60: 'The Celebrity Bash', 120: 'The Superstar Soirée' } }; const FEATURES = { princess: { 30: ['In-character princess actress','Meet & greet with birthday child','Photo opportunities','Royal birthday blessing'], 60: ['Full character immersion','Storytime & singalong','Royal coronation ceremony','Photo opportunities','Personalized attention for birthday child'], 120: ['Extended character experience','Full activity suite','Royal games & crafts','Coronation ceremony','Makeover activity (6+ children require 2 hrs)','Group singalong & dancing'] }, kpop: { 30: ['K-Pop idol in full costume','High-energy mini performance','Fan photo experience','Group song moment'], 60: ['Full K-Pop performance set','Dance-along with guests','Costume photo ops','Fan interaction time','Birthday song performance'], 120: ['Extended idol experience','Multiple performance segments','Dance tutorial for guests','Group fan photo session','Personalized fan card signing','Birthday surprise moment'] }, impersonator: { 30: ['Celebrity look-alike in full costume','Meet & greet photo moment','In-character performance','Birthday recognition'], 60: ['Full celebrity character experience','Live performance/singing (if applicable)','Photo opportunities','Interactive fan moment','Personalized birthday greeting'], 120: ['Extended celebrity appearance','Multiple performance moments','Guest interaction time','Costume photo experience','Games themed to the celebrity','Autographed keepsake'] } }; // State let state = { type: 'princess', duration: 60, performers: 1 }; window.pcSelect = function(btn) { const group = btn.dataset.group; const val = btn.dataset.val; btn.closest('.pc-options').querySelectorAll('.pc-btn').forEach(b => b.classList.remove('active')); btn.classList.add('active'); state[group] = group === 'duration' ? parseInt(val) : val; if (group === 'type') { const max = MAX_PERFORMERS[state.type]; const performerGroup = document.getElementById('pc-performer-group'); if (state.type === 'impersonator') { // Lock to 1 and hide the stepper state.performers = 1; performerGroup.style.display = 'none'; } else { performerGroup.style.display = ''; // Clamp performers to new max if (state.performers > max) state.performers = max; } document.getElementById('pc-performer-count').textContent = state.performers; document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : ''; } updateCalc(); }; window.pcStep = function(dir) { const max = MAX_PERFORMERS[state.type]; state.performers = Math.min(max, Math.max(1, state.performers + dir)); document.getElementById('pc-performer-count').textContent = state.performers; document.getElementById('pc-plural').textContent = state.performers > 1 ? 's' : ''; updateCalc(); }; function updateCalc() { const { type, duration, performers } = state; const base = BASE[duration]; const addPerf = performers > 1 ? EXTRA_PERFORMER[duration] * (performers - 1) : 0; const charPrem = CHAR_PREMIUM[type]; const total = base + addPerf + charPrem; const totalEl = document.getElementById('pc-total'); totalEl.classList.add('updating'); setTimeout(() => { totalEl.textContent = '$' + total.toLocaleString(); totalEl.classList.remove('updating'); }, 180); const durLabel = duration === 30 ? '30 Minutes' : duration === 60 ? '1 Hour' : '2 Hours'; const typeLabel = type === 'princess' ? 'Princess' : type === 'kpop' ? 'K-Pop Star' : 'Impersonator'; document.getElementById('pc-package-name').textContent = PACKAGE_NAMES[type][duration]; document.getElementById('pc-package-desc').textContent = typeLabel + ' · ' + durLabel + ' · ' + performers + ' Performer' + (performers > 1 ? 's' : ''); document.getElementById('pc-base-val').textContent = '$' + base; document.getElementById('pc-add-performer-val').textContent = addPerf > 0 ? '$' + addPerf : '—'; document.getElementById('pc-char-premium-val').textContent = CHAR_PREMIUM_LABEL[type]; const ul = document.getElementById('pc-features-list'); ul.innerHTML = FEATURES[type][duration].map(f => `<li>${f}</li>`).join(''); } })(); </script> <!-- ══ FAQ ══════════════════════════════════════════════════ --> <section class="section" id="faq" style="background:#F9F4F7;"> <div class="section-inner"> <span class="section-label reveal">Questions &amp; Answers</span> <h2 class="section-heading reveal">Frequently Asked</h2> <div style="margin-top:3rem;max-width:720px;" class="reveal"> <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;"> <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;"> What area do you serve? <span style="color:var(--gold);">+</span> </summary> <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We proudly serve the South Houston area and surrounding communities. Call us to confirm your specific location when booking.</p> </details> <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;"> <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;"> How far in advance should I book? <span style="color:var(--gold);">+</span> </summary> <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We recommend booking 2–4 weeks in advance, especially for weekend dates which fill up quickly. Give us a call to check availability!</p> </details> <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;"> <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;"> Do you offer video messages? <span style="color:var(--gold);">+</span> </summary> <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Yes! Personalized video messages from your chosen princess are available as an add-on. Perfect for birthdays, holidays, or just a magical surprise.</p> </details> <details style="border-bottom:1px solid rgba(201,169,110,0.3);padding:1.4rem 0;cursor:pointer;"> <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;"> Are your performers background-checked? <span style="color:var(--gold);">+</span> </summary> <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">Absolutely. The safety and comfort of your children is our top priority. All performers are vetted, professional, and experienced in working with children.</p> </details> <details style="padding:1.4rem 0;cursor:pointer;"> <summary style="font-family:var(--ff-title);font-size:1rem;color:var(--ink);list-style:none;display:flex;justify-content:space-between;align-items:center;"> Which characters are available? <span style="color:var(--gold);">+</span> </summary> <p style="margin-top:0.8rem;font-size:0.95rem;color:var(--text);">We have a rotating roster of beloved heroine-inspired characters. Call us to find out which princesses are currently available for your date!</p> </details> </div> </div> </section> <!-- ══ CTA BAND ═════════════════════════════════════════════ --> <section class="cta-band" id="book"> <span class="section-label" style="color:rgba(255,255,255,0.7)">Ready to Create Magic?</span> <h2 class="section-heading" style="max-width:640px;margin:0.8rem auto 0;">Book Your Princess Today</h2> <p>The most magical birthday party your child has ever had is just one phone call away. We'd love to hear about your celebration!</p> <a class="cta-phone-big" href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a> <a href="tel:xxxxxxxxxx" class="btn-white">✦ &nbsp;Call to Book Now</a> </section> <!-- ══ FOOTER ═══════════════════════════════════════════════ --> <footer> <div class="footer-inner"> <div> <div class="footer-brand-name">✦ Sophia's Magical Princess Party</div> <p class="footer-brand-tag">Bringing beloved heroine characters to life for children's celebrations across the South Houston area since 2017.</p> <p class="footer-socials">Insert Socials Here</p> </div> <div> <div class="footer-col-title">Navigate</div> <ul class="footer-links"> <li><a href="#characters">Characters</a></li> <li><a href="#how">How It Works</a></li> <li><a href="#pricing">Pricing</a></li> <li><a href="#testimonials">Reviews</a></li> <li><a href="#faq">FAQ</a></li> </ul> </div> <div> <div class="footer-col-title">Contact</div> <ul class="footer-links"> <li><a href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a></li> <li>South Houston, TX</li> <li>Mon–Sat, 9am–7pm</li> </ul> </div> </div> <div class="footer-bottom"> <span>© 2025 Sophia's Magical Princess Party. All rights reserved.</span> <span class="footer-disclaimer">We offer unique original characters inspired by classic stories and fables. We are a private company unaffiliated with any major production company or theme park. Any similarity to trademarked characters is coincidental.</span> </div> </footer> <script> // ── NAV scroll effect const nav = document.getElementById('nav'); window.addEventListener('scroll', () => { nav.classList.toggle('scrolled', window.scrollY > 60); }, { passive: true }); // ── Scroll reveal const reveals = document.querySelectorAll('.reveal'); const io = new IntersectionObserver((entries) => { entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } }); }, { threshold: 0.12 }); reveals.forEach(el => io.observe(el)); // ── FAQ caret toggle document.querySelectorAll('details').forEach(d => { d.addEventListener('toggle', () => { const icon = d.querySelector('summary span'); if (icon) icon.textContent = d.open ? '−' : '+'; }); }); </script> </body> </html>
'''


Here’s your **characters.html** page, fully matched to your existing design system. Here’s a rundown of everything built in:

**Design Fidelity**  
All CSS tokens (`--gold`, `--rose`, `--lavender`, `--cream`, Cinzel/Cormorant Garamond/Jost fonts, silk easing, grain overlays, decorative rings) are pulled directly from your template — the page will look like a native extension of the site.

**All 23 Characters**  
Each card includes a name, category, emoji placeholder (replaced by your photo), an outfit count badge, a “View Outfits” hover cue, and a gradient overlay. Cards are pre-sorted with Princesses (16), K-Pop Stars (3 — Luna Star, Sora Shine, Nova Beat), and Impersonators (2 — Pop Royalty, Diva Supreme), plus 2 additional princess slots.

**Filter Bar**  
Buttons let parents instantly sort by: All · Princesses · K-Pop Stars · Impersonators · “Multiple Outfits Only.”

**Lightbox System**  
Clicking any card opens a modal with all outfit thumbnails shown simultaneously with their labels and sub-labels (e.g. “Holiday Special,” “Fan Meet Edition”). Closeable via ✕ button, clicking outside, or `Escape`. A “Book This Character” CTA lives inside the lightbox.

**Sales Highlight System**  
To feature any outfit, simply add `class="outfit--featured"` to its thumbnail — this applies a gold border ring, glow shadow, and a badge. The badge text is controlled by `data-badge="Your Label"` (defaults to “Most Popular” if omitted). The entire highlight color scheme is driven by three CSS variables at the top of the file — swap them once to restyle all highlights site-wide.

**imgbb CDN**  
All `<img>` tags use `https://i.ibb.co/` URLs with `loading="lazy"` and graceful `onerror` fallbacks. Upload your photos at 800–1200px wide portrait (3:4) for best results — the detailed instructions are in a comment block above the lightbox JS.

'''html
`<!DOCTYPE html>`

`<html lang="en">`

`<head>`

`<meta charset="UTF-8" />`

`<meta name="viewport" content="width=device-width, initial-scale=1.0" />`

`<title>Our Characters — Sophia's Magical Princess Party</title>`

`<link rel="preconnect" href="https://fonts.googleapis.com" />`

`<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />`

`<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Cinzel:wght@400;500;600&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" />`

`<style>`

`/* ════════════════════════════════════════════════════════════`

`DESIGN TOKENS — matched exactly to SMPPv3.html`

`════════════════════════════════════════════════════════════ */`

`:root {`

`--gold: #C9A96E;`

`--gold-lt: #E8D5A3;`

`--rose: #D4768A;`

`--rose-lt: #F2C4CF;`

`--lavender: #A88EC0;`

`--sky: #7EB8D4;`

`--cream: #FAF6F0;`

`--ink: #1A1118;`

`--ink-soft: #3D2B3A;`

`--text: #4A3A46;`

`--ff-title: 'Cinzel', serif;`

`--ff-serif: 'Cormorant Garamond', serif;`

`--ff-sans: 'Jost', sans-serif;`

`--ease-silk: cubic-bezier(0.25, 0.46, 0.45, 0.94);`

`/* ── SALES HIGHLIGHT SYSTEM ────────────────────────────────`

`To mark an outfit as "featured" / drive sales, add the`

`class .outfit--featured to any .outfit-thumb element.`

`Swap out the color variables below to change the highlight`

`palette site-wide without touching individual cards. */`

`--highlight-border: #C9A96E; /* gold ring on card */`

`--highlight-badge-bg: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);`

`--highlight-badge-text: #fff;`

`--highlight-glow: rgba(201,169,110,0.28); /* card glow shadow */`

`}`

`/* ── RESET ──────────────────────────────────────────────── */`

`*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }`

`html { scroll-behavior: smooth; }`

`body {`

`background: var(--cream);`

`color: var(--text);`

`font-family: var(--ff-serif);`

`font-size: 18px;`

`line-height: 1.7;`

`overflow-x: hidden;`

`}`

`img { display: block; max-width: 100%; }`

`a { color: inherit; text-decoration: none; }`

`/* ── NAVIGATION (identical to template) ──────────────────── */`

`nav {`

`position: fixed; top: 0; left: 0; right: 0; z-index: 200;`

`display: flex; align-items: center; justify-content: space-between;`

`padding: 1.2rem 4rem;`

`background: transparent;`

`transition: background 0.4s var(--ease-silk), box-shadow 0.4s;`

`}`

`nav.scrolled {`

`background: rgba(250,246,240,0.96);`

`box-shadow: 0 1px 24px rgba(26,17,24,0.08);`

`backdrop-filter: blur(8px);`

`}`

`.nav-logo {`

`font-family: var(--ff-title); font-size: 1rem;`

`letter-spacing: 0.15em; color: var(--ink);`

`display: flex; align-items: center; gap: 0.6rem;`

`}`

`.nav-logo .crown { font-size: 1.2rem; }`

`.nav-links {`

`display: flex; gap: 2.4rem; list-style: none;`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`}`

`.nav-links a {`

`color: var(--ink-soft); position: relative; transition: color 0.25s;`

`}`

`.nav-links a::after {`

`content:''; position: absolute; left:0; bottom:-3px; width:0; height:1px;`

`background: var(--gold); transition: width 0.3s var(--ease-silk);`

`}`

`.nav-links a:hover { color: var(--gold); }`

`.nav-links a:hover::after { width: 100%; }`

`.nav-cta {`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`padding: 0.65rem 1.6rem;`

`border: 1px solid var(--gold); color: var(--gold);`

`transition: background 0.3s, color 0.3s; border-radius: 2px;`

`}`

`.nav-cta:hover { background: var(--gold); color: var(--cream); }`

`/* ── PAGE HERO ────────────────────────────────────────────── */`

`.page-hero {`

`position: relative;`

`min-height: 42vh;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`text-align: center;`

`padding: 10rem 2rem 5rem;`

`overflow: hidden;`

`}`

`.page-hero-bg {`

`position: absolute; inset: 0;`

`background:`

`radial-gradient(ellipse 80% 60% at 50% 0%, rgba(212,118,138,0.18) 0%, transparent 70%),`

`radial-gradient(ellipse 60% 70% at 15% 60%, rgba(168,142,192,0.14) 0%, transparent 65%),`

`radial-gradient(ellipse 55% 50% at 85% 55%, rgba(126,184,212,0.12) 0%, transparent 60%),`

`linear-gradient(175deg, #FDF9F4 0%, #F7EEF5 50%, #EFF3F9 100%);`

`}`

`.page-hero-bg::after {`

`content: '';`

`position: absolute; inset: 0;`

`background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");`

`opacity: 0.6;`

`}`

`/* decorative rings */`

`.hero-arc {`

`position: absolute; border-radius: 50%;`

`border: 1px solid rgba(201,169,110,0.22);`

`pointer-events: none;`

`}`

`.hero-arc-1 { width: 420px; height: 420px; top:50%; left:50%; transform:translate(-50%,-50%); }`

`.hero-arc-2 { width: 640px; height: 640px; top:50%; left:50%; transform:translate(-50%,-50%); }`

`.page-hero-eyebrow {`

`position: relative;`

`font-family: var(--ff-sans); font-size: 0.65rem; font-weight: 400;`

`letter-spacing: 0.35em; text-transform: uppercase;`

`color: var(--gold); margin-bottom: 1.4rem;`

`opacity: 0; animation: fadeUp 0.8s 0.2s var(--ease-silk) forwards;`

`}`

`.page-hero-title {`

`position: relative;`

`font-family: var(--ff-title);`

`font-size: clamp(2rem, 5vw, 4rem);`

`font-weight: 500; line-height: 1.12;`

`color: var(--ink); letter-spacing: 0.02em;`

`max-width: 760px;`

`opacity: 0; animation: fadeUp 0.9s 0.35s var(--ease-silk) forwards;`

`}`

`.page-hero-title em {`

`font-style: italic;`

`background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 50%, var(--sky) 100%);`

`-webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;`

`}`

`.page-hero-sub {`

`position: relative;`

`margin-top: 1.4rem;`

`font-family: var(--ff-serif); font-size: 1.15rem; font-weight: 300;`

`color: var(--text); max-width: 520px; line-height: 1.7;`

`opacity: 0; animation: fadeUp 0.9s 0.5s var(--ease-silk) forwards;`

`}`

`/* ── GOLD RULE DIVIDER ────────────────────────────────────── */`

`.gold-rule {`

`display: flex; align-items: center; gap: 1rem;`

`color: var(--gold); font-family: var(--ff-title); letter-spacing: 0.25em;`

`font-size: 0.6rem; text-transform: uppercase;`

`}`

`.gold-rule::before, .gold-rule::after {`

`content:''; flex:1; height:1px;`

`background: linear-gradient(90deg, transparent, var(--gold-lt), transparent);`

`}`

`/* ── SECTION WRAPPERS ─────────────────────────────────────── */`

`.section { padding: 7rem 2rem; }`

`.section-inner { max-width: 1200px; margin: 0 auto; }`

`.section-label {`

`font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.35em;`

`text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; display: block;`

`}`

`.section-heading {`

`font-family: var(--ff-title);`

`font-size: clamp(1.8rem, 4vw, 3rem);`

`font-weight: 500; line-height: 1.18;`

`color: var(--ink); letter-spacing: 0.02em;`

`}`

`.section-body {`

`font-size: 1.05rem; line-height: 1.8; color: var(--text);`

`max-width: 560px; margin-top: 1.2rem;`

`}`

`/* ── FILTER BAR ───────────────────────────────────────────── */`

`.filter-bar {`

`display: flex; flex-wrap: wrap; gap: 0.6rem;`

`margin-top: 2.8rem; margin-bottom: 3.5rem;`

`}`

`.filter-btn {`

`font-family: var(--ff-sans); font-size: 0.68rem; font-weight: 400;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`padding: 0.55rem 1.3rem;`

`border: 1px solid rgba(201,169,110,0.35);`

`background: white; color: var(--text); border-radius: 2px;`

`cursor: pointer;`

`transition: all 0.22s var(--ease-silk);`

`}`

`.filter-btn:hover { border-color: var(--rose); color: var(--rose); }`

`.filter-btn.active { background: var(--ink); border-color: var(--ink); color: white; }`

`/* ── CHARACTER GRID ───────────────────────────────────────── */`

`.characters-grid {`

`display: grid;`

`grid-template-columns: repeat(4, 1fr);`

`gap: 1.6rem;`

`}`

`/* ── CHARACTER CARD ───────────────────────────────────────── */`

`.char-card {`

`position: relative; border-radius: 4px; overflow: hidden;`

`aspect-ratio: 3/4;`

`background: #f0e8f0;`

`cursor: pointer;`

`box-shadow: 0 4px 16px rgba(26,17,24,0.08);`

`transition: transform 0.4s var(--ease-silk), box-shadow 0.4s;`

`}`

`.char-card:hover {`

`transform: translateY(-8px) scale(1.02);`

`box-shadow: 0 20px 56px rgba(26,17,24,0.15);`

`}`

`/* gradient overlay so text is always readable */`

`.char-card::before {`

`content:''; position: absolute; inset: 0; z-index: 1;`

`background: linear-gradient(0deg, rgba(26,17,24,0.72) 0%, rgba(26,17,24,0.08) 55%, transparent 100%);`

`transition: opacity 0.3s;`

`}`

`.char-card:hover::before { opacity: 0.85; }`

`/* character photo — filled from imgbb CDN */`

`.char-photo {`

`width: 100%; height: 100%; object-fit: cover;`

`object-position: top center;`

`transition: transform 0.6s var(--ease-silk);`

`}`

`.char-card:hover .char-photo { transform: scale(1.06); }`

`/* placeholder gradient when no image is set yet */`

`.char-placeholder {`

`position: absolute; inset: 0;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`gap: 0.5rem; color: rgba(60,40,60,0.35);`

`font-family: var(--ff-sans); font-size: 0.6rem;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`pointer-events: none;`

`}`

`.char-placeholder span { font-size: 2.4rem; }`

`/* card text info */`

`.char-info {`

`position: absolute; bottom: 0; left: 0; right: 0; z-index: 2;`

`padding: 1.4rem 1.2rem 1.2rem;`

`}`

`.char-name {`

`font-family: var(--ff-title); font-size: 0.98rem;`

`letter-spacing: 0.08em; color: white;`

`display: block; margin-bottom: 0.15rem;`

`}`

`.char-type {`

`font-family: var(--ff-sans); font-size: 0.62rem;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`color: rgba(255,255,255,0.65);`

`}`

`/* outfit count badge (bottom-right) */`

`.char-outfit-badge {`

`position: absolute; top: 0.8rem; right: 0.8rem; z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.58rem;`

`letter-spacing: 0.12em; text-transform: uppercase;`

`background: rgba(26,17,24,0.55);`

`color: rgba(255,255,255,0.85);`

`backdrop-filter: blur(4px);`

`border: 1px solid rgba(255,255,255,0.18);`

`border-radius: 2px; padding: 0.3rem 0.65rem;`

`transition: opacity 0.25s;`

`}`

`.char-card:hover .char-outfit-badge { opacity: 0; } /* hides on hover — lightbox cue shows */`

`/* "view outfits" hover cue */`

`.char-view-cue {`

`position: absolute; top: 50%; left: 50%; transform: translate(-50%, -40%);`

`z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.22em;`

`text-transform: uppercase; color: white;`

`display: flex; flex-direction: column; align-items: center; gap: 0.5rem;`

`opacity: 0;`

`transition: opacity 0.3s var(--ease-silk), transform 0.3s var(--ease-silk);`

`pointer-events: none;`

`}`

`.char-view-cue::before {`

`content: '✦'; font-size: 1.4rem; color: var(--gold-lt);`

`animation: pulse 2s infinite;`

`}`

`.char-card:hover .char-view-cue {`

`opacity: 1;`

`transform: translate(-50%, -50%);`

`}`

`/* ── "NEW" & CATEGORY LABEL BADGES ─────────────────────────── */`

`/* These are positioned top-left on the card */`

`.char-badge {`

`position: absolute; top: 0.8rem; left: 0.8rem; z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.55rem;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`padding: 0.25rem 0.6rem; border-radius: 2px;`

`color: white;`

`}`

`.char-badge--new { background: var(--sky); }`

`.char-badge--kpop { background: var(--lavender); }`

`.char-badge--imperson { background: var(--rose); }`

`/* ════════════════════════════════════════════════════════════`

`LIGHTBOX SYSTEM`

`Opens when a character card is tapped/clicked.`

`Shows all outfit variants with labels.`

`════════════════════════════════════════════════════════════ */`

`.lightbox-overlay {`

`position: fixed; inset: 0; z-index: 900;`

`background: rgba(26,17,24,0.88);`

`backdrop-filter: blur(10px);`

`display: flex; align-items: center; justify-content: center;`

`padding: 1.5rem;`

`opacity: 0; pointer-events: none;`

`transition: opacity 0.35s var(--ease-silk);`

`}`

`.lightbox-overlay.open {`

`opacity: 1; pointer-events: all;`

`}`

`.lightbox {`

`background: var(--cream);`

`border-radius: 6px;`

`max-width: 1040px; width: 100%;`

`max-height: 90vh;`

`overflow-y: auto;`

`position: relative;`

`box-shadow: 0 32px 80px rgba(26,17,24,0.45);`

`transform: translateY(20px);`

`transition: transform 0.35s var(--ease-silk);`

`}`

`.lightbox-overlay.open .lightbox { transform: translateY(0); }`

`/* scrollbar styling */`

`.lightbox::-webkit-scrollbar { width: 4px; }`

`.lightbox::-webkit-scrollbar-track { background: transparent; }`

`.lightbox::-webkit-scrollbar-thumb { background: var(--gold-lt); border-radius: 4px; }`

`.lightbox-header {`

`display: flex; align-items: flex-start; justify-content: space-between;`

`padding: 2.2rem 2.4rem 1.4rem;`

`border-bottom: 1px solid rgba(201,169,110,0.22);`

`position: sticky; top: 0; background: var(--cream); z-index: 5;`

`}`

`.lightbox-char-name {`

`font-family: var(--ff-title); font-size: clamp(1.3rem, 3vw, 2rem);`

`letter-spacing: 0.06em; color: var(--ink);`

`}`

`.lightbox-char-type {`

`font-family: var(--ff-sans); font-size: 0.62rem;`

`letter-spacing: 0.25em; text-transform: uppercase;`

`color: var(--gold); margin-top: 0.3rem;`

`}`

`.lightbox-char-desc {`

`font-family: var(--ff-serif); font-size: 0.95rem; font-weight: 300;`

`color: var(--text); max-width: 480px; margin-top: 0.6rem; line-height: 1.65;`

`}`

`.lightbox-close {`

`width: 40px; height: 40px; flex-shrink: 0;`

`border: 1px solid rgba(201,169,110,0.35);`

`background: white; border-radius: 2px; cursor: pointer;`

`display: flex; align-items: center; justify-content: center;`

`font-size: 1.1rem; color: var(--ink-soft);`

`transition: background 0.2s, color 0.2s;`

`margin-left: 1.5rem; margin-top: 0.2rem;`

`}`

`.lightbox-close:hover { background: var(--ink); color: white; }`

`/* outfit grid inside lightbox */`

`.lightbox-outfits {`

`display: grid;`

`grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));`

`gap: 1.4rem;`

`padding: 2rem 2.4rem 2.4rem;`

`}`

`/* ── INDIVIDUAL OUTFIT THUMBNAIL ──────────────────────────── */`

`.outfit-thumb {`

`position: relative;`

`border-radius: 4px; overflow: hidden;`

`aspect-ratio: 3/4;`

`background: #f0e8f0;`

`cursor: default;`

`box-shadow: 0 3px 12px rgba(26,17,24,0.08);`

`border: 2px solid transparent;`

`transition: transform 0.3s var(--ease-silk), box-shadow 0.3s, border-color 0.3s;`

`}`

`.outfit-thumb:hover {`

`transform: translateY(-4px);`

`box-shadow: 0 12px 32px rgba(26,17,24,0.12);`

`}`

`.outfit-thumb img {`

`width: 100%; height: 100%;`

`object-fit: cover; object-position: top center;`

`}`

`.outfit-placeholder {`

`position: absolute; inset: 0;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`gap: 0.4rem; color: rgba(60,40,60,0.3);`

`font-family: var(--ff-sans); font-size: 0.58rem;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`}`

`.outfit-placeholder span { font-size: 2rem; }`

`/* outfit label bar at bottom of thumb */`

`.outfit-label {`

`position: absolute; bottom: 0; left: 0; right: 0;`

`padding: 0.7rem 0.8rem 0.65rem;`

`background: linear-gradient(0deg, rgba(26,17,24,0.82) 0%, transparent 100%);`

`font-family: var(--ff-title); font-size: 0.7rem;`

`letter-spacing: 0.07em; color: white;`

`text-align: center;`

`}`

`.outfit-label small {`

`display: block;`

`font-family: var(--ff-sans); font-size: 0.55rem;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`color: rgba(255,255,255,0.6); margin-top: 0.1rem;`

`}`

`/* ════════════════════════════════════════════════════════════`

`FEATURED / SALES-HIGHLIGHT OUTFIT`

`─────────────────────────────────────────────────────────`

`Add class .outfit--featured to any .outfit-thumb to:`

`• Apply a gold border ring`

`• Show a "Most Popular" badge`

`• Add a subtle gold glow shadow`

`Change the badge text by setting data-badge="Your Label"`

`on the element (defaults to "Most Popular" if omitted).`

`════════════════════════════════════════════════════════════ */`

`.outfit--featured {`

`border-color: var(--highlight-border);`

`box-shadow:`

`0 3px 12px rgba(26,17,24,0.08),`

`0 0 0 1px var(--highlight-border),`

`0 8px 28px var(--highlight-glow);`

`}`

`.outfit--featured:hover {`

`box-shadow:`

`0 12px 32px rgba(26,17,24,0.13),`

`0 0 0 1px var(--highlight-border),`

`0 12px 36px var(--highlight-glow);`

`}`

`/* featured badge — pseudo-element driven, no extra HTML needed */`

`.outfit--featured::after {`

`content: attr(data-badge); /* reads data-badge="…" or falls back below */`

`position: absolute; top: 0.7rem; left: 0.7rem; z-index: 4;`

`font-family: var(--ff-sans); font-size: 0.52rem;`

`font-weight: 500; letter-spacing: 0.14em; text-transform: uppercase;`

`padding: 0.25rem 0.65rem;`

`background: var(--highlight-badge-bg);`

`color: var(--highlight-badge-text);`

`border-radius: 2px;`

`box-shadow: 0 2px 8px rgba(212,118,138,0.35);`

`}`

`/* fallback text when data-badge is empty or missing */`

`.outfit--featured:not([data-badge])::after,`

`.outfit--featured[data-badge=""]::after {`

`content: 'Most Popular';`

`}`

`/* ── LIGHTBOX CTA BAR ──────────────────────────────────────── */`

`.lightbox-cta {`

`border-top: 1px solid rgba(201,169,110,0.22);`

`padding: 1.6rem 2.4rem;`

`display: flex; align-items: center; justify-content: space-between;`

`flex-wrap: wrap; gap: 1rem;`

`background: white;`

`}`

`.lightbox-cta-text {`

`font-family: var(--ff-serif); font-size: 1.05rem; font-weight: 300;`

`color: var(--text);`

`}`

`.lightbox-cta-text strong {`

`font-weight: 500; color: var(--ink); font-style: italic;`

`}`

`.btn-book-char {`

`display: inline-flex; align-items: center; gap: 0.6rem;`

`font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 500;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`padding: 0.9rem 2rem;`

`background: linear-gradient(135deg, var(--rose), var(--lavender));`

`color: white; border-radius: 2px;`

`transition: opacity 0.2s, transform 0.2s;`

`box-shadow: 0 4px 20px rgba(212,118,138,0.35);`

`white-space: nowrap;`

`}`

`.btn-book-char:hover { opacity: 0.88; transform: translateY(-2px); }`

`/* ── SCROLL REVEAL ────────────────────────────────────────── */`

`.reveal { opacity: 0; transform: translateY(22px); transition: opacity 0.7s var(--ease-silk), transform 0.7s var(--ease-silk); }`

`.reveal.visible { opacity: 1; transform: none; }`

`/* ── ANIMATIONS ───────────────────────────────────────────── */`

`@keyframes fadeUp {`

`to { opacity: 1; transform: translateY(0); }`

`}`

`@keyframes pulse {`

`0%, 100% { opacity: 1; transform: scale(1); }`

`50% { opacity: 0.6; transform: scale(1.15); }`

`}`

`/* ── SECTION DISCLAIMER ───────────────────────────────────── */`

`.char-disclaimer {`

`margin-top: 3.5rem;`

`padding: 1.4rem 2rem;`

`border: 1px solid rgba(201,169,110,0.25);`

`border-radius: 2px;`

`background: white;`

`font-family: var(--ff-sans); font-size: 0.7rem;`

`letter-spacing: 0.06em; color: var(--text);`

`line-height: 1.6;`

`}`

`/* ── CTA BAND ─────────────────────────────────────────────── */`

`.cta-band {`

`background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);`

`padding: 6rem 2rem; text-align: center; position: relative; overflow: hidden;`

`}`

`.cta-band::before {`

`content:''; position: absolute; inset:0;`

`background: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.06'/%3E%3C/svg%3E");`

`opacity: 0.5;`

`}`

`.cta-band .section-label { color: rgba(255,255,255,0.75); position: relative; }`

`.cta-band .section-heading { color: white; position: relative; max-width: 640px; margin: 0.8rem auto 0; }`

`.cta-band p { position: relative; margin-top: 1.2rem; color: rgba(255,255,255,0.85); font-size: 1.05rem; }`

`.cta-phone-big {`

`display: block; position: relative;`

`font-family: var(--ff-title); font-size: clamp(2rem, 5vw, 3.5rem);`

`letter-spacing: 0.08em; color: white;`

`margin: 1.8rem auto 2rem;`

`}`

`.btn-white {`

`display: inline-flex; align-items: center; gap: 0.6rem; position: relative;`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`padding: 1.1rem 2.6rem;`

`background: white; color: var(--rose); border-radius: 2px;`

`transition: background 0.3s, transform 0.2s;`

`box-shadow: 0 4px 24px rgba(26,17,24,0.2);`

`}`

`.btn-white:hover { background: var(--cream); transform: translateY(-2px); }`

`/* ── FOOTER ───────────────────────────────────────────────── */`

`footer {`

`background: var(--ink); color: rgba(255,255,255,0.6);`

`padding: 4rem 2rem 2rem;`

`}`

`.footer-inner {`

`max-width: 1100px; margin: 0 auto;`

`display: grid; grid-template-columns: 2fr 1fr 1fr;`

`gap: 3rem; padding-bottom: 3rem;`

`border-bottom: 1px solid rgba(255,255,255,0.08);`

`}`

`.footer-brand-name {`

`font-family: var(--ff-title); font-size: 1rem;`

`letter-spacing: 0.12em; color: white; margin-bottom: 1rem;`

`}`

`.footer-brand-tag { font-size: 0.85rem; line-height: 1.7; max-width: 300px; }`

`.footer-col-title {`

`font-family: var(--ff-sans); font-size: 0.6rem;`

`letter-spacing: 0.3em; text-transform: uppercase;`

`color: var(--gold); margin-bottom: 1.2rem;`

`}`

`.footer-links { list-style: none; }`

`.footer-links li { margin-bottom: 0.6rem; font-size: 0.85rem; }`

`.footer-links a { transition: color 0.2s; }`

`.footer-links a:hover { color: white; }`

`.footer-bottom {`

`max-width: 1100px; margin: 2rem auto 0;`

`display: flex; justify-content: space-between; flex-wrap: wrap;`

`gap: 1rem; font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.06em;`

`}`

`.footer-disclaimer { max-width: 480px; color: rgba(255,255,255,0.3); }`

`/* ════════════════════════════════════════════════════════════`

`RESPONSIVE`

`════════════════════════════════════════════════════════════ */`

`@media (max-width: 1100px) {`

`.characters-grid { grid-template-columns: repeat(3, 1fr); }`

`}`

`@media (max-width: 768px) {`

`nav { padding: 1rem 1.5rem; }`

`.nav-links, .nav-cta { display: none; }`

`.characters-grid { grid-template-columns: repeat(2, 1fr); gap: 1rem; }`

`.lightbox-outfits { grid-template-columns: repeat(2, 1fr); padding: 1.4rem; }`

`.lightbox-header { padding: 1.4rem 1.4rem 1rem; }`

`.lightbox-cta { padding: 1.2rem 1.4rem; }`

`.footer-inner { grid-template-columns: 1fr; gap: 2rem; }`

`}`

`@media (max-width: 480px) {`

`.characters-grid { grid-template-columns: repeat(2, 1fr); gap: 0.8rem; }`

`.lightbox-outfits { grid-template-columns: 1fr 1fr; gap: 0.8rem; padding: 1rem; }`

`}`

`</style>`

`</head>`

`<body>`

`<!-- ══ NAVIGATION ═══════════════════════════════════════════ -->`

`<nav id="nav">`

`<a href="index.html" class="nav-logo">`

`<span class="crown">♛</span> Sophia's Magical Princess Party`

`</a>`

`<ul class="nav-links">`

`<li><a href="index.html">Home</a></li>`

`<li><a href="characters.html">Characters</a></li>`

`<li><a href="index.html#pricing">Pricing</a></li>`

`<li><a href="index.html#testimonials">Reviews</a></li>`

`<li><a href="index.html#faq">FAQ</a></li>`

`</ul>`

`<a href="tel:xxxxxxxxxx" class="nav-cta">Book Now</a>`

`</nav>`

`<!-- ══ PAGE HERO ════════════════════════════════════════════ -->`

`<section class="page-hero">`

`<div class="page-hero-bg"></div>`

`<div class="hero-arc hero-arc-1"></div>`

`<div class="hero-arc hero-arc-2"></div>`

`<span class="page-hero-eyebrow">Meet the Magic Makers</span>`

`<h1 class="page-hero-title">Our <em>Enchanting</em> Cast of Characters</h1>`

`<p class="page-hero-sub">`

`From beloved fairy-tale heroines to K-Pop superstars — every character is brought to life by a trained, background-checked professional ready to make your child's celebration unforgettable.`

`</p>`

`</section>`

`<!-- ══ CHARACTERS SECTION ═══════════════════════════════════ -->`

`<section class="section" id="characters">`

`<div class="section-inner">`

`<span class="section-label reveal">23 Characters &amp; Growing</span>`

`<h2 class="section-heading reveal">Every Child Finds Their Favorite</h2>`

`<p class="section-body reveal">`

`Tap or click any character to explore their available outfits and alternate looks — including limited seasonal styles. Highlighted outfits indicate our most-requested appearances.`

`</p>`

`<!-- FILTER BAR -->`

`<div class="filter-bar reveal">`

`<button class="filter-btn active" data-filter="all">All Characters</button>`

`<button class="filter-btn" data-filter="princess">✦ Princesses</button>`

`<button class="filter-btn" data-filter="kpop">♪ K-Pop Stars</button>`

`<button class="filter-btn" data-filter="impersonator">★ Impersonators</button>`

`<button class="filter-btn" data-filter="has-variants">Multiple Outfits</button>`

`</div>`

`<!-- ══ CHARACTER GRID ══════════════════════════════════════`

`HOW TO ADD / UPDATE CHARACTERS:`

`Each .char-card has:`

`• data-category : "princess" | "kpop" | "impersonator"`

`• data-name : display name (also fed to lightbox)`

`• data-type : subtitle line under name in lightbox`

`• data-desc : short description shown in lightbox`

`• data-outfits : JSON array of outfit objects:`

`{ "label": "Classic Gown", "sub": "Signature Look",`

`"img": "https://i.ibb.co/XXXXX/filename.jpg",`

`"featured": true, "badge": "Most Popular" }`

`featured=true → gold-border highlight on that outfit thumb`

`badge → overrides the default "Most Popular" badge text`

`═════════════════════════════════════════════════════ -->`

`<div class="characters-grid" id="characters-grid">`

`<!-- ── CHARACTER 01 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Elara the Ice Queen"`

`data-type="Princess Character"`

`data-desc="Regal, powerful, and warm-hearted beneath her icy exterior — Elara captivates every crowd with her shimmering gown and signature snow magic."`

`data-outfits='[`

`{"label":"Classic Ice Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder1a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Winter Ball Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder1b.jpg"},`

`{"label":"Coronation Dress","sub":"Formal Edition","img":"https://i.ibb.co/placeholder1c.jpg"}`

`]'>`

`<!-- Replace the src below with your imgbb direct-link URL -->`

`<img class="char-photo" src="https://i.ibb.co/placeholder1a.jpg" alt="Elara the Ice Queen" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>❄️</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Elara the Ice Queen</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 02 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Aurora Rose"`

`data-type="Princess Character"`

`data-desc="The Sleeping Beauty herself, Aurora greets every child with grace, warmth, and a twirl that never gets old."`

`data-outfits='[`

`{"label":"Pink Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder2a.jpg","featured":true,"badge":"Most Requested"},`

`{"label":"Blue Gown","sub":"Classic Alternate","img":"https://i.ibb.co/placeholder2b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder2a.jpg" alt="Aurora Rose" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌹</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Aurora Rose</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 03 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Bella"`

`data-type="Princess Character"`

`data-desc="Bookish and bright, Bella shows every child that kindness and curiosity are a princess's greatest gifts."`

`data-outfits='[`

`{"label":"Golden Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder3a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Village Dress","sub":"Casual Edition","img":"https://i.ibb.co/placeholder3b.jpg"},`

`{"label":"Winter Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder3c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder3a.jpg" alt="Bella" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>📚</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Bella</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 04 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Cindy"`

`data-type="Princess Character"`

`data-desc="From glass slippers to the grandest ballroom — Cindy brings pure fairy-tale magic to every celebration."`

`data-outfits='[`

`{"label":"Silver Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder4a.jpg","featured":true,"badge":"Best Seller"},`

`{"label":"Maid Dress","sub":"Before the Ball","img":"https://i.ibb.co/placeholder4b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder4a.jpg" alt="Cindy" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>👠</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Cindy</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 05 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Arielle"`

`data-type="Princess Character"`

`data-desc="Part of your world or part of ours — Arielle's infectious joy and flaming red hair light up every party."`

`data-outfits='[`

`{"label":"Mermaid Tail Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder5a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Blue Dress","sub":"Land Edition","img":"https://i.ibb.co/placeholder5b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder5a.jpg" alt="Arielle" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🧜</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Arielle</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 06 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Jasmine"`

`data-type="Princess Character"`

`data-desc="A princess of the desert sands with a spirit as free as the wind — Jasmine inspires every young dreamer."`

`data-outfits='[`

`{"label":"Teal Harem Outfit","sub":"Signature Look","img":"https://i.ibb.co/placeholder6a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Pink Bridal Dress","sub":"Celebration Edition","img":"https://i.ibb.co/placeholder6b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder6a.jpg" alt="Jasmine" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌙</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Jasmine</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 07 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Rapunzel"`

`data-type="Princess Character"`

`data-desc="With hair for days and a heart full of wonder, Rapunzel turns every room into an adventure."`

`data-outfits='[`

`{"label":"Purple Tower Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder7a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Pink Bridal Gown","sub":"Wedding Edition","img":"https://i.ibb.co/placeholder7b.jpg"},`

`{"label":"Blue Travel Outfit","sub":"Adventure Edition","img":"https://i.ibb.co/placeholder7c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder7a.jpg" alt="Rapunzel" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌻</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Rapunzel</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 08 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Snow White"`

`data-type="Princess Character"`

`data-desc="The fairest of them all — Snow White's timeless charm and iconic look have delighted children for generations."`

`data-outfits='[`

`{"label":"Classic Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder8a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder8a.jpg" alt="Snow White" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🍎</span>Photo Coming Soon</div>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Snow White</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 09 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Tiana"`

`data-type="Princess Character"`

`data-desc="Hardworking, dream-chasing, and dazzling — Tiana proves that with dedication and a little magic, every wish can come true."`

`data-outfits='[`

`{"label":"Green Ballgown","sub":"Signature Look","img":"https://i.ibb.co/placeholder9a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Lily Pad Dress","sub":"Garden Party Edition","img":"https://i.ibb.co/placeholder9b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder9a.jpg" alt="Tiana" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🐸</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Tiana</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 10 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Moana"`

`data-type="Princess Character"`

`data-desc="Chosen by the ocean itself — Moana's spirit of adventure and love of the sea inspires every child to be brave."`

`data-outfits='[`

`{"label":"Island Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder10a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder10a.jpg" alt="Moana" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌊</span>Photo Coming Soon</div>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Moana</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 11 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Merida"`

`data-type="Princess Character"`

`data-desc="Wild, brave, and fiercely independent — Merida shows every child that true strength comes from within."`

`data-outfits='[`

`{"label":"Highland Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder11a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Tournament Gown","sub":"Royal Edition","img":"https://i.ibb.co/placeholder11b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder11a.jpg" alt="Merida" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🏹</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Merida</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 12 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Mulan"`

`data-type="Princess Character"`

`data-desc="Courageous beyond measure, Mulan embodies the spirit of perseverance and honor — a true heroine for every child."`

`data-outfits='[`

`{"label":"Imperial Hanfu","sub":"Signature Look","img":"https://i.ibb.co/placeholder12a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Warrior Armor","sub":"Battle Edition","img":"https://i.ibb.co/placeholder12b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder12a.jpg" alt="Mulan" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🏵️</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Mulan</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 13 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Raya"`

`data-type="Princess Character"`

`data-desc="The last dragon warrior — Raya's bold spirit and fearless heart make every party feel like an epic adventure."`

`data-outfits='[`

`{"label":"Warrior Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder13a.jpg","featured":true,"badge":"New Look"},`

`{"label":"Warrior Armor","sub":"Battle Edition","img":"https://i.ibb.co/placeholder13b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder13a.jpg" alt="Raya" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🐉</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Raya</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 14 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Mirabel"`

`data-type="Princess Character"`

`data-desc="Gifted with the magic of family, Mirabel's colorful spirit and infectious laugh fill every room with joy."`

`data-outfits='[`

`{"label":"Embroidered Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder14a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder14a.jpg" alt="Mirabel" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🦋</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Mirabel</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 15 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Asha"`

`data-type="Princess Character"`

`data-desc="A wisher of wishes and keeper of stars — Asha brings the newest chapter of fairy-tale magic to your celebration."`

`data-outfits='[`

`{"label":"Star Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder15a.jpg","featured":true,"badge":"New Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder15a.jpg" alt="Asha" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>⭐</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Asha</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 16 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Tinker Bell"`

`data-type="Princess Character"`

`data-desc="Tiny in stature, enormous in personality — Tinker Bell's pixie dust makes every celebration sparkle."`

`data-outfits='[`

`{"label":"Classic Petal Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder16a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Winter Fairy Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder16b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder16a.jpg" alt="Tinker Bell" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🧚</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Tinker Bell</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 17 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Luna Star"`

`data-type="K-Pop Star Character"`

`data-desc="Our debut K-Pop sensation — Luna brings high-energy choreography, dazzling stage looks, and interactive fan moments to every event."`

`data-outfits='[`

`{"label":"Holographic Stage Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder17a.jpg","featured":true,"badge":"Best Seller"},`

`{"label":"Pastel Idol Dress","sub":"Fan Meet Edition","img":"https://i.ibb.co/placeholder17b.jpg"},`

`{"label":"Black Comeback Outfit","sub":"Comeback Edition","img":"https://i.ibb.co/placeholder17c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder17a.jpg" alt="Luna Star" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎤</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Luna Star</span>`

`<span class="char-type">K-Pop Star · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 18 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Sora Shine"`

`data-type="K-Pop Star Character"`

`data-desc="Sora's effortless style and unforgettable dance routines turn any party into a sold-out stadium moment."`

`data-outfits='[`

`{"label":"Neon Pop Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder18a.jpg","featured":true,"badge":"Most Requested"},`

`{"label":"Retro Y2K Outfit","sub":"Throwback Edition","img":"https://i.ibb.co/placeholder18b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder18a.jpg" alt="Sora Shine" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>💫</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Sora Shine</span>`

`<span class="char-type">K-Pop Star · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 19 — IMPERSONATOR ─── -->`

`<div class="char-card reveal"`

`data-category="impersonator"`

`data-name="Pop Royalty"`

`data-type="Celebrity Impersonator"`

`data-desc="Our signature Pop Royalty impersonator channels the energy, fashion, and showmanship of today's biggest pop icons."`

`data-outfits='[`

`{"label":"Concert Stage Look","sub":"Signature Performance","img":"https://i.ibb.co/placeholder19a.jpg","featured":true,"badge":"Premium Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder19a.jpg" alt="Pop Royalty" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎶</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--imperson">Impersonator</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Pop Royalty</span>`

`<span class="char-type">Celebrity Impersonator</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 20 — IMPERSONATOR ─── -->`

`<div class="char-card reveal"`

`data-category="impersonator"`

`data-name="Diva Supreme"`

`data-type="Celebrity Impersonator"`

`data-desc="Channeling old-Hollywood glamour with a modern twist — Diva Supreme commands every room with presence and poise."`

`data-outfits='[`

`{"label":"Sequin Evening Gown","sub":"Signature Performance","img":"https://i.ibb.co/placeholder20a.jpg","featured":true,"badge":"Premium Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder20a.jpg" alt="Diva Supreme" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎭</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--imperson">Impersonator</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Diva Supreme</span>`

`<span class="char-type">Celebrity Impersonator</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 21 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Sofia the Brave"`

`data-type="Princess Character"`

`data-desc="A young princess who proves that bravery, kindness, and a little magic can change the world."`

`data-outfits='[`

`{"label":"Purple Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder21a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Adventure Tunic","sub":"Quest Edition","img":"https://i.ibb.co/placeholder21b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder21a.jpg" alt="Sofia the Brave" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>👑</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Sofia the Brave</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 22 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Elena of the Valley"`

`data-type="Princess Character"`

`data-desc="A princess inspired by a rich cultural heritage — Elena's warmth and wisdom make her an instant favorite."`

`data-outfits='[`

`{"label":"Red Royal Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder22a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Festival Dress","sub":"Celebration Edition","img":"https://i.ibb.co/placeholder22b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder22a.jpg" alt="Elena of the Valley" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌺</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Elena of the Valley</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 23 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Nova Beat"`

`data-type="K-Pop Star Character"`

`data-desc="The newest member of our K-Pop lineup — Nova's futuristic aesthetic and magnetic energy are already a hit with fans of all ages."`

`data-outfits='[`

`{"label":"Silver Future Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder23a.jpg","featured":true,"badge":"New Look"},`

`{"label":"Cosmic Gown","sub":"Galaxy Edition","img":"https://i.ibb.co/placeholder23b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder23a.jpg" alt="Nova Beat" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌌</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-badge char-badge--new" style="top:2.6rem;">New</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Nova Beat</span>`

`<span class="char-type">K-Pop Star · 2 Outfits Available</span>`

`</div>`

`</div>`

`</div><!-- /characters-grid -->`

`<!-- Legal disclaimer -->`

`<div class="char-disclaimer reveal">`

`✦ &nbsp;All characters are original creations inspired by beloved fairy tales, classic stories, and pop culture archetypes. Sophia's Magical Princess Party is a private company with no affiliation to any major entertainment studio, production company, or theme park. Any similarity to trademarked characters is purely coincidental.`

`</div>`

`</div><!-- /section-inner -->`

`</section>`

`<!-- ══ CTA BAND ══════════════════════════════════════════════ -->`

`<section class="cta-band" id="book">`

`<span class="section-label">Ready to Create Magic?</span>`

`<h2 class="section-heading">Book Your Character Today</h2>`

`<p>The most magical celebration your child has ever had is just one phone call away. We'd love to hear about your event!</p>`

`<a class="cta-phone-big" href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a>`

`<a href="tel:xxxxxxxxxx" class="btn-white">✦ &nbsp;Call to Book Now</a>`

`</section>`

`<!-- ══ FOOTER ════════════════════════════════════════════════ -->`

`<footer>`

`<div class="footer-inner">`

`<div>`

`<div class="footer-brand-name">✦ Sophia's Magical Princess Party</div>`

`<p class="footer-brand-tag">Bringing beloved heroine characters to life for children's celebrations across the South Houston area since 2017.</p>`

`</div>`

`<div>`

`<div class="footer-col-title">Navigate</div>`

`<ul class="footer-links">`

`<li><a href="index.html">Home</a></li>`

`<li><a href="characters.html">Characters</a></li>`

`<li><a href="index.html#pricing">Pricing</a></li>`

`<li><a href="index.html#testimonials">Reviews</a></li>`

`<li><a href="index.html#faq">FAQ</a></li>`

`</ul>`

`</div>`

`<div>`

`<div class="footer-col-title">Contact</div>`

`<ul class="footer-links">`

`<li><a href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a></li>`

`<li>South Houston, TX</li>`

`<li>Mon–Sat, 9am–7pm</li>`

`</ul>`

`</div>`

`</div>`

`<div class="footer-bottom">`

`<span>© 2025 Sophia's Magical Princess Party. All rights reserved.</span>`

`<span class="footer-disclaimer">We offer unique original characters inspired by classic stories and fables. We are a private company unaffiliated with any major production company or theme park. Any similarity to trademarked characters is coincidental.</span>`

`</div>`

`</footer>`

`<!-- ══ LIGHTBOX OVERLAY ══════════════════════════════════════`

`Injected dynamically via JS — no static HTML needed. -->`

`<div class="lightbox-overlay" id="lightbox-overlay" role="dialog" aria-modal="true" aria-label="Character outfit viewer">`

`<div class="lightbox" id="lightbox">`

`<div class="lightbox-header">`

`<div>`

`<div class="lightbox-char-name" id="lb-name"></div>`

`<div class="lightbox-char-type" id="lb-type"></div>`

`<div class="lightbox-char-desc" id="lb-desc"></div>`

`</div>`

`<button class="lightbox-close" id="lightbox-close" aria-label="Close">✕</button>`

`</div>`

`<div class="lightbox-outfits" id="lb-outfits"></div>`

`<div class="lightbox-cta">`

`<p class="lightbox-cta-text">Love what you see? <strong>Call to check availability and book!</strong></p>`

`<a href="tel:xxxxxxxxxx" class="btn-book-char">✦ &nbsp;Book This Character</a>`

`</div>`

`</div>`

`</div>`

`<script>`

`/* ════════════════════════════════════════════════════════════`

`NAV — scroll effect`

`════════════════════════════════════════════════════════════ */`

`const nav = document.getElementById('nav');`

`window.addEventListener('scroll', () => {`

`nav.classList.toggle('scrolled', window.scrollY > 60);`

`}, { passive: true });`

`/* ════════════════════════════════════════════════════════════`

`SCROLL REVEAL`

`════════════════════════════════════════════════════════════ */`

`const io = new IntersectionObserver((entries) => {`

`entries.forEach(e => {`

`if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }`

`});`

`}, { threshold: 0.10 });`

`document.querySelectorAll('.reveal').forEach(el => io.observe(el));`

`/* ════════════════════════════════════════════════════════════`

`FILTER BAR`

`Hides cards whose data-category doesn't match the active`

`filter. "has-variants" shows only cards with ≥ 2 outfits.`

`════════════════════════════════════════════════════════════ */`

`document.querySelectorAll('.filter-btn').forEach(btn => {`

`btn.addEventListener('click', () => {`

`document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));`

`btn.classList.add('active');`

`const filter = btn.dataset.filter;`

`document.querySelectorAll('.char-card').forEach(card => {`

`let show = false;`

`if (filter === 'all') {`

`show = true;`

`} else if (filter === 'has-variants') {`

`const outfits = JSON.parse(card.dataset.outfits || '[]');`

`show = outfits.length >= 2;`

`} else {`

`show = card.dataset.category === filter;`

`}`

`card.style.display = show ? '' : 'none';`

`});`

`});`

`});`

`/* ════════════════════════════════════════════════════════════`

`LIGHTBOX`

`─────────────────────────────────────────────────────────`

`IMGBB CDN OPTIMISATION:`

`imgbb direct image URLs follow the pattern:`

`https://i.ibb.co/{hash}/{filename}.{ext}`

`These are served from imgbb's global CDN edge nodes.`

`We request images at their native URL — no additional`

`query params are needed; imgbb handles caching headers.`

`For best performance, upload images at 800–1200px wide`

`(portrait 3:4 ratio recommended) — the thumbnails in the`

`lightbox render at ≈200–320px wide, so imgbb's CDN edge`

`cache will serve the same asset without re-fetching.`

`════════════════════════════════════════════════════════════ */`

`const overlay = document.getElementById('lightbox-overlay');`

`const lbName = document.getElementById('lb-name');`

`const lbType = document.getElementById('lb-type');`

`const lbDesc = document.getElementById('lb-desc');`

`const lbOutfits = document.getElementById('lb-outfits');`

`const lbClose = document.getElementById('lightbox-close');`

`function openLightbox(card) {`

`const name = card.dataset.name || '';`

`const type = card.dataset.type || '';`

`const desc = card.dataset.desc || '';`

`const outfits = JSON.parse(card.dataset.outfits || '[]');`

`lbName.textContent = name;`

`lbType.textContent = type;`

`lbDesc.textContent = desc;`

`/* build outfit thumbnails */`

`lbOutfits.innerHTML = outfits.map(o => {`

`const featClass = o.featured ? ' outfit--featured' : '';`

``const badgeAttr = o.badge ? ` data-badge="${o.badge}"` : '';``

`` return ` ``

`<div class="outfit-thumb${featClass}"${badgeAttr}>`

`<img`

`src="${o.img}"`

`alt="${o.label}"`

`loading="lazy"`

`onerror="this.style.display='none';this.nextElementSibling.style.display='flex'">`

`<div class="outfit-placeholder" style="display:none">`

`<span>👗</span>Photo Coming Soon`

`</div>`

`<div class="outfit-label">`

`${o.label}`

``${o.sub ? `<small>${o.sub}</small>` : ''}``

`</div>`

``</div>`;``

`}).join('');`

`overlay.classList.add('open');`

`document.body.style.overflow = 'hidden';`

`lbClose.focus();`

`}`

`function closeLightbox() {`

`overlay.classList.remove('open');`

`document.body.style.overflow = '';`

`}`

`/* open on card click / tap */`

`document.querySelectorAll('.char-card').forEach(card => {`

`card.addEventListener('click', () => openLightbox(card));`

`/* keyboard accessibility */`

`card.setAttribute('tabindex', '0');`

`card.setAttribute('role', 'button');`

``card.setAttribute('aria-label', `View outfits for ${card.dataset.name}`);``

`card.addEventListener('keydown', e => {`

`if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); openLightbox(card); }`

`});`

`});`

`/* close via button, overlay click, or Escape */`

`lbClose.addEventListener('click', closeLightbox);`

`overlay.addEventListener('click', e => { if (e.target === overlay) closeLightbox(); });`

`document.addEventListener('keydown', e => { if (e.key === 'Escape' && overlay.classList.contains('open')) closeLightbox(); });`

`</script>`

`</body>`

`</html>`# Claude

## Characters · HTML

`<!DOCTYPE html>`

`<html lang="en">`

`<head>`

`<meta charset="UTF-8" />`

`<meta name="viewport" content="width=device-width, initial-scale=1.0" />`

`<title>Our Characters — Sophia's Magical Princess Party</title>`

`<link rel="preconnect" href="https://fonts.googleapis.com" />`

`<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />`

`<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Cinzel:wght@400;500;600&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" />`

`<style>`

`/* ════════════════════════════════════════════════════════════`

`DESIGN TOKENS — matched exactly to SMPPv3.html`

`════════════════════════════════════════════════════════════ */`

`:root {`

`--gold: #C9A96E;`

`--gold-lt: #E8D5A3;`

`--rose: #D4768A;`

`--rose-lt: #F2C4CF;`

`--lavender: #A88EC0;`

`--sky: #7EB8D4;`

`--cream: #FAF6F0;`

`--ink: #1A1118;`

`--ink-soft: #3D2B3A;`

`--text: #4A3A46;`

`--ff-title: 'Cinzel', serif;`

`--ff-serif: 'Cormorant Garamond', serif;`

`--ff-sans: 'Jost', sans-serif;`

`--ease-silk: cubic-bezier(0.25, 0.46, 0.45, 0.94);`

`/* ── SALES HIGHLIGHT SYSTEM ────────────────────────────────`

`To mark an outfit as "featured" / drive sales, add the`

`class .outfit--featured to any .outfit-thumb element.`

`Swap out the color variables below to change the highlight`

`palette site-wide without touching individual cards. */`

`--highlight-border: #C9A96E; /* gold ring on card */`

`--highlight-badge-bg: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);`

`--highlight-badge-text: #fff;`

`--highlight-glow: rgba(201,169,110,0.28); /* card glow shadow */`

`}`

`/* ── RESET ──────────────────────────────────────────────── */`

`*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }`

`html { scroll-behavior: smooth; }`

`body {`

`background: var(--cream);`

`color: var(--text);`

`font-family: var(--ff-serif);`

`font-size: 18px;`

`line-height: 1.7;`

`overflow-x: hidden;`

`}`

`img { display: block; max-width: 100%; }`

`a { color: inherit; text-decoration: none; }`

`/* ── NAVIGATION (identical to template) ──────────────────── */`

`nav {`

`position: fixed; top: 0; left: 0; right: 0; z-index: 200;`

`display: flex; align-items: center; justify-content: space-between;`

`padding: 1.2rem 4rem;`

`background: transparent;`

`transition: background 0.4s var(--ease-silk), box-shadow 0.4s;`

`}`

`nav.scrolled {`

`background: rgba(250,246,240,0.96);`

`box-shadow: 0 1px 24px rgba(26,17,24,0.08);`

`backdrop-filter: blur(8px);`

`}`

`.nav-logo {`

`font-family: var(--ff-title); font-size: 1rem;`

`letter-spacing: 0.15em; color: var(--ink);`

`display: flex; align-items: center; gap: 0.6rem;`

`}`

`.nav-logo .crown { font-size: 1.2rem; }`

`.nav-links {`

`display: flex; gap: 2.4rem; list-style: none;`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 400;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`}`

`.nav-links a {`

`color: var(--ink-soft); position: relative; transition: color 0.25s;`

`}`

`.nav-links a::after {`

`content:''; position: absolute; left:0; bottom:-3px; width:0; height:1px;`

`background: var(--gold); transition: width 0.3s var(--ease-silk);`

`}`

`.nav-links a:hover { color: var(--gold); }`

`.nav-links a:hover::after { width: 100%; }`

`.nav-cta {`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`padding: 0.65rem 1.6rem;`

`border: 1px solid var(--gold); color: var(--gold);`

`transition: background 0.3s, color 0.3s; border-radius: 2px;`

`}`

`.nav-cta:hover { background: var(--gold); color: var(--cream); }`

`/* ── PAGE HERO ────────────────────────────────────────────── */`

`.page-hero {`

`position: relative;`

`min-height: 42vh;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`text-align: center;`

`padding: 10rem 2rem 5rem;`

`overflow: hidden;`

`}`

`.page-hero-bg {`

`position: absolute; inset: 0;`

`background:`

`radial-gradient(ellipse 80% 60% at 50% 0%, rgba(212,118,138,0.18) 0%, transparent 70%),`

`radial-gradient(ellipse 60% 70% at 15% 60%, rgba(168,142,192,0.14) 0%, transparent 65%),`

`radial-gradient(ellipse 55% 50% at 85% 55%, rgba(126,184,212,0.12) 0%, transparent 60%),`

`linear-gradient(175deg, #FDF9F4 0%, #F7EEF5 50%, #EFF3F9 100%);`

`}`

`.page-hero-bg::after {`

`content: '';`

`position: absolute; inset: 0;`

`background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");`

`opacity: 0.6;`

`}`

`/* decorative rings */`

`.hero-arc {`

`position: absolute; border-radius: 50%;`

`border: 1px solid rgba(201,169,110,0.22);`

`pointer-events: none;`

`}`

`.hero-arc-1 { width: 420px; height: 420px; top:50%; left:50%; transform:translate(-50%,-50%); }`

`.hero-arc-2 { width: 640px; height: 640px; top:50%; left:50%; transform:translate(-50%,-50%); }`

`.page-hero-eyebrow {`

`position: relative;`

`font-family: var(--ff-sans); font-size: 0.65rem; font-weight: 400;`

`letter-spacing: 0.35em; text-transform: uppercase;`

`color: var(--gold); margin-bottom: 1.4rem;`

`opacity: 0; animation: fadeUp 0.8s 0.2s var(--ease-silk) forwards;`

`}`

`.page-hero-title {`

`position: relative;`

`font-family: var(--ff-title);`

`font-size: clamp(2rem, 5vw, 4rem);`

`font-weight: 500; line-height: 1.12;`

`color: var(--ink); letter-spacing: 0.02em;`

`max-width: 760px;`

`opacity: 0; animation: fadeUp 0.9s 0.35s var(--ease-silk) forwards;`

`}`

`.page-hero-title em {`

`font-style: italic;`

`background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 50%, var(--sky) 100%);`

`-webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;`

`}`

`.page-hero-sub {`

`position: relative;`

`margin-top: 1.4rem;`

`font-family: var(--ff-serif); font-size: 1.15rem; font-weight: 300;`

`color: var(--text); max-width: 520px; line-height: 1.7;`

`opacity: 0; animation: fadeUp 0.9s 0.5s var(--ease-silk) forwards;`

`}`

`/* ── GOLD RULE DIVIDER ────────────────────────────────────── */`

`.gold-rule {`

`display: flex; align-items: center; gap: 1rem;`

`color: var(--gold); font-family: var(--ff-title); letter-spacing: 0.25em;`

`font-size: 0.6rem; text-transform: uppercase;`

`}`

`.gold-rule::before, .gold-rule::after {`

`content:''; flex:1; height:1px;`

`background: linear-gradient(90deg, transparent, var(--gold-lt), transparent);`

`}`

`/* ── SECTION WRAPPERS ─────────────────────────────────────── */`

`.section { padding: 7rem 2rem; }`

`.section-inner { max-width: 1200px; margin: 0 auto; }`

`.section-label {`

`font-family: var(--ff-sans); font-size: 0.6rem; letter-spacing: 0.35em;`

`text-transform: uppercase; color: var(--gold); margin-bottom: 1rem; display: block;`

`}`

`.section-heading {`

`font-family: var(--ff-title);`

`font-size: clamp(1.8rem, 4vw, 3rem);`

`font-weight: 500; line-height: 1.18;`

`color: var(--ink); letter-spacing: 0.02em;`

`}`

`.section-body {`

`font-size: 1.05rem; line-height: 1.8; color: var(--text);`

`max-width: 560px; margin-top: 1.2rem;`

`}`

`/* ── FILTER BAR ───────────────────────────────────────────── */`

`.filter-bar {`

`display: flex; flex-wrap: wrap; gap: 0.6rem;`

`margin-top: 2.8rem; margin-bottom: 3.5rem;`

`}`

`.filter-btn {`

`font-family: var(--ff-sans); font-size: 0.68rem; font-weight: 400;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`padding: 0.55rem 1.3rem;`

`border: 1px solid rgba(201,169,110,0.35);`

`background: white; color: var(--text); border-radius: 2px;`

`cursor: pointer;`

`transition: all 0.22s var(--ease-silk);`

`}`

`.filter-btn:hover { border-color: var(--rose); color: var(--rose); }`

`.filter-btn.active { background: var(--ink); border-color: var(--ink); color: white; }`

`/* ── CHARACTER GRID ───────────────────────────────────────── */`

`.characters-grid {`

`display: grid;`

`grid-template-columns: repeat(4, 1fr);`

`gap: 1.6rem;`

`}`

`/* ── CHARACTER CARD ───────────────────────────────────────── */`

`.char-card {`

`position: relative; border-radius: 4px; overflow: hidden;`

`aspect-ratio: 3/4;`

`background: #f0e8f0;`

`cursor: pointer;`

`box-shadow: 0 4px 16px rgba(26,17,24,0.08);`

`transition: transform 0.4s var(--ease-silk), box-shadow 0.4s;`

`}`

`.char-card:hover {`

`transform: translateY(-8px) scale(1.02);`

`box-shadow: 0 20px 56px rgba(26,17,24,0.15);`

`}`

`/* gradient overlay so text is always readable */`

`.char-card::before {`

`content:''; position: absolute; inset: 0; z-index: 1;`

`background: linear-gradient(0deg, rgba(26,17,24,0.72) 0%, rgba(26,17,24,0.08) 55%, transparent 100%);`

`transition: opacity 0.3s;`

`}`

`.char-card:hover::before { opacity: 0.85; }`

`/* character photo — filled from imgbb CDN */`

`.char-photo {`

`width: 100%; height: 100%; object-fit: cover;`

`object-position: top center;`

`transition: transform 0.6s var(--ease-silk);`

`}`

`.char-card:hover .char-photo { transform: scale(1.06); }`

`/* placeholder gradient when no image is set yet */`

`.char-placeholder {`

`position: absolute; inset: 0;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`gap: 0.5rem; color: rgba(60,40,60,0.35);`

`font-family: var(--ff-sans); font-size: 0.6rem;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`pointer-events: none;`

`}`

`.char-placeholder span { font-size: 2.4rem; }`

`/* card text info */`

`.char-info {`

`position: absolute; bottom: 0; left: 0; right: 0; z-index: 2;`

`padding: 1.4rem 1.2rem 1.2rem;`

`}`

`.char-name {`

`font-family: var(--ff-title); font-size: 0.98rem;`

`letter-spacing: 0.08em; color: white;`

`display: block; margin-bottom: 0.15rem;`

`}`

`.char-type {`

`font-family: var(--ff-sans); font-size: 0.62rem;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`color: rgba(255,255,255,0.65);`

`}`

`/* outfit count badge (bottom-right) */`

`.char-outfit-badge {`

`position: absolute; top: 0.8rem; right: 0.8rem; z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.58rem;`

`letter-spacing: 0.12em; text-transform: uppercase;`

`background: rgba(26,17,24,0.55);`

`color: rgba(255,255,255,0.85);`

`backdrop-filter: blur(4px);`

`border: 1px solid rgba(255,255,255,0.18);`

`border-radius: 2px; padding: 0.3rem 0.65rem;`

`transition: opacity 0.25s;`

`}`

`.char-card:hover .char-outfit-badge { opacity: 0; } /* hides on hover — lightbox cue shows */`

`/* "view outfits" hover cue */`

`.char-view-cue {`

`position: absolute; top: 50%; left: 50%; transform: translate(-50%, -40%);`

`z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.22em;`

`text-transform: uppercase; color: white;`

`display: flex; flex-direction: column; align-items: center; gap: 0.5rem;`

`opacity: 0;`

`transition: opacity 0.3s var(--ease-silk), transform 0.3s var(--ease-silk);`

`pointer-events: none;`

`}`

`.char-view-cue::before {`

`content: '✦'; font-size: 1.4rem; color: var(--gold-lt);`

`animation: pulse 2s infinite;`

`}`

`.char-card:hover .char-view-cue {`

`opacity: 1;`

`transform: translate(-50%, -50%);`

`}`

`/* ── "NEW" & CATEGORY LABEL BADGES ─────────────────────────── */`

`/* These are positioned top-left on the card */`

`.char-badge {`

`position: absolute; top: 0.8rem; left: 0.8rem; z-index: 3;`

`font-family: var(--ff-sans); font-size: 0.55rem;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`padding: 0.25rem 0.6rem; border-radius: 2px;`

`color: white;`

`}`

`.char-badge--new { background: var(--sky); }`

`.char-badge--kpop { background: var(--lavender); }`

`.char-badge--imperson { background: var(--rose); }`

`/* ════════════════════════════════════════════════════════════`

`LIGHTBOX SYSTEM`

`Opens when a character card is tapped/clicked.`

`Shows all outfit variants with labels.`

`════════════════════════════════════════════════════════════ */`

`.lightbox-overlay {`

`position: fixed; inset: 0; z-index: 900;`

`background: rgba(26,17,24,0.88);`

`backdrop-filter: blur(10px);`

`display: flex; align-items: center; justify-content: center;`

`padding: 1.5rem;`

`opacity: 0; pointer-events: none;`

`transition: opacity 0.35s var(--ease-silk);`

`}`

`.lightbox-overlay.open {`

`opacity: 1; pointer-events: all;`

`}`

`.lightbox {`

`background: var(--cream);`

`border-radius: 6px;`

`max-width: 1040px; width: 100%;`

`max-height: 90vh;`

`overflow-y: auto;`

`position: relative;`

`box-shadow: 0 32px 80px rgba(26,17,24,0.45);`

`transform: translateY(20px);`

`transition: transform 0.35s var(--ease-silk);`

`}`

`.lightbox-overlay.open .lightbox { transform: translateY(0); }`

`/* scrollbar styling */`

`.lightbox::-webkit-scrollbar { width: 4px; }`

`.lightbox::-webkit-scrollbar-track { background: transparent; }`

`.lightbox::-webkit-scrollbar-thumb { background: var(--gold-lt); border-radius: 4px; }`

`.lightbox-header {`

`display: flex; align-items: flex-start; justify-content: space-between;`

`padding: 2.2rem 2.4rem 1.4rem;`

`border-bottom: 1px solid rgba(201,169,110,0.22);`

`position: sticky; top: 0; background: var(--cream); z-index: 5;`

`}`

`.lightbox-char-name {`

`font-family: var(--ff-title); font-size: clamp(1.3rem, 3vw, 2rem);`

`letter-spacing: 0.06em; color: var(--ink);`

`}`

`.lightbox-char-type {`

`font-family: var(--ff-sans); font-size: 0.62rem;`

`letter-spacing: 0.25em; text-transform: uppercase;`

`color: var(--gold); margin-top: 0.3rem;`

`}`

`.lightbox-char-desc {`

`font-family: var(--ff-serif); font-size: 0.95rem; font-weight: 300;`

`color: var(--text); max-width: 480px; margin-top: 0.6rem; line-height: 1.65;`

`}`

`.lightbox-close {`

`width: 40px; height: 40px; flex-shrink: 0;`

`border: 1px solid rgba(201,169,110,0.35);`

`background: white; border-radius: 2px; cursor: pointer;`

`display: flex; align-items: center; justify-content: center;`

`font-size: 1.1rem; color: var(--ink-soft);`

`transition: background 0.2s, color 0.2s;`

`margin-left: 1.5rem; margin-top: 0.2rem;`

`}`

`.lightbox-close:hover { background: var(--ink); color: white; }`

`/* outfit grid inside lightbox */`

`.lightbox-outfits {`

`display: grid;`

`grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));`

`gap: 1.4rem;`

`padding: 2rem 2.4rem 2.4rem;`

`}`

`/* ── INDIVIDUAL OUTFIT THUMBNAIL ──────────────────────────── */`

`.outfit-thumb {`

`position: relative;`

`border-radius: 4px; overflow: hidden;`

`aspect-ratio: 3/4;`

`background: #f0e8f0;`

`cursor: default;`

`box-shadow: 0 3px 12px rgba(26,17,24,0.08);`

`border: 2px solid transparent;`

`transition: transform 0.3s var(--ease-silk), box-shadow 0.3s, border-color 0.3s;`

`}`

`.outfit-thumb:hover {`

`transform: translateY(-4px);`

`box-shadow: 0 12px 32px rgba(26,17,24,0.12);`

`}`

`.outfit-thumb img {`

`width: 100%; height: 100%;`

`object-fit: cover; object-position: top center;`

`}`

`.outfit-placeholder {`

`position: absolute; inset: 0;`

`display: flex; flex-direction: column;`

`align-items: center; justify-content: center;`

`gap: 0.4rem; color: rgba(60,40,60,0.3);`

`font-family: var(--ff-sans); font-size: 0.58rem;`

`letter-spacing: 0.18em; text-transform: uppercase;`

`}`

`.outfit-placeholder span { font-size: 2rem; }`

`/* outfit label bar at bottom of thumb */`

`.outfit-label {`

`position: absolute; bottom: 0; left: 0; right: 0;`

`padding: 0.7rem 0.8rem 0.65rem;`

`background: linear-gradient(0deg, rgba(26,17,24,0.82) 0%, transparent 100%);`

`font-family: var(--ff-title); font-size: 0.7rem;`

`letter-spacing: 0.07em; color: white;`

`text-align: center;`

`}`

`.outfit-label small {`

`display: block;`

`font-family: var(--ff-sans); font-size: 0.55rem;`

`letter-spacing: 0.15em; text-transform: uppercase;`

`color: rgba(255,255,255,0.6); margin-top: 0.1rem;`

`}`

`/* ════════════════════════════════════════════════════════════`

`FEATURED / SALES-HIGHLIGHT OUTFIT`

`─────────────────────────────────────────────────────────`

`Add class .outfit--featured to any .outfit-thumb to:`

`• Apply a gold border ring`

`• Show a "Most Popular" badge`

`• Add a subtle gold glow shadow`

`Change the badge text by setting data-badge="Your Label"`

`on the element (defaults to "Most Popular" if omitted).`

`════════════════════════════════════════════════════════════ */`

`.outfit--featured {`

`border-color: var(--highlight-border);`

`box-shadow:`

`0 3px 12px rgba(26,17,24,0.08),`

`0 0 0 1px var(--highlight-border),`

`0 8px 28px var(--highlight-glow);`

`}`

`.outfit--featured:hover {`

`box-shadow:`

`0 12px 32px rgba(26,17,24,0.13),`

`0 0 0 1px var(--highlight-border),`

`0 12px 36px var(--highlight-glow);`

`}`

`/* featured badge — pseudo-element driven, no extra HTML needed */`

`.outfit--featured::after {`

`content: attr(data-badge); /* reads data-badge="…" or falls back below */`

`position: absolute; top: 0.7rem; left: 0.7rem; z-index: 4;`

`font-family: var(--ff-sans); font-size: 0.52rem;`

`font-weight: 500; letter-spacing: 0.14em; text-transform: uppercase;`

`padding: 0.25rem 0.65rem;`

`background: var(--highlight-badge-bg);`

`color: var(--highlight-badge-text);`

`border-radius: 2px;`

`box-shadow: 0 2px 8px rgba(212,118,138,0.35);`

`}`

`/* fallback text when data-badge is empty or missing */`

`.outfit--featured:not([data-badge])::after,`

`.outfit--featured[data-badge=""]::after {`

`content: 'Most Popular';`

`}`

`/* ── LIGHTBOX CTA BAR ──────────────────────────────────────── */`

`.lightbox-cta {`

`border-top: 1px solid rgba(201,169,110,0.22);`

`padding: 1.6rem 2.4rem;`

`display: flex; align-items: center; justify-content: space-between;`

`flex-wrap: wrap; gap: 1rem;`

`background: white;`

`}`

`.lightbox-cta-text {`

`font-family: var(--ff-serif); font-size: 1.05rem; font-weight: 300;`

`color: var(--text);`

`}`

`.lightbox-cta-text strong {`

`font-weight: 500; color: var(--ink); font-style: italic;`

`}`

`.btn-book-char {`

`display: inline-flex; align-items: center; gap: 0.6rem;`

`font-family: var(--ff-sans); font-size: 0.72rem; font-weight: 500;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`padding: 0.9rem 2rem;`

`background: linear-gradient(135deg, var(--rose), var(--lavender));`

`color: white; border-radius: 2px;`

`transition: opacity 0.2s, transform 0.2s;`

`box-shadow: 0 4px 20px rgba(212,118,138,0.35);`

`white-space: nowrap;`

`}`

`.btn-book-char:hover { opacity: 0.88; transform: translateY(-2px); }`

`/* ── SCROLL REVEAL ────────────────────────────────────────── */`

`.reveal { opacity: 0; transform: translateY(22px); transition: opacity 0.7s var(--ease-silk), transform 0.7s var(--ease-silk); }`

`.reveal.visible { opacity: 1; transform: none; }`

`/* ── ANIMATIONS ───────────────────────────────────────────── */`

`@keyframes fadeUp {`

`to { opacity: 1; transform: translateY(0); }`

`}`

`@keyframes pulse {`

`0%, 100% { opacity: 1; transform: scale(1); }`

`50% { opacity: 0.6; transform: scale(1.15); }`

`}`

`/* ── SECTION DISCLAIMER ───────────────────────────────────── */`

`.char-disclaimer {`

`margin-top: 3.5rem;`

`padding: 1.4rem 2rem;`

`border: 1px solid rgba(201,169,110,0.25);`

`border-radius: 2px;`

`background: white;`

`font-family: var(--ff-sans); font-size: 0.7rem;`

`letter-spacing: 0.06em; color: var(--text);`

`line-height: 1.6;`

`}`

`/* ── CTA BAND ─────────────────────────────────────────────── */`

`.cta-band {`

`background: linear-gradient(135deg, var(--rose) 0%, var(--lavender) 100%);`

`padding: 6rem 2rem; text-align: center; position: relative; overflow: hidden;`

`}`

`.cta-band::before {`

`content:''; position: absolute; inset:0;`

`background: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.06'/%3E%3C/svg%3E");`

`opacity: 0.5;`

`}`

`.cta-band .section-label { color: rgba(255,255,255,0.75); position: relative; }`

`.cta-band .section-heading { color: white; position: relative; max-width: 640px; margin: 0.8rem auto 0; }`

`.cta-band p { position: relative; margin-top: 1.2rem; color: rgba(255,255,255,0.85); font-size: 1.05rem; }`

`.cta-phone-big {`

`display: block; position: relative;`

`font-family: var(--ff-title); font-size: clamp(2rem, 5vw, 3.5rem);`

`letter-spacing: 0.08em; color: white;`

`margin: 1.8rem auto 2rem;`

`}`

`.btn-white {`

`display: inline-flex; align-items: center; gap: 0.6rem; position: relative;`

`font-family: var(--ff-sans); font-size: 0.75rem; font-weight: 500;`

`letter-spacing: 0.2em; text-transform: uppercase;`

`padding: 1.1rem 2.6rem;`

`background: white; color: var(--rose); border-radius: 2px;`

`transition: background 0.3s, transform 0.2s;`

`box-shadow: 0 4px 24px rgba(26,17,24,0.2);`

`}`

`.btn-white:hover { background: var(--cream); transform: translateY(-2px); }`

`/* ── FOOTER ───────────────────────────────────────────────── */`

`footer {`

`background: var(--ink); color: rgba(255,255,255,0.6);`

`padding: 4rem 2rem 2rem;`

`}`

`.footer-inner {`

`max-width: 1100px; margin: 0 auto;`

`display: grid; grid-template-columns: 2fr 1fr 1fr;`

`gap: 3rem; padding-bottom: 3rem;`

`border-bottom: 1px solid rgba(255,255,255,0.08);`

`}`

`.footer-brand-name {`

`font-family: var(--ff-title); font-size: 1rem;`

`letter-spacing: 0.12em; color: white; margin-bottom: 1rem;`

`}`

`.footer-brand-tag { font-size: 0.85rem; line-height: 1.7; max-width: 300px; }`

`.footer-col-title {`

`font-family: var(--ff-sans); font-size: 0.6rem;`

`letter-spacing: 0.3em; text-transform: uppercase;`

`color: var(--gold); margin-bottom: 1.2rem;`

`}`

`.footer-links { list-style: none; }`

`.footer-links li { margin-bottom: 0.6rem; font-size: 0.85rem; }`

`.footer-links a { transition: color 0.2s; }`

`.footer-links a:hover { color: white; }`

`.footer-bottom {`

`max-width: 1100px; margin: 2rem auto 0;`

`display: flex; justify-content: space-between; flex-wrap: wrap;`

`gap: 1rem; font-family: var(--ff-sans); font-size: 0.65rem; letter-spacing: 0.06em;`

`}`

`.footer-disclaimer { max-width: 480px; color: rgba(255,255,255,0.3); }`

`/* ════════════════════════════════════════════════════════════`

`RESPONSIVE`

`════════════════════════════════════════════════════════════ */`

`@media (max-width: 1100px) {`

`.characters-grid { grid-template-columns: repeat(3, 1fr); }`

`}`

`@media (max-width: 768px) {`

`nav { padding: 1rem 1.5rem; }`

`.nav-links, .nav-cta { display: none; }`

`.characters-grid { grid-template-columns: repeat(2, 1fr); gap: 1rem; }`

`.lightbox-outfits { grid-template-columns: repeat(2, 1fr); padding: 1.4rem; }`

`.lightbox-header { padding: 1.4rem 1.4rem 1rem; }`

`.lightbox-cta { padding: 1.2rem 1.4rem; }`

`.footer-inner { grid-template-columns: 1fr; gap: 2rem; }`

`}`

`@media (max-width: 480px) {`

`.characters-grid { grid-template-columns: repeat(2, 1fr); gap: 0.8rem; }`

`.lightbox-outfits { grid-template-columns: 1fr 1fr; gap: 0.8rem; padding: 1rem; }`

`}`

`</style>`

`</head>`

`<body>`

`<!-- ══ NAVIGATION ═══════════════════════════════════════════ -->`

`<nav id="nav">`

`<a href="index.html" class="nav-logo">`

`<span class="crown">♛</span> Sophia's Magical Princess Party`

`</a>`

`<ul class="nav-links">`

`<li><a href="index.html">Home</a></li>`

`<li><a href="characters.html">Characters</a></li>`

`<li><a href="index.html#pricing">Pricing</a></li>`

`<li><a href="index.html#testimonials">Reviews</a></li>`

`<li><a href="index.html#faq">FAQ</a></li>`

`</ul>`

`<a href="tel:xxxxxxxxxx" class="nav-cta">Book Now</a>`

`</nav>`

`<!-- ══ PAGE HERO ════════════════════════════════════════════ -->`

`<section class="page-hero">`

`<div class="page-hero-bg"></div>`

`<div class="hero-arc hero-arc-1"></div>`

`<div class="hero-arc hero-arc-2"></div>`

`<span class="page-hero-eyebrow">Meet the Magic Makers</span>`

`<h1 class="page-hero-title">Our <em>Enchanting</em> Cast of Characters</h1>`

`<p class="page-hero-sub">`

`From beloved fairy-tale heroines to K-Pop superstars — every character is brought to life by a trained, background-checked professional ready to make your child's celebration unforgettable.`

`</p>`

`</section>`

`<!-- ══ CHARACTERS SECTION ═══════════════════════════════════ -->`

`<section class="section" id="characters">`

`<div class="section-inner">`

`<span class="section-label reveal">23 Characters &amp; Growing</span>`

`<h2 class="section-heading reveal">Every Child Finds Their Favorite</h2>`

`<p class="section-body reveal">`

`Tap or click any character to explore their available outfits and alternate looks — including limited seasonal styles. Highlighted outfits indicate our most-requested appearances.`

`</p>`

`<!-- FILTER BAR -->`

`<div class="filter-bar reveal">`

`<button class="filter-btn active" data-filter="all">All Characters</button>`

`<button class="filter-btn" data-filter="princess">✦ Princesses</button>`

`<button class="filter-btn" data-filter="kpop">♪ K-Pop Stars</button>`

`<button class="filter-btn" data-filter="impersonator">★ Impersonators</button>`

`<button class="filter-btn" data-filter="has-variants">Multiple Outfits</button>`

`</div>`

`<!-- ══ CHARACTER GRID ══════════════════════════════════════`

`HOW TO ADD / UPDATE CHARACTERS:`

`Each .char-card has:`

`• data-category : "princess" | "kpop" | "impersonator"`

`• data-name : display name (also fed to lightbox)`

`• data-type : subtitle line under name in lightbox`

`• data-desc : short description shown in lightbox`

`• data-outfits : JSON array of outfit objects:`

`{ "label": "Classic Gown", "sub": "Signature Look",`

`"img": "https://i.ibb.co/XXXXX/filename.jpg",`

`"featured": true, "badge": "Most Popular" }`

`featured=true → gold-border highlight on that outfit thumb`

`badge → overrides the default "Most Popular" badge text`

`═════════════════════════════════════════════════════ -->`

`<div class="characters-grid" id="characters-grid">`

`<!-- ── CHARACTER 01 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Elara the Ice Queen"`

`data-type="Princess Character"`

`data-desc="Regal, powerful, and warm-hearted beneath her icy exterior — Elara captivates every crowd with her shimmering gown and signature snow magic."`

`data-outfits='[`

`{"label":"Classic Ice Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder1a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Winter Ball Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder1b.jpg"},`

`{"label":"Coronation Dress","sub":"Formal Edition","img":"https://i.ibb.co/placeholder1c.jpg"}`

`]'>`

`<!-- Replace the src below with your imgbb direct-link URL -->`

`<img class="char-photo" src="https://i.ibb.co/placeholder1a.jpg" alt="Elara the Ice Queen" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>❄️</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Elara the Ice Queen</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 02 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Aurora Rose"`

`data-type="Princess Character"`

`data-desc="The Sleeping Beauty herself, Aurora greets every child with grace, warmth, and a twirl that never gets old."`

`data-outfits='[`

`{"label":"Pink Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder2a.jpg","featured":true,"badge":"Most Requested"},`

`{"label":"Blue Gown","sub":"Classic Alternate","img":"https://i.ibb.co/placeholder2b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder2a.jpg" alt="Aurora Rose" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌹</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Aurora Rose</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 03 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Bella"`

`data-type="Princess Character"`

`data-desc="Bookish and bright, Bella shows every child that kindness and curiosity are a princess's greatest gifts."`

`data-outfits='[`

`{"label":"Golden Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder3a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Village Dress","sub":"Casual Edition","img":"https://i.ibb.co/placeholder3b.jpg"},`

`{"label":"Winter Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder3c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder3a.jpg" alt="Bella" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>📚</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Bella</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 04 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Cindy"`

`data-type="Princess Character"`

`data-desc="From glass slippers to the grandest ballroom — Cindy brings pure fairy-tale magic to every celebration."`

`data-outfits='[`

`{"label":"Silver Ball Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder4a.jpg","featured":true,"badge":"Best Seller"},`

`{"label":"Maid Dress","sub":"Before the Ball","img":"https://i.ibb.co/placeholder4b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder4a.jpg" alt="Cindy" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>👠</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Cindy</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 05 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Arielle"`

`data-type="Princess Character"`

`data-desc="Part of your world or part of ours — Arielle's infectious joy and flaming red hair light up every party."`

`data-outfits='[`

`{"label":"Mermaid Tail Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder5a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Blue Dress","sub":"Land Edition","img":"https://i.ibb.co/placeholder5b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder5a.jpg" alt="Arielle" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🧜</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Arielle</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 06 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Jasmine"`

`data-type="Princess Character"`

`data-desc="A princess of the desert sands with a spirit as free as the wind — Jasmine inspires every young dreamer."`

`data-outfits='[`

`{"label":"Teal Harem Outfit","sub":"Signature Look","img":"https://i.ibb.co/placeholder6a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Pink Bridal Dress","sub":"Celebration Edition","img":"https://i.ibb.co/placeholder6b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder6a.jpg" alt="Jasmine" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌙</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Jasmine</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 07 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Rapunzel"`

`data-type="Princess Character"`

`data-desc="With hair for days and a heart full of wonder, Rapunzel turns every room into an adventure."`

`data-outfits='[`

`{"label":"Purple Tower Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder7a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Pink Bridal Gown","sub":"Wedding Edition","img":"https://i.ibb.co/placeholder7b.jpg"},`

`{"label":"Blue Travel Outfit","sub":"Adventure Edition","img":"https://i.ibb.co/placeholder7c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder7a.jpg" alt="Rapunzel" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌻</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Rapunzel</span>`

`<span class="char-type">Princess · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 08 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Snow White"`

`data-type="Princess Character"`

`data-desc="The fairest of them all — Snow White's timeless charm and iconic look have delighted children for generations."`

`data-outfits='[`

`{"label":"Classic Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder8a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder8a.jpg" alt="Snow White" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🍎</span>Photo Coming Soon</div>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Snow White</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 09 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Tiana"`

`data-type="Princess Character"`

`data-desc="Hardworking, dream-chasing, and dazzling — Tiana proves that with dedication and a little magic, every wish can come true."`

`data-outfits='[`

`{"label":"Green Ballgown","sub":"Signature Look","img":"https://i.ibb.co/placeholder9a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Lily Pad Dress","sub":"Garden Party Edition","img":"https://i.ibb.co/placeholder9b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder9a.jpg" alt="Tiana" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🐸</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Tiana</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 10 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Moana"`

`data-type="Princess Character"`

`data-desc="Chosen by the ocean itself — Moana's spirit of adventure and love of the sea inspires every child to be brave."`

`data-outfits='[`

`{"label":"Island Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder10a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder10a.jpg" alt="Moana" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌊</span>Photo Coming Soon</div>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Moana</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 11 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Merida"`

`data-type="Princess Character"`

`data-desc="Wild, brave, and fiercely independent — Merida shows every child that true strength comes from within."`

`data-outfits='[`

`{"label":"Highland Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder11a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Tournament Gown","sub":"Royal Edition","img":"https://i.ibb.co/placeholder11b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder11a.jpg" alt="Merida" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🏹</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Merida</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 12 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Mulan"`

`data-type="Princess Character"`

`data-desc="Courageous beyond measure, Mulan embodies the spirit of perseverance and honor — a true heroine for every child."`

`data-outfits='[`

`{"label":"Imperial Hanfu","sub":"Signature Look","img":"https://i.ibb.co/placeholder12a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Warrior Armor","sub":"Battle Edition","img":"https://i.ibb.co/placeholder12b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder12a.jpg" alt="Mulan" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🏵️</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Mulan</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 13 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Raya"`

`data-type="Princess Character"`

`data-desc="The last dragon warrior — Raya's bold spirit and fearless heart make every party feel like an epic adventure."`

`data-outfits='[`

`{"label":"Warrior Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder13a.jpg","featured":true,"badge":"New Look"},`

`{"label":"Warrior Armor","sub":"Battle Edition","img":"https://i.ibb.co/placeholder13b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder13a.jpg" alt="Raya" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🐉</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Raya</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 14 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Mirabel"`

`data-type="Princess Character"`

`data-desc="Gifted with the magic of family, Mirabel's colorful spirit and infectious laugh fill every room with joy."`

`data-outfits='[`

`{"label":"Embroidered Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder14a.jpg","featured":true,"badge":"Most Popular"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder14a.jpg" alt="Mirabel" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🦋</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Mirabel</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 15 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Asha"`

`data-type="Princess Character"`

`data-desc="A wisher of wishes and keeper of stars — Asha brings the newest chapter of fairy-tale magic to your celebration."`

`data-outfits='[`

`{"label":"Star Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder15a.jpg","featured":true,"badge":"New Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder15a.jpg" alt="Asha" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>⭐</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--new">New</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Asha</span>`

`<span class="char-type">Princess · 1 Signature Look</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 16 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Tinker Bell"`

`data-type="Princess Character"`

`data-desc="Tiny in stature, enormous in personality — Tinker Bell's pixie dust makes every celebration sparkle."`

`data-outfits='[`

`{"label":"Classic Petal Dress","sub":"Signature Look","img":"https://i.ibb.co/placeholder16a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Winter Fairy Gown","sub":"Holiday Special","img":"https://i.ibb.co/placeholder16b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder16a.jpg" alt="Tinker Bell" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🧚</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Tinker Bell</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 17 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Luna Star"`

`data-type="K-Pop Star Character"`

`data-desc="Our debut K-Pop sensation — Luna brings high-energy choreography, dazzling stage looks, and interactive fan moments to every event."`

`data-outfits='[`

`{"label":"Holographic Stage Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder17a.jpg","featured":true,"badge":"Best Seller"},`

`{"label":"Pastel Idol Dress","sub":"Fan Meet Edition","img":"https://i.ibb.co/placeholder17b.jpg"},`

`{"label":"Black Comeback Outfit","sub":"Comeback Edition","img":"https://i.ibb.co/placeholder17c.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder17a.jpg" alt="Luna Star" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎤</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-outfit-badge">3 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Luna Star</span>`

`<span class="char-type">K-Pop Star · 3 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 18 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Sora Shine"`

`data-type="K-Pop Star Character"`

`data-desc="Sora's effortless style and unforgettable dance routines turn any party into a sold-out stadium moment."`

`data-outfits='[`

`{"label":"Neon Pop Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder18a.jpg","featured":true,"badge":"Most Requested"},`

`{"label":"Retro Y2K Outfit","sub":"Throwback Edition","img":"https://i.ibb.co/placeholder18b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder18a.jpg" alt="Sora Shine" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>💫</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Sora Shine</span>`

`<span class="char-type">K-Pop Star · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 19 — IMPERSONATOR ─── -->`

`<div class="char-card reveal"`

`data-category="impersonator"`

`data-name="Pop Royalty"`

`data-type="Celebrity Impersonator"`

`data-desc="Our signature Pop Royalty impersonator channels the energy, fashion, and showmanship of today's biggest pop icons."`

`data-outfits='[`

`{"label":"Concert Stage Look","sub":"Signature Performance","img":"https://i.ibb.co/placeholder19a.jpg","featured":true,"badge":"Premium Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder19a.jpg" alt="Pop Royalty" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎶</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--imperson">Impersonator</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Pop Royalty</span>`

`<span class="char-type">Celebrity Impersonator</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 20 — IMPERSONATOR ─── -->`

`<div class="char-card reveal"`

`data-category="impersonator"`

`data-name="Diva Supreme"`

`data-type="Celebrity Impersonator"`

`data-desc="Channeling old-Hollywood glamour with a modern twist — Diva Supreme commands every room with presence and poise."`

`data-outfits='[`

`{"label":"Sequin Evening Gown","sub":"Signature Performance","img":"https://i.ibb.co/placeholder20a.jpg","featured":true,"badge":"Premium Look"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder20a.jpg" alt="Diva Supreme" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🎭</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--imperson">Impersonator</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Diva Supreme</span>`

`<span class="char-type">Celebrity Impersonator</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 21 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Sofia the Brave"`

`data-type="Princess Character"`

`data-desc="A young princess who proves that bravery, kindness, and a little magic can change the world."`

`data-outfits='[`

`{"label":"Purple Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder21a.jpg","featured":true,"badge":"Fan Favorite"},`

`{"label":"Adventure Tunic","sub":"Quest Edition","img":"https://i.ibb.co/placeholder21b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder21a.jpg" alt="Sofia the Brave" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>👑</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Sofia the Brave</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 22 ─── -->`

`<div class="char-card reveal"`

`data-category="princess"`

`data-name="Elena of the Valley"`

`data-type="Princess Character"`

`data-desc="A princess inspired by a rich cultural heritage — Elena's warmth and wisdom make her an instant favorite."`

`data-outfits='[`

`{"label":"Red Royal Gown","sub":"Signature Look","img":"https://i.ibb.co/placeholder22a.jpg","featured":true,"badge":"Most Popular"},`

`{"label":"Festival Dress","sub":"Celebration Edition","img":"https://i.ibb.co/placeholder22b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder22a.jpg" alt="Elena of the Valley" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌺</span>Photo Coming Soon</div>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Elena of the Valley</span>`

`<span class="char-type">Princess · 2 Outfits Available</span>`

`</div>`

`</div>`

`<!-- ── CHARACTER 23 — K-POP ─── -->`

`<div class="char-card reveal"`

`data-category="kpop"`

`data-name="Nova Beat"`

`data-type="K-Pop Star Character"`

`data-desc="The newest member of our K-Pop lineup — Nova's futuristic aesthetic and magnetic energy are already a hit with fans of all ages."`

`data-outfits='[`

`{"label":"Silver Future Suit","sub":"Signature Look","img":"https://i.ibb.co/placeholder23a.jpg","featured":true,"badge":"New Look"},`

`{"label":"Cosmic Gown","sub":"Galaxy Edition","img":"https://i.ibb.co/placeholder23b.jpg"}`

`]'>`

`<img class="char-photo" src="https://i.ibb.co/placeholder23a.jpg" alt="Nova Beat" loading="lazy" onerror="this.style.display='none'">`

`<div class="char-placeholder"><span>🌌</span>Photo Coming Soon</div>`

`<span class="char-badge char-badge--kpop">K-Pop</span>`

`<span class="char-badge char-badge--new" style="top:2.6rem;">New</span>`

`<span class="char-outfit-badge">2 Outfits</span>`

`<div class="char-view-cue">View Outfits</div>`

`<div class="char-info">`

`<span class="char-name">Nova Beat</span>`

`<span class="char-type">K-Pop Star · 2 Outfits Available</span>`

`</div>`

`</div>`

`</div><!-- /characters-grid -->`

`<!-- Legal disclaimer -->`

`<div class="char-disclaimer reveal">`

`✦ &nbsp;All characters are original creations inspired by beloved fairy tales, classic stories, and pop culture archetypes. Sophia's Magical Princess Party is a private company with no affiliation to any major entertainment studio, production company, or theme park. Any similarity to trademarked characters is purely coincidental.`

`</div>`

`</div><!-- /section-inner -->`

`</section>`

`<!-- ══ CTA BAND ══════════════════════════════════════════════ -->`

`<section class="cta-band" id="book">`

`<span class="section-label">Ready to Create Magic?</span>`

`<h2 class="section-heading">Book Your Character Today</h2>`

`<p>The most magical celebration your child has ever had is just one phone call away. We'd love to hear about your event!</p>`

`<a class="cta-phone-big" href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a>`

`<a href="tel:xxxxxxxxxx" class="btn-white">✦ &nbsp;Call to Book Now</a>`

`</section>`

`<!-- ══ FOOTER ════════════════════════════════════════════════ -->`

`<footer>`

`<div class="footer-inner">`

`<div>`

`<div class="footer-brand-name">✦ Sophia's Magical Princess Party</div>`

`<p class="footer-brand-tag">Bringing beloved heroine characters to life for children's celebrations across the South Houston area since 2017.</p>`

`</div>`

`<div>`

`<div class="footer-col-title">Navigate</div>`

`<ul class="footer-links">`

`<li><a href="index.html">Home</a></li>`

`<li><a href="characters.html">Characters</a></li>`

`<li><a href="index.html#pricing">Pricing</a></li>`

`<li><a href="index.html#testimonials">Reviews</a></li>`

`<li><a href="index.html#faq">FAQ</a></li>`

`</ul>`

`</div>`

`<div>`

`<div class="footer-col-title">Contact</div>`

`<ul class="footer-links">`

`<li><a href="tel:xxxxxxxxxx">(xxx) xxx-xxxx</a></li>`

`<li>South Houston, TX</li>`

`<li>Mon–Sat, 9am–7pm</li>`

`</ul>`

`</div>`

`</div>`

`<div class="footer-bottom">`

`<span>© 2025 Sophia's Magical Princess Party. All rights reserved.</span>`

`<span class="footer-disclaimer">We offer unique original characters inspired by classic stories and fables. We are a private company unaffiliated with any major production company or theme park. Any similarity to trademarked characters is coincidental.</span>`

`</div>`

`</footer>`

`<!-- ══ LIGHTBOX OVERLAY ══════════════════════════════════════`

`Injected dynamically via JS — no static HTML needed. -->`

`<div class="lightbox-overlay" id="lightbox-overlay" role="dialog" aria-modal="true" aria-label="Character outfit viewer">`

`<div class="lightbox" id="lightbox">`

`<div class="lightbox-header">`

`<div>`

`<div class="lightbox-char-name" id="lb-name"></div>`

`<div class="lightbox-char-type" id="lb-type"></div>`

`<div class="lightbox-char-desc" id="lb-desc"></div>`

`</div>`

`<button class="lightbox-close" id="lightbox-close" aria-label="Close">✕</button>`

`</div>`

`<div class="lightbox-outfits" id="lb-outfits"></div>`

`<div class="lightbox-cta">`

`<p class="lightbox-cta-text">Love what you see? <strong>Call to check availability and book!</strong></p>`

`<a href="tel:xxxxxxxxxx" class="btn-book-char">✦ &nbsp;Book This Character</a>`

`</div>`

`</div>`

`</div>`

`<script>`

`/* ════════════════════════════════════════════════════════════`

`NAV — scroll effect`

`════════════════════════════════════════════════════════════ */`

`const nav = document.getElementById('nav');`

`window.addEventListener('scroll', () => {`

`nav.classList.toggle('scrolled', window.scrollY > 60);`

`}, { passive: true });`

`/* ════════════════════════════════════════════════════════════`

`SCROLL REVEAL`

`════════════════════════════════════════════════════════════ */`

`const io = new IntersectionObserver((entries) => {`

`entries.forEach(e => {`

`if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }`

`});`

`}, { threshold: 0.10 });`

`document.querySelectorAll('.reveal').forEach(el => io.observe(el));`

`/* ════════════════════════════════════════════════════════════`

`FILTER BAR`

`Hides cards whose data-category doesn't match the active`

`filter. "has-variants" shows only cards with ≥ 2 outfits.`

`════════════════════════════════════════════════════════════ */`

`document.querySelectorAll('.filter-btn').forEach(btn => {`

`btn.addEventListener('click', () => {`

`document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));`

`btn.classList.add('active');`

`const filter = btn.dataset.filter;`

`document.querySelectorAll('.char-card').forEach(card => {`

`let show = false;`

`if (filter === 'all') {`

`show = true;`

`} else if (filter === 'has-variants') {`

`const outfits = JSON.parse(card.dataset.outfits || '[]');`

`show = outfits.length >= 2;`

`} else {`

`show = card.dataset.category === filter;`

`}`

`card.style.display = show ? '' : 'none';`

`});`

`});`

`});`

`/* ════════════════════════════════════════════════════════════`

`LIGHTBOX`

`─────────────────────────────────────────────────────────`

`IMGBB CDN OPTIMISATION:`

`imgbb direct image URLs follow the pattern:`

`https://i.ibb.co/{hash}/{filename}.{ext}`

`These are served from imgbb's global CDN edge nodes.`

`We request images at their native URL — no additional`

`query params are needed; imgbb handles caching headers.`

`For best performance, upload images at 800–1200px wide`

`(portrait 3:4 ratio recommended) — the thumbnails in the`

`lightbox render at ≈200–320px wide, so imgbb's CDN edge`

`cache will serve the same asset without re-fetching.`

`════════════════════════════════════════════════════════════ */`

`const overlay = document.getElementById('lightbox-overlay');`

`const lbName = document.getElementById('lb-name');`

`const lbType = document.getElementById('lb-type');`

`const lbDesc = document.getElementById('lb-desc');`

`const lbOutfits = document.getElementById('lb-outfits');`

`const lbClose = document.getElementById('lightbox-close');`

`function openLightbox(card) {`

`const name = card.dataset.name || '';`

`const type = card.dataset.type || '';`

`const desc = card.dataset.desc || '';`

`const outfits = JSON.parse(card.dataset.outfits || '[]');`

`lbName.textContent = name;`

`lbType.textContent = type;`

`lbDesc.textContent = desc;`

`/* build outfit thumbnails */`

`lbOutfits.innerHTML = outfits.map(o => {`

`const featClass = o.featured ? ' outfit--featured' : '';`

``const badgeAttr = o.badge ? ` data-badge="${o.badge}"` : '';``

`` return ` ``

`<div class="outfit-thumb${featClass}"${badgeAttr}>`

`<img`

`src="${o.img}"`

`alt="${o.label}"`

`loading="lazy"`

`onerror="this.style.display='none';this.nextElementSibling.style.display='flex'">`

`<div class="outfit-placeholder" style="display:none">`

`<span>👗</span>Photo Coming Soon`

`</div>`

`<div class="outfit-label">`

`${o.label}`

``${o.sub ? `<small>${o.sub}</small>` : ''}``

`</div>`

``</div>`;``

`}).join('');`

`overlay.classList.add('open');`

`document.body.style.overflow = 'hidden';`

`lbClose.focus();`

`}`

`function closeLightbox() {`

`overlay.classList.remove('open');`

`document.body.style.overflow = '';`

`}`

`/* open on card click / tap */`

`document.querySelectorAll('.char-card').forEach(card => {`

`card.addEventListener('click', () => openLightbox(card));`

`/* keyboard accessibility */`

`card.setAttribute('tabindex', '0');`

`card.setAttribute('role', 'button');`

``card.setAttribute('aria-label', `View outfits for ${card.dataset.name}`);``

`card.addEventListener('keydown', e => {`

`if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); openLightbox(card); }`

`});`

`});`

`/* close via button, overlay click, or Escape */`

`lbClose.addEventListener('click', closeLightbox);`

`overlay.addEventListener('click', e => { if (e.target === overlay) closeLightbox(); });`

`document.addEventListener('keydown', e => { if (e.key === 'Escape' && overlay.classList.contains('open')) closeLightbox(); });`

`</script>`

`</body>`

`</html>`
'''
