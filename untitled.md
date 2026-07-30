# JAPZ-Worship-Essentials<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
  <title>JAPZ Worship Essentials</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@500;600;700&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap"
    rel="stylesheet">
  <style>
    /* ============================= RESET & TOKENS ============================= */
    *,
    *::before,
    *::after {
      box-sizing: border-box;
    }

    :root {
      color-scheme: dark;
      --void: #07070a;
      --panel: #131318;
      --panel-2: #1b1b21;
      --panel-3: #221e22;
      --border: rgba(255, 255, 255, 0.07);
      --border-strong: rgba(255, 255, 255, 0.14);
      --red: #ff2743;
      --red-deep: #7a0f1f;
      --red-glow: #ff3b57;
      --amber: #ffb020;
      --green: #37e08c;
      --text: #f4f2f0;
      --text-muted: #9a98a1;
      --text-dim: #5c5a63;
      --font-display: 'Rajdhani', sans-serif;
      --font-body: 'Inter', sans-serif;
      --font-mono: 'JetBrains Mono', monospace;
      --grad-bg: radial-gradient(ellipse 1200px 700px at 15% -10%, rgba(122, 15, 31, 0.35), transparent 60%),
        radial-gradient(ellipse 900px 600px at 110% 10%, rgba(255, 39, 67, 0.12), transparent 55%),
        linear-gradient(160deg, #08080a 0%, #0d0709 45%, #150609 100%);
      --grad-accent: linear-gradient(135deg, #ff3b57 0%, #7a0f1f 100%);
      --grad-panel: linear-gradient(180deg, var(--panel-2) 0%, var(--panel) 100%);
    }

    html,
    body {
      height: 100%;
    }

    body {
      margin: 0;
      font-family: var(--font-body);
      background: var(--grad-bg);
      background-attachment: fixed;
      color: var(--text);
      -webkit-font-smoothing: antialiased;
      overflow-x: hidden;
    }

    h1,
    h2,
    h3,
    h4 {
      font-family: var(--font-display);
      margin: 0;
      letter-spacing: 0.03em;
    }

    button {
      font-family: var(--font-body);
      cursor: pointer;
    }

    input {
      font-family: var(--font-body);
    }

    ::selection {
      background: var(--red);
      color: #fff;
    }

    ::-webkit-scrollbar {
      width: 10px;
      height: 10px;
    }

    ::-webkit-scrollbar-track {
      background: var(--void);
    }

    ::-webkit-scrollbar-thumb {
      background: #2a2830;
      border-radius: 6px;
      border: 2px solid var(--void);
    }

    ::-webkit-scrollbar-thumb:hover {
      background: var(--red-deep);
    }

    :focus-visible {
      outline: 2px solid var(--red);
      outline-offset: 2px;
    }

    @media (prefers-reduced-motion: reduce) {
      * {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
      }
    }

    /* ============================= LOADING SCREEN ============================= */
    #loading-screen {
      position: fixed;
      inset: 0;
      z-index: 100;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: var(--grad-bg);
      transition: opacity 0.6s ease, visibility 0.6s;
    }

    #loading-screen.hide {
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
    }

    .brand-mark {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: clamp(28px, 6vw, 52px);
      letter-spacing: 0.08em;
      text-transform: uppercase;
      background: linear-gradient(135deg, #fff 0%, #ff8a97 40%, var(--red) 100%);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 0 40px rgba(255, 39, 67, 0.25);
    }

    .brand-sub {
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.35em;
      color: var(--text-muted);
      margin-top: 8px;
      text-transform: uppercase;
    }

    .eq-deco {
      display: flex;
      align-items: flex-end;
      gap: 5px;
      height: 34px;
      margin: 28px 0 22px;
    }

    .eq-deco span {
      width: 5px;
      border-radius: 2px;
      background: linear-gradient(180deg, var(--red-glow), var(--red-deep));
      animation: eqbounce 1.1s ease-in-out infinite;
    }

    .eq-deco span:nth-child(1) {
      height: 40%;
      animation-delay: 0s;
    }

    .eq-deco span:nth-child(2) {
      height: 80%;
      animation-delay: 0.12s;
    }

    .eq-deco span:nth-child(3) {
      height: 55%;
      animation-delay: 0.24s;
    }

    .eq-deco span:nth-child(4) {
      height: 95%;
      animation-delay: 0.36s;
    }

    .eq-deco span:nth-child(5) {
      height: 65%;
      animation-delay: 0.48s;
    }

    .eq-deco span:nth-child(6) {
      height: 35%;
      animation-delay: 0.6s;
    }

    @keyframes eqbounce {

      0%,
      100% {
        transform: scaleY(0.4);
      }

      50% {
        transform: scaleY(1);
      }
    }

    .loading-bar-track {
      width: min(360px, 80vw);
      height: 6px;
      border-radius: 4px;
      background: var(--panel);
      border: 1px solid var(--border);
      overflow: hidden;
      box-shadow: inset 0 1px 4px rgba(0, 0, 0, 0.6);
    }

    .loading-bar-fill {
      height: 100%;
      width: 0%;
      border-radius: 4px;
      background: var(--grad-accent);
      box-shadow: 0 0 12px rgba(255, 39, 67, 0.6);
      transition: width 0.18s ease-out;
    }

    .loading-meta {
      display: flex;
      justify-content: space-between;
      width: min(360px, 80vw);
      margin-top: 10px;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text-muted);
    }

    #loading-pct {
      color: var(--red-glow);
    }

    /* ============================= LOGIN / GATE SCREEN ============================= */
    #login-screen {
      position: fixed;
      inset: 0;
      z-index: 90;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--grad-bg);
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
      transition: opacity 0.6s ease, visibility 0.6s;
    }

    #login-screen.show {
      opacity: 1;
      visibility: visible;
      pointer-events: auto;
    }

    #login-screen.hide {
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
    }

    .login-card {
      position: relative;
      width: min(400px, 88vw);
      padding: 38px 34px 30px;
      background: var(--grad-panel);
      border: 1px solid var(--border-strong);
      border-radius: 16px;
      box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6), 0 0 0 1px rgba(255, 39, 67, 0.06);
      text-align: center;
    }

    .login-card::before {
      content: '';
      position: absolute;
      inset: -1px;
      border-radius: 16px;
      padding: 1px;
      background: linear-gradient(135deg, rgba(255, 39, 67, 0.5), transparent 40%, transparent 70%, rgba(255, 39, 67, 0.25));
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      pointer-events: none;
    }

    .login-tagline {
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.25em;
      color: var(--text-muted);
      margin-top: 10px;
      text-transform: uppercase;
    }

    .login-divider {
      height: 1px;
      background: var(--border);
      margin: 24px 0 20px;
    }

    .login-field {
      text-align: left;
      margin-bottom: 18px;
    }

    .login-field label {
      display: block;
      font-size: 11px;
      letter-spacing: 0.12em;
      color: var(--text-muted);
      margin-bottom: 7px;
      text-transform: uppercase;
      font-family: var(--font-mono);
    }

    .login-field input {
      width: 100%;
      padding: 12px 14px;
      border-radius: 8px;
      background: var(--void);
      border: 1px solid var(--border-strong);
      color: var(--text);
      font-size: 14px;
    }

    .login-field input:focus {
      border-color: var(--red);
    }

    .btn-primary {
      width: 100%;
      padding: 14px;
      border: none;
      border-radius: 9px;
      background: var(--grad-accent);
      color: #fff;
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 16px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      box-shadow: 0 8px 24px rgba(255, 39, 67, 0.35);
      transition: transform 0.15s ease, box-shadow 0.15s ease;
    }

    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 30px rgba(255, 39, 67, 0.5);
    }

    .btn-primary:active {
      transform: translateY(0px) scale(0.99);
    }

    .login-note {
      margin-top: 16px;
      font-size: 11.5px;
      color: var(--text-dim);
      line-height: 1.5;
    }

    /* ============================= APP SHELL ============================= */
    #app {
      display: none;
      min-height: 100vh;
      flex-direction: column;
    }

    #app.show {
      display: flex;
    }

    .app-header {
      position: sticky;
      top: 0;
      z-index: 40;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding: 14px 22px;
      background: rgba(10, 9, 11, 0.85);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
    }

    .header-left {
      display: flex;
      align-items: center;
      gap: 14px;
      min-width: 0;
    }

    .logo-block {
      display: flex;
      flex-direction: column;
      line-height: 1.1;
    }

    .logo-text {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 19px;
      letter-spacing: 0.04em;
      white-space: nowrap;
    }

    .logo-text .accent {
      color: var(--red);
    }

    .logo-sub {
      font-family: var(--font-mono);
      font-size: 9.5px;
      color: var(--text-dim);
      letter-spacing: 0.2em;
      white-space: nowrap;
    }

    #welcome-name {
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text-muted);
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .stop-all-btn {
      display: flex;
      align-items: center;
      gap: 7px;
      padding: 9px 14px;
      border-radius: 8px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      color: var(--text);
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .stop-all-btn:hover {
      border-color: var(--red);
      color: var(--red-glow);
    }

    .stop-dot {
      width: 8px;
      height: 8px;
      border-radius: 2px;
      background: var(--red);
      box-shadow: 0 0 6px var(--red-glow);
    }

    .main-nav {
      display: flex;
      gap: 6px;
      padding: 12px 22px 0;
      overflow-x: auto;
    }

    .nav-tab {
      padding: 10px 18px;
      border: 1px solid var(--border);
      border-bottom: none;
      border-radius: 9px 9px 0 0;
      background: var(--panel);
      color: var(--text-muted);
      font-family: var(--font-display);
      font-weight: 600;
      font-size: 14px;
      letter-spacing: 0.06em;
      white-space: nowrap;
    }

    .nav-tab.active {
      background: var(--grad-panel);
      color: var(--text);
      border-color: var(--border-strong);
      box-shadow: 0 -2px 0 var(--red) inset;
    }

    .nav-tab:hover:not(.active) {
      color: var(--text);
    }

    .app-main {
      flex: 1;
      padding: 22px;
      max-width: 1240px;
      margin: 0 auto;
      width: 100%;
    }

    .section {
      display: none;
      animation: fadein 0.35s ease;
    }

    .section.active {
      display: block;
    }

    @keyframes fadein {
      from {
        opacity: 0;
        transform: translateY(6px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .section-panel {
      background: var(--grad-panel);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 22px;
    }

    .section-heading {
      display: flex;
      align-items: baseline;
      justify-content: space-between;
      margin-bottom: 18px;
      flex-wrap: wrap;
      gap: 8px;
    }

    .section-title {
      font-size: 20px;
    }

    .section-hint {
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text-dim);
    }

    /* ============================= SOUND PADS ============================= */
    #sp-category-tabs {
      display: flex;
      gap: 8px;
      margin-bottom: 18px;
      flex-wrap: wrap;
    }

    .cat-tab {
      width: 38px;
      height: 38px;
      border-radius: 9px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      color: var(--text-muted);
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 15px;
    }

    .cat-tab.active {
      background: var(--grad-accent);
      color: #fff;
      border-color: transparent;
      box-shadow: 0 4px 14px rgba(255, 39, 67, 0.4);
    }

    #sp-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
      gap: 12px;
    }

    .pad {
      position: relative;
      aspect-ratio: 1/1;
      border-radius: 12px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 6px;
      padding: 10px;
      transition: transform 0.08s ease, box-shadow 0.15s ease, border-color 0.15s ease;
      overflow: hidden;
    }

    .pad::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(160deg, rgba(255, 255, 255, 0.04), transparent 40%);
      pointer-events: none;
    }

    .pad:hover {
      border-color: rgba(255, 39, 67, 0.4);
    }

    .pad:active {
      transform: scale(0.97);
    }

    .pad.playing {
      background: var(--grad-accent);
      border-color: transparent;
      box-shadow: 0 0 22px rgba(255, 39, 67, 0.55), 0 0 0 1px rgba(255, 255, 255, 0.08) inset;
    }

    .pad.empty {
      border-style: dashed;
      opacity: 0.75;
    }

    .pad.loading {
      opacity: 0.5;
      pointer-events: none;
    }

    .pad-name {
      font-family: var(--font-display);
      font-weight: 600;
      font-size: 13px;
      text-align: center;
      background: transparent;
      border: none;
      color: var(--text);
      width: 100%;
      outline: none;
      text-transform: uppercase;
      letter-spacing: 0.03em;
    }

    .pad.playing .pad-name {
      color: #fff;
    }

    .pad-icon {
      font-size: 16px;
      color: var(--text-dim);
    }

    .pad.playing .pad-icon {
      color: #fff;
    }

    .pad-file {
      font-family: var(--font-mono);
      font-size: 8.5px;
      color: var(--text-dim);
      max-width: 100%;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }

    .pad.playing .pad-file {
      color: rgba(255, 255, 255, 0.75);
    }

    .pad-mini-row {
      position: absolute;
      top: 6px;
      right: 6px;
      display: flex;
      gap: 4px;
    }

    .mini-btn {
      width: 20px;
      height: 20px;
      border-radius: 5px;
      background: rgba(0, 0, 0, 0.35);
      border: 1px solid rgba(255, 255, 255, 0.12);
      color: var(--text-muted);
      font-size: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      line-height: 1;
    }

    .mini-btn:hover {
      color: #fff;
      border-color: var(--red);
    }

    .mini-btn.on {
      background: var(--red);
      color: #fff;
      border-color: var(--red);
    }

    .add-pad-btn {
      aspect-ratio: 1/1;
      border-radius: 12px;
      background: transparent;
      border: 1px dashed var(--border-strong);
      color: var(--text-dim);
      font-family: var(--font-mono);
      font-size: 11px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .add-pad-btn:hover {
      border-color: var(--red);
      color: var(--red-glow);
    }

    /* ============================= SOUNDBOARD (DRUM PADS) ============================= */
    #db-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      max-width: 640px;
      margin: 0 auto;
    }

    .drum-pad {
      position: relative;
      aspect-ratio: 1/0.85;
      border-radius: 14px;
      background: linear-gradient(180deg, #232025, #151318);
      border: 1px solid var(--border-strong);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 6px;
      padding: 10px;
      box-shadow: 0 4px 0 rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255, 255, 255, 0.05);
      transition: transform 0.06s ease;
    }

    .drum-pad:active {
      transform: translateY(2px);
      box-shadow: 0 2px 0 rgba(0, 0, 0, 0.4);
    }

    .drum-pad.playing {
      background: var(--grad-accent);
      border-color: transparent;
      box-shadow: 0 0 26px rgba(255, 39, 67, 0.6);
    }

    .drum-pad.empty {
      opacity: 0.7;
      border-style: dashed;
    }

    .drum-pad-label {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 13px;
      text-transform: uppercase;
      text-align: center;
    }

    .drum-pad-file {
      font-family: var(--font-mono);
      font-size: 8px;
      color: var(--text-dim);
      max-width: 100%;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }

    .drum-pad.playing .drum-pad-file {
      color: rgba(255, 255, 255, 0.8);
    }

    .drum-pad-icon {
      font-size: 18px;
      color: var(--text-dim);
    }

    .drum-pad.playing .drum-pad-icon {
      color: #fff;
    }

    .drum-pad-edit {
      position: absolute;
      bottom: 7px;
      right: 7px;
      padding: 3px 8px;
      border-radius: 6px;
      font-family: var(--font-mono);
      font-size: 9px;
      letter-spacing: 0.06em;
      background: rgba(0, 0, 0, 0.4);
      border: 1px solid rgba(255, 255, 255, 0.14);
      color: var(--text-muted);
    }

    .drum-pad-edit:hover {
      color: #fff;
      border-color: var(--red);
    }

    .drum-pad-edit:disabled {
      opacity: 0.3;
      pointer-events: none;
    }

    /* ============================= LOOP SECTION ============================= */
    .loop-list {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .loop-row {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 12px 16px;
      border-radius: 12px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
    }

    .loop-row.playing {
      border-color: var(--red);
      box-shadow: 0 0 18px rgba(255, 39, 67, 0.25);
    }

    .loop-reel {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      flex-shrink: 0;
      background: radial-gradient(circle at center, var(--panel) 0 30%, #2b2830 31% 55%, var(--panel) 56% 100%);
      border: 1px solid var(--border-strong);
    }

    .loop-row.playing .loop-reel {
      animation: spin 1.6s linear infinite;
      border-color: var(--red);
    }

    @keyframes spin {
      to {
        transform: rotate(360deg);
      }
    }

    .loop-info {
      flex: 1;
      min-width: 0;
    }

    .loop-name {
      font-family: var(--font-display);
      font-weight: 600;
      font-size: 14px;
      background: transparent;
      border: none;
      color: var(--text);
      width: 100%;
      outline: none;
    }

    .loop-file {
      font-family: var(--font-mono);
      font-size: 10px;
      color: var(--text-dim);
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }

    .loop-controls {
      display: flex;
      align-items: center;
      gap: 8px;
      flex-shrink: 0;
    }

    .loop-play-btn {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      background: var(--panel);
      border: 1px solid var(--border-strong);
      color: var(--text);
      font-size: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .loop-row.playing .loop-play-btn {
      background: var(--grad-accent);
      border-color: transparent;
      color: #fff;
    }

    .loop-upload-btn {
      padding: 8px 12px;
      border-radius: 8px;
      background: var(--panel);
      border: 1px solid var(--border-strong);
      color: var(--text-muted);
      font-family: var(--font-mono);
      font-size: 10.5px;
    }

    .loop-upload-btn:hover {
      color: #fff;
      border-color: var(--red);
    }

    /* ============================= MODAL: DRUM EDITOR ============================= */
    .modal-overlay {
      position: fixed;
      inset: 0;
      z-index: 80;
      background: rgba(4, 3, 5, 0.72);
      backdrop-filter: blur(3px);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
      transition: opacity 0.25s ease, visibility 0.25s;
      padding: 16px;
    }

    .modal-overlay.show {
      opacity: 1;
      visibility: visible;
      pointer-events: auto;
    }

    .modal-panel {
      width: min(640px, 100%);
      max-height: 88vh;
      overflow-y: auto;
      background: var(--grad-panel);
      border: 1px solid var(--border-strong);
      border-radius: 16px;
      box-shadow: 0 30px 90px rgba(0, 0, 0, 0.7);
    }

    .modal-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 16px 20px;
      border-bottom: 1px solid var(--border);
    }

    .modal-name-input {
      background: transparent;
      border: none;
      color: var(--text);
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 17px;
      outline: none;
      text-transform: uppercase;
      letter-spacing: 0.03em;
      flex: 1;
    }

    #de-close {
      width: 30px;
      height: 30px;
      border-radius: 8px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      color: var(--text-muted);
    }

    #de-close:hover {
      color: #fff;
      border-color: var(--red);
    }

    .modal-body {
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    .waveform-wrap {
      position: relative;
      height: 120px;
      background: var(--void);
      border-radius: 10px;
      border: 1px solid var(--border-strong);
      overflow: hidden;
    }

    #de-waveform {
      width: 100%;
      height: 100%;
      display: block;
    }

    .trim-selection {
      position: absolute;
      top: 0;
      bottom: 0;
      background: rgba(255, 39, 67, 0.14);
      border-left: 1px solid rgba(255, 39, 67, 0.5);
      border-right: 1px solid rgba(255, 39, 67, 0.5);
      pointer-events: none;
    }

    .trim-handle {
      position: absolute;
      top: 0;
      bottom: 0;
      width: 12px;
      margin-left: -6px;
      cursor: ew-resize;
    }

    .trim-handle::after {
      content: '';
      position: absolute;
      top: 0;
      bottom: 0;
      left: 5px;
      width: 2px;
      background: var(--red);
      box-shadow: 0 0 6px var(--red-glow);
    }

    .trim-handle::before {
      content: '';
      position: absolute;
      top: 6px;
      left: 1px;
      width: 10px;
      height: 10px;
      border-radius: 3px;
      background: var(--red);
      box-shadow: 0 0 6px var(--red-glow);
    }

    .time-readout {
      display: flex;
      gap: 20px;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text-muted);
      flex-wrap: wrap;
    }

    .time-readout b {
      color: var(--text);
      font-weight: 500;
    }

    .editor-transport {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    }

    .editor-transport button {
      padding: 9px 14px;
      border-radius: 8px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      color: var(--text);
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.05em;
    }

    .editor-transport button:hover {
      border-color: var(--red);
      color: var(--red-glow);
    }

    #de-play {
      background: var(--grad-accent);
      border-color: transparent;
      color: #fff;
    }

    .editor-controls-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 16px;
    }

    .control-block label {
      display: block;
      font-family: var(--font-mono);
      font-size: 10px;
      letter-spacing: 0.1em;
      color: var(--text-dim);
      margin-bottom: 8px;
      text-transform: uppercase;
    }

    .control-block input[type=range] {
      width: 100%;
    }

    .control-block span {
      display: block;
      margin-top: 4px;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--red-glow);
    }

    .eq-section .eq-title {
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.15em;
      color: var(--text-dim);
      margin-bottom: 12px;
      text-transform: uppercase;
    }

    .eq-knobs {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
      justify-content: space-between;
    }

    /* generic range input styling */
    input[type=range] {
      -webkit-appearance: none;
      height: 4px;
      background: var(--panel);
      border-radius: 3px;
    }

    input[type=range]::-webkit-slider-runnable-track {
      height: 4px;
      border-radius: 3px;
      background: linear-gradient(90deg, var(--red-deep), var(--red));
    }

    input[type=range]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 15px;
      height: 15px;
      border-radius: 50%;
      background: #fff;
      border: 2px solid var(--red);
      margin-top: -5.5px;
      box-shadow: 0 0 6px rgba(255, 39, 67, 0.6);
    }

    input[type=range]::-moz-range-track {
      height: 4px;
      border-radius: 3px;
      background: linear-gradient(90deg, var(--red-deep), var(--red));
    }

    input[type=range]::-moz-range-thumb {
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: #fff;
      border: 2px solid var(--red);
    }

    /* ============================= KNOB COMPONENT ============================= */
    .knob {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      width: 62px;
      user-select: none;
    }

    .knob-dial {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      position: relative;
      cursor: ns-resize;
      background: radial-gradient(circle at 35% 30%, #2c2a31, #131318 72%);
      border: 1px solid var(--border-strong);
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.6), inset 0 0 8px rgba(0, 0, 0, 0.55);
    }

    .knob-dial.active {
      box-shadow: 0 0 0 3px rgba(255, 39, 67, 0.3), inset 0 0 8px rgba(0, 0, 0, 0.55);
    }

    .knob-indicator {
      position: absolute;
      top: 4px;
      left: 50%;
      width: 2px;
      height: 15px;
      background: var(--red);
      border-radius: 2px;
      transform-origin: 50% 18px;
      transform: translateX(-50%) rotate(0deg);
      box-shadow: 0 0 5px var(--red-glow);
    }

    .knob-label {
      font-family: var(--font-mono);
      font-size: 8.5px;
      color: var(--text-dim);
      letter-spacing: 0.04em;
      text-align: center;
      white-space: nowrap;
    }

    .knob-value {
      font-family: var(--font-mono);
      font-size: 10px;
      color: var(--text-muted);
    }

    /* ============================= MIX SECTION ============================= */
    .mix-strips {
      display: flex;
      gap: 20px;
      overflow-x: auto;
      padding: 6px 2px 14px;
    }

    .mix-strip {
      flex: 0 0 168px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 14px;
      background: var(--panel-2);
      border: 1px solid var(--border-strong);
      border-radius: 14px;
      padding: 16px 12px;
    }

    .mix-strip.master-strip {
      background: linear-gradient(180deg, #241318, #161014);
      border-color: rgba(255, 39, 67, 0.3);
    }

    .strip-label {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 13px;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      text-align: center;
    }

    .strip-eq {
      display: flex;
      flex-wrap: wrap;
      gap: 10px 8px;
      justify-content: center;
    }

    .strip-reverb {
      display: flex;
      justify-content: center;
    }

    .fader-wrap {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
    }

    .fader-db {
      font-family: var(--font-mono);
      font-size: 10.5px;
      color: var(--red-glow);
    }

    .fader-track {
      position: relative;
      width: 52px;
      height: 150px;
      border-radius: 6px;
      background: linear-gradient(180deg, #0c0c10, #1a1a20);
      border: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .fader-input {
      width: 130px;
      transform: rotate(-90deg);
      background: transparent;
    }

    .fader-input::-webkit-slider-runnable-track {
      height: 4px;
      background: linear-gradient(90deg, var(--panel), var(--red-deep), var(--red));
      border-radius: 2px;
    }

    .fader-input::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 32px;
      height: 16px;
      border-radius: 4px;
      background: linear-gradient(180deg, #3d3a42, #131114);
      border: 1px solid var(--red);
      margin-top: -6px;
      box-shadow: 0 0 6px rgba(255, 39, 67, 0.5);
    }

    .fader-input::-moz-range-thumb {
      width: 32px;
      height: 16px;
      border-radius: 4px;
      background: linear-gradient(180deg, #3d3a42, #131114);
      border: 1px solid var(--red);
    }

    .meter {
      display: flex;
      flex-direction: column-reverse;
      gap: 2px;
      height: 80px;
      width: 20px;
    }

    .meter-seg {
      flex: 1;
      border-radius: 2px;
      background: #1c1a1f;
    }

    .meter-seg.lit.seg-green {
      background: var(--green);
      box-shadow: 0 0 5px rgba(55, 224, 140, 0.6);
    }

    .meter-seg.lit.seg-amber {
      background: var(--amber);
      box-shadow: 0 0 5px rgba(255, 176, 32, 0.6);
    }

    .meter-seg.lit.seg-red {
      background: var(--red);
      box-shadow: 0 0 6px var(--red-glow);
    }

    .meter-row {
      display: flex;
      align-items: flex-end;
      gap: 8px;
    }

    .strip-buttons {
      display: flex;
      gap: 6px;
    }

    .mute-btn,
    .solo-btn {
      padding: 6px 10px;
      border-radius: 6px;
      font-family: var(--font-mono);
      font-size: 9.5px;
      letter-spacing: 0.06em;
      background: var(--panel);
      border: 1px solid var(--border-strong);
      color: var(--text-dim);
    }

    .mute-btn.on {
      background: var(--red);
      border-color: var(--red);
      color: #fff;
    }

    .solo-btn.on {
      background: var(--amber);
      border-color: var(--amber);
      color: #141014;
    }

    /* ============================= EMPTY / UPLOAD HINT ============================= */
    .upload-plus {
      font-size: 20px;
      color: var(--text-dim);
    }

    .app-footer {
      text-align: center;
      padding: 20px;
      font-family: var(--font-mono);
      font-size: 10.5px;
      color: var(--text-dim);
    }

    /* ============================= RESPONSIVE ============================= */
    @media (max-width:640px) {
      #db-grid {
        grid-template-columns: repeat(2, 1fr);
        max-width: 340px;
      }

      .app-header {
        padding: 12px 14px;
      }

      .app-main {
        padding: 14px;
      }

      .section-panel {
        padding: 16px;
      }

      .logo-sub {
        display: none;
      }

      .loop-row {
        flex-wrap: wrap;
      }
    }
  </style>
</head>

<body>

  <!-- ============================= LOADING SCREEN ============================= -->
  <div id="loading-screen">
    <div class="brand-mark">JAPZ Worship Essentials</div>
    <div class="brand-sub">Live Performance Pad Engine</div>
    <div class="eq-deco"><span></span><span></span><span></span><span></span><span></span><span></span></div>
    <div class="loading-bar-track">
      <div class="loading-bar-fill" id="loading-bar-fill"></div>
    </div>
    <div class="loading-meta">
      <span id="loading-msg">Warming up the pad engine…</span>
      <span id="loading-pct">0%</span>
    </div>
  </div>

  <!-- ============================= LOGIN / GATE SCREEN ============================= -->
  <div id="login-screen">
    <div class="login-card">
      <div class="brand-mark" style="font-size:24px;">JAPZ Worship Essentials</div>
      <div class="login-tagline">Studio Access</div>
      <div class="login-divider"></div>
      <div class="login-field">
        <label for="user-name-input">Your Name (optional)</label>
        <input type="text" id="user-name-input" placeholder="e.g. Japz" autocomplete="off">
      </div>
      <button class="btn-primary" id="enter-btn">Enter Studio</button>
      <div class="login-note">Everything runs locally in this browser tab. Your audio files are never uploaded to a
        server, and nothing is saved once you close or refresh the page.</div>
    </div>
  </div>

  <!-- ============================= MAIN APP ============================= -->
  <div id="app">
    <header class="app-header">
      <div class="header-left">
        <div class="logo-block">
          <div class="logo-text">JAPZ<span class="accent">.</span>Worship Essentials</div>
          <div class="logo-sub">Sound Pads · Soundboard · Loops · Mix</div>
        </div>
        <span id="welcome-name"></span>
      </div>
      <div class="header-right">
        <button class="stop-all-btn" id="stop-all-btn"><span class="stop-dot"></span> Stop All</button>
      </div>
    </header>

    <nav class="main-nav" id="main-nav">
      <button class="nav-tab active" data-tab="soundpads">Sound Pads</button>
      <button class="nav-tab" data-tab="soundboard">Soundboard</button>
      <button class="nav-tab" data-tab="loops">Loops</button>
      <button class="nav-tab" data-tab="mix">Mix</button>
    </nav>

    <main class="app-main">

      <!-- SOUND PADS SECTION -->
      <section class="section active" id="section-soundpads">
        <div class="section-panel">
          <div class="section-heading">
            <h2 class="section-title">Sound Pads</h2>
            <span class="section-hint">Tap a category, upload a sound, tap again to play / stop</span>
          </div>
          <div id="sp-category-tabs"></div>
          <div id="sp-grid"></div>
        </div>
      </section>

      <!-- SOUNDBOARD SECTION -->
      <section class="section" id="section-soundboard">
        <div class="section-panel">
          <div class="section-heading">
            <h2 class="section-title">Soundboard</h2>
            <span class="section-hint">12 drum pads · tap EDIT to trim, boost, fade or EQ each hit</span>
          </div>
          <div id="db-grid"></div>
        </div>
      </section>

      <!-- LOOPS SECTION -->
      <section class="section" id="section-loops">
        <div class="section-panel">
          <div class="section-heading">
            <h2 class="section-title">Loops</h2>
            <span class="section-hint">Loops keep playing under your pads and soundboard</span>
          </div>
          <div class="loop-list" id="loop-list"></div>
        </div>
      </section>

      <!-- MIX SECTION -->
      <section class="section" id="section-mix">
        <div class="section-panel">
          <div class="section-heading">
            <h2 class="section-title">Mix</h2>
            <span class="section-hint">Master volume, parametric EQ &amp; reverb per channel</span>
          </div>
          <div class="mix-strips" id="mix-strips"></div>
        </div>
      </section>

    </main>

    <div class="app-footer">JAPZ Worship Essentials — runs entirely in your browser</div>
  </div>

  <!-- ============================= DRUM PAD EDITOR MODAL ============================= -->
  <div class="modal-overlay" id="drum-editor-modal">
    <div class="modal-panel">
      <div class="modal-header">
        <input type="text" id="de-name" class="modal-name-input" value="PAD">
        <button id="de-close">✕</button>
      </div>
      <div class="modal-body">
        <div class="waveform-wrap" id="de-waveform-wrap">
          <canvas id="de-waveform"></canvas>
          <div class="trim-selection" id="de-selection"></div>
          <div class="trim-handle" id="de-handle-start"></div>
          <div class="trim-handle" id="de-handle-end"></div>
        </div>
        <div class="time-readout">
          <span>Start <b id="de-start-time">0.00s</b></span>
          <span>End <b id="de-end-time">0.00s</b></span>
          <span>Length <b id="de-length-time">0.00s</b></span>
        </div>
        <div class="editor-transport">
          <button id="de-play">▶ Preview</button>
          <button id="de-stop">■ Stop</button>
          <button id="de-reset">Reset Edits</button>
          <button id="de-replace">Replace Sound</button>
        </div>
        <div class="editor-controls-grid">
          <div class="control-block">
            <label>Loudness</label>
            <input type="range" id="de-gain" min="0" max="300" value="100">
            <span id="de-gain-val">100%</span>
          </div>
          <div class="control-block">
            <label>Fade In</label>
            <input type="range" id="de-fadein" min="0" max="2000" value="0">
            <span id="de-fadein-val">0.00s</span>
          </div>
          <div class="control-block">
            <label>Fade Out</label>
            <input type="range" id="de-fadeout" min="0" max="2000" value="0">
            <span id="de-fadeout-val">0.00s</span>
          </div>
        </div>
        <div class="eq-section">
          <div class="eq-title">Parametric EQ</div>
          <div class="eq-knobs" id="de-eq-knobs"></div>
        </div>
      </div>
    </div>
  </div>

  <script>
    (function () {
      "use strict";

      /* ============================================================
         HELPERS
      ============================================================ */
      function el(tag, props, children) {
        props = props || {};
        const e = document.createElement(tag);
        Object.keys(props).forEach(function (k) {
          const v = props[k];
          if (k === 'class') e.className = v;
          else if (k === 'text') e.textContent = v;
          else if (k === 'html') e.innerHTML = v;
          else if (k.indexOf('on') === 0 && typeof v === 'function') e.addEventListener(k.slice(2).toLowerCase(), v);
          else e.setAttribute(k, v);
        });
        (children || []).forEach(function (c) {
          if (c == null) return;
          e.appendChild(typeof c === 'string' ? document.createTextNode(c) : c);
        });
        return e;
      }
      function clamp(v, min, max) { return Math.min(max, Math.max(min, v)); }
      function fmtTime(s) { if (!isFinite(s)) s = 0; return s.toFixed(2) + 's'; }
      function gainToDbLabel(v) {
        if (v <= 0.0005) return '-\u221E dB';
        const db = 20 * Math.log10(v);
        return (db > 0 ? '+' : '') + db.toFixed(1) + ' dB';
      }
      let uidCounter = 0;
      function uid(prefix) { uidCounter += 1; return prefix + '-' + uidCounter; }

      /* ============================================================
         GLOBAL STATE
      ============================================================ */
      const SOUND_CATEGORIES = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
      const DRUM_PAD_COUNT = 12;
      const LOOP_SLOT_COUNT = 6;

      let ctx = null;
      let masterBus = null;
      let cachedImpulse = null;
      let soloedChannel = null;
      let currentEditingPad = null;

      const state = {
        channels: {},          // soundpad / soundboard / loop bus chains
        soundPads: {},          // letter -> [padObj]
        drumPads: [],
        loopPads: []
      };

      let activeSPCategory = 'A';

      /* ============================================================
         PAD FACTORIES
      ============================================================ */
      function makeSoundPad(letter, idx) {
        return {
          id: uid('sp'), category: letter, name: letter + (idx + 1),
          buffer: null, fileName: '', loopEnabled: false,
          isPlaying: false, loading: false, source: null, el: null
        };
      }
      function makeDrumPad(i) {
        return {
          id: uid('dp'), name: 'PAD ' + (i + 1),
          buffer: null, originalBuffer: null, fileName: '',
          trimStart: 0, trimEnd: 0, gain: 1, fadeIn: 0, fadeOut: 0,
          eq: { lowFreq: 150, lowGain: 0, midFreq: 1000, midGain: 0, highFreq: 6000, highGain: 0 },
          isPlaying: false, loading: false, source: null, el: null
        };
      }
      function makeLoopPad(i) {
        return {
          id: uid('lp'), name: 'LOOP ' + (i + 1),
          buffer: null, fileName: '', loopEnabled: true,
          isPlaying: false, loading: false, source: null, el: null
        };
      }

      SOUND_CATEGORIES.forEach(function (letter) {
        state.soundPads[letter] = [];
        for (let i = 0; i < 6; i++) state.soundPads[letter].push(makeSoundPad(letter, i));
      });
      state.drumPads = Array.from({ length: DRUM_PAD_COUNT }, function (_, i) { return makeDrumPad(i); });
      state.loopPads = Array.from({ length: LOOP_SLOT_COUNT }, function (_, i) { return makeLoopPad(i); });

      /* ============================================================
         AUDIO ENGINE
      ============================================================ */
      function ensureAudio() {
        if (!ctx) initAudio();
        if (ctx && ctx.state === 'suspended') ctx.resume();
      }

      function getImpulse() {
        if (cachedImpulse) return cachedImpulse;
        const rate = ctx.sampleRate;
        const length = Math.floor(rate * 2.2);
        const impulse = ctx.createBuffer(2, length, rate);
        for (let ch = 0; ch < 2; ch++) {
          const data = impulse.getChannelData(ch);
          for (let i = 0; i < length; i++) {
            data[i] = (Math.random() * 2 - 1) * Math.pow(1 - i / length, 2.4);
          }
        }
        cachedImpulse = impulse;
        return impulse;
      }

      function buildChannel(name, opts) {
        opts = opts || {};
        const withEQ = opts.withEQ !== false;
        const withReverb = opts.withReverb !== false;

        const input = ctx.createGain();
        input.gain.value = 1;
        const chain = { input: input, name: name, muted: false, lastFaderValue: 1, meterEl: null };
        let node = input;

        if (withEQ) {
          const low = ctx.createBiquadFilter(); low.type = 'lowshelf'; low.frequency.value = 150; low.gain.value = 0;
          const mid = ctx.createBiquadFilter(); mid.type = 'peaking'; mid.frequency.value = 1000; mid.Q.value = 1; mid.gain.value = 0;
          const high = ctx.createBiquadFilter(); high.type = 'highshelf'; high.frequency.value = 6000; high.gain.value = 0;
          node.connect(low); low.connect(mid); mid.connect(high);
          node = high;
          chain.low = low; chain.mid = mid; chain.high = high;
        }

        const fader = ctx.createGain();
        fader.gain.value = 1;

        if (withReverb) {
          const dry = ctx.createGain(); dry.gain.value = 1;
          const convolver = ctx.createConvolver(); convolver.buffer = getImpulse();
          const wet = ctx.createGain(); wet.gain.value = 0;
          node.connect(dry); dry.connect(fader);
          node.connect(convolver); convolver.connect(wet); wet.connect(fader);
          chain.dry = dry; chain.convolver = convolver; chain.wet = wet;
        } else {
          node.connect(fader);
        }

        const analyser = ctx.createAnalyser();
        analyser.fftSize = 256;
        analyser.smoothingTimeConstant = 0.6;
        fader.connect(analyser);

        chain.fader = fader;
        chain.analyser = analyser;
        return chain;
      }

      function initAudio() {
        if (ctx) return;
        ctx = new (window.AudioContext || window.webkitAudioContext)();
        masterBus = buildChannel('Master', { withEQ: false, withReverb: false });
        masterBus.analyser.connect(ctx.destination);

        state.channels.soundpad = buildChannel('Sound Pads');
        state.channels.soundboard = buildChannel('Soundboard');
        state.channels.loop = buildChannel('Loop');

        ['soundpad', 'soundboard', 'loop'].forEach(function (key) {
          state.channels[key].analyser.connect(masterBus.input);
        });

        buildMixUI();
        startMeterLoop();
      }

      /* ============================================================
         FILE LOADING
      ============================================================ */
      function openFilePicker(pad, onLoaded) {
        const input = el('input', { type: 'file', accept: 'audio/*', style: 'display:none' });
        input.addEventListener('change', function (e) {
          const file = e.target.files && e.target.files[0];
          if (file) loadAudioFile(file, pad, onLoaded);
        });
        document.body.appendChild(input);
        input.click();
        setTimeout(function () { input.remove(); }, 1500);
      }

      function loadAudioFile(file, pad, onLoaded) {
        ensureAudio();
        pad.loading = true;
        refreshAllUI();
        const reader = new FileReader();
        reader.onload = function (e) {
          ctx.decodeAudioData(e.target.result).then(function (buffer) {
            pad.buffer = buffer;
            if ('trimEnd' in pad) {
              pad.originalBuffer = buffer;
              pad.trimStart = 0; pad.trimEnd = buffer.duration;
              pad.gain = 1; pad.fadeIn = 0; pad.fadeOut = 0;
              pad.eq = { lowFreq: 150, lowGain: 0, midFreq: 1000, midGain: 0, highFreq: 6000, highGain: 0 };
            }
            pad.fileName = file.name;
            pad.loading = false;
            refreshAllUI();
            if (onLoaded) onLoaded();
          }).catch(function () {
            pad.loading = false;
            refreshAllUI();
            alert('Could not read this audio file. Try MP3, WAV, OGG or M4A.');
          });
        };
        reader.onerror = function () { pad.loading = false; refreshAllUI(); };
        reader.readAsArrayBuffer(file);
      }

      function refreshAllUI() {
        renderSoundPadsUI();
        renderSoundboardUI();
        renderLoopsUI();
      }

      /* ============================================================
         SOUND PADS
      ============================================================ */
      function renderSoundPadsUI() {
        const tabsWrap = document.getElementById('sp-category-tabs');
        const gridWrap = document.getElementById('sp-grid');
        tabsWrap.innerHTML = '';
        SOUND_CATEGORIES.forEach(function (letter) {
          const tab = el('button', {
            class: 'cat-tab' + (letter === activeSPCategory ? ' active' : ''),
            text: letter,
            onClick: function () { activeSPCategory = letter; renderSoundPadsUI(); }
          });
          tabsWrap.appendChild(tab);
        });

        gridWrap.innerHTML = '';
        state.soundPads[activeSPCategory].forEach(function (pad) {
          gridWrap.appendChild(buildSoundPadEl(pad));
        });
        gridWrap.appendChild(el('button', {
          class: 'add-pad-btn', text: '+ Add Pad',
          onClick: function () {
            const arr = state.soundPads[activeSPCategory];
            arr.push(makeSoundPad(activeSPCategory, arr.length));
            renderSoundPadsUI();
          }
        }));
      }

      function buildSoundPadEl(pad) {
        const classes = ['pad'];
        if (!pad.buffer) classes.push('empty');
        if (pad.isPlaying) classes.push('playing');
        if (pad.loading) classes.push('loading');

        const nameInput = el('input', {
          class: 'pad-name', type: 'text', value: pad.name,
          onClick: function (e) { e.stopPropagation(); },
          onChange: function (e) { pad.name = e.target.value || pad.name; }
        });

        const iconEl = el('div', { class: 'pad-icon', text: pad.loading ? '…' : (!pad.buffer ? '\u2B06' : (pad.isPlaying ? '\u25A0' : '\u25B6')) });
        const fileEl = el('div', { class: 'pad-file', text: pad.buffer ? pad.fileName : 'No sound loaded' });

        const loopBtn = el('button', {
          class: 'mini-btn' + (pad.loopEnabled ? ' on' : ''), text: '\u27F3', title: 'Loop while held down',
          onClick: function (e) { e.stopPropagation(); pad.loopEnabled = !pad.loopEnabled; renderSoundPadsUI(); }
        });
        const replaceBtn = el('button', {
          class: 'mini-btn', text: '\u2963', title: 'Replace sound',
          onClick: function (e) { e.stopPropagation(); openFilePicker(pad); }
        });

        const wrap = el('div', { class: classes.join(' '), onClick: function () { onSoundPadClick(pad); } }, [
          el('div', { class: 'pad-mini-row' }, pad.buffer ? [loopBtn, replaceBtn] : []),
          iconEl, nameInput, fileEl
        ]);
        pad.el = wrap;
        return wrap;
      }

      function onSoundPadClick(pad) {
        if (pad.loading) return;
        if (!pad.buffer) { openFilePicker(pad); return; }
        if (pad.isPlaying) stopSoundPad(pad);
        else startSoundPad(pad);
      }
      function startSoundPad(pad) {
        ensureAudio();
        const src = ctx.createBufferSource();
        src.buffer = pad.buffer;
        src.loop = pad.loopEnabled;
        src.connect(state.channels.soundpad.input);
        src.onended = function () {
          if (pad.source === src) { pad.isPlaying = false; pad.source = null; updateSoundPadVisual(pad); }
        };
        src.start();
        pad.source = src; pad.isPlaying = true;
        updateSoundPadVisual(pad);
      }
      function stopSoundPad(pad) {
        if (pad.source) { try { pad.source.onended = null; pad.source.stop(); } catch (e) { } pad.source = null; }
        pad.isPlaying = false;
        updateSoundPadVisual(pad);
      }
      function updateSoundPadVisual(pad) {
        if (!pad.el) return;
        pad.el.classList.toggle('playing', pad.isPlaying);
        const icon = pad.el.querySelector('.pad-icon');
        if (icon) icon.textContent = pad.isPlaying ? '\u25A0' : '\u25B6';
      }

      /* ============================================================
         SOUNDBOARD (DRUM PADS)
      ============================================================ */
      function renderSoundboardUI() {
        const gridWrap = document.getElementById('db-grid');
        gridWrap.innerHTML = '';
        state.drumPads.forEach(function (pad) { gridWrap.appendChild(buildDrumPadEl(pad)); });
      }

      function buildDrumPadEl(pad) {
        const classes = ['drum-pad'];
        if (!pad.buffer) classes.push('empty');
        if (pad.isPlaying) classes.push('playing');
        if (pad.loading) classes.push('loading');

        const editBtn = el('button', {
          class: 'drum-pad-edit', text: 'EDIT',
          onClick: function (e) { e.stopPropagation(); if (pad.buffer) openDrumEditor(pad); }
        });
        if (!pad.buffer) editBtn.setAttribute('disabled', 'true');

        const wrap = el('div', { class: classes.join(' '), onClick: function () { onDrumPadClick(pad); } }, [
          el('div', { class: 'drum-pad-icon', text: pad.loading ? '…' : (!pad.buffer ? '\u2B06' : '\u25B6') }),
          el('div', { class: 'drum-pad-label', text: pad.name }),
          el('div', { class: 'drum-pad-file', text: pad.buffer ? pad.fileName : 'Tap to upload' }),
          editBtn
        ]);
        pad.el = wrap;
        return wrap;
      }

      function onDrumPadClick(pad) {
        if (pad.loading) return;
        if (!pad.buffer) { openFilePicker(pad, function () { /* stays ready to trigger */ }); return; }
        triggerDrumPad(pad);
      }

      function triggerDrumPad(pad) {
        ensureAudio();
        if (pad.source) { try { pad.source.stop(); } catch (e) { } }

        const src = ctx.createBufferSource();
        src.buffer = pad.buffer;
        const env = ctx.createGain();
        const low = ctx.createBiquadFilter(); low.type = 'lowshelf'; low.frequency.value = pad.eq.lowFreq; low.gain.value = pad.eq.lowGain;
        const mid = ctx.createBiquadFilter(); mid.type = 'peaking'; mid.frequency.value = pad.eq.midFreq; mid.Q.value = 1; mid.gain.value = pad.eq.midGain;
        const high = ctx.createBiquadFilter(); high.type = 'highshelf'; high.frequency.value = pad.eq.highFreq; high.gain.value = pad.eq.highGain;

        src.connect(env); env.connect(low); low.connect(mid); mid.connect(high); high.connect(state.channels.soundboard.input);

        const dur = Math.max(0.03, pad.trimEnd - pad.trimStart);
        const fadeIn = Math.min(pad.fadeIn, dur / 2);
        const fadeOut = Math.min(pad.fadeOut, dur / 2);
        const now = ctx.currentTime;
        const g = Math.max(pad.gain, 0.0001);

        env.gain.setValueAtTime(0.0001, now);
        if (fadeIn > 0.001) env.gain.exponentialRampToValueAtTime(g, now + fadeIn);
        else env.gain.setValueAtTime(g, now);

        if (fadeOut > 0.001) {
          env.gain.setValueAtTime(g, Math.max(now, now + dur - fadeOut));
          env.gain.exponentialRampToValueAtTime(0.0001, now + dur);
        }

        src.start(now, pad.trimStart, dur);
        pad.source = src; pad.isPlaying = true;
        updateDrumPadVisual(pad);
        src.onended = function () {
          if (pad.source === src) { pad.isPlaying = false; pad.source = null; updateDrumPadVisual(pad); }
        };
      }
      function stopDrumPad(pad) {
        if (pad.source) { try { pad.source.onended = null; pad.source.stop(); } catch (e) { } pad.source = null; }
        pad.isPlaying = false;
        updateDrumPadVisual(pad);
      }
      function updateDrumPadVisual(pad) {
        if (!pad.el) return;
        pad.el.classList.toggle('playing', pad.isPlaying);
        const icon = pad.el.querySelector('.drum-pad-icon');
        if (icon) icon.textContent = pad.isPlaying ? '\u25A0' : '\u25B6';
      }

      /* --------- Drum Pad Editor Modal --------- */
      function openDrumEditor(pad) {
        currentEditingPad = pad;
        const modal = document.getElementById('drum-editor-modal');
        document.getElementById('de-name').value = pad.name;
        modal.classList.add('show');

        requestAnimationFrame(function () {
          const canvas = document.getElementById('de-waveform');
          sizeCanvas(canvas);
          drawWaveform(canvas, pad.buffer);
          layoutTrimHandles(pad);
        });

        document.getElementById('de-gain').value = Math.round(pad.gain * 100);
        document.getElementById('de-fadein').value = Math.round(pad.fadeIn * 1000);
        document.getElementById('de-fadeout').value = Math.round(pad.fadeOut * 1000);
        updateEditorLabels(pad);
        updateEditorReadouts(pad);
        buildEQKnobs(pad);
      }
      function closeDrumEditor() {
        if (currentEditingPad) stopDrumPad(currentEditingPad);
        document.getElementById('drum-editor-modal').classList.remove('show');
        currentEditingPad = null;
      }

      function sizeCanvas(canvas) {
        const rect = canvas.parentElement.getBoundingClientRect();
        const dpr = window.devicePixelRatio || 1;
        canvas.width = Math.max(200, rect.width) * dpr;
        canvas.height = Math.max(80, rect.height) * dpr;
        canvas.style.width = rect.width + 'px';
        canvas.style.height = rect.height + 'px';
        const c2d = canvas.getContext('2d');
        c2d.setTransform(dpr, 0, 0, dpr, 0, 0);
      }

      function drawWaveform(canvas, buffer) {
        if (!buffer) return;
        const c2d = canvas.getContext('2d');
        const w = canvas.clientWidth, h = canvas.clientHeight;
        c2d.clearRect(0, 0, w, h);
        const data = buffer.getChannelData(0);
        const step = Math.max(1, Math.ceil(data.length / w));
        const amp = h / 2;
        c2d.strokeStyle = '#ff2743';
        c2d.lineWidth = 1;
        c2d.beginPath();
        for (let x = 0; x < w; x++) {
          let min = 1.0, max = -1.0;
          const start = x * step;
          for (let j = 0; j < step; j++) {
            const idx = start + j;
            if (idx < data.length) {
              const v = data[idx];
              if (v < min) min = v;
              if (v > max) max = v;
            }
          }
          c2d.moveTo(x + 0.5, (1 + min) * amp);
          c2d.lineTo(x + 0.5, (1 + max) * amp);
        }
        c2d.stroke();
      }

      function layoutTrimHandles(pad) {
        if (!pad.buffer) return;
        const dur = pad.buffer.duration || 0.0001;
        const startPct = clamp(pad.trimStart / dur, 0, 1) * 100;
        const endPct = clamp(pad.trimEnd / dur, 0, 1) * 100;
        document.getElementById('de-handle-start').style.left = startPct + '%';
        document.getElementById('de-handle-end').style.left = endPct + '%';
        const sel = document.getElementById('de-selection');
        sel.style.left = startPct + '%';
        sel.style.width = Math.max(0, endPct - startPct) + '%';
      }

      function updateEditorReadouts(pad) {
        document.getElementById('de-start-time').textContent = fmtTime(pad.trimStart);
        document.getElementById('de-end-time').textContent = fmtTime(pad.trimEnd);
        document.getElementById('de-length-time').textContent = fmtTime(Math.max(0, pad.trimEnd - pad.trimStart));
      }

      function updateEditorLabels(pad) {
        document.getElementById('de-gain-val').textContent = Math.round(pad.gain * 100) + '% (' + gainToDbLabel(pad.gain) + ')';
        document.getElementById('de-fadein-val').textContent = pad.fadeIn.toFixed(2) + 's';
        document.getElementById('de-fadeout-val').textContent = pad.fadeOut.toFixed(2) + 's';
      }

      function makeHandleDraggable(handleEl, pad, isStart) {
        handleEl.addEventListener('pointerdown', function (e) {
          e.preventDefault();
          try { handleEl.setPointerCapture(e.pointerId); } catch (err) { }
          const wrap = document.getElementById('de-waveform-wrap');
          function onMove(ev) {
            const rect = wrap.getBoundingClientRect();
            let frac = (ev.clientX - rect.left) / rect.width;
            frac = clamp(frac, 0, 1);
            const t = frac * pad.buffer.duration;
            if (isStart) pad.trimStart = Math.min(t, pad.trimEnd - 0.02);
            else pad.trimEnd = Math.max(t, pad.trimStart + 0.02);
            layoutTrimHandles(pad);
            updateEditorReadouts(pad);
          }
          function onUp() {
            window.removeEventListener('pointermove', onMove);
            window.removeEventListener('pointerup', onUp);
          }
          window.addEventListener('pointermove', onMove);
          window.addEventListener('pointerup', onUp);
        });
      }
      makeHandleDraggable(document.getElementById('de-handle-start'), null, true);
      makeHandleDraggable(document.getElementById('de-handle-end'), null, false);
      // rebind targets dynamically since pad changes each time editor opens
      function rebindHandles(pad) {
        const startH = document.getElementById('de-handle-start');
        const endH = document.getElementById('de-handle-end');
        const freshStart = startH.cloneNode(true);
        const freshEnd = endH.cloneNode(true);
        startH.parentNode.replaceChild(freshStart, startH);
        endH.parentNode.replaceChild(freshEnd, endH);
        makeHandleDraggable(freshStart, pad, true);
        makeHandleDraggable(freshEnd, pad, false);
      }

      function buildEQKnobs(pad) {
        const wrap = document.getElementById('de-eq-knobs');
        wrap.innerHTML = '';
        const bands = [
          { key: 'low', label: 'LOW', fmin: 60, fmax: 500 },
          { key: 'mid', label: 'MID', fmin: 200, fmax: 5000 },
          { key: 'high', label: 'HIGH', fmin: 2000, fmax: 16000 }
        ];
        bands.forEach(function (b) {
          const freqKnob = createKnob({
            label: b.label + ' FREQ', min: b.fmin, max: b.fmax, value: pad.eq[b.key + 'Freq'], step: 1,
            defaultValue: pad.eq[b.key + 'Freq'],
            format: function (v) { return v >= 1000 ? (v / 1000).toFixed(1) + 'k' : Math.round(v) + 'Hz'; },
            onChange: function (v) { pad.eq[b.key + 'Freq'] = v; }
          });
          const gainKnob = createKnob({
            label: b.label + ' GAIN', min: -12, max: 12, value: pad.eq[b.key + 'Gain'], step: 0.5, defaultValue: 0,
            format: function (v) { return (v > 0 ? '+' : '') + v.toFixed(1) + 'dB'; },
            onChange: function (v) { pad.eq[b.key + 'Gain'] = v; }
          });
          wrap.appendChild(freqKnob.el);
          wrap.appendChild(gainKnob.el);
        });
      }

      document.getElementById('de-name').addEventListener('input', function (e) {
        if (!currentEditingPad) return;
        currentEditingPad.name = e.target.value || currentEditingPad.name;
        const label = currentEditingPad.el && currentEditingPad.el.querySelector('.drum-pad-label');
        if (label) label.textContent = currentEditingPad.name;
      });
      document.getElementById('de-gain').addEventListener('input', function (e) {
        if (!currentEditingPad) return;
        currentEditingPad.gain = Number(e.target.value) / 100;
        updateEditorLabels(currentEditingPad);
      });
      document.getElementById('de-fadein').addEventListener('input', function (e) {
        if (!currentEditingPad) return;
        currentEditingPad.fadeIn = Number(e.target.value) / 1000;
        updateEditorLabels(currentEditingPad);
      });
      document.getElementById('de-fadeout').addEventListener('input', function (e) {
        if (!currentEditingPad) return;
        currentEditingPad.fadeOut = Number(e.target.value) / 1000;
        updateEditorLabels(currentEditingPad);
      });
      document.getElementById('de-play').addEventListener('click', function () {
        if (currentEditingPad) triggerDrumPad(currentEditingPad);
      });
      document.getElementById('de-stop').addEventListener('click', function () {
        if (currentEditingPad) stopDrumPad(currentEditingPad);
      });
      document.getElementById('de-reset').addEventListener('click', function () {
        const pad = currentEditingPad;
        if (!pad || !pad.originalBuffer) return;
        pad.trimStart = 0; pad.trimEnd = pad.originalBuffer.duration;
        pad.gain = 1; pad.fadeIn = 0; pad.fadeOut = 0;
        pad.eq = { lowFreq: 150, lowGain: 0, midFreq: 1000, midGain: 0, highFreq: 6000, highGain: 0 };
        document.getElementById('de-gain').value = 100;
        document.getElementById('de-fadein').value = 0;
        document.getElementById('de-fadeout').value = 0;
        updateEditorLabels(pad);
        updateEditorReadouts(pad);
        layoutTrimHandles(pad);
        buildEQKnobs(pad);
      });
      document.getElementById('de-replace').addEventListener('click', function () {
        const pad = currentEditingPad;
        if (!pad) return;
        openFilePicker(pad, function () {
          document.getElementById('de-name').value = pad.name;
          requestAnimationFrame(function () {
            const canvas = document.getElementById('de-waveform');
            sizeCanvas(canvas);
            drawWaveform(canvas, pad.buffer);
            layoutTrimHandles(pad);
          });
          updateEditorReadouts(pad);
          updateEditorLabels(pad);
          document.getElementById('de-gain').value = 100;
          document.getElementById('de-fadein').value = 0;
          document.getElementById('de-fadeout').value = 0;
          buildEQKnobs(pad);
        });
      });
      document.getElementById('de-close').addEventListener('click', closeDrumEditor);

      // patch openDrumEditor to rebind trim handles to the correct pad each time
      const _openDrumEditorOriginal = openDrumEditor;
      openDrumEditor = function (pad) {
        _openDrumEditorOriginal(pad);
        rebindHandles(pad);
      };

      /* ============================================================
         LOOPS
      ============================================================ */
      function renderLoopsUI() {
        const wrap = document.getElementById('loop-list');
        wrap.innerHTML = '';
        state.loopPads.forEach(function (pad) { wrap.appendChild(buildLoopEl(pad)); });
      }

      function buildLoopEl(pad) {
        const classes = ['loop-row'];
        if (pad.isPlaying) classes.push('playing');
        if (pad.loading) classes.push('loading');

        const nameInput = el('input', {
          class: 'loop-name', type: 'text', value: pad.name,
          onChange: function (e) { pad.name = e.target.value || pad.name; }
        });

        const playBtn = el('button', {
          class: 'loop-play-btn', text: pad.loading ? '…' : (pad.isPlaying ? '\u25A0' : '\u25B6'),
          onClick: function () {
            if (pad.loading) return;
            if (!pad.buffer) { openFilePicker(pad); return; }
            if (pad.isPlaying) stopLoopPad(pad); else startLoopPad(pad);
          }
        });

        const loopToggle = el('button', {
          class: 'mini-btn' + (pad.loopEnabled ? ' on' : ''), text: '\u27F3', title: 'Repeat',
          onClick: function () { pad.loopEnabled = !pad.loopEnabled; if (pad.source) pad.source.loop = pad.loopEnabled; renderLoopsUI(); }
        });

        const uploadBtn = el('button', {
          class: 'loop-upload-btn', text: pad.buffer ? 'Replace' : 'Upload',
          onClick: function () { openFilePicker(pad); }
        });

        const wrap = el('div', { class: classes.join(' ') }, [
          el('div', { class: 'loop-reel' }),
          el('div', { class: 'loop-info' }, [
            nameInput,
            el('div', { class: 'loop-file', text: pad.buffer ? pad.fileName : 'No loop loaded' })
          ]),
          el('div', { class: 'loop-controls' }, [loopToggle, playBtn, uploadBtn])
        ]);
        pad.el = wrap;
        return wrap;
      }

      function startLoopPad(pad) {
        ensureAudio();
        const src = ctx.createBufferSource();
        src.buffer = pad.buffer;
        src.loop = pad.loopEnabled;
        src.connect(state.channels.loop.input);
        src.onended = function () {
          if (pad.source === src) { pad.isPlaying = false; pad.source = null; renderLoopsUI(); }
        };
        src.start();
        pad.source = src; pad.isPlaying = true;
        renderLoopsUI();
      }
      function stopLoopPad(pad) {
        if (pad.source) { try { pad.source.onended = null; pad.source.stop(); } catch (e) { } pad.source = null; }
        pad.isPlaying = false;
        renderLoopsUI();
      }

      /* ============================================================
         KNOB COMPONENT
      ============================================================ */
      function createKnob(opts) {
        let val = opts.value;
        const min = opts.min, max = opts.max, step = opts.step || 1;
        const def = (opts.defaultValue !== undefined) ? opts.defaultValue : opts.value;
        const format = opts.format;
        const onChange = opts.onChange;

        const indicator = el('div', { class: 'knob-indicator' });
        const dial = el('div', { class: 'knob-dial', tabindex: '0' }, [indicator]);
        const labelEl = el('div', { class: 'knob-label', text: opts.label });
        const valueEl = el('div', { class: 'knob-value' });
        const wrap = el('div', { class: 'knob' }, [dial, labelEl, valueEl]);

        function render() {
          const frac = (val - min) / (max - min);
          const deg = -135 + frac * 270;
          indicator.style.transform = 'translateX(-50%) rotate(' + deg + 'deg)';
          valueEl.textContent = format ? format(val) : String(Math.round(val * 100) / 100);
        }
        function setVal(v) {
          v = clamp(v, min, max);
          v = Math.round(v / step) * step;
          val = v;
          render();
          if (onChange) onChange(val);
        }
        render();

        dial.addEventListener('pointerdown', function (e) {
          e.preventDefault();
          try { dial.setPointerCapture(e.pointerId); } catch (err) { }
          const startY = e.clientY, startVal = val;
          dial.classList.add('active');
          function onMove(ev) {
            const delta = startY - ev.clientY;
            setVal(startVal + (delta / 140) * (max - min));
          }
          function onUp() {
            dial.classList.remove('active');
            window.removeEventListener('pointermove', onMove);
            window.removeEventListener('pointerup', onUp);
          }
          window.addEventListener('pointermove', onMove);
          window.addEventListener('pointerup', onUp);
        });
        dial.addEventListener('dblclick', function () { setVal(def); });
        dial.addEventListener('keydown', function (e) {
          if (e.key === 'ArrowUp') { setVal(val + step); e.preventDefault(); }
          if (e.key === 'ArrowDown') { setVal(val - step); e.preventDefault(); }
        });

        return { el: wrap, setVal: setVal, getVal: function () { return val; } };
      }

      /* ============================================================
         MIX SECTION
      ============================================================ */
      function buildFader(ch) {
        const wrap = el('div', { class: 'fader-wrap' });
        const dbLabel = el('div', { class: 'fader-db', text: gainToDbLabel(ch.fader.gain.value) });
        const input = el('input', {
          type: 'range', class: 'fader-input', min: '0', max: '150',
          value: String(Math.round(ch.fader.gain.value * 100))
        });
        input.addEventListener('input', function () {
          const v = Number(input.value) / 100;
          ch.fader.gain.value = v;
          ch.lastFaderValue = v;
          dbLabel.textContent = gainToDbLabel(v);
        });
        const track = el('div', { class: 'fader-track' }, [input]);
        wrap.appendChild(dbLabel);
        wrap.appendChild(track);
        return wrap;
      }

      function buildMeterEl() {
        const wrap = el('div', { class: 'meter' });
        const segCount = 14;
        for (let i = 0; i < segCount; i++) {
          let cls = 'meter-seg';
          if (i >= segCount - 3) cls += ' seg-red';
          else if (i >= segCount - 6) cls += ' seg-amber';
          else cls += ' seg-green';
          wrap.appendChild(el('div', { class: cls }));
        }
        return wrap;
      }

      function toggleMute(channelKey, btn) {
        const ch = state.channels[channelKey] || masterBus;
        ch.muted = !ch.muted;
        if (ch.muted) {
          ch.lastFaderValue = ch.fader.gain.value > 0 ? ch.fader.gain.value : ch.lastFaderValue;
          ch.fader.gain.value = 0;
        } else {
          ch.fader.gain.value = ch.lastFaderValue || 1;
        }
        btn.classList.toggle('on', ch.muted);
        const strip = btn.closest('.mix-strip');
        const dbLabel = strip && strip.querySelector('.fader-db');
        const rangeInput = strip && strip.querySelector('.fader-input');
        if (dbLabel) dbLabel.textContent = gainToDbLabel(ch.fader.gain.value);
        if (rangeInput) rangeInput.value = String(Math.round(ch.fader.gain.value * 100));
      }

      function toggleSolo(channelKey, btn) {
        const keys = ['soundpad', 'soundboard', 'loop'];
        if (soloedChannel === channelKey) {
          soloedChannel = null;
          keys.forEach(function (k) {
            const ch = state.channels[k];
            if (!ch.muted) ch.fader.gain.value = ch.lastFaderValue || 1;
          });
        } else {
          soloedChannel = channelKey;
          keys.forEach(function (k) {
            const ch = state.channels[k];
            if (k === channelKey) {
              if (!ch.muted) ch.fader.gain.value = ch.lastFaderValue || 1;
            } else {
              ch.fader.gain.value = 0;
            }
          });
        }
        document.querySelectorAll('.solo-btn').forEach(function (b) { b.classList.remove('on'); });
        if (soloedChannel) btn.classList.add('on');
        syncFaderUI();
      }

      function syncFaderUI() {
        ['soundpad', 'soundboard', 'loop'].forEach(function (key) {
          const ch = state.channels[key];
          const strip = document.querySelector('.mix-strip[data-channel="' + key + '"]');
          if (!strip) return;
          const dbLabel = strip.querySelector('.fader-db');
          const rangeInput = strip.querySelector('.fader-input');
          if (dbLabel) dbLabel.textContent = gainToDbLabel(ch.fader.gain.value);
          if (rangeInput) rangeInput.value = String(Math.round(ch.fader.gain.value * 100));
        });
      }

      function buildChannelStrip(channelKey, label) {
        const ch = state.channels[channelKey];
        const strip = el('div', { class: 'mix-strip', 'data-channel': channelKey });
        strip.appendChild(el('div', { class: 'strip-label', text: label }));

        const eqWrap = el('div', { class: 'strip-eq' });
        const bands = [
          { node: ch.low, label: 'LOW', fmin: 40, fmax: 400 },
          { node: ch.mid, label: 'MID', fmin: 200, fmax: 6000 },
          { node: ch.high, label: 'HIGH', fmin: 1500, fmax: 16000 }
        ];
        bands.forEach(function (b) {
          const freqKnob = createKnob({
            label: b.label + ' FREQ', min: b.fmin, max: b.fmax, value: b.node.frequency.value,
            defaultValue: b.node.frequency.value,
            format: function (v) { return v >= 1000 ? (v / 1000).toFixed(1) + 'k' : Math.round(v) + 'Hz'; },
            onChange: function (v) { b.node.frequency.value = v; }
          });
          const gainKnob = createKnob({
            label: b.label + ' GAIN', min: -12, max: 12, value: b.node.gain.value, step: 0.5, defaultValue: 0,
            format: function (v) { return (v > 0 ? '+' : '') + v.toFixed(1) + 'dB'; },
            onChange: function (v) { b.node.gain.value = v; }
          });
          eqWrap.appendChild(freqKnob.el);
          eqWrap.appendChild(gainKnob.el);
        });
        strip.appendChild(eqWrap);

        const reverbPct = Math.round((ch.wet.gain.value / 0.8) * 100);
        const reverbKnob = createKnob({
          label: 'REVERB', min: 0, max: 100, value: reverbPct, step: 1, defaultValue: 0,
          format: function (v) { return Math.round(v) + '%'; },
          onChange: function (v) { ch.wet.gain.value = (v / 100) * 0.8; }
        });
        strip.appendChild(el('div', { class: 'strip-reverb' }, [reverbKnob.el]));

        strip.appendChild(buildFader(ch));

        const meterEl = buildMeterEl();
        ch.meterEl = meterEl;
        strip.appendChild(el('div', { class: 'meter-row' }, [meterEl]));

        const muteBtn = el('button', { class: 'mute-btn', text: 'MUTE' });
        muteBtn.addEventListener('click', function () { toggleMute(channelKey, muteBtn); });
        const soloBtn = el('button', { class: 'solo-btn', text: 'SOLO' });
        soloBtn.addEventListener('click', function () { toggleSolo(channelKey, soloBtn); });
        strip.appendChild(el('div', { class: 'strip-buttons' }, [muteBtn, soloBtn]));

        return strip;
      }

      function buildMasterStrip() {
        const strip = el('div', { class: 'mix-strip master-strip', 'data-channel': 'master' });
        strip.appendChild(el('div', { class: 'strip-label', text: 'MASTER' }));
        strip.appendChild(el('div', { class: 'strip-eq', style: 'min-height:0' }));
        strip.appendChild(buildFader(masterBus));
        const meterEl = buildMeterEl();
        masterBus.meterEl = meterEl;
        strip.appendChild(el('div', { class: 'meter-row' }, [meterEl]));
        const muteBtn = el('button', { class: 'mute-btn', text: 'MUTE' });
        muteBtn.addEventListener('click', function () { toggleMute('master', muteBtn); });
        strip.appendChild(el('div', { class: 'strip-buttons' }, [muteBtn]));
        return strip;
      }

      function buildMixUI() {
        const wrap = document.getElementById('mix-strips');
        wrap.innerHTML = '';
        wrap.appendChild(buildChannelStrip('soundpad', 'SOUND PADS'));
        wrap.appendChild(buildChannelStrip('soundboard', 'SOUNDBOARD'));
        wrap.appendChild(buildChannelStrip('loop', 'LOOP'));
        wrap.appendChild(buildMasterStrip());
      }

      /* ============================================================
         METERS
      ============================================================ */
      function updateMeterVisual(meterEl, analyser) {
        const data = new Uint8Array(analyser.fftSize);
        analyser.getByteTimeDomainData(data);
        let sumSq = 0;
        for (let i = 0; i < data.length; i++) {
          const v = (data[i] - 128) / 128;
          sumSq += v * v;
        }
        const rms = Math.sqrt(sumSq / data.length);
        const level = Math.min(1, rms * 4.5);
        const segs = meterEl.children;
        const litCount = Math.round(level * segs.length);
        for (let i = 0; i < segs.length; i++) {
          segs[i].classList.toggle('lit', i >= segs.length - litCount);
        }
      }
      function startMeterLoop() {
        function frame() {
          ['soundpad', 'soundboard', 'loop'].forEach(function (key) {
            const ch = state.channels[key];
            if (ch && ch.meterEl) updateMeterVisual(ch.meterEl, ch.analyser);
          });
          if (masterBus && masterBus.meterEl) updateMeterVisual(masterBus.meterEl, masterBus.analyser);
          requestAnimationFrame(frame);
        }
        requestAnimationFrame(frame);
      }

      /* ============================================================
         STOP ALL
      ============================================================ */
      function stopAllAudio() {
        Object.keys(state.soundPads).forEach(function (letter) {
          state.soundPads[letter].forEach(function (p) { if (p.isPlaying) stopSoundPad(p); });
        });
        state.drumPads.forEach(function (p) { if (p.isPlaying) stopDrumPad(p); });
        state.loopPads.forEach(function (p) { if (p.isPlaying) stopLoopPad(p); });
      }
      document.getElementById('stop-all-btn').addEventListener('click', stopAllAudio);

      /* ============================================================
         NAVIGATION
      ============================================================ */
      document.getElementById('main-nav').addEventListener('click', function (e) {
        const btn = e.target.closest('.nav-tab');
        if (!btn) return;
        const tab = btn.getAttribute('data-tab');
        document.querySelectorAll('.nav-tab').forEach(function (t) { t.classList.toggle('active', t === btn); });
        document.querySelectorAll('.section').forEach(function (s) {
          s.classList.toggle('active', s.id === 'section-' + tab);
        });
      });

      /* ============================================================
         LOADING SCREEN
      ============================================================ */
      function startLoadingSequence() {
        const bar = document.getElementById('loading-bar-fill');
        const pctEl = document.getElementById('loading-pct');
        const msgEl = document.getElementById('loading-msg');
        const messages = [
          'Warming up the pad engine…',
          'Calibrating the mixer…',
          'Tuning the reverb tank…',
          'Waking up the drum pads…',
          'Spooling the loop deck…',
          'Almost there…'
        ];
        let msgIdx = 0;
        msgEl.textContent = messages[0];
        const msgInterval = setInterval(function () {
          msgIdx = (msgIdx + 1) % messages.length;
          msgEl.textContent = messages[msgIdx];
        }, 550);

        let p = 0;
        const interval = setInterval(function () {
          p += Math.random() * 9 + 4;
          if (p >= 100) p = 100;
          bar.style.width = p + '%';
          pctEl.textContent = Math.floor(p) + '%';
          if (p >= 100) {
            clearInterval(interval);
            clearInterval(msgInterval);
            setTimeout(function () {
              document.getElementById('loading-screen').classList.add('hide');
              document.getElementById('login-screen').classList.add('show');
            }, 350);
          }
        }, 220);
      }

      /* ============================================================
         LOGIN / ENTER
      ============================================================ */
      document.getElementById('enter-btn').addEventListener('click', function () {
        const name = document.getElementById('user-name-input').value.trim();
        initAudio();
        document.getElementById('login-screen').classList.add('hide');
        document.getElementById('app').classList.add('show');
        if (name) document.getElementById('welcome-name').textContent = 'Welcome, ' + name;
      });
      document.getElementById('user-name-input').addEventListener('keydown', function (e) {
        if (e.key === 'Enter') document.getElementById('enter-btn').click();
      });

      /* ============================================================
         INIT
      ============================================================ */
      renderSoundPadsUI();
      renderSoundboardUI();
      renderLoopsUI();
      startLoadingSequence();

      window.addEventListener('resize', function () {
        if (currentEditingPad && currentEditingPad.buffer) {
          const canvas = document.getElementById('de-waveform');
          if (document.getElementById('drum-editor-modal').classList.contains('show')) {
            sizeCanvas(canvas);
            drawWaveform(canvas, currentEditingPad.buffer);
            layoutTrimHandles(currentEditingPad);
          }
        }
      });

    })();
  </script>
</body>

</html>
