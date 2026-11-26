<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MULTI PURPOSE TOOL — D4XNET PROJECT</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Archivo+Black&family=Plus+Jakarta+Sans:wght@500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />

  <style>
    :root {
      --ink: #061024;
      --navy-dark: #05132e;
      --navy-mid: #0a2458;
      --blue-royal: #1456d9;
      --blue-vivid: #2575fc;
      --cyan-ice: #38bdf8;
      --cyan-light: #bae6fd;
      --surface-white: #f8fbff;
      --surface-tint: #eaf3ff;
      --border-comic: 3px solid var(--ink);
      --shadow-comic-sm: 4px 4px 0px var(--ink);
      --shadow-comic-md: 6px 6px 0px var(--ink);
      --shadow-comic-lg: 8px 8px 0px var(--ink);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: linear-gradient(160deg, #030b1c 0%, var(--navy-dark) 45%, var(--navy-mid) 100%);
      color: var(--ink);
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
      -webkit-font-smoothing: antialiased;
    }

    /* Subtle Halftone Comic Dot Pattern */
    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 1;
      background-image: radial-gradient(rgba(56, 189, 248, 0.11) 1.25px, transparent 1.25px);
      background-size: 16px 16px;
    }

    /* Clean, Crisp 3D Comic Display Typography */
    .display-title {
      font-family: 'Archivo Black', sans-serif;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      line-height: 1.15;
    }

    .text-3d-clean {
      color: #ffffff;
      text-shadow:
        0 2px 0 var(--ink),
        3px 4px 0 var(--blue-royal),
        5px 6px 0 var(--ink);
    }

    .screen {
      display: none;
      position: relative;
      z-index: 2;
      min-height: 100vh;
      width: 100%;
    }

    .screen.active {
      display: block;
    }

    /* ==================== 1. ENTRY SCREEN ==================== */
    #entry-screen {
      position: fixed;
      inset: 0;
      z-index: 50;
      display: none;
      overflow: hidden;
    }

    #entry-screen.active {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    #bg-video-entry {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      z-index: 0;
      filter: brightness(0.62) contrast(1.06) saturate(1.15);
    }

    .entry-video-tint {
      position: absolute;
      inset: 0;
      z-index: 1;
      background: linear-gradient(180deg, rgba(3, 11, 28, 0.52) 0%, rgba(10, 36, 88, 0.68) 100%);
    }

    .entry-stage {
      position: relative;
      z-index: 2;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 24px;
      gap: 20px;
      animation: floatStage 3.6s ease-in-out infinite;
    }

    @keyframes floatStage {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-9px); }
    }

    .logo-clean-wrap {
      background: transparent !important;
      border: none !important;
      box-shadow: none !important;
      line-height: 0;
    }

    #vaxd-logo {
      max-width: 175px;
      max-height: 175px;
      width: auto;
      height: auto;
      display: block;
      background: transparent !important;
      filter: drop-shadow(0 5px 0 var(--ink)) drop-shadow(0 12px 20px rgba(0, 0, 0, 0.6));
    }

    .floating-main-title {
      font-size: clamp(2rem, 6vw, 4rem);
      padding: 4px 10px;
    }

    .btn-press-enter {
      margin-top: 6px;
      background: linear-gradient(180deg, var(--cyan-ice) 0%, var(--blue-vivid) 100%);
      color: var(--ink);
      font-family: 'Archivo Black', sans-serif;
      font-size: clamp(1.05rem, 2.5vw, 1.35rem);
      letter-spacing: 1.5px;
      padding: 16px 38px;
      border: var(--border-comic);
      border-radius: 16px;
      box-shadow: 0 6px 0 var(--ink), 0 12px 24px rgba(3, 11, 28, 0.5);
      cursor: pointer;
      transition: transform 0.14s ease, box-shadow 0.14s ease, filter 0.14s ease;
    }

    .btn-press-enter:hover {
      transform: translateY(-2px);
      filter: brightness(1.06);
      box-shadow: 0 8px 0 var(--ink), 0 16px 28px rgba(3, 11, 28, 0.6);
    }

    .btn-press-enter:active {
      transform: translateY(4px);
      box-shadow: 0 2px 0 var(--ink);
    }

    /* ==================== 2. LOGIN SCREEN ==================== */
    #login-screen.active {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px 18px;
    }

    .comic-panel {
      background: var(--surface-white);
      border: var(--border-comic);
      border-radius: 22px;
      box-shadow: var(--shadow-comic-lg);
      position: relative;
      overflow: hidden;
    }

    .comic-panel::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 10px;
      background: linear-gradient(90deg, var(--navy-mid) 0%, var(--blue-vivid) 50%, var(--cyan-ice) 100%);
      border-bottom: 3px solid var(--ink);
    }

    .login-card {
      width: 100%;
      max-width: 440px;
      padding: 34px 26px 28px;
    }

    .login-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--surface-tint);
      color: var(--navy-mid);
      border: 2.5px solid var(--ink);
      border-radius: 999px;
      padding: 5px 14px;
      font-weight: 800;
      font-size: 0.75rem;
      letter-spacing: 0.6px;
      box-shadow: 3px 3px 0 var(--ink);
      margin-bottom: 14px;
    }

    .login-heading {
      font-size: clamp(1.65rem, 4.5vw, 2.15rem);
      color: var(--navy-dark);
      margin-bottom: 8px;
    }

    .login-subtitle {
      color: #264273;
      font-size: 0.92rem;
      font-weight: 500;
      line-height: 1.5;
      margin-bottom: 22px;
    }

    .field-group {
      margin-bottom: 16px;
      text-align: left;
    }

    .field-label {
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 800;
      font-size: 0.8rem;
      letter-spacing: 0.5px;
      text-transform: uppercase;
      margin-bottom: 7px;
      color: var(--navy-dark);
    }

    .comic-input, .comic-select, .comic-textarea {
      width: 100%;
      padding: 12px 14px;
      font-family: 'Plus Jakarta Sans', sans-serif;
      font-size: 0.94rem;
      font-weight: 600;
      color: var(--ink);
      background: #ffffff;
      border: 2.5px solid var(--ink);
      border-radius: 12px;
      box-shadow: 3px 3px 0 var(--ink);
      outline: none;
      transition: transform 0.12s ease, box-shadow 0.12s ease, background 0.12s ease;
    }

    .comic-input:focus, .comic-select:focus, .comic-textarea:focus {
      background: #f0f7ff;
      transform: translate(-1px, -1px);
      box-shadow: 4px 4px 0 var(--blue-vivid);
    }

    .comic-textarea {
      min-height: 92px;
      resize: vertical;
    }

    .comic-btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      width: 100%;
      padding: 13px 20px;
      font-family: 'Archivo Black', sans-serif;
      font-size: 0.98rem;
      letter-spacing: 1px;
      text-transform: uppercase;
      color: #ffffff;
      background: linear-gradient(180deg, var(--blue-vivid) 0%, var(--blue-royal) 100%);
      border: 3px solid var(--ink);
      border-radius: 13px;
      box-shadow: 0 5px 0 var(--ink);
      cursor: pointer;
      transition: transform 0.12s ease, box-shadow 0.12s ease, filter 0.12s ease;
    }

    .comic-btn:hover {
      filter: brightness(1.07);
      transform: translateY(-2px);
      box-shadow: 0 7px 0 var(--ink);
    }

    .comic-btn:active {
      transform: translateY(3px);
      box-shadow: 0 2px 0 var(--ink);
    }

    .comic-btn.secondary {
      background: linear-gradient(180deg, #60a5fa 0%, var(--blue-vivid) 100%);
      color: var(--ink);
    }

    .comic-btn.dark-blue {
      background: linear-gradient(180deg, var(--navy-mid) 0%, var(--navy-dark) 100%);
      color: #ffffff;
    }

    .error-banner {
      display: none;
      margin-top: 14px;
      padding: 11px 14px;
      background: #fee2e2;
      border: 2.5px solid var(--ink);
      border-radius: 11px;
      box-shadow: 3px 3px 0 var(--ink);
      color: #991b1b;
      font-weight: 700;
      font-size: 0.86rem;
    }

    .error-banner.show {
      display: block;
    }

    /* ==================== 3. DASHBOARD SCREEN ==================== */
    .dash-container {
      max-width: 1180px;
      margin: 0 auto;
      padding: 26px 18px 80px;
    }

    .dash-top-header {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
      margin-bottom: 22px;
    }

    .dash-main-title {
      font-size: clamp(1.75rem, 5.2vw, 3.1rem);
      text-align: center;
      padding-top: 4px;
    }

    .dash-meta-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      gap: 10px;
      flex-wrap: wrap;
    }

    .session-pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--navy-dark);
      color: var(--cyan-light);
      border: 2.5px solid var(--ink);
      border-radius: 11px;
      padding: 7px 14px;
      font-weight: 700;
      font-size: 0.82rem;
      box-shadow: 3px 3px 0 var(--ink);
    }

    .logout-btn {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      background: var(--blue-vivid);
      color: #ffffff;
      border: 2.5px solid var(--ink);
      border-radius: 11px;
      padding: 7px 14px;
      font-family: 'Plus Jakarta Sans', sans-serif;
      font-weight: 800;
      font-size: 0.82rem;
      box-shadow: 3px 3px 0 var(--ink);
      cursor: pointer;
    }

    /* Rounded Video View Box with Direct Floating Text (No Inner Box) */
    .video-showcase-box {
      position: relative;
      width: 100%;
      height: clamp(220px, 38vw, 390px);
      border-radius: 28px;
      border: 3.5px solid var(--ink);
      box-shadow: 0 8px 0 var(--ink), 0 18px 32px rgba(2, 8, 23, 0.55);
      overflow: hidden;
      background: #040d21;
      margin-bottom: 30px;
    }

    #dash-5g-video {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
      filter: brightness(0.6) contrast(1.08) saturate(1.15);
    }

    .video-center-overlay {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      pointer-events: none;
      padding: 16px;
      text-align: center;
      background: radial-gradient(circle, rgba(5, 19, 46, 0.18) 0%, rgba(3, 11, 28, 0.62) 100%);
    }

    /* Direct Text Over Video — No View Box Wrapper */
    .d4xnet-direct-text {
      font-family: 'Archivo Black', sans-serif;
      font-size: clamp(1.75rem, 5vw, 3.5rem);
      letter-spacing: 2px;
      text-transform: uppercase;
      color: #ffffff;
      text-shadow:
        0 3px 0 var(--ink),
        3px 5px 0 var(--blue-royal),
        6px 7px 0 var(--ink),
        0 10px 24px rgba(0, 0, 0, 0.75);
      background: none !important;
      border: none !important;
      box-shadow: none !important;
      padding: 0;
    }

    .section-divider-label {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      background: linear-gradient(90deg, var(--blue-royal), var(--cyan-ice));
      color: var(--ink);
      border: 3px solid var(--ink);
      border-radius: 14px;
      padding: 9px 18px;
      font-family: 'Archivo Black', sans-serif;
      font-size: 0.95rem;
      letter-spacing: 0.8px;
      box-shadow: 4px 4px 0 var(--ink);
      margin-bottom: 22px;
    }

    /* Tools Grid */
    .tools-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(245px, 1fr));
      gap: 20px;
    }

    /* Slime Scroll Reveal Effect */
    .slime-reveal {
      opacity: 0;
      transform: translateY(34px) scale(0.94, 1.05);
      border-radius: 34px 20px 38px 22px;
      transition:
        opacity 0.48s cubic-bezier(0.22, 1.4, 0.36, 1),
        transform 0.6s cubic-bezier(0.22, 1.5, 0.36, 1),
        border-radius 0.5s cubic-bezier(0.22, 1.35, 0.36, 1);
    }

    .slime-reveal.slime-visible {
      opacity: 1;
      transform: translateY(0px) scale(1, 1);
      border-radius: 20px;
    }

    .tool-view-box {
      background: linear-gradient(170deg, #ffffff 0%, #ebf4ff 100%);
      border: 3px solid var(--ink);
      box-shadow: var(--shadow-comic-md);
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: space-between;
      gap: 14px;
      cursor: pointer;
      text-align: left;
      position: relative;
      overflow: hidden;
      min-height: 196px;
    }

    .tool-view-box:hover {
      transform: translate(-2px, -4px) !important;
      background: linear-gradient(170deg, #ffffff 0%, #dbeafe 100%);
      box-shadow: 8px 9px 0 var(--ink);
    }

    .tool-view-box:active {
      transform: translate(2px, 3px) !important;
      box-shadow: 3px 3px 0 var(--ink);
    }

    /* Unified Blue + Dark Blue SVG Icon Container */
    .svg-icon-frame {
      width: 54px;
      height: 54px;
      border-radius: 14px;
      background: linear-gradient(145deg, var(--navy-dark) 0%, var(--blue-royal) 100%);
      border: 2.5px solid var(--ink);
      box-shadow: 3.5px 3.5px 0 var(--ink);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .svg-icon-frame svg {
      width: 30px;
      height: 30px;
      display: block;
    }

    .tool-box-title {
      font-family: 'Archivo Black', sans-serif;
      font-size: 1.08rem;
      letter-spacing: 0.4px;
      color: var(--navy-dark);
      line-height: 1.25;
      margin-bottom: 5px;
    }

    .tool-box-desc {
      font-size: 0.82rem;
      font-weight: 600;
      color: #2b4778;
      line-height: 1.45;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    .tool-box-cta {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      font-size: 0.75rem;
      font-weight: 800;
      letter-spacing: 0.4px;
      background: var(--cyan-ice);
      color: var(--ink);
      border: 2px solid var(--ink);
      border-radius: 9px;
      padding: 5px 11px;
      box-shadow: 2.5px 2.5px 0 var(--ink);
    }

    /* ==================== 4. FULL SEPARATE TOOL PAGE ==================== */
    .tool-fullpage {
      min-height: 100vh;
      width: 100%;
      padding: 24px 18px 70px;
      background: linear-gradient(160deg, #030b1c 0%, var(--navy-dark) 48%, var(--navy-mid) 100%);
    }

    .tool-page-inner {
      max-width: 940px;
      margin: 0 auto;
    }

    .back-dash-btn {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      background: var(--cyan-ice);
      color: var(--ink);
      font-family: 'Archivo Black', sans-serif;
      font-size: 0.88rem;
      letter-spacing: 0.6px;
      padding: 10px 18px;
      border: 3px solid var(--ink);
      border-radius: 13px;
      box-shadow: 4px 4px 0 var(--ink);
      cursor: pointer;
      margin-bottom: 18px;
      transition: transform 0.12s ease;
    }

    .back-dash-btn:hover {
      transform: translate(-2px, -2px);
      box-shadow: 6px 6px 0 var(--ink);
    }

    .tool-workspace-card {
      background: var(--surface-white);
      border: 3.5px solid var(--ink);
      border-radius: 24px;
      box-shadow: var(--shadow-comic-lg);
      padding: 26px 22px;
    }

    .tool-page-header {
      border-bottom: 3px solid var(--ink);
      padding-bottom: 16px;
      margin-bottom: 22px;
    }

    .tool-page-title {
      font-size: clamp(1.35rem, 3.8vw, 2.1rem);
      color: var(--navy-dark);
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      line-height: 1.2;
    }

    .fa-3d-comic {
      color: var(--blue-vivid);
      text-shadow: 2px 2px 0 var(--ink);
    }

    .tool-page-desc {
      margin-top: 10px;
      font-size: 0.93rem;
      font-weight: 600;
      color: #264273;
      line-height: 1.5;
    }

    .form-grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 16px;
    }

    .result-box {
      margin-top: 22px;
      padding: 18px;
      background: #ffffff;
      border: 3px solid var(--ink);
      border-radius: 16px;
      box-shadow: 5px 5px 0 var(--ink);
    }

    .result-header-row {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      margin-bottom: 14px;
    }

    .result-tag {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      background: var(--surface-tint);
      color: var(--navy-dark);
      border: 2px solid var(--ink);
      border-radius: 9px;
      padding: 5px 12px;
      font-weight: 800;
      font-size: 0.8rem;
      box-shadow: 2.5px 2.5px 0 var(--ink);
    }

    .download-action-btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--cyan-ice);
      color: var(--ink);
      font-weight: 800;
      font-size: 0.84rem;
      text-decoration: none;
      padding: 9px 15px;
      border: 2.5px solid var(--ink);
      border-radius: 11px;
      box-shadow: 3.5px 3.5px 0 var(--ink);
      cursor: pointer;
    }

    .preview-img-wrap {
      position: relative;
      display: inline-block;
      max-width: 100%;
    }

    .top-left-dl-badge {
      position: absolute;
      top: 10px;
      left: 10px;
      z-index: 4;
      background: var(--cyan-ice);
      color: var(--ink);
      border: 2.5px solid var(--ink);
      border-radius: 10px;
      padding: 6px 12px;
      font-weight: 800;
      font-size: 0.8rem;
      text-decoration: none;
      box-shadow: 3px 3px 0 var(--ink);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .output-media-img {
      max-width: 100%;
      max-height: 500px;
      border-radius: 12px;
      border: 2.5px solid var(--ink);
      display: block;
      background: repeating-conic-gradient(#e2ecfa 0% 25%, #ffffff 0% 50%) 50% / 18px 18px;
    }

    /* Spotify Vinyl Disc */
    .spotify-track-card {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 18px;
      background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);
      border: 2.5px solid var(--ink);
      border-radius: 16px;
      padding: 16px;
      box-shadow: 4px 4px 0 var(--ink);
    }

    .vinyl-disc {
      width: 98px;
      height: 98px;
      border-radius: 50%;
      border: 3.5px solid var(--ink);
      box-shadow: 3px 3px 0 var(--ink);
      object-fit: cover;
      flex-shrink: 0;
    }

    .vinyl-disc.spinning {
      animation: spinDisc 4.2s linear infinite;
    }

    @keyframes spinDisc {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    /* GPT4 Chat Box */
    .chat-history-box {
      max-height: 380px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 12px;
      padding: 14px;
      background: #eaf2ff;
      border: 2.5px solid var(--ink);
      border-radius: 14px;
      margin-bottom: 14px;
    }

    .chat-bubble {
      max-width: 84%;
      padding: 11px 14px;
      border: 2.5px solid var(--ink);
      border-radius: 14px;
      box-shadow: 3px 3px 0 var(--ink);
      font-size: 0.91rem;
      line-height: 1.5;
      white-space: pre-wrap;
    }

    .chat-bubble.user {
      align-self: flex-end;
      background: var(--cyan-ice);
      color: var(--ink);
      font-weight: 700;
    }

    .chat-bubble.ai {
      align-self: flex-start;
      background: #ffffff;
      color: var(--ink);
    }

    /* Comic Results Grid */
    .comic-results-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(205px, 1fr));
      gap: 16px;
      margin-top: 14px;
    }

    .komik-card {
      background: #f8fbff;
      border: 2.5px solid var(--ink);
      border-radius: 14px;
      padding: 12px;
      box-shadow: 4px 4px 0 var(--ink);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 10px;
    }

    .komik-card img {
      width: 100%;
      height: 230px;
      object-fit: cover;
      border-radius: 10px;
      border: 2px solid var(--ink);
    }

    /* Spam Terminal */
    .spam-log-console {
      background: var(--navy-dark);
      color: var(--cyan-light);
      font-family: ui-monospace, SFMono-Regular, Menlo, monospace;
      font-size: 0.84rem;
      padding: 14px;
      border-radius: 12px;
      border: 2.5px solid var(--ink);
      max-height: 250px;
      overflow-y: auto;
      line-height: 1.55;
    }

    /* Stats Grid */
    .stat-pills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(155px, 1fr));
      gap: 12px;
      margin-top: 14px;
    }

    .stat-mini-box {
      background: var(--surface-tint);
      border: 2px solid var(--ink);
      border-radius: 11px;
      padding: 10px 12px;
      box-shadow: 3px 3px 0 var(--ink);
    }

    .stat-mini-label {
      font-size: 0.72rem;
      text-transform: uppercase;
      font-weight: 800;
      color: #2b4778;
    }

    .stat-mini-val {
      font-size: 0.98rem;
      font-weight: 800;
      color: var(--navy-dark);
      margin-top: 3px;
      word-break: break-word;
    }

    .json-pre {
      background: var(--navy-dark);
      color: var(--cyan-light);
      padding: 12px;
      border-radius: 12px;
      border: 2.5px solid var(--ink);
      font-size: 0.82rem;
      overflow-x: auto;
      max-height: 260px;
      margin-top: 12px;
    }
  </style>
