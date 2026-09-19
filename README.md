# Paddle-Wars-Main
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>THE PADDLE WARS - Stacking Queue</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

  :root {
    --bg: #F4F6F9;
    --surface: #FFFFFF;
    --primary: #0070F2;
    --primary-dark: #0058C6;
    --primary-light: #E1F4FF;
    --accent: #00B4D8;
    --green: #2E7D32;
    --green-bg: #E8F5E9;
    --orange: #E65100;
    --orange-bg: #FFF3E0;
    --red: #C62828;
    --red-bg: #FFEBEE;
    --text: #1A1A2E;
    --text-secondary: #5A6072;
    --border: #DEE2E8;
    --shadow: 0 2px 12px rgba(0,0,0,0.08);
    --shadow-lg: 0 8px 32px rgba(0,0,0,0.12);
    --radius: 12px;
    --radius-sm: 8px;
    --gold: #F9A825;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
  }

  /* Header */
  .header {
    background: linear-gradient(135deg, #0070F2 0%, #0058C6 50%, #00397A 100%);
    color: white;
    padding: 24px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 16px;
    box-shadow: 0 4px 20px rgba(0,112,242,0.3);
  }

  .header-left {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .header-logo {
    width: 48px; height: 48px;
    background: rgba(255,255,255,0.2);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px;
    backdrop-filter: blur(4px);
  }

  .header h1 {
    font-size: 24px;
    font-weight: 800;
    letter-spacing: -0.5px;
  }

  .header p {
    font-size: 13px;
    opacity: 0.85;
    margin-top: 2px;
    font-weight: 400;
  }

  /* Main Layout */
  .main {
    max-width: 1400px;
    margin: 0 auto;
    padding: 24px;
    display: grid;
    grid-template-columns: 360px 1fr;
    gap: 24px;
  }

  @media (max-width: 900px) {
    .main { grid-template-columns: 1fr; }
  }

  /* Cards */
  .card {
    background: var(--surface);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    overflow: hidden;
  }

  .card-header {
    padding: 16px 20px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .card-header h2 {
    font-size: 16px;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .card-header .badge {
    background: var(--primary);
    color: white;
    font-size: 12px;
    font-weight: 700;
    padding: 2px 10px;
    border-radius: 99px;
  }

  .card-body { padding: 20px; }

  /* Matchmaking Mode Banner */
  .matchmaking-banner {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 16px;
    border-radius: var(--radius-sm);
    font-size: 12px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .matchmaking-banner.fifo {
    background: var(--orange-bg);
    color: var(--orange);
    border: 1px solid #FFE0B2;
  }

  .matchmaking-banner.balanced {
    background: #E8F5E9;
    color: var(--green);
    border: 1px solid #C8E6C9;
  }

  .matchmaking-banner .mm-icon {
    font-size: 16px;
    flex-shrink: 0;
  }

  .matchmaking-banner .mm-progress {
    margin-left: auto;
    font-weight: 700;
    font-size: 11px;
    opacity: 0.85;
  }

  /* Add Player Form */
  .add-form {
    display: flex;
    gap: 8px;
    margin-bottom: 16px;
  }

  .add-form input {
    flex: 1;
    padding: 10px 14px;
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    font-size: 14px;
    font-family: inherit;
    transition: border-color 0.2s;
    outline: none;
  }

  .add-form input:focus {
    border-color: var(--primary);
  }

  .add-form input::placeholder {
    color: #9CA3AF;
  }

  .btn {
    padding: 10px 18px;
    border: none;
    border-radius: var(--radius-sm);
    font-size: 14px;
    font-weight: 600;
    font-family: inherit;
    cursor: pointer;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    white-space: nowrap;
  }

  .btn:active { transform: scale(0.97); }

  .btn-primary {
    background: var(--primary);
    color: white;
  }

  .btn-primary:hover { background: var(--primary-dark); }

  .btn-sm {
    padding: 6px 12px;
    font-size: 12px;
  }

  .btn-danger {
    background: var(--red-bg);
    color: var(--red);
  }

  .btn-danger:hover { background: #FFCDD2; }

  .btn-success {
    background: var(--green-bg);
    color: var(--green);
  }

  .btn-success:hover { background: #C8E6C9; }

  .btn-outline {
    background: transparent;
    color: var(--text-secondary);
    border: 1px solid var(--border);
  }

  .btn-outline:hover {
    background: var(--bg);
    color: var(--text);
  }

  .btn-icon {
    padding: 6px;
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
  }

  /* Queue List */
  .queue-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .queue-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 10px 12px;
    border-radius: var(--radius-sm);
    background: var(--bg);
    transition: all 0.25s;
    cursor: grab;
    border: 2px solid transparent;
  }

  .queue-item:hover { border-color: var(--primary); }

  .queue-item.dragging {
    opacity: 0.4;
    transform: scale(0.96);
  }

  .queue-item.drag-over {
    border-color: var(--primary);
    background: var(--primary-light);
  }

  .queue-rank {
    width: 26px;
    height: 26px;
    border-radius: 50%;
    background: var(--primary);
    color: white;
    font-size: 12px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .queue-rank.top { background: linear-gradient(135deg, #FF8F00, #F57C00); }

  .queue-info {
    flex: 1;
    min-width: 0;
  }

  .queue-name {
    font-size: 14px;
    font-weight: 500;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .queue-stats-row {
    display: flex;
    gap: 8px;
    margin-top: 2px;
    align-items: center;
  }

  .queue-stat-badge {
    font-size: 10px;
    font-weight: 700;
    padding: 1px 6px;
    border-radius: 4px;
    letter-spacing: 0.3px;
  }

  .queue-stat-badge.win {
    background: var(--green-bg);
    color: var(--green);
  }

  .queue-stat-badge.loss {
    background: var(--red-bg);
    color: var(--red);
  }

  .queue-stat-badge.games {
    background: var(--primary-light);
    color: var(--primary);
  }

  .queue-stat-badge.no-games {
    background: var(--bg);
    color: var(--text-secondary);
    border: 1px solid var(--border);
  }

  .queue-wait {
    font-size: 11px;
    color: var(--text-secondary);
    white-space: nowrap;
  }

  .queue-actions {
    display: flex;
    gap: 4px;
    opacity: 0;
    transition: opacity 0.2s;
    flex-shrink: 0;
  }

  .queue-item:hover .queue-actions { opacity: 1; }

  .empty-state {
    text-align: center;
    padding: 40px 20px;
    color: var(--text-secondary);
  }

  .empty-state .icon {
    font-size: 40px;
    margin-bottom: 12px;
    opacity: 0.5;
  }

  .empty-state p { font-size: 14px; }

  /* Right Column */
  .right-col {
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  /* Court Controls */
  .court-controls {
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
  }

  .court-controls label {
    font-size: 13px;
    font-weight: 600;
    color: var(--text-secondary);
  }

  .court-count-selector {
    display: flex;
    align-items: center;
    gap: 0;
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    overflow: hidden;
  }

  .court-count-selector button {
    width: 34px;
    height: 34px;
    border: none;
    background: var(--bg);
    cursor: pointer;
    font-size: 16px;
    font-weight: 700;
    color: var(--text);
    transition: background 0.2s;
  }

  .court-count-selector button:hover { background: var(--border); }

  .court-count-selector span {
    padding: 0 14px;
    font-weight: 700;
    font-size: 15px;
    min-width: 30px;
    text-align: center;
  }

  .game-mode-toggle {
    display: flex;
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    overflow: hidden;
    margin-left: auto;
  }

  .game-mode-toggle button {
    padding: 7px 16px;
    border: none;
    background: transparent;
    font-size: 13px;
    font-weight: 600;
    font-family: inherit;
    cursor: pointer;
    color: var(--text-secondary);
    transition: all 0.2s;
  }

  .game-mode-toggle button.active {
    background: var(--primary);
    color: white;
  }

  /* Courts Grid */
  .courts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 16px;
  }

  .court-card {
    border-radius: var(--radius);
    overflow: hidden;
    border: 2px solid var(--border);
    transition: all 0.3s;
    background: var(--surface);
  }

  .court-card.active {
    border-color: var(--green);
    box-shadow: 0 4px 16px rgba(46,125,50,0.15);
  }

  .court-card.picking-winner {
    border-color: var(--gold);
    box-shadow: 0 4px 16px rgba(249,168,37,0.25);
  }

  .court-card.empty {
    border-color: var(--border);
    border-style: dashed;
  }

  .court-top {
    padding: 14px 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .court-card.active .court-top { background: var(--green-bg); }
  .court-card.picking-winner .court-top { background: #FFF8E1; }
  .court-card.empty .court-top { background: var(--bg); }

  .court-label {
    font-weight: 700;
    font-size: 15px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .court-status {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    padding: 3px 10px;
    border-radius: 99px;
  }

  .court-card.active .court-status {
    background: var(--green);
    color: white;
  }

  .court-card.picking-winner .court-status {
    background: var(--gold);
    color: #5D4037;
  }

  .court-card.empty .court-status {
    background: var(--border);
    color: var(--text-secondary);
  }

  .court-body {
    padding: 16px;
  }

  .court-players {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin-bottom: 12px;
  }

  .court-player-slot {
    padding: 10px 12px;
    border-radius: var(--radius-sm);
    text-align: center;
    font-size: 13px;
    font-weight: 600;
    position: relative;
  }

  .court-player-slot.filled {
    background: var(--primary-light);
    color: var(--primary);
  }

  .court-player-slot .slot-stats {
    font-size: 10px;
    font-weight: 500;
    color: var(--text-secondary);
    margin-top: 2px;
  }

  .court-player-slot.empty-slot {
    background: var(--bg);
    color: var(--text-secondary);
    border: 2px dashed var(--border);
    font-weight: 400;
    font-style: italic;
  }

  .court-vs {
    grid-column: 1 / -1;
    text-align: center;
    font-size: 11px;
    font-weight: 800;
    color: var(--text-secondary);
    letter-spacing: 2px;
    padding: 2px 0;
  }

  .court-timer {
    text-align: center;
    padding: 6px;
    font-size: 22px;
    font-weight: 800;
    font-variant-numeric: tabular-nums;
    color: var(--text);
    letter-spacing: 1px;
  }

  .court-actions {
    display: flex;
    gap: 8px;
    margin-top: 10px;
  }

  .court-actions .btn { flex: 1; justify-content: center; }

  .court-card.empty .court-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 140px;
    gap: 12px;
  }

  .court-card.empty .court-body p {
    color: var(--text-secondary);
    font-size: 13px;
  }

  .court-preview {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
    justify-content: center;
  }
  .court-preview-team {
    display: flex;
    gap: 6px;
    align-items: center;
  }
  .court-preview-name {
    background: var(--primary-light);
    color: var(--primary-dark);
    padding: 5px 12px;
    border-radius: 16px;
    font-weight: 600;
    font-size: 13px;
  }
  .court-preview-vs {
    font-weight: 800;
    font-size: 11px;
    color: var(--text-secondary);
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .court-waiting {
    color: var(--text-secondary);
    font-size: 13px;
  }

  /* Winner Picker */
  .winner-pick-label {
    text-align: center;
    font-size: 13px;
    font-weight: 700;
    color: var(--text-secondary);
    margin-bottom: 8px;
    letter-spacing: 0.3px;
  }

  .winner-teams {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 8px;
    align-items: stretch;
    margin-bottom: 12px;
  }

  .winner-team-btn {
    padding: 14px 10px;
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    background: var(--surface);
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
    font-family: inherit;
  }

  .winner-team-btn:hover {
    border-color: var(--green);
    background: var(--green-bg);
    transform: scale(1.02);
  }

  .winner-team-btn .team-label {
    font-size: 10px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--text-secondary);
    margin-bottom: 6px;
  }

  .winner-team-btn .team-players {
    font-size: 13px;
    font-weight: 600;
    color: var(--text);
    line-height: 1.5;
  }

  .winner-team-btn .click-hint {
    font-size: 10px;
    color: var(--green);
    font-weight: 600;
    margin-top: 6px;
    opacity: 0;
    transition: opacity 0.2s;
  }

  .winner-team-btn:hover .click-hint {
    opacity: 1;
  }

  .winner-vs {
    display: flex;
    align-items: center;
    font-size: 12px;
    font-weight: 800;
    color: var(--text-secondary);
    letter-spacing: 2px;
  }

  .cancel-pick {
    text-align: center;
    margin-top: 4px;
  }

  /* History */
  .history-list {
    max-height: 500px;
    overflow-y: auto;
  }

  .history-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 13px;
  }

  .history-item:last-child { border-bottom: none; }

  .history-court {
    font-weight: 700;
    color: var(--primary);
    min-width: 70px;
  }

  .history-detail {
    flex: 1;
  }

  .history-teams {
    color: var(--text);
    font-weight: 500;
  }

  .history-teams .winner-marker {
    color: var(--green);
    font-weight: 700;
    font-size: 11px;
  }

  .history-teams .loser-marker {
    color: var(--text-secondary);
    font-size: 11px;
  }

  .history-time {
    font-size: 11px;
    color: var(--text-secondary);
    white-space: nowrap;
  }

  /* Toast */
  .toast-container {
    position: fixed;
    bottom: 24px;
    right: 24px;
    z-index: 999;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .toast {
    background: var(--text);
    color: white;
    padding: 12px 20px;
    border-radius: var(--radius-sm);
    font-size: 13px;
    font-weight: 500;
    box-shadow: var(--shadow-lg);
    animation: slideIn 0.3s ease, fadeOut 0.3s ease 2.7s forwards;
    max-width: 360px;
  }

  @keyframes slideIn {
    from { transform: translateX(100%); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
  }

  @keyframes fadeOut {
    to { opacity: 0; transform: translateY(10px); }
  }

  /* Responsive */
  @media (max-width: 600px) {
    .header { padding: 16px; }
    .header h1 { font-size: 18px; }
    .main { padding: 12px; }
    .courts-grid { grid-template-columns: 1fr; }
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: #B0B8C4; }

  /* Drag-and-drop hint */
  .drag-hint {
    font-size: 11px;
    color: var(--text-secondary);
    text-align: center;
    padding: 6px 0 2px;
    opacity: 0.7;
  }


  .matrix-tab:hover {
    color: var(--text);
  }

  /* Admin-only controls: hidden in viewer mode */
  body.viewer .admin-only {
    display: none !important;
  }

  /* Header login/logout button */
  .header-login-btn {
    background: rgba(255,255,255,0.18);
    color: white;
    border: 1px solid rgba(255,255,255,0.3);
    border-radius: 20px;
    padding: 8px 18px;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s;
    white-space: nowrap;
    font-family: inherit;
  }
  .header-login-btn:hover {
    background: rgba(255,255,255,0.3);
  }

  /* Login overlay */
  .login-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    backdrop-filter: blur(4px);
  }
  .login-card {
    background: white;
    border-radius: var(--radius);
    padding: 36px 32px;
    max-width: 360px;
    width: 90%;
    text-align: center;
    box-shadow: var(--shadow-lg);
  }
  .login-icon {
    font-size: 36px;
    margin-bottom: 8px;
  }
  .login-card h2 {
    font-size: 20px;
    font-weight: 800;
    margin-bottom: 6px;
  }
  .login-card p {
    font-size: 13px;
    color: var(--text-secondary);
    margin-bottom: 20px;
  }
  .login-form {
    display: flex;
    gap: 8px;
    margin-bottom: 12px;
  }
  .login-form input {
    flex: 1;
    padding: 10px 14px;
    border: 2px solid var(--border);
    border-radius: var(--radius-sm);
    font-size: 14px;
    font-family: inherit;
    outline: none;
  }
  .login-form input:focus {
    border-color: var(--primary);
  }
  .login-error {
    color: var(--red);
    font-size: 12px;
    font-weight: 600;
    margin-bottom: 10px;
  }
  .login-cancel {
    margin-top: 4px;
  }
</style>
</head>
<body>

<!-- Header -->
<div class="header">
  <div class="header-left">
    <div class="header-logo">&#127955;</div>
    <div>
      <h1>THE PADDLE WARS</h1>
      <p>Stacking Queue &mdash; Live court management &amp; balanced matchmaking</p>
    </div>
  </div>
  <button class="header-login-btn" id="headerAuthBtn" onclick="toggleAuth()">&#128274; Login</button>
</div>

<!-- Main -->
<div class="main">

  <!-- Left: Queue Panel -->
  <div class="card" id="queuePanel">
    <div class="card-header">
      <h2>&#9881;&#65039; Player Queue <span class="badge" id="queueCount">0</span></h2>
      <button class="btn btn-sm btn-outline admin-only" onclick="clearQueue()" title="Clear all">Clear</button>
    </div>
    <div class="card-body">
      <div id="matchmakingBanner"></div>
      <div class="add-form admin-only">
        <input type="text" id="playerNameInput" placeholder="Enter player name..."
               onkeydown="if(event.key==='Enter') addPlayer()" maxlength="30" autocomplete="off" />
        <button class="btn btn-primary" onclick="addPlayer()">+ Add</button>
      </div>
      <div class="drag-hint" id="dragHint" style="display:none;">Drag to reorder</div>
      <ul class="queue-list" id="queueList"></ul>
      <div class="empty-state" id="emptyQueue">
        <div class="icon">&#127934;</div>
        <p>No players in queue.<br/>Add players above to get started.</p>
      </div>
    </div>
  </div>

  <!-- Right Column -->
  <div class="right-col">

    <!-- Court Controls -->
    <div class="card admin-only">
      <div class="card-body" style="padding: 14px 20px;">
        <div class="court-controls">
          <label>Courts:</label>
          <div class="court-count-selector">
            <button onclick="changeCourts(-1)">&minus;</button>
            <span id="courtCountDisplay">2</span>
            <button onclick="changeCourts(1)">+</button>
          </div>
          <div class="game-mode-toggle">
            <button class="active" data-mode="doubles" onclick="setMode('doubles')">Doubles (4)</button>
            <button data-mode="singles" onclick="setMode('singles')">Singles (2)</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Courts -->
    <div class="courts-grid" id="courtsGrid"></div>

    <!-- History -->
    <div class="card">
      <div class="card-header">
        <h2>&#128203; Game History</h2>
      </div>
      <div class="card-body">
        <div class="history-list" id="historyList">
          <div class="empty-state" id="emptyHistory">
            <p>No completed games yet.</p>
          </div>
        </div>
      </div>
    </div>

  </div>
</div>

<!-- Toasts -->
<div class="toast-container" id="toastContainer"></div>

<script>
  // ---- AUTH ----
  const ADMIN_PASSWORD = 'JEKK111213';
  let isAdmin = false;

  function toggleAuth() {
    if (isAdmin) {
      doLogout();
    } else {
      document.getElementById('loginOverlay').style.display = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('loginError').style.display = 'none';
      setTimeout(() => document.getElementById('loginPassword').focus(), 100);
    }
  }

  function doLogin() {
    const pw = document.getElementById('loginPassword').value;
    if (pw === ADMIN_PASSWORD) {
      isAdmin = true;
      document.body.classList.remove('viewer');
      document.getElementById('loginOverlay').style.display = 'none';
      document.getElementById('headerAuthBtn').innerHTML = '&#128275; Logout';
      renderAll();
      toast('Logged in as admin.');
    } else {
      document.getElementById('loginError').style.display = '';
      document.getElementById('loginPassword').value = '';
      document.getElementById('loginPassword').focus();
    }
  }

  function doLogout() {
    isAdmin = false;
    document.body.classList.add('viewer');
    document.getElementById('headerAuthBtn').innerHTML = '&#128274; Login';
    renderAll();
    toast('Logged out. View-only mode.');
  }

  function closeLogin() {
    document.getElementById('loginOverlay').style.display = 'none';
  }

  // Start in viewer mode
  document.addEventListener('DOMContentLoaded', () => {
    document.body.classList.add('viewer');
  });

  // ---- STATE ----
  let queue = [];                // { id, name, joinedAt }
  let allPlayers = {};           // id -> { name, wins, losses, gamesPlayed }
  let courts = [];               // { id, players: [], startTime, pickingWinner: false }
  let gameHistory = [];          // { courtName, teamA, teamB, winnerTeam, duration, endTime }
  let courtCount = 2;
  let playersPerCourt = 4;
  let gameMode = 'doubles';
  let nextId = 1;
  // totalGames counter removed — games derived from player data

  // Round Robin tracking: how many times each pair has partnered / opposed
  let partnerCount = {};   // "minId-maxId" -> count
  let opponentCount = {};  // "minId-maxId" -> count

  // ---- HELPERS ----
  function esc(str) {
    const d = document.createElement('div');
    d.textContent = str;
    return d.innerHTML;
  }

  function toast(msg) {
    const container = document.getElementById('toastContainer');
    const el = document.createElement('div');
    el.className = 'toast';
    el.textContent = msg;
    container.appendChild(el);
    setTimeout(() => el.remove(), 3000);
  }

  function getStats(id) {
    return allPlayers[id] || { wins: 0, losses: 0, gamesPlayed: 0 };
  }

  function pairKey(a, b) {
    return Math.min(a, b) + '-' + Math.max(a, b);
  }

  function getPartnerCount(a, b) {
    return partnerCount[pairKey(a, b)] || 0;
  }

  function getOpponentCount(a, b) {
    return opponentCount[pairKey(a, b)] || 0;
  }

  // Record that two players partnered
  function recordPartner(a, b) {
    const key = pairKey(a, b);
    partnerCount[key] = (partnerCount[key] || 0) + 1;
  }

  // Record that two players opposed
  function recordOpponent(a, b) {
    const key = pairKey(a, b);
    opponentCount[key] = (opponentCount[key] || 0) + 1;
  }

  // ---- MATCHMAKING ----

  function getAllPlayerIds() {
    const ids = queue.map(p => p.id);
    courts.forEach(c => c.players.forEach(p => { if (!ids.includes(p.id)) ids.push(p.id); }));
    return ids;
  }

  function isBalancedMode() {
    const allIds = getAllPlayerIds();
    if (allIds.length < playersPerCourt) return false;
    return allIds.every(id => getStats(id).gamesPlayed >= 1);
  }

  function getMatchmakingProgress() {
    const allIds = getAllPlayerIds();
    if (allIds.length === 0) return { played: 0, total: 0 };
    const played = allIds.filter(id => getStats(id).gamesPlayed >= 1).length;
    return { played, total: allIds.length };
  }

  function getMinGamesPlayed() {
    const allIds = getAllPlayerIds();
    if (allIds.length === 0) return 0;
    let min = Infinity;
    allIds.forEach(id => {
      const g = getStats(id).gamesPlayed;
      if (g < min) min = g;
    });
    return min === Infinity ? 0 : min;
  }

  // Get total unique partner pairs possible from queue players
  function getRoundRobinProgress() {
    const allIds = getAllPlayerIds();
    const n = allIds.length;
    if (n < 2) return { completed: 0, total: 0, round: 1 };
    const totalPairs = n * (n - 1) / 2;
    let completed = 0;
    for (let i = 0; i < allIds.length; i++) {
      for (let j = i + 1; j < allIds.length; j++) {
        if (getPartnerCount(allIds[i], allIds[j]) > 0) completed++;
      }
    }
    const round = Math.floor(completed / totalPairs) + 1;
    return { completed, total: totalPairs, round };
  }

  // Generate all possible pairs from an array of queue indices
  function allPairsFrom(indices) {
    const pairs = [];
    for (let i = 0; i < indices.length; i++) {
      for (let j = i + 1; j < indices.length; j++) {
        pairs.push([indices[i], indices[j]]);
      }
    }
    return pairs;
  }

  // Score a team pair: how many times these two have partnered (lower = better for round robin)
  function pairPartnerScore(idxA, idxB) {
    return getPartnerCount(queue[idxA].id, queue[idxB].id);
  }

  // Score opponent pair: how many times these sets have faced each other
  function matchOpponentScore(teamA, teamB) {
    let score = 0;
    for (const a of teamA) {
      for (const b of teamB) {
        score += getOpponentCount(queue[a].id, queue[b].id);
      }
    }
    return score;
  }

  // Core selection for doubles round robin
  function selectNextPlayers() {
    if (queue.length < playersPerCourt) return null;

    if (gameMode === 'singles') {
      return selectSingles();
    }

    // --- DOUBLES ---
    const pool = queue.map((_, i) => i);

    // Step 1: Sort pool by fewest games (equal play)
    const sorted = pool.slice().sort((a, b) => {
      const gA = getStats(queue[a].id).gamesPlayed;
      const gB = getStats(queue[b].id).gamesPlayed;
      if (gA !== gB) return gA - gB;
      return a - b;
    });

    // Step 2: Take the top candidates (fewest games). 
    // We use a window: start with 4, expand to include all players at the same game count.
    const minG = getStats(queue[sorted[0]].id).gamesPlayed;
    let candidateEnd = playersPerCourt;
    // Expand window to include all players with <= minG + 1 games (one rotation buffer)
    while (candidateEnd < sorted.length && 
           getStats(queue[sorted[candidateEnd]].id).gamesPlayed <= minG + 1) {
      candidateEnd++;
    }
    const candidates = sorted.slice(0, candidateEnd);

    // Step 3: Find the best 4-player group with round robin pairing
    // Enumerate all ways to pick 2 pairs from candidates
    const allCandidatePairs = allPairsFrom(candidates);

    // Score each pair by partner count (lower = less played together = preferred)
    allCandidatePairs.sort((a, b) => {
      const scoreA = pairPartnerScore(a[0], a[1]);
      const scoreB = pairPartnerScore(b[0], b[1]);
      if (scoreA !== scoreB) return scoreA - scoreB;
      // Tiebreak: prefer players with fewer games
      const gA = getStats(queue[a[0]].id).gamesPlayed + getStats(queue[a[1]].id).gamesPlayed;
      const gB = getStats(queue[b[0]].id).gamesPlayed + getStats(queue[b[1]].id).gamesPlayed;
      return gA - gB;
    });

    let bestMatch = null;
    let bestScore = Infinity;

    // Try to find two non-overlapping pairs with the lowest combined partner score
    for (let i = 0; i < allCandidatePairs.length && i < 50; i++) {
      const pA = allCandidatePairs[i];
      const scoreA = pairPartnerScore(pA[0], pA[1]);
      
      for (let j = i + 1; j < allCandidatePairs.length && j < 80; j++) {
        const pB = allCandidatePairs[j];
        // No overlapping players
        if (pB[0] === pA[0] || pB[0] === pA[1] || pB[1] === pA[0] || pB[1] === pA[1]) continue;

        const scoreB = pairPartnerScore(pB[0], pB[1]);
        const totalPartnerScore = scoreA + scoreB;
        const oppScore = matchOpponentScore(pA, pB);
        const combined = totalPartnerScore * 10 + oppScore; // Partner variety is primary

        if (combined < bestScore) {
          bestScore = combined;
          bestMatch = { teamA: pA, teamB: pB };
        }
      }
      // Early exit if we found a perfect match (both pairs never partnered)
      if (bestScore === 0) break;
    }

    if (!bestMatch) {
      // Fallback: just take first 4
      const picked = sorted.slice(0, 4);
      return extractPlayers(picked, false);
    }

    // Step 4: If balanced mode, arrange (1W+1L) vs (1W+1L) within the selected 4
    const all4 = [...bestMatch.teamA, ...bestMatch.teamB];
    const balanced = isBalancedMode();

    if (balanced) {
      return extractPlayersBalanced(all4, bestMatch);
    } else {
      return extractPlayers(all4, false);
    }
  }

  function selectSingles() {
    const pool = queue.map((_, i) => i);

    const sorted = pool.slice().sort((a, b) => {
      const gA = getStats(queue[a].id).gamesPlayed;
      const gB = getStats(queue[b].id).gamesPlayed;
      if (gA !== gB) return gA - gB;
      return a - b;
    });

    // For singles, find two players who have opposed each other the least
    const minG = getStats(queue[sorted[0]].id).gamesPlayed;
    let candidateEnd = 2;
    while (candidateEnd < sorted.length && 
           getStats(queue[sorted[candidateEnd]].id).gamesPlayed <= minG + 1) {
      candidateEnd++;
    }
    const candidates = sorted.slice(0, candidateEnd);

    let bestPair = null;
    let bestScore = Infinity;

    for (let i = 0; i < candidates.length; i++) {
      for (let j = i + 1; j < candidates.length; j++) {
        const score = getOpponentCount(queue[candidates[i]].id, queue[candidates[j]].id);
        if (score < bestScore) {
          bestScore = score;
          bestPair = [candidates[i], candidates[j]];
        }
      }
    }

    if (!bestPair) bestPair = sorted.slice(0, 2);
    return extractPlayers(bestPair, false);
  }

  // Extract players from queue by indices (returns player objects, removes from queue)
  // IMPORTANT: preserves the original order of indices (pair grouping)
  function extractPlayers(indices) {
    // Snapshot players at their indices before splicing
    const map = {};
    indices.forEach(idx => { map[idx] = queue[idx]; });
    // Splice in descending order (safe removal)
    const desc = indices.slice().sort((a, b) => b - a);
    desc.forEach(idx => { queue.splice(idx, 1); });
    // Return in original indices order (preserves team pairing)
    return indices.map(idx => map[idx]);
  }

  // Extract 4 players and arrange as balanced teams: (1W+1L) vs (1W+1L)
  function extractPlayersBalanced(indices, matchInfo) {
    // Snapshot then splice safely
    const map = {};
    indices.forEach(idx => { map[idx] = queue[idx]; });
    const desc = indices.slice().sort((a, b) => b - a);
    desc.forEach(idx => { queue.splice(idx, 1); });
    const players = indices.map(idx => map[idx]);

    // Classify by W/L
    const w = [];
    const l = [];
    const e = [];
    players.forEach(p => {
      const s = getStats(p.id);
      const net = s.wins - s.losses;
      if (net > 0) w.push(p);
      else if (net < 0) l.push(p);
      else e.push(p);
    });

    // Distribute evens
    while (e.length > 0) {
      if (w.length <= l.length) w.push(e.pop());
      else l.push(e.pop());
    }

    // Pad if needed
    while (w.length < 2 && l.length > 2) w.push(l.pop());
    while (l.length < 2 && w.length > 2) l.push(w.pop());
    while (w.length < 2) w.push(l.length ? l.pop() : players.pop());
    while (l.length < 2) l.push(w.length ? w.pop() : players.pop());

    // Team A: w[0] + l[0], Team B: w[1] + l[1]
    return [w[0], l[0], w[1], l[1]];
  }

  // ---- PLAYERS ----
  function addPlayer() {
    const input = document.getElementById('playerNameInput');
    const name = input.value.trim();
    if (!name) return;

    const allNames = [...queue.map(p => p.name), ...courts.flatMap(c => c.players.map(p => p.name))];
    if (allNames.some(n => n.toLowerCase() === name.toLowerCase())) {
      toast('Player "' + name + '" is already registered.');
      return;
    }

    const id = nextId++;
    allPlayers[id] = { name, wins: 0, losses: 0, gamesPlayed: 0 };
    queue.push({ id, name, joinedAt: Date.now() });
    input.value = '';
    input.focus();
    renderAll();
    toast(name + ' added to queue.');
  }

  function removePlayer(id) {
    queue = queue.filter(p => p.id !== id);
    renderAll();
  }

  function moveUp(id) {
    const idx = queue.findIndex(p => p.id === id);
    if (idx > 0) {
      [queue[idx - 1], queue[idx]] = [queue[idx], queue[idx - 1]];
      renderQueue();
    }
  }

  function moveDown(id) {
    const idx = queue.findIndex(p => p.id === id);
    if (idx < queue.length - 1) {
      [queue[idx], queue[idx + 1]] = [queue[idx + 1], queue[idx]];
      renderQueue();
    }
  }

  function clearQueue() {
    if (queue.length === 0) return;
    if (!confirm('Remove all players from the queue?')) return;
    queue = [];
    renderAll();
  }

  // ---- RENDER HELPERS ----
  function renderAll() {
    renderQueue();
    renderCourts();
    renderHistory();
    renderMatchmakingBanner();
  }

  // ---- MATCHMAKING BANNER ----
  function renderMatchmakingBanner() {
    const el = document.getElementById('matchmakingBanner');
    const allIds = getAllPlayerIds();
    if (allIds.length === 0) {
      el.innerHTML = '';
      return;
    }

    const prog = getMatchmakingProgress();
    const balanced = isBalancedMode();
    const rr = getRoundRobinProgress();

    if (balanced) {
      el.innerHTML = `<div class="matchmaking-banner balanced">
        <span class="mm-icon">&#9878;</span>
        <span><strong>Balanced Round Robin</strong> &mdash; (1W + 1L) vs (1W + 1L), new partners each game</span>
        <span class="mm-progress">Pairs: ${rr.completed}/${rr.total}</span>
      </div>`;
    } else {
      el.innerHTML = `<div class="matchmaking-banner fifo">
        <span class="mm-icon">&#9203;</span>
        <span><strong>Round Robin</strong> &mdash; Equal games, rotating partners</span>
        <span class="mm-progress">${prog.played}/${prog.total} played 1+</span>
      </div>`;
    }
  }

  // ---- QUEUE RENDERING ----
  function renderQueue() {
    const list = document.getElementById('queueList');
    const empty = document.getElementById('emptyQueue');
    const hint = document.getElementById('dragHint');
    document.getElementById('queueCount').textContent = queue.length;

    if (queue.length === 0) {
      list.innerHTML = '';
      empty.style.display = '';
      hint.style.display = 'none';
      return;
    }

    empty.style.display = 'none';
    hint.style.display = queue.length > 1 ? '' : 'none';

    list.innerHTML = queue.map((p, i) => {
      const waitMin = Math.floor((Date.now() - p.joinedAt) / 60000);
      const waitStr = waitMin < 1 ? 'Just joined' : waitMin + ' min';
      const s = getStats(p.id);
      let statHTML = '';
      if (s.gamesPlayed === 0) {
        statHTML = '<span class="queue-stat-badge no-games">No games yet</span>';
      } else {
        statHTML = `<span class="queue-stat-badge win">${s.wins}W</span>
                    <span class="queue-stat-badge loss">${s.losses}L</span>
                    <span class="queue-stat-badge games">${s.gamesPlayed}G</span>`;
      }
      return `<li class="queue-item" draggable="${isAdmin}" data-id="${p.id}">
        <div class="queue-rank ${i === 0 ? 'top' : ''}">${i + 1}</div>
        <div class="queue-info">
          <div class="queue-name">${esc(p.name)}</div>
          <div class="queue-stats-row">${statHTML}</div>
        </div>
        <div class="queue-wait">${waitStr}</div>
        <div class="queue-actions admin-only">
          <button class="btn btn-icon btn-outline btn-sm" onclick="moveUp(${p.id})" title="Move up">&uarr;</button>
          <button class="btn btn-icon btn-outline btn-sm" onclick="moveDown(${p.id})" title="Move down">&darr;</button>
          <button class="btn btn-icon btn-danger btn-sm" onclick="removePlayer(${p.id})" title="Remove">&times;</button>
        </div>
      </li>`;
    }).join('');

    // Drag-and-drop
    list.querySelectorAll('.queue-item').forEach(el => {
      el.addEventListener('dragstart', onDragStart);
      el.addEventListener('dragover', onDragOver);
      el.addEventListener('dragleave', onDragLeave);
      el.addEventListener('drop', onDrop);
      el.addEventListener('dragend', onDragEnd);
    });
  }

  // ---- DRAG AND DROP ----
  let dragId = null;

  function onDragStart(e) {
    dragId = parseInt(e.currentTarget.dataset.id);
    e.currentTarget.classList.add('dragging');
    e.dataTransfer.effectAllowed = 'move';
  }

  function onDragOver(e) {
    e.preventDefault();
    e.currentTarget.classList.add('drag-over');
  }

  function onDragLeave(e) {
    e.currentTarget.classList.remove('drag-over');
  }

  function onDrop(e) {
    e.preventDefault();
    e.currentTarget.classList.remove('drag-over');
    const targetId = parseInt(e.currentTarget.dataset.id);
    if (dragId === null || dragId === targetId) return;
    const fromIdx = queue.findIndex(p => p.id === dragId);
    const toIdx = queue.findIndex(p => p.id === targetId);
    const [moved] = queue.splice(fromIdx, 1);
    queue.splice(toIdx, 0, moved);
    renderQueue();
  }

  function onDragEnd(e) {
    dragId = null;
    document.querySelectorAll('.queue-item').forEach(el => {
      el.classList.remove('dragging', 'drag-over');
    });
  }

  // ---- COURTS ----
  function initCourts() {
    courts = [];
    for (let i = 0; i < courtCount; i++) {
      courts.push({ id: i + 1, players: [], startTime: null, pickingWinner: false });
    }
    renderAll();
  }

  function changeCourts(delta) {
    const newCount = courtCount + delta;
    if (newCount < 1 || newCount > 8) return;
    if (delta > 0) {
      courts.push({ id: courts.length + 1, players: [], startTime: null, pickingWinner: false });
    } else {
      const removed = courts[courts.length - 1];
      if (removed.players.length > 0) {
        removed.players.forEach(p => queue.push({ ...p, joinedAt: Date.now() }));
      }
      courts.pop();
    }
    courtCount = newCount;
    document.getElementById('courtCountDisplay').textContent = courtCount;
    renderAll();
  }

  function setMode(mode) {
    if (mode === gameMode) return;
    if (courts.some(c => c.players.length > 0)) {
      toast('Finish or end all games before switching mode.');
      return;
    }
    gameMode = mode;
    playersPerCourt = mode === 'doubles' ? 4 : 2;
    document.querySelectorAll('.game-mode-toggle button').forEach(b => {
      b.classList.toggle('active', b.dataset.mode === mode);
    });
    renderAll();
  }

  function startGame(courtIdx) {
    const court = courts[courtIdx];
    const assignedPlayers = selectNextPlayers();

    if (!assignedPlayers) {
      toast('Need at least ' + playersPerCourt + ' players in queue.');
      return;
    }

    court.players = assignedPlayers;
    court.startTime = Date.now();
    court.pickingWinner = false;
    renderAll();
    toast('Game started on Court ' + court.id + '!');
  }

  function endGame(courtIdx) {
    const court = courts[courtIdx];
    if (court.players.length === 0) return;
    court.pickingWinner = true;
    renderCourts();
  }

  function cancelPick(courtIdx) {
    courts[courtIdx].pickingWinner = false;
    renderCourts();
  }

  function pickWinner(courtIdx, winnerTeamIdx) {
    const court = courts[courtIdx];
    if (court.players.length === 0) return;

    const duration = Date.now() - court.startTime;
    const half = playersPerCourt / 2;

    const teamA = court.players.slice(0, half);
    const teamB = court.players.slice(half);

    const winTeam = winnerTeamIdx === 0 ? teamA : teamB;
    const loseTeam = winnerTeamIdx === 0 ? teamB : teamA;

    // Update stats (defensive: verify allPlayers entry exists)
    winTeam.forEach(p => {
      if (!allPlayers[p.id]) { console.warn('pickWinner: missing allPlayers entry for winner id=' + p.id); return; }
      allPlayers[p.id].wins++;
      allPlayers[p.id].gamesPlayed++;
    });
    loseTeam.forEach(p => {
      if (!allPlayers[p.id]) { console.warn('pickWinner: missing allPlayers entry for loser id=' + p.id); return; }
      allPlayers[p.id].losses++;
      allPlayers[p.id].gamesPlayed++;
    });

    // Record round robin pairings
    if (gameMode === 'doubles') {
      recordPartner(teamA[0].id, teamA[1].id);
      recordPartner(teamB[0].id, teamB[1].id);
      // Opponents: each member of team A vs each member of team B
      for (const a of teamA) {
        for (const b of teamB) {
          recordOpponent(a.id, b.id);
        }
      }
    } else {
      recordOpponent(teamA[0].id, teamB[0].id);
    }

    // Log history
    gameHistory.unshift({
      courtName: 'Court ' + court.id,
      teamA: teamA.map(p => p.name),
      teamB: teamB.map(p => p.name),
      winnerTeam: winnerTeamIdx,
      duration,
      endTime: new Date()
    });
    // (totalGames counter removed — games derived from player data)

    // Return players to end of queue
    court.players.forEach(p => {
      queue.push({ ...p, joinedAt: Date.now() });
    });

    court.players = [];
    court.startTime = null;
    court.pickingWinner = false;

    renderAll();
    toast('Game ended on Court ' + court.id + '. Winners: ' + winTeam.map(p => p.name).join(' & '));
  }

  // ---- COURT RENDERING ----
  function renderCourts() {
    const grid = document.getElementById('courtsGrid');

    // Pre-compute the actual next assignment by running the real matchmaking (read-only)
    let nextAssignment = null;
    if (queue.length >= playersPerCourt) {
      const savedQueue = queue.slice();
      const result = selectNextPlayers();
      queue = savedQueue;
      if (result && result.length > 0) {
        const half = playersPerCourt / 2;
        nextAssignment = { teamA: result.slice(0, half), teamB: result.slice(half) };
      }
    }

    grid.innerHTML = courts.map((court, idx) => {
      const active = court.players.length > 0;

      if (!active) {
        let previewHTML = '';
        if (nextAssignment) {
          const teamAPreview = nextAssignment.teamA.map(p => `<span class="court-preview-name">${esc(p.name)}</span>`).join(' &amp; ');
          const teamBPreview = nextAssignment.teamB.map(p => `<span class="court-preview-name">${esc(p.name)}</span>`).join(' &amp; ');
          previewHTML = `<div class="court-preview">
            <div class="court-preview-team">${teamAPreview}</div>
            <div class="court-preview-vs">vs</div>
            <div class="court-preview-team">${teamBPreview}</div>
          </div>`;
        } else {
          previewHTML = '<p class="court-waiting">Waiting for players</p>';
        }
        return `<div class="court-card empty">
          <div class="court-top">
            <div class="court-label">&#127934; Court ${court.id}</div>
            <div class="court-status">Open</div>
          </div>
          <div class="court-body">
            ${previewHTML}
            <button class="btn btn-primary admin-only" onclick="startGame(${idx})" ${!nextAssignment ? 'disabled style="opacity:0.5;cursor:not-allowed;"' : ''}>
              Assign Next ${playersPerCourt} Players
            </button>
          </div>
        </div>`;
      }

      if (court.pickingWinner) {
        const half = playersPerCourt / 2;
        const teamA = court.players.slice(0, half);
        const teamB = court.players.slice(half);
        const teamANames = teamA.map(p => esc(p.name)).join('<br/>');
        const teamBNames = teamB.map(p => esc(p.name)).join('<br/>');
        const elapsed = Date.now() - court.startTime;
        const mins = String(Math.floor(elapsed / 60000)).padStart(2, '0');
        const secs = String(Math.floor((elapsed % 60000) / 1000)).padStart(2, '0');

        return `<div class="court-card picking-winner">
          <div class="court-top">
            <div class="court-label">&#127934; Court ${court.id}</div>
            <div class="court-status">Pick Winner</div>
          </div>
          <div class="court-body">
            <div class="court-timer">${mins}:${secs}</div>
            <div class="winner-pick-label admin-only">Who won?</div>
            <div class="winner-teams admin-only">
              <button class="winner-team-btn" onclick="pickWinner(${idx}, 0)">
                <div class="team-label">Team A</div>
                <div class="team-players">${teamANames}</div>
                <div class="click-hint">&#10003; Click to select</div>
              </button>
              <div class="winner-vs">VS</div>
              <button class="winner-team-btn" onclick="pickWinner(${idx}, 1)">
                <div class="team-label">Team B</div>
                <div class="team-players">${teamBNames}</div>
                <div class="click-hint">&#10003; Click to select</div>
              </button>
            </div>
            <div class="cancel-pick admin-only">
              <button class="btn btn-sm btn-outline" onclick="cancelPick(${idx})">Cancel</button>
            </div>
          </div>
        </div>`;
      }

      // Active game
      const half = playersPerCourt / 2;
      const slots = [];
      for (let i = 0; i < playersPerCourt; i++) {
        if (i === half) {
          slots.push(`<div class="court-vs">VS</div>`);
        }
        const p = court.players[i];
        if (p) {
          const s = getStats(p.id);
          const statLine = s.gamesPlayed > 0 ? `${s.wins}W - ${s.losses}L` : 'First game';
          slots.push(`<div class="court-player-slot filled">
            ${esc(p.name)}
            <div class="slot-stats">${statLine}</div>
          </div>`);
        } else {
          slots.push(`<div class="court-player-slot empty-slot">Empty</div>`);
        }
      }

      return `<div class="court-card active">
        <div class="court-top">
          <div class="court-label">&#127934; Court ${court.id}</div>
          <div class="court-status">In Play</div>
        </div>
        <div class="court-body">
          <div class="court-players">${slots.join('')}</div>
          <div class="court-timer" id="timer-${court.id}">00:00</div>
          <div class="court-actions">
            <button class="btn btn-sm btn-danger admin-only" onclick="endGame(${idx})">End Game</button>
          </div>
        </div>
      </div>`;
    }).join('');
  }

  // ---- TIMERS ----
  function updateTimers() {
    courts.forEach(court => {
      if (court.players.length > 0 && court.startTime && !court.pickingWinner) {
        const elapsed = Date.now() - court.startTime;
        const mins = String(Math.floor(elapsed / 60000)).padStart(2, '0');
        const secs = String(Math.floor((elapsed % 60000) / 1000)).padStart(2, '0');
        const el = document.getElementById('timer-' + court.id);
        if (el) el.textContent = mins + ':' + secs;
      }
    });
  }

  setInterval(updateTimers, 1000);
  setInterval(() => { if (queue.length) renderQueue(); }, 30000);

  // ---- HISTORY ----
  function renderHistory() {
    const list = document.getElementById('historyList');
    const empty = document.getElementById('emptyHistory');
    if (gameHistory.length === 0) {
      empty.style.display = '';
      return;
    }
    empty.style.display = 'none';
    list.innerHTML = gameHistory.map((h, idx) => {
      const dur = Math.floor(h.duration / 60000);
      const durStr = dur < 1 ? '<1 min' : dur + ' min';
      const timeStr = h.endTime.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });

      const aLabel = h.winnerTeam === 0 ? '<span class="winner-marker">&#9733; WIN</span>' : '<span class="loser-marker">LOSS</span>';
      const bLabel = h.winnerTeam === 1 ? '<span class="winner-marker">&#9733; WIN</span>' : '<span class="loser-marker">LOSS</span>';

      const aNames = h.teamA.map(esc).join(' &amp; ');
      const bNames = h.teamB.map(esc).join(' &amp; ');

      const gameNum = gameHistory.length - idx;

      return `<div class="history-item">
        <div class="history-court"><span style="color:var(--text-secondary);font-size:11px;">G${gameNum}</span> ${h.courtName}</div>
        <div class="history-detail">
          <div class="history-teams">${aNames} ${aLabel} <span style="margin:0 4px;color:#9CA3AF;">vs</span> ${bNames} ${bLabel}</div>
        </div>
        <div class="history-time">${durStr} &middot; ${timeStr}</div>
      </div>`;
    }).join('');
  }

  // ---- INIT ----
  initCourts();
  document.getElementById('playerNameInput').focus();
</script>
<!-- Login Overlay -->
<div class="login-overlay" id="loginOverlay" style="display:none;">
  <div class="login-card">
    <div class="login-icon">&#128274;</div>
    <h2>Admin Login</h2>
    <p>Enter the password to manage courts and players.</p>
    <div class="login-form">
      <input type="password" id="loginPassword" placeholder="Password"
             onkeydown="if(event.key==='Enter') doLogin()" autocomplete="off" />
      <button class="btn btn-primary" onclick="doLogin()">Login</button>
    </div>
    <div class="login-error" id="loginError" style="display:none;">Incorrect password</div>
    <button class="btn btn-sm btn-outline login-cancel" onclick="closeLogin()">Cancel</button>
  </div>
</div>

</body>
</html>

