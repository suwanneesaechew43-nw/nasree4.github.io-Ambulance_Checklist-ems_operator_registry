<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ทะเบียนผู้ปฏิบัติการ EMS ปี 2568</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Font Prompt for Thai UI -->
    <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Prompt', 'sans-serif'],
                    },
                    colors: {
                        ems: {
                            50: '#f0fdfa',
                            100: '#ccfbf1',
                            500: '#14b8a6',
                            600: '#0d9488',
                            700: '#0f766e',
                            800: '#115e59',
                            900: '#134e4a',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Prompt', sans-serif; }
        .glass-header {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col antialiased">

    <!-- Top Header -->
    <header class="sticky top-0 z-30 glass-header border-b border-slate-200/80 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 sm:h-20">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-gradient-to-tr from-teal-600 to-emerald-500 flex items-center justify-center text-white shadow-md shadow-teal-500/20">
                        <i class="fa-solid font-bold fa-truck-medical text-lg sm:text-2xl"></i>
                    </div>
                    <div>
                        <h1 class="text-lg sm:text-xl font-bold text-slate-900 tracking-tight leading-tight">ระบบทะเบียนผู้ปฏิบัติการ EMS</h1>
                        <p class="text-xs sm:text-sm text-slate-500 flex items-center gap-1.5">
                            <span><i class="fa-regular fa-calendar-check text-emerald-600"></i> ประจำปี พ.ศ. 2568</span>
                            <span class="hidden sm:inline text-slate-300">•</span>
                            <span class="hidden sm:inline text-slate-500">งานการพยาบาลผู้ป่วยอุบัติเหตุฉุกเฉินและนิติเวช</span>
                        </p>
                    </div>
                </div>
                <div class="flex items-center gap-2 sm:gap-3">
                    <button onclick="openInfoModal()" class="px-3 py-2 text-xs sm:text-sm font-medium text-slate-600 bg-slate-100 hover:bg-slate-200 rounded-lg transition-colors flex items-center gap-1.5">
                        <i class="fa-solid fa-circle-info text-teal-600"></i>
                        <span class="hidden sm:inline">ข้อมูลการประกาศ</span>
                    </button>
                    <button onclick="openTelegramModal()" class="px-3 py-2 text-xs sm:text-sm font-semibold text-white bg-sky-600 hover:bg-sky-700 active:bg-sky-800 rounded-lg shadow-sm transition-all flex items-center gap-1.5 relative">
                        <i class="fa-brands fa-telegram text-base"></i>
                        <span>แจ้งเตือน Telegram</span>
                        <span id="telegramBadge" class="hidden px-1.5 py-0.5 text-[10px] bg-rose-500 text-white rounded-full font-bold ml-0.5">0</span>
                    </button>
                    <button onclick="openAddModal()" class="px-3.5 py-2 text-xs sm:text-sm font-semibold text-white bg-teal-600 hover:bg-teal-700 active:bg-teal-800 rounded-lg shadow-sm transition-all flex items-center gap-1.5">
                        <i class="fa-solid fa-plus"></i>
                        <span>เพิ่มผู้ปฏิบัติการ</span>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 space-y-6">

        <!-- KPI Metrics Dashboard -->
        <div class="grid grid-cols-2 lg:grid-cols-5 gap-3 sm:gap-4">
            <!-- Card 1: Total Personnel -->
            <div class="bg-white p-4 rounded-xl border border-slate-200/80 shadow-sm flex items-center justify-between">
                <div>
                    <p class="text-xs font-medium text-slate-500">ผู้ปฏิบัติการทั้งหมด</p>
                    <h3 id="statTotal" class="text-2xl font-bold text-slate-900 mt-1">43</h3>
                    <p class="text-[11px] text-slate-400 mt-0.5">คนในระบบ</p>
                </div>
                <div class="w-10 h-10 rounded-lg bg-teal-50 text-teal-600 flex items-center justify-center">
                    <i class="fa-solid fa-users text-lg"></i>
                </div>
            </div>

            <!-- Card 2: ALS Level -->
            <div class="bg-white p-4 rounded-xl border border-slate-200/80 shadow-sm flex items-center justify-between">
                <div>
                    <p class="text-xs font-medium text-slate-500">ระดับ ALS</p>
                    <h3 id="statALS" class="text-2xl font-bold text-teal-700 mt-1">37</h3>
                    <p class="text-[11px] text-teal-600/80 mt-0.5">การช่วยชีวิตขั้นสูง</p>
                </div>
                <div class="w-10 h-10 rounded-lg bg-teal-50 text-teal-600 flex items-center justify-center">
                    <i class="fa-solid fa-user-doctor text-lg"></i>
                </div>
            </div>

            <!-- Card 3: EMR Level -->
            <div class="bg-white p-4 rounded-xl border border-slate-200/80 shadow-sm flex items-center justify-between">
                <div>
                    <p class="text-xs font-medium text-slate-500">ระดับ EMR</p>
                    <h3 id="statEMR" class="text-2xl font-bold text-sky-700 mt-1">1</h3>
                    <p class="text-[11px] text-sky-600/80 mt-0.5">ผู้ปฐมพยาบาลขั้นต้น</p>
                </div>
                <div class="w-10 h-10 rounded-lg bg-sky-50 text-sky-600 flex items-center justify-center">
                    <i class="fa-solid fa-kit-medical text-lg"></i>
                </div>
            </div>

            <!-- Card 4: Driver Role -->
            <div class="bg-white p-4 rounded-xl border border-slate-200/80 shadow-sm flex items-center justify-between">
                <div>
                    <p class="text-xs font-medium text-slate-500">พนักงานขับรถ (Driver)</p>
                    <h3 id="statDriver" class="text-2xl font-bold text-indigo-700 mt-1">5</h3>
                    <p class="text-[11px] text-indigo-600/80 mt-0.5">พนักงานขับรถพยาบาล</p>
                </div>
                <div class="w-10 h-10 rounded-lg bg-indigo-50 text-indigo-600 flex items-center justify-center">
                    <i class="fa-solid fa-ambulance text-lg"></i>
                </div>
            </div>

            <!-- Card 5: Expiring in 6 Months -->
            <div class="col-span-2 lg:col-span-1 bg-gradient-to-br from-amber-500/10 via-amber-500/5 to-transparent p-4 rounded-xl border border-amber-200 shadow-sm flex items-center justify-between">
                <div>
                    <p class="text-xs font-medium text-amber-800">ต้องต่ออายุ (ภายใน 6 เดือน)</p>
                    <h3 id="statExp70" class="text-2xl font-bold text-amber-700 mt-1">0</h3>
                    <p class="text-[11px] text-amber-600 mt-0.5">ต้องแจ้งเตือนต่ออายุ</p>
                </div>
                <div class="w-10 h-10 rounded-lg bg-amber-500/20 text-amber-700 flex items-center justify-center">
                    <i class="fa-solid fa-bell text-lg"></i>
                </div>
            </div>
        </div>

        <!-- Search and Filter Controls -->
        <div class="bg-white rounded-xl border border-slate-200/80 shadow-sm p-4 space-y-4">
            <div class="flex flex-col md:flex-row items-stretch md:items-center justify-between gap-3">
                
                <!-- Search Box -->
                <div class="relative flex-1">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                    <input type="text" id="searchInput" oninput="renderApp()" placeholder="ค้นหาตามชื่อ, เลข สพฉ., ระดับ หรือวันหมดอายุ..." class="w-full pl-10 pr-9 py-2 bg-slate-50 border border-slate-200 rounded-lg text-sm text-slate-800 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500 transition-all">
                    <button id="clearSearchBtn" onclick="clearSearch()" class="hidden absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 hover:text-slate-600">
                        <i class="fa-solid fa-circle-xmark"></i>
                    </button>
                </div>

                <!-- Year Expiry Filter Dropdown & Controls -->
                <div class="flex items-center gap-2 flex-wrap sm:flex-nowrap">
                    <div class="relative flex-1 sm:flex-none">
                        <select id="yearFilter" onchange="renderApp()" class="w-full sm:w-auto pl-3 pr-8 py-2 bg-slate-50 border border-slate-200 rounded-lg text-xs font-medium text-slate-700 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500 appearance-none">
                            <option value="ALL">🗓️ วันหมดอายุ: ทั้งหมด</option>
                            <option value="2570">ปี 2570</option>
                            <option value="2571">ปี 2571</option>
                            <option value="2572">ปี 2572</option>
                            <option value="2573">ปี 2573</option>
                            <option value="2574">ปี 2574</option>
                            <option value="NONE">ไม่ระบุวันหมดอายุ</option>
                        </select>
                        <i class="fa-solid fa-chevron-down absolute right-2.5 top-1/2 -translate-y-1/2 text-slate-400 text-xs pointer-events-none"></i>
                    </div>

                    <!-- View Switcher -->
                    <div class="flex items-center bg-slate-100 p-1 rounded-lg border border-slate-200/80">
                        <button id="btnViewTable" onclick="setViewMode('table')" class="px-3 py-1.5 text-xs font-semibold rounded-md bg-white text-slate-800 shadow-xs transition-all flex items-center gap-1.5">
                            <i class="fa-solid fa-list"></i>
                            <span class="hidden sm:inline">ตาราง</span>
                        </button>
                        <button id="btnViewGrid" onclick="setViewMode('grid')" class="px-3 py-1.5 text-xs font-semibold rounded-md text-slate-500 hover:text-slate-800 transition-all flex items-center gap-1.5">
                            <i class="fa-solid fa-grip"></i>
                            <span class="hidden sm:inline">การ์ด</span>
                        </button>
                    </div>

                    <!-- Export CSV Button -->
                    <button onclick="exportCSV()" class="px-3 py-2 text-xs font-medium text-slate-700 bg-slate-100 hover:bg-slate-200 border border-slate-200 rounded-lg transition-colors flex items-center gap-1.5">
                        <i class="fa-solid fa-file-csv text-emerald-600"></i>
                        <span class="hidden sm:inline">ส่งออก CSV</span>
                    </button>
                </div>
            </div>

            <!-- Role Quick Filter Chips -->
            <div class="flex items-center gap-1.5 overflow-x-auto pb-1 pt-1 border-t border-slate-100 text-xs">
                <span class="text-slate-400 text-[11px] font-medium mr-1">ระดับ:</span>
                <button id="chipRoleALL" onclick="setRoleFilter('ALL')" class="px-3 py-1.5 text-xs font-semibold rounded-lg bg-teal-600 text-white shadow-xs transition-all flex items-center gap-1.5">
                    <span>ทั้งหมด</span>
                    <span id="countRoleALL" class="bg-white/20 px-1.5 py-0.2 rounded-full text-[10px]">43</span>
                </button>
                <button id="chipRoleALS" onclick="setRoleFilter('ALS')" class="px-3 py-1.5 text-xs font-medium rounded-lg bg-white text-slate-600 hover:bg-slate-100 border border-slate-200 transition-all flex items-center gap-1.5">
                    <span>ALS</span>
                    <span id="countRoleALS" class="bg-slate-100 text-slate-600 px-1.5 py-0.2 rounded-full text-[10px]">37</span>
                </button>
                <button id="chipRoleEMR" onclick="setRoleFilter('EMR')" class="px-3 py-1.5 text-xs font-medium rounded-lg bg-white text-slate-600 hover:bg-slate-100 border border-slate-200 transition-all flex items-center gap-1.5">
                    <span>EMR</span>
                    <span id="countRoleEMR" class="bg-slate-100 text-slate-600 px-1.5 py-0.2 rounded-full text-[10px]">1</span>
                </button>
                <button id="chipRoleDriver" onclick="setRoleFilter('Driver')" class="px-3 py-1.5 text-xs font-medium rounded-lg bg-white text-slate-600 hover:bg-slate-100 border border-slate-200 transition-all flex items-center gap-1.5">
                    <span>Driver</span>
                    <span id="countRoleDriver" class="bg-slate-100 text-slate-600 px-1.5 py-0.2 rounded-full text-[10px]">5</span>
                </button>
            </div>
        </div>

        <!-- Data Table Container -->
        <div id="tableView" class="bg-white rounded-xl border border-slate-200/80 shadow-sm overflow-hidden">
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse text-xs sm:text-sm">
                    <thead>
                        <tr class="bg-slate-50 border-b border-slate-200 text-slate-600 font-semibold uppercase tracking-wider text-[11px]">
                            <th class="py-3 px-4 text-center w-12">#</th>
                            <th class="py-3 px-4 cursor-pointer hover:bg-slate-100 transition-colors" onclick="sortBy('name')">
                                ชื่อ - นามสกุล <i class="fa-solid fa-sort text-slate-300 ml-1"></i>
                            </th>
                            <th class="py-3 px-4 cursor-pointer hover:bg-slate-100 transition-colors" onclick="sortBy('role')">
                                ระดับ <i class="fa-solid fa-sort text-slate-300 ml-1"></i>
                            </th>
                            <th class="py-3 px-4">เลข สพฉ.</th>
                            <th class="py-3 px-4 cursor-pointer hover:bg-slate-100 transition-colors" onclick="sortBy('expiry')">
                                วันหมดอายุ <i class="fa-solid fa-sort text-slate-300 ml-1"></i>
                            </th>
                            <th class="py-3 px-4 text-center">รับทราบ Scope</th>
                            <th class="py-3 px-4 text-right">จัดการ</th>
                        </tr>
                    </thead>
                    <tbody id="tableBody" class="divide-y divide-slate-100">
                        <!-- Populated by JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Data Grid View Container -->
        <div id="gridView" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4 hidden">
            <!-- Populated by JavaScript -->
        </div>

        <!-- Empty State Message -->
        <div id="emptyState" class="hidden bg-white rounded-xl border border-slate-200 p-8 text-center space-y-3">
            <div class="w-12 h-12 mx-auto rounded-full bg-slate-100 flex items-center justify-center text-slate-400 text-xl">
                <i class="fa-solid fa-user-slash"></i>
            </div>
            <h4 class="text-sm font-semibold text-slate-700">ไม่พบข้อมูลผู้ปฏิบัติการ</h4>
            <p class="text-xs text-slate-400">ลองเปลี่ยนคำค้นหา หรือรีเซ็ตตัวกรองเพื่อแสดงผลข้อมูลอีกครั้ง</p>
        </div>

    </main>

    <!-- Modal: Telegram Notification Center -->
    <div id="telegramModal" class="fixed inset-0 bg-slate-900/40 backdrop-blur-xs z-50 flex items-center justify-center p-4 hidden opacity-0 transition-opacity duration-200">
        <div class="bg-white rounded-2xl max-w-xl w-full p-6 shadow-2xl transform scale-95 transition-transform duration-200 max-h-[90vh] flex flex-col">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100">
                <div class="flex items-center gap-2.5">
                    <div class="w-10 h-10 rounded-xl bg-sky-50 text-sky-600 flex items-center justify-center">
                        <i class="fa-brands fa-telegram text-2xl"></i>
                    </div>
                    <div>
                        <h3 class="text-base font-bold text-slate-900">แจ้งเตือนวันหมดอายุผ่าน Telegram</h3>
                        <p class="text-xs text-slate-500">ระบบส่งข้อความแจ้งเตือนใบอนุญาตเข้า Telegram Group</p>
                    </div>
                </div>
                <button onclick="closeTelegramModal()" class="text-slate-400 hover:text-slate-600">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <div class="py-4 overflow-y-auto flex-1 space-y-4">
                <!-- Telegram Bot Info Banner -->
                <div class="bg-sky-50/70 p-3.5 rounded-xl border border-sky-100 text-xs text-sky-900 space-y-1">
                    <div class="flex items-center justify-between">
                        <span class="font-bold flex items-center gap-1.5"><i class="fa-solid fa-robot text-sky-600"></i> Telegram Bot Configured</span>
                        <span class="bg-sky-200/80 text-sky-800 text-[10px] px-2 py-0.5 rounded-full font-mono font-semibold">Active</span>
                    </div>
                    <p class="text-slate-600 text-[11px]"><strong>Group Chat ID:</strong> <span class="font-mono bg-white px-1.5 py-0.5 rounded border border-sky-200">-5593653503</span></p>
                    <p class="text-slate-500 text-[11px]">การตั้งเกณฑ์แจ้งเตือน: ล่วงหน้า 6 เดือน (180 วัน), 1 เดือน (30 วัน) และ 1 สัปดาห์ (7 วัน)</p>
                </div>

                <!-- Expiry Summary Cards Grid -->
                <div class="grid grid-cols-3 gap-2">
                    <div class="p-3 bg-rose-50 border border-rose-200 rounded-xl text-center">
                        <span class="text-[11px] font-semibold text-rose-700 block">1 สัปดาห์ / หมดอายุ</span>
                        <span id="tgCount1w" class="text-xl font-bold text-rose-800">0</span>
                        <span class="text-[10px] text-rose-600 block">ด่วนที่สุด</span>
                    </div>
                    <div class="p-3 bg-amber-50 border border-amber-200 rounded-xl text-center">
                        <span class="text-[11px] font-semibold text-amber-700 block">1 เดือน (&lt;= 30 วัน)</span>
                        <span id="tgCount1m" class="text-xl font-bold text-amber-800">0</span>
                        <span class="text-[10px] text-amber-600 block">ด่วนมาก</span>
                    </div>
                    <div class="p-3 bg-blue-50 border border-blue-200 rounded-xl text-center">
                        <span class="text-[11px] font-semibold text-blue-700 block">6 เดือน (&lt;= 180 วัน)</span>
                        <span id="tgCount6m" class="text-xl font-bold text-blue-800">0</span>
                        <span class="text-[10px] text-blue-600 block">เฝ้าระวัง</span>
                    </div>
                </div>

                <!-- List Preview -->
                <div>
                    <h4 class="text-xs font-bold text-slate-700 mb-2 flex items-center justify-between">
                        <span>รายชื่อที่เข้าร่วมเกณฑ์แจ้งเตือน</span>
                        <span id="tgTotalAlerts" class="text-[11px] text-slate-500 font-normal">รวม 0 คน</span>
                    </h4>
                    <div id="tgPreviewList" class="space-y-1.5 max-h-48 overflow-y-auto pr-1">
                        <!-- Populated by JS -->
                    </div>
                </div>

                <!-- Status Feedback Log -->
                <div id="tgLogBox" class="hidden p-3 rounded-lg text-xs font-mono"></div>
            </div>

            <div class="pt-4 border-t border-slate-100 flex items-center justify-between gap-2">
                <button type="button" onclick="testTelegramConnection()" class="px-3.5 py-2 text-xs font-medium text-slate-700 bg-slate-100 hover:bg-slate-200 rounded-lg transition-colors flex items-center gap-1.5">
                    <i class="fa-solid fa-plug text-sky-600"></i>
                    <span>ทดสอบการเชื่อมต่อ</span>
                </button>
                <div class="flex items-center gap-2">
                    <button type="button" onclick="closeTelegramModal()" class="px-3.5 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 rounded-lg transition-colors">
                        ปิด
                    </button>
                    <button id="btnSendTelegram" onclick="sendTelegramAlerts()" class="px-4 py-2 text-xs font-semibold text-white bg-sky-600 hover:bg-sky-700 active:bg-sky-800 rounded-lg shadow-sm transition-all flex items-center gap-1.5">
                        <i class="fa-solid fa-paper-plane"></i>
                        <span>ส่งแจ้งเตือนเข้า Telegram</span>
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal: Info & Communicator Summary -->
    <div id="infoModal" class="fixed inset-0 bg-slate-900/40 backdrop-blur-xs z-50 flex items-center justify-center p-4 hidden opacity-0 transition-opacity duration-200">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 shadow-2xl transform scale-95 transition-transform duration-200">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100">
                <div class="flex items-center gap-2.5">
                    <div class="w-9 h-9 rounded-lg bg-teal-50 text-teal-600 flex items-center justify-center">
                        <i class="fa-solid fa-file-circle-check text-lg"></i>
                    </div>
                    <h3 class="text-base font-bold text-slate-900">รายละเอียดเอกสารทะเบียน</h3>
                </div>
                <button onclick="closeInfoModal()" class="text-slate-400 hover:text-slate-600">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>
            <div class="py-4 space-y-3.5 text-xs sm:text-sm text-slate-600">
                <div class="bg-slate-50 p-3 rounded-lg border border-slate-100">
                    <p class="text-slate-400 text-[11px] mb-0.5">หัวข้อเอกสาร</p>
                    <p class="font-medium text-slate-800">4.1.2 ทะเบียนผู้ปฏิบัติการ EMS ปี 2568</p>
                </div>
                <div>
                    <p class="text-slate-400 text-[11px] mb-0.5">ผู้สื่อสารหลัก</p>
                    <p class="font-semibold text-slate-800">นางนันทวดี จอนเจิม</p>
                    <p class="text-slate-500 text-xs">หัวหน้างานการพยาบาลผู้ป่วยอุบัติเหตุฉุกเฉินและนิติเวช</p>
                </div>
                <div class="border-t border-slate-100 pt-3">
                    <p class="text-slate-400 text-[11px] mb-1">วิธีการสื่อสารและรับทราบ Scope</p>
                    <ul class="space-y-1.5 text-xs text-slate-700">
                        <li class="flex items-center gap-2"><i class="fa-solid fa-check text-emerald-600"></i> ประชุมชี้แจง วันที่ 1 ตุลาคม 2568</li>
                        <li class="flex items-center gap-2"><i class="fa-solid fa-check text-emerald-600"></i> เอกสารแจกจ่ายส่วนงาน</li>
                        <li class="flex items-center gap-2"><i class="fa-solid fa-check text-emerald-600"></i> ติดประกาศบอร์ดประชาสัมพันธ์</li>
                    </ul>
                </div>
            </div>
            <div class="pt-3 border-t border-slate-100 text-right">
                <button onclick="closeInfoModal()" class="px-4 py-2 bg-slate-800 hover:bg-slate-900 text-white font-medium rounded-lg text-xs transition-colors">
                    เข้าใจแล้ว
                </button>
            </div>
        </div>
    </div>

    <!-- Modal: Add / Edit Operator -->
    <div id="operatorModal" class="fixed inset-0 bg-slate-900/40 backdrop-blur-xs z-50 flex items-center justify-center p-4 hidden opacity-0 transition-opacity duration-200">
        <div class="bg-white rounded-2xl max-w-lg w-full p-6 shadow-2xl transform scale-95 transition-transform duration-200">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100">
                <h3 id="modalTitle" class="text-base font-bold text-slate-900">เพิ่มผู้ปฏิบัติการ EMS</h3>
                <button onclick="closeAddModal()" class="text-slate-400 hover:text-slate-600">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>
            <form id="operatorForm" onsubmit="handleFormSubmit(event)" class="py-4 space-y-4">
                <input type="hidden" id="editId">
                <div>
                    <label class="block text-xs font-semibold text-slate-700 mb-1">ชื่อ - นามสกุล <span class="text-rose-500">*</span></label>
                    <input type="text" id="inputName" required placeholder="ตัวอย่าง: นางสาวซูนีดา มามะ" class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-lg text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">ระดับปฏิบัติการ <span class="text-rose-500">*</span></label>
                        <select id="inputRole" required class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-lg text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500">
                            <option value="ALS">ALS</option>
                            <option value="EMR">EMR</option>
                            <option value="Driver">Driver</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">เลข สพฉ.</label>
                        <input type="text" id="inputCode" placeholder="เช่น 5411227096" class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-lg text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-700 mb-1">วันหมดอายุ (วว/ดด/ปป)</label>
                    <input type="text" id="inputExpiry" placeholder="เช่น 31/07/74 หรือเว้นว่างถ้าไม่มี" class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-lg text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-teal-500/20 focus:border-teal-500">
                    <p class="text-[11px] text-slate-400 mt-1">ใส่วันหมดอายุในรูปแบบ เช่น 20/03/74 (พ.ศ. 2574)</p>
                </div>
                <div class="flex items-center gap-2 pt-2">
                    <input type="checkbox" id="inputAcknowledged" checked class="rounded border-slate-300 text-teal-600 focus:ring-teal-500">
                    <label for="inputAcknowledged" class="text-xs text-slate-700">รับทราบ Scope การปฏิบัติงานแล้ว (1 ต.ค. 2568)</label>
                </div>

                <div class="pt-4 border-t border-slate-100 flex items-center justify-end gap-2">
                    <button type="button" onclick="closeAddModal()" class="px-4 py-2 text-xs font-medium text-slate-600 hover:bg-slate-100 rounded-lg transition-colors">
                        ยกเลิก
                    </button>
                    <button type="submit" class="px-4 py-2 text-xs font-semibold text-white bg-teal-600 hover:bg-teal-700 rounded-lg shadow-sm transition-colors">
                        บันทึกข้อมูล
                    </button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Telegram Config
        const TELEGRAM_CONFIG = {
            botToken: '8767296623:AAGRsnjD41DKw_9fLNrH3vQNRlxihEhaDw0',
            groupId: '-5593653503'
        };

        // Date Parsing & Expiry Utilities for Thai BE Dates (DD/MM/YY)
        function parseExpiryDate(expStr) {
            if (!expStr || expStr === '-') return null;
            const parts = expStr.trim().split('/');
            if (parts.length !== 3) return null;
            
            const day = parseInt(parts[0], 10);
            const month = parseInt(parts[1], 10) - 1; // 0-indexed
            let year = parseInt(parts[2], 10);

            // Handle 2-digit Thai Buddhist Year (e.g. 70 -> 2570 BE)
            if (year < 100) {
                year = 2500 + year;
            }
            // Convert BE to AD (e.g. 2570 BE -> 2027 AD)
            if (year > 2400) {
                year = year - 543;
            }

            return new Date(year, month, day);
        }

        function getDaysUntilExpiry(expStr) {
            const expDate = parseExpiryDate(expStr);
            if (!expDate) return null;
            
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            expDate.setHours(0, 0, 0, 0);
            
            const diffTime = expDate - today;
            return Math.ceil(diffTime / (1000 * 60 * 60 * 24));
        }

        function getExpiryAlertCategory(expStr) {
            const days = getDaysUntilExpiry(expStr);
            if (days === null) return null;

            if (days <= 0) return { key: 'EXPIRED', label: 'หมดอายุแล้ว', days, badgeClass: 'bg-rose-100 text-rose-800 border-rose-300', icon: 'fa-triangle-exclamation text-rose-600' };
            if (days <= 7) return { key: '1W', label: 'เหลือน้อยกว่า 1 สัปดาห์', days, badgeClass: 'bg-rose-50 text-rose-700 border-rose-200', icon: 'fa-circle-exclamation text-rose-500' };
            if (days <= 30) return { key: '1M', label: 'เหลือน้อยกว่า 1 เดือน', days, badgeClass: 'bg-amber-50 text-amber-700 border-amber-200', icon: 'fa-clock text-amber-500' };
            if (days <= 180) return { key: '6M', label: 'เหลือน้อยกว่า 6 เดือน', days, badgeClass: 'bg-blue-50 text-blue-700 border-blue-200', icon: 'fa-calendar-day text-blue-500' };

            return { key: 'OK', label: 'ปกติ', days, badgeClass: 'bg-slate-100 text-slate-600 border-slate-200', icon: 'fa-check text-emerald-500' };
        }

        function getCategorizedPersonnel() {
            const result = {
                expired: [],
                week1: [],
                month1: [],
                month6: [],
                allAlerts: []
            };

            operators.forEach(op => {
                const cat = getExpiryAlertCategory(op.expiry);
                if (!cat) return;

                if (cat.key === 'EXPIRED') {
                    result.expired.push({ ...op, days: cat.days, cat });
                    result.allAlerts.push({ ...op, days: cat.days, cat });
                } else if (cat.key === '1W') {
                    result.week1.push({ ...op, days: cat.days, cat });
                    result.allAlerts.push({ ...op, days: cat.days, cat });
                } else if (cat.key === '1M') {
                    result.month1.push({ ...op, days: cat.days, cat });
                    result.allAlerts.push({ ...op, days: cat.days, cat });
                } else if (cat.key === '6M') {
                    result.month6.push({ ...op, days: cat.days, cat });
                    result.allAlerts.push({ ...op, days: cat.days, cat });
                }
            });

            return result;
        }

        // Full Dataset extracted from official PDF
        const initialOperatorsData = [
            { id: 1, name: "นส.อามีเนาะห์ ดามูนะ", role: "ALS", code: "ฉพ1761.", expiry: "31/03/71", acknowledged: true },
            { id: 2, name: "นางนันทวดี จอนเจิม", role: "ALS", code: "4411165068", expiry: "31/03/74", acknowledged: true },
            { id: 3, name: "นางกัรมาน ดามะเลาะ", role: "ALS", code: "5111204387", expiry: "23/03/71", acknowledged: true },
            { id: 4, name: "นางสาวตรีนุช สกุลแก้ว", role: "ALS", code: "5111204388", expiry: "23/03/71", acknowledged: true },
            { id: 5, name: "นางสาวซูไลลัน เซ็ง", role: "ALS", code: "5111205013", expiry: "23/03/71", acknowledged: true },
            { id: 6, name: "นางซาวียะห์ บือราแง", role: "ALS", code: "5411222069", expiry: "20/03/74", acknowledged: true },
            { id: 7, name: "นายอัลอามีน ยีเอ็ง", role: "ALS", code: "5411226924", expiry: "31/07/74", acknowledged: true },
            { id: 8, name: "นางสาวซูนีดา มามะ", role: "ALS", code: "5411227096", expiry: "31/07/74", acknowledged: true },
            { id: 9, name: "นางนายีเราะ สาและ", role: "ALS", code: "5411227205", expiry: "31/07/74", acknowledged: true },
            { id: 10, name: "นางสาวคอลียะห์ เจ๊ะสะนิ", role: "ALS", code: "5411226646", expiry: "20/03/74", acknowledged: true },
            { id: 11, name: "นายฮาซันอวัณบุตร", role: "ALS", code: "5511232413", expiry: "29/04/70", acknowledged: true },
            { id: 12, name: "นางสาวรุสมาวาตี มูดอ", role: "ALS", code: "4911198555", expiry: "26/11/74", acknowledged: true },
            { id: 13, name: "นางรุสนานี มอลอ", role: "ALS", code: "4911197151", expiry: "22/07/74", acknowledged: true },
            { id: 14, name: "นางสาวนูรีดา สะแลแม", role: "ALS", code: "5011201377", expiry: "22/07/74", acknowledged: true },
            { id: 15, name: "นางสาวลาตีป๊ะ สูหลง", role: "ALS", code: "5411225760", expiry: "20/03/74", acknowledged: true },
            { id: 16, name: "นางสาวอาฟีณีย์ ดารามะ", role: "ALS", code: "-", expiry: "23/06/72", acknowledged: true },
            { id: 17, name: "นางสาวรอฮานิง เจ๊ะหะมะ", role: "ALS", code: "5411227143", expiry: "03/07/74", acknowledged: true },
            { id: 18, name: "นายซัมรี หะยีกือเตะ", role: "ALS", code: "5411225325", expiry: "20/03/74", acknowledged: true },
            { id: 19, name: "นางสาวพีดาวาตี สะเตง", role: "ALS", code: "5411227219", expiry: "31/07/74", acknowledged: true },
            { id: 20, name: "นางสาวนูรอาซีกีม สาเมาะ", role: "ALS", code: "5511238960", expiry: "25/11/70", acknowledged: true },
            { id: 21, name: "นางสาวไซนูรี มะสาแม", role: "ALS", code: "5411221887", expiry: "20/03/74", acknowledged: true },
            { id: 22, name: "นางสาวนาชูวา มะเย็ง", role: "ALS", code: "-", expiry: "19/07/73", acknowledged: true },
            { id: 23, name: "นางซารีนา บินอารง", role: "ALS", code: "6311170948", expiry: "18/07/73", acknowledged: true },
            { id: 24, name: "นางสาววัลนิดา เจ๊ะปูเต๊ะ", role: "ALS", code: "5111208413", expiry: "23/11/71", acknowledged: true },
            { id: 25, name: "นางสาวนาฏยา พรมแก้ว", role: "ALS", code: "5111207185", expiry: "27/07/71", acknowledged: true },
            { id: 26, name: "นางยามีละ เจ๊ะซอ", role: "ALS", code: "5411222181", expiry: "20/03/74", acknowledged: true },
            { id: 27, name: "นางสาวรอฮายะห์ หามะ", role: "ALS", code: "5411222087", expiry: "20/03/74", acknowledged: true },
            { id: 28, name: "นางสาวนูร์รุสดา หามะ", role: "ALS", code: "5411228027", expiry: "31/07/74", acknowledged: true },
            { id: 29, name: "นางสาวโนร์อากีน แวยะโก๊ะ", role: "ALS", code: "5511234370", expiry: "25/05/70", acknowledged: true },
            { id: 30, name: "นางสาวนุรไอนิง หามะ", role: "ALS", code: "5411226655", expiry: "20/03/74", acknowledged: true },
            { id: 31, name: "นางสาวซาฟียะห์ สามะ", role: "ALS", code: "5411230927", expiry: "25/12/74", acknowledged: true },
            { id: 32, name: "นางสีตีฮายา วาหลง", role: "ALS", code: "4611094421", expiry: "23/03/71", acknowledged: true },
            { id: 33, name: "นายนัสรี เจ๊ะหามะ", role: "ALS", code: "ฉพ.1679", expiry: "-", acknowledged: true },
            { id: 34, name: "นายยุชรี แมะ", role: "ALS", code: "จฉพ.1295", expiry: "04/04/70", acknowledged: true },
            { id: 35, name: "นางสาวกุสุมา แวอุเซ็ง", role: "ALS", code: "4811107105", expiry: "31/07/73", acknowledged: true },
            { id: 36, name: "นางสาวนายีฮะ หะยีนุ", role: "ALS", code: "5411224083", expiry: "20/03/74", acknowledged: true },
            { id: 37, name: "นางสาวซารีฟาร์ อับดุลซามะ", role: "ALS", code: "5311218226", expiry: "21/03/73", acknowledged: true },
            { id: 38, name: "นายรุสดี กุเวกามา", role: "EMR", code: "-", expiry: "-", acknowledged: true },
            { id: 39, name: "นายมานะ ชินวงศ์", role: "Driver", code: "DRV-0001", expiry: "-", acknowledged: true },
            { id: 40, name: "นายสับรี หะยีบีดิง", role: "Driver", code: "DRV-0002", expiry: "-", acknowledged: true },
            { id: 41, name: "นายอาหะมะ บือราเฮง", role: "Driver", code: "DRV-0003", expiry: "-", acknowledged: true },
            { id: 42, name: "นายประหยัด จุ่งสกุล", role: "Driver", code: "DRV-0004", expiry: "-", acknowledged: true },
            { id: 43, name: "นายมูสำหมัดยูโต๊ะ เจ๊ะซอ", role: "Driver", code: "DRV-0005", expiry: "-", acknowledged: true }
        ];

        // App State
        let operators = JSON.parse(localStorage.getItem('ems_operators_2568')) || initialOperatorsData;
        let selectedRole = 'ALL';
        let currentView = 'table';
        let sortField = null;
        let sortDirection = 'asc';

        function renderApp() {
            updateKPIs();
            const filteredData = getFilteredData();
            
            if (currentView === 'table') {
                renderTable(filteredData);
            } else {
                renderGrid(filteredData);
            }

            // Handle empty state
            const emptyState = document.getElementById('emptyState');
            if (filteredData.length === 0) {
                emptyState.classList.remove('hidden');
            } else {
                emptyState.classList.add('hidden');
            }
        }

        function updateKPIs() {
            document.getElementById('statTotal').innerText = operators.length;
            document.getElementById('statALS').innerText = operators.filter(o => o.role === 'ALS').length;
            document.getElementById('statEMR').innerText = operators.filter(o => o.role === 'EMR').length;
            document.getElementById('statDriver').innerText = operators.filter(o => o.role === 'Driver').length;

            const cats = getCategorizedPersonnel();
            const alertTotal = cats.allAlerts.length;

            document.getElementById('statExp70').innerText = alertTotal;

            // Header Telegram Badge
            const tgBadge = document.getElementById('telegramBadge');
            if (alertTotal > 0) {
                tgBadge.innerText = alertTotal;
                tgBadge.classList.remove('hidden');
            } else {
                tgBadge.classList.add('hidden');
            }

            // Update chip counts
            document.getElementById('countRoleALL').innerText = operators.length;
            document.getElementById('countRoleALS').innerText = operators.filter(o => o.role === 'ALS').length;
            document.getElementById('countRoleEMR').innerText = operators.filter(o => o.role === 'EMR').length;
            document.getElementById('countRoleDriver').innerText = operators.filter(o => o.role === 'Driver').length;
        }

        function getFilteredData() {
            const query = document.getElementById('searchInput').value.trim().toLowerCase();
            const yearFilter = document.getElementById('yearFilter').value;

            // Toggle clear search button
            const clearBtn = document.getElementById('clearSearchBtn');
            if (query) {
                clearBtn.classList.remove('hidden');
            } else {
                clearBtn.classList.add('hidden');
            }

            let result = operators.filter(op => {
                // Role Filter
                if (selectedRole !== 'ALL' && op.role !== selectedRole) return false;

                // Year Expiration Filter
                if (yearFilter !== 'ALL') {
                    if (yearFilter === 'NONE') {
                        if (op.expiry && op.expiry !== '-') return false;
                    } else {
                        const targetShortYear = yearFilter.substring(2); // '2570' -> '70'
                        if (!op.expiry || !op.expiry.endsWith(`/${targetShortYear}`)) return false;
                    }
                }

                // Search Query Filter
                if (query) {
                    const matchName = op.name.toLowerCase().includes(query);
                    const matchCode = (op.code || '').toLowerCase().includes(query);
                    const matchRole = op.role.toLowerCase().includes(query);
                    const matchExpiry = (op.expiry || '').toLowerCase().includes(query);
                    return matchName || matchCode || matchRole || matchExpiry;
                }

                return true;
            });

            // Sorting logic
            if (sortField) {
                result.sort((a, b) => {
                    let valA = a[sortField] || '';
                    let valB = b[sortField] || '';

                    if (sortField === 'expiry') {
                        valA = parseYearFromExpiry(valA);
                        valB = parseYearFromExpiry(valB);
                    }

                    if (valA < valB) return sortDirection === 'asc' ? -1 : 1;
                    if (valA > valB) return sortDirection === 'asc' ? 1 : -1;
                    return 0;
                });
            }

            return result;
        }

        function parseYearFromExpiry(expStr) {
            if (!expStr || expStr === '-') return '9999';
            const parts = expStr.split('/');
            if (parts.length === 3) {
                return parts[2] + parts[1] + parts[0]; // YYMMDD sort key
            }
            return expStr;
        }

        function renderTable(data) {
            const tbody = document.getElementById('tableBody');
            tbody.innerHTML = '';

            data.forEach((item, index) => {
                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-50/80 transition-colors";

                // Role badge color
                let roleBadgeClass = "bg-slate-100 text-slate-700 border-slate-200";
                if (item.role === 'ALS') roleBadgeClass = "bg-teal-50 text-teal-700 border-teal-200/80 font-semibold";
                else if (item.role === 'EMR') roleBadgeClass = "bg-sky-50 text-sky-700 border-sky-200/80 font-semibold";
                else if (item.role === 'Driver') roleBadgeClass = "bg-indigo-50 text-indigo-700 border-indigo-200/80 font-semibold";

                // Expiry status badge
                let expiryBadge = `<span class="text-slate-400 font-mono text-xs">-</span>`;
                if (item.expiry && item.expiry !== '-') {
                    const cat = getExpiryAlertCategory(item.expiry);
                    if (cat && cat.key !== 'OK') {
                        const daysText = cat.days <= 0 ? 'หมดอายุแล้ว' : `เหลือ ${cat.days} วัน`;
                        expiryBadge = `<span class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-md text-xs font-semibold border ${cat.badgeClass}">
                            <i class="fa-solid ${cat.icon} text-[10px]"></i> ${item.expiry} (${daysText})
                        </span>`;
                    } else {
                        const yearMatch = item.expiry.split('/')[2];
                        expiryBadge = `<span class="inline-flex items-center gap-1 px-2.5 py-1 rounded-md text-xs font-mono bg-slate-100 text-slate-700 border border-slate-200">
                            ${item.expiry} (25${yearMatch})
                        </span>`;
                    }
                }

                tr.innerHTML = `
                    <td class="py-3 px-4 text-center font-mono text-xs text-slate-400">${index + 1}</td>
                    <td class="py-3 px-4">
                        <div class="font-semibold text-slate-800">${item.name}</div>
                    </td>
                    <td class="py-3 px-4">
                        <span class="inline-block px-2.5 py-0.5 rounded-full text-xs border ${roleBadgeClass}">${item.role}</span>
                    </td>
                    <td class="py-3 px-4 font-mono text-xs text-slate-600">
                        ${item.code && item.code !== '-' ? `<span class="bg-slate-100 px-2 py-0.5 rounded border border-slate-200">${item.code}</span>` : '<span class="text-slate-300">-</span>'}
                    </td>
                    <td class="py-3 px-4">${expiryBadge}</td>
                    <td class="py-3 px-4 text-center">
                        ${item.acknowledged 
                            ? `<span class="inline-flex items-center gap-1 text-xs text-emerald-600 font-medium bg-emerald-50 px-2 py-0.5 rounded-md border border-emerald-100"><i class="fa-solid fa-check text-[10px]"></i> 1 ต.ค. 68</span>`
                            : `<span class="text-xs text-slate-400">-</span>`
                        }
                    </td>
                    <td class="py-3 px-4 text-right space-x-1">
                        <button onclick="editOperator(${item.id})" class="p-1.5 text-slate-400 hover:text-teal-600 rounded-md hover:bg-teal-50 transition-colors" title="แก้ไข">
                            <i class="fa-solid fa-pen-to-square"></i>
                        </button>
                        <button onclick="deleteOperator(${item.id})" class="p-1.5 text-slate-400 hover:text-rose-600 rounded-md hover:bg-rose-50 transition-colors" title="ลบ">
                            <i class="fa-solid fa-trash-can"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        function renderGrid(data) {
            const gridView = document.getElementById('gridView');
            gridView.innerHTML = '';

            data.forEach((item, index) => {
                const cat = getExpiryAlertCategory(item.expiry);
                const isUrgent = cat && cat.key !== 'OK';
                
                let roleColor = "teal";
                if (item.role === "EMR") roleColor = "sky";
                if (item.role === "Driver") roleColor = "indigo";

                const card = document.createElement('div');
                card.className = `bg-white rounded-xl border p-4 shadow-xs relative flex flex-col justify-between transition-all hover:shadow-md ${isUrgent ? 'border-amber-300 bg-amber-50/20' : 'border-slate-200/80'}`;

                let expiryText = item.expiry || '-';
                if (isUrgent) {
                    const daysText = cat.days <= 0 ? 'หมดอายุแล้ว' : `เหลือ ${cat.days} วัน`;
                    expiryText = `${item.expiry} (${daysText})`;
                }

                card.innerHTML = `
                    <div>
                        <div class="flex items-start justify-between gap-2 mb-2">
                            <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-${roleColor}-50 text-${roleColor}-700 border border-${roleColor}-200">
                                ${item.role}
                            </span>
                            <span class="text-[11px] font-mono text-slate-400">#${index + 1}</span>
                        </div>
                        <h4 class="font-bold text-slate-800 text-base mb-2">${item.name}</h4>
                        
                        <div class="space-y-1.5 text-xs text-slate-600 mb-4">
                            <div class="flex items-center justify-between">
                                <span class="text-slate-400">เลข สพฉ.:</span>
                                <span class="font-mono ${item.code && item.code !== '-' ? 'text-slate-700 font-medium' : 'text-slate-300'}">${item.code || '-'}</span>
                            </div>
                            <div class="flex items-center justify-between">
                                <span class="text-slate-400">วันหมดอายุ:</span>
                                <span class="font-mono font-medium ${isUrgent ? 'text-amber-800 bg-amber-100/70 px-1.5 py-0.5 rounded' : 'text-slate-700'}">
                                    ${expiryText}
                                </span>
                            </div>
                            <div class="flex items-center justify-between">
                                <span class="text-slate-400">รับทราบ Scope:</span>
                                <span class="font-medium text-emerald-600 flex items-center gap-1">
                                    <i class="fa-solid fa-check text-[10px]"></i> 1 ต.ค. 68
                                </span>
                            </div>
                        </div>
                    </div>

                    <div class="pt-3 border-t border-slate-100 flex items-center justify-end gap-1">
                        <button onclick="editOperator(${item.id})" class="px-2.5 py-1 text-xs text-slate-600 hover:text-teal-600 bg-slate-50 hover:bg-teal-50 rounded-md transition-colors flex items-center gap-1">
                            <i class="fa-solid fa-pen-to-square"></i> แก้ไข
                        </button>
                        <button onclick="deleteOperator(${item.id})" class="px-2.5 py-1 text-xs text-slate-600 hover:text-rose-600 bg-slate-50 hover:bg-rose-50 rounded-md transition-colors flex items-center gap-1">
                            <i class="fa-solid fa-trash-can"></i> ลบ
                        </button>
                    </div>
                `;
                gridView.appendChild(card);
            });
        }

        function setViewMode(mode) {
            currentView = mode;
            const btnTable = document.getElementById('btnViewTable');
            const btnGrid = document.getElementById('btnViewGrid');
            const tableView = document.getElementById('tableView');
            const gridView = document.getElementById('gridView');

            if (mode === 'table') {
                btnTable.className = "px-3 py-1.5 text-xs font-semibold rounded-md bg-white text-slate-800 shadow-xs transition-all flex items-center gap-1.5";
                btnGrid.className = "px-3 py-1.5 text-xs font-semibold rounded-md text-slate-500 hover:text-slate-800 transition-all flex items-center gap-1.5";
                tableView.classList.remove('hidden');
                gridView.classList.add('hidden');
            } else {
                btnGrid.className = "px-3 py-1.5 text-xs font-semibold rounded-md bg-white text-slate-800 shadow-xs transition-all flex items-center gap-1.5";
                btnTable.className = "px-3 py-1.5 text-xs font-semibold rounded-md text-slate-500 hover:text-slate-800 transition-all flex items-center gap-1.5";
                gridView.classList.remove('hidden');
                tableView.classList.add('hidden');
            }
            renderApp();
        }

        function setRoleFilter(role) {
            selectedRole = role;
            ['ALL', 'ALS', 'EMR', 'Driver'].forEach(r => {
                const btn = document.getElementById(`chipRole${r}`);
                if (btn) {
                    if (r === role) {
                        btn.className = "px-3 py-1.5 text-xs font-semibold rounded-lg bg-teal-600 text-white shadow-xs transition-all flex items-center gap-1.5";
                    } else {
                        btn.className = "px-3 py-1.5 text-xs font-medium rounded-lg bg-white text-slate-600 hover:bg-slate-100 border border-slate-200 transition-all flex items-center gap-1.5";
                    }
                }
            });
            renderApp();
        }

        function clearSearch() {
            document.getElementById('searchInput').value = '';
            renderApp();
        }

        function sortBy(field) {
            if (sortField === field) {
                sortDirection = sortDirection === 'asc' ? 'desc' : 'asc';
            } else {
                sortField = field;
                sortDirection = 'asc';
            }
            renderApp();
        }

        function openTelegramModal() {
            const cats = getCategorizedPersonnel();
            
            document.getElementById('tgCount1w').innerText = cats.expired.length + cats.week1.length;
            document.getElementById('tgCount1m').innerText = cats.month1.length;
            document.getElementById('tgCount6m').innerText = cats.month6.length;
            document.getElementById('tgTotalAlerts').innerText = `รวม ${cats.allAlerts.length} คน`;

            const previewContainer = document.getElementById('tgPreviewList');
            previewContainer.innerHTML = '';

            if (cats.allAlerts.length === 0) {
                previewContainer.innerHTML = `<div class="p-4 text-center text-xs text-slate-400 bg-slate-50 rounded-lg">ไม่มีบุคลากรที่อยู่ในเกณฑ์หมดอายุล่วงหน้า (6 เดือน)</div>`;
            } else {
                cats.allAlerts.forEach(op => {
                    const div = document.createElement('div');
                    div.className = "flex items-center justify-between p-2.5 bg-slate-50 hover:bg-slate-100 rounded-lg text-xs transition-colors border border-slate-100";
                    const daysBadge = op.days <= 0 
                        ? `<span class="text-rose-600 font-bold">หมดอายุแล้ว</span>` 
                        : `<span class="text-slate-600 font-mono">เหลือ ${op.days} วัน</span>`;
                    
                    div.innerHTML = `
                        <div class="flex items-center gap-2">
                            <span class="px-2 py-0.5 text-[10px] rounded font-bold ${op.cat.badgeClass}">${op.role}</span>
                            <span class="font-medium text-slate-800">${op.name}</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <span class="text-slate-500 font-mono">${op.expiry}</span>
                            ${daysBadge}
                        </div>
                    `;
                    previewContainer.appendChild(div);
                });
            }

            // Hide log box initially
            document.getElementById('tgLogBox').className = "hidden p-3 rounded-lg text-xs font-mono";

            const modal = document.getElementById('telegramModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
            }, 10);
        }

        function closeTelegramModal() {
            const modal = document.getElementById('telegramModal');
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            setTimeout(() => modal.classList.add('hidden'), 200);
        }

        async function sendTelegramAlerts() {
            const btn = document.getElementById('btnSendTelegram');
            const logBox = document.getElementById('tgLogBox');
            const cats = getCategorizedPersonnel();

            btn.disabled = true;
            btn.innerHTML = `<i class="fa-solid fa-spinner fa-spin"></i> กำลังส่ง...`;
            
            logBox.className = "p-3 rounded-lg text-xs font-mono bg-slate-100 text-slate-700 block";
            logBox.innerText = "กำลังจัดเตรียมข้อมูลและส่งไปยัง Telegram...";

            const todayStr = new Date().toLocaleDateString('th-TH', { year: 'numeric', month: 'long', day: 'numeric' });

            let msg = `🚨 <b>รายงานการแจ้งเตือนใบอนุญาตผู้ปฏิบัติการ EMS หมดอายุ</b>\n`;
            msg += `📅 <b>ประจำวันที่:</b> ${todayStr}\n`;
            msg += `🏢 <b>หน่วยงาน:</b> งานการพยาบาลผู้ป่วยอุบัติเหตุฉุกเฉินและนิติเวช\n`;
            msg += `------------------------------------\n\n`;

            if (cats.allAlerts.length === 0) {
                msg += `✅ <b>สถานะ:</b> ไม่พบผู้ปฏิบัติการที่มีใบอนุญาตหมดอายุในระยะ 6 เดือนครับ\n`;
            } else {
                // Category 1: Expired & 1 Week
                const UrgentGroup = [...cats.expired, ...cats.week1];
                if (UrgentGroup.length > 0) {
                    msg += `🔴 <b>กลุ่มด่วนที่สุด (หมดอายุแล้ว / เหลือน้อยกว่า 1 สัปดาห์):</b>\n`;
                    UrgentGroup.forEach(op => {
                        const dayText = op.days <= 0 ? '❌ หมดอายุแล้ว' : `⚠️ เหลือ ${op.days} วัน`;
                        msg += `• <b>${op.name}</b> (${op.role}) | วันหมดอายุ: ${op.expiry} (${dayText})\n`;
                    });
                    msg += `\n`;
                }

                // Category 2: 1 Month
                if (cats.month1.length > 0) {
                    msg += `🟧 <b>กลุ่มเตือนภัย 1 เดือน (เหลือน้อยกว่า 30 วัน):</b>\n`;
                    cats.month1.forEach(op => {
                        msg += `• <b>${op.name}</b> (${op.role}) | วันหมดอายุ: ${op.expiry} (เหลือ ${op.days} วัน)\n`;
                    });
                    msg += `\n`;
                }

                // Category 3: 6 Months
                if (cats.month6.length > 0) {
                    msg += `🟦 <b>กลุ่มเฝ้าระวัง 6 เดือน (เหลือน้อยกว่า 180 วัน):</b>\n`;
                    cats.month6.forEach(op => {
                        msg += `• <b>${op.name}</b> (${op.role}) | วันหมดอายุ: ${op.expiry} (เหลือ ${op.days} วัน)\n`;
                    });
                    msg += `\n`;
                }

                msg += `ℹ️ <i>โปรดแจ้งผู้ปฏิบัติการเตรียมเอกสารสำหรับต่ออายุใบอนุญาต สพฉ.</i>\n`;
            }

            try {
                const res = await fetch(`https://api.telegram.org/bot${TELEGRAM_CONFIG.botToken}/sendMessage`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        chat_id: TELEGRAM_CONFIG.groupId,
                        text: msg,
                        parse_mode: 'HTML'
                    })
                });

                const data = await res.json();

                if (data.ok) {
                    logBox.className = "p-3 rounded-lg text-xs font-mono bg-emerald-50 text-emerald-800 border border-emerald-200 block";
                    logBox.innerHTML = `<i class="fa-solid fa-circle-check text-emerald-600 mr-1"></i> ส่งการแจ้งเตือนเข้า Telegram เรียบร้อยแล้ว! (Message ID: ${data.result.message_id})`;
                } else {
                    throw new Error(data.description || 'เกิดข้อผิดพลาดในการส่งข้อความ');
                }
            } catch (err) {
                logBox.className = "p-3 rounded-lg text-xs font-mono bg-rose-50 text-rose-800 border border-rose-200 block";
                logBox.innerHTML = `<i class="fa-solid fa-circle-xmark text-rose-600 mr-1"></i> ล้มเหลว: ${err.message}`;
            } finally {
                btn.disabled = false;
                btn.innerHTML = `<i class="fa-solid fa-paper-plane"></i> <span>ส่งแจ้งเตือนเข้า Telegram</span>`;
            }
        }

        async function testTelegramConnection() {
            const logBox = document.getElementById('tgLogBox');
            logBox.className = "p-3 rounded-lg text-xs font-mono bg-slate-100 text-slate-700 block";
            logBox.innerText = "กำลังทดสอบเชื่อมต่อกับ Telegram Bot API...";

            try {
                const res = await fetch(`https://api.telegram.org/bot${TELEGRAM_CONFIG.botToken}/getMe`);
                const data = await res.json();

                if (data.ok) {
                    logBox.className = "p-3 rounded-lg text-xs font-mono bg-sky-50 text-sky-800 border border-sky-200 block";
                    logBox.innerHTML = `<i class="fa-solid fa-check text-sky-600 mr-1"></i> เชื่อมต่อสำเร็จ! Bot Name: <strong>@${data.result.username}</strong> (${data.result.first_name})`;
                } else {
                    throw new Error(data.description || 'Token ไม่ถูกต้อง');
                }
            } catch (err) {
                logBox.className = "p-3 rounded-lg text-xs font-mono bg-rose-50 text-rose-800 border border-rose-200 block";
                logBox.innerHTML = `<i class="fa-solid fa-circle-xmark text-rose-600 mr-1"></i> เชื่อมต่อล้มเหลว: ${err.message}`;
            }
        }

        function openInfoModal() {
            const modal = document.getElementById('infoModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
            }, 10);
        }

        function closeInfoModal() {
            const modal = document.getElementById('infoModal');
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            setTimeout(() => modal.classList.add('hidden'), 200);
        }

        function openAddModal() {
            document.getElementById('editId').value = '';
            document.getElementById('modalTitle').innerText = 'เพิ่มผู้ปฏิบัติการ EMS';
            document.getElementById('operatorForm').reset();
            document.getElementById('inputAcknowledged').checked = true;

            const modal = document.getElementById('operatorModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
            }, 10);
        }

        function closeAddModal() {
            const modal = document.getElementById('operatorModal');
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            setTimeout(() => modal.classList.add('hidden'), 200);
        }

        function editOperator(id) {
            const op = operators.find(o => o.id === id);
            if (!op) return;

            document.getElementById('editId').value = op.id;
            document.getElementById('modalTitle').innerText = 'แก้ไขข้อมูลผู้ปฏิบัติการ';
            document.getElementById('inputName').value = op.name;
            document.getElementById('inputRole').value = op.role;
            document.getElementById('inputCode').value = op.code === '-' ? '' : op.code;
            document.getElementById('inputExpiry').value = op.expiry === '-' ? '' : op.expiry;
            document.getElementById('inputAcknowledged').checked = !!op.acknowledged;

            const modal = document.getElementById('operatorModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
            }, 10);
        }

        function handleFormSubmit(e) {
            e.preventDefault();
            const editId = document.getElementById('editId').value;
            const name = document.getElementById('inputName').value.trim();
            const role = document.getElementById('inputRole').value;
            const code = document.getElementById('inputCode').value.trim() || '-';
            const expiry = document.getElementById('inputExpiry').value.trim() || '-';
            const acknowledged = document.getElementById('inputAcknowledged').checked;

            if (editId) {
                // Edit existing
                const index = operators.findIndex(o => o.id == editId);
                if (index !== -1) {
                    operators[index] = { ...operators[index], name, role, code, expiry, acknowledged };
                }
            } else {
                // Add new
                const newId = operators.length > 0 ? Math.max(...operators.map(o => o.id)) + 1 : 1;
                operators.push({ id: newId, name, role, code, expiry, acknowledged });
            }

            saveOperators();
            closeAddModal();
            renderApp();
        }

        function deleteOperator(id) {
            const op = operators.find(o => o.id === id);
            if (!op) return;

            if (confirm(`คุณต้องการลบรายชื่อ "${op.name}" ออกจากระบบใช่หรือไม่?`)) {
                operators = operators.filter(o => o.id !== id);
                saveOperators();
                renderApp();
            }
        }

        function saveOperators() {
            localStorage.setItem('ems_operators_2568', JSON.stringify(operators));
        }

        function exportCSV() {
            const filtered = getFilteredData();
            let csvContent = "\uFEFFลำดับ,ชื่อ-นามสกุล,ระดับ,เลข สพฉ.,วันหมดอายุ,รับทราบ Scope\n";

            filtered.forEach((item, index) => {
                const ackText = item.acknowledged ? "รับทราบแล้ว (1 ต.ค. 2568)" : "ยังไม่รับทราบ";
                csvContent += `"${index + 1}","${item.name}","${item.role}","${item.code}","${item.expiry}","${ackText}"\n`;
            });

            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.setAttribute('href', url);
            link.setAttribute('download', `EMS_Registry_2568_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        // Initialize on DOM load
        window.onload = function() {
            renderApp();
        };
    </script>
</body>
</html>
