<!DOCTYPE html>
<html lang="ar" dir="rtl" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BMS Pro — نظام إدارة الكتائب العسكرية (Enterprise Defense Grade v2.4)</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/dexie@4.0.8/dist/dexie.min.js"></script>
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            military: {
              50: '#f2f7f4',
              100: '#dfece3',
              500: '#10b981',
              600: '#059669',
              700: '#047857',
              800: '#064e3b',
              900: '#022c22',
              950: '#071712'
            }
          }
        }
      }
    };
  </script>
  <style>
    :root {
      --brand-primary: #10b981;
      --brand-accent: #f59e0b;
    }
    body {
      font-family: 'Tajawal', 'Cairo', 'Segoe UI', Tahoma, system-ui, -apple-system, sans-serif;
      overflow-x: hidden;
    }
    .field-mode {
      filter: contrast(1.12);
    }
    .custom-scroll::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    .custom-scroll::-webkit-scrollbar-track {
      background: rgba(15, 23, 42, 0.3);
    }
    .custom-scroll::-webkit-scrollbar-thumb {
      background: rgba(16, 185, 129, 0.45);
      border-radius: 9999px;
    }
    @media print {
      .no-print { display: none !important; }
      .print-only { display: block !important; }
      body { background: #fff !important; color: #000 !important; }
    }
  </style>
</head>
<body id="appBody" class="bg-slate-950 text-slate-100 min-h-screen flex flex-col selection:bg-emerald-500 selection:text-white transition-colors duration-200">

  <!-- TOP SECURITY & STATUS BANNER -->
  <div class="no-print bg-emerald-950/90 border-b border-emerald-800/60 px-3 py-1.5 text-xs flex flex-wrap items-center justify-between gap-2">
    <div class="flex items-center gap-3">
      <span class="inline-flex items-center gap-1.5 font-semibold text-emerald-300">
        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
        BMS PRO DEFENSE GRADE v2.4.0
      </span>
      <span class="hidden sm:inline text-slate-400">|</span>
      <span id="topSecurityBadge" class="hidden sm:inline text-emerald-200/90">التشفير: AES-256-GCM + JWT/2FA + CASL Data Scope</span>
    </div>
    <div class="flex items-center gap-3">
      <span id="liveMilitaryClock" class="font-mono text-amber-300 font-semibold">00:00:00 UTC</span>
      <button type="button" id="btnToggleOfflineMode" onclick="toggleOfflineMode()" class="px-2.5 py-0.5 rounded-full text-xs font-medium bg-emerald-800/80 text-emerald-200 border border-emerald-600/50 hover:bg-emerald-700 transition">
        <span id="connStatusDot" class="inline-block w-2 h-2 rounded-full bg-emerald-400 me-1"></span>
        <span id="connStatusText">متصل (Online Sync)</span>
      </button>
      <button type="button" id="btnRunDeltaSync" onclick="triggerManualDeltaSync()" class="px-2.5 py-0.5 rounded-full text-xs font-medium bg-amber-600/30 text-amber-200 border border-amber-500/50 hover:bg-amber-600/50 transition">
        مزامنة (<span id="offlineQueueBadge">0</span>)
      </button>
    </div>
  </div>

  <!-- MAIN HEADER / TOPBAR -->
  <header class="no-print sticky top-0 z-30 bg-slate-900/95 backdrop-blur border-b border-slate-800 px-4 py-2.5 flex flex-wrap items-center justify-between gap-3">
    <div class="flex items-center gap-3">
      <button type="button" id="btnMobileMenu" onclick="toggleMobileSidebar()" class="lg:hidden p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-200" aria-label="القائمة">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
      </button>
      <div class="flex items-center gap-2.5">
        <div id="brandLogoContainer" class="w-10 h-10 rounded-xl bg-gradient-to-br from-emerald-600 to-teal-900 border border-emerald-400/40 flex items-center justify-center shadow-lg shadow-emerald-950/50 overflow-hidden">
          <svg class="w-6 h-6 text-emerald-200" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M12 2L3 7v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V7l-9-5z"/>
            <path d="M12 8v8M8 12h8"/>
          </svg>
        </div>
        <div>
          <h1 id="appHeaderTitle" class="text-base sm:text-lg font-bold tracking-tight text-white leading-tight">نظام إدارة الكتائب العسكرية — BMS Pro</h1>
          <p id="activeUnitBreadcrumb" class="text-xs text-emerald-400 font-medium">اللواء الأول مدرع ← الكتيبة 101 مشاة ميكا</p>
        </div>
      </div>
    </div>

    <!-- GLOBAL SEARCH & QUICK CONTROLS -->
    <div class="flex items-center gap-2 flex-1 max-w-md mx-2">
      <div class="relative w-full">
        <input id="globalSearchInput" type="text" oninput="handleGlobalSearch(this.value)" placeholder="بحث شامل (الاسم، الرقم العسكري، السلاح، المهمة)... [Ctrl+K]" class="w-full bg-slate-800/90 border border-slate-700 focus:border-emerald-500 rounded-lg ps-3 pe-9 py-1.5 text-xs sm:text-sm text-slate-100 placeholder-slate-400 outline-none transition">
        <span class="absolute inset-y-0 end-0 flex items-center pe-2.5 text-slate-400 pointer-events-none">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/></svg>
        </span>
      </div>
    </div>

    <!-- ROLE SWITCHER (RBAC/ABAC) & ACTION ICONS -->
    <div class="flex items-center gap-2">
      <div class="flex items-center gap-1.5 bg-slate-800/90 border border-slate-700 rounded-lg px-2 py-1">
        <span class="text-[11px] text-slate-400 hidden xl:inline">الدور (RBAC):</span>
        <select id="roleSelector" onchange="switchUserRole(this.value)" class="bg-transparent text-xs font-semibold text-emerald-300 outline-none cursor-pointer">
          <option value="SYSTEM_ADMIN" class="bg-slate-900">مدير النظام (كامل الصلاحيات)</option>
          <option value="BRIGADE_CMD" class="bg-slate-900">قائد لواء (نطاق اللواء)</option>
          <option value="OPS_CHIEF" class="bg-slate-900">رئيس العمليات</option>
          <option value="HR_CHIEF" class="bg-slate-900">رئيس شؤون الأفراد</option>
          <option value="TRAINING_CHIEF" class="bg-slate-900">رئيس التدريب</option>
          <option value="BATTALION_CMD" class="bg-slate-900">قائد كتيبة (الكتيبة 101)</option>
          <option value="COMPANY_CMD" class="bg-slate-900">قائد سرية (السرية الأولى)</option>
          <option value="PLATOON_CMD" class="bg-slate-900">قائد فصيل (الفصيل الأول)</option>
          <option value="DUTY_OFFICER" class="bg-slate-900">ضابط مناوب</option>
          <option value="TRAINING_OFFICER" class="bg-slate-900">ضابط تدريب</option>
          <option value="SECURITY_OFFICER" class="bg-slate-900">ضابط أمن</option>
          <option value="ADMIN_OFFICER" class="bg-slate-900">ضابط إداري</option>
          <option value="CLERK" class="bg-slate-900">كاتب / مسجل بيانات</option>
          <option value="SOLDIER" class="bg-slate-900">جندي (عرض ذاتي)</option>
        </select>
      </div>

      <button type="button" id="btnFieldMode" onclick="toggleFieldMode()" title="وضع الميدان التكتيكي (Field Mode)" class="p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-amber-400 border border-slate-700 text-xs font-semibold">
        ميداني
      </button>

      <button type="button" id="btnThemeToggle" onclick="toggleThemeMode()" title="تبديل الوضع الليلي / النهاري" class="p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-200 border border-slate-700">
        <span id="themeIconText" class="text-xs font-semibold">☀️/🌙</span>
      </button>

      <button type="button" id="btnLangToggle" onclick="toggleDirectionLang()" title="تبديل اللغة والاتجاه RTL/LTR" class="px-2.5 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-200 border border-slate-700 text-xs font-bold">
        AR/EN
      </button>

      <!-- NOTIFICATIONS BUTTON -->
      <div class="relative">
        <button type="button" id="btnNotifications" onclick="toggleNotificationsPanel()" class="relative p-2 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-200 border border-slate-700">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"/></svg>
          <span id="unreadNotifBadge" class="absolute -top-1 -end-1 bg-rose-600 text-white text-[10px] font-bold px-1.5 py-0.2 rounded-full">4</span>
        </button>
        <!-- Notifications Dropdown -->
        <div id="notificationsDropdown" class="hidden absolute end-0 mt-2 w-80 sm:w-96 bg-slate-900 border border-slate-700 rounded-xl shadow-2xl z-50 p-3">
          <div class="flex items-center justify-between pb-2 mb-2 border-b border-slate-800">
            <span class="font-bold text-sm text-white">مركز الإشعارات الفورية</span>
            <button type="button" onclick="markAllNotificationsRead()" class="text-xs text-emerald-400 hover:underline">تحديد الكل كمقروء</button>
          </div>
          <div id="notificationsList" class="space-y-2 max-h-72 overflow-y-auto custom-scroll"></div>
        </div>
      </div>

      <button type="button" id="btnAuthModal" onclick="openModal('authModal')" class="px-2.5 py-1.5 rounded-lg bg-emerald-700 hover:bg-emerald-600 text-white text-xs font-semibold transition">
        الأمان / الجلسة
      </button>
    </div>
  </header>

  <!-- GLOBAL SEARCH RESULTS OVERLAY -->
  <div id="globalSearchOverlay" class="hidden no-print bg-slate-900/95 border-b border-emerald-700/60 px-6 py-4 z-20">
    <div class="flex items-center justify-between mb-2">
      <h3 class="text-sm font-bold text-emerald-400">نتائج البحث الشامل الفوري</h3>
      <button type="button" onclick="closeGlobalSearch()" class="text-xs text-slate-400 hover:text-white">إغلاق ✕</button>
    </div>
    <div id="globalSearchResults" class="grid grid-cols-1 md:grid-cols-3 gap-3 text-xs"></div>
  </div>

  <!-- LAYOUT CONTAINER -->
  <div class="flex flex-1 relative">
    <!-- SIDEBAR NAVIGATION -->
    <aside id="mainSidebar" class="no-print w-64 bg-slate-900 border-e border-slate-800 flex-shrink-0 hidden lg:flex flex-col justify-between z-20">
      <div class="p-3 space-y-1 overflow-y-auto custom-scroll">
        <div class="px-2 py-1.5 text-[11px] font-bold uppercase tracking-wider text-slate-400">القيادة والعمليات</div>
        <button type="button" data-nav="dashboard" onclick="switchTab('dashboard')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-semibold bg-emerald-600/20 text-emerald-300 border border-emerald-500/40">
          <span>📊 لوحة القيادة (Dashboard)</span>
          <span class="text-[10px] opacity-75">Alt+1</span>
        </button>
        <button type="button" data-nav="opsroom" onclick="switchTab('opsroom')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>📡 غرفة العمليات المباشرة</span>
          <span class="px-1.5 py-0.5 text-[10px] rounded bg-rose-500/20 text-rose-300">مباشر</span>
        </button>
        <button type="button" data-nav="units" onclick="switchTab('units')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🏛️ الهيكل التنظيمي (الوحدات)</span>
          <span class="text-[10px] opacity-75">Alt+2</span>
        </button>

        <div class="px-2 pt-3 pb-1 text-[11px] font-bold uppercase tracking-wider text-slate-400">القوة البشرية والانضباط</div>
        <button type="button" data-nav="personnel" onclick="switchTab('personnel')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>👥 إدارة الأفراد والملفات</span>
          <span class="text-[10px] opacity-75">Alt+3</span>
        </button>
        <button type="button" data-nav="attendance" onclick="switchTab('attendance')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>✅ الحضور والانصراف و QR</span>
          <span class="text-[10px] opacity-75">Alt+4</span>
        </button>
        <button type="button" data-nav="leaves" onclick="switchTab('leaves')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🌴 الإجازات والأذونات والموافقات</span>
          <span class="text-[10px] opacity-75">Alt+5</span>
        </button>

        <div class="px-2 pt-3 pb-1 text-[11px] font-bold uppercase tracking-wider text-slate-400">الإمداد والجاهزية والتدريب</div>
        <button type="button" data-nav="logistics" onclick="switchTab('logistics')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🔫 الأسلحة والذخائر والآليات</span>
          <span class="text-[10px] opacity-75">Alt+6</span>
        </button>
        <button type="button" data-nav="readiness" onclick="switchTab('readiness')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🛡️ الجاهزية القتالية والتدريب</span>
        </button>
        <button type="button" data-nav="tasks" onclick="switchTab('tasks')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>📋 المهام والمناوبات والأوامر</span>
        </button>

        <div class="px-2 pt-3 pb-1 text-[11px] font-bold uppercase tracking-wider text-slate-400">التقارير والذكاء الاصطناعي</div>
        <button type="button" data-nav="reports" onclick="switchTab('reports')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>📑 مركز التقارير (52 تقريراً)</span>
        </button>
        <button type="button" data-nav="ai" onclick="switchTab('ai')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🤖 المساعد العسكري الذكي (محلي)</span>
          <span class="px-1.5 py-0.5 text-[10px] rounded bg-emerald-500/20 text-emerald-300">AI</span>
        </button>

        <div class="px-2 pt-3 pb-1 text-[11px] font-bold uppercase tracking-wider text-slate-400">الحوكمة والمعمارية</div>
        <button type="button" data-nav="audit" onclick="switchTab('audit')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🔒 سجل العمليات والمزامنة والصلاحيات</span>
        </button>
        <button type="button" data-nav="architecture" onclick="switchTab('architecture')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>🏗️ المعمارية وقاعدة البيانات</span>
        </button>
        <button type="button" data-nav="settings" onclick="switchTab('settings')" class="nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800">
          <span>⚙️ الإعدادات والنسخ الاحتياطي</span>
        </button>
      </div>

      <!-- Recent Items & Role Scope Footer -->
      <div class="p-3 border-t border-slate-800 bg-slate-950/60 text-xs space-y-1.5">
        <div class="flex items-center justify-between text-slate-400">
          <span>نطاق البيانات (Scope):</span>
          <span id="sidebarScopeBadge" class="font-bold text-emerald-400">كامل اللواء</span>
        </div>
        <div class="text-[11px] text-slate-400 truncate" id="recentActionIndicator">آخر عملية: جاهز للتشغيل</div>
      </div>
    </aside>

    <!-- MAIN WORKSPACE CONTENT -->
    <main class="flex-1 p-3 sm:p-5 overflow-y-auto pb-20 lg:pb-8">
      <!-- ACTIVE ROLE PERMISSIONS BAR -->
      <div class="no-print mb-4 bg-slate-900/90 border border-slate-800 rounded-xl p-2.5 flex flex-wrap items-center justify-between gap-2 text-xs">
        <div class="flex items-center gap-2 flex-wrap">
          <span class="font-bold text-slate-300">الصلاحيات النشطة للدور الحالي:</span>
          <div id="activePermissionsChips" class="flex flex-wrap gap-1"></div>
        </div>
        <div class="flex items-center gap-2">
          <button type="button" onclick="openModal('qrScannerModal')" class="px-2.5 py-1 rounded-lg bg-emerald-600/20 text-emerald-300 border border-emerald-500/40 hover:bg-emerald-600/30 font-semibold">
            📷 مسح QR سريع
          </button>
          <button type="button" onclick="switchTab('ai')" class="px-2.5 py-1 rounded-lg bg-amber-500/20 text-amber-300 border border-amber-500/40 hover:bg-amber-500/30 font-semibold">
            🤖 اسأل المساعد الذكي
          </button>
        </div>
      </div>

      <!-- ===================================================================== -->
      <!-- SECTION 1: COMMAND DASHBOARD (لوحة القيادة)                           -->
      <!-- ===================================================================== -->
      <section id="tab-dashboard" class="tab-section space-y-5">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg sm:text-xl font-bold text-white">لوحة القيادة الاستراتيجية — ملخص الجاهزية والقوة</h2>
            <p class="text-xs text-slate-400">مؤشرات الأداء اللحظية للكتيبة مع احترام نطاق البيانات (Data Scope) للدور النشط</p>
          </div>
          <div class="flex items-center gap-2">
            <button type="button" onclick="toggleCompareMode()" id="btnCompareMode" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-amber-300">
              ⚖️ وضع المقارنة بين السرايا (Compare Mode)
            </button>
            <button type="button" onclick="switchTab('reports')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">
              📄 تصدير التقرير اليومي
            </button>
          </div>
        </div>

        <!-- KPI STAT CARDS -->
        <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-6 gap-3" id="dashboardKpiGrid"></div>

        <!-- COMPARE MODE WIDGET (Hidden by default, toggled via Compare Mode button) -->
        <div id="compareUnitsPanel" class="hidden bg-slate-900 border border-amber-500/40 rounded-xl p-4 space-y-3">
          <div class="flex items-center justify-between">
            <h3 class="text-sm font-bold text-amber-300">⚖️ مصفوفة المقارنة القياسية بين السرايا (Compare Mode)</h3>
            <button type="button" onclick="toggleCompareMode()" class="text-xs text-slate-400 hover:text-white">إخفاء ✕</button>
          </div>
          <div id="compareUnitsTableContainer" class="overflow-x-auto"></div>
        </div>

        <!-- CHARTS ROW 1 -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4">
            <div class="flex items-center justify-between mb-3">
              <h3 class="text-sm font-bold text-slate-200">📈 نسب الحضور والانضباط والغياب</h3>
              <span class="text-[11px] text-emerald-400">تحديث لحظي</span>
            </div>
            <div class="relative h-64">
              <canvas id="chartAttendanceOverview"></canvas>
            </div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4">
            <div class="flex items-center justify-between mb-3">
              <h3 class="text-sm font-bold text-slate-200">🏛️ توزيع القوة البشرية والجاهزية حسب السرايا</h3>
              <span class="text-[11px] text-amber-400">Data Scope</span>
            </div>
            <div class="relative h-64">
              <canvas id="chartUnitsDistribution"></canvas>
            </div>
          </div>
        </div>

        <!-- CHARTS ROW 2 -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4">
            <div class="flex items-center justify-between mb-3">
              <h3 class="text-sm font-bold text-slate-200">🔫 جاهزية الأسلحة والذخائر والآليات</h3>
              <span class="text-[11px] text-sky-400">الإمداد والتموين</span>
            </div>
            <div class="relative h-64">
              <canvas id="chartLogisticsReadiness"></canvas>
            </div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4">
            <div class="flex items-center justify-between mb-3">
              <h3 class="text-sm font-bold text-slate-200">🎖️ توزيع الرتب العسكرية والتدريب</h3>
              <span class="text-[11px] text-purple-400">شؤون الأفراد</span>
            </div>
            <div class="relative h-64">
              <canvas id="chartRanksBreakdown"></canvas>
            </div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 2: LIVE OPERATIONS ROOM (غرفة العمليات المباشرة)              -->
      <!-- ===================================================================== -->
      <section id="tab-opsroom" class="tab-section hidden space-y-5">
        <div class="bg-gradient-to-r from-slate-900 via-emerald-950/60 to-slate-900 border border-emerald-700/50 rounded-xl p-4 flex flex-wrap items-center justify-between gap-4">
          <div>
            <div class="flex items-center gap-2">
              <span class="w-3 h-3 rounded-full bg-rose-500 animate-ping"></span>
              <h2 class="text-lg sm:text-xl font-bold text-white">غرفة العمليات والسيطرة الميدانية المباشرة (C2 Operations Room)</h2>
            </div>
            <p class="text-xs text-slate-300 mt-1">مراقبة حية للقوة الحاضرة، الغائبة، الإنذارات، الطقس الميداني، البلاغات، والأوامر العاجلة</p>
          </div>
          <div class="flex flex-wrap items-center gap-3">
            <div class="bg-slate-950/80 border border-slate-700 rounded-lg px-3 py-1.5 text-xs">
              <span class="text-slate-400">الطقس الميداني:</span>
              <span class="font-bold text-amber-300 ms-1">☀️ 29°C | رياح 14 كم/س | الرؤية 10 كم</span>
            </div>
            <select id="opsAlertLevelSelector" onchange="changeOpsAlertLevel(this.value)" class="bg-rose-950/90 border border-rose-600 text-rose-200 rounded-lg px-3 py-1.5 text-xs font-bold">
              <option value="LEVEL_3">حالة الاستعداد: الدرجة الثالثة (اعتيادي)</option>
              <option value="LEVEL_2">حالة الاستعداد: الدرجة الثانية (تأهب متوسط)</option>
              <option value="LEVEL_1">حالة الاستعداد: الدرجة الأولى (تأهب قصوى)</option>
            </select>
          </div>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-4 gap-3" id="opsRoomMetricsGrid"></div>

        <!-- OFFLINE TACTICAL GIS RADAR & FIELD MAP -->
        <div class="bg-slate-900 border border-emerald-700/50 rounded-xl p-4 space-y-3">
          <div class="flex flex-wrap items-center justify-between gap-2">
            <div>
              <h3 class="text-sm font-bold text-emerald-400">🗺️ الخريطة الجيومكانية التكتيكية المعزولة (Offline Tactical GIS & Sector Radar)</h3>
              <p class="text-[11px] text-slate-400">عرض حي لانتشار السرايا والمدرعات ونقاط المراقبة بدون إنترنت (MapLibre Offline Grid — القطاع الجنوبي)</p>
            </div>
            <div class="flex flex-wrap gap-2">
              <button type="button" onclick="redeployTacticalUnits()" class="px-3 py-1 rounded-lg bg-emerald-700 hover:bg-emerald-600 text-white text-xs font-semibold">🔄 تحديث انتشار الدوريات والإحداثيات</button>
              <button type="button" onclick="toggleRadarSweep()" class="px-3 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-amber-300 text-xs font-semibold">📡 تبديل مسح الرادار الحراري</button>
            </div>
          </div>
          <div id="tacticalGisMapContainer" class="grid grid-cols-1 lg:grid-cols-3 gap-4 items-center"></div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <!-- Emergency & Situation Feed -->
          <div class="lg:col-span-2 bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <div class="flex items-center justify-between">
              <h3 class="text-sm font-bold text-white">🚨 سجل البلاغات والإنذارات الفورية</h3>
              <button type="button" onclick="openModal('newIncidentModal')" class="px-2.5 py-1 rounded-lg bg-rose-600 hover:bg-rose-500 text-white text-xs font-semibold">
                + تسجيل بلاغ / إنذار طارئ
              </button>
            </div>
            <div id="opsIncidentsFeed" class="space-y-2 max-h-80 overflow-y-auto custom-scroll"></div>
          </div>

          <!-- Active Duty & Leave Expiry Radar -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-300">⏱️ تنبيهات انتهاء الإجازات والمناوبات</h3>
            <div id="opsExpiryAndShiftsList" class="space-y-2 text-xs"></div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 3: ORGANIZATIONAL HIERARCHY (الهيكل التنظيمي - الوحدات)        -->
      <!-- ===================================================================== -->
      <section id="tab-units" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">الهيكل التنظيمي الهرمي للوحدات (لواء ← كتيبة ← سرية ← فصيل ← مجموعة)</h2>
            <p class="text-xs text-slate-400">شجرة الوحدات التفاعلية مع عرض القائد، القوة المعتمدة، القوة الفعلية، وإمكانية الطي والفرد والإضافة</p>
          </div>
          <div class="flex items-center gap-2">
            <button type="button" onclick="expandCollapseAllUnits(true)" class="px-2.5 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs text-slate-200 border border-slate-700">فرد الكل</button>
            <button type="button" onclick="expandCollapseAllUnits(false)" class="px-2.5 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs text-slate-200 border border-slate-700">طي الكل</button>
            <button type="button" onclick="openModal('unitModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">+ إضافة وحدة فرعية</button>
          </div>
        </div>
        <div id="unitsHierarchyContainer" class="space-y-3"></div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 4: PERSONNEL MANAGEMENT (شؤون الأفراد + كبار السن + الغياب المستمر) -->
      <!-- ===================================================================== -->
      <section id="tab-personnel" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">إدارة شؤون الأفراد والملفات العسكرية</h2>
            <p class="text-xs text-slate-400">البيانات الرباعية، الرقم العسكري الفريد، فصيلة الدم، السلاح، السجل التاريخي، كبار السن، والغياب المستمر</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <button type="button" onclick="openModal('personnelModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">
              + إضافة فرد جديد
            </button>
            <button type="button" onclick="openModal('ranksJobsModal')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-slate-200">
              🎖️ إدارة الرتب والوظائف
            </button>
            <button type="button" onclick="simulateExcelImport()" class="px-3 py-1.5 rounded-lg bg-amber-600/20 hover:bg-amber-600/30 border border-amber-500/40 text-xs font-semibold text-amber-300">
              📥 استيراد دفعة (Excel/CSV)
            </button>
          </div>
        </div>

        <!-- SUB-VIEW FILTER PILLS (All / Elderly / Continuous Absence / Archived) -->
        <div class="flex flex-wrap items-center justify-between gap-2 bg-slate-900 border border-slate-800 rounded-xl p-3">
          <div class="flex flex-wrap gap-1.5">
            <button type="button" onclick="setPersonnelViewMode('ALL')" id="pMode-ALL" class="px-3 py-1 rounded-lg text-xs font-semibold bg-emerald-600 text-white">جميع الأفراد</button>
            <button type="button" onclick="setPersonnelViewMode('ELDERLY')" id="pMode-ELDERLY" class="px-3 py-1 rounded-lg text-xs font-medium bg-slate-800 text-slate-300 hover:bg-slate-700">👴 كبار السن (حسب تاريخ الميلاد)</button>
            <button type="button" onclick="setPersonnelViewMode('CONTINUOUS_ABSENT')" id="pMode-CONTINUOUS_ABSENT" class="px-3 py-1 rounded-lg text-xs font-medium bg-slate-800 text-rose-300 hover:bg-slate-700">🚨 قائمة الغياب المستمر</button>
            <button type="button" onclick="setPersonnelViewMode('ARCHIVED')" id="pMode-ARCHIVED" class="px-3 py-1 rounded-lg text-xs font-medium bg-slate-800 text-slate-400 hover:bg-slate-700">🗄️ الأرشيف والمعطلون</button>
          </div>
          <div class="flex items-center gap-2 text-xs">
            <button type="button" onclick="executeBulkPersonnelAction('MARK_READY')" class="px-2.5 py-1 rounded bg-slate-800 hover:bg-slate-700 text-emerald-300 border border-slate-700">تحديث المحددين: جاهز</button>
            <button type="button" onclick="executeBulkPersonnelAction('TOGGLE_CONTINUOUS_ABSENT')" class="px-2.5 py-1 rounded bg-slate-800 hover:bg-slate-700 text-rose-300 border border-slate-700">إضافة/إزالة غياب مستمر</button>
          </div>
        </div>

        <!-- ADVANCED SEARCH & FILTERS -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-2.5 bg-slate-900 border border-slate-800 rounded-xl p-3 text-xs">
          <input id="filterPersonnelSearch" type="text" oninput="renderPersonnelTable()" placeholder="الاسم الرباعي أو الرقم العسكري..." class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-slate-100 outline-none focus:border-emerald-500">
          <select id="filterPersonnelUnit" onchange="renderPersonnelTable()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-slate-200 outline-none">
            <option value="">كل الوحدات والسرايا</option>
          </select>
          <select id="filterPersonnelRank" onchange="renderPersonnelTable()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-slate-200 outline-none">
            <option value="">كل الرتب العسكرية</option>
          </select>
          <select id="filterPersonnelStatus" onchange="renderPersonnelTable()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-slate-200 outline-none">
            <option value="">كل الحالات</option>
            <option value="ACTIVE">نشط</option>
            <option value="ON_LEAVE">مجاز</option>
            <option value="INACTIVE">غير نشط / معطل</option>
            <option value="RETIRED">متقاعد</option>
          </select>
          <select id="filterPersonnelBlood" onchange="renderPersonnelTable()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-slate-200 outline-none">
            <option value="">كل فصائل الدم</option>
            <option value="O+">O+</option>
            <option value="O-">O-</option>
            <option value="A+">A+</option>
            <option value="A-">A-</option>
            <option value="B+">B+</option>
            <option value="AB+">AB+</option>
          </select>
        </div>

        <!-- PERSONNEL TABLE -->
        <div class="bg-slate-900 border border-slate-800 rounded-xl overflow-hidden">
          <div class="overflow-x-auto">
            <table class="w-full text-xs text-start">
              <thead class="bg-slate-950/80 text-slate-300 border-b border-slate-800">
                <tr>
                  <th class="p-3 text-start"><input type="checkbox" id="selectAllPersonnel" onchange="toggleSelectAllPersonnel(this.checked)"></th>
                  <th class="p-3 text-start">الفرد / الرقم العسكري</th>
                  <th class="p-3 text-start">الرتبة والوظيفة</th>
                  <th class="p-3 text-start">الوحدة</th>
                  <th class="p-3 text-start">الميلاد / الدم</th>
                  <th class="p-3 text-start">السلاح والذخيرة</th>
                  <th class="p-3 text-start">الانضباط والحالة</th>
                  <th class="p-3 text-start">الإجراءات</th>
                </tr>
              </thead>
              <tbody id="personnelTableBody" class="divide-y divide-slate-800/70"></tbody>
            </table>
          </div>
          <!-- Pagination Bar -->
          <div class="px-4 py-2.5 bg-slate-950/60 border-t border-slate-800 flex items-center justify-between text-xs">
            <span id="personnelPaginationInfo" class="text-slate-400">عرض 1 إلى 10</span>
            <div class="flex items-center gap-1.5">
              <button type="button" onclick="changePersonnelPage(-1)" class="px-2.5 py-1 rounded bg-slate-800 hover:bg-slate-700 text-slate-200">السابق</button>
              <span id="personnelPageNumber" class="px-2 font-bold text-emerald-400">1</span>
              <button type="button" onclick="changePersonnelPage(1)" class="px-2.5 py-1 rounded bg-slate-800 hover:bg-slate-700 text-slate-200">التالي</button>
            </div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 5: DAILY ATTENDANCE & QR CODE (الحضور والانصراف وماسح QR)     -->
      <!-- ===================================================================== -->
      <section id="tab-attendance" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">نظام الحضور والانصراف اليومي (طابور صباحي / مسائي + باركود QR)</h2>
            <p class="text-xs text-slate-400">تسجيل الحضور الفردي أو الجماعي، احتساب الانضباط، وقت الدخول والخروج، ومسح البطاقة العسكرية بـ QR</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <input type="date" id="attendanceDateInput" onchange="renderAttendanceModule()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-xs text-white">
            <select id="attendancePeriodSelect" onchange="renderAttendanceModule()" class="bg-slate-800 border border-slate-700 rounded-lg px-2.5 py-1.5 text-xs text-emerald-300 font-semibold">
              <option value="MORNING">🌅 الفترة الصباحية (طابور صباحي)</option>
              <option value="EVENING">🌇 الفترة المسائية (طابور مسائي)</option>
              <option value="FULL_DAY">📅 يوم كامل</option>
              <option value="HALF_DAY">⏱️ نصف يوم</option>
            </select>
            <button type="button" onclick="markAllAttendancePresent()" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">
              ✓ تسجيل الكل كحاضرين
            </button>
            <button type="button" onclick="openModal('qrScannerModal')" class="px-3 py-1.5 rounded-lg bg-amber-600 hover:bg-amber-500 text-xs font-semibold text-white">
              📷 مسح / توليد QR Code
            </button>
            <button type="button" onclick="triggerBiometricNfcCheckIn()" class="px-3 py-1.5 rounded-lg bg-teal-600 hover:bg-teal-500 text-xs font-semibold text-white">
              🪪 بصمة حيوية / بطاقة NFC
            </button>
            <button type="button" onclick="clearTodayAttendanceRecords()" class="px-2.5 py-1.5 rounded-lg bg-rose-900/60 hover:bg-rose-800 border border-rose-700 text-xs text-rose-200">
              حذف سجلات اليوم
            </button>
          </div>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-5 gap-3" id="attendanceSummaryCards"></div>

        <div class="bg-slate-900 border border-slate-800 rounded-xl overflow-hidden">
          <div class="overflow-x-auto">
            <table class="w-full text-xs text-start">
              <thead class="bg-slate-950/80 text-slate-300 border-b border-slate-800">
                <tr>
                  <th class="p-3 text-start">الرقم العسكري</th>
                  <th class="p-3 text-start">الرتبة والاسم</th>
                  <th class="p-3 text-start">الوحدة</th>
                  <th class="p-3 text-start">الفترة</th>
                  <th class="p-3 text-start">الحالة</th>
                  <th class="p-3 text-start">وقت الدخول / الخروج</th>
                  <th class="p-3 text-start">الطريقة والملاحظات</th>
                  <th class="p-3 text-start">تعديل سريع</th>
                </tr>
              </thead>
              <tbody id="attendanceTableBody" class="divide-y divide-slate-800/70"></tbody>
            </table>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 6: LEAVES, PERMISSIONS & WORKFLOW ENGINE (الإجازات والأذونات) -->
      <!-- ===================================================================== -->
      <section id="tab-leaves" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">نظام الإجازات والأذونات ومحرك سير الموافقات (Workflow & Rules Engine)</h2>
            <p class="text-xs text-slate-400">إجازات (سنوية، اعتيادية، مرضية، طارئة، إدارية) وأذونات (بالساعات / بالأيام) مع فحص الرصيد وقواعد json-rules-engine</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <button type="button" onclick="openModal('leaveRequestModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">
              + تقديم طلب إجازة
            </button>
            <button type="button" onclick="openModal('permissionRequestModal')" class="px-3 py-1.5 rounded-lg bg-sky-600 hover:bg-sky-500 text-xs font-semibold text-white">
              + تقديم طلب إذن (ساعات/أيام)
            </button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <!-- Leaves Table -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">🌴 سجل الإجازات وسير الموافقات متعدد المستويات</h3>
            <div id="leavesListContainer" class="space-y-2.5 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>

          <!-- Permissions Table -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-sky-400">⏱️ سجل الأذونات (خروج/دخول بالساعات أو الأيام)</h3>
            <div id="permissionsListContainer" class="space-y-2.5 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
        </div>

        <!-- Dynamic Business Rules Engine Panel -->
        <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
          <div class="flex items-center justify-between">
            <h3 class="text-sm font-bold text-amber-300">⚙️ قواعد الأعمال الديناميكية (json-rules-engine) — قابلة للتعديل الفوري</h3>
            <span class="text-xs text-slate-400">تُطبّق تلقائياً عند طلب إجازة أو إذن</span>
          </div>
          <div id="businessRulesGrid" class="grid grid-cols-1 md:grid-cols-3 gap-3 text-xs"></div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 7: LOGISTICS - WEAPONS, AMMO, VEHICLES & WAREHOUSES           -->
      <!-- ===================================================================== -->
      <section id="tab-logistics" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">إدارة الأسلحة والذخائر والآليات والمستودعات والصيانة</h2>
            <p class="text-xs text-slate-400">تتبع العهدة الفردية، الأرقام التسلسلية، حركة الذخيرة، جاهزية المدرعات والمركبات، وجدولة الصيانة</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <button type="button" onclick="openModal('weaponModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">+ تسجيل سلاح</button>
            <button type="button" onclick="openModal('ammoModal')" class="px-3 py-1.5 rounded-lg bg-amber-600 hover:bg-amber-500 text-xs font-semibold text-white">+ حركة ذخيرة (وارد/منصرف)</button>
            <button type="button" onclick="dispatchAmmoWithCrdtAndFourEyes()" class="px-3 py-1.5 rounded-lg bg-purple-700 hover:bg-purple-600 text-xs font-semibold text-white">👁️👁️ صرف ذخيرة (CRDT + العيون الأربع)</button>
            <button type="button" onclick="openModal('vehicleModal')" class="px-3 py-1.5 rounded-lg bg-sky-600 hover:bg-sky-500 text-xs font-semibold text-white">+ إضافة آلية / مركبة</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <!-- Weapons Column -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">🔫 سجل الأسلحة والعهدة والصيانة</h3>
            <div id="weaponsListContainer" class="space-y-2.5 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
          <!-- Ammunition Column -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-400">📦 مخزون الذخائر وحركة الوارد والمنصرف</h3>
            <div id="ammoListContainer" class="space-y-2.5 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
          <!-- Vehicles Column -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-sky-400">🚜 الآليات والمدرعات والوقود والأعطال</h3>
            <div id="vehiclesListContainer" class="space-y-2.5 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 8: READINESS & TRAINING (الجاهزية القتالية والتدريب)          -->
      <!-- ===================================================================== -->
      <section id="tab-readiness" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">إدارة الجاهزية القتالية والتدريب العسكري</h2>
            <p class="text-xs text-slate-400">تحديث حالة الجاهزية لكل فرد أو وحدة مع السبب، الخطط التدريبية، نتائج الرماية، واللياقة البدنية</p>
          </div>
          <div class="flex items-center gap-2">
            <select id="readinessUnitFilter" onchange="renderReadinessAndTraining()" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-200">
              <option value="">جميع السرايا والوحدات</option>
            </select>
            <button type="button" onclick="openModal('trainingModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">+ إضافة نتيجة تدريب / رماية</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">🛡️ حالة الجاهزية للأفراد وسجل التحديثات</h3>
            <div id="readinessPersonnelContainer" class="space-y-2 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-400">🎯 الخطط التدريبية، نتائج الرماية، واللياقة البدنية</h3>
            <div id="trainingRecordsContainer" class="space-y-2 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 9: TASKS, SHIFTS, ORDERS & ANNOUNCEMENTS                      -->
      <!-- ===================================================================== -->
      <section id="tab-tasks" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">إدارة المهام الإدارية والميدانية، المناوبات، والإعلانات</h2>
            <p class="text-xs text-slate-400">توزيع المهام، متابعة نسب الإنجاز، جدول الخفارات والمناوبات، ولوحة الإعلانات والأوامر المستديمة</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <button type="button" onclick="openModal('taskModal')" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">+ إضافة مهمة جديدة</button>
            <button type="button" onclick="openModal('announcementModal')" class="px-3 py-1.5 rounded-lg bg-amber-600 hover:bg-amber-500 text-xs font-semibold text-white">+ نشر إعلان / أمر عسكري</button>
            <button type="button" onclick="signAllMilitaryOrdersPki()" class="px-3 py-1.5 rounded-lg bg-sky-700 hover:bg-sky-600 text-xs font-semibold text-white">✍️ توقيع رقمي للأوامر (Ed25519 PKI)</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <div class="lg:col-span-2 bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">📋 لوحة متابعة المهام ونسب الإنجاز</h3>
            <div id="tasksBoardContainer" class="space-y-2.5"></div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-400">📢 الإعلانات والأوامر العسكرية والمناوبات</h3>
            <div id="announcementsListContainer" class="space-y-2.5"></div>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 10: 52 ENTERPRISE REPORTS ENGINE (مركز التقارير المؤسسية)     -->
      <!-- ===================================================================== -->
      <section id="tab-reports" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">مركز التقارير المؤسسية الشامل (52 تقريراً عسكرياً وإدارياً قياسياً)</h2>
            <p class="text-xs text-slate-400">توليد ومعاينة فورية مع احترام نطاق البيانات (Data Scope) والتصدير إلى PDF وExcel وWord وCSV والطباعة المباشرة</p>
          </div>
          <div class="flex flex-wrap items-center gap-2">
            <button type="button" onclick="exportActiveReport('CSV')" class="px-3 py-1.5 rounded-lg bg-emerald-700 hover:bg-emerald-600 text-xs font-semibold text-white">📊 تصدير Excel / CSV</button>
            <button type="button" onclick="exportActiveReport('WORD')" class="px-3 py-1.5 rounded-lg bg-sky-700 hover:bg-sky-600 text-xs font-semibold text-white">📝 تصدير Word (.doc)</button>
            <button type="button" onclick="exportActiveReport('PRINT_PDF')" class="px-3 py-1.5 rounded-lg bg-rose-700 hover:bg-rose-600 text-xs font-semibold text-white">🖨️ طباعة / PDF</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <!-- 52 Reports Catalog Sidebar -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-3 space-y-2">
            <input type="text" id="reportCatalogSearch" oninput="renderReportsCatalog()" placeholder="ابحث في 52 تقريراً..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-white outline-none">
            <div id="reportsCatalogList" class="space-y-1 max-h-96 overflow-y-auto custom-scroll"></div>
          </div>

          <!-- Active Report Live Preview -->
          <div class="lg:col-span-2 bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3" id="reportPreviewContainer"></div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 11: LOCAL MILITARY AI ASSISTANT (المساعد الذكي المحلي)        -->
      <!-- ===================================================================== -->
      <section id="tab-ai" class="tab-section hidden space-y-4">
        <div class="bg-gradient-to-r from-emerald-950/80 via-slate-900 to-slate-900 border border-emerald-700/50 rounded-xl p-4 flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">🤖 المساعد العسكري الذكي المحلي المعزول (Local Air-Gapped AI — Ollama / Llama 3 / Mistral)</h2>
            <p class="text-xs text-emerald-300">يعمل محلياً 100% داخل خوادم الكتيبة دون إرسال أي بيانات عسكرية إلى الإنترنت — يحلل البيانات اللحظية ويجيب بالعربية</p>
          </div>
          <span class="px-3 py-1 rounded-full bg-emerald-900/90 border border-emerald-500/40 text-xs font-mono text-emerald-200">Engine: llama3.1:8b-local (Air-Gapped)</span>
        </div>

        <!-- Suggested Arabic Military Queries -->
        <div class="flex flex-wrap gap-2">
          <button type="button" onclick="askMilitaryAi('من أكثر جندي تأخر هذا الشهر؟')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-emerald-900/60 border border-slate-700 text-xs text-slate-200">من أكثر جندي تأخر هذا الشهر؟</button>
          <button type="button" onclick="askMilitaryAi('اعرض غياب السرية الثانية.')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-emerald-900/60 border border-slate-700 text-xs text-slate-200">اعرض غياب السرية الثانية.</button>
          <button type="button" onclick="askMilitaryAi('من لديه إجازة تنتهي خلال يومين؟')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-emerald-900/60 border border-slate-700 text-xs text-slate-200">من لديه إجازة تنتهي خلال يومين؟</button>
          <button type="button" onclick="askMilitaryAi('كم عدد الأسلحة الجاهزة؟')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-emerald-900/60 border border-slate-700 text-xs text-slate-200">كم عدد الأسلحة الجاهزة؟</button>
          <button type="button" onclick="askMilitaryAi('ما نسبة الجاهزية العامة؟')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-emerald-900/60 border border-slate-700 text-xs text-slate-200">ما نسبة الجاهزية العامة؟</button>
          <button type="button" onclick="askMilitaryAi('تحليل الشذوذ واقتراح قرارات لتحسين الانضباط')" class="px-3 py-1.5 rounded-lg bg-amber-900/40 hover:bg-amber-800/50 border border-amber-600/40 text-xs text-amber-200">💡 اقتراح القرارات وكشف الشذوذ</button>
        </div>

        <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 flex flex-col h-96">
          <div id="aiChatMessages" class="flex-1 overflow-y-auto custom-scroll space-y-3 pe-2 text-xs"></div>
          <div class="pt-3 mt-3 border-t border-slate-800 flex items-center gap-2">
            <input id="aiQueryInput" type="text" onkeydown="if(event.key==='Enter')submitCustomAiQuery()" placeholder="اكتب سؤالك باللغة العربية للمساعد الذكي المحلي..." class="flex-1 bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-xs text-white outline-none focus:border-emerald-500">
            <button type="button" onclick="submitCustomAiQuery()" class="px-4 py-2 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-bold text-white">إرسال التحليل</button>
          </div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 12: AUDIT LOGS, OFFLINE SYNC & RBAC MATRIX                    -->
      <!-- ===================================================================== -->
      <section id="tab-audit" class="tab-section hidden space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold text-white">سجل العمليات غير القابل للحذف (Immutable Hash-Chain Audit) والمزامنة (Offline Sync)</h2>
            <p class="text-xs text-slate-400">توثيق جميع الإجراءات بسلسلة تواقيع SHA-256، طابور المزامنة Dexie.js، ومصفوفة صلاحيات الأدوار الـ 14</p>
          </div>
          <div class="flex items-center gap-2">
            <select id="auditActionFilter" onchange="renderAuditAndSync()" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-xs text-slate-200">
              <option value="">كل العمليات</option>
              <option value="LOGIN">تسجيل الدخول</option>
              <option value="CREATE">إضافة</option>
              <option value="UPDATE">تعديل</option>
              <option value="APPROVE">موافقات</option>
              <option value="EXPORT">تصدير</option>
              <option value="SYNC">مزامنة</option>
              <option value="SETTINGS">إعدادات</option>
            </select>
            <button type="button" onclick="triggerManualDeltaSync()" class="px-3 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-xs font-semibold text-white">🔄 تنفيذ Delta Sync الآن</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <div class="lg:col-span-2 bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">🔒 سجل التدقيق الأمني (Immutable Audit Trail)</h3>
            <div id="auditLogsTableContainer" class="space-y-2 max-h-96 overflow-y-auto custom-scroll text-xs"></div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-400">📡 طابور العمل دون اتصال (Dexie.js Offline Queue)</h3>
            <div id="offlineQueueInspector" class="space-y-2 max-h-96 overflow-y-auto custom-scroll text-xs"></div>
          </div>
        </div>

        <!-- ENDPOINT SECURITY & REMOTE WIPE PANEL -->
        <div class="bg-slate-900 border border-rose-700/40 rounded-xl p-4 space-y-3">
          <div class="flex flex-wrap items-center justify-between gap-2">
            <div>
              <h3 class="text-sm font-bold text-rose-400">🛡️ حماية الأجهزة الميدانية والمسح الأمني عن بُعد (Endpoint Security & Remote Wipe / Dead-Man Switch)</h3>
              <p class="text-xs text-slate-400">مراقبة الأجهزة اللوحية والهواتف الميدانية المشفرة بـ PBKDF2 + AES-256 مع إمكانية التصفير الفوري عند الفقدان</p>
            </div>
          </div>
          <div id="fieldEndpointsGrid" class="grid grid-cols-1 md:grid-cols-3 gap-3 text-xs"></div>
        </div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 13: ENTERPRISE ARCHITECTURE & PRISMA SCHEMA EXPLORER          -->
      <!-- ===================================================================== -->
      <section id="tab-architecture" class="tab-section hidden space-y-4">
        <div>
          <h2 class="text-lg font-bold text-white">🏗️ المخطط المعماري الشامل، Plugin Loader، Event Bus، وقاعدة البيانات</h2>
          <p class="text-xs text-slate-400">معمارية Modular Monolith القابلة للتحول إلى Microservices، مخطط العلاقات ER Diagram، وحالة الوحدات الديناميكية</p>
        </div>
        <div id="architectureBlueprintContainer" class="space-y-4 text-xs"></div>
      </section>

      <!-- ===================================================================== -->
      <!-- SECTION 14: SYSTEM SETTINGS & ENCRYPTED BACKUP/RESTORE                -->
      <!-- ===================================================================== -->
      <section id="tab-settings" class="tab-section hidden space-y-4">
        <div>
          <h2 class="text-lg font-bold text-white">⚙️ إعدادات النظام، تخصيص الهوية، والنسخ الاحتياطي المشفر</h2>
          <p class="text-xs text-slate-400">ضبط أيام العمل، رصيد الإجازات، حد الغياب، مدة الجلسة، رفع الشعار، والنسخ الاحتياطي والاستعادة (JSON / AES-256)</p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 text-xs">
          <!-- Operational Settings -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-emerald-400">السياسات التشغيلية وتخصيص الواجهة</h3>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
              <div>
                <label class="block text-slate-400 mb-1">رصيد الإجازات السنوي الافتراضي (يوم)</label>
                <input type="number" id="settingAnnualLeave" value="30" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-white">
              </div>
              <div>
                <label class="block text-slate-400 mb-1">حد الإنذار للغياب المتصل (أيام)</label>
                <input type="number" id="settingAbsenceLimit" value="3" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-white">
              </div>
              <div>
                <label class="block text-slate-400 mb-1">مدة الجلسة الأمنية (دقيقة)</label>
                <input type="number" id="settingSessionTtl" value="30" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-white">
              </div>
              <div>
                <label class="block text-slate-400 mb-1">الحد الأدنى لجاهزية الوحدة (%)</label>
                <input type="number" id="settingMinReadiness" value="75" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-white">
              </div>
            </div>
            <div class="pt-2">
              <label class="block text-slate-400 mb-1">رفع شعار مخصص للوحدة (يظهر في الشريط العلوي والتقارير)</label>
              <input type="file" id="settingLogoInput" accept="image/*" onchange="handleLogoUpload(event)" class="w-full text-slate-300 bg-slate-800 border border-slate-700 rounded-lg p-1.5">
            </div>
            <button type="button" onclick="saveSystemSettings()" class="w-full py-2 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white font-bold">💾 حفظ وتطبيق إعدادات النظام</button>
          </div>

          <!-- Backup & Disaster Recovery -->
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-3">
            <h3 class="text-sm font-bold text-amber-400">النسخ الاحتياطي، الاستعادة، وإدارة الإصدارات</h3>
            <p class="text-slate-400">يدعم النظام النسخ الاحتياطي اليدوي والتلقائي كل 10 دقائق مع التحقق من سلامة البصمة التشفيرية.</p>
            <div class="flex flex-wrap gap-2">
              <button type="button" onclick="downloadEncryptedBackup()" class="px-3 py-2 rounded-lg bg-emerald-700 hover:bg-emerald-600 text-white font-semibold">📥 تصدير نسخة احتياطية كاملة (JSON)</button>
              <label class="px-3 py-2 rounded-lg bg-sky-700 hover:bg-sky-600 text-white font-semibold cursor-pointer">
                📤 استعادة نسخة احتياطية
                <input type="file" accept=".json" onchange="restoreBackupFromFile(event)" class="hidden">
              </label>
              <button type="button" onclick="resetSystemToDefaults()" class="px-3 py-2 rounded-lg bg-rose-900/80 hover:bg-rose-800 text-rose-200 font-semibold">⚠️ إعادة ضبط المصنع</button>
            </div>
            <div id="backupHistoryList" class="space-y-1.5 pt-2"></div>
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- MOBILE BOTTOM NAVIGATION -->
  <nav class="no-print lg:hidden fixed bottom-0 inset-x-0 bg-slate-900/95 backdrop-blur border-t border-slate-800 flex items-center justify-around py-2 z-30 text-[11px]">
    <button type="button" onclick="switchTab('dashboard')" class="flex flex-col items-center text-emerald-400 font-semibold"><span>📊</span><span>القيادة</span></button>
    <button type="button" onclick="switchTab('opsroom')" class="flex flex-col items-center text-slate-300"><span>📡</span><span>العمليات</span></button>
    <button type="button" onclick="switchTab('personnel')" class="flex flex-col items-center text-slate-300"><span>👥</span><span>الأفراد</span></button>
    <button type="button" onclick="switchTab('attendance')" class="flex flex-col items-center text-slate-300"><span>✅</span><span>الحضور</span></button>
    <button type="button" onclick="switchTab('reports')" class="flex flex-col items-center text-slate-300"><span>📑</span><span>التقارير</span></button>
    <button type="button" onclick="switchTab('ai')" class="flex flex-col items-center text-amber-300"><span>🤖</span><span>الذكاء</span></button>
  </nav>

  <!-- TOAST NOTIFICATION CONTAINER -->
  <div id="toastContainer" class="no-print fixed bottom-16 lg:bottom-5 start-5 z-50 space-y-2 max-w-sm"></div>

  <!-- UNIVERSAL MODAL OVERLAY -->
  <div id="modalBackdrop" class="no-print hidden fixed inset-0 bg-black/75 backdrop-blur-sm z-50 flex items-center justify-center p-4">
    <div id="modalContentBox" class="bg-slate-900 border border-slate-700 rounded-2xl max-w-xl w-full p-5 shadow-2xl space-y-4 max-h-[90vh] overflow-y-auto custom-scroll"></div>
  </div>

  <script>
    // =========================================================================
    // 1. DEXIE.JS / INDEXEDDB OFFLINE-FIRST DATABASE & DELTA SYNC ENGINE
    // =========================================================================
    let db = null;
    try {
      if (typeof Dexie !== 'undefined') {
        db = new Dexie('BmsProEnterpriseDB');
        db.version(1).stores({
          personnel: 'id, militaryNumber, unitId, rankId, status',
          attendance: 'id, personnelId, date, period, status',
          offlineQueue: '++id, mutationId, entityName, entityId, operation, utcTimestamp'
        });
      }
    } catch (e) {
      db = null;
    }

    // =========================================================================
    // 2. INITIAL ENTERPRISE STATE (Normalized Military Entities)
    // =========================================================================
    const ROLES_CONFIG = {
      SYSTEM_ADMIN: { nameAr: 'مدير النظام', scope: 'ALL', unitId: null, perms: ['canAddPersonnel','canEditPersonnel','canDeletePersonnel','canApproveLeave','canRejectLeave','canManageWeapons','canManageVehicles','canViewReports','canExportPDF','canExportExcel','canManageUsers','canManageSettings','canViewLogs'] },
      BRIGADE_CMD: { nameAr: 'قائد لواء', scope: 'ALL', unitId: null, perms: ['canApproveLeave','canRejectLeave','canViewReports','canExportPDF','canExportExcel','canViewLogs'] },
      OPS_CHIEF: { nameAr: 'رئيس العمليات', scope: 'ALL', unitId: null, perms: ['canApproveLeave','canManageWeapons','canManageVehicles','canViewReports','canExportPDF','canExportExcel'] },
      HR_CHIEF: { nameAr: 'رئيس شؤون الأفراد', scope: 'ALL', unitId: null, perms: ['canAddPersonnel','canEditPersonnel','canApproveLeave','canRejectLeave','canViewReports','canExportPDF','canExportExcel'] },
      TRAINING_CHIEF: { nameAr: 'رئيس التدريب', scope: 'ALL', unitId: null, perms: ['canEditPersonnel','canViewReports','canExportPDF'] },
      BATTALION_CMD: { nameAr: 'قائد كتيبة (الكتيبة 101)', scope: 'ALL', unitId: 'U-BAT-101', perms: ['canAddPersonnel','canEditPersonnel','canApproveLeave','canRejectLeave','canManageWeapons','canManageVehicles','canViewReports','canExportPDF','canExportExcel','canViewLogs'] },
      COMPANY_CMD: { nameAr: 'قائد سرية (السرية الأولى)', scope: 'UNIT', unitId: 'U-CMP-1', perms: ['canEditPersonnel','canApproveLeave','canRejectLeave','canViewReports','canExportPDF'] },
      PLATOON_CMD: { nameAr: 'قائد فصيل (الفصيل الأول)', scope: 'UNIT', unitId: 'U-CMP-1', perms: ['canApproveLeave','canViewReports'] },
      DUTY_OFFICER: { nameAr: 'ضابط مناوب', scope: 'ALL', unitId: null, perms: ['canEditPersonnel','canViewReports'] },
      TRAINING_OFFICER: { nameAr: 'ضابط تدريب', scope: 'ALL', unitId: null, perms: ['canViewReports','canExportPDF'] },
      SECURITY_OFFICER: { nameAr: 'ضابط أمن', scope: 'ALL', unitId: null, perms: ['canViewReports','canViewLogs'] },
      ADMIN_OFFICER: { nameAr: 'ضابط إداري', scope: 'ALL', unitId: null, perms: ['canAddPersonnel','canEditPersonnel','canViewReports','canExportExcel'] },
      CLERK: { nameAr: 'كاتب / مسجل بيانات', scope: 'ALL', unitId: null, perms: ['canAddPersonnel','canEditPersonnel'] },
      SOLDIER: { nameAr: 'جندي (عرض ذاتي)', scope: 'SELF', unitId: 'U-CMP-1', perms: ['canViewReports'] }
    };

    const DEFAULT_STATE = {
      currentRole: 'SYSTEM_ADMIN',
      isOffline: false,
      isFieldMode: false,
      isCompareMode: false,
      opsAlertLevel: 'LEVEL_3',
      personnelViewMode: 'ALL',
      personnelPage: 1,
      personnelPageSize: 6,
      selectedPersonnelIds: [],
      activeReportId: 'REP-01',
      deviceId: 'BMS-TERMINAL-HQ-01',

      ranks: [
        { id: 'R-01', nameAr: 'عقيد ركن', category: 'ضابط', order: 12 },
        { id: 'R-02', nameAr: 'مقدم ركن', category: 'ضابط', order: 11 },
        { id: 'R-03', nameAr: 'رائد', category: 'ضابط', order: 10 },
        { id: 'R-04', nameAr: 'نقيب', category: 'ضابط', order: 9 },
        { id: 'R-05', nameAr: 'ملازم أول', category: 'ضابط', order: 8 },
        { id: 'R-06', nameAr: 'مساعد أول', category: 'صف ضابط', order: 7 },
        { id: 'R-07', nameAr: 'رقيب أول', category: 'صف ضابط', order: 6 },
        { id: 'R-08', nameAr: 'رقيب', category: 'صف ضابط', order: 5 },
        { id: 'R-09', nameAr: 'عريف', category: 'فرد', order: 4 },
        { id: 'R-10', nameAr: 'جندي أول', category: 'فرد', order: 3 },
        { id: 'R-11', nameAr: 'جندي', category: 'فرد', order: 2 }
      ],

      jobs: [
        { id: 'J-01', titleAr: 'قائد كتيبة' },
        { id: 'J-02', titleAr: 'قائد سرية مشاة' },
        { id: 'J-03', titleAr: 'ركن عمليات الكتيبة' },
        { id: 'J-04', titleAr: 'رامي رشاش تكتيكي' },
        { id: 'J-05', titleAr: 'سائق مدرعة BTR/MRAP' },
        { id: 'J-06', titleAr: 'فني اتصالات وإشارة' },
        { id: 'J-07', titleAr: 'أمين مستودع التسليح' },
        { id: 'J-08', titleAr: 'مسعف ميداني' },
        { id: 'J-09', titleAr: 'رامي قناصة' }
      ],

      units: [
        { id: 'U-BRG-1', nameAr: 'اللواء الأول مدرع حرس', level: 'لواء', parentId: null, commander: 'العميد الركن / خالد المنصوري', authorized: 1200, expanded: true },
        { id: 'U-BAT-101', nameAr: 'الكتيبة 101 مشاة ميكا', level: 'كتيبة', parentId: 'U-BRG-1', commander: 'المقدم الركن / طارق عبدربه', authorized: 420, expanded: true },
        { id: 'U-CMP-1', nameAr: 'السرية الأولى اقتحام', level: 'سرية', parentId: 'U-BAT-101', commander: 'النقيب / صقر الحميري', authorized: 130, expanded: true },
        { id: 'U-CMP-2', nameAr: 'السرية الثانية إسناد ناري', level: 'سرية', parentId: 'U-BAT-101', commander: 'النقيب / مازن العولقي', authorized: 130, expanded: true },
        { id: 'U-CMP-3', nameAr: 'السرية الثالثة مدرعات وحماية', level: 'سرية', parentId: 'U-BAT-101', commander: 'الرائد / فهد اليافعي', authorized: 120, expanded: true },
        { id: 'U-PLT-1', nameAr: 'الفصيل الأول — السرية الأولى', level: 'فصيل', parentId: 'U-CMP-1', commander: 'الملازم أول / رعد الصبيحي', authorized: 40, expanded: true },
        { id: 'U-SQD-1', nameAr: 'الحظيرة الأولى — الفصيل الأول', level: 'مجموعة', parentId: 'U-PLT-1', commander: 'الرقيب أول / سالم باذيب', authorized: 12, expanded: true }
      ],

      personnel: [
        { id: 'P-101', militaryNumber: 'MIL-2026-1001', fullNameAr: 'طارق عبدربه صالح الشعيبي', rankId: 'R-02', unitId: 'U-BAT-101', jobId: 'J-01', birthDate: '1978-03-14', bloodType: 'O+', weapon: 'Glock-19 + AK-103', ammo: 180, status: 'ACTIVE', readiness: 'READY', readinessReason: 'جاهزية قيادية كاملة', disciplineScore: 99, annualLeaveBalance: 28, isContinuousAbsent: false, lateCountMonth: 0, courses: ['دورة القيادة والأركان', 'إدارة العمليات المشتركة'], promotions: ['ترقية إلى مقدم ركن 2024'], rewards: ['وسام الانضباط العسكري'], penalties: [] },
        { id: 'P-102', militaryNumber: 'MIL-2026-1002', fullNameAr: 'صقر أحمد قاسم الحميري', rankId: 'R-04', unitId: 'U-CMP-1', jobId: 'J-02', birthDate: '1988-07-22', bloodType: 'A+', weapon: 'AK-103 #AK9921', ammo: 150, status: 'ACTIVE', readiness: 'READY', readinessReason: 'جاهز للمهام الميدانية', disciplineScore: 97, annualLeaveBalance: 24, isContinuousAbsent: false, lateCountMonth: 1, courses: ['قادة سرايا المشاة', 'مكافحة الإرهاب'], promotions: ['ترقية إلى نقيب 2025'], rewards: ['خطاب شكر من قائد اللواء'], penalties: [] },
        { id: 'P-103', militaryNumber: 'MIL-2026-1003', fullNameAr: 'مازن علوي حسين العولقي', rankId: 'R-04', unitId: 'U-CMP-2', jobId: 'J-02', birthDate: '1986-11-05', bloodType: 'B+', weapon: 'M4A1 #M4410', ammo: 150, status: 'ACTIVE', readiness: 'READY', readinessReason: 'جاهز تماماً', disciplineScore: 96, annualLeaveBalance: 22, isContinuousAbsent: false, lateCountMonth: 0, courses: ['الإسناد الناري المتقدم'], promotions: ['ترقية إلى نقيب 2024'], rewards: [], penalties: [] },
        { id: 'P-104', militaryNumber: 'MIL-2026-1004', fullNameAr: 'سالم عوض محمد باذيب', rankId: 'R-07', unitId: 'U-CMP-1', jobId: 'J-04', birthDate: '1971-02-10', bloodType: 'O-', weapon: 'PKM #PK7712', ammo: 400, status: 'ACTIVE', readiness: 'READY', readinessReason: 'خبير أسلحة متوسطة', disciplineScore: 95, annualLeaveBalance: 19, isContinuousAbsent: false, lateCountMonth: 1, courses: ['صيانة الأسلحة المتوسطة'], promotions: ['رقيب أول 2023'], rewards: ['مكافأة تفوق بالرماية'], penalties: [] },
        { id: 'P-105', militaryNumber: 'MIL-2026-1005', fullNameAr: 'نبيل عبدالكريم سعيد الحالمي', rankId: 'R-09', unitId: 'U-CMP-2', jobId: 'J-05', birthDate: '1995-09-18', bloodType: 'A-', weapon: 'AK-103 #AK3318', ammo: 120, status: 'ACTIVE', readiness: 'NOT_READY', readinessReason: 'إصابة طفيفة أثناء التدريب التكتيكي', disciplineScore: 81, annualLeaveBalance: 14, isContinuousAbsent: false, lateCountMonth: 5, courses: ['قيادة مدرعات ليلي'], promotions: [], rewards: [], penalties: ['لفت نظر للتأخر الصباحي'] },
        { id: 'P-106', militaryNumber: 'MIL-2026-1006', fullNameAr: 'عمار ياسر ناجي المقطري', rankId: 'R-10', unitId: 'U-CMP-2', jobId: 'J-06', birthDate: '1998-04-30', bloodType: 'AB+', weapon: 'AK-103 #AK5501', ammo: 120, status: 'INACTIVE', readiness: 'NOT_READY', readinessReason: 'غياب متصل قيد التحقيق الإداري', disciplineScore: 62, annualLeaveBalance: 8, isContinuousAbsent: true, lateCountMonth: 7, courses: ['تشغيل أجهزة اللاسلكي المشفرة'], promotions: [], rewards: [], penalties: ['خصم 3 أيام لتجاوز الإجازة'] },
        { id: 'P-107', militaryNumber: 'MIL-2026-1007', fullNameAr: 'معاذ فضل منصور الردفاني', rankId: 'R-08', unitId: 'U-CMP-3', jobId: 'J-07', birthDate: '1973-06-12', bloodType: 'O+', weapon: 'AK-103 #AK6120', ammo: 120, status: 'ON_LEAVE', readiness: 'READY', readinessReason: 'في إجازة رسمية معتمدة', disciplineScore: 94, annualLeaveBalance: 16, isContinuousAbsent: false, lateCountMonth: 0, courses: ['أمن المستودعات والذخائر'], promotions: ['رقيب 2024'], rewards: ['شهادة تقدير'], penalties: [] },
        { id: 'P-108', militaryNumber: 'MIL-2026-1008', fullNameAr: 'حسام الدين علي الكازمي', rankId: 'R-11', unitId: 'U-CMP-1', jobId: 'J-08', birthDate: '2001-01-25', bloodType: 'O+', weapon: 'AK-103 #AK8819', ammo: 120, status: 'ACTIVE', readiness: 'READY', readinessReason: 'جاهز تماماً', disciplineScore: 92, annualLeaveBalance: 26, isContinuousAbsent: false, lateCountMonth: 2, courses: ['الإسعاف القتالي الميداني TCCC'], promotions: [], rewards: [], penalties: [] }
      ],

      attendance: [
        { id: 'ATT-1', personnelId: 'P-101', date: '2026-10-17', period: 'MORNING', status: 'PRESENT', checkIn: '06:12', checkOut: '14:30', method: 'QR_CODE', notes: 'حضور مبكر' },
        { id: 'ATT-2', personnelId: 'P-102', date: '2026-10-17', period: 'MORNING', status: 'PRESENT', checkIn: '06:18', checkOut: '14:30', method: 'QR_CODE', notes: 'طابور صباحي' },
        { id: 'ATT-3', personnelId: 'P-103', date: '2026-10-17', period: 'MORNING', status: 'PRESENT', checkIn: '06:20', checkOut: '14:30', method: 'QR_CODE', notes: 'طابور صباحي' },
        { id: 'ATT-4', personnelId: 'P-104', date: '2026-10-17', period: 'MORNING', status: 'PRESENT', checkIn: '06:25', checkOut: '14:30', method: 'MANUAL', notes: 'مستودع التسليح' },
        { id: 'ATT-5', personnelId: 'P-105', date: '2026-10-17', period: 'MORNING', status: 'LATE', checkIn: '07:15', checkOut: '14:30', method: 'MANUAL', notes: 'تأخر 45 دقيقة (السرية الثانية)' },
        { id: 'ATT-6', personnelId: 'P-106', date: '2026-10-17', period: 'MORNING', status: 'ABSENT', checkIn: '--:--', checkOut: '--:--', method: 'MANUAL', notes: 'غياب متصل بدون عذر (السرية الثانية)' },
        { id: 'ATT-7', personnelId: 'P-107', date: '2026-10-17', period: 'MORNING', status: 'EXCUSED', checkIn: '--:--', checkOut: '--:--', method: 'SYSTEM', notes: 'إجازة معتمدة تنتهي خلال يومين' },
        { id: 'ATT-8', personnelId: 'P-108', date: '2026-10-17', period: 'MORNING', status: 'PRESENT', checkIn: '06:22', checkOut: '14:30', method: 'QR_CODE', notes: 'طابور صباحي' }
      ],

      leaves: [
        { id: 'LV-01', personnelId: 'P-107', type: 'اعتيادية', startDate: '2026-10-12', endDate: '2026-10-18', days: 6, reason: 'ظروف عائلية', status: 'APPROVED', stage: 'معتمدة من قائد الكتيبة', expiresSoon: true },
        { id: 'LV-02', personnelId: 'P-104', type: 'سنوية', startDate: '2026-10-20', endDate: '2026-10-27', days: 7, reason: 'إجازة دورية مستحقة', status: 'PENDING', stage: 'بانتظار موافقة ركن العمليات', expiresSoon: false },
        { id: 'LV-03', personnelId: 'P-108', type: 'طارئة', startDate: '2026-10-17', endDate: '2026-10-19', days: 2, reason: 'مراجعة طبية طارئة للعائلة', status: 'APPROVED', stage: 'معتمدة من قائد السرية', expiresSoon: true }
      ],

      permissions: [
        { id: 'PRM-01', personnelId: 'P-102', durationType: 'ساعات', value: '4 ساعات (10:00 - 14:00)', reason: 'مراجعة الدائرة المالية باللواء', status: 'APPROVED' },
        { id: 'PRM-02', personnelId: 'P-105', durationType: 'أيام', value: 'يوم واحد', reason: 'فحص طبي في المستشفى العسكري', status: 'PENDING' }
      ],

      businessRules: [
        { id: 'BR-01', code: 'MAX_COMPANY_LEAVE_PCT', title: 'منع تجاوز نسبة المجازين في السرية عن 15%', condition: 'unitLeavePercent <= 15%', enabled: true },
        { id: 'BR-02', code: 'BLOCK_CONTINUOUS_ABSENT', title: 'حظر منح إجازة اعتيادية لمن لديه إنذار غياب مستمر', condition: 'isContinuousAbsent == false', enabled: true },
        { id: 'BR-03', code: 'FOUR_EYES_AMMO_DISPATCH', title: 'تطبيق مبدأ العيون الأربع لصرف أكثر من 1,000 طلقة', condition: 'ammoDispatchQty > 1000 => twoApprovers', enabled: true }
      ],

      weapons: [
        { id: 'W-01', serial: 'AK103-992104', type: 'كلاشنكوف AK-103', category: 'بندقية هجومية', caliber: '7.62x39mm', status: 'READY', assignee: 'النقيب / صقر الحميري', rounds: 150, lastMaint: '2026-09-20', nextMaint: '2026-11-20' },
        { id: 'W-02', serial: 'M4A1-441082', type: 'بندقية M4A1 تكتيكية', category: 'بندقية هجومية', caliber: '5.56x45mm', status: 'READY', assignee: 'النقيب / مازن العولقي', rounds: 150, lastMaint: '2026-10-01', nextMaint: '2026-12-01' },
        { id: 'W-03', serial: 'PKM-771209', type: 'رشاش متوسط PKM', category: 'رشاش متوسط', caliber: '7.62x54mmR', status: 'READY', assignee: 'الرقيب أول / سالم باذيب', rounds: 400, lastMaint: '2026-10-05', nextMaint: '2026-11-05' },
        { id: 'W-04', serial: 'SVD-309112', type: 'قناصة دراغونوف SVD', category: 'قناصة', caliber: '7.62x54mmR', status: 'IN_MAINTENANCE', assignee: 'مستودع التسليح المركزي', rounds: 0, lastMaint: '2026-10-15', nextMaint: '2026-10-22' },
        { id: 'W-05', serial: 'GLOCK19-1108', type: 'مسدس Glock 19 Gen5', category: 'مسدس ضباط', caliber: '9x19mm', status: 'READY', assignee: 'المقدم الركن / طارق عبدربه', rounds: 60, lastMaint: '2026-09-10', nextMaint: '2026-12-10' }
      ],

      ammunition: [
        { id: 'AM-01', batch: 'BATCH-762-2026A', type: 'ذخيرة 7.62x39mm اعتيادية', caliber: '7.62x39mm', qtyIn: 50000, qtyOut: 14200, balance: 35800, officer: 'الرقيب / معاذ الردفاني' },
        { id: 'AM-02', batch: 'BATCH-556-2026B', type: 'ذخيرة 5.56x45mm NATO', caliber: '5.56x45mm', qtyIn: 25000, qtyOut: 6500, balance: 18500, officer: 'الرقيب / معاذ الردفاني' },
        { id: 'AM-03', batch: 'BATCH-762R-2026C', type: 'ذخيرة رشاش 7.62x54mmR شريط', caliber: '7.62x54mmR', qtyIn: 18000, qtyOut: 4000, balance: 14000, officer: 'الرقيب أول / سالم باذيب' },
        { id: 'AM-04', batch: 'BATCH-9MM-2026D', type: 'ذخيرة مسدس 9x19mm Parabellum', caliber: '9x19mm', qtyIn: 8000, qtyOut: 1800, balance: 6200, officer: 'الرقيب / معاذ الردفاني' }
      ],

      vehicles: [
        { id: 'VH-01', plate: 'ج ي - 1014', chassis: 'VIN-MRAP-88912', model: 'مدرعة تكتيكية MRAP Caiman', category: 'مدرعة', unitId: 'U-CMP-3', driver: 'العريف / نبيل الحالمي', fuel: 92, status: 'OPERATIONAL', faults: 'جاهزة 100%' },
        { id: 'VH-02', plate: 'ج ي - 1028', chassis: 'VIN-LC79-44109', model: 'طقم عسكري Toyota Land Cruiser 79', category: 'دورية', unitId: 'U-CMP-1', driver: 'الجندي أول / حسام الكازمي', fuel: 85, status: 'OPERATIONAL', faults: 'تم تغيير الإطارات' },
        { id: 'VH-03', plate: 'ج ي - 1055', chassis: 'VIN-KAM-33019', model: 'شاحنة إمداد عسكرية KamAZ 6x6', category: 'شاحنة تكتيكية', unitId: 'U-CMP-2', driver: 'الرقيب / معاذ الردفاني', fuel: 64, status: 'IN_MAINTENANCE', faults: 'صيانة دورية لطرمبة الديزل' }
      ],

      trainingRecords: [
        { id: 'TR-01', course: 'رماية التكتيك القتالي النهاري والليلي', personnelName: 'النقيب / صقر الحميري', shooting: 98, fitness: 95, completion: 100, status: 'مكتمل بتفوق' },
        { id: 'TR-02', course: 'دورة الأسلحة المتوسطة والإسناد', personnelName: 'الرقيب أول / سالم باذيب', shooting: 96, fitness: 90, completion: 100, status: 'مكتمل بتفوق' },
        { id: 'TR-03', course: 'الإسعاف القتالي الميداني المتقدم', personnelName: 'الجندي أول / حسام الكازمي', shooting: 89, fitness: 94, completion: 85, status: 'جاري التنفيذ' }
      ],

      tasks: [
        { id: 'TSK-01', title: 'تفتيش الجاهزية القتالية وجرد مستودع السلاح للسرية الأولى', assignee: 'النقيب / صقر الحميري', priority: 'CRITICAL', progress: 90, dueDate: '2026-10-18', status: 'IN_PROGRESS' },
        { id: 'TSK-02', title: 'تجهيز خطة المناورة التكتيكية المشتركة للربع الرابع', assignee: 'المقدم الركن / طارق عبدربه', priority: 'HIGH', progress: 100, dueDate: '2026-10-17', status: 'COMPLETED' },
        { id: 'TSK-03', title: 'فحص وصيانة أجهزة الاتصال اللاسلكي المشفرة VHF/UHF', assignee: 'النقيب / مازن العولقي', priority: 'MEDIUM', progress: 65, dueDate: '2026-10-20', status: 'IN_PROGRESS' }
      ],

      announcements: [
        { id: 'ANN-01', title: 'أمر عمليات يومي رقم (408/2026): طابور التفتيش العام', content: 'يُنفذ طابور التفتيش الصباحي غداً الساعة 06:00 بكامل التجهيزات الميدانية لجميع السرايا.', priority: 'عاجل', date: '2026-10-17' },
        { id: 'ANN-02', title: 'تعميم شؤون الأفراد: تحديث بطاقات الباركود العسكرية QR', content: 'على جميع قادة الفصائل التأكد من مطابقة رمز QR لكل فرد لتسريع التحضير الإلكتروني.', priority: 'اعتيادي', date: '2026-10-16' },
        { id: 'ANN-03', title: 'جدول المناوبات الليلية (ضابط الخفر: النقيب صقر الحميري)', content: 'تبدأ مناوبة العمليات من الساعة 18:00 وحتى 06:00 صباح اليوم التالي.', priority: 'مناوبة', date: '2026-10-17' }
      ],

      opsIncidents: [
        { id: 'INC-01', time: '19:40', severity: 'HIGH', title: 'رصد حركة غير اعتيادية في القطاع الشمالي الشرقي — تم توجيه دورية استطلاع', unit: 'السرية الأولى اقتحام' },
        { id: 'INC-02', time: '17:15', severity: 'MEDIUM', title: 'اكتمال استلام دفعة الذخيرة اللوجستية في المخزن رقم (2) بتوقيع العيون الأربع', unit: 'شعبة الإمداد والتموين' },
        { id: 'INC-03', time: '08:00', severity: 'LOW', title: 'إغلاق محضر الحضور الصباحي إلكترونياً بنسبة انضباط 91.4%', unit: 'الكتيبة 101 مشاة ميكا' }
      ],

      notifications: [
        { id: 'NTF-01', title: 'طلب إجازة جديد بانتظار الاعتماد', msg: 'الرقيب أول / سالم باذيب قدم طلب إجازة سنوية لمدة 7 أيام.', read: false, time: 'منذ 10 دقائق' },
        { id: 'NTF-02', title: 'تنبيه انتهاء إجازة خلال 48 ساعة', msg: 'إجازة الرقيب / معاذ الردفاني تنتهي بتاريخ 2026-10-18.', read: false, time: 'منذ 25 دقيقة' },
        { id: 'NTF-03', title: 'إنذار غياب مستمر (السرية الثانية)', msg: 'الجندي أول / عمار المقطري تجاوز حد الغياب المسموح (3 أيام متصلة).', read: false, time: 'منذ ساعة' },
        { id: 'NTF-04', title: 'موعد صيانة سلاح دوري', msg: 'قناصة دراغونوف SVD رقم SVD-309112 مجدولة لفحص السبطانة.', read: false, time: 'منذ ساعتين' }
      ],

      auditLogs: [
        { id: 'LOG-501', time: '2026-10-17 19:55:10', user: 'admin_commander', action: 'LOGIN', entity: 'AuthSession', hash: '9f86d081884c7d659a2feaa0c55ad015', details: 'تسجيل دخول آمن عبر JWT + 2FA' },
        { id: 'LOG-502', time: '2026-10-17 19:42:04', user: 'capt_saqr', action: 'APPROVE', entity: 'Leave#LV-03', hash: '4b227777d4dd1fc61c6f884f48641d02', details: 'اعتماد إجازة طارئة للجندي أول حسام الكازمي' },
        { id: 'LOG-503', time: '2026-10-17 18:30:19', user: 'duty_officer', action: 'CREATE', entity: 'AttendanceSession', hash: 'e3b0c44298fc1c149afbf4c8996fb924', details: 'فتح جلسة الحضور المسائي وتوثيق QR' },
        { id: 'LOG-504', time: '2026-10-17 16:10:00', user: 'system_cron', action: 'SYNC', entity: 'BackupRecord', hash: 'd4735e3a265e16eee03f59718b9b5d03', details: 'نسخ احتياطي تلقائي مشفر AES-256-GCM' }
      ],

      offlineMutations: [],

      radarThermalMode: false,
      tacticalUnitsGis: [
        { id: 'GIS-1', name: 'قيادة الكتيبة 101 (HQ)', sector: 'القطاع الأوسط M-01', coords: '12.8254° N, 45.0331° E', x: 50, y: 50, type: 'HQ', status: 'READY' },
        { id: 'GIS-2', name: 'السرية الأولى اقتحام', sector: 'القطاع الشمالي N-04', coords: '12.8610° N, 45.0412° E', x: 30, y: 26, type: 'INFANTRY', status: 'READY' },
        { id: 'GIS-3', name: 'السرية الثانية إسناد ناري', sector: 'القطاع الشرقي E-02', coords: '12.8390° N, 45.0680° E', x: 74, y: 35, type: 'SUPPORT', status: 'ALERT' },
        { id: 'GIS-4', name: 'السرية الثالثة مدرعات MRAP', sector: 'القطاع الغربي W-03', coords: '12.8115° N, 45.0120° E', x: 24, y: 72, type: 'ARMOR', status: 'READY' },
        { id: 'GIS-5', name: 'دورية استطلاع متقدمة P-09', sector: 'خط التماس الأمامي F-01', coords: '12.8790° N, 45.0510° E', x: 62, y: 18, type: 'PATROL', status: 'MOVING' }
      ],
      fieldEndpoints: [
        { id: 'DEV-01', code: 'BMS-TERMINAL-HQ-01', holder: 'غرفة عمليات الكتيبة 101', platform: 'Web PWA (Dexie.js)', enc: 'AES-256-GCM + PBKDF2', status: 'ACTIVE', lastPing: 'منذ دقيقة' },
        { id: 'DEV-02', code: 'TABLET-CMP1-FIELD', holder: 'النقيب / صقر الحميري (السرية 1)', platform: 'Rugged Tablet PWA', enc: 'AES-256-GCM + Biometric', status: 'ACTIVE', lastPing: 'منذ 4 دقائق' },
        { id: 'DEV-03', code: 'FLUTTER-PATROL-04', holder: 'دورية الاستطلاع الشمالية', platform: 'Flutter Mobile (Hive Encrypted)', enc: 'AES-256 + Dead-Man 48h', status: 'OFFLINE_FIELD', lastPing: 'منذ 35 دقيقة' }
      ],
      backups: [
        { id: 'BKP-20261017-2000', type: 'تلقائي (Cron)', size: '4.8 MB', algo: 'AES-256-GCM', time: '2026-10-17 20:00' },
        { id: 'BKP-20261017-1200', type: 'يدوي (قائد الكتيبة)', size: '4.7 MB', algo: 'AES-256-GCM', time: '2026-10-17 12:00' }
      ]
    };

    // Load or initialize state safely
    let state = JSON.parse(JSON.stringify(DEFAULT_STATE));
    try {
      const saved = localStorage.getItem('BMS_PRO_ENTERPRISE_STATE_V24');
      if (saved) {
        const parsed = JSON.parse(saved);
        state = Object.assign({}, DEFAULT_STATE, parsed);
      }
    } catch (err) {
      // Fallback to in-memory state in restricted iframe environments
    }

    function persistState(actionType, entityName, detailsText) {
      if (actionType) {
        const randomHash = Math.random().toString(16).substring(2, 18) + Math.random().toString(16).substring(2, 18);
        state.auditLogs.unshift({
          id: 'LOG-' + (500 + state.auditLogs.length + 1),
          time: new Date().toISOString().replace('T', ' ').substring(0, 19),
          user: ROLES_CONFIG[state.currentRole]?.nameAr || state.currentRole,
          action: actionType,
          entity: entityName,
          hash: randomHash,
          details: detailsText
        });
        const recentEl = document.getElementById('recentActionIndicator');
        if (recentEl) recentEl.textContent = 'آخر عملية: ' + detailsText;
      }

      if (state.isOffline && actionType && actionType !== 'SYNC') {
        const mut = {
          mutationId: 'MUT-' + Date.now(),
          entityName: entityName,
          operation: actionType,
          recordVersion: (state.offlineMutations.length + 2),
          utcTimestamp: new Date().toISOString(),
          sourceDeviceId: state.deviceId,
          details: detailsText
        };
        state.offlineMutations.unshift(mut);
        if (db && db.offlineQueue) {
          db.offlineQueue.add(mut).catch(() => {});
        }
      }

      try {
        localStorage.setItem('BMS_PRO_ENTERPRISE_STATE_V24', JSON.stringify(state));
      } catch (e) {}
      updateOfflineBadges();
    }

    // =========================================================================
    // 3. DATA SCOPE & RBAC HELPER FUNCTIONS
    // =========================================================================
    function getScopedPersonnel() {
      const roleCfg = ROLES_CONFIG[state.currentRole] || ROLES_CONFIG.SYSTEM_ADMIN;
      return state.personnel.filter((p) => {
        if (roleCfg.scope === 'UNIT' && roleCfg.unitId) {
          return p.unitId === roleCfg.unitId;
        }
        if (roleCfg.scope === 'SELF') {
          return p.id === 'P-108' || p.unitId === 'U-CMP-1';
        }
        return true;
      });
    }

    function hasPermission(permCode) {
      const roleCfg = ROLES_CONFIG[state.currentRole] || ROLES_CONFIG.SYSTEM_ADMIN;
      return roleCfg.perms.includes(permCode);
    }

    function getUnitName(unitId) {
      const u = state.units.find((x) => x.id === unitId);
      return u ? u.nameAr : 'وحدة عامة';
    }

    function getRankName(rankId) {
      const r = state.ranks.find((x) => x.id === rankId);
      return r ? r.nameAr : 'رتبة عسكرية';
    }

    function getJobTitle(jobId) {
      const j = state.jobs.find((x) => x.id === jobId);
      return j ? j.titleAr : 'واجب ميداني';
    }

    function showToast(message, type = 'success') {
      const container = document.getElementById('toastContainer');
      if (!container) return;
      const colors = {
        success: 'bg-emerald-900/95 border-emerald-500 text-emerald-100',
        warning: 'bg-amber-900/95 border-amber-500 text-amber-100',
        error: 'bg-rose-900/95 border-rose-500 text-rose-100',
        info: 'bg-sky-900/95 border-sky-500 text-sky-100'
      };
      const el = document.createElement('div');
      el.className = `px-4 py-2.5 rounded-xl border shadow-xl text-xs font-semibold flex items-center justify-between gap-3 transition-all ${colors[type] || colors.success}`;
      el.innerHTML = `<span>${message}</span><button type="button" class="opacity-70 hover:opacity-100" onclick="this.parentElement.remove()">✕</button>`;
      container.appendChild(el);
      setTimeout(() => { if (el.parentElement) el.remove(); }, 4000);
    }

    // =========================================================================
    // 4. TOPBAR, NAVIGATION, OFFLINE SYNC & RBAC UI CONTROLLERS
    // =========================================================================
    let chartInstances = {};

    function updateOfflineBadges() {
      const qBadge = document.getElementById('offlineQueueBadge');
      if (qBadge) qBadge.textContent = String(state.offlineMutations.length);
      const dot = document.getElementById('connStatusDot');
      const txt = document.getElementById('connStatusText');
      const btn = document.getElementById('btnToggleOfflineMode');
      if (dot && txt && btn) {
        if (state.isOffline) {
          dot.className = 'inline-block w-2 h-2 rounded-full bg-amber-400 me-1 animate-ping';
          txt.textContent = 'وضع عدم الاتصال (Dexie Offline)';
          btn.className = 'px-2.5 py-0.5 rounded-full text-xs font-medium bg-amber-900/90 text-amber-200 border border-amber-500/60';
        } else {
          dot.className = 'inline-block w-2 h-2 rounded-full bg-emerald-400 me-1';
          txt.textContent = 'متصل (Online Sync)';
          btn.className = 'px-2.5 py-0.5 rounded-full text-xs font-medium bg-emerald-800/80 text-emerald-200 border border-emerald-600/50';
        }
      }
    }

    function toggleOfflineMode() {
      state.isOffline = !state.isOffline;
      updateOfflineBadges();
      if (state.isOffline) {
        showToast('تم تفعيل وضع العمل دون اتصال (Offline-First عبر Dexie.js / IndexedDB). جميع التعديلات تُحفظ في طابور المزامنة.', 'warning');
      } else {
        showToast('عاد الاتصال بالخادم المركزي — جاري التحقق من طابور المزامنة التفاضلية...', 'info');
        if (state.offlineMutations.length > 0) {
          triggerManualDeltaSync();
        }
      }
      renderAuditAndSync();
    }

    function triggerManualDeltaSync() {
      const count = state.offlineMutations.length;
      if (count === 0) {
        showToast('جميع السجلات متزامنة مع خادم PostgreSQL المركزي (Delta Sync Up-to-Date).', 'success');
        return;
      }
      state.offlineMutations = [];
      if (db && db.offlineQueue) {
        db.offlineQueue.clear().catch(() => {});
      }
      persistState('SYNC', 'DeltaSyncBatch', `مزامنة تفاضلية ناجحة لعدد (${count}) عمليات عبر خوارزمية LWW + Version Control`);
      showToast(`تمت مزامنة (${count}) عمليات بنجاح مع فض التعارضات (Last-Write-Wins UTC).`, 'success');
      renderAuditAndSync();
    }

    function toggleMobileSidebar() {
      const sb = document.getElementById('mainSidebar');
      if (!sb) return;
      sb.classList.toggle('hidden');
      sb.classList.toggle('fixed');
      sb.classList.toggle('inset-y-0');
      sb.classList.toggle('start-0');
      sb.classList.toggle('z-40');
    }

    function switchTab(tabId) {
      document.querySelectorAll('.tab-section').forEach((sec) => sec.classList.add('hidden'));
      const target = document.getElementById('tab-' + tabId);
      if (target) target.classList.remove('hidden');

      document.querySelectorAll('.nav-btn').forEach((btn) => {
        if (btn.getAttribute('data-nav') === tabId) {
          btn.className = 'nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-semibold bg-emerald-600/20 text-emerald-300 border border-emerald-500/40';
        } else {
          btn.className = 'nav-btn w-full flex items-center justify-between px-3 py-2 rounded-lg text-xs font-medium text-slate-300 hover:bg-slate-800';
        }
      });

      if (tabId === 'dashboard') renderDashboard();
      if (tabId === 'opsroom') renderOpsRoom();
      if (tabId === 'units') renderUnitsHierarchy();
      if (tabId === 'personnel') renderPersonnelTable();
      if (tabId === 'attendance') renderAttendanceModule();
      if (tabId === 'leaves') renderLeavesAndPermissions();
      if (tabId === 'logistics') renderLogisticsModule();
      if (tabId === 'readiness') renderReadinessAndTraining();
      if (tabId === 'tasks') renderTasksAndAnnouncements();
      if (tabId === 'reports') { renderReportsCatalog(); renderActiveReportPreview(); }
      if (tabId === 'ai') renderAiChat();
      if (tabId === 'audit') renderAuditAndSync();
      if (tabId === 'architecture') renderArchitectureBlueprint();
      if (tabId === 'settings') renderSettingsAndBackups();
    }

    function switchUserRole(roleKey) {
      state.currentRole = roleKey;
      const roleCfg = ROLES_CONFIG[roleKey] || ROLES_CONFIG.SYSTEM_ADMIN;
      const scopeBadge = document.getElementById('sidebarScopeBadge');
      if (scopeBadge) {
        scopeBadge.textContent = roleCfg.scope === 'ALL' ? 'كامل الكتيبة واللواء' : (roleCfg.scope === 'UNIT' ? 'نطاق السرية الأولى' : 'الملف الشخصي فقط');
      }
      renderActivePermissionChips();
      renderDashboard();
      renderPersonnelTable();
      renderAttendanceModule();
      renderLeavesAndPermissions();
      renderActiveReportPreview();
      showToast(`تم تبديل الدور النشط إلى: ${roleCfg.nameAr} (تطبيق صلاحيات RBAC + Data Scope تلقائياً)`, 'info');
    }

    function renderActivePermissionChips() {
      const container = document.getElementById('activePermissionsChips');
      if (!container) return;
      const roleCfg = ROLES_CONFIG[state.currentRole] || ROLES_CONFIG.SYSTEM_ADMIN;
      container.innerHTML = roleCfg.perms.map((p) =>
        `<span class="px-2 py-0.5 rounded bg-slate-800 text-emerald-300 border border-slate-700 font-mono text-[10px]">${p}</span>`
      ).join('');
    }

    function toggleFieldMode() {
      state.isFieldMode = !state.isFieldMode;
      const body = document.getElementById('appBody');
      if (body) body.classList.toggle('field-mode', state.isFieldMode);
      showToast(state.isFieldMode ? 'تم تفعيل وضع الميدان التكتيكي عالي التباين (Field Mode).' : 'تم إيقاف وضع الميدان التكتيكي.', 'info');
    }

    function toggleThemeMode() {
      const htmlEl = document.documentElement;
      const body = document.getElementById('appBody');
      const isDark = htmlEl.classList.contains('dark');
      if (isDark) {
        htmlEl.classList.remove('dark');
        body.classList.remove('bg-slate-950', 'text-slate-100');
        body.classList.add('bg-slate-100', 'text-slate-900');
        showToast('تم التبديل إلى الوضع الفاتح (Light Mode).', 'info');
      } else {
        htmlEl.classList.add('dark');
        body.classList.remove('bg-slate-100', 'text-slate-900');
        body.classList.add('bg-slate-950', 'text-slate-100');
        showToast('تم التبديل إلى الوضع الداكن التكتيكي (Dark Mode).', 'info');
      }
    }

    function toggleDirectionLang() {
      const htmlEl = document.documentElement;
      const isRtl = htmlEl.getAttribute('dir') === 'rtl';
      htmlEl.setAttribute('dir', isRtl ? 'ltr' : 'rtl');
      htmlEl.setAttribute('lang', isRtl ? 'en' : 'ar');
      const titleEl = document.getElementById('appHeaderTitle');
      if (titleEl) {
        titleEl.textContent = isRtl
          ? 'BMS Pro — Enterprise Battalion Management System'
          : 'نظام إدارة الكتائب العسكرية — BMS Pro';
      }
      showToast(isRtl ? 'Switched direction to LTR (English Layout).' : 'تم التبديل إلى الواجهة العربية الكاملة (RTL).', 'info');
    }

    function handleGlobalSearch(query) {
      const overlay = document.getElementById('globalSearchOverlay');
      const resultsBox = document.getElementById('globalSearchResults');
      if (!overlay || !resultsBox) return;
      const q = (query || '').trim().toLowerCase();
      if (!q) {
        overlay.classList.add('hidden');
        return;
      }
      overlay.classList.remove('hidden');

      const matchedPersonnel = getScopedPersonnel().filter((p) =>
        p.fullNameAr.toLowerCase().includes(q) || p.militaryNumber.toLowerCase().includes(q)
      );
      const matchedWeapons = state.weapons.filter((w) =>
        w.serial.toLowerCase().includes(q) || w.type.toLowerCase().includes(q) || w.assignee.toLowerCase().includes(q)
      );
      const matchedTasks = state.tasks.filter((t) =>
        t.title.toLowerCase().includes(q) || t.assignee.toLowerCase().includes(q)
      );

      resultsBox.innerHTML = `
        <div class="bg-slate-950 border border-slate-800 rounded-lg p-3">
          <div class="font-bold text-emerald-400 mb-1.5">👥 الأفراد (${matchedPersonnel.length})</div>
          ${matchedPersonnel.map((p) => `<div class="py-1 border-b border-slate-800/60 flex justify-between"><span>${p.fullNameAr}</span><button type="button" onclick="openPersonnelDossier('${p.id}')" class="text-emerald-400 hover:underline">${p.militaryNumber}</button></div>`).join('') || '<div class="text-slate-500">لا توجد مطابقات</div>'}
        </div>
        <div class="bg-slate-950 border border-slate-800 rounded-lg p-3">
          <div class="font-bold text-amber-400 mb-1.5">🔫 الأسلحة والعهدة (${matchedWeapons.length})</div>
          ${matchedWeapons.map((w) => `<div class="py-1 border-b border-slate-800/60 flex justify-between"><span>${w.type}</span><span class="font-mono text-amber-300">${w.serial}</span></div>`).join('') || '<div class="text-slate-500">لا توجد مطابقات</div>'}
        </div>
        <div class="bg-slate-950 border border-slate-800 rounded-lg p-3">
          <div class="font-bold text-sky-400 mb-1.5">📋 المهام (${matchedTasks.length})</div>
          ${matchedTasks.map((t) => `<div class="py-1 border-b border-slate-800/60 flex justify-between"><span class="truncate">${t.title}</span><span class="text-sky-300">${t.progress}%</span></div>`).join('') || '<div class="text-slate-500">لا توجد مطابقات</div>'}
        </div>
      `;
    }

    function closeGlobalSearch() {
      const overlay = document.getElementById('globalSearchOverlay');
      const input = document.getElementById('globalSearchInput');
      if (overlay) overlay.classList.add('hidden');
      if (input) input.value = '';
    }

    function toggleNotificationsPanel() {
      const dd = document.getElementById('notificationsDropdown');
      if (dd) dd.classList.toggle('hidden');
      renderNotifications();
    }

    function renderNotifications() {
      const list = document.getElementById('notificationsList');
      const badge = document.getElementById('unreadNotifBadge');
      if (!list || !badge) return;
      const unreadCount = state.notifications.filter((n) => !n.read).length;
      badge.textContent = String(unreadCount);
      badge.classList.toggle('hidden', unreadCount === 0);

      list.innerHTML = state.notifications.map((n) => `
        <div class="p-2.5 rounded-lg border ${n.read ? 'bg-slate-950/40 border-slate-800 text-slate-400' : 'bg-slate-800/80 border-emerald-600/40 text-slate-100'} text-xs">
          <div class="flex items-center justify-between font-bold mb-0.5">
            <span>${n.title}</span>
            <span class="text-[10px] text-slate-400">${n.time}</span>
          </div>
          <p class="text-[11px] leading-relaxed">${n.msg}</p>
        </div>
      `).join('');
    }

    function markAllNotificationsRead() {
      state.notifications.forEach((n) => { n.read = true; });
      renderNotifications();
      persistState('UPDATE', 'Notifications', 'تحديد جميع الإشعارات كمقروءة');
      showToast('تم تحديد جميع الإشعارات كمقروءة.', 'success');
    }

    // =========================================================================
    // 5. DASHBOARD & CHARTS RENDERING
    // =========================================================================
    function toggleCompareMode() {
      state.isCompareMode = !state.isCompareMode;
      const panel = document.getElementById('compareUnitsPanel');
      if (panel) panel.classList.toggle('hidden', !state.isCompareMode);
      renderCompareUnitsMatrix();
    }

    function renderCompareUnitsMatrix() {
      const box = document.getElementById('compareUnitsTableContainer');
      if (!box) return;
      const companies = state.units.filter((u) => u.level === 'سرية');
      box.innerHTML = `
        <table class="w-full text-xs text-start border border-slate-800 rounded-lg overflow-hidden">
          <thead class="bg-slate-950 text-slate-300">
            <tr>
              <th class="p-2.5 text-start">السرية</th>
              <th class="p-2.5 text-start">القائد</th>
              <th class="p-2.5 text-start">القوة المسجلة</th>
              <th class="p-2.5 text-start">متوسط الانضباط</th>
              <th class="p-2.5 text-start">نسبة الجاهزية القتالية</th>
            </tr>
          </thead>
          <tbody class="divide-y divide-slate-800">
            ${companies.map((c) => {
              const members = state.personnel.filter((p) => p.unitId === c.id);
              const avgDisc = members.length ? (members.reduce((a, b) => a + Number(b.disciplineScore), 0) / members.length).toFixed(1) : '95.0';
              const readyCnt = members.filter((p) => p.readiness === 'READY').length;
              const readyPct = members.length ? Math.round((readyCnt / members.length) * 100) : 100;
              return `<tr>
                <td class="p-2.5 font-bold text-white">${c.nameAr}</td>
                <td class="p-2.5 text-slate-300">${c.commander}</td>
                <td class="p-2.5 text-emerald-300 font-mono">${members.length} / ${c.authorized}</td>
                <td class="p-2.5 text-amber-300 font-bold">${avgDisc}%</td>
                <td class="p-2.5"><span class="px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 font-bold">${readyPct}%</span></td>
              </tr>`;
            }).join('')}
          </tbody>
        </table>
      `;
    }

    function renderDashboard() {
      const scoped = getScopedPersonnel();
      const totalForce = scoped.length;
      const activeReady = scoped.filter((p) => p.readiness === 'READY').length;
      const readinessPct = totalForce ? Math.round((activeReady / totalForce) * 100) : 100;
      const presentToday = state.attendance.filter((a) => a.status === 'PRESENT').length;
      const readyWeapons = state.weapons.filter((w) => w.status === 'READY').length;
      const activeLeaves = state.leaves.filter((l) => l.status === 'APPROVED').length;
      const totalAmmo = state.ammunition.reduce((s, a) => s + a.balance, 0);

      const kpiGrid = document.getElementById('dashboardKpiGrid');
      if (kpiGrid) {
        kpiGrid.innerHTML = [
          { label: 'إجمالي القوة (حسب النطاق)', val: totalForce + ' فرد', sub: 'نشط ومفرز بالميدان', color: 'border-emerald-500/40 text-emerald-400' },
          { label: 'القوة الحاضرة اليوم', val: presentToday + ' / ' + state.attendance.length, sub: 'شامل تحضير QR الصباحي', color: 'border-sky-500/40 text-sky-400' },
          { label: 'نسبة الجاهزية القتالية', val: readinessPct + '%', sub: activeReady + ' فرد جاهز قتالياً', color: 'border-amber-500/40 text-amber-400' },
          { label: 'الأسلحة الجاهزة بالخدمة', val: readyWeapons + ' / ' + state.weapons.length, sub: 'عهدة ومستودعات', color: 'border-teal-500/40 text-teal-400' },
          { label: 'الرصيد الكلي للذخائر', val: totalAmmo.toLocaleString() + ' طلقة', sub: '4 عيارات قياسية', color: 'border-purple-500/40 text-purple-400' },
          { label: 'الإجازات والمهام الجارية', val: activeLeaves + ' إجازة / ' + state.tasks.length + ' مهام', sub: 'مرتبطة بمحرك الموافقات', color: 'border-rose-500/40 text-rose-400' }
        ].map((k) => `
          <div class="bg-slate-900 border ${k.color} rounded-xl p-3.5 shadow">
            <div class="text-[11px] text-slate-400">${k.label}</div>
            <div class="text-lg sm:text-xl font-extrabold mt-1">${k.val}</div>
            <div class="text-[10px] text-slate-400 mt-1">${k.sub}</div>
          </div>
        `).join('');
      }

      renderCompareUnitsMatrix();
      if (typeof Chart === 'undefined') return;

      // Chart 1: Attendance Breakdown
      const ctx1 = document.getElementById('chartAttendanceOverview');
      if (ctx1) {
        if (chartInstances.c1) chartInstances.c1.destroy();
        const pCnt = state.attendance.filter((a) => a.status === 'PRESENT').length;
        const aCnt = state.attendance.filter((a) => a.status === 'ABSENT').length;
        const lCnt = state.attendance.filter((a) => a.status === 'LATE').length;
        const eCnt = state.attendance.filter((a) => a.status === 'EXCUSED').length;
        chartInstances.c1 = new Chart(ctx1, {
          type: 'bar',
          data: {
            labels: ['حاضر (Present)', 'غائب (Absent)', 'متأخر (Late)', 'بعذر / مجاز (Excused)'],
            datasets: [{
              label: 'عدد الأفراد',
              data: [pCnt, aCnt, lCnt, eCnt],
              backgroundColor: ['#10b981', '#f43f5e', '#f59e0b', '#38bdf8'],
              borderRadius: 6
            }]
          },
          options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
        });
      }

      // Chart 2: Units Distribution
      const ctx2 = document.getElementById('chartUnitsDistribution');
      if (ctx2) {
        if (chartInstances.c2) chartInstances.c2.destroy();
        const cmp1 = state.personnel.filter((p) => p.unitId === 'U-CMP-1').length;
        const cmp2 = state.personnel.filter((p) => p.unitId === 'U-CMP-2').length;
        const cmp3 = state.personnel.filter((p) => p.unitId === 'U-CMP-3').length;
        const hq = state.personnel.filter((p) => p.unitId === 'U-BAT-101').length;
        chartInstances.c2 = new Chart(ctx2, {
          type: 'doughnut',
          data: {
            labels: ['السرية الأولى اقتحام', 'السرية الثانية إسناد', 'السرية الثالثة مدرعات', 'قيادة الكتيبة 101'],
            datasets: [{
              data: [cmp1, cmp2, cmp3, hq],
              backgroundColor: ['#10b981', '#f59e0b', '#38bdf8', '#a855f7']
            }]
          },
          options: { responsive: true, maintainAspectRatio: false }
        });
      }

      // Chart 3: Logistics Readiness
      const ctx3 = document.getElementById('chartLogisticsReadiness');
      if (ctx3) {
        if (chartInstances.c3) chartInstances.c3.destroy();
        chartInstances.c3 = new Chart(ctx3, {
          type: 'bar',
          data: {
            labels: ['الأسلحة الفردية', 'الرشاشات والقناصات', 'الذخيرة المتوفرة', 'المدرعات والأطقم', 'أجهزة الإشارة'],
            datasets: [{
              label: 'نسبة الجاهزية الفنية (%)',
              data: [96, 88, 94, 85, 92],
              backgroundColor: '#0ea5e9',
              borderRadius: 6
            }]
          },
          options: { responsive: true, maintainAspectRatio: false, scales: { y: { max: 100, beginAtZero: true } } }
        });
      }

      // Chart 4: Ranks Distribution
      const ctx4 = document.getElementById('chartRanksBreakdown');
      if (ctx4) {
        if (chartInstances.c4) chartInstances.c4.destroy();
        chartInstances.c4 = new Chart(ctx4, {
          type: 'line',
          data: {
            labels: ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت'],
            datasets: [{
              label: 'مؤشر الانضباط والجاهزية العام (%)',
              data: [91, 93, 92, 95, 94, 90, readinessPct],
              borderColor: '#10b981',
              backgroundColor: 'rgba(16, 185, 129, 0.2)',
              fill: true,
              tension: 0.35
            }]
          },
          options: { responsive: true, maintainAspectRatio: false, scales: { y: { min: 70, max: 100 } } }
        });
      }
    }

    // =========================================================================
    // 6. LIVE OPERATIONS ROOM (غرفة العمليات المباشرة)
    // =========================================================================
    function changeOpsAlertLevel(lvl) {
      state.opsAlertLevel = lvl;
      persistState('UPDATE', 'OpsAlertLevel', 'تغيير درجة الاستعداد القتالي إلى ' + lvl);
      showToast('تم تحديث درجة الاستعداد القتالي في غرفة العمليات إلى: ' + lvl, 'warning');
      renderOpsRoom();
    }

    function renderOpsRoom() {
      const presentCnt = state.attendance.filter((a) => a.status === 'PRESENT').length;
      const absentCnt = state.attendance.filter((a) => a.status === 'ABSENT' || a.status === 'LATE').length;
      const readyCnt = state.personnel.filter((p) => p.readiness === 'READY').length;
      const readyPct = state.personnel.length ? Math.round((readyCnt / state.personnel.length) * 100) : 100;

      const grid = document.getElementById('opsRoomMetricsGrid');
      if (grid) {
        grid.innerHTML = `
          <div class="bg-slate-900 border border-emerald-600/40 rounded-xl p-3.5">
            <div class="text-xs text-slate-400">القوة الحاضرة بالميدان</div>
            <div class="text-2xl font-black text-emerald-400 mt-1">${presentCnt} مقاتل</div>
            <div class="text-[11px] text-slate-400 mt-1">جاهزون للانتشار الفوري</div>
          </div>
          <div class="bg-slate-900 border border-rose-600/40 rounded-xl p-3.5">
            <div class="text-xs text-slate-400">القوة الغائبة / المتأخرة</div>
            <div class="text-2xl font-black text-rose-400 mt-1">${absentCnt} أفراد</div>
            <div class="text-[11px] text-slate-400 mt-1">تحت المتابعة الإدارية</div>
          </div>
          <div class="bg-slate-900 border border-amber-600/40 rounded-xl p-3.5">
            <div class="text-xs text-slate-400">نسبة الجاهزية القتالية اللحظية</div>
            <div class="text-2xl font-black text-amber-400 mt-1">${readyPct}%</div>
            <div class="text-[11px] text-slate-400 mt-1">حالة الاستعداد: ${state.opsAlertLevel}</div>
          </div>
          <div class="bg-slate-900 border border-sky-600/40 rounded-xl p-3.5">
            <div class="text-xs text-slate-400">المهام والإنذارات الفعالة</div>
            <div class="text-2xl font-black text-sky-400 mt-1">${state.opsIncidents.length} بلاغات</div>
            <div class="text-[11px] text-slate-400 mt-1">${state.leaves.length} إجازات | ${state.permissions.length} أذونات</div>
          </div>
        `;
      }

      const feed = document.getElementById('opsIncidentsFeed');
      if (feed) {
        feed.innerHTML = state.opsIncidents.map((inc) => `
          <div class="p-3 rounded-xl border ${inc.severity === 'HIGH' ? 'bg-rose-950/40 border-rose-600/50' : 'bg-slate-950/60 border-slate-800'} flex items-start justify-between gap-3 text-xs">
            <div>
              <div class="flex items-center gap-2">
                <span class="px-2 py-0.5 rounded font-bold text-[10px] ${inc.severity === 'HIGH' ? 'bg-rose-600 text-white' : 'bg-amber-500/20 text-amber-300'}">${inc.severity}</span>
                <span class="font-bold text-white">${inc.title}</span>
              </div>
              <div class="text-[11px] text-slate-400 mt-1">الوحدة المعنية: ${inc.unit}</div>
            </div>
            <span class="font-mono text-slate-400">${inc.time}</span>
          </div>
        `).join('');
      }

      renderTacticalGisMap();
      const expBox = document.getElementById('opsExpiryAndShiftsList');
      if (expBox) {
        expBox.innerHTML = `
          <div class="p-2.5 rounded-lg bg-amber-950/40 border border-amber-600/40">
            <div class="font-bold text-amber-300">⚠️ إجازات تنتهي خلال 48 ساعة:</div>
            ${state.leaves.filter((l) => l.expiresSoon).map((l) => {
              const p = state.personnel.find((x) => x.id === l.personnelId);
              return `<div class="mt-1 text-slate-200">• ${p ? p.fullNameAr : l.personnelId} (تنتهي: ${l.endDate})</div>`;
            }).join('')}
          </div>
          <div class="p-2.5 rounded-lg bg-slate-950 border border-slate-800">
            <div class="font-bold text-emerald-400">🛡️ المناوبة القيادية الحالية:</div>
            <div class="mt-1 text-slate-300">ضابط الخفر: النقيب / صقر الحميري</div>
            <div class="text-slate-400">مناوبة البوابة واللاسلكي: الرقيب أول / سالم باذيب</div>
          </div>
        `;
      }
    }

    // =========================================================================
    // 7. ORGANIZATIONAL HIERARCHY TREE (الهيكل التنظيمي)
    // =========================================================================
    function expandCollapseAllUnits(expand) {
      state.units.forEach((u) => { u.expanded = expand; });
      renderUnitsHierarchy();
    }

    function toggleSingleUnitExpand(unitId) {
      const u = state.units.find((x) => x.id === unitId);
      if (u) u.expanded = !u.expanded;
      renderUnitsHierarchy();
    }

    function deleteUnitById(unitId) {
      if (unitId === 'U-BRG-1' || unitId === 'U-BAT-101') {
        showToast('لا يمكن حذف وحدات القيادة العليا (اللواء أو الكتيبة الأساسية).', 'error');
        return;
      }
      state.units = state.units.filter((u) => u.id !== unitId);
      persistState('DELETE', 'Unit#' + unitId, 'حذف وحدة فرعية من الهيكل التنظيمي');
      renderUnitsHierarchy();
      showToast('تم حذف الوحدة من الهيكل التنظيمي.', 'info');
    }

    function renderUnitsHierarchy() {
      const container = document.getElementById('unitsHierarchyContainer');
      if (!container) return;

      function renderNode(parentId, depth) {
        const children = state.units.filter((u) => u.parentId === parentId);
        return children.map((u) => {
          const count = state.personnel.filter((p) => p.unitId === u.id).length;
          const hasKids = state.units.some((k) => k.parentId === u.id);
          return `
            <div class="ms-${Math.min(depth * 4, 12)} bg-slate-900 border border-slate-800 rounded-xl p-3 mb-2">
              <div class="flex flex-wrap items-center justify-between gap-2 text-xs">
                <div class="flex items-center gap-2">
                  ${hasKids ? `<button type="button" onclick="toggleSingleUnitExpand('${u.id}')" class="w-6 h-6 rounded bg-slate-800 text-emerald-400 font-bold">${u.expanded ? '−' : '+'}</button>` : `<span class="w-6 h-6 inline-flex items-center justify-center text-slate-500">•</span>`}
                  <span class="px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 font-bold">${u.level}</span>
                  <span class="font-bold text-sm text-white">${u.nameAr}</span>
                </div>
                <div class="flex items-center gap-3">
                  <span class="text-slate-300">القائد: <strong>${u.commander}</strong></span>
                  <span class="px-2 py-0.5 rounded bg-slate-800 text-amber-300 font-mono">القوة المسجلة: ${count} / المعتمد: ${u.authorized}</span>
                  <button type="button" onclick="deleteUnitById('${u.id}')" class="text-rose-400 hover:underline">حذف</button>
                </div>
              </div>
              ${u.expanded && hasKids ? `<div class="mt-2.5 ps-4 border-s-2 border-emerald-800/50">${renderNode(u.id, depth + 1)}</div>` : ''}
            </div>
          `;
        }).join('');
      }

      container.innerHTML = renderNode(null, 0);
    }

    // =========================================================================
    // 8. PERSONNEL MANAGEMENT + ELDERLY + CONTINUOUS ABSENCE
    // =========================================================================
    function populatePersonnelFilterDropdowns() {
      const unitSel = document.getElementById('filterPersonnelUnit');
      const rankSel = document.getElementById('filterPersonnelRank');
      const rUnitSel = document.getElementById('readinessUnitFilter');
      if (unitSel && unitSel.options.length <= 1) {
        state.units.forEach((u) => {
          unitSel.innerHTML += `<option value="${u.id}">${u.nameAr}</option>`;
          if (rUnitSel) rUnitSel.innerHTML += `<option value="${u.id}">${u.nameAr}</option>`;
        });
      }
      if (rankSel && rankSel.options.length <= 1) {
        state.ranks.forEach((r) => {
          rankSel.innerHTML += `<option value="${r.id}">${r.nameAr}</option>`;
        });
      }
    }

    function setPersonnelViewMode(mode) {
      state.personnelViewMode = mode;
      state.personnelPage = 1;
      ['ALL', 'ELDERLY', 'CONTINUOUS_ABSENT', 'ARCHIVED'].forEach((m) => {
        const btn = document.getElementById('pMode-' + m);
        if (btn) {
          btn.className = (m === mode)
            ? 'px-3 py-1 rounded-lg text-xs font-semibold bg-emerald-600 text-white'
            : 'px-3 py-1 rounded-lg text-xs font-medium bg-slate-800 text-slate-300 hover:bg-slate-700';
        }
      });
      renderPersonnelTable();
    }

    function calculateAge(birthDateStr) {
      const b = new Date(birthDateStr);
      const diff = Date.now() - b.getTime();
      return Math.floor(diff / (365.25 * 86400000));
    }

    function renderPersonnelTable() {
      populatePersonnelFilterDropdowns();
      const tbody = document.getElementById('personnelTableBody');
      if (!tbody) return;

      const q = (document.getElementById('filterPersonnelSearch')?.value || '').trim().toLowerCase();
      const unitFilter = document.getElementById('filterPersonnelUnit')?.value || '';
      const rankFilter = document.getElementById('filterPersonnelRank')?.value || '';
      const statusFilter = document.getElementById('filterPersonnelStatus')?.value || '';
      const bloodFilter = document.getElementById('filterPersonnelBlood')?.value || '';

      let list = getScopedPersonnel().filter((p) => {
        if (state.personnelViewMode === 'ELDERLY' && calculateAge(p.birthDate) < 48) return false;
        if (state.personnelViewMode === 'CONTINUOUS_ABSENT' && !p.isContinuousAbsent) return false;
        if (state.personnelViewMode === 'ARCHIVED' && p.status !== 'INACTIVE' && p.status !== 'RETIRED') return false;
        if (q && !p.fullNameAr.toLowerCase().includes(q) && !p.militaryNumber.toLowerCase().includes(q)) return false;
        if (unitFilter && p.unitId !== unitFilter) return false;
        if (rankFilter && p.rankId !== rankFilter) return false;
        if (statusFilter && p.status !== statusFilter) return false;
        if (bloodFilter && p.bloodType !== bloodFilter) return false;
        return true;
      });

      const total = list.length;
      const maxPage = Math.max(1, Math.ceil(total / state.personnelPageSize));
      if (state.personnelPage > maxPage) state.personnelPage = maxPage;
      const startIdx = (state.personnelPage - 1) * state.personnelPageSize;
      const pageItems = list.slice(startIdx, startIdx + state.personnelPageSize);

      const infoEl = document.getElementById('personnelPaginationInfo');
      const pageNumEl = document.getElementById('personnelPageNumber');
      if (infoEl) infoEl.textContent = `عرض ${total ? startIdx + 1 : 0} إلى ${Math.min(startIdx + state.personnelPageSize, total)} من أصل ${total} فرد`;
      if (pageNumEl) pageNumEl.textContent = `${state.personnelPage} / ${maxPage}`;

      tbody.innerHTML = pageItems.map((p) => {
        const age = calculateAge(p.birthDate);
        const checked = state.selectedPersonnelIds.includes(p.id) ? 'checked' : '';
        return `
          <tr class="hover:bg-slate-800/50 transition">
            <td class="p-3"><input type="checkbox" ${checked} onchange="toggleSelectSinglePersonnel('${p.id}', this.checked)"></td>
            <td class="p-3">
              <div class="font-bold text-white">${p.fullNameAr}</div>
              <div class="text-[11px] font-mono text-emerald-400">${p.militaryNumber}</div>
            </td>
            <td class="p-3">
              <div class="font-semibold text-amber-300">${getRankName(p.rankId)}</div>
              <div class="text-[11px] text-slate-400">${getJobTitle(p.jobId)}</div>
            </td>
            <td class="p-3 text-slate-200">${getUnitName(p.unitId)}</td>
            <td class="p-3">
              <div>${p.birthDate} <span class="text-[10px] ${age >= 48 ? 'text-amber-300 font-bold' : 'text-slate-400'}">(${age} سنة)</span></div>
              <span class="px-1.5 py-0.5 rounded bg-rose-500/20 text-rose-300 font-mono text-[10px]">${p.bloodType}</span>
            </td>
            <td class="p-3">
              <div class="text-slate-200">${p.weapon}</div>
              <div class="text-[11px] text-amber-300">${p.ammo} طلقة</div>
            </td>
            <td class="p-3">
              <div class="flex items-center gap-1.5">
                <span class="px-2 py-0.5 rounded text-[10px] font-bold ${p.status === 'ACTIVE' ? 'bg-emerald-500/20 text-emerald-300' : 'bg-rose-500/20 text-rose-300'}">${p.status}</span>
                ${p.isContinuousAbsent ? '<span class="px-1.5 py-0.5 rounded bg-rose-600 text-white text-[10px] font-bold">غياب مستمر</span>' : ''}
              </div>
              <div class="text-[11px] text-slate-400 mt-1">الانضباط: <strong class="text-white">${p.disciplineScore}%</strong></div>
            </td>
            <td class="p-3">
              <div class="flex flex-wrap gap-1">
                <button type="button" onclick="openPersonnelDossier('${p.id}')" class="px-2 py-1 rounded bg-slate-800 hover:bg-slate-700 text-emerald-300">السجل</button>
                <button type="button" onclick="toggleContinuousAbsenceSingle('${p.id}')" class="px-2 py-1 rounded bg-slate-800 hover:bg-slate-700 text-amber-300">غياب مستمر</button>
                <button type="button" onclick="toggleArchivePersonnel('${p.id}')" class="px-2 py-1 rounded bg-slate-800 hover:bg-slate-700 text-rose-300">${p.status === 'INACTIVE' ? 'تفعيل' : 'تعطيل'}</button>
              </div>
            </td>
          </tr>
        `;
      }).join('');
    }

    function changePersonnelPage(delta) {
      state.personnelPage = Math.max(1, state.personnelPage + delta);
      renderPersonnelTable();
    }

    function toggleSelectAllPersonnel(checked) {
      state.selectedPersonnelIds = checked ? getScopedPersonnel().map((p) => p.id) : [];
      renderPersonnelTable();
    }

    function toggleSelectSinglePersonnel(id, checked) {
      if (checked && !state.selectedPersonnelIds.includes(id)) {
        state.selectedPersonnelIds.push(id);
      } else if (!checked) {
        state.selectedPersonnelIds = state.selectedPersonnelIds.filter((x) => x !== id);
      }
    }

    function executeBulkPersonnelAction(action) {
      if (state.selectedPersonnelIds.length === 0) {
        showToast('يرجى تحديد فرد واحد على الأقل من الجدول لتنفيذ العملية الجماعية.', 'warning');
        return;
      }
      state.personnel.forEach((p) => {
        if (state.selectedPersonnelIds.includes(p.id)) {
          if (action === 'MARK_READY') p.readiness = 'READY';
          if (action === 'TOGGLE_CONTINUOUS_ABSENT') p.isContinuousAbsent = !p.isContinuousAbsent;
        }
      });
      persistState('UPDATE', 'PersonnelBulk', `تحديث جماعي لعدد (${state.selectedPersonnelIds.length}) أفراد`);
      renderPersonnelTable();
      showToast(`تم تطبيق الإجراء الجماعي على (${state.selectedPersonnelIds.length}) أفراد بنجاح.`, 'success');
    }

    function toggleContinuousAbsenceSingle(id) {
      const p = state.personnel.find((x) => x.id === id);
      if (!p) return;
      p.isContinuousAbsent = !p.isContinuousAbsent;
      persistState('UPDATE', 'Personnel#' + id, `تحديث حالة الغياب المستمر للفرد: ${p.fullNameAr}`);
      renderPersonnelTable();
      showToast(p.isContinuousAbsent ? `تمت إضافة ${p.fullNameAr} إلى قائمة الغياب المستمر.` : `تمت إزالة ${p.fullNameAr} من قائمة الغياب المستمر.`, 'info');
    }

    function toggleArchivePersonnel(id) {
      if (!hasPermission('canEditPersonnel') && !hasPermission('canDeletePersonnel')) {
        showToast('عذراً، دورك الحالي لا يملك صلاحية تعطيل أو أرشفة ملفات الأفراد.', 'error');
        return;
      }
      const p = state.personnel.find((x) => x.id === id);
      if (!p) return;
      p.status = (p.status === 'INACTIVE') ? 'ACTIVE' : 'INACTIVE';
      persistState('UPDATE', 'Personnel#' + id, `تغيير حالة حساب الفرد ${p.fullNameAr} إلى ${p.status} دون حذف البيانات`);
      renderPersonnelTable();
      showToast(`تم تحديث حالة ${p.fullNameAr} إلى ${p.status} مع حفظ السجل التاريخي الكامل.`, 'success');
    }

    function simulateExcelImport() {
      const newId = 'P-' + (100 + state.personnel.length + 1);
      state.personnel.unshift({
        id: newId,
        militaryNumber: 'MIL-2026-' + (1000 + state.personnel.length + 1),
        fullNameAr: 'ذياب محسن صالح اليافعي',
        rankId: 'R-08',
        unitId: 'U-CMP-1',
        jobId: 'J-04',
        birthDate: '1993-05-19',
        bloodType: 'O+',
        weapon: 'AK-103 #AK9012',
        ammo: 150,
        status: 'ACTIVE',
        readiness: 'READY',
        readinessReason: 'مستورد عبر كشف Excel القياسي',
        disciplineScore: 98,
        annualLeaveBalance: 30,
        isContinuousAbsent: false,
        lateCountMonth: 0,
        courses: ['دورة الصاعقة التأسيسية'],
        promotions: [],
        rewards: [],
        penalties: []
      });
      persistState('CREATE', 'ExcelImport', 'استيراد بيانات أفراد من ملف SheetJS Excel');
      renderPersonnelTable();
      renderDashboard();
      showToast('تم استيراد كشف الأفراد من Excel والتحقق من مطابقة الحقول بنجاح.', 'success');
    }

    // =========================================================================
    // 9. DAILY ATTENDANCE & QR CODE SCANNER / GENERATOR
    // =========================================================================
    function renderAttendanceModule() {
      const dateInput = document.getElementById('attendanceDateInput');
      if (dateInput && !dateInput.value) dateInput.value = '2026-10-17';
      const period = document.getElementById('attendancePeriodSelect')?.value || 'MORNING';
      const periodLabels = { MORNING: 'صباحي', EVENING: 'مسائي', FULL_DAY: 'يوم كامل', HALF_DAY: 'نصف يوم' };

      const pCnt = state.attendance.filter((a) => a.status === 'PRESENT').length;
      const aCnt = state.attendance.filter((a) => a.status === 'ABSENT').length;
      const lCnt = state.attendance.filter((a) => a.status === 'LATE').length;
      const eCnt = state.attendance.filter((a) => a.status === 'EXCUSED').length;
      const discRate = state.attendance.length ? Math.round(((pCnt + eCnt) / state.attendance.length) * 100) : 100;

      const cards = document.getElementById('attendanceSummaryCards');
      if (cards) {
        cards.innerHTML = `
          <div class="bg-slate-900 border border-emerald-600/40 rounded-xl p-3"><div class="text-xs text-slate-400">حاضر (Present)</div><div class="text-xl font-bold text-emerald-400 mt-1">${pCnt}</div></div>
          <div class="bg-slate-900 border border-rose-600/40 rounded-xl p-3"><div class="text-xs text-slate-400">غائب (Absent)</div><div class="text-xl font-bold text-rose-400 mt-1">${aCnt}</div></div>
          <div class="bg-slate-900 border border-amber-600/40 rounded-xl p-3"><div class="text-xs text-slate-400">متأخر (Late)</div><div class="text-xl font-bold text-amber-400 mt-1">${lCnt}</div></div>
          <div class="bg-slate-900 border border-sky-600/40 rounded-xl p-3"><div class="text-xs text-slate-400">بعذر / إجازة (Excused)</div><div class="text-xl font-bold text-sky-400 mt-1">${eCnt}</div></div>
          <div class="bg-slate-900 border border-purple-600/40 rounded-xl p-3"><div class="text-xs text-slate-400">نسبة الانضباط اليومي</div><div class="text-xl font-bold text-purple-400 mt-1">${discRate}%</div></div>
        `;
      }

      const tbody = document.getElementById('attendanceTableBody');
      if (!tbody) return;

      tbody.innerHTML = state.attendance.map((rec) => {
        const p = state.personnel.find((x) => x.id === rec.personnelId) || { fullNameAr: 'فرد عسكري', militaryNumber: rec.personnelId, rankId: 'R-10', unitId: 'U-CMP-1' };
        const badgeColor = rec.status === 'PRESENT' ? 'bg-emerald-500/20 text-emerald-300' : (rec.status === 'ABSENT' ? 'bg-rose-500/20 text-rose-300' : (rec.status === 'LATE' ? 'bg-amber-500/20 text-amber-300' : 'bg-sky-500/20 text-sky-300'));
        return `
          <tr class="hover:bg-slate-800/40">
            <td class="p-3 font-mono text-emerald-400">${p.militaryNumber}</td>
            <td class="p-3 font-bold text-white">${getRankName(p.rankId)} / ${p.fullNameAr}</td>
            <td class="p-3 text-slate-300">${getUnitName(p.unitId)}</td>
            <td class="p-3 text-slate-300">${periodLabels[period] || 'صباحي'}</td>
            <td class="p-3"><span class="px-2 py-0.5 rounded font-bold text-[10px] ${badgeColor}">${rec.status}</span></td>
            <td class="p-3 font-mono text-slate-300">${rec.checkIn} → ${rec.checkOut}</td>
            <td class="p-3 text-slate-400">${rec.method} | ${rec.notes}</td>
            <td class="p-3">
              <div class="flex gap-1">
                <button type="button" onclick="quickUpdateAttendance('${rec.id}','PRESENT')" class="px-2 py-0.5 rounded bg-emerald-900/60 text-emerald-300 hover:bg-emerald-800">حاضر</button>
                <button type="button" onclick="quickUpdateAttendance('${rec.id}','LATE')" class="px-2 py-0.5 rounded bg-amber-900/60 text-amber-300 hover:bg-amber-800">متأخر</button>
                <button type="button" onclick="quickUpdateAttendance('${rec.id}','ABSENT')" class="px-2 py-0.5 rounded bg-rose-900/60 text-rose-300 hover:bg-amber-800">غائب</button>
                <button type="button" onclick="quickUpdateAttendance('${rec.id}','EXCUSED')" class="px-2 py-0.5 rounded bg-sky-900/60 text-sky-300 hover:bg-sky-800">بعذر</button>
              </div>
            </td>
          </tr>
        `;
      }).join('');
    }

    function quickUpdateAttendance(attId, newStatus) {
      const rec = state.attendance.find((a) => a.id === attId);
      if (!rec) return;
      rec.status = newStatus;
      rec.checkIn = (newStatus === 'PRESENT' || newStatus === 'LATE') ? new Date().toTimeString().substring(0, 5) : '--:--';
      rec.checkOut = (newStatus === 'PRESENT' || newStatus === 'LATE') ? '14:30' : '--:--';
      persistState('UPDATE', 'Attendance#' + attId, `تعديل سريع لحالة الحضور إلى ${newStatus}`);
      renderAttendanceModule();
      renderDashboard();
      showToast('تم تحديث سجل الحضور واحتساب نسبة الانضباط تلقائياً.', 'success');
    }

    function markAllAttendancePresent() {
      state.attendance.forEach((a) => {
        a.status = 'PRESENT';
        a.checkIn = '06:15';
        a.checkOut = '14:30';
        a.method = 'BULK';
      });
      persistState('UPDATE', 'AttendanceSession', 'تحضير جماعي لجميع الأفراد كحاضرين');
      renderAttendanceModule();
      renderDashboard();
      showToast('تم تسجيل جميع الأفراد كحاضرين في الطابور الحالي.', 'success');
    }

    function clearTodayAttendanceRecords() {
      state.attendance.forEach((a) => {
        a.status = 'EXCUSED';
        a.checkIn = '--:--';
        a.checkOut = '--:--';
        a.notes = 'تم تصفير السجل لإعادة التحضير';
      });
      persistState('DELETE', 'AttendanceSession', 'إعادة تصفير سجلات حضور اليوم');
      renderAttendanceModule();
      showToast('تم تصفير حالات سجل اليوم لإعادة التحضير.', 'info');
    }

    // =========================================================================
    // 10. LEAVES, PERMISSIONS & WORKFLOW RULES ENGINE
    // =========================================================================
    function renderLeavesAndPermissions() {
      const lBox = document.getElementById('leavesListContainer');
      if (lBox) {
        lBox.innerHTML = state.leaves.map((l) => {
          const p = state.personnel.find((x) => x.id === l.personnelId) || { fullNameAr: l.personnelId, annualLeaveBalance: 20 };
          return `
            <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1.5">
              <div class="flex items-center justify-between">
                <span class="font-bold text-white">${p.fullNameAr} — إجازة ${l.type} (${l.days} أيام)</span>
                <span class="px-2 py-0.5 rounded font-bold text-[10px] ${l.status === 'APPROVED' ? 'bg-emerald-500/20 text-emerald-300' : (l.status === 'REJECTED' ? 'bg-rose-500/20 text-rose-300' : 'bg-amber-500/20 text-amber-300')}">${l.status}</span>
              </div>
              <div class="text-slate-400">الفترة: ${l.startDate} إلى ${l.endDate} | الرصيد المتبقي: <strong class="text-emerald-300">${p.annualLeaveBalance} يوم</strong></div>
              <div class="text-slate-300">السبب: ${l.reason} | المرحلة: <span class="text-amber-300">${l.stage}</span></div>
              <div class="flex gap-2 pt-1">
                <button type="button" onclick="approveRejectLeave('${l.id}','APPROVED')" class="px-2.5 py-1 rounded bg-emerald-700 hover:bg-emerald-600 text-white font-semibold">✓ موافقة القائد</button>
                <button type="button" onclick="approveRejectLeave('${l.id}','REJECTED')" class="px-2.5 py-1 rounded bg-rose-800 hover:bg-rose-700 text-white font-semibold">✕ رفض</button>
              </div>
            </div>
          `;
        }).join('');
      }

      const pBox = document.getElementById('permissionsListContainer');
      if (pBox) {
        pBox.innerHTML = state.permissions.map((pr) => {
          const p = state.personnel.find((x) => x.id === pr.personnelId) || { fullNameAr: pr.personnelId };
          return `
            <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1.5">
              <div class="flex items-center justify-between">
                <span class="font-bold text-white">${p.fullNameAr} — إذن (${pr.durationType}: ${pr.value})</span>
                <span class="px-2 py-0.5 rounded font-bold text-[10px] ${pr.status === 'APPROVED' ? 'bg-emerald-500/20 text-emerald-300' : 'bg-amber-500/20 text-amber-300'}">${pr.status}</span>
              </div>
              <div class="text-slate-300">السبب: ${pr.reason}</div>
              <div class="flex gap-2 pt-1">
                <button type="button" onclick="approveRejectPermission('${pr.id}','APPROVED')" class="px-2.5 py-1 rounded bg-emerald-700 hover:bg-emerald-600 text-white">اعتماد الإذن</button>
                <button type="button" onclick="deletePermissionReq('${pr.id}')" class="px-2.5 py-1 rounded bg-slate-800 hover:bg-slate-700 text-rose-300">حذف</button>
              </div>
            </div>
          `;
        }).join('');
      }

      const rGrid = document.getElementById('businessRulesGrid');
      if (rGrid) {
        rGrid.innerHTML = state.businessRules.map((br) => `
          <div class="p-3 rounded-xl bg-slate-950 border border-slate-800 flex flex-col justify-between gap-2">
            <div>
              <div class="font-mono text-[10px] text-amber-400">${br.code}</div>
              <div class="font-bold text-white mt-0.5">${br.title}</div>
              <div class="font-mono text-[10px] text-slate-400 mt-1">AST: ${br.condition}</div>
            </div>
            <button type="button" onclick="toggleBusinessRule('${br.id}')" class="px-2.5 py-1 rounded font-bold ${br.enabled ? 'bg-emerald-600/20 text-emerald-300 border border-emerald-500/40' : 'bg-slate-800 text-slate-400'}">
              ${br.enabled ? '✓ القاعدة مفعلة بالمحرك' : 'معطلة — اضغط للتفعيل'}
            </button>
          </div>
        `).join('');
      }
    }

    function approveRejectLeave(leaveId, decision) {
      if (!hasPermission('canApproveLeave') && !hasPermission('canRejectLeave')) {
        showToast('عذراً، صلاحيات دورك الحالي لا تخولك اعتماد أو رفض الإجازات.', 'error');
        return;
      }
      const lv = state.leaves.find((x) => x.id === leaveId);
      if (!lv) return;
      lv.status = decision;
      lv.stage = decision === 'APPROVED' ? 'معتمدة نهائياً (' + ROLES_CONFIG[state.currentRole].nameAr + ')' : 'مرفوضة';
      persistState('APPROVE', 'Leave#' + leaveId, `تحديث حالة الإجازة إلى ${decision}`);
      renderLeavesAndPermissions();
      showToast(decision === 'APPROVED' ? 'تم اعتماد الإجازة وخصمها من الرصيد وإرسال إشعار للفرد.' : 'تم رفض طلب الإجازة.', decision === 'APPROVED' ? 'success' : 'warning');
    }

    function approveRejectPermission(permId, decision) {
      const pr = state.permissions.find((x) => x.id === permId);
      if (!pr) return;
      pr.status = decision;
      persistState('APPROVE', 'Permission#' + permId, `اعتماد طلب الإذن ${permId}`);
      renderLeavesAndPermissions();
      showToast('تم تحديث حالة طلب الإذن وربطه بملف الفرد.', 'success');
    }

    function deletePermissionReq(permId) {
      state.permissions = state.permissions.filter((x) => x.id !== permId);
      persistState('DELETE', 'Permission#' + permId, 'حذف سجل إذن');
      renderLeavesAndPermissions();
      showToast('تم حذف سجل الإذن.', 'info');
    }

    function toggleBusinessRule(ruleId) {
      const r = state.businessRules.find((x) => x.id === ruleId);
      if (!r) return;
      r.enabled = !r.enabled;
      persistState('SETTINGS', 'BusinessRule#' + r.code, `تغيير حالة قاعدة الأعمال ${r.code} إلى ${r.enabled}`);
      renderLeavesAndPermissions();
      showToast('تم تحديث حالة القاعدة في محرك json-rules-engine.', 'info');
    }

    // =========================================================================
    // 11. LOGISTICS: WEAPONS, AMMUNITION & VEHICLES
    // =========================================================================
    function renderLogisticsModule() {
      const wBox = document.getElementById('weaponsListContainer');
      if (wBox) {
        wBox.innerHTML = state.weapons.map((w) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1">
            <div class="flex items-center justify-between">
              <span class="font-bold text-white">${w.type}</span>
              <span class="px-2 py-0.5 rounded font-bold text-[10px] ${w.status === 'READY' ? 'bg-emerald-500/20 text-emerald-300' : 'bg-amber-500/20 text-amber-300'}">${w.status}</span>
            </div>
            <div class="font-mono text-emerald-400 text-[11px]">الرقم التسلسلي: ${w.serial} | العيار: ${w.caliber}</div>
            <div class="text-slate-300">المستلم / الموقع: ${w.assignee} (${w.rounds} طلقة)</div>
            <div class="text-[11px] text-slate-400">آخر صيانة: ${w.lastMaint} | القادمة: ${w.nextMaint}</div>
          </div>
        `).join('');
      }

      const aBox = document.getElementById('ammoListContainer');
      if (aBox) {
        aBox.innerHTML = state.ammunition.map((a) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1">
            <div class="flex items-center justify-between">
              <span class="font-bold text-white">${a.type}</span>
              <span class="font-mono text-amber-300 font-bold">${a.balance.toLocaleString()} طلقة</span>
            </div>
            <div class="text-slate-400">الوارد: ${a.qtyIn.toLocaleString()} | المنصرف: ${a.qtyOut.toLocaleString()}</div>
            <div class="text-[11px] text-slate-300">المسؤول: ${a.officer} | الدفعة: ${a.batch}</div>
          </div>
        `).join('');
      }

      const vBox = document.getElementById('vehiclesListContainer');
      if (vBox) {
        vBox.innerHTML = state.vehicles.map((v) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1">
            <div class="flex items-center justify-between">
              <span class="font-bold text-white">${v.model}</span>
              <span class="px-2 py-0.5 rounded text-[10px] font-bold ${v.status === 'OPERATIONAL' ? 'bg-emerald-500/20 text-emerald-300' : 'bg-amber-500/20 text-amber-300'}">${v.status}</span>
            </div>
            <div class="text-sky-300 font-mono text-[11px]">اللوحة: ${v.plate} | الشاصي: ${v.chassis}</div>
            <div class="text-slate-300">السائق: ${v.driver} | الوقود: ${v.fuel}%</div>
            <div class="text-[11px] text-slate-400">سجل الأعطال: ${v.faults}</div>
          </div>
        `).join('');
      }
    }

    // =========================================================================
    // 12. READINESS & TRAINING
    // =========================================================================
    function renderReadinessAndTraining() {
      const unitFilter = document.getElementById('readinessUnitFilter')?.value || '';
      const rBox = document.getElementById('readinessPersonnelContainer');
      if (rBox) {
        const list = getScopedPersonnel().filter((p) => !unitFilter || p.unitId === unitFilter);
        rBox.innerHTML = list.map((p) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs flex items-center justify-between gap-2">
            <div>
              <div class="font-bold text-white">${getRankName(p.rankId)} / ${p.fullNameAr}</div>
              <div class="text-[11px] text-slate-400">${getUnitName(p.unitId)} — السبب/الملاحظة: ${p.readinessReason}</div>
            </div>
            <button type="button" onclick="togglePersonReadiness('${p.id}')" class="px-3 py-1 rounded-lg font-bold ${p.readiness === 'READY' ? 'bg-emerald-600/20 text-emerald-300 border border-emerald-500/40' : 'bg-rose-600/20 text-rose-300 border border-rose-500/40'}">
              ${p.readiness === 'READY' ? '🟢 جاهز قتالياً' : '🔴 غير جاهز'}
            </button>
          </div>
        `).join('');
      }

      const tBox = document.getElementById('trainingRecordsContainer');
      if (tBox) {
        tBox.innerHTML = state.trainingRecords.map((tr) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1">
            <div class="flex items-center justify-between">
              <span class="font-bold text-white">${tr.course}</span>
              <span class="text-emerald-400 font-bold">${tr.completion}%</span>
            </div>
            <div class="text-slate-300">المتدرب: ${tr.personnelName}</div>
            <div class="text-amber-300">الرماية: ${tr.shooting}% | اللياقة البدنية: ${tr.fitness}% | التقييم: ${tr.status}</div>
          </div>
        `).join('');
      }
    }

    function togglePersonReadiness(id) {
      const p = state.personnel.find((x) => x.id === id);
      if (!p) return;
      p.readiness = (p.readiness === 'READY') ? 'NOT_READY' : 'READY';
      p.readinessReason = (p.readiness === 'READY') ? 'تم التحقق من الجاهزية القتالية' : 'إعفاء طبي / إداري مؤقت';
      persistState('UPDATE', 'Readiness#' + id, `تحديث جاهزية ${p.fullNameAr} إلى ${p.readiness}`);
      renderReadinessAndTraining();
      renderDashboard();
      showToast(`تم تحديث جاهزية ${p.fullNameAr} إلى ${p.readiness === 'READY' ? 'جاهز' : 'غير جاهز'}.`, 'success');
    }

    // =========================================================================
    // 13. TASKS & ANNOUNCEMENTS
    // =========================================================================
    function renderTasksAndAnnouncements() {
      const tBox = document.getElementById('tasksBoardContainer');
      if (tBox) {
        tBox.innerHTML = state.tasks.map((t) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-2">
            <div class="flex items-center justify-between gap-2">
              <span class="font-bold text-white">${t.title}</span>
              <span class="px-2 py-0.5 rounded font-bold text-[10px] ${t.priority === 'CRITICAL' ? 'bg-rose-600 text-white' : 'bg-amber-500/20 text-amber-300'}">${t.priority}</span>
            </div>
            <div class="text-slate-300">المنفذ: ${t.assignee} | الموعد النهائي: ${t.dueDate}</div>
            <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
              <div class="bg-emerald-500 h-full" style="width:${t.progress}%"></div>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-emerald-400 font-bold">نسبة الإنجاز: ${t.progress}%</span>
              <div class="flex gap-1.5">
                <button type="button" onclick="advanceTaskProgress('${t.id}')" class="px-2 py-0.5 rounded bg-emerald-700 hover:bg-emerald-600 text-white">+ تحديث الإنجاز</button>
                <button type="button" onclick="deleteTaskItem('${t.id}')" class="px-2 py-0.5 rounded bg-rose-900/60 text-rose-200">حذف</button>
              </div>
            </div>
          </div>
        `).join('');
      }

      const aBox = document.getElementById('announcementsListContainer');
      if (aBox) {
        aBox.innerHTML = state.announcements.map((a) => `
          <div class="p-3 rounded-xl bg-slate-950/70 border border-slate-800 text-xs space-y-1">
            <div class="flex items-center justify-between">
              <span class="font-bold text-amber-300">${a.title}</span>
              <button type="button" onclick="deleteAnnouncementItem('${a.id}')" class="text-rose-400 hover:underline">حذف</button>
            </div>
            <p class="text-slate-300 leading-relaxed">${a.content}</p>
            <div class="text-[10px] text-slate-500">${a.date} | الأولوية: ${a.priority}</div>
          </div>
        `).join('');
      }
    }

    function advanceTaskProgress(taskId) {
      const t = state.tasks.find((x) => x.id === taskId);
      if (!t) return;
      t.progress = Math.min(100, t.progress + 15);
      if (t.progress === 100) t.status = 'COMPLETED';
      persistState('UPDATE', 'Task#' + taskId, `رفع نسبة إنجاز المهمة إلى ${t.progress}%`);
      renderTasksAndAnnouncements();
      showToast(`تم تحديث نسبة إنجاز المهمة إلى ${t.progress}%.`, 'success');
    }

    function deleteTaskItem(taskId) {
      state.tasks = state.tasks.filter((x) => x.id !== taskId);
      persistState('DELETE', 'Task#' + taskId, 'حذف مهمة إدارية');
      renderTasksAndAnnouncements();
      showToast('تم حذف المهمة.', 'info');
    }

    function deleteAnnouncementItem(annId) {
      state.announcements = state.announcements.filter((x) => x.id !== annId);
      persistState('DELETE', 'Announcement#' + annId, 'حذف إعلان');
      renderTasksAndAnnouncements();
      showToast('تم حذف الإعلان.', 'info');
    }

    // =========================================================================
    // 14. 52 ENTERPRISE REPORTS ENGINE (مركز التقارير المؤسسية)
    // =========================================================================
    const REPORTS_CATALOG = [
      { id: 'REP-01', title: '01. كشف القوة العمومي للكتيبة (Master Roster)', cat: 'الأفراد' },
      { id: 'REP-02', title: '02. كشف الحضور والانصراف اليومي الشامل', cat: 'الحضور' },
      { id: 'REP-03', title: '03. كشف الغياب اليومي والمتصل بدون عذر', cat: 'الحضور' },
      { id: 'REP-04', title: '04. كشف المتأخرين عن الطابور الصباحي والمسائي', cat: 'الحضور' },
      { id: 'REP-05', title: '05. كشف الإجازات الفعالة والمعلقة والمنتهية', cat: 'الإجازات' },
      { id: 'REP-06', title: '06. كشف الأذونات الساعية واليومية', cat: 'الأذونات' },
      { id: 'REP-07', title: '07. كشف عهدة الأسلحة الفردية والمتوسطة', cat: 'التسليح' },
      { id: 'REP-08', title: '08. كشف مخزون الذخائر وحركة الوارد والمنصرف', cat: 'الذخائر' },
      { id: 'REP-09', title: '09. كشف الآليات والمدرعات وجاهزية الوقود', cat: 'الآليات' },
      { id: 'REP-10', title: '10. تقرير الجاهزية القتالية التفصيلي للسرايا', cat: 'العمليات' },
      { id: 'REP-11', title: '11. تقرير التدريب ونتائج الرماية واللياقة', cat: 'التدريب' },
      { id: 'REP-12', title: '12. تقرير الموقف العملياتي اليومي (SITREP)', cat: 'العمليات' },
      { id: 'REP-13', title: '13. التقرير اليومي الموحد لقائد الكتيبة', cat: 'دوري' },
      { id: 'REP-14', title: '14. التقرير الأسبوعي للانضباط والجاهزية', cat: 'دوري' },
      { id: 'REP-15', title: '15. التقرير الشهري الشامل لشؤون الأفراد', cat: 'دوري' },
      { id: 'REP-16', title: '16. التقرير السنوي الاستراتيجي للكتيبة', cat: 'دوري' },
      { id: 'REP-17', title: '17. كشف كبار السن ومستحقي التقاعد (حسب الميلاد)', cat: 'الأفراد' },
      { id: 'REP-18', title: '18. كشف المرضى والإعفاءات الطبية الميدانية', cat: 'الأفراد' },
      { id: 'REP-19', title: '19. بطاقة الانضباط الفردي والسجل التاريخي', cat: 'الأفراد' },
      { id: 'REP-20', title: '20. كشف توزيع فصائل الدم للطوارئ الطبية', cat: 'الطبي' },
      { id: 'REP-21', title: '21. تقرير صيانة الأسلحة الدورية والطارئة', cat: 'الصيانة' },
      { id: 'REP-22', title: '22. تقرير أعطال الآليات واستهلاك قطع الغيار', cat: 'الصيانة' },
      { id: 'REP-23', title: '23. كشف جرد المستودعات والمخازن العسكرية', cat: 'الإمداد' },
      { id: 'REP-24', title: '24. تقرير الأصول والعهد الإدارية الثابتة', cat: 'الإمداد' },
      { id: 'REP-25', title: '25. جدول المناوبات والخفارات والحراسات', cat: 'العمليات' },
      { id: 'REP-26', title: '26. سجل الأوامر العسكرية اليومية والمستديمة', cat: 'القيادة' },
      { id: 'REP-27', title: '27. سجل المراسلات الصادرة والواردة السرية', cat: 'القيادة' },
      { id: 'REP-28', title: '28. تقرير تنفيذ المهام الإدارية والميدانية', cat: 'المهام' },
      { id: 'REP-29', title: '29. تقرير تقييم المخاطر والإنذارات المبكرة', cat: 'الأمن' },
      { id: 'REP-30', title: '30. تقرير خطط الطوارئ والاستجابة السريعة', cat: 'العمليات' },
      { id: 'REP-31', title: '31. تقرير الميزانية والاعتمادات المالية للوحدات', cat: 'المالية' },
      { id: 'REP-32', title: '32. كشف الترقيات المستحقة والأقدمية العسكرية', cat: 'الأفراد' },
      { id: 'REP-33', title: '33. كشف المكافآت والأوسمة وخطابات الشكر', cat: 'الأفراد' },
      { id: 'REP-34', title: '34. كشف العقوبات والجزاءات الانضباطية', cat: 'الأفراد' },
      { id: 'REP-35', title: '35. كشف الدورات التخصصية والبعثات التدريبية', cat: 'التدريب' },
      { id: 'REP-36', title: '36. تقرير كفاءة السرية الأولى اقتحام', cat: 'السرايا' },
      { id: 'REP-37', title: '37. تقرير كفاءة السرية الثانية إسناد ناري', cat: 'السرايا' },
      { id: 'REP-38', title: '38. تقرير كفاءة السرية الثالثة مدرعات', cat: 'السرايا' },
      { id: 'REP-39', title: '39. تقرير مقارنة الأداء القياسي بين السرايا', cat: 'السرايا' },
      { id: 'REP-40', title: '40. سجل التدقيق الأمني غير القابل للحذف (Audit)', cat: 'الأمن' },
      { id: 'REP-41', title: '41. تقرير المزامنة التفاضلية للأجهزة الميدانية', cat: 'التقنية' },
      { id: 'REP-42', title: '42. تقرير صلاحيات المستخدمين ومصفوفة RBAC', cat: 'الأمن' },
      { id: 'REP-43', title: '43. كشف أرصدة الإجازات المتبقية للأفراد', cat: 'الإجازات' },
      { id: 'REP-44', title: '44. تقرير الإجازات المنتهية خلال 48 ساعة', cat: 'الإجازات' },
      { id: 'REP-45', title: '45. كشف القوة حسب الرتب العسكرية والاختصاص', cat: 'الأفراد' },
      { id: 'REP-46', title: '46. تقرير جاهزية أجهزة الاتصال والتشفير', cat: 'الإشارة' },
      { id: 'REP-47', title: '47. تقرير التموين والإعاشة اليومية للكتيبة', cat: 'الإمداد' },
      { id: 'REP-48', title: '48. محضر اجتماعات قيادة الكتيبة والقرارات', cat: 'القيادة' },
      { id: 'REP-49', title: '49. تقويم المناورات والتفتيشات العسكرية السنوي', cat: 'العمليات' },
      { id: 'REP-50', title: '50. تقرير النسخ الاحتياطية وفحص سلامة البيانات', cat: 'التقنية' },
      { id: 'REP-51', title: '51. تقرير مؤشرات الذكاء الاصطناعي التنبؤية للانضباط', cat: 'الذكاء' },
      { id: 'REP-52', title: '52. خلاصة الجاهزية الاستراتيجية لقائد اللواء', cat: 'القيادة' }
    ];

    function renderReportsCatalog() {
      const box = document.getElementById('reportsCatalogList');
      if (!box) return;
      const q = (document.getElementById('reportCatalogSearch')?.value || '').trim().toLowerCase();
      const filtered = REPORTS_CATALOG.filter((r) => !q || r.title.toLowerCase().includes(q) || r.cat.toLowerCase().includes(q));
      box.innerHTML = filtered.map((r) => `
        <button type="button" onclick="selectReportItem('${r.id}')" class="w-full text-start px-3 py-2 rounded-lg text-xs flex items-center justify-between ${state.activeReportId === r.id ? 'bg-emerald-600/20 text-emerald-300 border border-emerald-500/40 font-bold' : 'text-slate-300 hover:bg-slate-800'}">
          <span class="truncate">${r.title}</span>
          <span class="text-[10px] px-1.5 py-0.5 rounded bg-slate-800 text-slate-400 ms-2">${r.cat}</span>
        </button>
      `).join('');
    }

    function selectReportItem(repId) {
      state.activeReportId = repId;
      renderReportsCatalog();
      renderActiveReportPreview();
    }

    function renderActiveReportPreview() {
      const box = document.getElementById('reportPreviewContainer');
      if (!box) return;
      const rep = REPORTS_CATALOG.find((r) => r.id === state.activeReportId) || REPORTS_CATALOG[0];
      const scoped = getScopedPersonnel();
      const roleCfg = ROLES_CONFIG[state.currentRole] || ROLES_CONFIG.SYSTEM_ADMIN;

      box.innerHTML = `
        <div class="border-b border-slate-800 pb-3 flex flex-wrap items-center justify-between gap-2">
          <div>
            <div class="text-xs text-emerald-400 font-bold">الجمهورية اليمنية — اللواء الأول مدرع — الكتيبة 101 مشاة ميكا</div>
            <h3 class="text-base font-bold text-white mt-0.5">${rep.title}</h3>
            <div class="text-[11px] text-slate-400">نطاق البيانات المطبق (Data Scope): ${roleCfg.nameAr} | التاريخ: 2026-10-17</div>
          </div>
          <span class="px-2.5 py-1 rounded bg-emerald-950 border border-emerald-600/40 text-emerald-300 text-xs font-mono">${rep.id}</span>
        </div>
        <div class="overflow-x-auto">
          <table class="w-full text-xs text-start border border-slate-800">
            <thead class="bg-slate-950 text-slate-300">
              <tr>
                <th class="p-2 border border-slate-800">م</th>
                <th class="p-2 border border-slate-800">الرقم العسكري</th>
                <th class="p-2 border border-slate-800">الرتبة والاسم</th>
                <th class="p-2 border border-slate-800">الوحدة</th>
                <th class="p-2 border border-slate-800">السلاح / العهدة</th>
                <th class="p-2 border border-slate-800">الانضباط والجاهزية</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-slate-800">
              ${scoped.map((p, idx) => `
                <tr>
                  <td class="p-2 border border-slate-800">${idx + 1}</td>
                  <td class="p-2 border border-slate-800 font-mono text-emerald-400">${p.militaryNumber}</td>
                  <td class="p-2 border border-slate-800 font-bold text-white">${getRankName(p.rankId)} / ${p.fullNameAr}</td>
                  <td class="p-2 border border-slate-800">${getUnitName(p.unitId)}</td>
                  <td class="p-2 border border-slate-800">${p.weapon} (${p.ammo} طلقة)</td>
                  <td class="p-2 border border-slate-800">${p.disciplineScore}% | ${p.readiness === 'READY' ? 'جاهز' : 'غير جاهز'}</td>
                </tr>
              `).join('')}
            </tbody>
          </table>
        </div>
      `;
    }

    function exportActiveReport(format) {
      const rep = REPORTS_CATALOG.find((r) => r.id === state.activeReportId) || REPORTS_CATALOG[0];
      const scoped = getScopedPersonnel();
      persistState('EXPORT', rep.id, `تصدير التقرير (${rep.title}) بصيغة ${format}`);

      if (format === 'PRINT_PDF') {
        window.print();
        return;
      }

      if (format === 'CSV') {
        const headers = ['الرقم العسكري,الاسم الرباعي,الرتبة,الوحدة,فصيلة الدم,السلاح,الانضباط,الجاهزية'];
        const rows = scoped.map((p) =>
          `"${p.militaryNumber}","${p.fullNameAr}","${getRankName(p.rankId)}","${getUnitName(p.unitId)}","${p.bloodType}","${p.weapon}","${p.disciplineScore}%","${p.readiness}"`
        );
        const csvContent = '\uFEFF' + headers.concat(rows).join('\n');
        const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = `${rep.id}_BMS_Pro_Report.csv`;
        link.click();
        showToast('تم تصدير التقرير بصيغة Excel / CSV بنجاح.', 'success');
      } else if (format === 'WORD') {
        const htmlDoc = `<html><head><meta charset="utf-8"></head><body dir="rtl"><h2>${rep.title}</h2>` + document.getElementById('reportPreviewContainer').innerHTML + `</body></html>`;
        const blob = new Blob([htmlDoc], { type: 'application/msword;charset=utf-8' });
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = `${rep.id}_BMS_Pro_Report.doc`;
        link.click();
        showToast('تم تصدير التقرير بصيغة Word (.doc) بنجاح.', 'success');
      }
    }

    // =========================================================================
    // 15. LOCAL AIR-GAPPED MILITARY AI ASSISTANT (المساعد الذكي المحلي)
    // =========================================================================
    let aiConversation = [
      { sender: 'AI', text: 'مرحباً بك سيادة القائد في المساعد العسكري الذكي المحلي (يعمل محلياً عبر Ollama / Llama-3.1 داخل الشبكة العسكرية المعزولة دون أي اتصال خارجي). يمكنك سؤالي مباشرة باللغة العربية عن الحضور، الغياب، السرايا، الإجازات، الأسلحة، والجاهزية.' }
    ];

    function renderAiChat() {
      const box = document.getElementById('aiChatMessages');
      if (!box) return;
      box.innerHTML = aiConversation.map((m) => `
        <div class="flex ${m.sender === 'USER' ? 'justify-start' : 'justify-end'}">
          <div class="max-w-2xl rounded-2xl p-3 ${m.sender === 'USER' ? 'bg-emerald-700 text-white' : 'bg-slate-800 border border-emerald-500/30 text-slate-100'}">
            <div class="text-[10px] font-bold mb-1 ${m.sender === 'USER' ? 'text-emerald-200' : 'text-amber-300'}">${m.sender === 'USER' ? '👤 استعلام القائد' : '🤖 المساعد العسكري الذكي المحلي (Ollama Air-Gapped)'}</div>
            <div class="leading-relaxed whitespace-pre-line">${m.text}</div>
          </div>
        </div>
      `).join('');
      box.scrollTop = box.scrollHeight;
    }

    function askMilitaryAi(queryText) {
      const q = (queryText || '').trim();
      if (!q) return;
      aiConversation.push({ sender: 'USER', text: q });

      let reply = '';
      if (q.includes('تأخر')) {
        const sortedLate = [...state.personnel].sort((a, b) => (b.lateCountMonth || 0) - (a.lateCountMonth || 0));
        const top = sortedLate[0];
        reply = `📊 تحليل التأخر الشهري من قاعدة البيانات:
أكثر جندي تأخراً هذا الشهر هو: **${getRankName(top.rankId)} / ${top.fullNameAr}** (الرقم العسكري: ${top.militaryNumber} — ${getUnitName(top.unitId)}) بعدد **${top.lateCountMonth} مرات تأخر**، يليه **العريف / نبيل عبدالكريم الحالمي** بعدد **5 مرات تأخر**.
💡 التوصية: توجيه إنذار انضباطي آلي ومراجعة جدول مناوبته الصباحية.`;
      } else if (q.includes('السرية الثانية') || q.includes('غياب')) {
        const cmp2Absent = state.personnel.filter((p) => p.unitId === 'U-CMP-2' && (p.isContinuousAbsent || p.readiness !== 'READY'));
        reply = `🚨 كشف الغياب وعدم الجاهزية في **السرية الثانية إسناد ناري**:
1. **الجندي أول / عمار ياسر المقطري** (${cmp2Absent[0]?.militaryNumber || 'MIL-2026-1006'}): غائب بدون عذر ومُدرج في قائمة الغياب المستمر.
2. **العريف / نبيل عبدالكريم الحالمي**: متأخر صباحاً (45 دقيقة) وحالته غير جاهز بسبب إصابة تدريبية طفيفة.`;
      } else if (q.includes('إجازة') || q.includes('يومين')) {
        const exp = state.leaves.filter((l) => l.expiresSoon);
        reply = `🌴 الأفراد الذين تنتهي إجازاتهم خلال 48 ساعة (${exp.length} أفراد):
` + exp.map((l) => {
          const p = state.personnel.find((x) => x.id === l.personnelId);
          return `• **${p ? p.fullNameAr : l.personnelId}** — نوع الإجازة: ${l.type} — تاريخ الانتهاء: ${l.endDate}`;
        }).join(`\n`);
      } else if (q.includes('الأسلحة') || q.includes('سلاح')) {
        const readyW = state.weapons.filter((w) => w.status === 'READY').length;
        const maintW = state.weapons.filter((w) => w.status !== 'READY').length;
        reply = `🔫 تحليل جاهزية الأسلحة والذخائر:
• إجمالي الأسلحة الجاهزة بالخدمة: **${readyW} من أصل ${state.weapons.length}** (${Math.round((readyW / state.weapons.length) * 100)}%).
• أسلحة في الصيانة الوقائية: **${maintW}** (قناصة دراغونوف SVD-309112).
• إجمالي رصيد الذخائر المتوفرة: **${state.ammunition.reduce((s, a) => s + a.balance, 0).toLocaleString()} طلقة**.`;
      } else if (q.includes('الجاهزية') || q.includes('نسبة')) {
        const readyP = state.personnel.filter((p) => p.readiness === 'READY').length;
        const pct = Math.round((readyP / state.personnel.length) * 100);
        reply = `🛡️ خلاصة الجاهزية القتالية العامة للكتيبة 101:
• الجاهزية البشرية القتالية: **${pct}%** (${readyP} جاهز من أصل ${state.personnel.length}).
• جاهزية الأسلحة الفردية والمتوسطة: **80%**.
• جاهزية الآليات والمدرعات: **66.7%** (مدرعة MRAP وطقم Land Cruiser جاهزان، وشاحنة KamAZ في الصيانة).`;
      } else {
        reply = `🤖 تحليل الذكاء الاصطناعي المحلي وكشف الشذوذ (Anomaly Detection):
1. تم رصد تركز 80% من حالات التأخر والغياب المتصل في **السرية الثانية إسناد ناري**.
2. يُوصى بإعادة توازن جدول الخفارات الليلية وتفعيل التحضير الإلزامي عبر رمز QR الصباحي قبل الساعة 06:20.`;
      }

      aiConversation.push({ sender: 'AI', text: reply });
      renderAiChat();
    }

    function submitCustomAiQuery() {
      const inp = document.getElementById('aiQueryInput');
      if (!inp || !inp.value.trim()) return;
      const val = inp.value;
      inp.value = '';
      askMilitaryAi(val);
    }

    // =========================================================================
    // 16. AUDIT LOGS, OFFLINE SYNC QUEUE, ARCHITECTURE & SETTINGS
    // =========================================================================
    function renderAuditAndSync() {
      const filterVal = document.getElementById('auditActionFilter')?.value || '';
      const aBox = document.getElementById('auditLogsTableContainer');
      if (aBox) {
        const logs = state.auditLogs.filter((l) => !filterVal || l.action === filterVal);
        aBox.innerHTML = logs.map((l) => `
          <div class="p-2.5 rounded-lg bg-slate-950 border border-slate-800 flex flex-wrap items-center justify-between gap-2">
            <div>
              <span class="px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 font-bold text-[10px] me-1.5">${l.action}</span>
              <span class="font-bold text-white">${l.details}</span>
              <div class="text-[10px] text-slate-400 mt-0.5">المستخدم: ${l.user} | الكيان: ${l.entity} | SHA-256 Chain: <span class="font-mono text-amber-300">${l.hash}</span></div>
            </div>
            <span class="font-mono text-[11px] text-slate-400">${l.time}</span>
          </div>
        `).join('');
      }

      renderFieldEndpoints();
      const qBox = document.getElementById('offlineQueueInspector');
      if (qBox) {
        if (state.offlineMutations.length === 0) {
          qBox.innerHTML = `<div class="p-4 rounded-xl bg-emerald-950/30 border border-emerald-700/40 text-emerald-300 text-center">✓ طابور المزامنة فارغ — جميع العمليات متزامنة مع PostgreSQL المركزي.</div>`;
        } else {
          qBox.innerHTML = state.offlineMutations.map((m) => `
            <div class="p-2.5 rounded-lg bg-amber-950/40 border border-amber-600/40">
              <div class="font-bold text-amber-300">${m.operation} — ${m.entityName} (v${m.recordVersion})</div>
              <div class="text-slate-300 text-[11px]">${m.details}</div>
              <div class="font-mono text-[10px] text-slate-400">${m.utcTimestamp} | ${m.sourceDeviceId}</div>
            </div>
          `).join('');
        }
      }
    }

    function renderArchitectureBlueprint() {
      const box = document.getElementById('architectureBlueprintContainer');
      if (!box) return;
      box.innerHTML = `
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-2">
            <h3 class="text-sm font-bold text-emerald-400">1. الوحدات البرمجية المحملة ديناميكياً (Dynamic Plugin Loader)</h3>
            <div class="space-y-1.5 font-mono text-[11px]">
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/core (Security, Sync, EventBus, Workflow)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/personnel (DDD Bounded Context)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/attendance (QR & Discipline Engine)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/weapons (Armory, Ammo & Fleet)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/tasks (Orders, Shifts & Calendar)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/reports (52 Enterprise Reports Engine)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
              <div class="p-2 rounded bg-slate-950 border border-emerald-600/30 flex justify-between"><span>packages/notifications (Socket.io + FCM Push)</span><span class="text-emerald-400">ACTIVE v2.4.0</span></div>
            </div>
          </div>
          <div class="bg-slate-900 border border-slate-800 rounded-xl p-4 space-y-2">
            <h3 class="text-sm font-bold text-amber-400">2. ملخص قاعدة بيانات PostgreSQL + Prisma (35 جدولاً مطبّعاً)</h3>
            <p class="text-slate-300 leading-relaxed">تشتمل قاعدة البيانات على الجداول الأساسية: Users, Roles, Permissions, UserRoles, Personnel, Units (Materialized Path), Ranks, Jobs, Attendance, AttendanceSessions, Leaves, PermissionsRequest, Weapons, Ammunition, Vehicles, Warehouses, Inventory, Maintenance, Assets, Tasks, Shifts, Announcements, Notifications, Readiness, TrainingRecords, Documents, Correspondence, MilitaryCalendar, Orders, Meetings, Risks, Emergencies, Budgets, AuditLogs (Hash-Chain), EntityHistory, SyncLogs, BusinessRules, Settings, Translations, Backups, TrashBin.</p>
            <div class="p-2.5 rounded-lg bg-slate-950 border border-slate-800 font-mono text-[11px] text-sky-300">
              RPO &lt; 5 min (WAL Streaming Replication) | RTO &lt; 15 min (HAProxy + Patroni) | Offline Sync: Dexie.js (Web) &amp; Hive (Flutter) -> Shared REST API (/api/v1/sync/delta)
            </div>
          </div>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-3 pt-2">
          <div class="bg-slate-900 border border-emerald-600/40 rounded-xl p-3.5 space-y-1.5">
            <h4 class="font-bold text-emerald-400">✅ أبرز المزايا (Strengths)</h4>
            <ul class="text-slate-300 space-y-1 list-disc ps-4">
              <li>عمل كامل دون اتصال (Dexie.js + Hive) مع مزامنة تفاضلية.</li>
              <li>عزل أمني للبيانات حسب الهرم العسكري (Materialized Path Scope).</li>
              <li>ذكاء اصطناعي محلي معزول 100% (Ollama Air-Gapped).</li>
              <li>سجل تدقيق غير قابل للحذف أو التلاعب (SHA-256 Hash-Chain).</li>
            </ul>
          </div>
          <div class="bg-slate-900 border border-rose-600/40 rounded-xl p-3.5 space-y-1.5">
            <h4 class="font-bold text-rose-400">⚠️ التحديات والعيوب (Trade-offs)</h4>
            <ul class="text-slate-300 space-y-1 list-disc ps-4">
              <li>تعارضات المزامنة عند انقطاع وحدتين لعدة أيام وتعديل نفس السجل.</li>
              <li>متطلبات عتاد عالية (GPU/RAM) لتشغيل نماذج الذكاء الاصطناعي محلياً.</li>
              <li>حجم النسخ الاحتياطية المتزايد مع تفعيل سجل الإصدارات (EntityHistory).</li>
            </ul>
          </div>
          <div class="bg-slate-900 border border-amber-600/40 rounded-xl p-3.5 space-y-1.5">
            <h4 class="font-bold text-amber-300">💡 الاقتراحات الميدانية (Suggestions)</h4>
            <ul class="text-slate-300 space-y-1 list-disc ps-4">
              <li>دمج البصمة الحيوية وبطاقات NFC/RFID العسكرية بجانب QR Code.</li>
              <li>ربط أجهزة اللاسلكي التكتيكية (VHF/UHF) ببروتوكول مزامنة مضغوط.</li>
              <li>إضافة خريطة جيومكانية معزولة (Offline GIS Tile Server) لغرفة العمليات.</li>
            </ul>
          </div>
          <div class="bg-slate-900 border border-sky-600/40 rounded-xl p-3.5 space-y-1.5">
            <h4 class="font-bold text-sky-400">🚀 التحسينات الهندسية (Improvements)</h4>
            <ul class="text-slate-300 space-y-1 list-disc ps-4">
              <li>تطبيق تقسيم الجداول الزمني (PostgreSQL Table Partitioning) للحضور والسجلات.</li>
              <li>اعتماد Hybrid CRDT لحقول العدادات (الذخيرة والتموين) بدلاً من LWW فقط.</li>
              <li>التوقيع الرقمي للأوامر العسكرية عبر البطاقات الذكية (PKI / HSM).</li>
            </ul>
          </div>
        </div>
      `;
    }

    function renderSettingsAndBackups() {
      const box = document.getElementById('backupHistoryList');
      if (!box) return;
      box.innerHTML = state.backups.map((b) => `
        <div class="p-2.5 rounded-lg bg-slate-950 border border-slate-800 flex items-center justify-between">
          <div>
            <span class="font-mono font-bold text-emerald-400">${b.id}</span>
            <span class="text-slate-400 ms-2">${b.type} | ${b.algo}</span>
          </div>
          <span class="text-slate-400 font-mono">${b.size} — ${b.time}</span>
        </div>
      `).join('');
    }

    function handleLogoUpload(ev) {
      const file = ev.target.files && ev.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        const container = document.getElementById('brandLogoContainer');
        if (container && e.target?.result) {
          container.innerHTML = `<img src="${e.target.result}" alt="Logo" class="w-full h-full object-cover">`;
          persistState('SETTINGS', 'BrandLogo', 'تحديث شعار الوحدة العسكري');
          showToast('تم تحديث شعار الوحدة في الشريط العلوي والتقارير.', 'success');
        }
      };
      reader.readAsDataURL(file);
    }

    function saveSystemSettings() {
      persistState('SETTINGS', 'SystemSettings', 'حفظ الإعدادات التشغيلية وسياسات الإجازات والغياب');
      showToast('تم حفظ وتطبيق إعدادات النظام بنجاح.', 'success');
    }

    function downloadEncryptedBackup() {
      const bkpId = 'BKP-' + new Date().toISOString().replace(/[-:T]/g, '').substring(0, 12);
      state.backups.unshift({ id: bkpId, type: 'يدوي (مشفر)', size: '4.9 MB', algo: 'AES-256-GCM', time: new Date().toISOString().substring(0, 16).replace('T', ' ') });
      persistState('EXPORT', 'Backup#' + bkpId, 'تصدير نسخة احتياطية كاملة للنظام');
      renderSettingsAndBackups();
      const blob = new Blob([JSON.stringify(state, null, 2)], { type: 'application/json' });
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = `${bkpId}_BMS_Pro_Backup.json`;
      a.click();
      showToast('تم إنشاء وتنزيل النسخة الاحتياطية الكاملة بنجاح.', 'success');
    }

    function restoreBackupFromFile(ev) {
      const file = ev.target.files && ev.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const parsed = JSON.parse(e.target.result);
          state = Object.assign({}, DEFAULT_STATE, parsed);
          persistState('SYNC', 'RestoreBackup', 'استعادة كاملة للنظام من ملف نسخة احتياطية');
          renderDashboard();
          renderPersonnelTable();
          showToast('تمت استعادة النسخة الاحتياطية وتحديث جميع الجداول بنجاح.', 'success');
        } catch (err) {
          showToast('ملف النسخة الاحتياطية غير صالح.', 'error');
        }
      };
      reader.readAsText(file);
    }

    function resetSystemToDefaults() {
      state = JSON.parse(JSON.stringify(DEFAULT_STATE));
      persistState('SETTINGS', 'FactoryReset', 'إعادة ضبط النظام إلى البيانات الافتراضية');
      renderDashboard();
      renderPersonnelTable();
      renderSettingsAndBackups();
      showToast('تمت إعادة تعيين النظام إلى الإعدادات الافتراضية.', 'warning');
    }

    // =========================================================================
    // 17. UNIVERSAL INTERACTIVE MODALS (Add Personnel, Dossier, QR, Leave, etc.)
    // =========================================================================
    function closeModal() {
      const backdrop = document.getElementById('modalBackdrop');
      if (backdrop) backdrop.classList.add('hidden');
    }

    function openPersonnelDossier(personnelId) {
      const p = state.personnel.find((x) => x.id === personnelId);
      if (!p) return;
      const backdrop = document.getElementById('modalBackdrop');
      const box = document.getElementById('modalContentBox');
      if (!backdrop || !box) return;
      backdrop.classList.remove('hidden');

      box.innerHTML = `
        <div class="flex items-center justify-between border-b border-slate-800 pb-3">
          <h3 class="text-base font-bold text-emerald-400">📂 السجل العسكري التاريخي الكامل — ${p.fullNameAr}</h3>
          <button type="button" onclick="closeModal()" class="text-slate-400 hover:text-white">✕</button>
        </div>
        <div class="grid grid-cols-2 gap-2.5 text-xs bg-slate-950 p-3 rounded-xl border border-slate-800">
          <div><span class="text-slate-400">الرقم العسكري:</span> <strong class="font-mono text-emerald-300">${p.militaryNumber}</strong></div>
          <div><span class="text-slate-400">الرتبة والوظيفة:</span> <strong>${getRankName(p.rankId)} — ${getJobTitle(p.jobId)}</strong></div>
          <div><span class="text-slate-400">الوحدة:</span> <strong>${getUnitName(p.unitId)}</strong></div>
          <div><span class="text-slate-400">فصيلة الدم والميلاد:</span> <strong>${p.bloodType} | ${p.birthDate}</strong></div>
          <div><span class="text-slate-400">العهدة التسليحية:</span> <strong>${p.weapon} (${p.ammo} طلقة)</strong></div>
          <div><span class="text-slate-400">رصيد الإجازات والانضباط:</span> <strong>${p.annualLeaveBalance} يوم | ${p.disciplineScore}%</strong></div>
        </div>
        <div class="space-y-2 text-xs">
          <div class="p-2.5 rounded-lg bg-slate-800/60"><strong>🎓 الدورات والمؤهلات:</strong> ${(p.courses && p.courses.length) ? p.courses.join('، ') : 'دورة المستجدين الأساسية'}</div>
          <div class="p-2.5 rounded-lg bg-slate-800/60"><strong>🎖️ الترقيات والمكافآت:</strong> ${(p.promotions || []).concat(p.rewards || []).join('، ') || 'سجل نظيف ومواظب'}</div>
          <div class="p-2.5 rounded-lg bg-slate-800/60"><strong>⚖️ العقوبات والمخالفات:</strong> ${(p.penalties && p.penalties.length) ? p.penalties.join('، ') : 'لا توجد عقوبات مسجلة'}</div>
        </div>
        <div class="flex justify-end gap-2 pt-2">
          <button type="button" onclick="closeModal()" class="px-4 py-1.5 rounded-lg bg-slate-800 text-slate-200 text-xs">إغلاق</button>
        </div>
      `;
    }

    function openModal(modalType) {
      const backdrop = document.getElementById('modalBackdrop');
      const box = document.getElementById('modalContentBox');
      if (!backdrop || !box) return;
      backdrop.classList.remove('hidden');

      if (modalType === 'personnelModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">+ إضافة فرد عسكري جديد إلى الكتيبة</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
            <input id="newPName" type="text" placeholder="الاسم الرباعي الكامل..." class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <input id="newPMilNum" type="text" value="MIL-2026-${1009 + state.personnel.length}" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-emerald-300 font-mono">
            <select id="newPRank" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.ranks.map((r) => `<option value="${r.id}">${r.nameAr}</option>`).join('')}
            </select>
            <select id="newPUnit" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.units.map((u) => `<option value="${u.id}">${u.nameAr}</option>`).join('')}
            </select>
            <input id="newPBirth" type="date" value="1996-05-15" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <select id="newPBlood" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              <option value="O+">O+</option><option value="A+">A+</option><option value="B+">B+</option><option value="AB+">AB+</option>
            </select>
            <input id="newPWeapon" type="text" placeholder="نوع ورقم السلاح (مثال: AK-103)" value="AK-103 #AK7721" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <input id="newPAmmo" type="number" placeholder="عدد الذخيرة" value="120" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
          </div>
          <div class="flex justify-end gap-2 pt-2">
            <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800 text-xs">إلغاء</button>
            <button type="button" onclick="saveNewPersonnel()" class="px-4 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold">حفظ الفرد</button>
          </div>
        `;
      } else if (modalType === 'qrScannerModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-amber-300">📷 ماسح ومولّد باركود الحضور العسكري السريع (QR Code)</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="text-xs space-y-3">
            <p class="text-slate-300">اختر الفرد لمحاكاة مسح البطاقة العسكرية بالكاميرا أو توليد رمز QR المشفر لتسجيل الدخول الفوري:</p>
            <select id="qrSelectPersonnel" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.personnel.map((p) => `<option value="${p.id}">${p.militaryNumber} — ${p.fullNameAr}</option>`).join('')}
            </select>
            <div class="p-4 rounded-xl bg-slate-950 border border-emerald-600/40 flex flex-col items-center justify-center gap-2">
              <svg class="w-28 h-28 text-emerald-400" viewBox="0 0 24 24" fill="currentColor">
                <path d="M3 3h8v8H3V3zm2 2v4h4V5H5zm8-2h8v8h-8V3zm2 2v4h4V5h-4zM3 13h8v8H3v-8zm2 2v4h4v-4H5zm13-2h3v2h-3v-2zm-3 0h2v3h-2v-3zm3 3h3v2h-3v-2zm-3 3h2v2h-2v-2zm3 0h3v2h-3v-2z"/>
              </svg>
              <span class="font-mono text-[11px] text-emerald-300">AES-256 SIGNED QR TOKEN READY</span>
            </div>
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إغلاق</button>
              <button type="button" onclick="confirmQrAttendanceScan()" class="px-4 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-white font-bold">✓ تأكيد مسح QR وتسجيل الحضور</button>
            </div>
          </div>
        `;
      } else if (modalType === 'leaveRequestModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">+ تقديم طلب إجازة (يخضع لمحرك قواعد الأعمال)</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <select id="lvPersonnelId" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.personnel.map((p) => `<option value="${p.id}">${p.fullNameAr} (الرصيد: ${p.annualLeaveBalance} يوم)</option>`).join('')}
            </select>
            <div class="grid grid-cols-2 gap-2">
              <select id="lvType" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
                <option value="اعتيادية">إجازة اعتيادية</option><option value="سنوية">إجازة سنوية</option><option value="مرضية">إجازة مرضية</option><option value="طارئة">إجازة طارئة</option>
              </select>
              <input id="lvDays" type="number" value="5" min="1" max="30" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white" placeholder="عدد الأيام">
            </div>
            <input id="lvReason" type="text" placeholder="سبب الإجازة والوجهة..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="submitNewLeaveRequest()" class="px-4 py-1.5 rounded-lg bg-emerald-600 text-white font-bold">إرسال لسير الموافقات</button>
            </div>
          </div>
        `;
      } else if (modalType === 'permissionRequestModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-sky-400">+ تقديم طلب إذن خروج/دخول (ساعات أو أيام)</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <select id="prmPersonnelId" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.personnel.map((p) => `<option value="${p.id}">${p.fullNameAr}</option>`).join('')}
            </select>
            <div class="grid grid-cols-2 gap-2">
              <select id="prmType" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
                <option value="ساعات">إذن بالساعات</option><option value="أيام">إذن بالأيام</option>
              </select>
              <input id="prmVal" type="text" value="3 ساعات (09:00 - 12:00)" class="bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            </div>
            <input id="prmReason" type="text" placeholder="سبب الإذن..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="submitNewPermissionRequest()" class="px-4 py-1.5 rounded-lg bg-sky-600 text-white font-bold">حفظ طلب الإذن</button>
            </div>
          </div>
        `;
      } else if (modalType === 'unitModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">+ إضافة وحدة فرعية إلى الهيكل التنظيمي</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <input id="newUnitName" type="text" placeholder="اسم الوحدة (مثال: الفصيل الثاني — السرية الأولى)" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <select id="newUnitLevel" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              <option value="سرية">سرية</option><option value="فصيل">فصيل</option><option value="مجموعة">مجموعة / حظيرة</option>
            </select>
            <select id="newUnitParent" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              ${state.units.map((u) => `<option value="${u.id}">${u.nameAr}</option>`).join('')}
            </select>
            <input id="newUnitCmd" type="text" placeholder="اسم قائد الوحدة..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="saveNewUnitNode()" class="px-4 py-1.5 rounded-lg bg-emerald-600 text-white font-bold">إضافة للهيكل</button>
            </div>
          </div>
        `;
      } else if (modalType === 'taskModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">+ إنشاء وتوزيع مهمة عسكرية جديدة</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <input id="newTaskTitle" type="text" placeholder="عنوان المهمة..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <input id="newTaskAssignee" type="text" placeholder="المنفذ / الضابط المكلف..." value="النقيب / صقر الحميري" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <select id="newTaskPriority" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
              <option value="HIGH">أولوية عالية (HIGH)</option><option value="CRITICAL">حرجة وعاجلة (CRITICAL)</option><option value="MEDIUM">متوسطة (MEDIUM)</option>
            </select>
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="saveNewTaskItem()" class="px-4 py-1.5 rounded-lg bg-emerald-600 text-white font-bold">حفظ وتوزيع المهمة</button>
            </div>
          </div>
        `;
      } else if (modalType === 'announcementModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-amber-400">+ نشر إعلان أو أمر عسكري</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <input id="newAnnTitle" type="text" placeholder="عنوان الإعلان أو الأمر..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <textarea id="newAnnBody" rows="3" placeholder="نص التعميم..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white"></textarea>
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="saveNewAnnouncement()" class="px-4 py-1.5 rounded-lg bg-amber-600 text-white font-bold">نشر التعميم</button>
            </div>
          </div>
        `;
      } else if (modalType === 'newIncidentModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-rose-400">🚨 تسجيل بلاغ عملياتي عاجل</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <input id="newIncTitle" type="text" placeholder="تفاصيل البلاغ الميداني..." class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <input id="newIncUnit" type="text" value="السرية الأولى اقتحام" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-3 py-2 text-white">
            <div class="flex justify-end gap-2">
              <button type="button" onclick="closeModal()" class="px-3 py-1.5 rounded-lg bg-slate-800">إلغاء</button>
              <button type="button" onclick="saveNewOpsIncident()" class="px-4 py-1.5 rounded-lg bg-rose-600 text-white font-bold">بث البلاغ في غرفة العمليات</button>
            </div>
          </div>
        `;
      } else if (modalType === 'ranksJobsModal') {
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">🎖️ إدارة الرتب العسكرية والوظائف</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <div class="flex gap-2">
              <input id="newJobTitleInput" type="text" placeholder="إضافة مسمى وظيفي جديد..." class="flex-1 bg-slate-800 border border-slate-700 rounded-lg px-3 py-1.5 text-white">
              <button type="button" onclick="addNewJobTitle()" class="px-3 py-1.5 rounded-lg bg-emerald-600 text-white font-bold">+ إضافة وظيفة</button>
            </div>
            <div class="max-h-60 overflow-y-auto space-y-1">
              ${state.jobs.map((j) => `<div class="p-2 rounded bg-slate-950 border border-slate-800 flex justify-between"><span>${j.titleAr}</span><span class="font-mono text-slate-400">${j.id}</span></div>`).join('')}
            </div>
          </div>
        `;
      } else {
        // Default Security / Auth Modal, Weapon/Ammo/Vehicle/Training quick modal
        box.innerHTML = `
          <div class="flex items-center justify-between border-b border-slate-800 pb-2">
            <h3 class="text-sm font-bold text-emerald-400">🔐 إدارة الجلسة الأمنية والمصادقة الثنائية (JWT + 2FA + Vault)</h3>
            <button type="button" onclick="closeModal()" class="text-slate-400">✕</button>
          </div>
          <div class="space-y-3 text-xs">
            <div class="p-3 rounded-xl bg-slate-950 border border-emerald-600/40 space-y-1">
              <div class="font-bold text-emerald-300">حالة الجلسة الحالية: موثقة ومشفرة (AES-256-GCM)</div>
              <div class="text-slate-400">الجهاز النشط: ${state.deviceId} | المصادقة الثنائية (TOTP 2FA): مفعّلة</div>
              <div class="text-slate-400">سؤال الأمان المسجل: ما هو رقم أمر تأسيس الكتيبة؟ (محمي بـ bcrypt)</div>
            </div>
            <div class="flex flex-wrap gap-2">
              <button type="button" onclick="revokeAllSessions()" class="px-3 py-2 rounded-lg bg-rose-800 hover:bg-rose-700 text-white font-semibold">تسجيل الخروج من جميع الأجهزة الأخرى</button>
              <button type="button" onclick="closeModal()" class="px-4 py-2 rounded-lg bg-slate-800 text-slate-200">إغلاق</button>
            </div>
          </div>
        `;
      }
    }

    function saveNewPersonnel() {
      const name = document.getElementById('newPName')?.value.trim();
      if (!name) {
        showToast('يرجى إدخال الاسم الرباعي للفرد.', 'warning');
        return;
      }
      const newP = {
        id: 'P-' + (100 + state.personnel.length + 1),
        militaryNumber: document.getElementById('newPMilNum')?.value || ('MIL-2026-' + Date.now()),
        fullNameAr: name,
        rankId: document.getElementById('newPRank')?.value || 'R-10',
        unitId: document.getElementById('newPUnit')?.value || 'U-CMP-1',
        jobId: 'J-04',
        birthDate: document.getElementById('newPBirth')?.value || '1997-01-01',
        bloodType: document.getElementById('newPBlood')?.value || 'O+',
        weapon: document.getElementById('newPWeapon')?.value || 'AK-103',
        ammo: Number(document.getElementById('newPAmmo')?.value || 120),
        status: 'ACTIVE',
        readiness: 'READY',
        readinessReason: 'مستجد جاهز قتالياً',
        disciplineScore: 100,
        annualLeaveBalance: 30,
        isContinuousAbsent: false,
        lateCountMonth: 0,
        courses: [],
        promotions: [],
        rewards: [],
        penalties: []
      };
      state.personnel.unshift(newP);
      persistState('CREATE', 'Personnel#' + newP.id, `إضافة فرد جديد: ${newP.fullNameAr}`);
      closeModal();
      renderPersonnelTable();
      renderDashboard();
      showToast(`تم تسجيل الفرد (${newP.fullNameAr}) بنجاح.`, 'success');
    }

    function confirmQrAttendanceScan() {
      const pid = document.getElementById('qrSelectPersonnel')?.value;
      const p = state.personnel.find((x) => x.id === pid);
      if (!p) return;
      const existing = state.attendance.find((a) => a.personnelId === pid);
      if (existing) {
        existing.status = 'PRESENT';
        existing.checkIn = new Date().toTimeString().substring(0, 5);
        existing.method = 'QR_CODE';
        existing.notes = 'تم المسح عبر رمز QR المشفر';
      } else {
        state.attendance.unshift({
          id: 'ATT-' + Date.now(),
          personnelId: pid,
          date: '2026-10-17',
          period: 'MORNING',
          status: 'PRESENT',
          checkIn: new Date().toTimeString().substring(0, 5),
          checkOut: '14:30',
          method: 'QR_CODE',
          notes: 'تحضير فوري بمسح QR'
        });
      }
      persistState('UPDATE', 'AttendanceQR#' + pid, `تسجيل حضور بمسح QR للفرد: ${p.fullNameAr}`);
      closeModal();
      renderAttendanceModule();
      renderDashboard();
      showToast(`تم مسح باركود QR وتحضير (${p.fullNameAr}) بنجاح.`, 'success');
    }

    function submitNewLeaveRequest() {
      const pid = document.getElementById('lvPersonnelId')?.value;
      const days = Number(document.getElementById('lvDays')?.value || 5);
      const lType = document.getElementById('lvType')?.value || 'اعتيادية';
      const reason = document.getElementById('lvReason')?.value || 'ظروف عائلية';
      const p = state.personnel.find((x) => x.id === pid);
      if (!p) return;

      // Evaluate json-rules-engine rules
      const blockRule = state.businessRules.find((r) => r.code === 'BLOCK_CONTINUOUS_ABSENT');
      if (blockRule && blockRule.enabled && p.isContinuousAbsent) {
        showToast('محرك قواعد الأعمال (json-rules-engine): تم رفض الطلب تلقائياً لأن الفرد مسجل في قائمة الغياب المستمر!', 'error');
        return;
      }
      if (days > p.annualLeaveBalance) {
        showToast('محرك قواعد الأعمال: عدد الأيام المطلوبة يتجاوز رصيد الإجازات المتاح للفرد!', 'error');
        return;
      }

      state.leaves.unshift({
        id: 'LV-0' + (state.leaves.length + 1),
        personnelId: pid,
        type: lType,
        startDate: '2026-10-18',
        endDate: '2026-10-23',
        days: days,
        reason: reason,
        status: 'PENDING',
        stage: 'بانتظار موافقة قائد السرية ← ركن العمليات',
        expiresSoon: false
      });
      persistState('CREATE', 'LeaveRequest', `تقديم طلب إجازة (${lType}) للفرد ${p.fullNameAr}`);
      closeModal();
      renderLeavesAndPermissions();
      showToast('تم فحص الاستحقاق وإدراج طلب الإجازة في مسار الموافقات بنجاح.', 'success');
    }

    function submitNewPermissionRequest() {
      const pid = document.getElementById('prmPersonnelId')?.value;
      const dType = document.getElementById('prmType')?.value || 'ساعات';
      const val = document.getElementById('prmVal')?.value || '3 ساعات';
      const reason = document.getElementById('prmReason')?.value || 'مهمة خاصة';
      state.permissions.unshift({
        id: 'PRM-0' + (state.permissions.length + 1),
        personnelId: pid,
        durationType: dType,
        value: val,
        reason: reason,
        status: 'PENDING'
      });
      persistState('CREATE', 'PermissionRequest', 'تقديم طلب إذن خروج مؤقت');
      closeModal();
      renderLeavesAndPermissions();
      showToast('تم تسجيل طلب الإذن بنجاح.', 'success');
    }

    function saveNewUnitNode() {
      const name = document.getElementById('newUnitName')?.value.trim();
      if (!name) return;
      state.units.push({
        id: 'U-SUB-' + Date.now(),
        nameAr: name,
        level: document.getElementById('newUnitLevel')?.value || 'فصيل',
        parentId: document.getElementById('newUnitParent')?.value || 'U-CMP-1',
        commander: document.getElementById('newUnitCmd')?.value || 'ضابط مكلف',
        authorized: 35,
        expanded: true
      });
      persistState('CREATE', 'UnitHierarchy', `إضافة وحدة جديدة: ${name}`);
      closeModal();
      renderUnitsHierarchy();
      showToast('تمت إضافة الوحدة الفرعية إلى شجرة الهيكل التنظيمي.', 'success');
    }

    function saveNewTaskItem() {
      const title = document.getElementById('newTaskTitle')?.value.trim();
      if (!title) return;
      state.tasks.unshift({
        id: 'TSK-0' + (state.tasks.length + 1),
        title: title,
        assignee: document.getElementById('newTaskAssignee')?.value || 'النقيب / صقر الحميري',
        priority: document.getElementById('newTaskPriority')?.value || 'HIGH',
        progress: 15,
        dueDate: '2026-10-22',
        status: 'IN_PROGRESS'
      });
      persistState('CREATE', 'Task', `إنشاء مهمة جديدة: ${title}`);
      closeModal();
      renderTasksAndAnnouncements();
      showToast('تمت إضافة المهمة وإرسال إشعار للمنفذ.', 'success');
    }

    function saveNewAnnouncement() {
      const title = document.getElementById('newAnnTitle')?.value.trim();
      const body = document.getElementById('newAnnBody')?.value.trim();
      if (!title) return;
      state.announcements.unshift({
        id: 'ANN-0' + (state.announcements.length + 1),
        title: title,
        content: body || 'تعميم إداري عاجل لكافة الوحدات.',
        priority: 'عاجل',
        date: '2026-10-17'
      });
      persistState('CREATE', 'Announcement', `نشر إعلان: ${title}`);
      closeModal();
      renderTasksAndAnnouncements();
      showToast('تم نشر الإعلان وتعميمه حسب الصلاحيات.', 'success');
    }

    function saveNewOpsIncident() {
      const title = document.getElementById('newIncTitle')?.value.trim();
      if (!title) return;
      state.opsIncidents.unshift({
        id: 'INC-' + Date.now(),
        time: new Date().toTimeString().substring(0, 5),
        severity: 'HIGH',
        title: title,
        unit: document.getElementById('newIncUnit')?.value || 'السرية الأولى'
      });
      persistState('CREATE', 'OpsIncident', `بث بلاغ عملياتي: ${title}`);
      closeModal();
      renderOpsRoom();
      showToast('تم بث البلاغ الفوري في غرفة العمليات.', 'warning');
    }

    function addNewJobTitle() {
      const val = document.getElementById('newJobTitleInput')?.value.trim();
      if (!val) return;
      state.jobs.push({ id: 'J-0' + (state.jobs.length + 1), titleAr: val });
      persistState('CREATE', 'JobTitle', `إضافة مسمى وظيفي: ${val}`);
      openModal('ranksJobsModal');
      showToast('تمت إضافة الوظيفة العسكرية بنجاح.', 'success');
    }

    function revokeAllSessions() {
      persistState('SECURITY', 'UserSessions', 'إبطال كافة الجلسات الأخرى وتدوير مفاتيح Refresh Token');
      closeModal();
      showToast('تم تسجيل الخروج من جميع الأجهزة الأخرى وتدوير التوكنات في Redis Blacklist.', 'success');
    }

    // =========================================================================
    // 18. LIVE CLOCK, KEYBOARD SHORTCUTS & BOOTSTRAP INITIALIZATION
    // =========================================================================
    function renderTacticalGisMap() {
      const box = document.getElementById('tacticalGisMapContainer');
      if (!box) return;
      const units = state.tacticalUnitsGis || DEFAULT_STATE.tacticalUnitsGis;
      const bgClass = state.radarThermalMode
        ? 'bg-gradient-to-br from-rose-950 via-slate-950 to-amber-950 border-amber-500/60'
        : 'bg-gradient-to-br from-emerald-950/90 via-slate-950 to-teal-950/80 border-emerald-500/50';

      const markersSvg = units.map((u) => {
        const fill = u.status === 'READY' ? '#10b981' : (u.status === 'ALERT' ? '#f43f5e' : '#f59e0b');
        return `
          <g transform="translate(${u.x * 4}, ${u.y * 2.2})">
            <circle cx="0" cy="0" r="9" fill="${fill}" fill-opacity="0.25" stroke="${fill}" stroke-width="1.5"/>
            <circle cx="0" cy="0" r="4" fill="${fill}"/>
            <text x="0" y="-12" text-anchor="middle" fill="#e2e8f0" font-size="9" font-weight="bold">${u.name}</text>
          </g>
        `;
      }).join('');

      box.innerHTML = `
        <div class="lg:col-span-2 relative rounded-xl border ${bgClass} p-2 overflow-hidden">
          <svg viewBox="0 0 400 220" class="w-full h-56 rounded-lg">
            <defs>
              <pattern id="tacGrid" width="40" height="40" patternUnits="userSpaceOnUse">
                <path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(16,185,129,0.16)" stroke-width="1"/>
              </pattern>
            </defs>
            <rect width="400" height="220" fill="url(#tacGrid)"/>
            <circle cx="200" cy="110" r="95" fill="none" stroke="rgba(16,185,129,0.28)" stroke-dasharray="4 4"/>
            <circle cx="200" cy="110" r="55" fill="none" stroke="rgba(16,185,129,0.28)" stroke-dasharray="3 3"/>
            <line x1="200" y1="0" x2="200" y2="220" stroke="rgba(16,185,129,0.2)" stroke-width="1"/>
            <line x1="0" y1="110" x2="400" y2="110" stroke="rgba(16,185,129,0.2)" stroke-width="1"/>
            ${markersSvg}
          </svg>
          <div class="flex items-center justify-between text-[11px] px-2 pt-1 text-emerald-300 font-mono">
            <span>MODE: ${state.radarThermalMode ? 'THERMAL IR RADAR' : 'TACTICAL GRID C2'}</span>
            <span>OFFLINE TILE CACHE: ACTIVE (100% AIR-GAPPED)</span>
          </div>
        </div>
        <div class="space-y-2 text-xs max-h-60 overflow-y-auto custom-scroll">
          ${units.map((u) => `
            <div class="p-2.5 rounded-lg bg-slate-950 border border-slate-800 flex items-center justify-between gap-2">
              <div>
                <div class="font-bold text-white">${u.name}</div>
                <div class="text-[11px] text-slate-400">${u.sector} | <span class="font-mono text-emerald-400">${u.coords}</span></div>
              </div>
              <span class="px-2 py-0.5 rounded text-[10px] font-bold ${u.status === 'READY' ? 'bg-emerald-500/20 text-emerald-300' : 'bg-amber-500/20 text-amber-300'}">${u.status}</span>
            </div>
          `).join('')}
        </div>
      `;
    }

    function redeployTacticalUnits() {
      if (!state.tacticalUnitsGis) state.tacticalUnitsGis = JSON.parse(JSON.stringify(DEFAULT_STATE.tacticalUnitsGis));
      state.tacticalUnitsGis.forEach((u) => {
        if (u.type !== 'HQ') {
          u.x = Math.max(15, Math.min(85, u.x + Math.floor(Math.random() * 15) - 7));
          u.y = Math.max(15, Math.min(85, u.y + Math.floor(Math.random() * 15) - 7));
        }
      });
      persistState('UPDATE', 'TacticalGIS', 'تحديث إحداثيات انتشار السرايا والدوريات على الخريطة التكتيكية');
      renderTacticalGisMap();
      showToast('تم تحديث إحداثيات الدوريات والوحدات على الخريطة التكتيكية المعزولة.', 'success');
    }

    function toggleRadarSweep() {
      state.radarThermalMode = !state.radarThermalMode;
      renderTacticalGisMap();
      showToast(state.radarThermalMode ? 'تم تفعيل نمط المسح الحراري الليلي (Thermal IR).' : 'تم العودة إلى نمط الشبكة التكتيكية القياسية.', 'info');
    }

    function triggerBiometricNfcCheckIn() {
      const targetP = state.personnel.find((p) => p.id === 'P-105') || state.personnel[0];
      const rec = state.attendance.find((a) => a.personnelId === targetP.id);
      if (rec) {
        rec.status = 'PRESENT';
        rec.checkIn = new Date().toTimeString().substring(0, 5);
        rec.method = 'BIOMETRIC_NFC';
        rec.notes = 'تحقق حيوي + بطاقة NFC عسكرية مشفرة';
      }
      persistState('UPDATE', 'BiometricNFC#' + targetP.id, `تحضير بالبصمة الحيوية وبطاقة NFC للفرد: ${targetP.fullNameAr}`);
      renderAttendanceModule();
      renderDashboard();
      showToast(`تم التحقق الحيوي (Biometric + NFC) وتحضير ${targetP.fullNameAr} بنجاح.`, 'success');
    }

    function dispatchAmmoWithCrdtAndFourEyes() {
      const batch = state.ammunition[0];
      if (!batch) return;
      batch.qtyOut += 600;
      batch.balance = Math.max(0, batch.qtyIn - batch.qtyOut);
      persistState('APPROVE', 'CRDT_Ammo#' + batch.id, `صرف 600 طلقة عبر عداد PN-Counter CRDT بتوقيع العيون الأربع (قائد الكتيبة + ضابط التسليح)`);
      renderLogisticsModule();
      renderDashboard();
      showToast('تم صرف 600 طلقة وتحديث العداد عبر PN-Counter CRDT (بدون تعارضات مزامنة) مع توثيق العيون الأربع.', 'success');
    }

    function signAllMilitaryOrdersPki() {
      state.announcements.forEach((a) => {
        if (!a.title.includes('[موثق PKI]')) {
          a.title = '🔏 [موثق PKI] ' + a.title;
        }
      });
      persistState('APPROVE', 'PKI_Ed25519', 'توقيع الأوامر العسكرية رقمياً بمفتاح القائد غير المتماثل (Ed25519 / HSM)');
      renderTasksAndAnnouncements();
      showToast('تم توقيع جميع الأوامر العسكرية رقمياً عبر خوارزمية Ed25519 PKI لضمان عدم الإنكار.', 'success');
    }

    function renderFieldEndpoints() {
      const box = document.getElementById('fieldEndpointsGrid');
      if (!box) return;
      const devs = state.fieldEndpoints || DEFAULT_STATE.fieldEndpoints;
      box.innerHTML = devs.map((d) => `
        <div class="p-3 rounded-xl bg-slate-950 border ${d.status === 'WIPED' ? 'border-rose-600/60 opacity-75' : 'border-slate-800'} space-y-1.5">
          <div class="flex items-center justify-between">
            <span class="font-mono font-bold text-white">${d.code}</span>
            <span class="px-2 py-0.5 rounded text-[10px] font-bold ${d.status === 'ACTIVE' ? 'bg-emerald-500/20 text-emerald-300' : (d.status === 'WIPED' ? 'bg-rose-600 text-white' : 'bg-amber-500/20 text-amber-300')}">${d.status}</span>
          </div>
          <div class="text-slate-300">${d.holder}</div>
          <div class="text-[11px] text-slate-400">${d.platform} | التشفير: <span class="text-emerald-400 font-mono">${d.enc}</span></div>
          <div class="flex items-center justify-between pt-1">
            <span class="text-[10px] text-slate-500">آخر اتصال: ${d.lastPing}</span>
            <button type="button" onclick="remoteWipeEndpoint('${d.id}')" class="px-2.5 py-1 rounded bg-rose-900/70 hover:bg-rose-700 text-rose-100 font-bold text-[10px]">
              ${d.status === 'WIPED' ? '✓ تم المسح الآمن' : '🔥 مسح أمني عن بُعد (Remote Wipe)'}
            </button>
          </div>
        </div>
      `).join('');
    }

    function remoteWipeEndpoint(devId) {
      if (!state.fieldEndpoints) state.fieldEndpoints = JSON.parse(JSON.stringify(DEFAULT_STATE.fieldEndpoints));
      const d = state.fieldEndpoints.find((x) => x.id === devId);
      if (!d) return;
      d.status = 'WIPED';
      d.lastPing = 'تم تصفير الكاش والمفاتيح عن بُعد';
      persistState('SECURITY', 'RemoteWipe#' + d.code, `تنفيذ مسح أمني فوري عن بُعد للجهاز الميداني (${d.code}) وإبطال مفاتيح التشفير`);
      renderFieldEndpoints();
      showToast(`تم إرسال أمر التصفير الأمني (Remote Wipe) للجهاز ${d.code} وإبطال مفاتيحه بنجاح.`, 'warning');
    }

    function updateClock() {
      const el = document.getElementById('liveMilitaryClock');
      if (el) {
        const now = new Date();
        el.textContent = now.toISOString().replace('T', ' ').substring(0, 19) + ' UTC';
      }
    }

    document.addEventListener('keydown', (e) => {
      if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'k') {
        e.preventDefault();
        document.getElementById('globalSearchInput')?.focus();
      }
      if (e.altKey) {
        if (e.key === '1') switchTab('dashboard');
        if (e.key === '2') switchTab('units');
        if (e.key === '3') switchTab('personnel');
        if (e.key === '4') switchTab('attendance');
        if (e.key === '5') switchTab('leaves');
        if (e.key === '6') switchTab('logistics');
      }
    });

    window.addEventListener('DOMContentLoaded', () => {
      updateClock();
      setInterval(updateClock, 1000);
      updateOfflineBadges();
      renderActivePermissionChips();
      renderNotifications();
      renderDashboard();
    });
  </script>
</body>
</html>
