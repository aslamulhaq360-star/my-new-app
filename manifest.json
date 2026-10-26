<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>১৮০ দিন অভ্যাস ট্র্যাকার</title>
<meta name="theme-color" content="#4f46e5">
<link rel="manifest" href="manifest.json">
<link rel="icon" href="icon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="icon.svg">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&family=Noto+Sans+Bengali:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="style.css">
</head>
<body>
<div id="toast-container"></div>

<header class="app-header">
  <h1 id="habit-title">অভ্যাস ট্র্যাকার</h1>
  <div class="header-date" id="header-today"></div>
</header>

<main id="app">

  <section id="tab-dashboard" class="tab active">
    <div class="card today-card">
      <div class="today-card-header">
        <span id="today-date-label">আজ: --</span>
        <span id="today-day-number" class="day-badge">দিন --/180</span>
      </div>

      <div class="ring-wrapper">
        <svg class="progress-ring" viewBox="0 0 160 160">
          <circle class="ring-bg" cx="80" cy="80" r="70"></circle>
          <circle class="ring-fg" id="today-ring" cx="80" cy="80" r="70"></circle>
        </svg>
        <div class="ring-center">
          <span id="ring-emoji">⏳</span>
          <span id="today-status-display" class="today-status">চিহ্নিত হয়নি</span>
        </div>
      </div>

      <button id="btn-mark-today" class="btn-primary">✅ আজকের অভ্যাস চিহ্নিত করুন</button>
    </div>

    <div class="stats-grid">
      <div class="stat-box"><div class="stat-value" id="stat-elapsed">0</div><div class="stat-label">অতিবাহিত দিন</div></div>
      <div class="stat-box"><div class="stat-value" id="stat-remaining">0</div><div class="stat-label">অবশিষ্ট দিন</div></div>
      <div class="stat-box"><div class="stat-value" id="stat-current-streak">0</div><div class="stat-label">বর্তমান স্ট্রিক 🔥</div></div>
      <div class="stat-box"><div class="stat-value" id="stat-max-streak">0</div><div class="stat-label">সর্বোচ্চ স্ট্রিক 🏆</div></div>
      <div class="stat-box"><div class="stat-value" id="stat-success-rate">0%</div><div class="stat-label">সফলতার হার</div></div>
      <div class="stat-box"><div class="stat-value" id="stat-failure-rate">0%</div><div class="stat-label">ব্যর্থতার হার</div></div>
    </div>

    <div class="card">
      <h3>সময়ের অগ্রগতি</h3>
      <div class="progress-bar-wrap"><div class="progress-bar" id="progress-elapsed"></div></div>
      <div class="progress-labels"><span id="elapsed-percent-label">0%</span></div>
    </div>

    <div class="card">
      <h3>বিশ্লেষণ (মোট ১৮০ দিনের মধ্যে)</h3>
      <div class="mini-stats">
        <div>✅ সফল: <span id="mini-success">0</span> (<span id="mini-success-pct">0%</span>)</div>
        <div>🟡 আংশিক সফল: <span id="mini-partial">0</span></div>
        <div>❌ ব্যর্থ: <span id="mini-fail">0</span></div>
        <div>⚪ ছুটি/স্কিপ: <span id="mini-skip">0</span></div>
        <div>⏳ চিহ্নিত হয়নি: <span id="mini-unmarked">0</span></div>
      </div>
    </div>

    <div class="card" id="missed-days-card" style="display:none">
      <h3>⚠️ মিস হওয়া দিন</h3>
      <p id="missed-days-text"></p>
      <button id="btn-fill-missed" class="btn-secondary">পূরণ করুন</button>
    </div>

    <div class="card">
      <h3>🏁 মাইলফলক</h3>
      <div class="milestone-list" id="milestone-list"></div>
    </div>
  </section>

  <section id="tab-calendar" class="tab">
    <div class="card">
      <h3>১৮০ দিনের হিটম্যাপ</h3>
      <div class="legend">
        <span class="legend-item"><i class="dot success"></i>সফল</span>
        <span class="legend-item"><i class="dot partial"></i>আংশিক</span>
        <span class="legend-item"><i class="dot fail"></i>ব্যর্থ</span>
        <span class="legend-item"><i class="dot skip"></i>ছুটি</span>
        <span class="legend-item"><i class="dot unmarked"></i>খালি</span>
        <span class="legend-item"><i class="dot future"></i>ভবিষ্যৎ</span>
      </div>
      <div class="calendar-grid" id="calendar-grid"></div>
      <p class="hint">যেকোনো দিনে ট্যাপ করে মার্ক করুন বা পরিবর্তন করুন (মিসড দিন পূরণ করতেও পারবেন)</p>
    </div>
  </section>

  <section id="tab-stats" class="tab">
    <div class="sub-nav">
      <button class="sub-nav-btn active" data-sub="daily">দৈনিক</button>
      <button class="sub-nav-btn" data-sub="weekly">সাপ্তাহিক</button>
      <button class="sub-nav-btn" data-sub="monthly">মাসিক</button>
    </div>

    <div id="sub-daily" class="sub-tab active">
      <div class="card"><h3>গত ৭ দিনের হিসেব</h3><div id="daily-list"></div></div>
    </div>

    <div id="sub-weekly" class="sub-tab">
      <div class="card">
        <h3>সাপ্তাহিক লক্ষ্য</h3>
        <label>সপ্তাহে কমপক্ষে সফল দিন (৭ দিনের মধ্যে)
          <input type="number" id="weekly-goal-input" min="1" max="7">
        </label>
      </div>
      <div id="weekly-list"></div>
    </div>

    <div id="sub-monthly" class="sub-tab">
      <div class="card">
        <h3>মাসিক লক্ষ্য</h3>
        <label>মাসে কমপক্ষে সফল দিন (৩০ দিনের মধ্যে)
          <input type="number" id="monthly-goal-input" min="1" max="30">
        </label>
      </div>
      <div id="monthly-list"></div>
    </div>

    <div class="card"><h3>সামগ্রিক বিশ্লেষণ</h3><canvas id="chart-doughnut"></canvas></div>
    <div class="card"><h3>সাপ্তাহিক প্রবণতা</h3><canvas id="chart-weekly"></canvas></div>
    <div class="card"><h3>ক্রমবর্ধমান সফলতার হার</h3><canvas id="chart-line"></canvas></div>
  </section>

  <section id="tab-review" class="tab">
    <div class="card">
      <h3>রিভিউ ও জার্নাল</h3>
      <select id="review-filter">
        <option value="all">সব</option>
        <option value="success">✅ সফল</option>
        <option value="partial">🟡 আংশিক</option>
        <option value="fail">❌ ব্যর্থ</option>
        <option value="skip">⚪ ছুটি</option>
      </select>
      <div id="review-list"></div>
    </div>
  </section>

  <section id="tab-settings" class="tab">
    <div class="card">
      <h3>সাধারণ সেটিংস</h3>
      <label>অভ্যাসের নাম<input type="text" id="setting-habit-name"></label>
      <label>শুরুর তারিখ<input type="date" id="setting-start-date"></label>
      <label>মোট দিন<input type="number" id="setting-total-days" min="1"></label>
      <label><input type="checkbox" id="setting-dark-mode"> ডার্ক মোড</label>
      <button id="btn-save-settings" class="btn-primary">সংরক্ষণ করুন</button>
    </div>

    <div class="card">
      <h3>রিমাইন্ডার</h3>
      <label><input type="checkbox" id="setting-reminder-enabled"> রিমাইন্ডার চালু করুন</label>
      <label>সময়<input type="time" id="setting-reminder-time"></label>
      <p class="hint">নোট: অ্যাপ ওপেন থাকা অবস্থায় রিমাইন্ডার কাজ করবে। নোটিফিকেশন পারমিশন দিতে হবে।</p>
    </div>

    <div class="card">
      <h3>ডেটা ব্যবস্থাপনা</h3>
      <button id="btn-export" class="btn-secondary">⬇️ ব্যাকআপ ডাউনলোড করুন</button>
      <label class="file-label">⬆️ ব্যাকআপ থেকে পুনরুদ্ধার করুন<input type="file" id="import-file" accept=".json"></label>
      <button id="btn-reset" class="btn-danger">🗑️ সব ডেটা রিসেট করুন</button>
    </div>
  </section>