</head>
<body>

  <!-- ==================== 1. ENTRY SCREEN ==================== -->
  <section id="entry-screen" class="active">
    <video id="bg-video-entry" src="mf_video.mp4" autoplay loop muted playsinline></video>
    <div class="entry-video-tint"></div>

    <div class="entry-stage">
      <div class="logo-clean-wrap">
        <img id="vaxd-logo" src="vaxd.png" alt="VAXD Logo" onerror="this.style.display='none'" />
      </div>
      <h1 class="display-title text-3d-clean floating-main-title">MULTI PURPOSE TOOL</h1>
      <button id="press-to-enter-btn" class="btn-press-enter" type="button">
        PRESS TO ENTER
      </button>
    </div>
  </section>

  <!-- ==================== 2. LOGIN SCREEN ==================== -->
  <section id="login-screen" class="screen">
    <div class="comic-panel login-card">
      <div class="login-badge">
        <i class="fa-solid fa-bolt fa-3d-comic"></i>
        D4XNET ACCESS PORTAL
      </div>
      <h2 class="display-title login-heading">MULTI PURPOSE TOOL</h2>
      <p class="login-subtitle">
        Masukkan kredensial operator untuk membuka panel kontrol <strong>MULTI PURPOSE TOOL</strong>.
      </p>

      <form id="login-form" novalidate>
        <div class="field-group">
          <label class="field-label" for="login-usn">
            <i class="fa-solid fa-user-shield"></i> USERNAME
          </label>
          <input
            id="login-usn"
            class="comic-input"
            type="text"
            placeholder="Masukkan username..."
            autocomplete="username"
            required
          />
        </div>

        <div class="field-group">
          <label class="field-label" for="login-pw">
            <i class="fa-solid fa-key"></i> PASSWORD
          </label>
          <input
            id="login-pw"
            class="comic-input"
            type="password"
            placeholder="Masukkan password..."
            autocomplete="current-password"
            required
          />
        </div>

        <button class="comic-btn" type="submit">
          <i class="fa-solid fa-arrow-right-to-bracket"></i> MASUK DASHBOARD
        </button>

        <div id="login-error" class="error-banner" role="alert"></div>
      </form>
    </div>
  </section>

  <!-- ==================== 3. DASHBOARD SCREEN ==================== -->
  <section id="dashboard-screen" class="screen">
    <div class="dash-container">
      <div class="dash-top-header">
        <h1 class="display-title text-3d-clean dash-main-title">MULTI PURPOSE TOOL</h1>
        <div class="dash-meta-bar">
          <div class="session-pill">
            <i class="fa-solid fa-shield-halved"></i>
            OPERATOR: <span id="active-user-label">lozxxdev</span>
          </div>
          <button id="logout-btn" class="logout-btn" type="button">
            <i class="fa-solid fa-right-from-bracket"></i> KELUAR
          </button>
        </div>
      </div>

      <!-- Rounded Video View Box with Direct Text D4XNET PROJECT (No Inner View Box) -->
      <div class="video-showcase-box">
        <video id="dash-5g-video" src="5g_video.mp4" autoplay loop muted playsinline></video>
        <div class="video-center-overlay">
          <div class="d4xnet-direct-text">D4XNET PROJECT</div>
        </div>
      </div>

      <div class="section-divider-label">
        <i class="fa-solid fa-layer-group"></i>
        20 MODUL API AKTIF — PILIH TOOL
      </div>

      <div id="tools-grid" class="tools-grid"></div>
    </div>
  </section>

  <!-- ==================== 4. SEPARATE TOOL VIEW SCREEN ==================== -->
  <section id="tool-screen" class="screen tool-fullpage">
    <div class="tool-page-inner">
      <button id="back-to-dashboard-btn" class="back-dash-btn" type="button">
        <i class="fa-solid fa-arrow-left"></i> KEMBALI KE DASHBOARD
      </button>

      <div class="tool-workspace-card">
        <div class="tool-page-header">
          <h2 id="active-tool-title" class="display-title tool-page-title"></h2>
          <p id="active-tool-desc" class="tool-page-desc"></p>
        </div>

        <div id="active-tool-form-area"></div>
        <div id="active-tool-result-area"></div>
      </div>
    </div>
  </section>

  <script>
    // ==================== HARMONIZED BLUE + ICE CYAN + WHITE SVGs ====================
    const CUSTOM_SVGS = {
      amSend: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M8 14L40 9L33 39L23 28L8 14Z" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <path d="M40 9L23 28" stroke="#061024" stroke-width="2.8" stroke-linecap="round"/>
          <circle cx="34" cy="15" r="4.5" fill="#FFFFFF" stroke="#061024" stroke-width="2.5"/>
        </svg>`,
      igStory: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="9" y="9" width="30" height="30" rx="9" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <circle cx="24" cy="24" r="7.5" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <circle cx="33" cy="15" r="2.3" fill="#061024"/>
        </svg>`,
      ssPhone: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="14" y="6" width="20" height="36" rx="5" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <path d="M19 12H23M25 36H29" stroke="#1456D9" stroke-width="2.8" stroke-linecap="round"/>
          <path d="M9 17V12H14M39 31V36H34" stroke="#38BDF8" stroke-width="2.8" stroke-linecap="round"/>
        </svg>`,
      toQr: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="8" y="8" width="13" height="13" rx="3" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <rect x="27" y="8" width="13" height="13" rx="3" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <rect x="8" y="27" width="13" height="13" rx="3" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <path d="M27 27H33.5V33.5H27V27ZM33.5 33.5H40V40H33.5V33.5Z" fill="#FFFFFF" stroke="#061024" stroke-width="2.4"/>
        </svg>`,
      tiktokDl: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M27 9V29.5C27 33.4 23.9 36.5 20 36.5C16.1 36.5 13 33.4 13 29.5C13 25.6 16.1 22.5 20 22.5C21 22.5 21.9 22.7 22.7 23" stroke="#FFFFFF" stroke-width="3.6" stroke-linecap="round"/>
          <path d="M27 9C28.5 14 32 16.8 37 17.3" stroke="#38BDF8" stroke-width="3.6" stroke-linecap="round"/>
          <path d="M35 28L31 33L27 28M31 23V33" stroke="#38BDF8" stroke-width="2.8" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>`,
      qcWa: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M9 13C9 10.8 10.8 9 13 9H35C37.2 9 39 10.8 39 13V28C39 30.2 37.2 32 35 32H20L12 39V32H13C10.8 32 9 30.2 9 28V13Z" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <path d="M16 18H32M16 24H26" stroke="#FFFFFF" stroke-width="2.8" stroke-linecap="round"/>
        </svg>`,
      upscale: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="9" y="18" width="21" height="21" rx="4" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <rect x="18" y="9" width="21" height="21" rx="4" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <path d="M25 23L33 15M33 15H27M33 15V21" stroke="#061024" stroke-width="2.8" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>`,
      remini: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="24" cy="24" r="15" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <path d="M24 13L26.8 21.2L35 24L26.8 26.8L24 35L21.2 26.8L13 24L21.2 21.2L24 13Z" fill="#FFFFFF" stroke="#061024" stroke-width="2.4" stroke-linejoin="round"/>
        </svg>`,
      spotify: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="24" cy="24" r="16" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <path d="M14.5 19.5C20.8 17.6 27.4 18.1 33.5 21.2" stroke="#FFFFFF" stroke-width="2.8" stroke-linecap="round"/>
          <path d="M16 25.2C21.2 23.8 26.7 24.2 31.6 26.7" stroke="#FFFFFF" stroke-width="2.8" stroke-linecap="round"/>
          <path d="M17.5 30.6C21.4 29.6 25.5 29.9 29.2 31.8" stroke="#FFFFFF" stroke-width="2.6" stroke-linecap="round"/>
        </svg>`,
      ytMp4: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="7" y="11" width="34" height="26" rx="7" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <polygon points="21,17.5 31,24 21,30.5" fill="#FFFFFF" stroke="#061024" stroke-width="2.4" stroke-linejoin="round"/>
        </svg>`,
      stalkerFf: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M24 7L37 12.5V24C37 32.8 31.3 39.4 24 41.8C16.7 39.4 11 32.8 11 24V12.5L24 7Z" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <circle cx="24" cy="22" r="5.5" fill="#FFFFFF" stroke="#061024" stroke-width="2.4"/>
          <path d="M16.5 33C18.3 29.8 21 28.4 24 28.4C27 28.4 29.7 29.8 31.5 33" stroke="#FFFFFF" stroke-width="2.4" stroke-linecap="round"/>
        </svg>`,
      stalkerMl: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <polygon points="24,7 41,20 34.5,40 13.5,40 7,20" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <polygon points="24,14 32.5,22 24,34 15.5,22" fill="#FFFFFF" stroke="#061024" stroke-width="2.4" stroke-linejoin="round"/>
        </svg>`,
      stalkerTt: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="21" cy="21" r="10.5" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <circle cx="21" cy="21" r="4.8" fill="#FFFFFF" stroke="#061024" stroke-width="2"/>
          <path d="M29 29L39 39" stroke="#FFFFFF" stroke-width="4.5" stroke-linecap="round"/>
          <path d="M29 29L39 39" stroke="#061024" stroke-width="2.4" stroke-linecap="round"/>
        </svg>`,
      gpt4Mini: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="9" y="11" width="30" height="25" rx="8" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <circle cx="18.5" cy="23" r="3.2" fill="#1456D9"/>
          <circle cx="29.5" cy="23" r="3.2" fill="#1456D9"/>
          <path d="M18.5 30H29.5" stroke="#061024" stroke-width="2.8" stroke-linecap="round"/>
          <path d="M24 6V11" stroke="#38BDF8" stroke-width="3.2" stroke-linecap="round"/>
        </svg>`,
      comicIndo: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M9 11C9 9.3 10.3 8 12 8H24V38H12C10.3 38 9 36.7 9 35V11Z" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <path d="M24 8H36C37.7 8 39 9.3 39 11V35C39 36.7 37.7 38 36 38H24V8Z" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <path d="M13.5 16H19.5M13.5 22H19.5M28.5 16H34.5M28.5 22H34.5" stroke="#061024" stroke-width="2.4" stroke-linecap="round"/>
        </svg>`,
      bgRemove: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="9" y="9" width="30" height="30" rx="7" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <path d="M9 24H39M24 9V39" stroke="#93C5FD" stroke-width="2" stroke-dasharray="3 3"/>
          <path d="M15 32L22 21L27.5 27.5L33 17" stroke="#1456D9" stroke-width="3.2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>`,
      nglSpam: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M10 11H38L33 27H15L10 11Z" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <path d="M16 33.5H32M19.5 39H28.5" stroke="#FFFFFF" stroke-width="3.2" stroke-linecap="round"/>
          <path d="M16 18H32" stroke="#FFFFFF" stroke-width="2.6" stroke-linecap="round"/>
        </svg>`,
      bypassLink: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M18 30L30 18" stroke="#FFFFFF" stroke-width="3.6" stroke-linecap="round"/>
          <path d="M13.5 25L10.5 28C8.3 30.2 8.3 33.8 10.5 36C12.7 38.2 16.3 38.2 18.5 36L21.5 33" stroke="#38BDF8" stroke-width="3.2" stroke-linecap="round"/>
          <path d="M26.5 19L29.5 16C31.7 13.8 35.3 13.8 37.5 16C39.7 18.2 39.7 21.8 37.5 24L34.5 27" stroke="#38BDF8" stroke-width="3.2" stroke-linecap="round"/>
        </svg>`,
      ttqc: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="8" y="10" width="32" height="24" rx="7" fill="#FFFFFF" stroke="#061024" stroke-width="2.8"/>
          <path d="M16 34L12 41L22 34" fill="#38BDF8" stroke="#061024" stroke-width="2.8" stroke-linejoin="round"/>
          <circle cx="16.5" cy="22" r="3.8" fill="#38BDF8" stroke="#061024" stroke-width="2"/>
          <path d="M24 19H33M24 25H30" stroke="#061024" stroke-width="2.6" stroke-linecap="round"/>
        </svg>`,
      nokiaCanvas: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="14" y="6" width="20" height="36" rx="5.5" fill="#38BDF8" stroke="#061024" stroke-width="2.8"/>
          <rect x="18" y="11" width="12" height="11" rx="2" fill="#FFFFFF" stroke="#061024" stroke-width="2.4"/>
          <circle cx="18.5" cy="28" r="1.6" fill="#061024"/>
          <circle cx="24" cy="28" r="1.6" fill="#061024"/>
          <circle cx="29.5" cy="28" r="1.6" fill="#061024"/>
          <circle cx="18.5" cy="34" r="1.6" fill="#061024"/>
          <circle cx="24" cy="34" r="1.6" fill="#061024"/>
          <circle cx="29.5" cy="34" r="1.6" fill="#061024"/>
        </svg>`,
      wmp2: `
        <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="7" y="10" width="34" height="28" rx="6" fill="#0A2458" stroke="#061024" stroke-width="2.8"/>
          <path d="M13 28V20M18.5 32V15M24 30V18M29.5 33V14M35 27V21" stroke="#38BDF8" stroke-width="3.2" stroke-linecap="round"/>
        </svg>`
    };

    // ==================== 20 TOOLS DEFINITION ====================
    const TOOLS = [
      {
        id: "am-prem-send",
        boxTitle: "AM PREM SEND!",
        pageTitle: "AM PREM SEND",
        faIcon: "fa-paper-plane",
        svg: CUSTOM_SVGS.amSend,
        desc: "Kirim link akses / layanan AM Prem menggunakan endpoint API NexaDev secara realtime."
      },
      {
        id: "ig-story-image",
        boxTitle: "IG IMAGE",
        pageTitle: "IG STORY IMAGE",
        faIcon: "fa-instagram",
        svg: CUSTOM_SVGS.igStory,
        desc: "Mockup tampilan Instagram Story lengkap dengan foto, avatar, dan nama pengguna."
      },
      {
        id: "ss-phone",
        boxTitle: "SS PHONE",
        pageTitle: "SS PHONE",
        faIcon: "fa-mobile-screen-button",
        svg: CUSTOM_SVGS.ssPhone,
        desc: "API untuk menangkap tampilan (screenshot) dari halaman situs web secara otomatis dalam bentuk gambar dengan opsi tampilan desktop maupun mobile."
      },
      {
        id: "to-qr",
        boxTitle: "TO QR",
        pageTitle: "URL TO QR",
        faIcon: "fa-qrcode",
        svg: CUSTOM_SVGS.toQr,
        desc: "Mengubah URL menjadi gambar kode QR secara instan."
      },
      {
        id: "tiktok-downloader",
        boxTitle: "TIKTOK DOWNLOADER",
        pageTitle: "TIKTOK DOWNLOADER",
        faIcon: "fa-music",
        svg: CUSTOM_SVGS.tiktokDl,
        desc: "Pengunduhan URL TikTok video MP4 tanpa watermark maupun audio MP3 menggunakan endpoint API."
      },
      {
        id: "qc-wa",
        boxTitle: "QC WA",
        pageTitle: "QCWA",
        faIcon: "fa-comments",
        svg: CUSTOM_SVGS.qcWa,
        desc: "Quote card bergaya chat WhatsApp tanpa lampiran gambar, mendukung mode terang dan gelap."
      },
      {
        id: "upscale-v1",
        boxTitle: "UP SCALE",
        pageTitle: "UPSCALE V1",
        faIcon: "fa-wand-magic-sparkles",
        svg: CUSTOM_SVGS.upscale,
        desc: "API generasi terbaru untuk meng-upscale dan memperjelas resolusi gambar secara instan dengan kustomisasi tingkat perbesaran."
      },
      {
        id: "remini",
        boxTitle: "REMINI",
        pageTitle: "REMINI",
        faIcon: "fa-sparkles",
        svg: CUSTOM_SVGS.remini,
        desc: "API untuk meningkatkan kualitas visual gambar (upscale/HD) dan memperjelas detail foto buram secara otomatis menggunakan teknologi AI Remini."
      },
      {
        id: "spotify",
        boxTitle: "SPOTIFY",
        pageTitle: "SPOTIFY",
        faIcon: "fa-headphones",
        svg: CUSTOM_SVGS.spotify,
        desc: "Mencari lagu Spotify dan memutar audio langsung menggunakan endpoint API resmi."
      },
      {
        id: "yt-mp4",
        boxTitle: "YT MP4",
        pageTitle: "YT MP4 DOWNLOAD",
        faIcon: "fa-circle-play",
        svg: CUSTOM_SVGS.ytMp4,
        desc: "API untuk mengunduh video atau audio dari YouTube dengan kustomisasi tipe media dan pilihan kualitas resolusi (360p, 720p, 1080p)."
      },
      {
        id: "stalker-ff",
        boxTitle: "STALKER FF",
        pageTitle: "STALKER FF",
        faIcon: "fa-crosshairs",
        svg: CUSTOM_SVGS.stalkerFf,
        desc: "API untuk memverifikasi dan mengambil Nickname/In-Game Name (IGN) akun Free Fire berdasarkan User ID secara otomatis. (/api/ff)."
      },
      {
        id: "stalker-ml",
        boxTitle: "STALKER ML",
        pageTitle: "STALKER ML",
        faIcon: "fa-gamepad",
        svg: CUSTOM_SVGS.stalkerMl,
        desc: "API untuk memverifikasi serta mengekstrak Nickname/In-Game Name (IGN) akun Mobile Legends: Bang Bang berdasarkan User ID dan Server/Zone ID. (/api/ml)"
      },
      {
        id: "stalker-tiktok",
        boxTitle: "STALKER TIKTOK",
        pageTitle: "STALKER TIKTOK",
        faIcon: "fa-user-secret",
        svg: CUSTOM_SVGS.stalkerTt,
        desc: "API untuk mengekstrak dan memverifikasi detail profil akun TikTok (User ID, foto profil, statistik followers, following, total suka, hingga bio)."
      },
      {
        id: "gpt4-mini",
        boxTitle: "GPT4 MINI",
        pageTitle: "GPT4 MINI L0ZX",
        faIcon: "fa-robot",
        svg: CUSTOM_SVGS.gpt4Mini,
        desc: "Chat realtime bersama GPT4 Mini AI menggunakan endpoint API NexaDev."
      },
      {
        id: "comic-indo",
        boxTitle: "COMIC INDO",
        pageTitle: "COMIC INDO SEARCH",
        faIcon: "fa-book-open",
        svg: CUSTOM_SVGS.comicIndo,
        desc: "Pencarian komik bahasa Indonesia lengkap dengan sampul, rating, dan tautan baca."
      },
      {
        id: "bg-remove",
        boxTitle: "BG REMOVE",
        pageTitle: "REMOVE BG",
        faIcon: "fa-eraser",
        svg: CUSTOM_SVGS.bgRemove,
        desc: "Menghapus latar belakang gambar secara otomatis dan bersih menggunakan endpoint API."
      },
      {
        id: "ngl-spam",
        boxTitle: "NGL SPAM",
        pageTitle: "SPAM NGL",
        faIcon: "fa-envelope-open-text",
        svg: CUSTOM_SVGS.nglSpam,
        desc: "Kirim pesan bertubi-tubi (spam) ke akun NGL berdasarkan link profil. (/tools/nglspam/)."
      },
      {
        id: "bypass-link",
        boxTitle: "BYPASS LINK",
        pageTitle: "BYPASS LINK",
        faIcon: "fa-link-slash",
        svg: CUSTOM_SVGS.bypassLink,
        desc: "Lewati link pendek otomatis seperti Linkvertise, Safelink, dan shortlink lainnya."
      },
      {
        id: "ttqc",
        boxTitle: "TTQC",
        pageTitle: "TTQC (TIKTOK QUOTE CARD)",
        faIcon: "fa-quote-right",
        svg: CUSTOM_SVGS.ttqc,
        desc: "Buat quote card bergaya tangkapan layar komentar atau chat TikTok."
      },
      {
        id: "nokia-canvas",
        boxTitle: "NOKIA CANVAS",
        pageTitle: "NOKIA CANVAS",
        faIcon: "fa-mobile-retro",
        svg: CUSTOM_SVGS.nokiaCanvas,
        desc: "Mockup layar ponsel legendaris Nokia jadul berisikan SMS kustom."
      },
      {
        id: "wmp2-canvas",
        boxTitle: "WINDOWS PLAYER",
        pageTitle: "WMP2 CANVAS",
        faIcon: "fa-sliders",
        svg: CUSTOM_SVGS.wmp2,
        desc: "Render teks visualisasi audio bergaya Windows Media Player v2 retro. (/wmp2)"
      }
    ];

    // ==================== NAVIGATION & AUTH ====================
    const entryScreen = document.getElementById("entry-screen");
    const loginScreen = document.getElementById("login-screen");
    const dashboardScreen = document.getElementById("dashboard-screen");
    const toolScreen = document.getElementById("tool-screen");

    const bgVideoEntry = document.getElementById("bg-video-entry");
    const dash5gVideo = document.getElementById("dash-5g-video");
    bgVideoEntry.muted = true;
    dash5gVideo.muted = true;

    function showScreen(target) {
      [loginScreen, dashboardScreen, toolScreen].forEach(s => s.classList.remove("active"));
      entryScreen.classList.remove("active");
      if (target === "entry") {
        entryScreen.classList.add("active");
      } else {
        target.classList.add("active");
      }
      window.scrollTo({ top: 0, behavior: "instant" });
    }

    document.getElementById("press-to-enter-btn").addEventListener("click", () => {
      showScreen(loginScreen);
    });

    const VALID_USN = "lozxxdev";
    const VALID_PW = "lozxx403";

    document.getElementById("login-form").addEventListener("submit", (e) => {
      e.preventDefault();
      const usn = document.getElementById("login-usn").value.trim();
      const pw = document.getElementById("login-pw").value;
      const errEl = document.getElementById("login-error");

      if (!usn || !pw) {
        errEl.textContent = "Username dan Password wajib diisi keduanya!";
        errEl.classList.add("show");
        return;
      }

      if (usn !== VALID_USN || pw !== VALID_PW) {
        errEl.textContent = "Username atau Password salah! Periksa kembali kredensial Anda.";
        errEl.classList.add("show");
        return;
      }

      errEl.classList.remove("show");
      document.getElementById("active-user-label").textContent = usn;
      showScreen(dashboardScreen);
      initSlimeScrollObserver();
    });

    document.getElementById("logout-btn").addEventListener("click", () => {
      document.getElementById("login-form").reset();
      showScreen(loginScreen);
    });

    document.getElementById("back-to-dashboard-btn").addEventListener("click", () => {
      const audioEl = document.getElementById("spotify-audio-player");
      if (audioEl) {
        audioEl.pause();
      }
      showScreen(dashboardScreen);
      initSlimeScrollObserver();
    });

    // ==================== RENDER DASHBOARD VIEW BOXES ====================
    const toolsGrid = document.getElementById("tools-grid");

    function renderDashboardBoxes() {
      toolsGrid.innerHTML = "";
      TOOLS.forEach((tool, idx) => {
        const box = document.createElement("button");
        box.type = "button";
        box.className = "tool-view-box slime-reveal";
        box.style.transitionDelay = `${(idx % 4) * 50}ms`;
        box.innerHTML = `
          <div class="svg-icon-frame">${tool.svg}</div>
          <div>
            <div class="tool-box-title">${escapeHtml(tool.boxTitle)}</div>
            <div class="tool-box-desc">${escapeHtml(tool.desc)}</div>
          </div>
          <span class="tool-box-cta">
            BUKA TOOL <i class="fa-solid fa-arrow-up-right-from-square"></i>
          </span>
        `;
        box.addEventListener("click", () => openToolPage(tool));
        toolsGrid.appendChild(box);
      });
    }

    let slimeObserver = null;
    function initSlimeScrollObserver() {
      if (slimeObserver) slimeObserver.disconnect();
      const cards = document.querySelectorAll(".slime-reveal");

      slimeObserver = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("slime-visible");
          } else if (entry.boundingClientRect.top > window.innerHeight * 0.85) {
            entry.target.classList.remove("slime-visible");
          }
        });
      }, {
        threshold: 0.12,
        rootMargin: "0px 0px -25px 0px"
      });

      cards.forEach((card) => {
        const rect = card.getBoundingClientRect();
        if (rect.top < window.innerHeight * 0.92) {
          card.classList.add("slime-visible");
        }
        slimeObserver.observe(card);
      });
    }

    renderDashboardBoxes();

    // ==================== HELPERS ====================
    function escapeHtml(str = "") {
      return String(str)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;");
    }

    async function readFileAsDataUrl(file) {
      return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = () => resolve(reader.result);
        reader.onerror = reject;
        reader.readAsDataURL(file);
      });
    }

    function setLoadingResult(container, label = "Memproses permintaan ke API...") {
      container.innerHTML = `
        <div class="result-box">
          <div class="result-tag">
            <i class="fa-solid fa-spinner fa-spin"></i> ${escapeHtml(label)}
          </div>
        </div>
      `;
    }

    function setErrorResult(container, msg) {
      container.innerHTML = `
        <div class="result-box">
          <div class="result-tag" style="background:#fee2e2;color:#991b1b;">
            <i class="fa-solid fa-triangle-exclamation"></i> GAGAL / ERROR
          </div>
          <p style="margin-top: 10px; font-weight: 700; color: #991b1b;">${escapeHtml(msg)}</p>
        </div>
      `;
    }

    async function fetchBinaryImageObjectUrl(endpointUrl) {
      const res = await fetch(endpointUrl);
      if (!res.ok) {
        throw new Error(`HTTP ${res.status} saat mengambil gambar dari API.`);
      }
      const contentType = res.headers.get("content-type") || "";
      if (contentType.includes("application/json")) {
        const json = await res.json();
        if (json.data?.url) {
          return json.data.url;
        }
        throw new Error(json.message || "API mengembalikan JSON tanpa gambar.");
      }
      const blob = await res.blob();
      return URL.createObjectURL(blob);
    }

    function renderImageDownloadResult(container, imgSrc, filename, topLeftButton = false) {
      container.innerHTML = `
        <div class="result-box">
          <div class="result-header-row">
            <span class="result-tag"><i class="fa-solid fa-circle-check"></i> BERHASIL DI-GENERATE</span>
            <a class="download-action-btn" href="${imgSrc}" download="${escapeHtml(filename)}">
              <i class="fa-solid fa-download"></i> DOWNLOAD GAMBAR
            </a>
          </div>
          <div class="preview-img-wrap">
            ${topLeftButton ? `
              <a class="top-left-dl-badge" href="${imgSrc}" download="${escapeHtml(filename)}">
                <i class="fa-solid fa-download"></i> UNDUH
              </a>
            ` : ""}
            <img class="output-media-img" src="${imgSrc}" alt="Hasil Generate" />
          </div>
        </div>
      `;
    }

    // ==================== OPEN INDIVIDUAL TOOL PAGE ====================
    function openToolPage(tool) {
      const titleEl = document.getElementById("active-tool-title");
      const descEl = document.getElementById("active-tool-desc");
      const formArea = document.getElementById("active-tool-form-area");
      const resultArea = document.getElementById("active-tool-result-area");

      titleEl.innerHTML = `
        <span class="svg-icon-frame" style="width:44px;height:44px;border-radius:11px;">${tool.svg}</span>
        <span>${escapeHtml(tool.pageTitle)}</span>
        <i class="fa-solid ${escapeHtml(tool.faIcon)} fa-3d-comic" style="font-size:1.25rem;"></i>
      `;
      descEl.textContent = tool.desc;
      formArea.innerHTML = "";
      resultArea.innerHTML = "";

      showScreen(toolScreen);
      buildToolInterface(tool, formArea, resultArea);
    }

    // ==================== ALL 20 TOOL IMPLEMENTATIONS ====================
    function buildToolInterface(tool, formArea, resultArea) {
      switch (tool.id) {
        case "am-prem-send": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">API KEY</label>
                <input id="am-key" class="comic-input" type="text" value="RS-rL6J%25cpp" />
              </div>
              <div class="field-group">
                <label class="field-label">EMAIL TARGET</label>
                <input id="am-email" class="comic-input" type="email" value="valszkwui@gmail.com" placeholder="nama@email.com" />
              </div>
            </div>
            <button id="am-send-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-paper-plane"></i> KIRIM AM PREM SEND
            </button>
          `;
          document.getElementById("am-send-btn").addEventListener("click", async () => {
            const keyVal = encodeURIComponent(document.getElementById("am-key").value.trim());
            const emailVal = encodeURIComponent(document.getElementById("am-email").value.trim());
            if (!emailVal) return setErrorResult(resultArea, "Email wajib diisi.");
            setLoadingResult(resultArea, "Mengirim request ke AM Prem Send...");
            try {
              const url = `https://api.nexadev.my.id/am/send/?key=${keyVal}&email=${emailVal}`;
              const res = await fetch(url);
              const data = await res.json();
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-header-row">
                    <span class="result-tag"><i class="fa-solid fa-check-double"></i> ${escapeHtml(data.message || "Respons Diterima")}</span>
                    <span class="session-pill">Status: ${data.status ? "TRUE" : "FALSE"}</span>
                  </div>
                  <pre class="json-pre">${escapeHtml(JSON.stringify(data, null, 2))}</pre>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "ig-story-image": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">USN (USERNAME)</label>
                <input id="ig-usn" class="comic-input" type="text" value="vlzznotdev" placeholder="Masukkan username..." />
              </div>
              <div class="field-group">
                <label class="field-label">NAME</label>
                <input id="ig-name" class="comic-input" type="text" value="L0ZXX" placeholder="Masukkan nama..." />
              </div>
              <div class="field-group">
                <label class="field-label">PHOTO URL</label>
                <input id="ig-photo" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/jaoCqc.jpeg" />
              </div>
              <div class="field-group">
                <label class="field-label">AVATAR URL</label>
                <input id="ig-avatar" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/Mbasnl.jpeg" />
              </div>
            </div>
            <button id="ig-gen-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-image"></i> GENERATE IG STORY IMAGE
            </button>
          `;
          document.getElementById("ig-gen-btn").addEventListener("click", async () => {
            const usn = encodeURIComponent(document.getElementById("ig-usn").value.trim());
            const name = encodeURIComponent(document.getElementById("ig-name").value.trim());
            const photo = encodeURIComponent(document.getElementById("ig-photo").value.trim());
            const avatar = encodeURIComponent(document.getElementById("ig-avatar").value.trim());
            if (!usn || !name) return setErrorResult(resultArea, "USN dan NAME wajib diisi.");
            setLoadingResult(resultArea, "Merender IG Story Image...");
            try {
              const apiUrl = `https://api.nexadev.my.id/igstory-img?photo=${photo}&avatar=${avatar}&usn=${usn}&name=${name}`;
              const imgSrc = await fetchBinaryImageObjectUrl(apiUrl);
              renderImageDownloadResult(resultArea, imgSrc, `igstory_${Date.now()}.png`, true);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "ss-phone": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">MASUKAN URL WEBSITE</label>
                <input id="ss-url" class="comic-input" type="url" value="https://api.nexadev.my.id" placeholder="https://contoh.com" />
              </div>
              <div class="field-group">
                <label class="field-label">TIPE DEVICE</label>
                <select id="ss-device" class="comic-select">
                  <option value="phone" selected>Phone (Mobile)</option>
                  <option value="desktop">Desktop</option>
                </select>
              </div>
            </div>
            <button id="ss-gen-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-camera"></i> AMBIL SCREENSHOT
            </button>
          `;
          document.getElementById("ss-gen-btn").addEventListener("click", async () => {
            const rawUrl = document.getElementById("ss-url").value.trim();
            const device = document.getElementById("ss-device").value;
            if (!rawUrl) return setErrorResult(resultArea, "URL wajib diisi.");
            setLoadingResult(resultArea, "Menangkap screenshot situs web...");
            try {
              const endpoint = `https://api.nexadev.my.id/api/ss?url=${encodeURIComponent(rawUrl)}&device=${encodeURIComponent(device)}`;
              const res = await fetch(endpoint);
              const data = await res.json();
              const imgUrl = data?.data?.url;
              if (!data.status || !imgUrl) {
                throw new Error(data.message || "Gagal mendapatkan URL hasil screenshot.");
              }
              renderImageDownloadResult(resultArea, imgUrl, `ss_${device}_${Date.now()}.jpeg`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "to-qr": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">MASUKAN URL</label>
              <input id="qr-url" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/ISsVGW.jpg" placeholder="https://..." />
            </div>
            <button id="qr-gen-btn" class="comic-btn secondary" type="button">
              <i class="fa-solid fa-qrcode"></i> GENERATE QR CODE
            </button>
          `;
          document.getElementById("qr-gen-btn").addEventListener("click", async () => {
            const rawUrl = document.getElementById("qr-url").value.trim();
            if (!rawUrl) return setErrorResult(resultArea, "URL wajib diisi.");
            setLoadingResult(resultArea, "Membuat gambar QR...");
            try {
              const endpoint = `https://api.nexadev.my.id/tools/toqr?url=${encodeURIComponent(rawUrl)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `qr_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "tiktok-downloader": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">MASUKAN URL TIKTOK</label>
                <input id="tt-url" class="comic-input" type="url" value="https://vt.tiktok.com/ZSsFvXSvq/" placeholder="https://vt.tiktok.com/..." />
              </div>
              <div class="field-group">
                <label class="field-label">PILIH OPSI MEDIA</label>
                <select id="tt-mode" class="comic-select">
                  <option value="video" selected>MP4 Video (No Watermark)</option>
                  <option value="audio">MP3 Sound / Audio</option>
                </select>
              </div>
            </div>
            <button id="tt-dl-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-download"></i> PROSES TIKTOK
            </button>
          `;
          document.getElementById("tt-dl-btn").addEventListener("click", async () => {
            const rawUrl = document.getElementById("tt-url").value.trim();
            const mode = document.getElementById("tt-mode").value;
            if (!rawUrl) return setErrorResult(resultArea, "URL TikTok wajib diisi.");
            setLoadingResult(resultArea, "Mengambil data video/audio TikTok...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/api/snaptik/?url=${encodeURIComponent(rawUrl)}`);
              const data = await res.json();
              if (!data.status || !Array.isArray(data.download_links)) {
                throw new Error(data.message || "Gagal mengambil tautan unduhan TikTok.");
              }

              const filteredLinks = data.download_links.filter(item => {
                const t = (item.type || "").toLowerCase();
                return mode === "audio"
                  ? (t.includes("mp3") || t.includes("audio") || t.includes("sound"))
                  : (t.includes("mp4") || t.includes("video"));
              });
              const displayLinks = filteredLinks.length ? filteredLinks : data.download_links;

              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-tag"><i class="fa-solid fa-check"></i> ${escapeHtml(data.title || "TikTok Media Siap")}</div>
                  ${data.thumbnail ? `<div style="margin-top:14px;"><img src="${escapeHtml(data.thumbnail)}" class="output-media-img" style="max-height:240px;" alt="Thumbnail" /></div>` : ""}
                  <div style="display:flex;flex-wrap:wrap;gap:12px;margin-top:16px;">
                    ${displayLinks.map((lnk, idx) => `
                      <a class="download-action-btn" href="${escapeHtml(lnk.url)}" target="_blank" rel="noopener noreferrer" download>
                        <i class="fa-solid fa-file-arrow-down"></i> ${escapeHtml(lnk.type || `Unduh Opsi ${idx + 1}`)}
                      </a>
                    `).join("")}
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "qc-wa": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">NUMBER PHONE</label>
                <input id="qc-phone" class="comic-input" type="text" value="6289601261574" />
              </div>
              <div class="field-group">
                <label class="field-label">USN</label>
                <input id="qc-usn" class="comic-input" type="text" value="VLZZZ G4T3NKH KATA EMAK" />
              </div>
              <div class="field-group">
                <label class="field-label">MODE (LIGHT / DARK)</label>
                <select id="qc-mode" class="comic-select">
                  <option value="light" selected>light</option>
                  <option value="dark">dark</option>
                </select>
              </div>
              <div class="field-group">
                <label class="field-label">TAG</label>
                <input id="qc-tag" class="comic-input" type="text" value="ambaa tukammm" />
              </div>
              <div class="field-group">
                <label class="field-label">PROFILE PICTURE URL</label>
                <input id="qc-pp" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/BJLnsy.png" />
              </div>
            </div>
            <div class="field-group">
              <label class="field-label">TEXT QUOTE</label>
              <textarea id="qc-text" class="comic-textarea">ngapain bersaing kalo sainganya ga pantes</textarea>
            </div>
            <button id="qc-gen-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-comment-dots"></i> GENERATE QCWA
            </button>
          `;
          document.getElementById("qc-gen-btn").addEventListener("click", async () => {
            const phone = document.getElementById("qc-phone").value.trim();
            const usn = document.getElementById("qc-usn").value.trim();
            const text = document.getElementById("qc-text").value.trim();
            const mode = document.getElementById("qc-mode").value;
            const tag = document.getElementById("qc-tag").value.trim();
            const pp = document.getElementById("qc-pp").value.trim();
            if (!text) return setErrorResult(resultArea, "Text quote wajib diisi.");
            setLoadingResult(resultArea, "Membuat Quote Card WhatsApp...");
            try {
              const url = `https://api.nexadev.my.id/qcwa?usn=${encodeURIComponent(usn)}&phone=${encodeURIComponent(phone)}&pp=${encodeURIComponent(pp)}&text=${encodeURIComponent(text)}&mode=${encodeURIComponent(mode)}&tag=${encodeURIComponent(tag)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(url);
              renderImageDownloadResult(resultArea, imgSrc, `qcwa_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "upscale-v1": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">UPLOAD GAMBAR FILE</label>
                <input id="up-file" class="comic-input" type="file" accept="image/*" />
              </div>
              <div class="field-group">
                <label class="field-label">RESOLUSI (PERBESARAN)</label>
                <select id="up-res" class="comic-select">
                  <option value="2">2x</option>
                  <option value="4" selected>4x</option>
                </select>
              </div>
            </div>
            <div class="field-group">
              <label class="field-label">ATAU URL GAMBAR</label>
              <input id="up-url" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/QdhzJe.jpg" />
            </div>
            <button id="up-gen-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-up-right-and-down-left-from-center"></i> GENERATE UPSCALE V1
            </button>
          `;
          document.getElementById("up-gen-btn").addEventListener("click", async () => {
            const fileInput = document.getElementById("up-file");
            const resVal = document.getElementById("up-res").value;
            let targetUrl = document.getElementById("up-url").value.trim();

            if (fileInput.files && fileInput.files[0]) {
              targetUrl = await readFileAsDataUrl(fileInput.files[0]);
            }
            if (!targetUrl) return setErrorResult(resultArea, "Upload file gambar atau masukkan URL gambar.");

            setLoadingResult(resultArea, "Meng-upscale gambar...");
            try {
              const endpoint = `https://api.nexadev.my.id/api/upscale1?url=${encodeURIComponent(targetUrl)}&resolusi=${encodeURIComponent(resVal)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `upscale_${resVal}x_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "remini": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">UPLOAD IMAGE</label>
              <input id="rem-file" class="comic-input" type="file" accept="image/*" />
            </div>
            <div class="field-group">
              <label class="field-label">ATAU URL IMAGE</label>
              <input id="rem-url" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/tpRbqq.jpg" />
            </div>
            <button id="rem-gen-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-wand-sparkles"></i> GENERATE REMINI HD
            </button>
          `;
          document.getElementById("rem-gen-btn").addEventListener("click", async () => {
            const fileInput = document.getElementById("rem-file");
            let targetUrl = document.getElementById("rem-url").value.trim();
            if (fileInput.files && fileInput.files[0]) {
              targetUrl = await readFileAsDataUrl(fileInput.files[0]);
            }
            if (!targetUrl) return setErrorResult(resultArea, "Upload image atau masukkan URL image.");
            setLoadingResult(resultArea, "Memperjelas foto dengan AI Remini...");
            try {
              const endpoint = `https://api.nexadev.my.id/api/remini?url=${encodeURIComponent(targetUrl)}`;
              const res = await fetch(endpoint);
              const data = await res.json();
              const outUrl = data?.data?.url;
              if (!data.status || !outUrl) throw new Error(data.message || "Gagal memproses gambar Remini.");
              renderImageDownloadResult(resultArea, outUrl, `remini_hd_${Date.now()}.jpg`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "spotify": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">CARI JUDUL LAGU / ARTIS SPOTIFY</label>
              <div style="display:flex;gap:10px;flex-wrap:wrap;">
                <input id="sp-query" class="comic-input" style="flex:1;min-width:220px;" type="text" value="separuh aku" placeholder="Ketik judul lagu..." />
                <button id="sp-search-btn" class="comic-btn" style="width:auto;padding:12px 24px;" type="button">
                  <i class="fa-solid fa-magnifying-glass"></i> CARI LAGU
                </button>
              </div>
            </div>
          `;
          document.getElementById("sp-search-btn").addEventListener("click", async () => {
            const q = document.getElementById("sp-query").value.trim();
            if (!q) return setErrorResult(resultArea, "Masukkan kata kunci lagu.");
            setLoadingResult(resultArea, "Mencari lagu di Spotify API...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/api/spotifyplay?q=${encodeURIComponent(q)}`);
              const data = await res.json();
              const track = data?.data;
              if (!data.status || !track?.mp3_url) {
                throw new Error(data.message || "Lagu tidak ditemukan.");
              }

              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-tag"><i class="fa-solid fa-music"></i> LAGU DITEMUKAN — KLIK PLAY UNTUK MEMUTAR</div>
                  <div class="spotify-track-card" style="margin-top:14px;">
                    <img id="sp-disc" class="vinyl-disc" src="${escapeHtml(track.cover)}" alt="Cover" />
                    <div style="flex:1;min-width:220px;">
                      <div style="display:inline-flex;align-items:center;gap:6px;background:#fff;border:2px solid var(--ink);border-radius:8px;padding:3px 9px;font-size:0.78rem;font-weight:700;">
                        <i class="fa-solid fa-circle-user"></i> ${escapeHtml(track.artist || "Artist")} • ${escapeHtml(track.duration || "")}
                      </div>
                      <h3 class="display-title" style="font-size:1.35rem;color:var(--navy-dark);margin-top:8px;">
                        ${escapeHtml(track.title)}
                      </h3>
                      <p style="font-weight:700;font-size:0.86rem;color:#264273;margin-bottom:10px;">
                        Album: ${escapeHtml(track.album || "-")} (${escapeHtml(String(track.year || ""))})
                      </p>
                      <audio id="spotify-audio-player" controls style="width:100%;">
                        <source src="${escapeHtml(track.mp3_url)}" type="audio/mpeg" />
                      </audio>
                    </div>
                  </div>
                </div>
              `;

              const audio = document.getElementById("spotify-audio-player");
              const disc = document.getElementById("sp-disc");
              audio.addEventListener("play", () => disc.classList.add("spinning"));
              audio.addEventListener("pause", () => disc.classList.remove("spinning"));
              audio.addEventListener("ended", () => disc.classList.remove("spinning"));
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "yt-mp4": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">URL YOUTUBE</label>
                <input id="yt-url" class="comic-input" type="url" value="https://youtu.be/gQmLrZw5Jlg?si=LZWsf2kY90HG9nEo" />
              </div>
              <div class="field-group">
                <label class="field-label">TIPE MEDIA</label>
                <select id="yt-type" class="comic-select">
                  <option value="video" selected>video</option>
                  <option value="audio">audio</option>
                </select>
              </div>
              <div class="field-group">
                <label class="field-label">UKURAN / KUALITAS VIDEO</label>
                <select id="yt-quality" class="comic-select">
                  <option value="360p">360p</option>
                  <option value="720p" selected>720p</option>
                  <option value="1080p">1080p</option>
                </select>
              </div>
            </div>
            <button id="yt-gen-btn" class="comic-btn dark-blue" type="button">
              <i class="fa-solid fa-video"></i> PROSES YT MP4
            </button>
          `;
          document.getElementById("yt-gen-btn").addEventListener("click", async () => {
            const urlVal = document.getElementById("yt-url").value.trim();
            const typeVal = document.getElementById("yt-type").value;
            const qualVal = document.getElementById("yt-quality").value;
            if (!urlVal) return setErrorResult(resultArea, "URL YouTube wajib diisi.");
            setLoadingResult(resultArea, "Mengambil link unduhan YouTube...");
            try {
              const endpoint = `https://api.nexadev.my.id/api/ytmp4?url=${encodeURIComponent(urlVal)}&type=${encodeURIComponent(typeVal)}&quality=${encodeURIComponent(qualVal)}`;
              const res = await fetch(endpoint);
              const data = await res.json();
              const dlUrl = data?.data?.url;
              if (!data.status || !dlUrl) {
                throw new Error(data.message || "Gagal memproses video YouTube.");
              }
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-header-row">
                    <span class="result-tag"><i class="fa-solid fa-circle-check"></i> ${escapeHtml(data.title || "Video Siap")}</span>
                    <a class="download-action-btn" href="${escapeHtml(dlUrl)}" target="_blank" rel="noopener noreferrer" download="${escapeHtml(data?.data?.filename || "youtube_download.mp4")}">
                      <i class="fa-solid fa-download"></i> DOWNLOAD / SIMPAN (${escapeHtml(data?.data?.quality || qualVal)})
                    </a>
                  </div>
                  ${data.thumbnail ? `<img src="${escapeHtml(data.thumbnail)}" class="output-media-img" style="max-height:260px;" alt="YT Thumb" />` : ""}
                  <div class="stat-pills-grid">
                    <div class="stat-mini-box"><div class="stat-mini-label">Channel</div><div class="stat-mini-val">${escapeHtml(data.channel || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Durasi</div><div class="stat-mini-val">${escapeHtml(data.fduration || data.duration || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Views</div><div class="stat-mini-val">${escapeHtml(data.views || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Ukuran</div><div class="stat-mini-val">${escapeHtml(data?.data?.size || "-")}</div></div>
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "stalker-ff": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">USER ID FREE FIRE (UID)</label>
              <input id="ff-uid" class="comic-input" type="text" value="7606762852" placeholder="Contoh: 7606762852" />
            </div>
            <button id="ff-check-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-crosshairs"></i> CEK AKUN FREE FIRE
            </button>
          `;
          document.getElementById("ff-check-btn").addEventListener("click", async () => {
            const uid = document.getElementById("ff-uid").value.trim();
            if (!uid) return setErrorResult(resultArea, "UID Free Fire wajib diisi.");
            setLoadingResult(resultArea, "Mengambil data profil Free Fire...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/api/ff?id=${encodeURIComponent(uid)}`);
              const data = await res.json();
              const p = data?.profile;
              if (!data.ok || !p) throw new Error(data.message || "Akun FF tidak ditemukan.");
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-header-row">
                    <span class="result-tag"><i class="fa-solid fa-user-check"></i> ${escapeHtml(p.nickname)}</span>
                    <span class="session-pill">UID: ${escapeHtml(p.uid)}</span>
                  </div>
                  ${p.avatar?.url ? `<img src="${escapeHtml(p.avatar.url)}" class="output-media-img" style="max-width:130px;max-height:130px;" alt="FF Avatar" />` : ""}
                  <div class="stat-pills-grid">
                    <div class="stat-mini-box"><div class="stat-mini-label">Nickname</div><div class="stat-mini-val">${escapeHtml(p.nickname)}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Level</div><div class="stat-mini-val">${escapeHtml(String(p.level))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Likes</div><div class="stat-mini-val">${escapeHtml(String(p.likesText || p.likes))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Server</div><div class="stat-mini-val">${escapeHtml(p.server || p.region || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">CS Rank</div><div class="stat-mini-val">${escapeHtml(p.ranks?.cs?.tier || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Clan</div><div class="stat-mini-val">${escapeHtml(p.clan?.name || "-")}</div></div>
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "stalker-ml": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">USER ID MLBB</label>
                <input id="ml-id" class="comic-input" type="text" value="134972929" />
              </div>
              <div class="field-group">
                <label class="field-label">SERVER / ZONE ID</label>
                <input id="ml-zone" class="comic-input" type="text" value="2687" />
              </div>
            </div>
            <button id="ml-check-btn" class="comic-btn secondary" type="button">
              <i class="fa-solid fa-gamepad"></i> CEK NICKNAME MLBB
            </button>
          `;
          document.getElementById("ml-check-btn").addEventListener("click", async () => {
            const idVal = document.getElementById("ml-id").value.trim();
            const zoneVal = document.getElementById("ml-zone").value.trim();
            if (!idVal || !zoneVal) return setErrorResult(resultArea, "User ID dan Zone ID wajib diisi.");
            setLoadingResult(resultArea, "Mengecek akun Mobile Legends...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/api/ml?id=${encodeURIComponent(idVal)}&zone=${encodeURIComponent(zoneVal)}`);
              const data = await res.json();
              if (!data.status || !data?.data?.username) {
                throw new Error(data.message || "Akun MLBB tidak ditemukan.");
              }
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-tag"><i class="fa-solid fa-circle-check"></i> AKUN DITEMUKAN</div>
                  <div class="stat-pills-grid">
                    <div class="stat-mini-box"><div class="stat-mini-label">Username / IGN</div><div class="stat-mini-val">${escapeHtml(data.data.username)}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Region</div><div class="stat-mini-val">${escapeHtml(data.data.region || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">ID (Zone)</div><div class="stat-mini-val">${escapeHtml(idVal)} (${escapeHtml(zoneVal)})</div></div>
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "stalker-tiktok": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">USERNAME TIKTOK</label>
              <input id="ttst-user" class="comic-input" type="text" value="L0ZXX" placeholder="Tanpa @" />
            </div>
            <button id="ttst-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-user-secret"></i> STALK PROFIL TIKTOK
            </button>
          `;
          document.getElementById("ttst-btn").addEventListener("click", async () => {
            const username = document.getElementById("ttst-user").value.trim().replace(/^@/, "");
            if (!username) return setErrorResult(resultArea, "Username TikTok wajib diisi.");
            setLoadingResult(resultArea, "Mengambil profil TikTok...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/api/tiktokstalker?username=${encodeURIComponent(username)}`);
              const data = await res.json();
              const d = data?.data;
              if (!data.status || !d) throw new Error(data.message || "Profil TikTok tidak ditemukan.");
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-header-row">
                    <span class="result-tag"><i class="fa-solid fa-user"></i> @${escapeHtml(d.username)}</span>
                    <span class="session-pill">ID: ${escapeHtml(String(d.id || "-"))}</span>
                  </div>
                  ${d.photo ? `<img src="${escapeHtml(d.photo)}" class="output-media-img" style="max-width:130px;max-height:130px;border-radius:50%;" alt="TT Avatar" />` : ""}
                  <div class="stat-pills-grid">
                    <div class="stat-mini-box"><div class="stat-mini-label">Nama</div><div class="stat-mini-val">${escapeHtml(d.name || "-")}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Followers</div><div class="stat-mini-val">${escapeHtml(String(d.followers ?? 0))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Following</div><div class="stat-mini-val">${escapeHtml(String(d.following ?? 0))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Total Likes</div><div class="stat-mini-val">${escapeHtml(String(d.likes ?? 0))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Posts</div><div class="stat-mini-val">${escapeHtml(String(d.posts ?? 0))}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Bio</div><div class="stat-mini-val">${escapeHtml(d.bio || "-")}</div></div>
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "gpt4-mini": {
          formArea.innerHTML = `
            <div id="gpt-chat-box" class="chat-history-box">
              <div class="chat-bubble ai">Halo! Silakan ketik pesan apa saja untuk ngobrol langsung dengan GPT4 Mini L0ZX.</div>
            </div>
            <div style="display:flex;gap:10px;flex-wrap:wrap;">
              <input id="gpt-input" class="comic-input" style="flex:1;min-width:220px;" type="text" placeholder="Tulis pesan kamu di sini..." />
              <button id="gpt-send-btn" class="comic-btn" style="width:auto;padding:12px 24px;" type="button">
                <i class="fa-solid fa-paper-plane"></i> SEND
              </button>
            </div>
          `;
          const chatBox = document.getElementById("gpt-chat-box");
          const inputEl = document.getElementById("gpt-input");
          const sendBtn = document.getElementById("gpt-send-btn");

          async function sendChat() {
            const msg = inputEl.value.trim();
            if (!msg) return;
            inputEl.value = "";

            const userBubble = document.createElement("div");
            userBubble.className = "chat-bubble user";
            userBubble.textContent = msg;
            chatBox.appendChild(userBubble);

            const aiBubble = document.createElement("div");
            aiBubble.className = "chat-bubble ai";
            aiBubble.innerHTML = `<i class="fa-solid fa-spinner fa-spin"></i> Mengetik balasan...`;
            chatBox.appendChild(aiBubble);
            chatBox.scrollTop = chatBox.scrollHeight;

            try {
              const res = await fetch(`https://api.nexadev.my.id/ai/gpt4?q=${encodeURIComponent(msg)}`);
              const data = await res.json();
              aiBubble.textContent = data?.data?.message || data?.message || "Tidak ada balasan dari AI.";
            } catch (err) {
              aiBubble.textContent = "Error: " + err.message;
            }
            chatBox.scrollTop = chatBox.scrollHeight;
          }

          sendBtn.addEventListener("click", sendChat);
          inputEl.addEventListener("keydown", (e) => {
            if (e.key === "Enter") sendChat();
          });
          break;
        }

        case "comic-indo": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">CARI JUDUL KOMIK INDO</label>
              <div style="display:flex;gap:10px;flex-wrap:wrap;">
                <input id="komik-q" class="comic-input" style="flex:1;min-width:220px;" type="text" value="nano" placeholder="Contoh: nano, solo, isekai..." />
                <button id="komik-search-btn" class="comic-btn" style="width:auto;padding:12px 24px;" type="button">
                  <i class="fa-solid fa-book-open"></i> CARI KOMIK
                </button>
              </div>
            </div>
          `;
          document.getElementById("komik-search-btn").addEventListener("click", async () => {
            const q = document.getElementById("komik-q").value.trim();
            if (!q) return setErrorResult(resultArea, "Masukkan kata kunci komik.");
            setLoadingResult(resultArea, "Mencari daftar komik...");
            try {
              const res = await fetch(`https://api.nexadev.my.id/komik?q=${encodeURIComponent(q)}`);
              const data = await res.json();
              const list = data?.results || [];
              if (!data.success || !list.length) {
                throw new Error(data.message || "Komik tidak ditemukan.");
              }
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-tag"><i class="fa-solid fa-layer-group"></i> DITEMUKAN ${list.length} KOMIK</div>
                  <div class="comic-results-grid">
                    ${list.map(item => `
                      <div class="komik-card">
                        <div>
                          <img src="${escapeHtml(item.cover || "")}" alt="${escapeHtml(item.title)}" onerror="this.style.display='none'" />
                          <div style="font-weight:700;font-size:0.88rem;margin-top:8px;color:var(--navy-dark);">${escapeHtml(item.title)}</div>
                          <div style="font-size:0.78rem;font-weight:700;color:#264273;margin-top:4px;">
                            <i class="fa-solid fa-star" style="color:var(--blue-vivid);"></i> Rating: ${escapeHtml(String(item.rating || "-"))}
                          </div>
                        </div>
                        <a class="download-action-btn" style="justify-content:center;" href="${escapeHtml(item.link)}" target="_blank" rel="noopener noreferrer">
                          <i class="fa-solid fa-book-reader"></i> MULAI MEMBACA
                        </a>
                      </div>
                    `).join("")}
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "bg-remove": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">UPLOAD FILE GAMBAR</label>
              <input id="rmbg-file" class="comic-input" type="file" accept="image/*" />
            </div>
            <div class="field-group">
              <label class="field-label">ATAU URL GAMBAR</label>
              <input id="rmbg-url" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/iTOxYD.jpg" />
            </div>
            <button id="rmbg-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-eraser"></i> HAPUS BACKGROUND
            </button>
          `;
          document.getElementById("rmbg-btn").addEventListener("click", async () => {
            const fileInput = document.getElementById("rmbg-file");
            let targetUrl = document.getElementById("rmbg-url").value.trim();
            if (fileInput.files && fileInput.files[0]) {
              targetUrl = await readFileAsDataUrl(fileInput.files[0]);
            }
            if (!targetUrl) return setErrorResult(resultArea, "Upload file atau masukkan URL gambar.");
            setLoadingResult(resultArea, "Membersihkan latar belakang gambar...");
            try {
              const endpoint = `https://api.nexadev.my.id/tools/remove/?url=${encodeURIComponent(targetUrl)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `nobg_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "ngl-spam": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">URL NGL PROFIL</label>
                <input id="ngl-url" class="comic-input" type="url" value="https://ngl.link/vlzz" />
              </div>
              <div class="field-group">
                <label class="field-label">LINK / USERNAME</label>
                <input id="ngl-user" class="comic-input" type="text" value="vlzz" placeholder="Username NGL" />
              </div>
              <div class="field-group">
                <label class="field-label">PESAN</label>
                <input id="ngl-msg" class="comic-input" type="text" value="haiiiii" />
              </div>
              <div class="field-group">
                <label class="field-label">JUMLAH SPAM</label>
                <input id="ngl-count" class="comic-input" type="number" min="1" max="200" value="5" />
              </div>
            </div>
            <button id="ngl-run-btn" class="comic-btn dark-blue" type="button">
              <i class="fa-solid fa-bolt"></i> JALANKAN SPAM NGL
            </button>
          `;
          document.getElementById("ngl-run-btn").addEventListener("click", async () => {
            const rawUrl = document.getElementById("ngl-url").value.trim();
            const msg = document.getElementById("ngl-msg").value.trim();
            const count = Math.max(1, parseInt(document.getElementById("ngl-count").value, 10) || 1);
            if (!rawUrl || !msg) return setErrorResult(resultArea, "URL dan pesan wajib diisi.");

            resultArea.innerHTML = `
              <div class="result-box">
                <div class="result-tag"><i class="fa-solid fa-terminal"></i> ANIMASI PROSES SPAM BERJALAN</div>
                <div id="ngl-console" class="spam-log-console" style="margin-top:12px;"></div>
                <div id="ngl-summary" style="margin-top:12px;font-weight:800;color:var(--navy-dark);"></div>
              </div>
            `;
            const consoleEl = document.getElementById("ngl-console");
            const summaryEl = document.getElementById("ngl-summary");
            let successCount = 0;

            for (let i = 1; i <= count; i++) {
              const line = document.createElement("div");
              line.textContent = `[#${i}/${count}] Mengirim paket ke ${rawUrl} -> "${msg}"...`;
              consoleEl.appendChild(line);
              consoleEl.scrollTop = consoleEl.scrollHeight;

              try {
                const apiEndpoint = `https://api.nexadev.my.id/tools/nglspam/?url=${encodeURIComponent(rawUrl)}&pesan=${encodeURIComponent(msg)}&jumlah=1`;
                const res = await fetch(apiEndpoint);
                const data = await res.json();
                if (data.status) {
                  successCount++;
                  line.textContent = `[#${i}/${count}] SUCCESS -> ${data.message || "Terkirim"}`;
                } else {
                  line.style.color = "#93c5fd";
                  line.textContent = `[#${i}/${count}] RESPONSE -> ${data.message || "Diblokir / Gagal"}`;
                }
              } catch (err) {
                line.style.color = "#93c5fd";
                line.textContent = `[#${i}/${count}] ERROR -> ${err.message}`;
              }
              consoleEl.scrollTop = consoleEl.scrollHeight;
            }

            summaryEl.textContent = `Selesai! Total sukses terkirim: ${successCount} dari ${count} percobaan.`;
          });
          break;
        }

        case "bypass-link": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">MASUKAN URL PENDEK (LINKVERTISE / SAFELINK / DLL)</label>
              <input id="bp-url" class="comic-input" type="url" value="https://linkvertise.com/519136/resource-pack-hd?o=sharing" />
            </div>
            <button id="bp-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-unlock-keyhole"></i> BYPASS SEKARANG
            </button>
          `;
          document.getElementById("bp-btn").addEventListener("click", async () => {
            const rawUrl = document.getElementById("bp-url").value.trim();
            if (!rawUrl) return setErrorResult(resultArea, "URL wajib diisi.");
            setLoadingResult(resultArea, "Melewati shortlink...");
            try {
              const endpoint = `https://api.nexadev.my.id/api/bypass?key=${encodeURIComponent("RS-FZ7!yvwF")}&url=${encodeURIComponent(rawUrl)}`;
              const res = await fetch(endpoint);
              const data = await res.json();
              const finalUrl = data?.data?.result_url;
              if (!data.status || !finalUrl) throw new Error(data.message || "Gagal bypass link.");
              resultArea.innerHTML = `
                <div class="result-box">
                  <div class="result-tag"><i class="fa-solid fa-circle-check"></i> BYPASS BERHASIL (${escapeHtml(data.response_time || "")})</div>
                  <div class="stat-pills-grid">
                    <div class="stat-mini-box"><div class="stat-mini-label">Original URL</div><div class="stat-mini-val">${escapeHtml(data?.data?.original_url || rawUrl)}</div></div>
                    <div class="stat-mini-box"><div class="stat-mini-label">Result URL</div><div class="stat-mini-val">${escapeHtml(finalUrl)}</div></div>
                  </div>
                  <div style="margin-top:14px;">
                    <a class="download-action-btn" href="${escapeHtml(finalUrl)}" target="_blank" rel="noopener noreferrer">
                      <i class="fa-solid fa-up-right-from-square"></i> BUKA HASIL LINK
                    </a>
                  </div>
                </div>
              `;
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "ttqc": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">NAME</label>
                <input id="ttqc-name" class="comic-input" type="text" value="L0ZXX NOT DEV" />
              </div>
              <div class="field-group">
                <label class="field-label">AVATAR / PHOTO URL</label>
                <input id="ttqc-url" class="comic-input" type="url" value="https://clooud.my.id/uploder/uploads/fRkHHO.jpeg" />
              </div>
            </div>
            <div class="field-group">
              <label class="field-label">TEXT</label>
              <input id="ttqc-text" class="comic-input" type="text" value="halo gua L0ZX" />
            </div>
            <button id="ttqc-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-quote-right"></i> GENERATE TTQC
            </button>
          `;
          document.getElementById("ttqc-btn").addEventListener("click", async () => {
            const name = document.getElementById("ttqc-name").value.trim();
            const text = document.getElementById("ttqc-text").value.trim();
            const url = document.getElementById("ttqc-url").value.trim();
            if (!name || !text) return setErrorResult(resultArea, "NAME dan TEXT wajib diisi.");
            setLoadingResult(resultArea, "Membuat TikTok Quote Card...");
            try {
              const endpoint = `https://api.nexadev.my.id/ttqc?url=${encodeURIComponent(url)}&name=${encodeURIComponent(name)}&text=${encodeURIComponent(text)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `ttqc_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "nokia-canvas": {
          formArea.innerHTML = `
            <div class="form-grid-2">
              <div class="field-group">
                <label class="field-label">TITLE</label>
                <input id="nk-title" class="comic-input" type="text" value="L0ZX" />
              </div>
              <div class="field-group">
                <label class="field-label">FROM</label>
                <input id="nk-from" class="comic-input" type="text" value="lozx" />
              </div>
              <div class="field-group">
                <label class="field-label">DATE</label>
                <input id="nk-date" class="comic-input" type="text" value="08/06/2026" />
              </div>
              <div class="field-group">
                <label class="field-label">TIME</label>
                <input id="nk-time" class="comic-input" type="text" value="12:00" />
              </div>
            </div>
            <div class="field-group">
              <label class="field-label">TEXT SMS</label>
              <textarea id="nk-text" class="comic-textarea">kata-kata hari ini</textarea>
            </div>
            <button id="nk-btn" class="comic-btn secondary" type="button">
              <i class="fa-solid fa-mobile-screen"></i> GENERATE NOKIA CANVAS
            </button>
          `;
          document.getElementById("nk-btn").addEventListener("click", async () => {
            const text = document.getElementById("nk-text").value.trim();
            const from = document.getElementById("nk-from").value.trim();
            const date = document.getElementById("nk-date").value.trim();
            const time = document.getElementById("nk-time").value.trim();
            const title = document.getElementById("nk-title").value.trim();
            if (!text) return setErrorResult(resultArea, "Text SMS wajib diisi.");
            setLoadingResult(resultArea, "Merender layar Nokia jadul...");
            try {
              const endpoint = `https://api.nexadev.my.id/nokia?text=${encodeURIComponent(text)}&from=${encodeURIComponent(from)}&date=${encodeURIComponent(date)}&time=${encodeURIComponent(time)}&title=${encodeURIComponent(title)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `nokia_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }

        case "wmp2-canvas": {
          formArea.innerHTML = `
            <div class="field-group">
              <label class="field-label">TEXT VISUALISASI (GUNAKAN "|" UNTUK PEMISAH BARIS)</label>
              <input id="wmp-text" class="comic-input" type="text" value="ngapain cemburu|kan|cuman sebatas|teman" />
            </div>
            <button id="wmp-btn" class="comic-btn" type="button">
              <i class="fa-solid fa-compact-disc"></i> GENERATE WMP2 CANVAS
            </button>
          `;
          document.getElementById("wmp-btn").addEventListener("click", async () => {
            const text = document.getElementById("wmp-text").value.trim();
            if (!text) return setErrorResult(resultArea, "Text wajib diisi.");
            setLoadingResult(resultArea, "Merender Windows Media Player v2 Canvas...");
            try {
              const endpoint = `https://api.nexadev.my.id/wmp2?text=${encodeURIComponent(text)}`;
              const imgSrc = await fetchBinaryImageObjectUrl(endpoint);
              renderImageDownloadResult(resultArea, imgSrc, `wmp2_${Date.now()}.png`, false);
            } catch (err) {
              setErrorResult(resultArea, err.message);
            }
          });
          break;
        }
      }
    }
  </script>
</body>
</html>