</main>

<nav class="bottom-nav">
  <button class="nav-btn active" data-tab="dashboard">🏠<span>হোম</span></button>
  <button class="nav-btn" data-tab="calendar">📅<span>ক্যালেন্ডার</span></button>
  <button class="nav-btn" data-tab="stats">📊<span>পরিসংখ্যান</span></button>
  <button class="nav-btn" data-tab="review">📝<span>রিভিউ</span></button>
  <button class="nav-btn" data-tab="settings">⚙️<span>সেটিংস</span></button>
</nav>

<div id="day-modal" class="modal-overlay">
  <div class="modal">
    <h3 id="modal-date-title">তারিখ</h3>
    <label>অবস্থা নির্বাচন করুন
      <select id="modal-status">
        <option value="">— নির্বাচন করুন —</option>
        <option value="success">✅ সফল</option>
        <option value="partial">🟡 আংশিক সফল</option>
        <option value="fail">❌ ব্যর্থ</option>
        <option value="skip">⚪ ছুটি/স্কিপ</option>
      </select>
    </label>
    <label id="modal-reason-wrap" style="display:none">ব্যর্থতার কারণ
      <select id="modal-reason">
        <option value="">— নির্বাচন করুন —</option>
        <option value="laziness">অলসতা</option>
        <option value="time">সময় স্বল্পতা</option>
        <option value="sick">অসুস্থতা</option>
        <option value="forgot">ভুলে গিয়েছিলাম</option>
        <option value="priority">অন্য কাজের অগ্রাধিকার</option>
        <option value="other">অন্যান্য</option>
      </select>
    </label>
    <label>নোট/জার্নাল (ঐচ্ছিক)
      <textarea id="modal-note" rows="3" placeholder="আজকের অনুভূতি লিখুন..."></textarea>
    </label>
    <div class="modal-actions">
      <button id="modal-save" class="btn-primary">সংরক্ষণ</button>
      <button id="modal-delete" class="btn-danger">মুছুন</button>
      <button id="modal-cancel" class="btn-secondary">বাতিল</button>
    </div>
  </div>
</div>

<div id="install-banner" class="install-banner">
  <span>📲 অ্যাপটি হোম স্ক্রিনে যোগ করুন</span>
  <span><button id="install-btn">ইনস্টল</button><button id="install-dismiss">✕</button></span>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4"></script>
<script src="app.js"></script>
</body>
</html>
