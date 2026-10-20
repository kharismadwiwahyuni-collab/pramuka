<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generator Modul Permainan & Latihan Pramuka Interaktif</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome CDN -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Cinzel:wght@700;900&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        scout: {
                            50: '#fcf8f2',
                            100: '#f5ea8d',
                            200: '#edd585',
                            500: '#8c531d',
                            700: '#5c2d10',
                            800: '#3e1e0b',
                            900: '#2a1306',
                            950: '#1a0b03'
                        },
                        forest: {
                            800: '#143823',
                            900: '#0d2818',
                            950: '#05140b'
                        },
                        campfire: {
                            400: '#fb923c',
                            500: '#f97316',
                            600: '#ea580c',
                            700: '#c2410c'
                        }
                    },
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                        heading: ['Cinzel', 'serif']
                    }
                }
            }
        }
    </script>

    <style>
        /* Wood & Campfire Gradient Backgrounds */
        .bg-camp-hero {
            background: linear-gradient(135deg, rgba(5, 20, 11, 0.95) 0%, rgba(30, 15, 6, 0.92) 50%, rgba(13, 40, 24, 0.95) 100%),
                        url('https://images.unsplash.com/photo-1508873696983-2df515122519?auto=format&fit=crop&w=1200&q=80') center/cover no-repeat;
        }

        .bg-paper-texture {
            background-color: #ffffff;
            background-image: radial-gradient(#e5e7eb 0.75px, transparent 0.75px);
            background-size: 16px 16px;
        }

        /* Official Print PDF Styling */
        @page {
            size: A4;
            margin: 16mm 15mm;
        }

        @media print {
            html,
            body {
                background: white !important;
                color: black !important;
                width: 100% !important;
                min-height: 0 !important;
                margin: 0 !important;
                font-family: Arial, sans-serif !important;
                font-size: 10pt !important;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
            body * {
                visibility: hidden !important;
            }
            .no-print {
                display: none !important;
            }
            #printArea {
                display: block !important;
                position: absolute;
                left: 0;
                top: 0;
                width: 100% !important;
                margin: 0;
                padding: 0 !important;
                box-shadow: none !important;
                border: none !important;
                background: white !important;
                color: #1c1917 !important;
                visibility: visible !important;
            }
            #printArea *,
            #printArea *::before,
            #printArea *::after {
                visibility: visible !important;
            }
            #printArea > div {
                width: 100% !important;
                max-width: none !important;
                margin: 0 !important;
                padding: 0 !important;
                border: 0 !important;
                border-radius: 0 !important;
                box-shadow: none !important;
                background: white !important;
            }
            #printArea h2,
            #printArea h3 {
                break-after: avoid;
                page-break-after: avoid;
            }
            #outGroupTitle,
            #outGroupSummary,
            #outPeralatan,
            #outStepsList,
            #outTips,
            #outSafety,
            #outCharacter,
            #outUnitsContainer,
            #printArea > div > div:first-child {
                break-inside: avoid;
                page-break-inside: avoid;
            }
            #outStepsList li,
            #outSafety li,
            #outCharacter li {
                break-inside: avoid;
                page-break-inside: avoid;
            }
            .page-break {
                page-break-before: always;
            }
            .print-border {
                border: 2px solid #1c1917 !important;
            }
            .print-badge {
                border: 1px solid #78716c !important;
                background-color: #f5f5f4 !important;
                color: #0c0a09 !important;
            }
        }

        [contenteditable="true"] {
            outline: 1px dashed #d97706;
            outline-offset: 2px;
            cursor: text;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #1c1917;
        }
        ::-webkit-scrollbar-thumb {
            background: #d97706;
            border-radius: 4px;
        }
    </style>
</head>
<body class="bg-stone-900 text-stone-100 font-sans min-h-screen flex flex-col selection:bg-amber-500 selection:text-stone-950">

    <!-- HEADER HERO BANNER -->
    <header class="bg-camp-hero text-amber-100 shadow-2xl border-b-4 border-amber-600 relative overflow-hidden no-print">
        <!-- Overlay Campfire Glow -->
        <div class="absolute -top-24 -left-24 w-72 h-72 bg-amber-600/20 rounded-full blur-3xl pointer-events-none"></div>
        <div class="absolute -bottom-20 right-10 w-80 h-80 bg-emerald-600/15 rounded-full blur-3xl pointer-events-none"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 py-6 relative z-10 flex flex-col md:flex-row items-center justify-between gap-4">
            <div class="flex items-center space-x-4">
                <div class="bg-gradient-to-br from-amber-500 to-amber-700 text-stone-950 p-3.5 rounded-2xl shadow-lg shadow-amber-600/30 ring-2 ring-amber-400/50 flex items-center justify-center">
                    <i class="fa-solid fa-campground text-2xl"></i>
                </div>
                <div>
                    <div class="flex items-center gap-2">
                        <span class="text-[10px] font-bold tracking-widest uppercase bg-amber-500/20 text-amber-300 px-2.5 py-0.5 rounded-full border border-amber-500/30">
                            Edisi Pembina Pramuka Indonesia
                        </span>
                    </div>
                    <h1 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-white mt-0.5">
                        GENERATOR MODUL PERMAINAN PRAMUKA
                    </h1>
                    <p class="text-xs sm:text-sm text-stone-300 font-medium">
                        Sistem Pembuat Modul Latihan Interaktif, Otomatis & Standar Resmi Gudep
                    </p>
                </div>
            </div>

            <!-- Navigation Tabs -->
            <div class="flex items-center gap-2 bg-stone-950/80 p-1.5 rounded-xl border border-stone-800 shadow-inner">
                <button onclick="switchTab('generator')" id="tabGenBtn" class="px-5 py-2.5 rounded-lg font-bold text-xs sm:text-sm transition-all duration-200 bg-gradient-to-r from-amber-500 to-amber-600 text-stone-950 shadow-md flex items-center gap-2">
                    <i class="fa-solid fa-wand-magic-sparkles"></i>
                    <span>Generator Modul</span>
                </button>
                <button onclick="switchTab('katalog')" id="tabKatBtn" aria-hidden="true" tabindex="-1" style="display: none">
                    <span>Katalog (200 Game)</span>
                </button>
            </div>
        </div>
    </header>

    <!-- MAIN CONTAINER -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 py-8 flex-grow w-full">

        <!-- TAB 1: GENERATOR MODUL -->
        <div id="tabGenerator" class="grid grid-cols-1 lg:grid-cols-12 gap-8">

            <!-- FORM INPUT PEMBINA (LEFT SIDE) -->
            <div class="lg:col-span-5 no-print space-y-6">
                <div class="bg-stone-800/90 backdrop-blur-md rounded-2xl p-6 border border-stone-700/80 shadow-2xl relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-amber-500/5 rounded-bl-full pointer-events-none"></div>

                    <div class="flex items-center justify-between pb-4 mb-5 border-b border-stone-700">
                        <h2 class="text-base font-bold text-amber-400 flex items-center gap-2">
                            <i class="fa-solid fa-sliders text-amber-500"></i>
                            <span>PARAMETER MODUL LATIHAN</span>
                        </h2>
                        <span class="text-[10px] text-stone-400 font-mono">Langkah 1 dari 2</span>
                    </div>

                    <form id="gameForm" onsubmit="generateGame(event)" class="space-y-4">
                        
                        <!-- Gudep & Pangkalan -->
                        <div>
                            <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                🏛️ Gudep & Pangkalan Latihan
                            </label>
                            <input type="text" id="inputGudep" required value="Gugus Depan 01.001-01.002" placeholder="Contoh: Gugus Depan 01.001-01.002"
                                class="w-full px-3.5 py-2.5 bg-stone-900/90 border border-stone-700 rounded-xl text-xs sm:text-sm text-stone-100 placeholder-stone-500 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition">
                            <input type="text" id="inputPangkalan" required value="Pangkalan Latihan & Pembinaan Karakter Pramuka Interaktif" placeholder="Nama Sekolah / Pangkalan"
                                class="w-full px-3.5 py-2.5 mt-2 bg-stone-900/90 border border-stone-700 rounded-xl text-xs sm:text-sm text-stone-100 placeholder-stone-500 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition">
                        </div>

                        <!-- Tingkat Pramuka -->
                        <div>
                            <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                ⚜️ Golongan Tingkatan Pramuka
                            </label>
                            <div class="grid grid-cols-2 gap-2">
                                <label class="flex items-center p-2.5 bg-stone-900/70 border border-stone-700 rounded-xl cursor-pointer hover:border-amber-500/60 transition group">
                                    <input type="radio" name="tingkat" value="Siaga" onchange="updateGroupDefaults()" class="text-amber-500 focus:ring-amber-500">
                                    <div class="ml-2.5">
                                        <span class="block text-xs font-bold text-stone-200 group-hover:text-amber-400">🟢 SIAGA</span>
                                        <span class="text-[10px] text-stone-400">Usia 7-10 Thn</span>
                                    </div>
                                </label>
                                <label class="flex items-center p-2.5 bg-stone-900/70 border border-stone-700 rounded-xl cursor-pointer hover:border-amber-500/60 transition group">
                                    <input type="radio" name="tingkat" value="Penggalang" onchange="updateGroupDefaults()" class="text-amber-500 focus:ring-amber-500">
                                    <div class="ml-2.5">
                                        <span class="block text-xs font-bold text-stone-200 group-hover:text-amber-400">🔴 PENGGALANG</span>
                                        <span class="text-[10px] text-stone-400">Usia 11-15 Thn</span>
                                    </div>
                                </label>
                                <label class="flex items-center p-2.5 bg-stone-900/70 border border-stone-700 rounded-xl cursor-pointer hover:border-amber-500/60 transition group">
                                    <input type="radio" name="tingkat" value="Penegak" checked onchange="updateGroupDefaults()" class="text-amber-500 focus:ring-amber-500">
                                    <div class="ml-2.5">
                                        <span class="block text-xs font-bold text-stone-200 group-hover:text-amber-400">🟡 PENEGAK</span>
                                        <span class="text-[10px] text-stone-400">Usia 16-20 Thn</span>
                                    </div>
                                </label>
                                <label class="flex items-center p-2.5 bg-stone-900/70 border border-stone-700 rounded-xl cursor-pointer hover:border-amber-500/60 transition group">
                                    <input type="radio" name="tingkat" value="Pandega" onchange="updateGroupDefaults()" class="text-amber-500 focus:ring-amber-500">
                                    <div class="ml-2.5">
                                        <span class="block text-xs font-bold text-stone-200 group-hover:text-amber-400">🟤 PANDEGA</span>
                                        <span class="text-[10px] text-stone-400">Usia 21-25 Thn</span>
                                    </div>
                                </label>
                            </div>
                        </div>

                        <!-- Jumlah Peserta & Tanggal -->
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                    👥 Peserta (Orang)
                                </label>
                                <input type="number" id="inputPeserta" min="4" max="500" value="45" required
                                    class="w-full px-3.5 py-2.5 bg-stone-900/90 border border-stone-700 rounded-xl text-xs sm:text-sm text-stone-100 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none">
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                    📅 Tanggal Latihan
                                </label>
                                <input type="date" id="inputTanggal" required
                                    class="w-full px-3.5 py-2.5 bg-stone-900/90 border border-stone-700 rounded-xl text-xs sm:text-sm text-stone-100 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none">
                            </div>
                        </div>

                        <!-- Nama Pembina / Pelatih -->
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                    👤 Kakak Pembina
                                </label>
                                <input type="text" id="inputPembina" value="Kak Kakak Pembina" required
                                    class="w-full px-3 py-2 bg-stone-900/90 border border-stone-700 rounded-xl text-xs text-stone-100 focus:ring-2 focus:ring-amber-500 outline-none">
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-stone-300 uppercase tracking-wider mb-1.5">
                                    🎗️ Ketua Gudep
                                </label>
                                <input type="text" id="inputKetuaGudep" value="Kak Mabigus / Ka Gudep" required
                                    class="w-full px-3 py-2 bg-stone-900/90 border border-stone-700 rounded-xl text-xs text-stone-100 focus:ring-2 focus:ring-amber-500 outline-none">
                            </div>
                        </div>

                        <!-- Kategori Permainan -->
                        <div>
                            <div class="flex items-center justify-between mb-1.5">
                                <label class="text-xs font-bold text-stone-300 uppercase tracking-wider">
                                    🎲 Kategori Permainan
                                </label>
                                <span class="text-[10px] text-stone-500">Pilih satu kategori</span>
                            </div>

                            <div class="max-h-44 overflow-y-auto p-2.5 bg-stone-900/90 border border-stone-700 rounded-xl space-y-1.5 text-xs">
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="A" checked class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🎲 1. Ice Breaking & Pemanasan</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="B" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🤝 2. Kerja Sama Tim & Kekompakan</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="C" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🧭 3. Wide Game & Jelajah Alam</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="D" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">⚡ 4. Ketangkasan & Refleks Physical</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="E" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🌧️ 5. Dalam Ruangan (Indoor / Hujan)</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="F" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🔥 6. Api Unggun & Malam Keakraban</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="G" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🧠 7. Kepemimpinan & Strategi</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="H" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🎨 8. Kreatif & Pementasan Seni</span>
                                </label>
                                <label class="flex items-center space-x-2 cursor-pointer p-1 rounded hover:bg-stone-800 transition">
                                    <input type="radio" name="kategori" value="I" class="text-amber-500 focus:ring-amber-500">
                                    <span class="text-stone-200">🛠️ 9. Teknik Kepramukaan (Tekpram)</span>
                                </label>
                            </div>
                        </div>

                        <!-- Action Submit Button -->
                        <button id="generateButton" type="submit" class="w-full py-3.5 px-4 bg-gradient-to-r from-amber-500 via-amber-600 to-orange-600 hover:from-amber-400 hover:to-orange-500 text-stone-950 font-extrabold rounded-xl shadow-lg shadow-amber-600/30 transition-all transform hover:-translate-y-0.5 flex items-center justify-center space-x-2 text-sm tracking-wide">
                            <i class="fa-solid fa-fire-flame-curved text-lg"></i>
                            <span>GENERATE MODUL PERMAINAN</span>
                        </button>
                        <p id="generateStatus" class="hidden text-center text-sm font-bold" role="status" aria-live="polite"></p>
                    </form>
                </div>
            </div>

            <!-- DISPLAY GENERATED MODULE (RIGHT SIDE / PRINT DISPLAY) -->
            <div class="lg:col-span-7">

                <!-- EMPTY INITIAL STATE -->
                <div id="emptyState" class="bg-stone-800/60 rounded-2xl border-2 border-dashed border-stone-700 p-12 text-center text-stone-400 shadow-xl no-print">
                    <div class="w-20 h-20 bg-stone-900 text-amber-500 rounded-2xl flex items-center justify-center mx-auto mb-4 text-3xl shadow-inner border border-stone-700">
                        <i class="fa-solid fa-scroll"></i>
                    </div>
                    <h3 class="font-extrabold text-stone-200 text-lg mb-1">Modul Belum Dibuat</h3>
                    <p class="text-xs text-stone-400 max-w-md mx-auto leading-relaxed">
                        Lengkapi parameter kegiatan di formulir sebelah kiri, lalu klik tombol <b class="text-amber-400">Generate Modul Permainan</b> untuk memuat modul lengkap berstandar resmi Gugus Depan.
                    </p>
                </div>

                <!-- GENERATED MODULE SHEET (DESIGNED TO MATCH PDF EXHIBIT) -->
                <div id="printArea" class="hidden">
                    <div class="bg-paper-texture text-stone-900 rounded-2xl shadow-2xl border-2 border-stone-800 p-6 sm:p-8 relative">

                        <!-- OFFICIAL KOP / HEADER MODUL -->
                        <div class="border-b-4 border-double border-stone-900 pb-4 mb-5 text-center relative">
                            <div class="text-[11px] font-black tracking-widest text-stone-600 uppercase">
                                GERAKAN PRAMUKA GUGUS DEPAN
                            </div>
                            <div id="outGudep" class="text-lg font-black text-stone-900 uppercase tracking-tight mt-0.5">
                                GUGUS DEPAN 01.001-01.002
                            </div>
                            <div id="outPangkalan" class="text-xs font-semibold text-stone-700">
                                Pangkalan Latihan & Pembinaan Karakter Pramuka Interaktif
                            </div>
                            <div class="inline-block bg-stone-900 text-amber-300 font-extrabold text-xs px-4 py-1 rounded-full uppercase tracking-wider mt-3 shadow-sm">
                                MODUL PERMAINAN LATIHAN
                            </div>
                        </div>

                        <!-- METADATA GRID BOX (EXACT MATCH TO PDF) -->
                        <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 text-xs mb-6 bg-stone-100 p-3 rounded-xl border border-stone-300">
                            <div class="border-r border-stone-300 pr-2">
                                <span class="text-[10px] uppercase font-bold text-stone-500 block">TINGKATAN:</span>
                                <span id="outTingkatan" class="font-extrabold text-stone-900 uppercase">PENEGAK</span>
                            </div>
                            <div class="border-r border-stone-300 sm:border-r pr-2 pl-1">
                                <span class="text-[10px] uppercase font-bold text-stone-500 block">KATEGORI:</span>
                                <span id="outKategori" class="font-bold text-amber-800">Ice Breaking</span>
                            </div>
                            <div class="border-r border-stone-300 pr-2 pl-1">
                                <span class="text-[10px] uppercase font-bold text-stone-500 block">TARGET DURASI:</span>
                                <span id="outDurasi" class="font-bold text-stone-800">30 Menit</span>
                            </div>
                            <div class="pl-1">
                                <span class="text-[10px] uppercase font-bold text-stone-500 block">JUMLAH PESERTA:</span>
                                <span id="outPeserta" class="font-bold text-stone-800">45 Orang</span>
                            </div>
                            <div class="col-span-2 sm:col-span-4 border-t border-stone-200 pt-1.5 mt-1 text-[11px] font-semibold text-stone-600 flex justify-between items-center">
                                <span><i class="fa-regular fa-calendar-check mr-1 text-amber-700"></i> Tanggal Latihan:</span>
                                <span id="outTanggal" class="font-bold text-stone-900">Selasa, 20 Oktober 2026</span>
                            </div>
                        </div>

                        <!-- GAME TITLE & QUOTE -->
                        <div class="mb-6">
                            <h2 id="outNamaGame" class="text-2xl font-black text-stone-950 tracking-tight">
                                Jabat Tangan Aneh
                            </h2>
                            <p id="outQuoteGame" class="text-xs sm:text-sm font-medium text-stone-600 italic mt-1 leading-relaxed border-l-2 border-amber-500 pl-3">
                                "Permainan pencair suasana dengan memperagakan berbagai gaya jabat tangan tidak biasa untuk saling mengenal."
                            </p>
                            <p id="outGamePlayers" class="hidden text-[11px] text-stone-500 mt-2"></p>
                        </div>

                        <!-- SANGGA / REGU / BARUNG BREAKDOWN (EXACT MATCH TO PDF) -->
                        <div class="mb-6 bg-stone-50 p-4 rounded-xl border border-stone-200">
                            <h3 id="outGroupTitle" class="text-xs font-black uppercase text-stone-800 tracking-wider mb-2.5 flex items-center gap-1.5">
                                <i class="fa-solid fa-users-gear text-amber-600"></i>
                                <span>PEMBAGIAN SANGGA & KELOMPOK (8 SANGGA)</span>
                            </h3>
                            <p id="outGroupSummary" class="text-xs text-stone-600 mb-3">
                                Berdasarkan input 45 peserta golongan Penegak, peserta dibagi menjadi 8 Sangga (rata-rata 5-6 orang per Sangga).
                            </p>
                            <!-- Dynamic Unit Grid -->
                            <div id="outUnitsContainer" class="grid grid-cols-2 sm:grid-cols-3 gap-2 text-xs">
                                <!-- Populated dynamically -->
                            </div>
                        </div>

                        <!-- ALAT & BAHAN -->
                        <div class="mb-6">
                            <h3 class="text-xs font-black uppercase text-stone-800 tracking-wider mb-1.5 flex items-center gap-1.5">
                                🎒 ALAT & BAHAN YANG DIPERLUKAN:
                            </h3>
                            <div id="outPeralatan" class="text-xs text-stone-700 bg-stone-100 p-3 rounded-lg border border-stone-200 font-medium">
                                Tidak ada
                            </div>
                        </div>

                        <!-- LANGKAH-LANGKAH PELAKSANAAN -->
                        <div class="mb-6">
                            <h3 class="text-xs font-black uppercase text-stone-800 tracking-wider mb-2 flex items-center gap-1.5">
                                📋 LANGKAH-LANGKAH PELAKSANAAN (CARA MAIN):
                            </h3>
                            <ol id="outStepsList" class="list-decimal list-inside space-y-2 text-xs text-stone-800 leading-relaxed font-medium bg-stone-50 p-4 rounded-xl border border-stone-200">
                                <!-- Populated dynamically -->
                            </ol>
                        </div>

                        <!-- TIPS & VARIASI PEMBINA -->
                        <div class="mb-6">
                            <h3 class="text-xs font-black uppercase text-amber-900 tracking-wider mb-1.5 flex items-center gap-1.5">
                                💡 TIPS & VARIASI PEMBINA:
                            </h3>
                            <div id="outTips" class="text-xs text-amber-950 bg-amber-50 p-3.5 rounded-xl border border-amber-200 leading-relaxed font-medium">
                                Makin absurd gaya jabat tangannya (misalnya 'jabat tangan jempol kaki'), makin cair suasananya.
                            </div>
                        </div>

                        <!-- INSTRUKSI KESELAMATAN (SAFETY RULES) -->
                        <div class="mb-6">
                            <h3 class="text-xs font-black uppercase text-red-900 tracking-wider mb-1.5 flex items-center gap-1.5">
                                🛡️ INSTRUKSI KESELAMATAN (PANDUAN UMUM):
                            </h3>
                            <ul id="outSafety" class="list-disc list-inside space-y-1 text-xs text-red-950 bg-red-50/70 p-3.5 rounded-xl border border-red-200 font-medium">
                                <li>Pastikan area bebas dari permukaan licin atau batu tajam.</li>
                                <li>Sediakan kotak P3K standar di dekat lokasi kegiatan.</li>
                            </ul>
                        </div>

                        <!-- PENANAMAN NILAI KODE KEHORMATAN -->
                        <div class="mb-8">
                            <h3 class="text-xs font-black uppercase text-emerald-900 tracking-wider mb-1.5 flex items-center gap-1.5">
                                ⚜️ PENANAMAN NILAI KODE KEHORMATAN PRAMUKA:
                            </h3>
                            <ul id="outCharacter" class="space-y-1.5 text-xs text-emerald-950 bg-emerald-50/80 p-3.5 rounded-xl border border-emerald-200 font-medium">
                                <!-- Populated dynamically -->
                            </ul>
                        </div>

                        <!-- OFFICIAL SIGNATURE BLOCK (EXACT MATCH TO PDF) -->
                        <div class="pt-6 border-t-2 border-stone-800 grid grid-cols-2 text-center text-xs text-stone-800">
                            <div>
                                <p class="font-bold">Mengetahui,</p>
                                <p class="text-[11px] text-stone-600">Ketua Gudep / Kak Pembina</p>
                                <div class="h-16"></div>
                                <p id="outSignKetua" class="font-black text-stone-900 underline">Kak Mabigus / Ka Gudep</p>
                            </div>
                            <div>
                                <p class="font-bold">Pembuat Modul,</p>
                                <p class="text-[11px] text-stone-600">Pelatih / Pembina Pendamping</p>
                                <div class="h-16"></div>
                                <p id="outSignPembina" class="font-black text-stone-900 underline">Kak Kakak Pembina</p>
                            </div>
                        </div>

                        <!-- BOTTOM ACTION BAR -->
                        <div class="mt-8 pt-4 border-t border-stone-300 flex flex-wrap gap-2 justify-between items-center no-print">
                            <button id="rerollButton" type="button" onclick="generateGame(event)" class="px-4 py-2 bg-stone-900 hover:bg-stone-800 text-amber-400 font-bold text-xs rounded-xl transition flex items-center gap-1.5 shadow">
                                <i class="fa-solid fa-dice"></i>
                                <span>Acak Game Lain</span>
                            </button>

                            <div class="flex gap-2">
                                <button id="moduleEditButton" type="button" onclick="toggleModuleEdit()" class="px-4 py-2 bg-amber-100 hover:bg-amber-200 text-amber-950 font-bold text-xs rounded-xl transition flex items-center gap-1.5">
                                    <i class="fa-solid fa-pen-to-square"></i>
                                    <span>Edit Modul</span>
                                </button>
                                <button onclick="downloadWord()" class="px-4 py-2 bg-blue-100 hover:bg-blue-200 text-blue-950 font-bold text-xs rounded-xl transition flex items-center gap-1.5">
                                    <i class="fa-solid fa-file-word"></i>
                                    <span>Unduh Word</span>
                                </button>
                                <button onclick="copyModuleText()" class="px-4 py-2 bg-stone-200 hover:bg-stone-300 text-stone-800 font-bold text-xs rounded-xl transition flex items-center gap-1.5">
                                    <i class="fa-solid fa-copy"></i>
                                    <span>Salin Teks</span>
                                </button>
                                <button onclick="window.print()" class="px-5 py-2 bg-gradient-to-r from-amber-600 to-amber-700 hover:from-amber-500 hover:to-amber-600 text-white font-extrabold text-xs rounded-xl transition flex items-center gap-1.5 shadow-md">
                                    <i class="fa-solid fa-file-pdf"></i>
                                    <span>Cetak / Simpan PDF</span>
                                </button>
                            </div>
                        </div>

                    </div>
                </div>

            </div>

        </div>

        <!-- TAB 2: KATALOG DATABASE (200 GAMES) -->
        <div id="tabKatalog" class="hidden space-y-6">
            <div class="bg-stone-800/90 p-5 rounded-2xl border border-stone-700 shadow-xl flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="font-extrabold text-white text-lg flex items-center gap-2">
                        <i class="fa-solid fa-book-bookmark text-amber-500"></i>
                        <span>BASIS DATA 200 PERMAINAN PRAMUKA</span>
                    </h2>
                    <p class="text-xs text-stone-400 mt-0.5">Koleksi referensi game terlengkap untuk latihan mingguan Gudep.</p>
                </div>
                <div class="flex flex-wrap md:flex-nowrap gap-2 w-full md:w-auto">
                    <input type="text" id="searchKatalog" oninput="filterKatalog()" placeholder="Cari nama permainan..."
                        class="px-3.5 py-2 bg-stone-900 border border-stone-700 rounded-xl text-xs text-stone-100 w-full md:w-64 focus:ring-2 focus:ring-amber-500 outline-none">
                    <select id="filterKategori" onchange="filterKatalog()" class="px-3 py-2 bg-stone-900 border border-stone-700 rounded-xl text-xs text-stone-200 focus:ring-2 focus:ring-amber-500 outline-none">
                        <option value="ALL">Semua Kategori</option>
                        <option value="A">🎲 Ice Breaking</option>
                        <option value="B">🤝 Kerja Sama Tim</option>
                        <option value="C">🧭 Wide Game</option>
                        <option value="D">⚡ Ketangkasan</option>
                        <option value="E">🌧️ Dalam Ruangan</option>
                        <option value="F">🔥 Api Unggun</option>
                        <option value="G">🧠 Kepemimpinan</option>
                        <option value="H">🎨 Kreatif & Seni</option>
                        <option value="I">🛠️ Tekpram</option>
                    </select>
                </div>
            </div>

            <!-- Dynamic Catalog Grid -->
            <div id="katalogContainer" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                <!-- Dynamically Populated -->
            </div>
        </div>

    </main>

    <!-- FOOTER -->
    <footer class="bg-stone-950 text-stone-500 text-xs py-6 text-center border-t border-stone-800 no-print mt-12">
        <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-3">
            <p>© 2026 Generator Modul Permainan & Latihan Pramuka Interaktif. Salam Pramuka!</p>
            <p class="text-stone-600">Dibuat khusus untuk Pembina & Pelatih Gerakan Pramuka Indonesia</p>
        </div>
    </footer>

    <script>
window.GAME_DATABASE = [
  {
    "id": 1,
    "cat": "A",
    "name": "Jabat Tangan Aneh",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak dicantumkan dalam sumber",
    "steps": [
      "Semua peserta berjalan bebas mengelilingi area yang tidak terlalu luas.",
      "Pembina meneriakkan gaya jabat tangan, misalnya \"jabat tangan siku!\", \"jabat tangan kaki!\", \"jabat tangan punggung!\".",
      "Peserta harus segera mencari pasangan terdekat dan berjabat tangan dengan bagian tubuh yang disebutkan sambil menyebut namanya masing-masing.",
      "Setelah tiap ronde, peserta melanjutkan berjalan dan menunggu perintah gaya berikutnya.",
      "Di ronde terakhir, setiap peserta harus mengingat minimal tiga nama teman baru yang ia ajak jabat tangan."
    ],
    "tips": "Makin absurd gaya jabat tangannya (misalnya \"jabat tangan jempol kaki\"), makin cair suasananya."
  },
  {
    "id": 2,
    "cat": "A",
    "name": "Bola Nama Berantai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Satu bola kecil atau gulungan kaus kaki",
    "steps": [
      "Peserta berdiri membentuk lingkaran.",
      "Orang pertama melempar bola ke peserta lain sambil menyebut namanya sendiri dengan lantang, misalnya \"Aku Dimas!\".",
      "Penerima melempar ke orang lain sambil menyebut namanya sendiri, begitu seterusnya sampai semua kebagian.",
      "Putaran kedua: lemparan harus mengikuti urutan yang sama seperti putaran pertama, tapi kali ini menyebut nama penerima (\"Buat Sinta!\").",
      "Putaran ketiga: ulangi urutan yang sama secepat mungkin tanpa boleh salah sasaran."
    ],
    "tips": "Tambahkan bola kedua saat putaran ketiga supaya makin seru dan melatih fokus."
  },
  {
    "id": 3,
    "cat": "A",
    "name": "Kata Berlawanan",
    "quote": "",
    "players": "10–40 orang",
    "dur": "10 menit",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berbaris atau membentuk lingkaran menghadap pembina.",
      "Pembina mengucapkan satu kata sifat, misalnya \"tinggi!\", \"cepat!\", \"besar!\".",
      "Peserta harus segera menunjukkan gerakan yang berlawanan: \"tinggi\" berarti jongkok, \"cepat\" berarti bergerak lambat, \"besar\" berarti mengecilkan badan.",
      "Yang salah gerakan atau terlambat keluar dari lingkaran dan menjadi juri.",
      "Lanjutkan sampai tersisa 3–5 peserta tercepat dan mereka dinyatakan pemenang."
    ],
    "tips": "Percepat tempo perintah di tengah permainan untuk menguji refleks sekaligus memanaskan badan."
  },
  {
    "id": 4,
    "cat": "A",
    "name": "PindaH Pulau",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Beberapa lembar koran atau kardus bekas (sebagai \"pulau\")",
    "steps": [
      "Sebar lembaran koran di tanah dengan jarak sekitar satu langkah kaki, jumlahnya satu lebih sedikit dari jumlah peserta.",
      "Semua peserta berdiri di atas satu lembar koran masing-masing (\"pulau\").",
      "Pembina berteriak \"banjir datang!\" dan peserta harus berpindah ke pulau lain — tidak boleh ke pulau yang sama dua kali berturut-turut.",
      "Setiap ronde, pembina mengambil satu pulau sehingga peserta harus berbagi pulau berdua atau bertiga tanpa kaki menyentuh tanah.",
      "Peserta yang kakinya menyentuh tanah keluar; permainan berakhir saat hanya tersisa satu pulau dengan beberapa orang berdesakan di atasnya."
    ],
    "tips": "Batasi waktu pindah hanya 5 detik supaya peserta harus bergerak cepat dan saling membantu."
  },
  {
    "id": 5,
    "cat": "A",
    "name": "Senam Angka Badan",
    "quote": "",
    "players": "10–40 orang",
    "dur": "10 menit",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berkelompok 4–5 orang dan berdiri berjajar.",
      "Pembina meneriakkan sebuah angka, misalnya \"7!\" atau \"2026!\".",
      "Setiap kelompok harus membentuk angka tersebut dengan tubuh mereka — bisa berbaring, berdiri, atau mengangkat tangan.",
      "Kelompok yang paling cepat dan paling mirip bentuknya mendapat poin.",
      "Ulangi dengan angka berbeda sebanyak 5–6 ronde, kelompok dengan poin terbanyak menang."
    ],
    "tips": "Gunakan kata pendek seperti \"SIAP\" atau \"REGU\" selain angka supaya lebih variatif."
  },
  {
    "id": 6,
    "cat": "A",
    "name": "Kejar Ekor Kertas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Potongan kertas/krep sepanjang 30 cm per peserta, atau tali rafia",
    "steps": [
      "Setiap peserta menyelipkan potongan kertas di pinggang belakang celana seperti ekor.",
      "Semua peserta bergerak di area yang dibatasi, berusaha merebut \"ekor\" peserta lain.",
      "Peserta yang ekornya direbut boleh tetap bermain dengan cara merebut ekor orang lain untuk mendapatkan ekor baru.",
      "Setiap ekor yang berhasil direbut dihitung sebagai satu poin untuk perebutnya.",
      "Setelah 5 menit, hitung poin; tiga peraih ekor terbanyak menjadi pemenang."
    ],
    "tips": "Mainkan dengan musik — saat musik berhenti, semua harus diam mematung (yang bergerak kehilangan satu ekor)."
  },
  {
    "id": 7,
    "cat": "A",
    "name": "Bisik Berantai Gambar",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan spidol per kelompok",
    "steps": [
      "Bagi peserta menjadi kelompok 6–8 orang, tiap kelompok berbaris ke belakang.",
      "Orang paling belakang menggambar sesuatu di punggung orang di depannya dengan jari (misalnya gambar rumah, pohon, matahari).",
      "Orang tersebut meneruskan \"gambar rasa\" yang ia rasakan ke punggung orang di depannya, begitu seterusnya sampai paling depan.",
      "Orang paling depan menggambar di kertas apa yang ia rasakan di punggungnya.",
      "Bandingkan gambar asli dan gambar akhir — kelompok dengan hasil paling mirip menang."
    ],
    "tips": "Mulai dari gambar sederhana (lingkaran, segitiga) lalu naik ke gambar yang lebih rumit di ronde berikutnya."
  },
  {
    "id": 8,
    "cat": "A",
    "name": "Tepuk Tangan Komando",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berdiri melingkar, pembina di tengah sebagai pemberi komando.",
      "Pembina menjelaskan tiga aba-aba: \"satu!\" = tepuk tangan sekali, \"dua!\" = tepuk paha dua kali, \"tiga!\" = hentak kaki lalu tepuk tangan.",
      "Pembina mengucapkan aba-aba secara acak dengan tempo makin cepat.",
      "Peserta yang salah gerakan atau terlambat jongkok satu ronde sebagai hukuman lalu ikut lagi.",
      "Setelah 5 menit, peserta yang tidak pernah salah maju ke depan dan memimpin satu ronde sebagai komandan."
    ],
    "tips": "Selingi dengan aba-aba palsu (\"satu setengah!\") — yang ikut bergerak dinyatakan gugur ronde itu."
  },
  {
    "id": 9,
    "cat": "A",
    "name": "Balon Berpasangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Balon secukupnya (satu per pasangan)",
    "steps": [
      "Peserta berpasangan, tiap pasangan menjepit satu balon di antara dahi mereka tanpa boleh dipegang tangan.",
      "Pasangan harus berjalan bersama dari garis start ke garis finis sejauh sekitar 10 meter.",
      "Jika balon jatuh atau pecah, pasangan kembali ke garis start dan mengulang.",
      "Di garis finis, pasangan harus memecahkan balon dengan cara menghimpitnya (tanpa tangan) untuk mengambil kertas misi di dalamnya.",
      "Pasangan tercepat yang berhasil menyelesaikan misi di kertas menjadi pemenang."
    ],
    "tips": "Isi kertas misi dengan perintah lucu seperti \"teriak yel-yel regu sekencang-kencangnya\" supaya finisnya meriah."
  },
  {
    "id": 10,
    "cat": "A",
    "name": "Lingkaran Listrik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berdiri melingkar dan bergandengan tangan.",
      "Satu orang ditunjuk sebagai \"sumber listrik\" yang diam-diam meremas tangan tetangganya sebagai sinyal.",
      "Remasan diteruskan dari tangan ke tangan mengelilingi lingkaran secepat mungkin.",
      "Satu orang menjadi pengamat di tengah lingkaran dan harus menebak di mana posisi \"arus listrik\" saat ini berada.",
      "Jika tebakan pengamat benar, si pembawa arus menjadi pengamat baru; jika salah setelah tiga tebakan, pengamat diganti."
    ],
    "tips": "Perbolehkan arus dikirim ke dua arah (kiri atau kanan) supaya pengamat makin sulit menebak."
  },
  {
    "id": 11,
    "cat": "A",
    "name": "Tebak Gaya Benda",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "wadah/Topi untuk undian",
    "steps": [
      "Tulis nama-nama benda di kertas (misalnya \"kompor\", \"payung\", \"jam dinding\"), lipat, masukkan ke wadah.",
      "Bagi peserta menjadi dua kelompok yang duduk berhadapan.",
      "Satu perwakilan mengambil undian lalu memperagakan benda itu dengan gerakan tubuh tanpa suara.",
      "Kelompoknya harus menebak dalam waktu 1 menit; jawaban benar dapat 10 poin.",
      "Giliran berganti ke kelompok lawan; kelompok dengan poin tertinggi setelah semua mendapat giliran menang."
    ],
    "tips": "Batasi kategori bendanya per ronde (ronde 1: alat dapur, ronde 2: alat Pramuka) supaya makin menantang."
  },
  {
    "id": 12,
    "cat": "A",
    "name": "Lomba Jalan Kepiting",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada (cukup area lapang 15–20 meter)",
    "steps": [
      "Peserta berpasangan, duduk membelakangi satu sama lain lalu mengaitkan lengan (punggung menempel punggung).",
      "Dalam posisi itu, pasangan harus berdiri bersama tanpa melepas kaitan lengan.",
      "Setelah berhasil berdiri, pasangan berjalan seperti kepiting (menyamping) menuju garis finis.",
      "Jika kaitan lengan terlepas, pasangan harus duduk dan mengulang dari posisi awal di tempat mereka berhenti.",
      "Tiga pasangan tercepat sampai finis menjadi pemenang."
    ],
    "tips": "Tambahkan rintangan ringan seperti berjalan memutari tongkat supaya butuh koordinasi lebih."
  },
  {
    "id": 13,
    "cat": "A",
    "name": "Siapa Hilang?",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain/sarung untuk menutup mata satu peserta",
    "steps": [
      "Semua peserta berdiri melingkar, satu orang ditutup matanya di tengah lingkaran.",
      "Pembina menunjuk diam-diam satu peserta untuk jongkok/bersembunyi di balik lingkaran.",
      "Penutup mata dibuka, dan orang di tengah harus menebak siapa yang hilang dalam waktu 30 detik.",
      "Jika benar, yang bersembunyi bergantian menjadi penebak; jika salah, ia menjadi penebak lagi maksimal dua kali.",
      "Lanjutkan beberapa ronde dengan jumlah yang disembunyikan ditambah menjadi dua orang."
    ],
    "tips": "Minta peserta yang tersisa bertukar posisi/kaus agar penebak makin terkecoh."
  },
  {
    "id": 14,
    "cat": "A",
    "name": "Estafet Kaus Kaki",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 pasang kaus kaki besar per tim",
    "steps": [
      "Bagi peserta menjadi tim-tim berisi 6–8 orang, tiap tim berbaris ke belakang.",
      "Orang pertama memakai sepasang kaus kaki besar di tangannya (seperti sarung tinju).",
      "Ia harus berlari ke titik balik sekitar 10 meter, menyentuh tiang, lalu kembali.",
      "Kaus kaki dilepas dan dipakaikan ke orang berikutnya yang melanjutkan lari yang sama.",
      "Tim yang semua anggotanya selesai lebih dulu menang; kaus kaki yang lepas di tengah jalan harus dipakai ulang di tempat."
    ],
    "tips": "Ganti kaus kaki dengan sarung tangan kain supaya lebih mudah didapat dan tetap lucu dipakai."
  },
  {
    "id": 15,
    "cat": "A",
    "name": "Yel-Yel Sambung Kata",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta duduk melingkar per regu.",
      "Orang pertama meneriakkan satu kata semangat, misalnya \"Tangkas!\".",
      "Orang berikutnya harus menyambung dengan kata yang berima atau berkaitan, misalnya \"Tangkas– Cerdas!\", lalu berikutnya \"Cerdas–Ikhlas!\".",
      "Yang tidak bisa menyambung dalam 5 detik atau mengulang kata yang sudah dipakai keluar dari lingkaran.",
      "Tiga orang terakhir yang bertahan menggabungkan kata-katanya menjadi yel-yel regu dadakan dan diteriakkan bersama."
    ],
    "tips": "Wajibkan kata sambungannya berhubungan dengan Dasa Darma supaya sekalian mengasah hafalan."
  },
  {
    "id": 16,
    "cat": "A",
    "name": "Lempar Tangkap Berhitung",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Satu bola kecil",
    "steps": [
      "Peserta berdiri melingkar agak renggang.",
      "Pelempar pertama melempar bola ke siapa saja sambil menyebut angka \"satu!\".",
      "Penerima melempar ke orang lain sambil menyebut \"dua!\", begitu seterusnya berurutan.",
      "Jika ada yang salah menyebut angka, menjatuhkan bola, atau melempar ke orang yang sama dua kali beruntun, ia keluar satu ronde.",
      "Setiap putaran penuh (kembali ke angka satu), tempo lemparan dipercepat; pemenangnya adalah yang bertahan paling lama."
    ],
    "tips": "Di ronde lanjut, hitung mundur dari 20 ke 1 atau gunakan kelipatan (2, 4, 6...) supaya otaknya ikut panas."
  },
  {
    "id": 17,
    "cat": "A",
    "name": "Manusia Karpet Ajaib",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 lembar kain/sarung per tim",
    "steps": [
      "Bagi peserta menjadi tim 6–7 orang, tiap tim mendapat dua lembar kain.",
      "Tim harus menyeberang dari garis start ke finis (sekitar 15 meter) dengan cara seluruh anggota selalu berdiri di atas kain — kaki tidak boleh menyentuh tanah.",
      "Caranya: letakkan satu kain di depan, pindah ke sana, lalu ambil kain belakang dan letakkan lagi di depan, begitu seterusnya.",
      "Anggota yang kakinya menyentuh tanah membuat timnya mengulang dari titik terakhir yang aman.",
      "Tim tercepat sampai finis dengan semua anggota menang."
    ],
    "tips": "Persempit kainnya (misalnya sarung dilipat dua) supaya tim harus berdesakan dan makin kompak."
  },
  {
    "id": 18,
    "cat": "A",
    "name": "Duel Jempol Raksasa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berpasangan dan saling berhadapan, kedua tangan saling menggenggam kecuali jempol yang diacungkan ke atas.",
      "Dengan aba-aba pembina, tiap orang berusaha menekan jempol lawan hingga menyentuh punggung tangannya sendiri.",
      "Pemenang tiap duel maju melawan pemenang duel lain (sistem gugur).",
      "Duel dibatasi 30 detik; jika seri, keduanya suit untuk menentukan yang lolos.",
      "Juara terakhir dinobatkan sebagai \"Raja Jempol\" dan boleh memberi hukuman lucu ke finalis yang kalah."
    ],
    "tips": "Mainkan versi beregu: total kemenangan tiap regu dijumlahkan untuk menentukan regu terkuat."
  },
  {
    "id": 19,
    "cat": "A",
    "name": "Rantai Nama Super Cepat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berdiri melingkar.",
      "Orang pertama menyebut namanya sendiri plus satu gerakan khas, misalnya \"Rina!\" sambil melompat.",
      "Orang kedua mengulang nama dan gerakan orang pertama, lalu menambah namanya sendiri plus gerakan baru.",
      "Begitu seterusnya mengelilingi lingkaran — rantai nama dan gerakan makin panjang.",
      "Yang lupa urutan atau salah gerakan keluar; yang bertahan sampai akhir menang."
    ],
    "tips": "Batasi gerakan khasnya yang berhubungan dengan hobi masing-masing supaya sekalian saling kenal lebih dalam."
  },
  {
    "id": 20,
    "cat": "A",
    "name": "Perang Bantal Kertas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Banyak bola dari kertas koran bekas yang diremas",
    "steps": [
      "Bagi area menjadi dua wilayah dengan garis tengah, tiap tim menempati satu wilayah.",
      "Sebar bola-bola kertas koran di kedua wilayah sama banyak.",
      "Dengan aba-aba mulai, tiap tim melemparkan bola kertas ke wilayah lawan selama 3 menit.",
      "Peserta tidak boleh melewati garis tengah dan tidak boleh menendang bola.",
      "Saat waktu habis, tim dengan jumlah bola kertas paling sedikit di wilayahnya menang."
    ],
    "tips": "Selipkan 2–3 \"bola emas\" (kertas dibungkus lakban warna) yang bernilai minus 5 bola bagi pemilik wilayah — jadi rebutan melemparnya ke lawan."
  },
  {
    "id": 21,
    "cat": "B",
    "name": "Menara Koran",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Koran bekas, selotip",
    "steps": [
      "Bagi peserta menjadi regu berisi 4–6 orang. Setiap regu mendapat 10 lembar koran dan 1 rol selotip.",
      "Tugas regu: membangun menara setinggi mungkin yang bisa berdiri sendiri selama 10 detik.",
      "Koran boleh digulung, dilipat, atau diremas, tetapi tidak boleh disandarkan ke dinding atau meja.",
      "Beri waktu 15 menit untuk membangun; pembina menghitung mundur 1 menit terakhir.",
      "Menara yang tetap berdiri setelah 10 detik diukur tingginya; regu dengan menara tertinggi menang."
    ],
    "tips": "Untuk versi lebih sulit, larang penggunaan selotip — regu hanya boleh melipat dan menyisipkan koran."
  },
  {
    "id": 22,
    "cat": "B",
    "name": "Jaring Laba-laba",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali rafia atau tali pramuka, dua tiang/pohon",
    "steps": [
      "Bentangkan tali di antara dua tiang membentuk jaring laba-laba dengan lubang-lubang berukuran bervariasi.",
      "Regu harus memindahkan semua anggotanya dari satu sisi jaring ke sisi lain tanpa menyentuh tali.",
      "Setiap lubang hanya boleh dilewati satu orang; lubang yang sudah dipakai dianggap \"tertutup\".",
      "Anggota yang sudah lolos boleh membantu mengangkat atau menahan teman dari sisi seberang.",
      "Jika ada yang menyentuh tali, orang tersebut harus mengulang dari awal (atau seluruh regu mengulang, sesuai kesepakatan)."
    ],
    "tips": "Buat beberapa lubang kecil di bagian atas agar regu harus memikirkan strategi urutan siapa duluan."
  },
  {
    "id": 23,
    "cat": "B",
    "name": "Pipa Bocor",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Pipa paralon berlubang (atau bambu), bola pingpong, ember air, gelas ukur",
    "steps": [
      "Berdirikan pipa paralon setinggi ±1 meter yang sudah dilubangi kecil-kecil di beberapa titik; letakkan bola pingpong di dasar pipa.",
      "Regu harus mengangkat bola pingpong hingga keluar dari ujung atas pipa hanya dengan menuangkan air ke dalam pipa.",
      "Anggota bergantian mengambil air dari ember dengan gelas, tetapi lubang-lubang pipa harus ditutup dengan jari agar air tidak bocor.",
      "Setiap anggota hanya boleh menutup maksimal dua lubang dengan jarinya.",
      "Regu tercepat mengeluarkan bola pingpong adalah pemenangnya."
    ],
    "tips": "Tambah lubang atau kurangi jumlah gelas agar regu harus mengatur giliran dan strategi menutup lubang."
  },
  {
    "id": 24,
    "cat": "B",
    "name": "Tongkat Terapung",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tongkat pramuka atau bambu ringan (±2 meter)",
    "steps": [
      "Peserta berdiri berhadapan dalam dua baris, lalu mengacungkan jari telunjuk ke depan sejajar bahu.",
      "Pembina meletakkan tongkat ringan di atas semua jari telunjuk peserta.",
      "Tugas regu: menurunkan tongkat hingga menyentuh tanah, dengan syarat semua jari harus selalu menempel pada tongkat.",
      "Jika ada satu jari pun yang lepas, ulangi dari posisi awal.",
      "Tantangan sesungguhnya: tongkat cenderung \"terapung\" naik, jadi regu harus bergerak sangat pelan dan sinkron."
    ],
    "tips": "Setelah berhasil sekali, ulangi dengan mata sebagian peserta ditutup agar komunikasi verbal makin penting."
  },
  {
    "id": 25,
    "cat": "B",
    "name": "Lintas Sungai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kardus bekas atau koran sebagai \"batu pijakan\"), tali untuk garis start-finish",
    "steps": [
      "Tandai \"sungai\" selebar 5–8 meter dengan tali di kedua sisinya.",
      "Setiap regu mendapat \"batu pijakan\" sejumlah anggota regu dikurangi satu (mis. regu 6 orang dapat 5 pijakan).",
      "Seluruh regu harus menyeberangi sungai hanya dengan berpijak pada pijakan; kaki yang menyentuh tanah di luar pijakan membuat seluruh regu mengulang.",
      "Pijakan yang tidak diinjak boleh digeser ke depan, tetapi tidak boleh dilempar.",
      "Regu yang seluruh anggotanya sampai di seberang lebih dulu menang."
    ],
    "tips": "Perlebar sungai atau kurangi pijakan agar regu harus menggendong atau melompat berantai."
  },
  {
    "id": 26,
    "cat": "B",
    "name": "Kursi Lingkaran",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berdiri membentuk lingkaran rapat, bahu saling bersentuhan, semua menghadap ke arah yang sama (mis. searah jarum jam).",
      "Atas aba-aba pembina, semua peserta perlahan menekuk lutut dan duduk di atas paha orang di belakangnya.",
      "Tahan posisi duduk ini selama 30 detik tanpa ada yang jatuh atau berdiri.",
      "Jika formasi runtuh, ulangi dari awal dan coba bertahan lebih lama.",
      "Setelah berhasil, coba berjalan bersama satu putaran lingkaran sambil tetap \"duduk\"."
    ],
    "tips": "Tantang regu untuk bertepuk tangan bersama atau menyanyikan yel-yel sambil mempertahankan formasi."
  },
  {
    "id": 27,
    "cat": "B",
    "name": "Terowongan Manusia",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Bola atau balon",
    "steps": [
      "Regu berdiri berbanjar dengan kaki direnggangkan selebar bahu, membentuk terowongan.",
      "Orang paling belakang merangkak melewati terowongan sambil mendorong bola ke depan.",
      "Setelah keluar di depan, ia berdiri menjadi bagian terowongan paling depan, lalu orang berikutnya di belakang mulai merangkak.",
      "Lanjutkan hingga seluruh regu berpindah sejauh jarak yang ditentukan (mis. 15 meter).",
      "Jika bola keluar dari terowongan, regu harus berhenti dan mengulang dari posisi terakhir bola keluar."
    ],
    "tips": "Gunakan dua bola sekaligus atau minta peserta merangkak mundur untuk menambah kesulitan."
  },
  {
    "id": 28,
    "cat": "B",
    "name": "Piramida Manusia",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Matras (opsional, untuk keamanan)",
    "steps": [
      "Regu merancang formasi piramida: baris bawah sebagai fondasi (4–6 orang berlutut), baris tengah (2–3 orang), dan satu orang di puncak.",
      "Baris bawah berlutut rapat dengan punggung sejajar; pastikan yang berbadan besar di bawah.",
      "Baris tengah naik perlahan dengan bantuan teman, berlutut di atas punggung baris bawah.",
      "Orang puncak dibantu naik terakhir, lalu mengangkat kedua tangan sebagai tanda selesai.",
      "Piramida harus bertahan 10 detik tanpa runtuh; dokumentasikan dengan foto sebagai kenang-kenangan."
    ],
    "tips": "Minta setiap tingkat piramida meneriakkan yel regu secara bergantian dari bawah ke atas."
  },
  {
    "id": 29,
    "cat": "B",
    "name": "Kompas Buta",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain penutup mata, kursi/rintangan ringan, tali",
    "steps": [
      "Susun rintangan ringan (kursi, kardus, tali rendah) membentuk jalur berkelok di lapangan.",
      "Satu anggota regu ditutup matanya dan menjadi \"penjelajah\"; anggota lain berdiri di sisi jalur sebagai \"kompas\".",
      "Para kompas hanya boleh memberi arahan suara (mis. \"dua langkah ke kiri\", \"jongkok\") — tidak boleh menyentuh penjelajah.",
      "Jika penjelajah menyentuh rintangan, regu mendapat penalti 10 detik.",
      "Ganti penjelajah hingga semua anggota regu pernah menjadi penjelajah; total waktu tercepat menang."
    ],
    "tips": "Batasi kosakata arahan hanya boleh \"maju, kiri, kanan, berhenti, jongkok\" agar komunikasi harus presisi."
  },
  {
    "id": 30,
    "cat": "B",
    "name": "Estafet Spons Air",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Spons besar, 2 ember per regu satu berisi air, satu kosong), gelas ukur",
    "steps": [
      "Setiap regu berbaris; di depan barisan ada ember berisi air, 10 meter di belakangnya ada ember kosong.",
      "Orang pertama mencelupkan spons ke ember air, lalu berlari dan memerasnya ke ember kosong.",
      "Spons dioper ke orang berikutnya yang mengulang hal yang sama; begitu seterusnya selama 10 menit.",
      "Anggota regu boleh menyusun strategi urutan pelari tercepat di awal atau di akhir.",
      "Setelah waktu habis, ukur air di ember kosong; regu dengan air terbanyak menang."
    ],
    "tips": "Tambahkan rintangan zig-zag yang harus dilewati pelari agar tidak sekadar adu lari."
  },
  {
    "id": 31,
    "cat": "B",
    "name": "Bangun Jembatan Kertas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas HVS, selotip, dua meja/kursi sebagai penyangga, kelereng atau beban kecil",
    "steps": [
      "Letakkan dua meja berjarak 50 cm; celah di antaranya adalah \"jurang\".",
      "Setiap regu mendapat 10 lembar kertas HVS dan selotip; tugasnya membangun jembatan melintasi jurang.",
      "Jembatan harus mampu menahan beban (mis. 5 kelereng) selama 10 detik tanpa roboh.",
      "Regu boleh menguji dan memperbaiki jembatan selama waktu pembangunan 15 menit.",
      "Setelah waktu habis, uji semua jembatan; yang terkuat menang, bukan yang terindah."
    ],
    "tips": "Batasi selotip hanya 30 cm per regu agar mereka mengandalkan teknik lipatan kertas."
  },
  {
    "id": 32,
    "cat": "B",
    "name": "Rantai Pesan Tubuh",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu berisi perintah gerakan",
    "steps": [
      "Regu berdiri berbanjar menghadap ke depan; hanya orang paling belakang yang boleh melihat kartu perintah dari pembina.",
      "Orang paling belakang menepuk bahu orang di depannya dan memperagakan gerakan (tanpa suara) sesuai kartu.",
      "Gerakan diteruskan ke depan dari orang ke orang, hanya dengan sentuhan dan peragaan tubuh.",
      "Orang paling depan menyebutkan atau memperagakan tebakannya di hadapan pembina.",
      "Setiap tebakan benar mendapat poin; mainkan 5–6 ronde dengan kartu berbeda."
    ],
    "tips": "Gunakan perintah gerakan lucu khas pramuka (mis. \"baris-berbaris sambil melompat\") agar suasananya cair."
  },
  {
    "id": 33,
    "cat": "B",
    "name": "Menara Gelas Plastik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Gelas plastik (±30 per regu), karet gelang, tali",
    "steps": [
      "Setiap regu mendapat 30 gelas plastik, 4 karet gelang, dan tali secukupnya.",
      "Tantangan: menyusun menara gelas setinggi mungkin TANPA menyentuh gelas langsung dengan tangan.",
      "Regu harus membuat \"alat penjepit\" dari karet gelang dan tali yang dipegang bersama oleh beberapa anggota.",
      "Setiap gelas yang jatuh dan penyok tidak boleh dipakai lagi.",
      "Menara tertinggi yang berdiri sendiri selama 10 detik memenangkan permainan."
    ],
    "tips": "Wajibkan minimal 4 orang memegang tali penjepit sekaligus agar koordinasi makin diuji."
  },
  {
    "id": 34,
    "cat": "B",
    "name": "Bola Balon Berpasangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Balon",
    "steps": [
      "Peserta berpasangan; setiap pasangan menjepit satu balon di antara punggung mereka (punggung ketemu punggung).",
      "Pasangan harus berjalan menempuh jarak 10 meter tanpa memegang balon dengan tangan.",
      "Jika balon jatuh atau pecah, pasangan kembali ke garis start dan mengulang dengan balon baru.",
      "Setelah satu pasangan sampai, pasangan berikutnya dari regu yang sama mulai berjalan.",
      "Regu yang semua pasangannya selesai lebih dulu menang."
    ],
    "tips": "Minta pasangan berjalan mundur atau melewati rintangan zig-zag agar komunikasi pasangan makin penting."
  },
  {
    "id": 35,
    "cat": "B",
    "name": "Susun Puzzle Raksasa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Puzzle gambar besar (atau potongan gambar yang digunting), amplop",
    "steps": [
      "Siapkan satu gambar besar (mis. peta Indonesia atau lambang pramuka) yang dipotong menjadi 20–30 keping; masukkan ke amplop.",
      "Setiap regu mendapat satu amplop berisi kepingan yang sama.",
      "Aturan khusus: setiap anggota hanya boleh memegang dan memasang kepingan dengan warna tertentu (ditentukan lewat undian).",
      "Artinya tidak ada satu orang pun yang bisa menyelesaikan puzzle sendirian — semua harus berkontribusi.",
      "Regu pertama yang menyusun gambar dengan benar dan lengkap menang."
    ],
    "tips": "Acak warna kepingan antar-regu lalu minta mereka bernegosiasi tukar-menukar kepingan."
  },
  {
    "id": 36,
    "cat": "B",
    "name": "Jembatan Tangan Estafet",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Bola kecil (tenis atau plastik)",
    "steps": [
      "Regu berdiri berbanjar dengan jarak satu lengan; semua mengangkat kedua tangan ke atas membentuk \"jembatan\".",
      "Bola diletakkan di tangan orang paling belakang, lalu dioper ke depan hanya lewat sentuhan tangan ke tangan.",
      "Setiap operan harus melewati minimal dua pasang tangan sebelum sampai ke depan (tidak boleh dilempar jauh).",
      "Setelah bola sampai di depan, orang paling depan berlari ke belakang dan permainan berlanjut hingga garis finish tercapai.",
      "Jika bola jatuh, regu berhenti 10 detik sebagai penalti sebelum melanjutkan."
    ],
    "tips": "Gunakan dua bola berlawanan arah dalam satu barisan agar konsentrasi regu terpecah."
  },
  {
    "id": 37,
    "cat": "B",
    "name": "Perahu Kertas Raksasa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Koran bekas banyak, selotip, baskom air, kelereng (sebagai penumpang)",
    "steps": [
      "Setiap regu mendapat koran dan selotip untuk membuat perahu kertas sebesar mungkin.",
      "Semua anggota regu harus ikut melipat minimal satu bagian perahu — perahu \"perseorangan\" didiskualifikasi.",
      "Perahu diapungkan di baskom berisi air, lalu dimuati kelereng satu per satu sebagai \"penumpang\".",
      "Perahu dinyatakan tenggelam jika air masuk dan kelereng basah; catat jumlah kelereng yang berhasil dimuat.",
      "Regu dengan jumlah penumpang (kelereng) terbanyak sebelum tenggelam menang."
    ],
    "tips": "Batasi waktu melipat hanya 10 menit agar regu harus membagi tugas lipat, rekat, dan uji apung."
  },
  {
    "id": 38,
    "cat": "B",
    "name": "Lingkaran Duduk Berjalan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Bentuk lingkaran rapat seperti pada permainan Kursi Lingkaran, lalu duduk di paha orang di belakang.",
      "Setelah formasi stabil, tantang regu untuk berjalan bersama memutar lingkaran 360 derajat.",
      "Setiap 30 detik, pembina memberi aba-aba \"ganti arah\" sehingga lingkaran berbalik arah jalan.",
      "Jika ada yang jatuh, seluruh lingkaran berhenti, berdiri, dan mulai lagi dari titik jatuh.",
      "Regu yang berhasil menyelesaikan satu putaran penuh tanpa jatuh mendapat tepuk tangan meriah."
    ],
    "tips": "Minta lingkaran berjalan sambil menyanyikan lagu regu dengan tempo mengikuti langkah kaki."
  },
  {
    "id": 39,
    "cat": "B",
    "name": "Oper Air Gelas Kepala",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Gelas plastik, ember air, ember kosong",
    "steps": [
      "Regu berbaris; setiap orang memegang gelas plastik berisi air di atas kepalanya (boleh ditahan dengan satu tangan).",
      "Orang pertama menuang air dari gelasnya ke gelas orang kedua — tanpa menurunkan gelas dari kepala.",
      "Air diteruskan ke belakang dari gelas ke gelas hingga orang terakhir menuangkannya ke ember kosong.",
      "Air yang tumpah tidak boleh diambil lagi; regu harus mengatur kecepatan agar tumpahan minimal.",
      "Setelah 10 menit, ukur air di ember; regu dengan air terbanyak menang."
    ],
    "tips": "Minta peserta menuang dengan mata melihat ke depan (tidak boleh menengok) agar komunikasi antaranggota makin penting."
  },
  {
    "id": 40,
    "cat": "B",
    "name": "Tali Simpul Raksasa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali panjang (±10 meter)",
    "steps": [
      "Semua anggota regu memegang tali panjang membentuk lingkaran, lalu atas aba-aba melepaskan tali dan berjalan mengacaknya menjadi \"simpul raksasa\".",
      "Setelah kusut, semua kembali memegang tali di titik masing-masing — tidak boleh melepas lagi.",
      "Tugas regu: mengurai simpul hingga tali kembali membentuk lingkaran sempurna, tanpa ada yang melepas pegangan.",
      "Anggota boleh melangkah melewati tali, berputar, atau berjongkok, asal pegangan tidak lepas.",
      "Regu tercepat mengurai simpul menjadi lingkaran rapi menang."
    ],
    "tips": "Mainkan dengan dua tali yang saling bertautan agar regu harus mengurai dua simpul sekaligus."
  },
  {
    "id": 41,
    "cat": "B",
    "name": "Bangun Kota Kardus",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kardus bekas berbagai ukuran, selotip, spidol, gunting",
    "steps": [
      "Setiap regu mendapat tumpukan kardus dan ditantang membangun \"kota\" mini: minimal ada balai kota, sekolah, dan jembatan.",
      "Bagi peran: sebagian memotong, sebagian menempel, sebagian menggambar detail dengan spidol.",
      "Semua bangunan harus bisa berdiri sendiri dan tersusun dalam satu area \"kota\" berukuran 2x2 meter.",
      "Beri waktu 20 menit; 5 menit terakhir untuk merapikan dan memberi nama kota.",
      "Setiap regu mempresentasikan kotanya 1 menit; kota paling lengkap dan kokoh menang."
    ],
    "tips": "Tambahkan syarat \"kota harus punya sistem pertahanan dari serangan bola kertas\" lalu uji dengan lemparan bola kertas."
  },
  {
    "id": 42,
    "cat": "B",
    "name": "Estafet Kelereng Sendok",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Sendok makan, kelereng, cone/tiang penanda",
    "steps": [
      "Setiap regu berbaris di garis start; orang pertama menggigit gagang sendok yang di atasnya ada kelereng.",
      "Ia berjalan (tidak boleh berlari) memutari tiang 5 meter di depan, lalu kembali dan mengoper sendok+kelereng ke orang berikutnya — operan dilakukan dari mulut ke mulut tanpa tangan.",
      "Jika kelereng jatuh, pengemban harus kembali ke garis start dan mengulang.",
      "Tangan hanya boleh dipakai untuk mengambil kelereng yang jatuh, bukan untuk menahan sendok.",
      "Regu yang semua anggotanya selesai lebih dulu menang."
    ],
    "tips": "Minta operan sendok dilakukan sambil kedua regu menyanyikan yel — yang tertawa dan menjatuhkan kelereng mengulang."
  },
  {
    "id": 43,
    "cat": "B",
    "name": "Jaring Penyelamat Telur",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Telur mentah, koran, sedotan, selotip, kantong plastik",
    "steps": [
      "Setiap regu mendapat satu telur mentah dan bahan pelindung terbatas (koran, sedotan, selotip, kantong plastik).",
      "Tugas: membuat \"kapsul penyelamat\" agar telur selamat saat dijatuhkan dari ketinggian 3 meter.",
      "Semua anggota harus berkontribusi minimal satu ide desain sebelum regu memilih desain final lewat musyawarah.",
      "Kapsul dijatuhkan dari lantai 2 atau tangga; telur yang pecah berarti misi gagal.",
      "Regu yang telurnya selamat dengan desain paling ringan/hemat bahan mendapat nilai tambah."
    ],
    "tips": "Naikkan ketinggian jatuh bertahap (2 m, 3 m, 4 m) sebagai babak penyisihan hingga tersisa satu pemenang."
  },
  {
    "id": 44,
    "cat": "B",
    "name": "Simfoni Tepuk Tangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Regu berdiri melingkar; pembina mengajarkan pola tepuk tangan 8 ketukan (mis. 2 tepuk tangan, 1 tepuk paha, 1 jentik jari, diulang).",
      "Seluruh regu berlatih bersama hingga pola terdengar kompak dan serempak.",
      "Setelah kompak, percepat tempo pola secara bertahap atas aba-aba pembina.",
      "Anggota yang salah pola harus jongkok satu putaran pola sebagai \"hukuman lucu\", lalu ikut lagi.",
      "Tantangan akhir: tampilkan simfoni tepuk tangan 1 menit penuh tanpa kesalahan di depan regu lain."
    ],
    "tips": "Bagi lingkaran menjadi dua kelompok yang memainkan pola berbeda secara bersamaan seperti orkestra."
  },
  {
    "id": 45,
    "cat": "B",
    "name": "Rantai Kaki Tiga",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali rafia atau kain untuk mengikat kaki, cone penanda",
    "steps": [
      "Peserta berpasangan; kaki kanan satu orang diikat dengan kaki kiri pasangannya (kaki tiga).",
      "Pasangan-pasangan dalam satu regu kemudian saling bergandengan tangan membentuk rantai panjang.",
      "Rantai harus berjalan bersama menempuh lintasan 20 meter memutari cone dan kembali.",
      "Jika ada ikatan kaki yang lepas atau rantai tangan yang putus, seluruh rantai berhenti 10 detik.",
      "Regu yang rantai kakinya sampai finish utuh dan tercepat menang."
    ],
    "tips": "Minta rantai berjalan mundur di setengah lintasan terakhir agar koordinasi makin diuji."
  },
  {
    "id": 46,
    "cat": "C",
    "name": "Misi Penyelamatan Pendaki",
    "quote": "",
    "players": "20–40 orang (4–5 regu)",
    "dur": "90 menit",
    "tools": "Peta sketsa area, kompas, kartu petunjuk, boneka/karung \"korban\"",
    "steps": [
      "Pembina menyembunyikan satu \"korban\" (boneka atau karung berisi bantal) di titik tersembunyi dalam area latihan.",
      "Setiap regu menerima peta sketsa dan serangkaian 4 petunjuk arah (azimut kompas + jarak langkah) yang harus diikuti berurutan.",
      "Di setiap titik singgah ada pos kecil berisi petunjuk berikutnya plus tantangan cepat (misal simpul atau teka-teki).",
      "Regu yang menemukan korban pertama harus memindahkan \"korban\" ke posko dengan tandu darurat dari tongkat dan sarung.",
      "Pemenang adalah regu yang tiba di posko dengan korban dalam kondisi \"utuh\" dan waktu tercepat."
    ],
    "tips": "Tambahkan rintangan waktu, misalnya petunjuk kedaluwarsa setelah 15 menit agar regu tidak berleha-leha."
  },
  {
    "id": 47,
    "cat": "C",
    "name": "Perburuan Harta Karun Kompas",
    "quote": "",
    "players": "16–32 orang (4 regu)",
    "dur": "60 menit",
    "tools": "Kompas per regu, kartu azimut, kotak harta kecil",
    "steps": [
      "Pembina menyiapkan 5 titik tersembunyi, masing-masing ditandai dengan pita yang hanya terlihat dari jarak dekat.",
      "Setiap regu mendapat kartu berisi 5 pasang data: azimut derajat dan jumlah langkah dari titik start.",
      "Regu berjalan mengikuti azimut dengan kompas; di tiap titik yang benar mereka menemukan potongan peta.",
      "Setelah 5 potongan terkumpul, regu menyusun peta untuk menemukan lokasi harta karun utama.",
      "Regu tercepat menemukan kotak harta (berisi hadiah kecil atau lencana) menjadi pemenang."
    ],
    "tips": "Untuk pemula, gunakan azimut mata angin sederhana (utara, timur laut) sebelum memakai derajat."
  },
  {
    "id": 48,
    "cat": "C",
    "name": "Operasi Spionase: Kurir Rahasia",
    "quote": "",
    "players": "20–36 orang",
    "dur": "75 menit",
    "tools": "Amplop pesan rahasia, peta pos, tanda pengenal agen, peluit",
    "steps": [
      "Bagi peserta jadi dua tim: Tim Kurir dan Tim Intelijen Lawan yang berpatroli di area.",
      "Kurir harus mengantar 3 amplop pesan dari markas ke 3 pos berbeda tanpa tertangkap (disentuh) agen lawan.",
      "Jika tertangkap, kurir harus menyerahkan amplopnya dan kembali ke markas untuk mengambil misi baru.",
      "Setiap amplop yang sampai berisi kode yang harus dipecahkan di pos tujuan (misal sandi rumput atau morse sederhana).",
      "Tim Kurir menang jika semua pesan terkirim dan kode terpecahkan dalam waktu yang ditentukan."
    ],
    "tips": "Beri kurir \"nyawa\" berupa 2 gelang karet; tiap tertangkap satu gelang disita."
  },
  {
    "id": 49,
    "cat": "C",
    "name": "Ekspedisi Jejak Satwa",
    "quote": "",
    "players": "15–30 orang",
    "dur": "60 menit",
    "tools": "Kartu gambar jejak hewan, buku catatan, peta area",
    "steps": [
      "Sebelum permainan, pembina menyebar 12 kartu gambar jejak hewan (buatan dari kardus) di sekitar area.",
      "Setiap regu mendapat peta area dan daftar 12 hewan yang jejaknya harus ditemukan.",
      "Regu menjelajah area, mencatat lokasi setiap jejak, dan menebak hewan pemiliknya.",
      "Di 3 titik ada pos pembina yang memberi pertanyaan pengetahuan alam; jawaban benar dapat poin bonus.",
      "Regu dengan identifikasi terbanyak dan benar menjadi pemenang."
    ],
    "tips": "Ganti tema menjadi jejak tumbuhan obat atau jenis sampah untuk variasi edukasi lingkungan."
  },
  {
    "id": 50,
    "cat": "C",
    "name": "Lintas Pos Peta Buta",
    "quote": "",
    "players": "20–40 orang (4–5 regu)",
    "dur": "90 menit",
    "tools": "Peta buta (tanpa nama tempat), kompas, lembar kontrol",
    "steps": [
      "Setiap regu menerima peta buta area perkemahan: hanya garis kontur, jalan, dan sungai tanpa keterangan.",
      "Pembina memberi 6 koordinat sederhana (misal \"200 m timur laut dari jembatan bambu\") yang harus didatangi berurutan.",
      "Di setiap titik ada stempel pos; regu menempelkan stempel di lembar kontrol sebagai bukti kunjungan.",
      "Satu titik adalah \"pos jebakan\" yang koordinatnya sengaja samar — regu harus menafsir petunjuk tambahan dari pembina.",
      "Regu yang mengumpulkan 6 stempel tercepat dengan rute tercatat rapi menang."
    ],
    "tips": "Minta setiap regu menggambar ulang rute mereka di peta sebagai latihan orientasi."
  },
  {
    "id": 51,
    "cat": "C",
    "name": "Misi Air Bersih",
    "quote": "",
    "players": "20–32 orang (4 regu)",
    "dur": "75 menit",
    "tools": "Jeriken kosong, peta mata air/sumur, tali, saringan kain",
    "steps": [
      "Skenarionya: desa kehabisan air bersih, setiap regu harus menemukan sumber air di area latihan.",
      "Peta menunjukkan 4 calon sumber; hanya 2 yang benar-benar berisi air (ember tersembunyi).",
      "Regu menavigasi dengan kompas ke tiap sumber; di sumber yang benar mereka mengisi jeriken.",
      "Dalam perjalanan pulang, regu melewati pos penyaringan: air harus disaring dengan kain dan dinilai kejernihannya.",
      "Regu tercepat membawa air tersaring paling jernih ke posko menang."
    ],
    "tips": "Tambahkan tantangan: jeriken hanya boleh dibawa dengan tandu, tidak boleh dijinjing."
  },
  {
    "id": 52,
    "cat": "C",
    "name": "Perang Bendera Hutan",
    "quote": "",
    "players": "24–40 orang (2 tim besar)",
    "dur": "60 menit",
    "tools": "2 bendera tim, tali rafia batas area, peluit",
    "steps": [
      "Area dibagi dua wilayah; setiap tim menyembunyikan benderanya di wilayah sendiri (harus terlihat sebagian, tidak boleh dikubur).",
      "Pemain yang masuk wilayah lawan bisa \"ditangkap\" dengan disentuh; yang tertangkap duduk di penjara lawan.",
      "Tawanan bisa dibebaskan jika kawan satu tim berhasil menyentuhnya tanpa tertangkap.",
      "Tim menang jika berhasil merebut bendera lawan dan membawanya ke wilayah sendiri.",
      "Permainan dihentikan wasit jika waktu habis; tim dengan bendera lawan lebih dekat ke wilayahnya dinilai unggul."
    ],
    "tips": "Batasi area dengan tali rafia agar permainan tetap terkendali dan aman."
  },
  {
    "id": 53,
    "cat": "C",
    "name": "Jejak Rintangan Alam",
    "quote": "",
    "players": "16–32 orang (4 regu)",
    "dur": "45 menit",
    "tools": "Tali tambang, kardus rintangan, penanda rute",
    "steps": [
      "Pembina membuat rute 300–500 meter dengan 6 rintangan alam: merangkak di bawah tali, melompati parit kecil, memanjat gundukan, dan menyeberangi \"jembatan\" balok.",
      "Regu start dengan interval 3 menit agar tidak menumpuk di rintangan.",
      "Di 2 rintangan ada pos pembina yang menilai teknik (misal cara merangkak yang benar) dan memberi poin.",
      "Setiap anggota regu harus melewati semua rintangan; regu boleh membantu anggotanya.",
      "Pemenang ditentukan dari total waktu tercepat ditambah poin teknik."
    ],
    "tips": "Lakukan setelah hujan reda agar rintangan lumpur menambah keseruan (pastikan aman)."
  },
  {
    "id": 54,
    "cat": "C",
    "name": "Kurir Peta Estafet",
    "quote": "",
    "players": "20–40 orang (4–5 regu)",
    "dur": "50 menit",
    "tools": "Potongan peta per anggota, kompas, pos estafet",
    "steps": [
      "Setiap anggota regu hanya hafal/membawa satu potongan rute peta menuju pos berikutnya.",
      "Anggota pertama berlari ke pos 1 mengikuti potongannya, lalu \"mewariskan\" petunjuk lisan ke anggota kedua.",
      "Anggota kedua melanjutkan ke pos 2, begitu seterusnya sampai 5 pos terlewati.",
      "Tidak boleh ada yang melihat potongan milik anggota lain; komunikasi hanya lewat penjelasan lisan di titik serah terima.",
      "Regu yang semua anggotanya tiba di garis finis dengan urutan pos benar dan tercepat menang."
    ],
    "tips": "Acak urutan potongan peta agar regu harus berdiskusi dulu sebelum start."
  },
  {
    "id": 55,
    "cat": "C",
    "name": "Penyelamatan Sandi Morse Jarak Jauh",
    "quote": "",
    "players": "20–36 orang",
    "dur": "60 menit",
    "tools": "Senter/cermin isyarat, kartu morse, peta pos",
    "steps": [
      "Skenarionya: satu regu \"terjebak\" di bukit dan hanya bisa berkomunikasi lewat isyarat cahaya.",
      "Regu penolong tersebar di 3 pos dengan jarak pandang 100–200 meter.",
      "Pesan SOS dan koordinat lokasi dikirim estafet antarpos menggunakan senter (siang: cermin) dengan sandi morse.",
      "Setiap pos harus mencatat pesan dengan benar sebelum meneruskannya; kesalahan satu huruf bisa mengubah arti.",
      "Regu penolong yang tiba di lokasi \"korban\" dengan pesan yang benar dan tercepat menang."
    ],
    "tips": "Malam hari versi api unggun: gunakan nyala senter bergantian, suasananya jauh lebih seru."
  },
  {
    "id": 56,
    "cat": "C",
    "name": "Ekspedisi Sampah: Misi Bumi Bersih",
    "quote": "",
    "players": "20–40 orang (4–5 regu)",
    "dur": "60 menit",
    "tools": "Karung sampah, sarung tangan, peta zona, timbangan",
    "steps": [
      "Area latihan dibagi jadi 5 zona; setiap regu mendapat peta dan 1 zona tanggung jawab.",
      "Regu menjelajah zonanya memungut sampah; sampah dipilah jadi organik, plastik, dan kertas.",
      "Di tengah waktu ada pos tukar: regu boleh menukar 1 kg sampah plastik dengan petunjuk lokasi \"harta\" (sampah elektronik bernilai).",
      "Semua karung ditimbang di finis; sampah terpilah benar dapat pengali poin.",
      "Regu dengan poin tertinggi (berat × ketepatan pilah) menang dan area jadi bersih."
    ],
    "tips": "Libatkan warga sekitar sebagai juri kebersihan zona untuk dampak sosial."
  },
  {
    "id": 57,
    "cat": "C",
    "name": "Navigasi Bintang Malam",
    "quote": "",
    "players": "15–30 orang",
    "dur": "45 menit",
    "tools": "Peta langit sederhana, senter merah, penanda arah",
    "steps": [
      "Dilakukan malam hari di lapangan terbuka; setiap regu mendapat peta langit dan senter berfilter merah.",
      "Pembina menunjuk 5 benda langit (misal Biduk/Orion, Bintang Utara) yang harus ditemukan regu.",
      "Setiap benda langit yang teridentifikasi memberi petunjuk arah menuju satu pos darat.",
      "Regu berjalan ke pos-pos tersebut hanya bermodal arah mata angin dari bintang.",
      "Regu yang menemukan semua pos dan kembali dengan catatan pengamatan lengkap menang."
    ],
    "tips": "Jika mendung, ganti dengan navigasi suara: regu mengikuti bunyi peluit dari pos."
  },
  {
    "id": 58,
    "cat": "C",
    "name": "Perburuan Foto Alam",
    "quote": "",
    "players": "16–32 orang (4 regu)",
    "dur": "75 menit",
    "tools": "HP/kamera per regu, daftar 15 objek foto, peta area",
    "steps": [
      "Setiap regu mendapat daftar 15 objek alam yang harus difoto: misal sarang burung, jamur, jejak kaki hewan, bunga liar.",
      "Regu menjelajah area bebas; setiap foto harus memuat minimal 2 anggota regu sebagai bukti kehadiran.",
      "Ada 3 objek \"misteri\" yang hanya dideskripsikan samar (misal \"sesuatu yang hanya tumbuh di tempat lembap\").",
      "Kembali sebelum batas waktu; keterlambatan 5 menit mengurangi 1 poin.",
      "Juri menilai kelengkapan, kreativitas, dan ketepatan identifikasi objek."
    ],
    "tips": "Jadikan foto terbaik sebagai konten media sosial gugus depan."
  },
  {
    "id": 59,
    "cat": "C",
    "name": "Rute Amfibi: Darat dan Air",
    "quote": "",
    "players": "20–32 orang (4 regu)",
    "dur": "90 menit",
    "tools": "Peta, pelampung, tali, perahu karet (jika ada) atau ember apung",
    "steps": [
      "Rute terdiri dari 3 etape: jalan kaki bernavigasi kompas, menyeberangi sungai/kolam dangkal, dan lari finis.",
      "Etape air hanya boleh dilewati dengan alat apung yang dibuat regu dari bahan yang disediakan (jeriken, bambu).",
      "Di tengah sungai ada pos apung: regu harus mengambil bendera sebelum melanjutkan.",
      "Semua anggota harus tiba di finis; regu boleh bergantian mendorong alat apung.",
      "Pemenang adalah regu tercepat dengan seluruh anggota selamat dan alat apung utuh."
    ],
    "tips": "Pastikan kedalaman air maksimal selutut orang dewasa dan selalu ada pengawas bersertifikat."
  },
  {
    "id": 60,
    "cat": "C",
    "name": "Misi Koki Rimba",
    "quote": "",
    "players": "20–36 orang (4 regu)",
    "dur": "120 menit",
    "tools": "Peta bahan makanan, peralatan masak lapangan, kayu bakar",
    "steps": [
      "Setiap regu mendapat peta lokasi 5 \"depot\" bahan makanan yang tersebar di area.",
      "Regu menavigasi ke tiap depot untuk mengambil bahan (beras, telur, sayur, bumbu, buah) — tiap depot dijaga pos dengan kuis.",
      "Kuis benar = bahan penuh; kuis salah = bahan dikurangi setengah.",
      "Kembali ke perkemahan, regu memasak 1 menu lengkap dengan api dari kayu bakar dalam waktu 45 menit.",
      "Juri menilai rasa, kebersihan masak, dan kekompakan; navigasi tercepat dapat poin bonus."
    ],
    "tips": "Wajibkan satu menu dari bahan liar yang aman (misal daun singkong) sebagai tantangan tambahan."
  },
  {
    "id": 61,
    "cat": "C",
    "name": "Jejak Sejarah Desa",
    "quote": "",
    "players": "20–40 orang (4–5 regu)",
    "dur": "90 menit",
    "tools": "Peta desa, daftar tokoh/tempat bersejarah, buku catatan",
    "steps": [
      "Pembina bekerja sama dengan perangkat desa menentukan 6 titik bersejarah (tugu, rumah tua, makam pahlawan, situs).",
      "Setiap regu mendapat peta dan misi: mewawancarai warga di tiap titik tentang sejarahnya.",
      "Hasil wawancara dicatat; di 2 titik ada sesepuh yang memberi cerita plus pertanyaan lisan.",
      "Regu menyusun laporan mini 1 halaman per titik yang dikunjungi.",
      "Laporan dinilai kelengkapan fakta dan kesopanan wawancara; regu terbaik menang."
    ],
    "tips": "Minta izin perangkat desa dulu dan bekali regu surat pengantar resmi gugus depan."
  },
  {
    "id": 62,
    "cat": "C",
    "name": "Operasi Jembatan Darurat",
    "quote": "",
    "players": "20–32 orang (4 regu)",
    "dur": "100 menit",
    "tools": "Tali pramuka, tongkat/bambu, peta lokasi sungai",
    "steps": [
      "Skenarionya: banjir memutus akses dusun; setiap regu harus membangun jembatan darurat dari tali dan bambu.",
      "Regu menavigasi dengan peta ke lokasi \"sungai\" (parit atau area yang ditandai) sejauh 500 meter.",
      "Di lokasi, regu membangun jembatan tali sederhana dalam waktu 40 menit; pembina menilai simpul dan kekuatan.",
      "Jembatan diuji: minimal 3 anggota regu harus bisa menyeberang bergantian tanpa runtuh.",
      "Regu tercepat membangun jembatan yang lolos uji kekuatan menang."
    ],
    "tips": "Ini mini-pionering; nilai juga kerapian simpul pangkal, jangkar, dan palang."
  },
  {
    "id": 63,
    "cat": "C",
    "name": "Lomba Orienteering Mini",
    "quote": "",
    "players": "16–32 orang",
    "dur": "45 menit",
    "tools": "Peta orienteering sederhana, kompas, kartu kontrol, stempel",
    "steps": [
      "Pembina membuat peta sederhana area dengan 8 titik kontrol bernomor acak.",
      "Setiap peserta/regu mendapat kartu kontrol dan harus mengunjungi titik-titik sesuai urutan yang diundi.",
      "Start dilakukan interval 1 menit; peserta dilarang mengikuti peserta lain (jarak minimal 20 meter).",
      "Di tiap titik ada stempel unik yang dicap ke kartu kontrol.",
      "Pemenang adalah yang menyelesaikan semua titik dengan waktu tercepat dan cap lengkap."
    ],
    "tips": "Ini pengenalan olahraga orienteering; gunakan titik dengan warna mencolok agar mudah dikenali pemula."
  },
  {
    "id": 64,
    "cat": "C",
    "name": "Misi Penjaga Hutan",
    "quote": "",
    "players": "24–40 orang",
    "dur": "80 menit",
    "tools": "Peta patroli, kartu pelanggaran, teropong mainan, peluit",
    "steps": [
      "Sebagian peserta jadi \"Penjaga Hutan\", sebagian jadi \"Perambah\" yang menyebar dan melakukan 5 jenis \"pelanggaran\" (membuang sampah, menebang ranting, menyalakan api).",
      "Penjaga berpatroli mengikuti rute peta; setiap pelanggaran yang ditemukan dan didokumentasikan dapat poin.",
      "Perambah yang tertangkap basah harus \"disidang\" di pos: menjelaskan pelanggarannya dan janji perbaikannya.",
      "Perambah boleh bersembunyi, tapi tidak boleh keluar dari batas area yang ditandai.",
      "Tim Penjaga dengan dokumentasi pelanggaran terbanyak dan tersistematis menang."
    ],
    "tips": "Akhiri dengan diskusi: hubungkan ke materi pelestarian lingkungan dan SKU yang relevan."
  },
  {
    "id": 65,
    "cat": "C",
    "name": "Ekspedisi Puncak: Simulasi Pendakian",
    "quote": "",
    "players": "20–36 orang (4 regu)",
    "dur": "120 menit",
    "tools": "Peta rute, kartu ceklis logistik, tali, pos ketinggian",
    "steps": [
      "Rute 1–2 km dibagi jadi 4 \"ketinggian\" (basecamp, pos 1, pos 2, puncak) dengan jarak dan tanjakan bervariasi.",
      "Setiap regu membawa \"logistik\" (ransel berisi botol air) yang tidak boleh berkurang isinya secara tidak wajar.",
      "Di tiap pos ada tantangan: pos 1 kuis navigasi, pos 2 P3K (simulasi kram), pos 3 membuat bivak darurat 10 menit.",
      "Regu harus mengatur tempo: ada batas waktu minimum antarpos agar tidak kebut-kebutan (melatih manajemen energi).",
      "Regu yang mencapai puncak dengan logistik utuh, semua tantangan lolos, dan catatan perjalanan rapi menang."
    ],
    "tips": "Tekankan prinsip \"tidak ada yang ditinggal\": regu yang anggotanya tidak lengkap di puncak didiskualifikasi dari juara."
  },
  {
    "id": 66,
    "cat": "D",
    "name": "Duel Simpul Kilat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali pramuka 1 meter per orang, peluit",
    "steps": [
      "Semua peserta berbaris memegang tali; pembina menyebutkan satu simpul (mis. simpul pangkal, jangkar, mati).",
      "Dalam 30 detik peserta harus membuat simpul tersebut dengan benar.",
      "Pembina memeriksa; yang salah atau tidak selesai tereliminasi ke barisan penonton.",
      "Tiap ronde simpulnya berganti dan waktunya dipersingkat 5 detik.",
      "Peserta terakhir yang bertahan menjadi juara duel."
    ],
    "tips": "Ronde final: buat simpul dengan mata tertutup atau tangan di belakang punggung."
  },
  {
    "id": 67,
    "cat": "D",
    "name": "Estafet Semaphore Berantai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 bendera semaphore per regu, kartu kata",
    "steps": [
      "Setiap regu berbaris; anggota pertama mengambil kartu berisi satu kata.",
      "Anggota pertama mengirim kata itu dengan semaphore ke anggota kedua yang berjarak 10 meter.",
      "Anggota kedua mencatat lalu meneruskan ke anggota ketiga, begitu seterusnya sampai ujung barisan.",
      "Anggota terakhir menuliskan kata yang diterima di papan; ejaan harus tepat.",
      "Regu tercepat dengan kata benar mendapat poin; mainkan 3 kata untuk akumulasi."
    ],
    "tips": "Untuk pemula gunakan kata 4–5 huruf dulu sebelum naik ke kata sulit."
  },
  {
    "id": 68,
    "cat": "D",
    "name": "Lempar Tepat Sasaran",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "3 bola kecil/beanbag per orang, target lingkaran dari kardus",
    "steps": [
      "Buat 3 target lingkaran dengan jarak 3, 5, dan 7 meter, masing-masing bernilai 10, 20, 30 poin.",
      "Setiap peserta mendapat 3 kali lemparan; boleh memilih target mana saja.",
      "Lemparan harus dari belakang garis; menyentuh garis membuat lemparan hangus.",
      "Hitung total poin tiap peserta setelah semua melempar.",
      "Tiga poin tertinggi maju ke babak final dengan jarak target ditambah 2 meter."
    ],
    "tips": "Ganti bola dengan kaus kaki berisi beras agar aman dimainkan di dalam ruangan."
  },
  {
    "id": 69,
    "cat": "D",
    "name": "Balap Tandu P3K",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 tongkat + 1 sarung/kain per regu, boneka \"korban\"",
    "steps": [
      "Setiap regu membuat tandu darurat dari 2 tongkat dan sarung dalam waktu maksimal 5 menit.",
      "Pembina menilai kekuatan dan kerapian ikatan tandu sebelum balapan.",
      "Satu anggota jadi \"korban\" berbaring di tandu; 4 anggota lain menggotong melewati rute 50 meter berkelok.",
      "Korban tidak boleh menyentuh tanah; jika jatuh, regu harus berhenti dan memperbaikinya.",
      "Regu tercepat mencapai finis dengan tandu utuh dan korban \"selamat\" menang."
    ],
    "tips": "Tambahkan pos di tengah rute: regu harus memasang perban segitiga di lengan korban sebelum lanjut."
  },
  {
    "id": 70,
    "cat": "D",
    "name": "Kompas Buta: Jalan Lurus",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kompas per orang, penutup mata, patok finis",
    "steps": [
      "Peserta berdiri di garis start, menentukan azimut ke patok finis dengan kompas (mis. 45°).",
      "Mata ditutup; peserta berjalan 30 langkah mengikuti ingatan arah kompas tanpa melihat.",
      "Pembina mengawasi keamanan; rute harus di lapangan datar tanpa lubang.",
      "Setelah 30 langkah, peserta membuka penutup mata dan mengukur penyimpangannya dari garis lurus ideal.",
      "Peserta dengan penyimpangan terkecil menang; ulangi 3 ronde dengan azimut berbeda."
    ],
    "tips": "Latihan lanjutan: kombinasikan dengan hitungan langkah ganda untuk mengukur jarak tempuh."
  },
  {
    "id": 71,
    "cat": "D",
    "name": "Menara Sedotan Pionering Mini",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "30 sedotan + 1 m selotip per regu, kelereng",
    "steps": [
      "Setiap regu membangun menara dari sedotan dan selotip setinggi mungkin dalam 12 menit.",
      "Hanya boleh memakai bahan yang disediakan; selotip tidak boleh ditempel ke meja.",
      "Setelah waktu habis, menara harus berdiri sendiri selama 10 detik.",
      "Kelereng diletakkan di puncak; menara yang bertahan dengan kelereng dapat poin bonus.",
      "Menara tertinggi yang bertahan menjadi pemenang."
    ],
    "tips": "Versi Pramuka asli: ganti sedotan dengan ranting dan tali untuk latihan ikatan palang mini."
  },
  {
    "id": 72,
    "cat": "D",
    "name": "Tebak Sandi Morse Audio",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Peluit, kartu alfabet morse per orang",
    "steps": [
      "Pembina meniup peluit membentuk pola morse sebuah kata (titik = tiupan pendek, strip = tiupan panjang).",
      "Peserta mencatat pola yang didengar lalu menerjemahkannya dengan kartu morse.",
      "Kata pertama yang benar dan tercepat mengangkat tangan dapat poin.",
      "Mainkan 8–10 kata dengan tingkat kesulitan bertambah (dari 3 huruf sampai 8 huruf).",
      "Peserta dengan poin terbanyak menjadi juara."
    ],
    "tips": "Variasikan media: ketukan meja, kedipan senter, atau tepukan tangan."
  },
  {
    "id": 73,
    "cat": "D",
    "name": "Jembatan Keseimbangan Balok",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Balok kayu/bambu panjang 4 m, stopwatch, beanbag",
    "steps": [
      "Balok diletakkan 30 cm di atas tanah; peserta berjalan di atasnya dari ujung ke ujung.",
      "Di tengah balok, peserta harus berhenti, jongkok, mengambil beanbag, lalu berdiri lagi.",
      "Waktu dihitung dengan stopwatch; jatuh dari balok berarti mengulang dari awal.",
      "Setiap peserta punya 2 kesempatan; waktu terbaik yang dicatat.",
      "Waktu tercepat menang; jika seri, yang tanpa jatuh menang."
    ],
    "tips": "Tambah tantangan: bawa segelas air tanpa tumpah selama menyeberang."
  },
  {
    "id": 74,
    "cat": "D",
    "name": "Ikatan Tali Estafet Buta",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali panjang per regu, penutup mata",
    "steps": [
      "Setiap regu berbaris; semua anggota kecuali yang paling depan memakai penutup mata.",
      "Anggota pertama (melihat) memberi instruksi lisan agar regu membentuk simpul/ikatan tertentu pada tali.",
      "Yang bertutup mata hanya boleh mengikuti instruksi suara, tidak boleh mengintip.",
      "Waktu maksimal 5 menit per ikatan; pembina menilai kebenaran hasilnya.",
      "Regu tercepat membuat 3 ikatan berbeda dengan benar menang."
    ],
    "tips": "Ini melatih komunikasi dan kepemimpinan; putar peran agar semua merasakan jadi pemberi instruksi."
  },
  {
    "id": 75,
    "cat": "D",
    "name": "Bidik Kaleng Bocce Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "1 bola target + 3 bola per pemain (warna beda tiap regu), lapangan datar",
    "steps": [
      "Lempar bola target ke jarak 5–8 meter; itulah titik sasaran ronde ini.",
      "Setiap pemain melempar 3 bolanya bergantian, berusaha sedekat mungkin ke bola target.",
      "Boleh menyenggol bola lawan agar menjauh — itu bagian strateginya.",
      "Setelah semua melempar, hanya regu dengan bola terdekat yang dapat poin sejumlah bola mereka yang lebih dekat dari bola lawan terdekat.",
      "Mainkan 5 ronde; total poin tertinggi menang."
    ],
    "tips": "Mainkan di tanah berpasir agar bola tidak menggelinding terlalu jauh."
  },
  {
    "id": 76,
    "cat": "D",
    "name": "Rakit Pelampung Kertas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "1 lembar koran + selotip per regu, baskom air, koin/baut",
    "steps": [
      "Setiap regu membuat perahu/rakit dari 1 lembar koran dan selotip dalam 10 menit.",
      "Rakit diapungkan di baskom; harus mengapung minimal 30 detik tanpa bantuan.",
      "Beban ditambah satu per satu (koin atau baut); catat jumlah beban sebelum tenggelam.",
      "Rakit yang mengapung dinilai juga kerapian lipatannya.",
      "Pemenang adalah rakit yang menahan beban terbanyak; jika seri, yang paling rapi menang."
    ],
    "tips": "Diskusikan prinsip daya apung setelahnya — ini fisika sederhana yang menyenangkan."
  },
  {
    "id": 77,
    "cat": "D",
    "name": "Peta Kilat: Hafal dan Gambar",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "1 peta contoh, kertas dan spidol per orang",
    "steps": [
      "Pembina memajang peta sederhana (jalan, sungai, 5 titik penting) selama 60 detik untuk dihafal.",
      "Peta ditutup; peserta menggambar ulang peta dari ingatan dalam 5 menit.",
      "Penilaian: kelengkapan 5 titik (50%), posisi relatif benar (30%), kerapian (20%).",
      "Peserta boleh memberi nama sendiri pada titiknya asal posisinya tepat.",
      "Skor tertinggi menang; pamerkan 3 gambar terbaik untuk dibahas bersama."
    ],
    "tips": "Naikkan level: peta hanya boleh dilihat 30 detik, atau tambah jadi 8 titik."
  },
  {
    "id": 78,
    "cat": "D",
    "name": "Operasi Bidik Laser Senter",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter per orang, target kertas di dinding, ruangan gelap",
    "steps": [
      "Dilakukan di ruangan gelap; target berupa 5 lingkaran bernomor ditempel di dinding jarak 5 meter.",
      "Pembina menyebutkan urutan nomor (mis. 3-1-4); peserta harus menyorotkan senter ke lingkaran sesuai urutan.",
      "Tiap ronde urutannya makin panjang (3 angka, lalu 5, lalu 7).",
      "Salah sorot atau salah urutan mengurangi poin; kecepatan juga dinilai.",
      "Poin tertinggi setelah 5 ronde menang."
    ],
    "tips": "Cocok untuk malam hari di perkemahan; ganti nomor dengan huruf sandi untuk latihan tambahan."
  },
  {
    "id": 79,
    "cat": "D",
    "name": "Lomba Memasang Tenda Kilat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "1 tenda dome per regu (frame, kain, pasak)",
    "steps": [
      "Setiap regu menerima tenda yang sudah dibongkar dan dimasukkan ke tasnya.",
      "Pada aba-aba, regu berlomba memasang tenda sampai berdiri sempurna dan pintu bisa ditutup.",
      "Pembina memeriksa: rangka terkunci, pasak menancap, tali pengencang terpasang.",
      "Tenda yang belum sempurna harus diperbaiki sebelum waktu dicatat.",
      "Regu tercepat dengan tenda sempurna menang; ada penalti 30 detik per cacat yang ditemukan."
    ],
    "tips": "Ronde kedua: bongkar dan lipat kembali ke tasnya — kerapian melipat juga dinilai."
  },
  {
    "id": 80,
    "cat": "D",
    "name": "Jerat Simpul: Tebak dari Raba",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "8 tali bersimpul berbeda dalam kantong kain, penutup mata",
    "steps": [
      "Siapkan 8 tali yang masing-masing sudah dibuat satu jenis simpul (pangkal, jangkar, mati, hidup, anyam, dll), dimasukkan ke kantong.",
      "Peserta dengan mata tertutup merogoh kantong dan meraba satu tali.",
      "Dalam 20 detik ia harus menebak nama simpulnya hanya dari rabaan.",
      "Tebakan benar dapat 10 poin; boleh minta \"petunjuk fungsi\" tapi poin jadi 5.",
      "Setiap peserta meraba 4 tali; poin tertinggi menang."
    ],
    "tips": "Ini cara seru menguji hafalan simpul tanpa melihat — kemampuan penting saat gelap di lapangan."
  },
  {
    "id": 81,
    "cat": "D",
    "name": "Estafet P3K: Balut Berantai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Perban gulung, mitela, plester per regu",
    "steps": [
      "Setiap regu berbaris; di ujung barisan ada \"korban\" dengan 4 kartu luka (luka kepala, lengan patah, kaki terkilir, mimisan).",
      "Anggota pertama lari ke korban, memasang balutan untuk luka pertama sesuai kartu, lalu kembali.",
      "Anggota kedua melanjutkan luka kedua, begitu seterusnya sampai 4 luka tertangani.",
      "Pembina menilai kebenaran teknik balutan di akhir (bukan kecepatan semata).",
      "Skor = kecepatan (40%) + kebenaran teknik (60%); tertinggi menang."
    ],
    "tips": "Sediakan kartu panduan P3K di pos korban agar peserta belajar sambil bermain."
  },
  {
    "id": 82,
    "cat": "D",
    "name": "Lempar Lasso Ban",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali laso (tali dengan simpul jerat) per orang, 3 patok target",
    "steps": [
      "Setiap peserta membuat simpul jerat hidup di ujung talinya menjadi laso.",
      "Tiga patok target dipasang pada jarak 3, 5, dan 7 meter dengan poin 10, 20, 30.",
      "Setiap peserta mendapat 5 lemparan; laso harus mengait patok agar poin sah.",
      "Teknik yang dinilai: putaran laso stabil sebelum dilempar.",
      "Total poin tertinggi menang; babak final memakai patok berjalan (dibawa pembina pelan-pelan)."
    ],
    "tips": "Latihan koordinasi mata-tangan ini juga melatih kesabaran; jangan buru-buru melempar."
  },
  {
    "id": 83,
    "cat": "D",
    "name": "Sandi Semaphore Kilat Berpasangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Bendera semaphore per pasangan, daftar kata",
    "steps": [
      "Peserta berpasangan; satu jadi pengirim, satu jadi penerima, jarak 8 meter saling berhadapan.",
      "Pembina menunjukkan kata ke pengirim; pengirim mengirim huruf per huruf dengan semaphore.",
      "Penerima mencatat hurufnya; boleh minta \"ulangi huruf ke-3\" maksimal 2 kali per kata.",
      "Setiap kata benar dapat poin sesuai jumlah hurufnya; 5 kata per ronde.",
      "Pasangan dengan poin tertinggi menang; lalu tukar peran untuk ronde kedua."
    ],
    "tips": "Kata-katanya ambil dari istilah kepramukaan (mis. \"dasadarma\", \"satya\") agar sekaligus hafalan."
  },
  {
    "id": 84,
    "cat": "D",
    "name": "Menara Kartu Keseimbangan Tim",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "1 pak kartu remi per regu",
    "steps": [
      "Setiap regu membangun menara kartu setinggi mungkin dalam 10 menit.",
      "Aturannya: setiap anggota hanya boleh menaruh maksimal 5 kartu, lalu harus bergantian.",
      "Tidak boleh ada penyangga selain kartu; menara harus berdiri di atas meja.",
      "Saat waktu habis, menara harus bertahan 15 detik tanpa disentuh.",
      "Menara tertinggi yang bertahan menang; jika runtuh saat penilaian, tinggi terakhir yang sah adalah 0."
    ],
    "tips": "Melatih kesabaran dan tangan yang tenang — cocok sebagai permainan penenang setelah aktivitas fisik."
  },
  {
    "id": 85,
    "cat": "D",
    "name": "Navigasi Langkah Ganda",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kompas, meteran, patok, kartu misi",
    "steps": [
      "Setiap peserta mengkalibrasi dulu: jalan 20 langkah ganda, ukur jaraknya dengan meteran, catat.",
      "Pembina memberi kartu misi: mis. \"dari start, azimut 60° sejauh 40 meter, lalu azimut 180° sejauh 25 meter\".",
      "Peserta mengubah meter menjadi jumlah langkah ganda versi kakinya sendiri, lalu berjalan dengan kompas.",
      "Di titik akhir yang dihitung, peserta menancapkan patok namanya.",
      "Pemenang adalah patok yang paling dekat dengan titik target sebenarnya (diukur pembina)."
    ],
    "tips": "Ini keterampilan inti navigasi darat; yang menang biasanya yang paling teliti mengkalibrasi."
  },
  {
    "id": 86,
    "cat": "D",
    "name": "Duel Morse Ketuk Meja",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Meja, kartu morse per orang",
    "steps": [
      "Dua peserta duduk berhadapan di meja; satu mengetuk pola morse sebuah kata, lawannya menerjemahkan.",
      "Pengetuk mendapat kata rahasia dari pembina; ia mengetuk titik (ketukan ringan) dan strip (ketukan keras).",
      "Penerjemah menuliskan hurufnya; waktu maksimal 60 detik per kata.",
      "Benar = pengetuk dan penerjemah sama-sama dapat poin (melatih kerja sama, bukan saling menjatuhkan).",
      "Sistem gugur: pasangan dengan poin terendah tiap ronde tereliminasi sampai tersisa juara."
    ],
    "tips": "Ronde final tanpa kartu morse — hanya mengandalkan hafalan."
  },
  {
    "id": 87,
    "cat": "D",
    "name": "Rintangan Keseimbangan Bambu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "5 bambu panjang, 3 ember air, stopwatch",
    "steps": [
      "Susun 5 bambu sejajar sebagai jalur selebar 40 cm sepanjang 10 meter.",
      "Peserta berjalan di atas bambu sambil membawa ember berisi air setengah penuh.",
      "Di tengah jalur ada \"pos angin\": pembina mengipasi dengan kardus untuk mengganggu keseimbangan.",
      "Air yang tumpah diukur; setiap 100 ml tumpah = penalti 10 detik.",
      "Waktu tercepat termasuk penalti menang; jatuh dari bambu berarti mengulang."
    ],
    "tips": "Pastikan bambu tidak licin dan area jatuh aman (matras atau tanah empuk)."
  },
  {
    "id": 88,
    "cat": "D",
    "name": "Membuat Api Tanpa Korek",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Baterai + sabut baja / kaca pembesar, tinder kering, kayu kecil",
    "steps": [
      "Setiap regu mendapat satu metode: baterai dan sabut baja, atau kaca pembesar (siang hari).",
      "Regu harus menyalakan tinder (kapas/sabut kelapa kering) lalu membesarkan api sampai bisa membakar ranting.",
      "Api dinyatakan sah jika bisa menyalakan selembar kertas dalam 30 detik.",
      "Dilarang memakai korek/matches; pembina mengawasi penuh dan menyiapkan air pemadam.",
      "Regu tercepat menyalakan api yang sah menang; semua api dipadamkan sempurna setelahnya."
    ],
    "tips": "Lakukan di area terbuka jauh dari tenda; jadikan momen diskusi tentang etika api di alam."
  },
  {
    "id": 89,
    "cat": "D",
    "name": "Lempar Tangkap Bola Berpola",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "3 bola kecil per regu",
    "steps": [
      "Regu berdiri melingkar; satu bola dilempar dengan pola: lempar ke lawan sambil menyebut namanya.",
      "Setelah 1 menit lancar, tambah bola kedua dengan arah berlawanan.",
      "Setelah 2 menit, tambah bola ketiga; siapa pun yang menjatuhkan bola, regunya mengulang pola dari awal.",
      "Tiap 3 menit, lingkaran melebar 1 langkah ke belakang.",
      "Regu yang bertahan paling lama tanpa menjatuhkan bola (maksimal 10 menit) menang."
    ],
    "tips": "Variasikan dengan lemparan memantul ke tanah sekali sebelum ditangkap."
  },
  {
    "id": 90,
    "cat": "D",
    "name": "Tantangan 60 Detik Serba Bisa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Daftar 6 pos keterampilan, stopwatch, kartu skor",
    "steps": [
      "Siapkan 6 pos: simpul pangkal, 5 huruf semaphore, balut luka lengan, azimut kompas, lipat tenda kilat, 3 lemparan tepat sasaran.",
      "Setiap peserta punya total 60 detik per pos untuk menyelesaikan tantangannya.",
      "Setiap pos lolos sempurna = 10 poin; lolos sebagian = 5 poin; gagal = 0.",
      "Peserta berputar ke semua pos; total maksimal 60 poin.",
      "Skor tertinggi menang; umumkan juga \"juara per pos\" agar banyak yang dapat apresiasi."
    ],
    "tips": "Jadikan ini pos evaluasi keterampilan anggota secara berkala."
  },
  {
    "id": 91,
    "cat": "E",
    "name": "Detektif Suara",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain penutup mata",
    "steps": [
      "Semua peserta duduk melingkar di dalam ruangan, satu orang ditutup matanya di tengah sebagai detektif.",
      "Pembina menunjuk diam-diam satu peserta untuk mengeluarkan satu bunyi (misalnya menirukan suara hewan atau ketukan meja).",
      "Detektif membuka tutup mata dan harus menebak siapa yang mengeluarkan bunyi dalam dua kali kesempatan.",
      "Jika benar, si pembuat bunyi menjadi detektif berikutnya; jika salah, detektif mendapat satu kesempatan lagi dengan bunyi berbeda.",
      "Lanjutkan 5–6 ronde dengan variasi bunyi yang makin sulit ditebak."
    ],
    "tips": "Larang peserta mengubah posisi duduk supaya detektif tidak bisa menebak dari gerakan."
  },
  {
    "id": 92,
    "cat": "E",
    "name": "Cerita Berantai Satu Kata",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada (opsional: perekam HP untuk memutar ulang)",
    "steps": [
      "Peserta duduk melingkar.",
      "Orang pertama mengucapkan satu kata pembuka cerita, misalnya \"Kemarin\".",
      "Orang berikutnya menambahkan satu kata, misalnya \"kami\", lalu berikutnya \"tersesat\" — sehingga terbentuk kalimat cerita.",
      "Cerita harus tetap nyambung; yang mengucapkan kata yang merusak alur atau diam lebih dari 5 detik keluar satu ronde.",
      "Setelah satu putaran penuh, baca ulang ceritanya dari awal — biasanya hasilnya kocak dan jadi bahan tawa bersama."
    ],
    "tips": "Tentukan tema di awal (misalnya \"petualangan Pramuka\") supaya ceritanya tidak ngawur ke mana-mana."
  },
  {
    "id": 93,
    "cat": "E",
    "name": "Tebak Benda Dalam Kotak",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kardus dengan lubang untuk tangan, 8–10 benda kecil (sendok, sikat gigi, kunci, dll.)",
    "steps": [
      "Masukkan benda-benda ke dalam kardus yang sudah dilubangi dua sisi untuk memasukkan tangan.",
      "Peserta maju satu per satu, memasukkan kedua tangan tanpa mengintip, dan meraba satu benda selama 30 detik.",
      "Ia menuliskan tebakannya di kertas tanpa memberi tahu peserta lain.",
      "Setelah semua mendapat giliran, buka kardus dan cocokkan jawaban.",
      "Peserta dengan tebakan benar terbanyak menang."
    ],
    "tips": "Pilih benda-benda yang bentuknya mirip (misalnya sendok dan garpu) untuk menaikkan level kesulitan."
  },
  {
    "id": 94,
    "cat": "E",
    "name": "Peta Buta Ruangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan pensil per peserta, penutup mata",
    "steps": [
      "Satu peserta ditutup matanya lalu dituntun berjalan mengelilingi ruangan oleh pembina selama 1 menit (melewati meja, pintu, jendela).",
      "Setelah itu ia duduk dan diminta menggambar denah ruangan berdasarkan ingatan sentuhan dan suaranya.",
      "Peserta lain menilai: setiap perabot yang posisinya benar mendapat 10 poin.",
      "Giliran berganti ke 3–4 peserta lain dengan rute tuntunan yang berbeda.",
      "Penggambar denah dengan skor tertinggi menang."
    ],
    "tips": "Tambahkan 2–3 benda \"jebakan\" (misalnya tas yang digeser) di tengah rute supaya ingatannya diuji."
  },
  {
    "id": 95,
    "cat": "E",
    "name": "Lomba Sedotan Balap Kapas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Sedotan per peserta, gumpalan kapas/tisu, meja panjang atau lantai",
    "steps": [
      "Buat lintasan balap di atas meja atau lantai dengan garis start dan finis (sekitar 2 meter).",
      "Tiap peserta mendapat satu sedotan dan satu gumpalan kapas.",
      "Dengan aba-aba mulai, peserta meniup kapasnya lewat sedotan agar bergerak ke garis finis — tidak boleh menyentuh kapas dengan tangan.",
      "Kapas yang keluar lintasan harus dikembalikan ke titik keluarnya.",
      "Peserta tercepat mencapai finis menang; mainkan sistem gugur jika peserta banyak."
    ],
    "tips": "Buat rintangan dari buku yang disusun sebagai \"terowongan\" supaya tiupannya harus lebih terkontrol."
  },
  {
    "id": 96,
    "cat": "E",
    "name": "Siapa Bosnya?",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta duduk melingkar, satu orang keluar ruangan sebagai penebak.",
      "Peserta yang tersisa diam-diam menunjuk satu orang sebagai \"bos\" — semua harus meniru gerakan bos.",
      "Bos mulai melakukan gerakan (tepuk tangan, angguk kepala, goyang bahu) dan yang lain mengikutinya.",
      "Bos berganti gerakan setiap beberapa detik, pengikut harus segera menyesuaikan tanpa melihat langsung ke arah bos.",
      "Penebak masuk dan punya tiga kesempatan menebak siapa bosnya; jika benar, bos menjadi penebak berikutnya."
    ],
    "tips": "Atur agar bos duduk tidak di posisi mencolok dan pengikut meliriknya sekilas saja supaya penebak terkecoh."
  },
  {
    "id": 97,
    "cat": "E",
    "name": "Tebak Lagu Bersiul",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Daftar judul lagu (lagu Pramuka/nasional), kertas skor",
    "steps": [
      "Bagi peserta menjadi dua kelompok.",
      "Satu perwakilan mengambil undian judul lagu lalu menyanyikannya dengan cara bersiul (tanpa lirik, tanpa senandung).",
      "Kelompoknya harus menebak judul lagu dalam waktu 1 menit; benar dapat 10 poin.",
      "Jika gagal, kelompok lawan boleh mencuri jawaban dan mendapat 5 poin.",
      "Setelah 8–10 lagu, kelompok dengan poin terbanyak menang."
    ],
    "tips": "Khususkan daftar lagunya lagu-lagu Pramuka dan daerah supaya sekalian mengasah wawasan."
  },
  {
    "id": 98,
    "cat": "E",
    "name": "Menara Kartu Regu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Satu set kartu remi/domino per kelompok",
    "steps": [
      "Bagi peserta menjadi kelompok 4–6 orang, tiap kelompok mendapat satu set kartu.",
      "Tugasnya: membangun menara kartu setinggi mungkin dalam waktu 10 menit.",
      "Aturannya: tidak boleh memakai perekat, penjepit, atau alat bantu apa pun — hanya kartu.",
      "Menara harus bisa berdiri sendiri selama 10 detik saat waktu habis untuk diukur tingginya.",
      "Kelompok dengan menara tertinggi dan tetap berdiri menang."
    ],
    "tips": "Di tengah waktu (menit ke-5), wajibkan tiap kelompok menukar 5 kartunya dengan kelompok lain supaya strateginya diuji."
  },
  {
    "id": 99,
    "cat": "E",
    "name": "Bisik Gambar Berantai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan spidol/pensil per peserta",
    "steps": [
      "Semua peserta duduk berbaris atau melingkar, masing-masing memegang kertas dan alat tulis.",
      "Tiap orang menulis satu kata benda di kertasnya (misalnya \"gunung\"), lalu mengoper kertas ke kanan.",
      "Penerima menggambar kata yang tertulis itu, melipat tulisan aslinya hingga tak terlihat, lalu mengoper lagi.",
      "Penerima berikutnya menuliskan tebakan kata dari gambar yang dilihatnya, melipat gambarnya, dan mengoper lagi.",
      "Setelah kertas kembali ke pemilik awal, buka lipatannya satu per satu — perubahan kata dan gambar yang kocak dijamin mengundang tawa."
    ],
    "tips": "Batasi waktu tiap giliran hanya 30 detik supaya gambarnya spontan dan hasilnya makin lucu."
  },
  {
    "id": 100,
    "cat": "E",
    "name": "Kursi Musik Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kursi (jumlah peserta dikurangi satu), HP/speaker untuk musik atau yel-yel",
    "steps": [
      "Susun kursi melingkar menghadap keluar, jumlahnya satu lebih sedikit dari peserta.",
      "Saat musik/yel-yel berbunyi, peserta berjalan mengelilingi kursi.",
      "Saat musik berhenti, semua berebut duduk; yang tidak kebagian kursi keluar satu ronde.",
      "Setiap ronde, kurangi satu kursi lagi.",
      "Pemenangnya adalah peserta terakhir yang berhasil duduk."
    ],
    "tips": "Ganti musik dengan pembina yang menyanyikan yel-yel regu — berhentinya jadi tak terduga dan lebih seru."
  },
  {
    "id": 101,
    "cat": "E",
    "name": "Tebak Profesi Pantomim",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas undian berisi nama profesi",
    "steps": [
      "Tulis berbagai profesi di kertas undian (dokter, petani, pemadam kebakaran, pembina Pramuka, dll.).",
      "Bagi peserta menjadi dua kelompok yang duduk berhadapan.",
      "Perwakilan kelompok mengambil undian dan memperagakan profesi itu tanpa suara selama 1 menit.",
      "Kelompoknya menebak; jawaban benar dalam 30 detik pertama dapat 20 poin, setelahnya 10 poin.",
      "Giliran bergantian; kelompok dengan poin tertinggi menang."
    ],
    "tips": "Tambahkan kategori \"profesi masa depan\" (misalnya YouTuber, pilot drone) supaya anak-anak lebih antusias."
  },
  {
    "id": 102,
    "cat": "E",
    "name": "Rantai Kata Terlarang",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan spidol untuk menulis kata terlarang",
    "steps": [
      "Tentukan satu kata terlarang, misalnya \"ya\", \"tidak\", atau \"Pramuka\".",
      "Pembina mengajukan pertanyaan-pertanyaan jebakan ke tiap peserta secara bergiliran (\"Kamu anggota Pramuka, kan?\").",
      "Peserta harus menjawab tanpa mengucapkan kata terlarang dan tanpa jeda lebih dari 3 detik.",
      "Yang keceplosan mengucapkan kata terlarang atau terlalu lama diam keluar dari permainan.",
      "Tiga peserta terakhir yang bertahan saling mengajukan pertanyaan sampai tersisa satu pemenang."
    ],
    "tips": "Ganti kata terlarang tiap 3 ronde (misalnya \"dan\", \"itu\") supaya peserta tidak sempat hafal polanya."
  },
  {
    "id": 103,
    "cat": "E",
    "name": "Origami Kecepatan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas lipat secukupnya, contoh gambar hasil lipatan",
    "steps": [
      "Pembina menunjukkan satu bentuk origami sederhana (misalnya perahu, topi, atau burung) beserta langkah-langkahnya.",
      "Peserta diberi waktu 5 menit untuk berlatih melipat mengikuti contoh.",
      "Setelah latihan, adakan lomba: siapa yang bisa melipat bentuk tersebut paling cepat dan paling rapi dalam 3 menit.",
      "Juri (pembina + 2 peserta) menilai kecepatan (50%) dan kerapian (50%).",
      "Tiga pelipat terbaik mendapat penghargaan; kertas hasil lipatan bisa dibawa pulang."
    ],
    "tips": "Naikkan level di ronde kedua dengan bentuk yang sedikit lebih rumit seperti katak lompat."
  },
  {
    "id": 104,
    "cat": "E",
    "name": "Telepon Rusak Gerakan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Peserta berbaris ke belakang, semua menghadap ke depan kecuali orang paling belakang.",
      "Pembina menunjukkan satu gerakan pendek ke orang paling belakang (misalnya melompat sambil berputar).",
      "Orang itu menepuk bahu orang di depannya, lalu memperagakan gerakan yang ia lihat — tanpa bicara.",
      "Begitu seterusnya sampai orang paling depan, yang lalu memperagakan gerakan finalnya ke semua.",
      "Bandingkan gerakan awal dan akhir; kelompok dengan perubahan paling sedikit (paling akurat) menang."
    ],
    "tips": "Mainkan dua barisan sekaligus dan adu akurasi antarbarisan supaya ada kompetisinya."
  },
  {
    "id": 105,
    "cat": "E",
    "name": "Kuis Cepat Tangan Di Atas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Daftar pertanyaan pengetahuan umum/Pramuka",
    "steps": [
      "Peserta duduk berkelompok 4–5 orang, tiap kelompok menunjuk satu juru bicara.",
      "Pembina membacakan pertanyaan (misalnya \"Apa kepanjangan SKU?\" atau \"Ibukota provinsi...?\").",
      "Kelompok yang tahu jawabannya mengangkat tangan secepat mungkin; yang tercepat boleh menjawab.",
      "Jawaban benar dapat 10 poin, jawaban salah membuat kelompok itu tidak boleh menjawab pertanyaan berikutnya.",
      "Setelah 15–20 pertanyaan, kelompok dengan poin tertinggi menang."
    ],
    "tips": "Selipkan pertanyaan \"bonus ganda\" yang poinnya 20 supaya kelompok yang tertinggal masih bisa mengejar."
  },
  {
    "id": 106,
    "cat": "E",
    "name": "Susun Cerita Kartu Gambar",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "15–20 kartu bergambar acak (bisa dari potongan majalah)",
    "steps": [
      "Sebar kartu-kartu bergambar acak di tengah lingkaran, gambar menghadap atas.",
      "Tiap kelompok (4–5 orang) mengambil 5 kartu secara acak.",
      "Dalam 10 menit, kelompok harus menyusun cerita petualangan yang memasukkan semua gambar di kartunya secara logis.",
      "Tiap kelompok menceritakan hasilnya di depan kelompok lain dengan gaya mendongeng.",
      "Kelompok lain memberi nilai 1–10 untuk kekompakan cerita dan kreativitas; nilai tertinggi menang."
    ],
    "tips": "Wajibkan cerita mengandung satu nilai Dasa Darma supaya ada muatan karakternya."
  },
  {
    "id": 107,
    "cat": "E",
    "name": "Duel Jari Suit Bertingkat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua peserta berpasangan dan melakukan suit (batu-gunting-kertas) biasa.",
      "Pemenang suit naik satu \"tingkat\" (dinyatakan level 1), yang kalah tetap level 0 dan mencari lawan baru sesama level 0.",
      "Pemenang level 1 hanya boleh melawan sesama level 1; pemenangnya naik ke level 2, begitu seterusnya.",
      "Permainan berlangsung 7 menit; peserta bebas mencari lawan selevel di dalam ruangan.",
      "Saat waktu habis, peserta dengan level tertinggi menjadi juara; jika seri, adu suit final."
    ],
    "tips": "Beri tiap level nama pangkat Pramuka (level 1 = Ramu, level 2 = Rakit, dst.) supaya nuansa Pramukanya terasa."
  },
  {
    "id": 108,
    "cat": "E",
    "name": "Tebak Benda Dari Kantong",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kantong kain tidak tembus pandang berisi 10 benda kecil",
    "steps": [
      "Masukkan 10 benda kecil berbeda ke dalam kantong kain (batu, kancing, tutup botol, karet gelang, dll.).",
      "Peserta duduk melingkar, kantong diedarkan dari tangan ke tangan.",
      "Tiap peserta boleh meraba isi kantong selama 20 detik tanpa mengintip, lalu menuliskan daftar benda yang ia kenali.",
      "Setelah satu putaran, buka kantong dan cocokkan jawaban tiap peserta.",
      "Peserta dengan daftar tebakan benar terbanyak menang."
    ],
    "tips": "Batasi hanya boleh meraba dengan satu tangan supaya tantangannya naik."
  },
  {
    "id": 109,
    "cat": "E",
    "name": "Drama Satu Menit",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas undian berisi tema/situasi",
    "steps": [
      "Bagi peserta menjadi kelompok 4–6 orang.",
      "Tiap kelompok mengambil undian tema (misalnya \"tersesat di hutan\", \"menolong teman jatuh\", \"upacara bendera kacau\").",
      "Kelompok diberi waktu 10 menit untuk menyiapkan drama singkat berdurasi maksimal 1 menit — boleh lucu, boleh serius.",
      "Tiap kelompok mementaskan dramanya di depan kelompok lain.",
      "Penonton memberi nilai untuk kekompakan, pesan moral, dan hiburan; kelompok dengan nilai tertinggi menang."
    ],
    "tips": "Wajibkan tiap drama diakhiri dengan pekik \"Satyaku kudarmakan\" yang diteriakkan bersama supaya meriah."
  },
  {
    "id": 110,
    "cat": "E",
    "name": "Bingo Pengetahuan Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu bingo 5x5 per peserta (kotaknya berisi istilah Pramuka), spidol, undian soal",
    "steps": [
      "Bagikan kartu bingo yang tiap kotaknya berisi istilah kepramukaan (SKU, Dasa Darma, semaphore, kompas, tenda, dll.) dalam urutan acak.",
      "Pembina membacakan definisi atau pertanyaan (\"Singkatan dari Syarat Kecakapan Umum?\"), bukan istilahnya langsung.",
      "Peserta yang merasa jawabannya ada di kartunya menyilang kotak tersebut.",
      "Peserta yang berhasil menyilang 5 kotak sejajar (vertikal/horizontal/diagonal) berteriak \"Bingo!\" dan kartunya diverifikasi.",
      "Jika verifikasinya benar ia menang; jika salah ia didiskualifikasi ronde itu dan permainan lanjut."
    ],
    "tips": "Siapkan 2–3 pola kartu berbeda supaya tidak semua peserta bingo dalam waktu bersamaan."
  },
  {
    "id": 111,
    "cat": "F",
    "name": "Cerita Berantai Satu Kalimat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua duduk melingkar mengelilingi api unggun. Pembina memberi kalimat pembuka, misalnya \"Malam itu kami mendengar suara aneh dari balik tenda...\"",
      "Pemain di sebelah kanan pembina melanjutkan cerita dengan tepat satu kalimat.",
      "Giliran berlanjut mengelilingi lingkaran, masing-masing menambah satu kalimat.",
      "Cerita berlanjut dua atau tiga putaran penuh hingga mencapai akhir yang disepakati.",
      "Di akhir, pembina merangkum alur cerita lucu atau seram yang tercipta."
    ],
    "tips": "Tentukan tema di awal (petualangan, misteri, komedi) agar cerita tidak melebar ke mana-mana."
  },
  {
    "id": 112,
    "cat": "F",
    "name": "Tebak Suara Malam",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua duduk melingkar, lampu/senter dimatikan kecuali api unggun di tengah.",
      "Satu pemain ditunjuk menjadi penebak dan diminta memejamkan mata.",
      "Pembina menunjuk diam-diam satu pemain lain untuk menirukan suara (binatang, benda, atau aktivitas, misalnya jangkrik, air mendidih, atau ritsleting tenda).",
      "Penebak membuka mata dan menebak siapa yang bersuara serta suara apa yang ditirukan.",
      "Jika benar, penebak bertukar peran; jika salah, penebak tetap untuk satu ronde lagi."
    ],
    "tips": "Buat daftar suara bertema alam dan perkemahan agar pemain tidak kehabisan ide."
  },
  {
    "id": 113,
    "cat": "F",
    "name": "Siapa yang Hilang?",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter",
    "steps": [
      "Semua duduk melingkar mengelilingi api unggun. Satu pemain menjadi \"pengamat\" dan berdiri di tengah lingkaran.",
      "Pengamat diberi waktu 30 detik untuk menghafal wajah dan posisi semua pemain.",
      "Pengamat disuruh memejamkan mata atau membalikkan badan. Satu pemain yang ditunjuk pembina diam-diam pindah duduk ke tempat yang jauh atau bersembunyi di balik lingkaran.",
      "Pengamat membuka mata dan menebak siapa yang hilang atau berpindah tempat, maksimal tiga tebakan.",
      "Jika berhasil, pemain yang \"hilang\" menjadi pengamat berikutnya."
    ],
    "tips": "Untuk kelompok besar, sembunyikan dua pemain sekaligus agar lebih menantang."
  },
  {
    "id": 114,
    "cat": "F",
    "name": "Bayangan Tangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter dan kain/terpal putih",
    "steps": [
      "Bentangkan kain putih di antara dua tongkat atau pohon sebagai layar. Satu senter diarahkan ke kain dari belakang.",
      "Satu pemain (dalang) duduk di belakang kain dan membuat bayangan dengan tangannya: burung, anjing, kupu-kupu, atau tokoh.",
      "Pemain lain di depan kain menebak bentuk bayangan apa yang dibuat.",
      "Setiap pemain mendapat giliran menjadi dalang selama dua menit.",
      "Di akhir, pilih tiga bayangan tangan terkreatif versi penonton."
    ],
    "tips": "Siapkan kartu contoh bentuk bayangan tangan agar pemula tidak bingung memulai."
  },
  {
    "id": 115,
    "cat": "F",
    "name": "Bisik Berantai Malam",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua duduk melingkar. Pembina membisikkan satu kalimat ke telinga pemain pertama, misalnya \"Tiga ekor kunang-kunang menari di atas tenda dapur umum.\"",
      "Pemain pertama membisikkan persis yang ia dengar ke pemain berikutnya, tanpa mengulang.",
      "Bisikan diteruskan mengelilingi lingkaran sampai ke pemain terakhir.",
      "Pemain terakhir mengucapkan kalimatnya dengan suara keras.",
      "Bandingkan kalimat akhir dengan kalimat awal — biasanya berubah lucu. Ulangi dengan kalimat baru dari arah berlawanan."
    ],
    "tips": "Gunakan kalimat berisi bunyi yang mirip (misalnya \"sapu lidi\" dan \"sapu lada\") agar hasilnya lebih kocak."
  },
  {
    "id": 116,
    "cat": "F",
    "name": "Senter Pemburu Harta Cahaya",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter per regu, kertas petunjuk",
    "steps": [
      "Pembina menyembunyikan 8–10 kertas petunjuk di area aman sekitar api unggun (radius maksimal 20 meter, sudah disurvei bebas lubang dan semak berbahaya).",
      "Pemain dibagi menjadi regu beranggotakan 4–6 orang, masing-masing membawa satu senter.",
      "Setiap regu mencari petunjuk dengan cahaya senter. Setiap petunjuk berisi teka-teki menuju lokasi petunjuk berikutnya.",
      "Aturan keselamatan: dilarang berlari, senter harus selalu menyala, dan tidak boleh keluar dari batas area yang ditandai tali rafia.",
      "Regu yang menemukan petunjuk terakhir dan kembali ke api unggun lebih dulu menjadi pemenang."
    ],
    "tips": "Akhiri dengan hadiah kecil seperti permen atau stiker untuk regu pemenang."
  },
  {
    "id": 117,
    "cat": "F",
    "name": "Cerita Hantu Versi Lucu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Setiap regu (4–6 orang) mendapat 10 menit untuk menyusun cerita seram versi lucu — hantu yang ketakutan, pocong yang nyasar, atau kuntilanak yang malu-malu.",
      "Perwakilan tiap regu menceritakan ceritanya di depan api unggun dengan gaya pendongeng: suara pelan, jeda menegangkan, lalu punchline lucu.",
      "Pemain lain dilarang mengganggu selama bercerita, boleh bereaksi spontan.",
      "Setelah semua regu tampil, voting dengan acungan tangan untuk cerita paling menyeramkan sekaligus paling lucu.",
      "Regu pemenang mendapat kesempatan memilih lagu api unggun berikutnya."
    ],
    "tips": "Batasi cerita maksimal 3 menit per regu agar tidak ada yang terlalu panjang."
  },
  {
    "id": 118,
    "cat": "F",
    "name": "Kode Senter Morse",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter per regu, kartu kode Morse sederhana",
    "steps": [
      "Pemain dibagi menjadi regu beranggotakan 4–6 orang. Setiap regu menerima kartu kode Morse untuk huruf A–Z yang disederhanakan.",
      "Regu pengirim berdiri sekitar 15 meter dari regu penerima, lalu mengirim satu kata pendek (misalnya \"TAPAK\" atau \"SEMANGAT\") dengan kedipan senter: kedip cepat untuk titik, kedip panjang untuk garis.",
      "Regu penerima mencatat dan menerjemahkan kedipan menjadi kata.",
      "Jika terjemahan benar, regu bertukar peran dan mengirim kata baru yang lebih panjang.",
      "Regu dengan terjemahan benar terbanyak dalam waktu yang ditentukan menang."
    ],
    "tips": "Mulai dengan kata tiga huruf agar pemain memahami polanya dulu sebelum naik level."
  },
  {
    "id": 119,
    "cat": "F",
    "name": "Tebak Bintang",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada (opsional: aplikasi peta bintang)",
    "steps": [
      "Semua berbaring atau duduk santai menghadap langit malam yang cerah.",
      "Pembina menunjuk satu rasi bintang yang terlihat dan menjelaskan namanya serta cerita di baliknya.",
      "Satu pemain ditunjuk menunjuk rasi atau bintang lain yang ia kenali dan menyebutkan namanya.",
      "Pemain lain boleh membantu atau mengoreksi dengan sopan.",
      "Lanjutkan bergiliran; pemain yang berhasil menyebutkan tiga rasi dengan benar mendapat julukan \"Penjaga Langit\" malam itu."
    ],
    "tips": "Siapkan 5 kartu nama rasi umum (Orion, Biduk, Salib Selatan, Scorpio, Leo) sebagai contekan."
  },
  {
    "id": 120,
    "cat": "F",
    "name": "Jaga Api",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kayu bakar cadangan, jam/weker",
    "steps": [
      "Api unggun dibiarkan menyala kecil. Pemain dibagi menjadi regu jaga bergiliran, masing-masing 5 menit.",
      "Tugas regu jaga: menjaga api tetap menyala tanpa padam dan tanpa membesar berlebihan — hanya boleh menambah maksimal dua potong kayu per giliran.",
      "Regu yang tidak berjaga duduk agak jauh dan tidak boleh memberi tahu atau membantu.",
      "Pembina menilai setiap giliran: api padam berarti gagal, api terlalu besar berarti peringatan.",
      "Regu dengan nyala api paling stabil sepanjang malam mendapat predikat \"Penjaga Api Terbaik\"."
    ],
    "tips": "Selalu ada pembina yang mengawasi langsung demi keselamatan, dan sediakan air/ember pasir di dekat api."
  },
  {
    "id": 121,
    "cat": "F",
    "name": "Lagu Sambung Kata",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Gitar/ukulele (opsional)",
    "steps": [
      "Semua duduk melingkar. Pembina memulai dengan menyanyikan satu baris lagu Pramuka atau lagu daerah.",
      "Pemain berikutnya harus melanjutkan dengan lagu lain yang kata pertamanya diawali huruf terakhir dari kata terakhir baris sebelumnya.",
      "Setiap pemain punya waktu 10 detik untuk berpikir; yang gagal menyanyi satu bait lagu hukuman pilihan kelompok.",
      "Lagu tidak boleh diulang dalam satu putaran permainan.",
      "Permainan berlanjut dua putaran, lalu tutup dengan menyanyikan satu lagu bersama-sama."
    ],
    "tips": "Bolehkan lagu pop atau lagu anak selama liriknya sopan."
  },
  {
    "id": 122,
    "cat": "F",
    "name": "Misteri Kotak Gelap",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kotak kardus dengan lubang tangan, benda-benda aman (buah, spons, mainan)",
    "steps": [
      "Pembina menyiapkan kotak kardus berisi 5–8 benda yang aman diraba (jeruk, spons basah, sisir, kaus kaki bersih, sendok kayu).",
      "Kotak diletakkan di tengah lingkaran dalam keadaan gelap; pemain bergiliran memasukkan tangan tanpa mengintip.",
      "Setiap pemain meraba satu benda selama 10 detik lalu menuliskan atau membisikkan tebakannya ke pembina.",
      "Setelah semua mendapat giliran, pembina membuka kotak dan mencocokkan jawaban.",
      "Pemain dengan tebakan benar terbanyak menjadi \"Tangan Ajaib\" malam itu."
    ],
    "tips": "Pastikan tidak ada benda tajam, panas, atau menjijikkan di dalam kotak."
  },
  {
    "id": 123,
    "cat": "F",
    "name": "Pemburu Kunang-Kunang",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Toples kaca/plastik per regu (berlubang tutupnya)",
    "steps": [
      "Pemain dibagi menjadi regu beranggotakan 3–5 orang, masing-masing membawa satu toples.",
      "Setiap regu diberi waktu 10 menit untuk \"berburu\" kunang-kunang di area aman sekitar perkemahan — dilarang berlari dan wajib berjalan berpasangan.",
      "Kunang-kunang dimasukkan ke toples dengan hati-hati, maksimal lima ekor per regu.",
      "Setelah waktu habis, semua regu kembali ke api unggun dan memamerkan hasil tangkapannya.",
      "Di akhir permainan, semua kunang-kunang dilepaskan kembali ke alam."
    ],
    "tips": "Jadikan momen pelepasan sebagai penutup yang syahdu sambil menyanyikan satu lagu pelan."
  },
  {
    "id": 124,
    "cat": "F",
    "name": "Tebak Siapa Aku (Tokoh)",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas post-it dan spidol",
    "steps": [
      "Setiap pemain menulis nama satu tokoh terkenal (pahlawan nasional, penemu, atlet) di post-it tanpa diketahui pemiliknya.",
      "Post-it ditempel di dahi pemain lain secara acak, jadi tiap orang tidak tahu tokoh di dahinya sendiri.",
      "Bergiliran, setiap pemain boleh bertanya satu pertanyaan ya/tidak ke kelompok, misalnya \"Apakah saya pahlawan Indonesia?\"",
      "Pemain yang berhasil menebak tokohnya boleh duduk santai sambil membantu memberi petunjuk.",
      "Permainan selesai saat semua pemain berhasil menebak, maksimal 20 menit."
    ],
    "tips": "Batasi pilihan tokoh yang sudah dikenal anak seusia peserta agar tidak terlalu sulit."
  },
  {
    "id": 125,
    "cat": "F",
    "name": "Rantai Kata Berirama",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua duduk melingkar. Pembina memulai dengan mengucapkan satu kata, misalnya \"api\".",
      "Pemain berikutnya harus mengucapkan kata yang berima atau berhubungan, misalnya \"menyala\", lalu berikutnya \"cahaya\".",
      "Setiap pemain punya waktu 5 detik; yang kehabisan kata atau mengulang kata yang sudah dipakai keluar satu putaran.",
      "Putaran berlanjut hingga tersisa tiga pemain terakhir.",
      "Tiga pemain terakhir adu cepat satu ronde final untuk menentukan pemenang."
    ],
    "tips": "Bolehkan rima longgar (bunyi akhir mirip) agar permainan tetap mengalir untuk anak yang lebih kecil."
  },
  {
    "id": 126,
    "cat": "F",
    "name": "Pantomim Bayangan Api",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi kata/aktivitas",
    "steps": [
      "Pemain dibagi menjadi dua tim. Satu pemain maju dan mengambil kertas berisi kata (misalnya \"memasak mie\", \"mendirikan tenda\", \"menyeberangi sungai\").",
      "Pemain tersebut berdiri di antara api unggun dan timnya sehingga bayangannya terlihat jelas, lalu memperagakan kata itu tanpa suara — boleh memakai bayangan tubuhnya sebagai efek.",
      "Timnya menebak dalam waktu 1 menit. Tebakan benar dapat 10 poin.",
      "Giliran berganti ke tim lawan dengan kata baru.",
      "Tim dengan poin tertinggi setelah 20 menit menang."
    ],
    "tips": "Jaga jarak aman minimal 2 meter dari api unggun untuk pemain yang memperagakan."
  },
  {
    "id": 127,
    "cat": "F",
    "name": "Kenangan Satu Kata",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Semua duduk melingkar dalam suasana tenang. Pembina meminta setiap pemain memikirkan momen berkesan hari itu selama perkemahan.",
      "Bergiliran, setiap pemain menyebutkan momennya dalam tepat satu kata, misalnya \"hujan\", \"tertawa\", atau \"tersesat\".",
      "Tidak boleh ada komentar atau tawa mengejek atas pilihan kata siapa pun.",
      "Setelah satu putaran penuh, pembina mengajak tiga sukarelawan menceritakan sedikit latar di balik kata pilihannya.",
      "Tutup dengan tepuk tangan bersama sebagai apresiasi atas hari yang dilalui."
    ],
    "tips": "Cocok dijadikan ritual penutup malam sebelum tidur di perkemahan."
  },
  {
    "id": 128,
    "cat": "F",
    "name": "Duel Cerita Dua Kalimat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis",
    "steps": [
      "Setiap pemain menulis satu cerita mini yang hanya terdiri dari tepat dua kalimat — kalimat pertama membangun suasana, kalimat kedua memberi kejutan.",
      "Kertas dikumpulkan, dikocok, lalu dibacakan satu per satu oleh pembina dengan intonasi dramatis.",
      "Setelah semua dibacakan, setiap pemain memilih tiga cerita favoritnya (tidak boleh memilih milik sendiri).",
      "Tiga cerita dengan suara terbanyak dibacakan ulang sebagai finalis.",
      "Voting akhir menentukan \"Cerita Dua Kalimat Terbaik\" malam itu."
    ],
    "tips": "Beri contoh dulu, misalnya: \"Aku mendengar langkah kaki di luar tenda. Ternyata itu suara perutku sendiri yang lapar.\""
  },
  {
    "id": 129,
    "cat": "F",
    "name": "Jejak Cahaya",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter per pemain, tali rafia pembatas area",
    "steps": [
      "Area permainan dibatasi tali rafia (maksimal 25 x 25 meter) di lapangan yang rata dan sudah disurvei aman, tanpa lubang atau akar menonjol.",
      "Satu pemain menjadi \"penjaga cahaya\" dan berdiri di tengah dengan senter menyala. Pemain lain menyebar di dalam area.",
      "Saat aba-aba dimulai, semua pemain bergerak perlahan (dilarang berlari) menghindari sorotan senter penjaga.",
      "Pemain yang terkena sorotan cahaya selama 3 detik harus diam di tempat (membeku) hingga ada pemain lain yang menyentuhnya untuk membebaskan.",
      "Setiap 3 menit penjaga berganti. Pemain yang paling jarang membeku menjadi pemenang."
    ],
    "tips": "Semua senter peserta boleh dinyalakan redup agar area tidak terlalu gelap dan tetap aman."
  },
  {
    "id": 130,
    "cat": "F",
    "name": "Surat untuk Bintang",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis",
    "steps": [
      "Setiap pemain menerima selembar kertas dan diminta menulis satu harapan atau cita-cita untuk dirinya setahun ke depan.",
      "Kertas dilipat dan dimasukkan ke dalam satu wadah (misalnya helm atau topi).",
      "Pembina mengocok wadah, lalu setiap pemain mengambil satu kertas secara acak.",
      "Bergiliran, setiap pemain membacakan harapan yang ia ambil dengan suara lantang ke arah langit, diawali \"Untuk bintang-bintang, aku titipkan harapan...\"",
      "Pemilik asli harapan boleh mengaku atau merahasiakannya; tutup dengan doa bersama."
    ],
    "tips": "Kumpulkan semua kertas sebagai arsip regu dan buka kembali di perkemahan tahun berikutnya."
  },
  {
    "id": 131,
    "cat": "G",
    "name": "Kapten Kapal",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain penutup mata, kursi sebagai rintangan, peluit",
    "steps": [
      "Satu orang ditunjuk menjadi kapten; anggota lain menjadi awak kapal yang semuanya ditutup matanya.",
      "Pembina menyusun \"lautan badai\" berupa rintangan kursi dan tali di lapangan.",
      "Kapten berdiri di menara (kursi) dan hanya boleh memberi perintah suara untuk menuntun awak melewati badai.",
      "Awak yang menyentuh rintangan dianggap \"tercebur\" dan harus kembali ke titik awal dipandu kapten.",
      "Setelah semua awak selamat, regu menilai kepemimpinan kapten: perintahnya jelas atau membingungkan?"
    ],
    "tips": "Ganti kapten di tengah jalan tanpa pemberitahuan agar awak merasakan gaya kepemimpinan berbeda."
  },
  {
    "id": 132,
    "cat": "G",
    "name": "Dilema Sekoci",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu peran (dokter, anak kecil, kakek, insinyur, dll.), kertas dan pulpen",
    "steps": [
      "Skenario: kapal tenggelam, sekoci hanya muat 5 dari 10 orang. Setiap peserta mendapat kartu peran rahasia.",
      "Satu orang ditunjuk sebagai pemimpin yang memimpin musyawarah siapa yang naik sekoci.",
      "Setiap peserta diberi 1 menit membela diri sesuai perannya agar dipilih selamat.",
      "Pemimpin harus mengambil keputusan final dalam 5 menit setelah mendengar semua argumen.",
      "Diskusikan bersama: apakah keputusan pemimpin adil? Apa yang sulit dari posisi pemimpin?"
    ],
    "tips": "Beri pemimpin informasi rahasia tambahan (misal sekoci bocor, hanya muat 4 orang) di tengah musyawarah."
  },
  {
    "id": 133,
    "cat": "G",
    "name": "Tebak Pemimpin Tersembunyi",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Regu berdiri melingkar; satu orang keluar ruangan menjadi \"detektif\".",
      "Pembina menunjuk satu orang secara diam-diam sebagai \"pemimpin tersembunyi\".",
      "Detektif kembali; pemimpin tersembunyi mulai melakukan gerakan (tepuk tangan, angguk, lompat) yang diam-diam diikuti seluruh lingkaran.",
      "Detektif punya 3 kesempatan menebak siapa pemimpinnya dengan mengamati siapa yang bergerak duluan.",
      "Jika tebakan benar, pemimpin jadi detektif baru; jika gagal tiga kali, pemimpin bertahan satu ronde lagi."
    ],
    "tips": "Minta pemimpin berganti gerakan setiap 10 detik agar detektif makin sulit melacak."
  },
  {
    "id": 134,
    "cat": "G",
    "name": "Negosiasi Sumber Daya",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu sumber daya (kayu, tali, kain, makanan), kertas misi per regu",
    "steps": [
      "Bagi peserta menjadi 3–4 regu; setiap regu mendapat misi membangun sesuatu (misal tenda darurat) dan sekumpulan kartu sumber daya yang tidak lengkap.",
      "Setiap regu menunjuk satu negosiator utama; hanya negosiator yang boleh berunding dengan regu lain.",
      "Buka sesi pasar bebas 10 menit: regu saling barter kartu sumber daya agar misinya terpenuhi.",
      "Negosiator harus memutuskan kapan menukar, kapan menahan, dan kapan menggertak.",
      "Regu yang misinya paling lengkap di akhir waktu menang; evaluasi strategi tiap negosiator."
    ],
    "tips": "Selipkan satu kartu \"jebakan\" yang tampak berharga padahal tidak dibutuhkan siapa pun."
  },
  {
    "id": 135,
    "cat": "G",
    "name": "Komandan Buta",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain penutup mata, balok/bata ringan atau kardus, tali area",
    "steps": [
      "Satu orang menjadi komandan (matanya terbuka); anggota lain ditutup matanya dan menjadi \"pasukan\".",
      "Di tengah area berserakan balok; tugas pasukan membangun menara setinggi 1 meter hanya dengan arahan suara komandan.",
      "Komandan tidak boleh menyentuh balok atau anggota pasukan — hanya boleh bicara.",
      "Pasukan yang menjatuhkan menara harus membongkar dan mengulang dari awal atas perintah komandan.",
      "Batasi waktu 12 menit; setelah selesai, pasukan menilai: instruksi komandan mudah diikuti atau tidak?"
    ],
    "tips": "Tambahkan \"kebisingan perang\" (regu lain berteriak) agar komandan harus mengatur volume dan kejelasan perintah."
  },
  {
    "id": 136,
    "cat": "G",
    "name": "Sidang Dewan Darurat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu skenario krisis, kertas suara, kotak suara sederhana",
    "steps": [
      "Pembina membacakan skenario krisis (misal \"air bersih perkemahan habis, bantuan datang 2 hari lagi\").",
      "Regu memilih seorang ketua sidang yang memimpin jalannya diskusi dan menjaga ketertiban.",
      "Setiap anggota mengusulkan satu solusi dalam 30 detik; ketua mencatat semua usulan di papan/kertas.",
      "Buka debat singkat 5 menit, lalu lakukan pemungutan suara tertutup untuk memilih solusi terbaik.",
      "Ketua mengumumkan hasil dan menyusun rencana aksi 3 langkah dari solusi terpilih."
    ],
    "tips": "Beri ketua hak veto satu kali agar peserta merasakan dinamika kekuasaan dalam pengambilan keputusan."
  },
  {
    "id": 137,
    "cat": "G",
    "name": "Misi 60 Detik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu misi, stopwatch/peluit",
    "steps": [
      "Tunjuk seorang pemimpin regu; ia menerima kartu misi rahasia (misal \"susun anggota dari yang tertinggi ke terpendek\").",
      "Pemimpin hanya punya 60 detik untuk memahami misi, menyusun strategi, dan memimpin regu menyelesaikannya.",
      "Anggota regu tidak boleh melihat kartu misi — mereka hanya mengikuti perintah pemimpin.",
      "Jika misi gagal dalam 60 detik, pemimpin boleh meminta 1 petunjuk dari pembina dengan penalti 10 detik.",
      "Mainkan 4–5 ronde dengan pemimpin dan misi berbeda; nilai kecepatan dan kejelasan tiap pemimpin."
    ],
    "tips": "Pilih misi yang butuh pembagian tugas cepat, misal \"kumpulkan 5 benda berwarna merah dari lapangan\"."
  },
  {
    "id": 138,
    "cat": "G",
    "name": "Tukar Kapten",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali, bola, cone (untuk tugas tim)",
    "steps": [
      "Regu diberi tugas tim (misal memindahkan bola dengan tali tanpa tangan menyentuh bola) dan memilih kapten sendiri.",
      "Di tengah tugas, pembina meniup peluit: kapten harus bertukar dengan kapten regu lain (atau dengan anggota biasa).",
      "Kapten baru harus melanjutkan strategi yang sedang berjalan — boleh mengubahnya, tetapi harus menjelaskan alasannya ke regu.",
      "Peluit dibunyikan 3–4 kali selama permainan sehingga kepemimpinan terus berganti.",
      "Diskusikan: kapten seperti apa yang paling mudah diikuti saat mengambil alih di tengah jalan?"
    ],
    "tips": "Larang kapten baru bertanya tentang strategi lama — ia harus membaca situasi sendiri."
  },
  {
    "id": 139,
    "cat": "G",
    "name": "Peta Harta Karun",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas peta sederhana, amplop petunjuk, \"harta\" (hadiah kecil)",
    "steps": [
      "Sembunyikan harta di area perkemahan; buat 5–6 petunjuk yang masing-masing mengarah ke lokasi berbeda (hanya satu yang benar).",
      "Tunjuk seorang ketua ekspedisi; ia menerima semua petunjuk sekaligus.",
      "Ketua harus memutuskan pembagian tim pencari: siapa ke petunjuk mana, dengan bekal waktu 15 menit.",
      "Tim yang menemukan harta membawanya ke ketua; ketua memutuskan strategi berdasarkan laporan yang masuk.",
      "Evaluasi: apakah pembagian tugas ketua tepat? Informasi apa yang seharusnya ditanyakan lebih dulu?"
    ],
    "tips": "Selipkan petunjuk palsu yang sengaja menyesatkan agar ketua harus menilai kredibilitas informasi."
  },
  {
    "id": 140,
    "cat": "G",
    "name": "Krisis Logistik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu bahan makanan/minuman, kertas anggaran, kalkulator (opsional)",
    "steps": [
      "Skenario: regu akan berkemah 3 hari tetapi dana logistik dipotong setengah. Tunjuk seorang \"kepala logistik\".",
      "Kepala logistik menerima daftar harga bahan dan anggaran terbatas; ia harus menyusun menu 3 hari yang cukup untuk semua anggota.",
      "Anggota regu boleh mengajukan \"permintaan khusus\" (misal alergi, vegetarian) yang harus diakomodasi.",
      "Kepala logistik mempresentasikan rencananya dalam 3 menit; regu boleh mengajukan keberatan satu kali.",
      "Keputusan final tetap di tangan kepala logistik; diskusikan trade-off yang ia buat."
    ],
    "tips": "Di tengah penyusunan, umumkan \"harga beras naik 50%\" agar kepala logistik harus merevisi rencana di bawah tekanan."
  },
  {
    "id": 141,
    "cat": "G",
    "name": "Rantai Komando",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu perintah tertulis",
    "steps": [
      "Regu berbaris; orang pertama adalah komandan yang menerima kartu perintah rahasia dari pembina.",
      "Komandan membisikkan perintah ke orang kedua, lalu orang kedua ke ketiga, begitu seterusnya sampai ujung barisan.",
      "Orang terakhir melaksanakan perintah yang ia dengar di depan semua orang.",
      "Bandingkan perintah asli dengan yang dilaksanakan; hitung seberapa banyak yang berubah.",
      "Ulangi dengan komandan berbeda; komandan yang pesannya paling utuh sampai di ujung adalah yang terbaik."
    ],
    "tips": "Gunakan perintah berisi angka dan arah (misal \"4 langkah kiri, 2 langkah kanan, jongkok\") agar distorsi mudah terlihat."
  },
  {
    "id": 142,
    "cat": "G",
    "name": "Debat Kilat Pemimpin",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu topik, stopwatch",
    "steps": [
      "Pilih dua calon \"ketua regu\"; keduanya diberi topik yang sama (misal \"aturan main bola di perkemahan\").",
      "Masing-masing punya 1 menit untuk menyampaikan visinya tanpa interupsi.",
      "Buka sesi tanya jawab 5 menit: anggota regu boleh menguji kedua calon dengan pertanyaan sulit.",
      "Lakukan pemungutan suara tertutup; pemenang menjadi ketua regu untuk permainan berikutnya.",
      "Diskusikan: argumen seperti apa yang paling meyakinkan, dan mengapa?"
    ],
    "tips": "Beri salah satu calon \"kartu skandal\" (fakta mengejutkan tentang dirinya) yang boleh dipakai lawan saat debat."
  },
  {
    "id": 143,
    "cat": "G",
    "name": "Keputusan Terakhir",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu skenario \"pilih satu dari dua\", kertas dan pulpen",
    "steps": [
      "Tunjuk seorang pemimpin; ia akan menghadapi 5 skenario \"pilih satu dari dua\" yang serba sulit (misal \"selamatkan tenda atau selamatkan perbekalan\").",
      "Untuk tiap skenario, pemimpin boleh berdiskusi dengan regu maksimal 2 menit, lalu harus memutuskan sendiri.",
      "Setiap keputusan dicatat beserta alasannya dalam satu kalimat.",
      "Setelah 5 skenario, pembina membacakan \"konsekuensi\" tiap pilihan (disiapkan sebelumnya) dan regu menilai.",
      "Refleksi: keputusan mana yang paling berat, dan apa yang membantu pemimpin memutuskan?"
    ],
    "tips": "Kurangi waktu diskusi menjadi 30 detik di dua skenario terakhir untuk melatih keputusan di bawah tekanan."
  },
  {
    "id": 144,
    "cat": "G",
    "name": "Misi Rahasia Ganda",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu misi rahasia per orang, meja perundingan",
    "steps": [
      "Setiap peserta mendapat kartu misi rahasia: sebagian punya misi kelompok (misal \"bangun kesepakatan damai\"), satu-dua orang punya misi pribadi bertentangan (misal \"gagalkan kesepakatan\").",
      "Tunjuk seorang pemimpin perundingan yang tidak tahu siapa pemilik misi rahasia.",
      "Buka perundingan 15 menit untuk mencapai \"kesepakatan bersama\" tertulis yang ditandatangani semua pihak.",
      "Pemimpin harus membaca gelagat peserta, mengatur giliran bicara, dan menjaga perundingan tidak buntu.",
      "Setelah waktu habis, buka semua kartu: apakah misi kelompok tercapai? Siapa yang paling pandai menyembunyikan agendanya?"
    ],
    "tips": "Beri pemimpin hak memanggil \"jeda\" 1 menit untuk berunding privat dengan satu peserta yang dicurigai."
  },
  {
    "id": 145,
    "cat": "G",
    "name": "Bangun Kota Anggaran",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas, pulpen, kartu proyek berbiaya, uang mainan",
    "steps": [
      "Regu berperan sebagai dewan kota dengan anggaran terbatas (misal 100 koin mainan).",
      "Tunjuk seorang wali kota yang memimpin; tersedia 8 kartu proyek (jalan, sekolah, pasar, dll.) masing-masing berbiaya dan bermanfaat berbeda.",
      "Setiap anggota melobi satu proyek favoritnya dalam 1 menit.",
      "Wali kota menyusun paket proyek yang muat anggaran, boleh memotong atau menggabung usulan.",
      "Dewan memberikan suara setuju/tidak; jika ditolak, wali kota merevisi satu kali lalu keputusan final di tangannya."
    ],
    "tips": "Di tengah permainan, umumkan \"bencana banjir\" yang memaksa wali kota mengalihkan 30 koin untuk darurat."
  },
  {
    "id": 146,
    "cat": "G",
    "name": "Jejak Komandan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Cone atau tiang sebagai rintangan",
    "steps": [
      "Susun lintasan rintangan sederhana (zig-zag cone, tali rendah, lingkaran lompat).",
      "Tunjuk seorang komandan yang berjalan paling depan; barisan mengikutinya dalam formasi satu banjar.",
      "Aturan: barisan hanya boleh meniru persis gerakan komandan — jika komandan melompat, semua melompat; jika ia berhenti, semua berhenti.",
      "Komandan boleh sengaja melakukan gerakan tipuan (misal pura-pura melompat) untuk menguji fokus barisan.",
      "Anggota yang salah gerakan pindah ke barisan paling belakang; setelah 10 menit, tunjuk komandan baru."
    ],
    "tips": "Minta komandan memberi aba-aba suara yang bertentangan dengan gerakannya (misal teriak \"jongkok\" sambil melompat)."
  },
  {
    "id": 147,
    "cat": "G",
    "name": "Lelang Keputusan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu pilihan kegiatan, koin/poin mainan",
    "steps": [
      "Sediakan 6 kartu pilihan kegiatan perkemahan (api unggun, jelajah malam, lomba masak, dll.); regu hanya bisa memilih 2.",
      "Tunjuk seorang ketua lelang; setiap anggota mendapat 10 koin untuk \"menawar\" kegiatan favoritnya.",
      "Ketua memimpin lelang terbuka: kegiatan dengan tawaran total tertinggi terpilih.",
      "Anggota boleh bersekutu menggabungkan koin, tetapi kesepakatan harus diumumkan terbuka.",
      "Setelah 2 kegiatan terpilih, diskusikan: apakah hasilnya adil bagi yang kalah lelang? Apa peran ketua menjaga ketertiban?"
    ],
    "tips": "Beri ketua 5 koin \"dana talangan\" yang boleh ia sumbangkan diam-diam ke kegiatan yang menurutnya terbaik."
  },
  {
    "id": 148,
    "cat": "G",
    "name": "Pesan Terakhir Komandan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas pesan, amplop",
    "steps": [
      "Skenario: regu terpisah dalam \"hutan\", hanya komandan yang tahu titik kumpul. Ia boleh mengirim satu pesan tertulis.",
      "Tunjuk komandan; ia menulis pesan maksimal 20 kata yang harus memuat: lokasi, waktu, dan tanda pengenal.",
      "Pesan diedarkan; anggota lain berperan sebagai \"kurir\" yang hanya boleh menghafal, tidak membawa kertas.",
      "Kurir menyampaikan pesan secara berantai dengan hafalan; orang terakhir menulis ulang pesan yang ia terima.",
      "Bandingkan pesan akhir dengan aslinya; diskusikan bagaimana komandan seharusnya menyusun pesan agar tahan distorsi."
    ],
    "tips": "Batasi pesan hanya 10 kata agar komandan harus memilih informasi paling kritis."
  },
  {
    "id": 149,
    "cat": "G",
    "name": "Balik Peran Mendadak",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu peran (pemimpin, pencatat, penjaga waktu, pelaksana)",
    "steps": [
      "Regu diberi tugas (misal menyusun rencana pentas seni 10 menit) dengan peran yang dibagikan lewat kartu.",
      "Setiap 5 menit pembina meniup peluit: semua peran diputar — pemimpin jadi pelaksana, pencatat jadi pemimpin, dan seterusnya.",
      "Pemimpin baru harus membaca catatan pemimpin lama dalam 1 menit lalu melanjutkan kepemimpinan.",
      "Tugas harus selesai dalam 20 menit apa pun yang terjadi dengan pergantian peran.",
      "Refleksi: peran mana yang paling sulit diambil alih mendadak, dan apa yang membuat serah terima berjalan mulus?"
    ],
    "tips": "Pada putaran terakhir, acak kartu peran agar tidak ada yang mendapat peran yang sudah dikuasainya."
  },
  {
    "id": 150,
    "cat": "G",
    "name": "Voting Buta Kebijakan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu usulan kebijakan, kertas suara",
    "steps": [
      "Kumpulkan 5 usulan kebijakan perkemahan dari anggota (misal jam malam, jadwal piket) secara anonim.",
      "Tunjuk seorang moderator yang membacakan tiap usulan tanpa menyebut pengusulnya.",
      "Setiap usulan didiskusikan 3 menit; moderator memastikan yang pendiam pun kebagian bicara.",
      "Lakukan voting tertutup per usulan; usulan dengan suara terbanyak menjadi kebijakan resmi.",
      "Diskusikan: apakah anonimitas membuat orang lebih jujur? Apa peran moderator menjaga netralitas?"
    ],
    "tips": "Selipkan satu usulan \"jebakan\" yang sengaja kontroversial untuk menguji kedewasaan diskusi."
  },
  {
    "id": 151,
    "cat": "G",
    "name": "Ekspedisi Tanpa Peta",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kompas (opsional), kartu petunjuk arah samar, cone pos",
    "steps": [
      "Buat 4 pos rahasia di sekitar perkemahan; ketua ekspedisi hanya menerima petunjuk arah yang samar (misal \"ke arah matahari terbit, 100 langkah\").",
      "Ketua membagi regu menjadi tim-tim kecil dan menugaskan tiap tim ke satu petunjuk.",
      "Setiap 5 menit, tim pelapor kembali memberi laporan; ketua boleh mengubah strategi dan memindahkan tim.",
      "Tim yang menemukan pos membawa kembali \"token\" sebagai bukti; ketua mencatat progres di kertas.",
      "Regu dengan token terbanyak menang; evaluasi keputusan alokasi tim oleh ketua."
    ],
    "tips": "Buat satu petunjuk sengaja ambigu ganda agar ketua harus memutuskan interpretasi mana yang dikejar."
  },
  {
    "id": 152,
    "cat": "G",
    "name": "Dewan Juri Lomba",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Lembar kriteria penilaian, kertas skor",
    "steps": [
      "Regu menjadi dewan juri untuk menilai 3 penampilan (bisa penampilan regu lain atau rekaman yang disiapkan pembina).",
      "Tunjuk seorang ketua juri yang memimpin diskusi penilaian dan memastikan tidak ada yang mendominasi.",
      "Setiap juri memberi skor individu dulu secara tertutup, lalu ketua membuka diskusi untuk menyamakan persepsi.",
      "Jika terjadi selisih skor besar, ketua memediasi hingga dewan sepakat pada skor final.",
      "Umumkan pemenang; diskusikan bagaimana ketua menangani perbedaan pendapat yang tajam."
    ],
    "tips": "Beri satu juri \"kepentingan tersembunyi\" (misal temannya tampil) dan lihat apakah ketua bisa menjaga objektivitas."
  },
  {
    "id": 153,
    "cat": "G",
    "name": "Ultimatum Waktu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Stopwatch, kartu tugas bertingkat",
    "steps": [
      "Pemimpin regu menerima 3 tugas bertingkat (mudah, sedang, sulit) tetapi waktu total hanya 10 menit.",
      "Pemimpin harus memutuskan: kerjakan berurutan, bagi tugas paralel, atau korbankan satu tugas.",
      "Setiap tugas selesai dinilai; tugas sulit bernilai 3x tugas mudah.",
      "Anggota tidak boleh protes keputusan pembagian tugas selama waktu berjalan — protes hanya boleh setelah selesai.",
      "Hitung skor akhir; diskusikan strategi pemimpin: apakah pengorbanan tugas sulit keputusan tepat?"
    ],
    "tips": "Di menit ke-5, potong waktu tersisa menjadi 3 menit agar pemimpin harus merevisi strategi di tengah jalan."
  },
  {
    "id": 154,
    "cat": "G",
    "name": "Aliansi Tiga Kubu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Bendera/tanda tiga warna, kartu misi aliansi",
    "steps": [
      "Bagi peserta menjadi 3 kubu dengan kekuatan berbeda (kubu besar, sedang, kecil); tiap kubu memilih pemimpinnya.",
      "Misi: menangkan \"pemilu dewan\" — kubu butuh suara mayoritas, jadi aliansi antar-kubu diperlukan.",
      "Buka 15 menit diplomasi: para pemimpin bernegosiasi, menawarkan konsesi, dan membentuk aliansi.",
      "Kesepakatan aliansi harus tertulis dan ditandatangani para pemimpin; pengkhianatan diperbolehkan tetapi tercatat.",
      "Gelar pemungutan suara; kubu/aliansi pemenang menjelaskan strateginya, lalu diskusikan etika pengkhianatan dalam permainan."
    ],
    "tips": "Ubah komposisi kekuatan kubu di tengah diplomasi (misal kubu kecil mendapat \"kartu veto\") agar peta aliansi berubah."
  },
  {
    "id": 155,
    "cat": "G",
    "name": "Evaluasi Cermin Pemimpin",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan pulpen, kotak saran",
    "steps": [
      "Setelah seharian kegiatan, setiap regu diminta mengevaluasi pemimpin regunya secara anonim lewat kertas.",
      "Setiap anggota menulis satu kekuatan dan satu saran perbaikan untuk pemimpinnya.",
      "Kertas dikumpulkan ke kotak, dikocok, lalu dibacakan oleh pembina (bukan oleh pemimpinnya sendiri).",
      "Pemimpin menanggapi setiap masukan dalam 1 menit: menerima, menjelaskan, atau meminta klarifikasi.",
      "Tutup dengan setiap pemimpin menyampaikan satu komitmen perbaikan yang akan ia lakukan besok."
    ],
    "tips": "Minta juga setiap anggota menulis satu hal yang akan ia lakukan untuk memudahkan tugas pemimpinnya."
  },
  {
    "id": 156,
    "cat": "H",
    "name": "Drama Satu Babak Dadakan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi tema dan peran",
    "steps": [
      "Pemain dibagi menjadi regu beranggotakan 6 orang. Setiap regu mengambil undian berisi tema (misalnya \"Hari pertama perkemahan\", \"Regu yang kehilangan kompas\") dan daftar peran.",
      "Regu diberi waktu 15 menit untuk menyusun drama satu babak berdurasi 3–5 menit, lengkap dengan dialog dan pembagian peran.",
      "Setiap regu mementaskan dramanya di depan kelompok lain yang menjadi penonton.",
      "Penonton memberi apresiasi dengan tepuk tangan dan satu komentar positif per penampilan.",
      "Pilih pemenang untuk kategori \"Cerita Terbaik\", \"Akting Terbaik\", dan \"Paling Lucu\"."
    ],
    "tips": "Sediakan properti sederhana dari barang perkemahan (tenda, nesting, tali) untuk memperkaya pementasan."
  },
  {
    "id": 157,
    "cat": "H",
    "name": "Yel-Yel Regu Baru",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis",
    "steps": [
      "Setiap regu (5–8 orang) diminta menciptakan yel-yel orisinal untuk regunya: minimal 4 baris, ada nama regu, dan ada gerakan.",
      "Regu diberi waktu 15 menit untuk menulis lirik, menentukan irama/ketukan, dan melatih gerakan kompak.",
      "Setiap regu tampil membawakan yel-yelnya di depan kelompok lain.",
      "Kelompok lain menilai dengan tiga kriteria: kekompakan, kreativitas lirik, dan semangat.",
      "Yel-yel terbaik ditetapkan sebagai yel-yel resmi regu selama perkemahan."
    ],
    "tips": "Rekam penampilan tiap regu agar bisa diputar ulang dan dievaluasi bersama."
  },
  {
    "id": 158,
    "cat": "H",
    "name": "Lukis Wajah Tema Alam",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Cat wajah (face paint) yang aman, cermin kecil",
    "steps": [
      "Pemain berpasangan. Setiap pasangan mendapat seperangkat cat wajah yang aman untuk kulit.",
      "Setiap orang melukis wajah pasangannya dengan tema alam: kupu-kupu, harimau, bunga, atau matahari.",
      "Waktu melukis 12 menit; yang dilukis boleh memberi arahan tetapi tidak boleh melihat cermin dulu.",
      "Setelah selesai, semua berbaris dan memamerkan hasil lukisannya.",
      "Voting untuk kategori \"Paling Mirip\", \"Paling Kreatif\", dan \"Paling Berani\"."
    ],
    "tips": "Pastikan cat wajah yang dipakai berlabel aman untuk kulit anak dan sediakan tisu basah untuk membersihkan."
  },
  {
    "id": 159,
    "cat": "H",
    "name": "Pantomim Profesi",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi nama profesi",
    "steps": [
      "Pemain dibagi menjadi dua tim. Satu pemain maju mengambil kertas berisi nama profesi (dokter, pemadam kebakaran, koki, arsitek, nelayan).",
      "Pemain memperagakan profesi itu tanpa suara dan tanpa menunjuk benda di sekitar, hanya dengan gerakan tubuh dan mimik wajah.",
      "Timnya menebak dalam waktu 1 menit; jawaban benar mendapat 10 poin.",
      "Jika tim sendiri gagal, tim lawan boleh mencuri jawaban untuk 5 poin.",
      "Tim dengan poin tertinggi setelah semua anggota mendapat giliran menang."
    ],
    "tips": "Campur profesi mudah dan sulit agar semua level usia bisa ikut menikmati."
  },
  {
    "id": 160,
    "cat": "H",
    "name": "Lagu Parodi Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis, gitar (opsional)",
    "steps": [
      "Setiap regu (5–8 orang) memilih satu lagu populer yang dikenal semua anggota.",
      "Regu menulis ulang lirik lagu itu menjadi parodi bertema kegiatan Pramuka: perkemahan, memasak, begadang, atau latihan baris-berbaris.",
      "Waktu menulis 15 menit; lirik harus sopan dan minimal 2 bait plus refrain.",
      "Setiap regu menyanyikan parodinya di depan kelompok, boleh dengan iringan gitar.",
      "Voting menentukan parodi terlucu dan paling kompak dinyanyikan."
    ],
    "tips": "Kumpulkan semua lirik parodi menjadi \"buku lagu\" regu sebagai kenang-kenangan."
  },
  {
    "id": 161,
    "cat": "H",
    "name": "Patung Manusia",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tidak ada",
    "steps": [
      "Pemain dibagi menjadi regu beranggotakan 4–6 orang. Setiap regu mendapat satu tema, misalnya \"Gotong royong\", \"Upacara bendera\", atau \"Badai di perkemahan\".",
      "Regu menyusun anggotanya menjadi \"patung hidup\" yang menggambarkan tema itu — setiap orang membeku dalam satu pose.",
      "Satu orang boleh menjadi narator yang menjelaskan patungnya dalam 30 detik.",
      "Regu lain menebak tema patung sebelum narator menjelaskan; tebakan benar dapat poin.",
      "Patung paling ekspresif dan paling sulit ditebak mendapat penghargaan."
    ],
    "tips": "Foto setiap patung untuk dokumentasi dan bahan evaluasi kreativitas."
  },
  {
    "id": 162,
    "cat": "H",
    "name": "Puisi Berantai",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis",
    "steps": [
      "Setiap pemain menerima selembar kertas dan menulis satu baris pembuka puisi bertema alam atau persahabatan.",
      "Kertas dilipat sehingga hanya baris terakhir yang terlihat, lalu diedarkan ke pemain berikutnya.",
      "Setiap pemain melanjutkan puisi dengan satu baris yang nyambung dengan baris yang terlihat, lalu melipat lagi.",
      "Kertas diedarkan 5–6 kali hingga kembali ke pemilik awal.",
      "Setiap pemilik membuka dan membacakan puisi \"berantai\" hasil karya bersama itu dengan lantang."
    ],
    "tips": "Pilih tiga puisi terbaik untuk ditempel di mading perkemahan."
  },
  {
    "id": 163,
    "cat": "H",
    "name": "Kerajinan Tali Temali Hias",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali pramuka, gunting, manik-manik/aksesori",
    "steps": [
      "Setiap pemain menerima seutas tali pramuka sepanjang 1 meter dan beberapa manik-manik.",
      "Pembina mendemonstrasikan tiga simpul dasar hias: simpul mati ganda, simpul anyam sederhana, dan simpul gelang.",
      "Pemain membuat gelang atau gantungan kunci dari tali dengan mengombinasikan simpul yang diajarkan plus kreasi sendiri.",
      "Setiap karya harus memuat minimal dua jenis simpul berbeda.",
      "Pamerkan semua karya; pilih yang paling rapi, paling unik, dan paling rumit."
    ],
    "tips": "Hasil karya bisa dijadikan suvenir perkemahan atau hadiah tukar kado."
  },
  {
    "id": 164,
    "cat": "H",
    "name": "Tari Kreasi Regu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Pengeras suara/HP untuk musik",
    "steps": [
      "Setiap regu (6–8 orang) mendapat waktu 15 menit untuk menciptakan tarian kreasi berdurasi 1–2 menit dengan tema yang diundi (perjuangan, persahabatan, alam).",
      "Tarian boleh menggabungkan gerakan tradisional, modern, atau gerakan khas Pramuka (isyarat semaphore, tepuk Pramuka).",
      "Setiap regu tampil di depan kelompok lain dengan iringan musik pilihan mereka.",
      "Penilaian meliputi kekompakan, kesesuaian tema, dan kreativitas gerakan.",
      "Regu terbaik tampil ulang sebagai penutup acara."
    ],
    "tips": "Sediakan area latihan yang cukup luas agar tiap regu bisa berlatih tanpa mengganggu regu lain."
  },
  {
    "id": 165,
    "cat": "H",
    "name": "Gambar Buta Berpasangan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas, spidol, kain penutup mata",
    "steps": [
      "Pemain berpasangan. Satu orang matanya ditutup kain, satu orang menjadi \"pemandu suara\".",
      "Pemandu mendeskripsikan sebuah objek sederhana (rumah, perahu, gunung) hanya dengan kata-kata, tanpa menyentuh tangan pasangannya.",
      "Si buta menggambar berdasarkan deskripsi selama 3 menit.",
      "Setelah selesai, penutup mata dibuka dan pasangan membandingkan gambar dengan objek aslinya.",
      "Pasangan dengan gambar paling mirip menang; ulangi dengan peran bertukar."
    ],
    "tips": "Naikkan level dengan objek yang lebih rumit seperti \"tenda dengan api unggun di depannya\"."
  },
  {
    "id": 166,
    "cat": "H",
    "name": "Opera Mini Regu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi alur cerita",
    "steps": [
      "Setiap regu (5–8 orang) menerima kartu alur cerita legenda atau dongeng nusantara (Malin Kundang, Timun Mas, Sangkuriang versi ringkas).",
      "Regu mementaskan cerita itu dalam bentuk opera mini: semua dialog harus DINYANYIKAN, tidak boleh berbicara biasa.",
      "Waktu persiapan 15 menit untuk membagi peran dan menentukan nada/lagu tiap adegan.",
      "Setiap regu pentas 4–6 menit di depan kelompok.",
      "Beri penghargaan untuk \"Vokal Terbaik\", \"Cerita Paling Jelas\", dan \"Penampilan Terkocak\"."
    ],
    "tips": "Bolehkan memakai nada lagu anak-anak yang sudah dikenal agar mudah dinyanyikan."
  },
  {
    "id": 167,
    "cat": "H",
    "name": "Kolase Alam",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Karton, lem, gunting, bahan alam (daun, ranting, bunga kering)",
    "steps": [
      "Setiap regu (4–5 orang) menerima selembar karton dan peralatan lem.",
      "Regu mengumpulkan bahan-bahan alam di sekitar area perkemahan selama 10 menit — hanya boleh memungut yang sudah jatuh, dilarang memetik tanaman hidup.",
      "Regu menyusun kolase bertema \"Keindahan Alam Indonesia\" dari bahan yang dikumpulkan.",
      "Setiap kolase diberi judul dan satu kalimat penjelasan.",
      "Pamerkan semua kolase; voting untuk yang paling indah dan paling bermakna."
    ],
    "tips": "Kolase terbaik bisa dibingkai sederhana dan dipajang di sanggar/gudep."
  },
  {
    "id": 168,
    "cat": "H",
    "name": "Iklan Produk Kocak",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi nama produk aneh",
    "steps": [
      "Setiap regu (5–6 orang) mengundi satu \"produk aneh\", misalnya \"Sisir untuk botak\", \"Payung untuk ikan\", atau \"Sepatu untuk ular\".",
      "Regu membuat naskah iklan TV berdurasi 1–2 menit yang meyakinkan penonton untuk membeli produk itu.",
      "Iklan harus memuat slogan, demonstrasi produk, dan testimoni palsu yang lucu.",
      "Setiap regu mementaskan iklannya seperti syuting iklan sungguhan.",
      "Voting menentukan iklan paling meyakinkan dan paling mengocok perut."
    ],
    "tips": "Rekam dengan HP dan putar ulang — biasanya jauh lebih lucu ditonton kedua kali."
  },
  {
    "id": 169,
    "cat": "H",
    "name": "Musik Barang Bekas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Barang bekas (ember, botol, sendok, kaleng)",
    "steps": [
      "Setiap regu (5–6 orang) mengumpulkan barang bekas di sekitar perkemahan: ember, botol plastik, sendok, kaleng, dan jerigen.",
      "Regu merakit \"alat musik\" dari barang-barang itu dan menentukan siapa memainkan apa.",
      "Regu berlatih membawakan satu lagu sederhana (misalnya lagu Pramuka atau lagu daerah) dengan aransemen alat musik bekas selama 15 menit.",
      "Setiap regu tampil membawakan lagunya di depan kelompok.",
      "Beri penghargaan untuk \"Aransemen Terkreatif\" dan \"Kekompakan Terbaik\"."
    ],
    "tips": "Pastikan barang bekas sudah dibersihkan dulu dan tidak ada yang tajam atau berbahaya."
  },
  {
    "id": 170,
    "cat": "H",
    "name": "Cerita Bergambar Komik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas, spidol warna, penggaris",
    "steps": [
      "Setiap regu (4–5 orang) membuat komik strip 4–6 panel bertema pengalaman Pramuka yang lucu atau berkesan.",
      "Setiap panel harus memuat gambar dan minimal satu balon dialog.",
      "Waktu pengerjaan 20 menit; pembagian tugas disarankan (ada yang menggambar, ada yang menulis dialog).",
      "Setiap regu mempresentasikan komiknya dengan membacakan dialog tiap panel bergaya drama.",
      "Komik terbaik ditempel di mading; beri penghargaan untuk gambar terbaik dan cerita terlucu."
    ],
    "tips": "Tidak perlu jago menggambar — gaya stick figure yang ekspresif justru sering lebih lucu."
  },
  {
    "id": 171,
    "cat": "H",
    "name": "Fashion Show Barang Perkemahan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Barang-barang perkemahan (sarung, tali, kantong plastik, koran)",
    "steps": [
      "Setiap regu (5–6 orang) merancang satu kostum \"adibusana\" dari barang-barang perkemahan: sarung jadi gaun, tali jadi aksesori, koran jadi topi.",
      "Satu anggota regu menjadi model, sisanya menjadi desainer dan narator.",
      "Waktu merancang 15 menit; kostum harus bisa dipakai berjalan dan tidak merusak barang.",
      "Setiap model berjalan di \"catwalk\" sambil narator menjelaskan konsep busananya dengan gaya komentator fashion.",
      "Voting untuk \"Busana Terkreatif\", \"Model Terpede\", dan \"Narasi Terkocak\"."
    ],
    "tips": "Siapkan musik catwalk dari HP agar suasana peragaan lebih hidup."
  },
  {
    "id": 172,
    "cat": "H",
    "name": "Tebak Gaya Seniman",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi gaya/kartun tokoh",
    "steps": [
      "Satu pemain maju dan mengambil kertas berisi gaya khas, misalnya \"pelukis yang perfeksionis\", \"fotografer lebay\", atau \"penyanyi dangdut\".",
      "Pemain memperagakan gaya itu dalam aktivitas sederhana (melukis di udara, memotret penonton) tanpa menyebut nama gayanya.",
      "Pemain lain menebak gaya apa yang diperagakan dalam waktu 1 menit.",
      "Penebak benar mendapat poin dan maju sebagai pemeran berikutnya.",
      "Pemain dengan poin terbanyak di akhir menjadi \"Seniman Serba Bisa\"."
    ],
    "tips": "Siapkan daftar gaya yang variatif, dari yang mudah sampai yang butuh akting total."
  },
  {
    "id": 173,
    "cat": "H",
    "name": "Rantai Puisi Akrostik",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas dan alat tulis",
    "steps": [
      "Setiap regu (4–5 orang) mengundi satu kata kunci, misalnya \"PRAMUKA\", \"ALAM\", atau \"SAHABAT\".",
      "Regu membuat puisi akrostik: setiap baris diawali huruf-huruf kata kunci secara berurutan.",
      "Waktu menulis 12 menit; puisi minimal sepanjang kata kunci dan harus bermakna.",
      "Setiap regu membacakan puisinya dengan intonasi puitis di depan kelompok.",
      "Pilih puisi terbaik berdasarkan keindahan bahasa dan kesesuaian makna."
    ],
    "tips": "Puisi-puisi terbaik dikumpulkan menjadi antologi kecil regu."
  },
  {
    "id": 174,
    "cat": "H",
    "name": "Sulap Sederhana",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu, koin, sapu tangan, gelas plastik",
    "steps": [
      "Pembina mendemonstrasikan 3 trik sulap sederhana: koin menghilang, kartu tebakan, dan sapu tangan berubah warna (dengan penjelasan rahasianya).",
      "Setiap pemain memilih satu trik untuk dipelajari dan berlatih selama 10 menit berpasangan.",
      "Setiap pemain tampil mempertunjukkan triknya di depan kelompok tanpa membocorkan rahasia.",
      "Penonton menilai kerapian gerakan dan kepercayaan diri pesulap.",
      "Tiga pesulap terbaik mendapat gelar \"Master Sulap Regu\"."
    ],
    "tips": "Tekankan bahwa yang dinilai adalah kelancaran showmanship, bukan kerumitan triknya."
  },
  {
    "id": 175,
    "cat": "H",
    "name": "Lukisan Raksasa Bersama",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain/terpal putih besar atau kertas plano, cat air/kuas",
    "steps": [
      "Bentangkan kain putih besar di tanah atau tempel kertas plano di dinding.",
      "Tentukan tema lukisan bersama, misalnya \"Perkemahan Impian Kami\".",
      "Setiap pemain mendapat satu kuas dan waktu bergiliran 2 menit untuk menambahkan gambar atau warnanya ke lukisan.",
      "Tidak boleh menghapus atau menutupi gambar pemain lain; setiap tambahan harus menyambung karya yang sudah ada.",
      "Setelah semua mendapat giliran, beri judul pada lukisan dan foto bersama di depannya."
    ],
    "tips": "Lukisan jadi bisa dipajang di gudep sebagai kenangan angkatan."
  },
  {
    "id": 176,
    "cat": "H",
    "name": "Drama Radio (Tanpa Visual)",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Naskah pendek, alat pembuat efek suara (opsional)",
    "steps": [
      "Setiap regu (5–6 orang) menerima naskah drama pendek 3–4 menit bertema petualangan atau misteri.",
      "Regu tampil di balik tirai/kain sehingga penonton HANYA mendengar suara — semua akting lewat dialog, intonasi, dan efek suara buatan (langkah kaki, pintu, angin).",
      "Waktu latihan 12 menit untuk membagi peran dan menyiapkan efek suara.",
      "Setiap regu pentas; penonton menutup mata agar fokus pada suara.",
      "Voting untuk \"Efek Suara Terbaik\" dan \"Drama Paling Seru Didengar\"."
    ],
    "tips": "Rekam penampilan dan dengarkan ulang — biasanya hasilnya mengejutkan dan lucu."
  },
  {
    "id": 177,
    "cat": "H",
    "name": "Kaligrafi Nama Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas, spidol kaligrafi/pensil, contoh huruf",
    "steps": [
      "Pembina menunjukkan contoh dasar kaligrafi latin sederhana: huruf tegak bersambung yang dihias.",
      "Setiap pemain menulis nama panggilan atau nama regunya dengan gaya kaligrafi sekreatif mungkin selama 15 menit.",
      "Boleh dihias dengan gambar kecil: bunga, bintang, atau tunas kelapa khas Pramuka.",
      "Semua karya ditempel di papan pajangan untuk dinikmati bersama.",
      "Voting untuk \"Tulisan Terindah\", \"Hiasan Terkreatif\", dan \"Paling Rapi\"."
    ],
    "tips": "Karya terbaik bisa dilaminasi sederhana dan dijadikan pembatas buku kenang-kenangan."
  },
  {
    "id": 178,
    "cat": "H",
    "name": "Tari Topeng Kertas",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas karton, gunting, tali/karet, spidol warna",
    "steps": [
      "Setiap pemain membuat topeng kertas bertema karakter: hewan, tokoh pewayangan sederhana, atau ekspresi wajah (gembira, marah, sedih).",
      "Waktu membuat topeng 15 menit; topeng harus bisa dipakai dan berlubang di bagian mata.",
      "Setelah jadi, pemain memakai topengnya dan menari mengikuti irama musik bersama-sama selama satu lagu penuh.",
      "Di tengah tarian, musik berhenti mendadak — semua harus membeku dalam pose sesuai karakter topengnya.",
      "Pilih topeng terbaik dan penari paling totalitas."
    ],
    "tips": "Gunakan gunting tumpul untuk anak yang lebih kecil dan awasi penggunaannya."
  },
  {
    "id": 179,
    "cat": "H",
    "name": "Lomba Bercerita Dongeng",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas berisi judul dongeng",
    "steps": [
      "Setiap peserta mengundi satu judul dongeng nusantara (Timun Mas, Keong Mas, Lutung Kasarung, Si Kancil).",
      "Peserta diberi waktu 10 menit untuk mengingat alur dan menyiapkan gaya bercerita sendiri — boleh versi asli atau versi modern yang lucu.",
      "Setiap peserta bercerita 3–5 menit di depan kelompok dengan intonasi, jeda, dan gestur pendongeng.",
      "Penonton menilai: kejelasan alur, kemahiran bercerita, dan daya hibur.",
      "Tiga pendongeng terbaik mendapat gelar \"Pendongeng Hebat\" dan diminta tampil di acara api unggun."
    ],
    "tips": "Izinkan peserta membawa satu properti kecil untuk memperkuat ceritanya."
  },
  {
    "id": 180,
    "cat": "H",
    "name": "Galeri Karya Penutup",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Semua karya dari permainan kreatif sebelumnya, meja pajangan",
    "steps": [
      "Kumpulkan semua karya yang dihasilkan selama sesi permainan kreatif: komik, kolase, puisi, topeng, lukisan, kaligrafi, dan kerajinan tali.",
      "Tata karya-karya itu menjadi \"galeri\" di meja atau ditempel di tali jemuran karya.",
      "Setiap regu menunjuk satu \"kurator\" yang menjelaskan karya regunya kepada pengunjung galeri.",
      "Semua pemain berkeliling galeri, memberi stiker bintang pada tiga karya favoritnya (tidak boleh karya regu sendiri).",
      "Umumkan tiga karya berbintang terbanyak sebagai \"Karya Terbaik Perkemahan\" dan foto bersama di depan galeri."
    ],
    "tips": "Jadikan galeri ini acara penutup yang hangat sebelum upacara penutupan."
  },
  {
    "id": 181,
    "cat": "I",
    "name": "Estafet PBB Tongkat Isyarat Peluit",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tongkat pramuka per anggota, peluit pembina, stopwatch",
    "steps": [
      "Setiap regu berbaris bersaf memegang tongkat pramuka masing-masing.",
      "Pembina memberikan komando PBB tongkat tanpa suara lisan, melainkan menggunakan pola tiupan peluit khusus (misal: 1 tiupan panjang = 'Luruskan Barisan', 2 tiupan pendek = 'Hormat Tongkat', 3 tiupan pendek = 'Tegak Tongkat', dsb.).",
      "Regu harus menangkap isyarat peluit dan mengeksekusi gerakan PBB tongkat secara serentak dan presisi.",
      "Pembina melakukan penilaian berdasarkan kecepatan respon, keserentakan gerakan, dan kerapian barisan.",
      "Regu dengan akumulasi kesalahan paling sedikit dan gerakan paling kompak menjadi pemenang."
    ],
    "tips": "Diskusikan dan sepakati kode tiupan peluit PBB bersama seluruh Pemimpin Regu (Pinru) sebelum lomba dimulai."
  },
  {
    "id": 182,
    "cat": "I",
    "name": "Peta Pita Kilat Penjelajahan",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Lembar peta pita/HVS, penggaris, kompas bidik, busur derajat, pensil, meja jalan",
    "steps": [
      "Regu berjalan menyusuri rute penjelajahan sepanjang 300–500 meter yang memiliki 5–6 titik belokan.",
      "Di setiap titik belokan, regu wajib mencatat data ke dalam lembar peta pita: arah azimut (derajat kompas), jumlah langkah/jarak, jam, serta benda/sasaran tepi (seperti pohon besar, tiang listrik, atau jembatan).",
      "Pengukuran jarak dilakukan dengan menghitung langkah kaki yang dikonversi ke meter.",
      "Di garis finis, lembar peta pita dikumpulkan untuk diperiksa kerapian skala, kelengkapan kolom, dan ketepatan derajat azimutnya.",
      "Regu dengan pemetaan paling akurat dan rapi keluar sebagai pemenang."
    ],
    "tips": "Kalibrasi dulu rata-rata panjang langkah ganda setiap anggota sebelum penjelajahan dimulai."
  },
  {
    "id": 183,
    "cat": "I",
    "name": "Pionering Cepat: Menara Pandang Kaki Tiga",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "3 tongkat pramuka panjang (160 cm), 3 tongkat sedang, tali pramuka secukupnya",
    "steps": [
      "Setiap regu berlomba merakit struktur pionering menara pandang kaki tiga (tripod tower) sederhana.",
      "Pembuatan diawali dengan simpul pangkal, dilanjutkan ikatan silang/kaki tiga pada puncak tongkat, dan ikatan palang pada sabuk penguat bawah.",
      "Seluruh ikatan harus dibuat kencang, rapi, dan simetris tanpa bantuan alat pemotong atau paku.",
      "Setelah berdiri, menara diuji kekokohannya dengan diangkat atau diberi beban ringan di bagian puncaknya.",
      "Pemenang ditentukan dari kecepatan waktu pengerjaan, kerapian gulungan sisa tali, dan kekuatan ikatan."
    ],
    "tips": "Nilai ketepatan penggunaan jenis ikatan (ikatan kaki tiga vs ikatan palang) secara rinci."
  },
  {
    "id": 184,
    "cat": "I",
    "name": "Sandi Rumput & Morse Senter Malam",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Senter per regu, kertas & pensil, tabel sandi morse/rumput",
    "steps": [
      "Dilakukan saat malam hari; Pembina berdiri di seberang lapangan (jarak 30–50 meter) membawa senter utama.",
      "Pembina memancarkan pesan rahasia menggunakan kedipan cahaya morse (kedip pendek = titik, kedip panjang = garis).",
      "Regu bertugas mencatat pola titik dan garis yang diterima, lalu mengonversikannya ke bentuk Sandi Rumput di lembar jawaban.",
      "Pesan yang terpecahkan berisi instruksi tindakan cepat (misal: \"Buat simpul tiang pada tiang bendera utama\").",
      "Regu pertama yang berhasil menerjemahkan sandi dan menjalankan perintahnya dengan benar menjadi juara."
    ],
    "tips": "Bagi tugas dalam regu: satu orang memantau kedipan senter, satu mencatat titik-garis, dan satu menerjemahkan."
  },
  {
    "id": 185,
    "cat": "I",
    "name": "Menaksir Tinggi Pohon Metode Segitiga",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tongkat pramuka (160 cm), pita ukur/meteran, lembar kalkulasi",
    "steps": [
      "Setiap regu ditugaskan menaksir tinggi sebuah pohon atau tiang bendera tinggi tanpa dianjat.",
      "Regu menerapkan metode penaksiran segitiga siku-siku sama kaki (metode sudut 45°) menggunakan bantuan tongkat pramuka dan jarak langkah pengamatan.",
      "Regu mencatat titik acuan pengamatan, jarak ke objek, dan perhitungan matematisnya secara lengkap di lembar laporan.",
      "Pembina membandingkan hasil taksiran regu dengan ukuran objek yang sebenarnya (yang sudah diukur presisi sebelumnya).",
      "Regu dengan persentase selisih/eror terkeceil dari ukuran asli dinyatakan menang."
    ],
    "tips": "Bolehkan penggunaan metode perbandingan bayangan jika penaksiran dilakukan pada siang hari yang terik."
  },
  {
    "id": 186,
    "cat": "I",
    "name": "Formasi Barisan Isyarat Tangan Pembina",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Peluit pembina",
    "steps": [
      "Seluruh anggota regu menyebar secara acak di area lapangan.",
      "Pembina membunyikan peluit tiupan panggil (\"Pritt-pritt!\"), lalu membentangkan tangan membentuk satu isyarat formasi barisan Pramuka Penggalang/Penegak (misal: mengepal ke atas = Lingkaran Besar, tangan direntangkan lurus = Bersaf, tangan V = Angkare, atau tangan menekuk = U-Pendek).",
      "Seluruh regu harus berlari dan membentuk formasi sesuai isyarat tangan pembina dalam waktu sekilas.",
      "Pemimpin Regu (Pinru) harus segera mengambil posisi kanan depan atau tengah sesuai aturan formasi.",
      "Regu yang paling lambat membentuk formasi atau salah menafsirkan isyarat tangan tereliminasi secara bertahap."
    ],
    "tips": "Ubah formasi secara cepat berturut-turut untuk menguji refleks dan pemahaman materi PBB formasi."
  },
  {
    "id": 187,
    "cat": "I",
    "name": "Duel Sandi Kotak & Sandi AN",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kartu soal Sandi Kotak I/II dan Sandi AN, kertas jawaban, pensil",
    "steps": [
      "Setiap regu menerima lembar soal berisi cerita teka-teki yang ditulis menggunakan kombinasi Sandi Kotak I dan Sandi AN.",
      "Regu membagi lembar soal menjadi beberapa bagian agar anggota dapat memecahkannya secara paralel.",
      "Kata-kata yang terpecahkan disusun menjadi kalimat perintah acak yang mengarah pada tempat penyimpanan benda tersembunyi.",
      "Regu harus menemukan benda tersebut, berlari kembali ke garis start, dan menyanyikan yel-yel regu.",
      "Regu tercepat dengan hasil terjemahan sandi yang 100% tepat keluar sebagai pemenang."
    ],
    "tips": "Untuk tingkat Penegak, kombinasikan dengan Sandi Kotak III atau Sandi AZ agar tantangan lebih rumit."
  },
  {
    "id": 188,
    "cat": "I",
    "name": "Lomba Peta Panorama (Sketsa Pemandangan)",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kertas peta panorama, kompas bidik, penggaris bidik (mika/kardus bergaris grid), pensil 2B & pensil warna",
    "steps": [
      "Setiap regu membidik satu sektor pemandangan di lapangan dengan rentang sudut azimut tertentu (misal dari 110° sampai 150°).",
      "Menggunakan penggaris bidik, regu menggambar sketsa panorama dengan membagi area menjadi 3 bagian kedalaman: latar depan, latar tengah, dan latar belakang.",
      "Gambar diberi arsiran sesuai standar topo/panorama (misal arsiran miring untuk bukit, garis mendatar untuk air, titik-titik untuk vegetasi).",
      "Lengkapi dengan data angin, cuaca, tanggal, waktu, dan sudut pembatas di bagian atas lembaran.",
      "Penilaian berfokus pada proporsi pemandangan, ketepatan simbol/arsiran, dan kelengkapan data peta."
    ],
    "tips": "Gunakan mika transparan bergaris kuadran untuk mempermudah transfer skala objek dari alam ke kertas."
  },
  {
    "id": 189,
    "cat": "I",
    "name": "Tiang Bendera Portabel 3 Tongkat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "3 tongkat pramuka, 3 patok bambu/kayu, tali pramuka, bendera Merah Putih/Cikal",
    "steps": [
      "Regu ditantang mendirikan tiang bendera portabel yang terdiri dari sambungan 3 tongkat pramuka secara mandiri.",
      "Penyambungan tongkat menggunakan ikatan canggah/sambung tongkat yang rapi dan kuat.",
      "Agar tiang berdiri tegak lurus, regu memasang 3 tali penarik (guy lines) yang dikaitkan ke patok tanah menggunakan simpul penarik (taut-line hitch) dan simpul pangkal.",
      "Setelah tiang berdiri tegak tanpa dipegangi, bendera dikerek hingga puncaknya.",
      "Kriteria pemenang: tiang lurus tegak, ikatan kencang, dan proses pengerekan bendera lancar."
    ],
    "tips": "Tiang diuji ketahanannya dengan ditiup angin alami atau digoyangkan perlahan pada tali utama."
  },
  {
    "id": 190,
    "cat": "I",
    "name": "PBB Mata Tertutup Koor Regu",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Kain penutup mata untuk seluruh anggota (kecuali Pinru), peluit",
    "steps": [
      "Seluruh anggota regu mengenakan penutup mata, kecuali Pemimpin Regu (Pinru) yang bertindak sebagai komandan barisan.",
      "Pinru memberikan instruksi aba-aba PBB dasar (misal: \"Jalan di tempat - GERAK!\", \"Hadap kanan - GERAK!\", \"Dua langkah ke kiri - JALAN!\").",
      "Anggota regu harus bergerak serentak mempertahankan kerapian barisan hanya bermodal instruksi pendengaran dan irama ketukan kaki.",
      "Pinru dilarang menyentuh anggota barisan secara fisik saat instruksi berlangsung.",
      "Penilaian diambil dari tingkat kelurusan barisan akhir, keserentakan gerakan, dan kedisiplinan pasukan."
    ],
    "tips": "Lakukan di area rumput yang luas, datar, dan bebas rintangan demi keamanan peserta."
  },
  {
    "id": 191,
    "cat": "I",
    "name": "Menaksir Lebar Sungai Tanpa Menyeberang",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tongkat pramuka, beberapa patok penanda, pita ukur/meteran",
    "steps": [
      "Regu dihadapkan pada tepi \"sungai\" (area yang ditandai tali pembatas di lapangan).",
      "Tanpa menyeberangi garis batas, regu harus menghitung lebar sungai menuju titik pohon/sasaran di seberang sungai.",
      "Regu menggunakan ilmu geometri kepramukaan (metode segitiga kongruen / sudut 90° dan 45°) dengan menancapkan patok penanda di tepi sungai.",
      "Setelah mendapat angka taksiran, regu menuliskan metodologi dan rumus perhitungannya di lembar laporan.",
      "Pemenang adalah regu yang perhitungannya paling mendekati jarak sebenarnya yang sudah diukur oleh juri."
    ],
    "tips": "Penilaian tidak hanya pada angka akhir, tetapi juga pada rincian langkah pembentukan sudut siku-siku di lapangan."
  },
  {
    "id": 192,
    "cat": "I",
    "name": "Semaphore Rintangan Isyarat Cepat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 pasang bendera semaphore, penutup mata, tali rintangan/cone",
    "steps": [
      "Satu perwakilan regu menjadi pengirim isyarat semaphore dari stasiun pengirim jarak 20 meter.",
      "Di stasiun penerima, satu anggota bertugas membaca bendera semaphore, sementara satu anggota lainnya ditutup matanya untuk berjalan di jalur rintangan.",
      "Pengirim mengirimkan kata arah secara bertahap lewat semaphore (misal: \"KIRI\", \"MAJU\", \"LOMPAT\", \"STOP\").",
      "Penerima membaca huruf semaphore dengan cepat lalu meneriakkan panduan arah tersebut untuk menuntun rekannya yang ditutup matanya melewati rintangan.",
      "Regu yang anggotanya berhasil mencapai garis finis paling cepat tanpa menabrak rintangan menjadi juara."
    ],
    "tips": "Kecepatan penerjemahan huruf semaphore menentukan seberapa lancar navigator bergerak di jalur rintangan."
  },
  {
    "id": 193,
    "cat": "I",
    "name": "Sandi Jam & Kompas Pemburu Koordinat",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Jam analog/digital, kompas bidik, kartu soal sandi jam, kertas catatan",
    "steps": [
      "Regu menerima kartu soal Sandi Jam (misal: kunci `07.00 = A`, dengan interval 5 menit per huruf berikutnya).",
      "Setelah sandi terpecahkan, hasilnya berupa petunjuk angka azimut kompas dan jumlah langkah (misal: \"Azimut 240 derajat sejauh 35 langkah\").",
      "Regu harus langsung membidik sudut menggunakan kompas bidik dan berjalan sesuai petunjuk untuk menemukan patok pos tersembunyi.",
      "Di pos tersebut terdapat stempel bukti dan potongan soal sandi jam berikutnya.",
      "Regu yang mengumpulkan stempel pos terlengkap dan kembali ke basecamp tercepat menang."
    ],
    "tips": "Ubah interval jam (misal 10 menit atau selisih detik) untuk variasi tingkat kesulitan."
  },
  {
    "id": 194,
    "cat": "I",
    "name": "Balap Tandu Darurat Ikatan Jangkar",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 tongkat pramuka panjang (160 cm), 2 mitela/kain sarung/tali pramuka, boneka korban/anggota regu",
    "steps": [
      "Regu merakit tandu darurat P3K menggunakan 2 tongkat pramuka dan jaring tali dengan ikatan jangkar & simpul pangkal.",
      "Pembina memeriksa kekuatan jaring tandu dan kerapian simpul sebelum balapan dimulai.",
      "Satu anggota regu berbaring di atas tandu sebagai korban; 4 anggota regu menggotong tandu berlari menyusuri rute berpola angka 8 sejauh 40 meter.",
      "Korban tidak boleh terjatuh, dan bagian tubuh korban tidak boleh menyentuh tanah sepanjang perjalanan.",
      "Pemenang dinilai dari kecepatan waktu, kerapian ikatan P3K, dan kenyamanan/keselamatan korban."
    ],
    "tips": "Tambahkan rintangan merangkak rendah di mana penggotong harus menurunkan posisi tandu secara hati-hati."
  },
  {
    "id": 195,
    "cat": "I",
    "name": "PBB Tongkat Variasi & Formasi Kreatif",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tongkat pramuka per anggota, stopwatch",
    "steps": [
      "Setiap regu menyajikan pertunjukkan PBB Tongkat Variasi kreasi mandiri dengan durasi 5–7 menit.",
      "Gerakan wajib meliputi: Hormat Tongkat, Tegak Tongkat, Rehat Tongkat, dan Periksa Rapih dengan Tongkat.",
      "Gerakan wajib dilanjutkan dengan variasi formasi (perubahan bentuk barisan), tepuk tangan/tongkat berirama, dan hentakan kaki serentak.",
      "Komandan regu memberi komando di luar barisan atau di dalam formasi dengan suara lantang.",
      "Penilaian berfokus pada kerapian PBB dasar, kekompakan ketukan tongkat, kreativitas formasi, dan kedisiplinan."
    ],
    "tips": "Padukan denturan bunyi tongkat yang menghantam tanah secara serentak untuk menciptakan irama ketukan yang gagah."
  },
  {
    "id": 196,
    "cat": "I",
    "name": "Estafet Simpul Pramuka 8 Rasa",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "8 utas tali pramuka, tiang/papan uji simpul, stopwatch",
    "steps": [
      "Di seberang garis start disiapkan 8 pos kecil, masing-masing memiliki tiang/papan uji simpul.",
      "Anggota regu berlari secara estafet bergantian menuju pos untuk membuat 8 jenis simpul wajib Pramuka: * Pos 1: Simpul Mati * Pos 2: Simpul Hidup * Pos 3: Simpul Pangkal * Pos 4: Simpul Jangkar * Pos 5: Simpul Anyam * Pos 6: Simpul Tiang * Pos 7: Simpul Erat * Pos 8: Simpul Kembar / Nelayan",
      "Pembina mengecek kebenaran dan fungsi simpul di setiap pos. Jika salah, peserta harus membetulkannya sebelum menyerahkan tongkat estafet.",
      "Regu yang menyelesaikan seluruh 8 simpul dengan benar dan tercepat keluar sebagai pemenang."
    ],
    "tips": "Acak jenis simpul di tiap meja soal agar peserta tidak bisa memprediksi peran dari garis start."
  },
  {
    "id": 197,
    "cat": "I",
    "name": "Penentuan Titik Koordinat Peta Topografi",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Peta topografi/Rupa Bumi Indonesia (RBI), penggaris koordinat/Protractor, kompas bidik, pensil",
    "steps": [
      "Setiap regu dibekali lembar peta topografi asli suatu daerah perkemahan/pegunungan.",
      "Pembina membacakan soal garis koordinat (Grid Reference 6 angka atau 8 angka) dan ketinggian kontur tanah.",
      "Regu harus menemukan posisi titik pos pada peta, mengukur jarak sebenarnya menggunakan skala peta, dan menghitung derajat azimut serta back-azimut dari titik A ke titik B.",
      "Hasil perhitungan ditulis rinci di lembar kerja peta.",
      "Penilaian berfokus pada presisi penentuan koordinat grid, ketepatan perhitungan skala, dan sudut azimut."
    ],
    "tips": "Sangat cocok sebagai ajang kompetisi teknik kepramukaan (Tekpram) tingkat Penggalang Terap dan Penegak."
  },
  {
    "id": 198,
    "cat": "I",
    "name": "Pionering Jembatan Monyet Sederhana",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "Tali tambang utama (karmantel/tali manila), tali pramuka, 4 tongkat besar / pohon tumpuan",
    "steps": [
      "Regu bekerja sama membangun penyeberangan tali tunggal sederhana (jembatan monyet mini).",
      "Regu membuat penambat utama pada pohon atau struktur tumpuan menggunakan Simpul Tambat, Simpul Pangkal, dan pengencang Simpul Penarik (Taut-line Hitch).",
      "Tali utama dikencangkan agar tidak melengkung berlebihan saat diberi beban penyeberang.",
      "Setelah selesai dan diperiksa keamanan simpulnya oleh Pembina, satu anggota regu melintas menyeberangi lintasan tali tersebut.",
      "Kriteria juara: keamanan ikatan penambat (safety check), ketegangan tali, dan kelancaran penyeberangan."
    ],
    "tips": "Utamakan pemeriksaan ulang (double check) pada simpul penambat utama sebelum peserta memanjat tali."
  },
  {
    "id": 199,
    "cat": "I",
    "name": "Sandi KIM Sight (Mengingat Isyarat Sandi)",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "15 kartu simbol sandi (Kotak, Morse, Semaphore, Rumput), kain penutup, lembar jawaban",
    "steps": [
      "Mengombinasikan permainan KIM (Kemampuan Indera Manusia) penglihatan dengan materi sandi Pramuka.",
      "Pembina membuka kain penutup yang menutupi 15 kartu bermuatkan simbol sandi selama tepat 30 detik.",
      "Seluruh anggota regu mengamati dan mengingat bentuk simbol sandi serta posisinya tanpa boleh mencatat.",
      "Kain ditutup kembali; regu diberi waktu 3 menit untuk berdiskusi dan menuliskan ulang ke-15 simbol sandi tersebut beserta artinya di lembar jawaban.",
      "Regu dengan jumlah tebakan simbol dan arti sandi paling banyak dan tepat menjadi pemenang."
    ],
    "tips": "Latih strategi regu dengan membagi fokus pengamatan anggota (misal: anggota A mengingat kolom kiri, B kolom tengah)."
  },
  {
    "id": 200,
    "cat": "I",
    "name": "Bivak Darurat Jas Hujan & Tali Pramuka",
    "quote": "",
    "players": "",
    "dur": "Tidak dicantumkan dalam sumber",
    "tools": "2 jas hujan ponco, 4 tongkat pramuka, tali pramuka, 4 patok bambu, ember air, stopwatch",
    "steps": [
      "Regu ditantang membangun shelter / bivak darurat perlindungan alam menggunakan 2 jas hujan ponco dan tali pramuka.",
      "Regu mendirikan rangka dari tongkat pramuka, mengikat ponco dengan simpul pangkal & penarik pada patok tanah hingga membentang kencang.",
      "Bivak harus memiliki atap miring yang stabil agar tidak menampung air hujan dan dinding angin yang terlindungi.",
      "Setelah selesai, pembina menguji kekuatan shelter dengan menyiramkan satu ember air di atas atap bivak untuk memastikan air mengalir lancar dan bagian dalam tetap kering.",
      "Pemenang dinilai dari kecepatan pembuatan, kekokohan ikatan, dan efektivitas perlindungan bivak dari air siraman."
    ],
    "tips": "Jadikan permainan ini sebagai simulasi kondisi darurat (survival) dalam kegiatan penjelajahan malam."
  }
];
    </script>
    <script>
        // Set Default Date to Today
        document.addEventListener("DOMContentLoaded", () => {
            const today = new Date();
            const yyyy = today.getFullYear();
            const mm = String(today.getMonth() + 1).padStart(2, '0');
            const dd = String(today.getDate()).padStart(2, '0');
            document.getElementById('inputTanggal').value = `${yyyy}-${mm}-${dd}`;
            const gameForm = document.getElementById('gameForm');
            gameForm.addEventListener('input', resetGenerateStatus);
            gameForm.addEventListener('change', resetGenerateStatus);
        });

        // CATEGORY MAPPER
        const CATEGORY_MAP = {
            "A": "Ice Breaking & Pemanasan",
            "B": "Kerja Sama Tim",
            "C": "Wide Game",
            "D": "Ketangkasan",
            "E": "Dalam Ruangan",
            "F": "Api Unggun & Malam",
            "G": "Kepemimpinan",
            "H": "Kreatif & Seni",
            "I": "Teknik Kepramukaan"
        };

        const GAME_DATABASE = window.GAME_DATABASE;
        let isGenerating = false;

        function resetGenerateStatus() {
            if (isGenerating) return;
            const button = document.getElementById('generateButton');
            button.disabled = false;
            button.className = "w-full py-3.5 px-4 bg-gradient-to-r from-amber-500 via-amber-600 to-orange-600 hover:from-amber-400 hover:to-orange-500 text-stone-950 font-extrabold rounded-xl shadow-lg shadow-amber-600/30 transition-all transform hover:-translate-y-0.5 flex items-center justify-center space-x-2 text-sm tracking-wide";
            button.innerHTML = '<i class="fa-solid fa-fire-flame-curved text-lg"></i><span>GENERATE MODUL PERMAINAN</span>';
            document.getElementById('generateStatus').classList.add('hidden');
        }

        // NAMING CONVENTIONS FOR SCOUT UNITS
        const SCOUT_UNITS = {
            "Siaga": {
                type: "Barung",
                leader: "Pinrung",
                names: ["Barung Merah", "Barung Hijau", "Barung Kuning", "Barung Biru", "Barung Putih", "Barung Hitam", "Barung Cokelat", "Barung Ungu"],
                maxSize: 6
            },
            "Penggalang": {
                type: "Regu",
                leader: "Pinru",
                names: ["Regu Garuda", "Regu Elang", "Regu Harimau", "Regu Kancil", "Regu Mawar", "Regu Melati", "Regu Dahlia", "Regu Anggrek", "Regu Serigala", "Regu Rajawali", "Regu Cobra", "Regu Banteng"],
                maxSize: 8
            },
            "Penegak": {
                type: "Sangga",
                leader: "Pinsa",
                names: ["Sangga Perintis", "Sangga Penegas", "Sangga Pencoba", "Sangga Pendobrak", "Sangga Pelaksana"],
                maxSize: 6
            },
            "Pandega": {
                type: "Reka",
                leader: "Kareka",
                names: ["Reka Kerja", "Reka Bakti", "Reka Pembina", "Reka Pengembang", "Reka Perintis"],
                maxSize: 6
            }
        };

        // GENERATE GAME MODULE FUNCTION
        async function generateGame(e, selectedGameId) {
            if (e) e.preventDefault();
            if (isGenerating) return;

            // Form Inputs
            const gudep = document.getElementById('inputGudep').value || "Gugus Depan 01.001-01.002";
            const pangkalan = document.getElementById('inputPangkalan').value || "Pangkalan Latihan Pramuka";
            const tingkat = document.querySelector('input[name="tingkat"]:checked').value;
            const peserta = parseInt(document.getElementById('inputPeserta').value) || 30;
            const tglVal = document.getElementById('inputTanggal').value;
            const pembina = document.getElementById('inputPembina').value || "Kak Pembina";
            const ketuaGudep = document.getElementById('inputKetuaGudep').value || "Kak Mabigus / Ka Gudep";

            // Format Date to Indonesian
            const formattedDate = formatDateIndonesian(tglVal);

            // Selected Categories
            const selectedCategory = document.querySelector('input[name="kategori"]:checked');

            if (!selectedCategory) {
                alert("Pilih satu kategori permainan!");
                return;
            }

            // Filter Games
            const filteredGames = GAME_DATABASE.filter(g => g.cat === selectedCategory.value);
            if (filteredGames.length === 0) {
                alert("Tidak ada permainan dalam kategori ini!");
                return;
            }

            // Pick Random Game
            const game = selectedGameId === undefined
                ? filteredGames[Math.floor(Math.random() * filteredGames.length)]
                : filteredGames.find(g => g.id === selectedGameId);
            if (!game) {
                alert("Permainan yang dipilih tidak tersedia dalam kategori ini.");
                return;
            }

            isGenerating = true;
            const generateButton = document.getElementById('generateButton');
            const rerollButton = document.getElementById('rerollButton');
            const generateStatus = document.getElementById('generateStatus');
            generateButton.disabled = true;
            rerollButton.disabled = true;
            generateButton.classList.add('opacity-80', 'cursor-wait');
            generateButton.innerHTML = '<i class="fa-solid fa-spinner fa-spin text-lg"></i><span>Sedang memproses...</span>';
            generateStatus.className = "text-center text-sm font-semibold text-amber-300";
            generateStatus.innerText = "Mohon tunggu, modul sedang dibuat...";

            try {
                await new Promise(resolve => setTimeout(resolve, 3000));

            // Fill Kop & Metadata
            document.getElementById('outGudep').innerText = gudep.toUpperCase();
            document.getElementById('outPangkalan').innerText = pangkalan;
            document.getElementById('outTingkatan').innerText = tingkat.toUpperCase();
            document.getElementById('outKategori').innerText = CATEGORY_MAP[game.cat] || "Umum";
            document.getElementById('outDurasi').innerText = game.dur || "Tidak dicantumkan dalam sumber";
            document.getElementById('outPeserta').innerText = `${peserta} Orang`;
            document.getElementById('outTanggal').innerText = formattedDate;

            // Title & Quote
            document.getElementById('outNamaGame').innerText = game.name;
            const quoteElement = document.getElementById('outQuoteGame');
            quoteElement.innerText = game.quote || "";
            quoteElement.classList.toggle('hidden', !game.quote);
            const sourcePlayersElement = document.getElementById('outGamePlayers');
            sourcePlayersElement.innerText = game.players
                ? `Jumlah pemain sesuai sumber: ${game.players}`
                : "";
            sourcePlayersElement.classList.toggle('hidden', !game.players);

            // Group Breakdown Calculation (MATCHING PDF EXHIBIT EXACTLY)
            const unitInfo = SCOUT_UNITS[tingkat] || SCOUT_UNITS["Penggalang"];
            const maxPerUnit = unitInfo.maxSize;
            let numUnits = Math.ceil(peserta / maxPerUnit);
            if (numUnits < 2) numUnits = 2; // Minimum 2 units for competition

            const baseCount = Math.floor(peserta / numUnits);
            const remainder = peserta % numUnits;

            document.getElementById('outGroupTitle').innerHTML = `
                <i class="fa-solid fa-users-gear text-amber-600"></i>
                <span>PEMBAGIAN ${unitInfo.type.toUpperCase()} & KELOMPOK (${numUnits} ${unitInfo.type.toUpperCase()})</span>
            `;

            document.getElementById('outGroupSummary').innerText = 
                `Berdasarkan input ${peserta} peserta golongan ${tingkat}, peserta dibagi menjadi ${numUnits} ${unitInfo.type} (rata-rata ${baseCount}-${baseCount + (remainder > 0 ? 1 : 0)} orang per ${unitInfo.type}).`;

            // Generate Unit Cards
            const unitsContainer = document.getElementById('outUnitsContainer');
            unitsContainer.innerHTML = '';

            for (let i = 0; i < numUnits; i++) {
                let unitName = unitInfo.names[i % unitInfo.names.length];
                if (i >= unitInfo.names.length) {
                    unitName += ` ${Math.floor(i / unitInfo.names.length) + 1}`;
                }
                let memberCount = baseCount + (i < remainder ? 1 : 0);

                const unitChip = document.createElement('div');
                unitChip.className = "bg-white p-2 rounded-lg border border-stone-300 font-semibold text-stone-800 flex justify-between items-center shadow-sm";
                unitChip.innerHTML = `
                    <span class="text-[11px]"><i class="fa-solid fa-shield-halved text-amber-600 mr-1"></i> ${unitName}</span>
                    <span class="text-[10px] bg-stone-100 text-stone-600 px-2 py-0.5 rounded border border-stone-200">(${memberCount} Anggota)</span>
                `;
                unitsContainer.appendChild(unitChip);
            }

            // Equipment List
            document.getElementById('outPeralatan').innerText = game.tools;

            // Steps
            const stepsList = document.getElementById('outStepsList');
            stepsList.innerHTML = '';
            game.steps.forEach(step => {
                const li = document.createElement('li');
                li.innerText = step;
                stepsList.appendChild(li);
            });

            // Tips
            document.getElementById('outTips').innerText = game.tips || "Lakukan pengawasan adaptif sesuai karakteristik umur anggota.";

            // Safety Rules
            const safetyUl = document.getElementById('outSafety');
            safetyUl.innerHTML = '';
            const safetyItems = game.safety || [
                "Pastikan area kegiatan bebas dari permukaan licin dan benda tajam.",
                "Siapkan perlengkapan P3K standar di dekat lokasi."
            ];
            safetyItems.forEach(s => {
                const li = document.createElement('li');
                li.innerText = s;
                safetyUl.appendChild(li);
            });

            // Character Values (Kode Kehormatan)
            const characterUl = document.getElementById('outCharacter');
            characterUl.innerHTML = '';
            const charItems = game.character || [
                "Informasi nilai karakter khusus tidak dicantumkan dalam sumber permainan."
            ];
            charItems.forEach(c => {
                const li = document.createElement('li');
                li.className = "flex items-start gap-1.5";
                li.innerHTML = `<i class="fa-solid fa-check text-emerald-600 mt-0.5 text-[10px]"></i> <span>${c}</span>`;
                characterUl.appendChild(li);
            });

            // Signatures
            document.getElementById('outSignKetua').innerText = ketuaGudep;
            document.getElementById('outSignPembina').innerText = pembina;

            // Show Module Container
            document.getElementById('emptyState').classList.add('hidden');
            document.getElementById('printArea').classList.remove('hidden');

            // Scroll on Mobile
            if (window.innerWidth < 1024) {
                document.getElementById('printArea').scrollIntoView({ behavior: 'smooth' });
            }
                generateButton.disabled = false;
                generateButton.className = "w-full py-3.5 px-4 bg-emerald-600 hover:bg-emerald-500 text-white font-extrabold rounded-xl shadow-lg shadow-emerald-600/30 transition-all flex items-center justify-center space-x-2 text-sm tracking-wide";
                generateButton.innerHTML = '<i class="fa-solid fa-circle-check text-lg"></i><span>GENERATE BERHASIL</span>';
                generateStatus.className = "text-center text-sm font-bold text-emerald-400";
                generateStatus.innerText = "✓ Generate berhasil!";
            } catch (error) {
                console.error("Gagal membuat modul permainan:", error);
                generateButton.disabled = false;
                generateButton.className = "w-full py-3.5 px-4 bg-gradient-to-r from-amber-500 via-amber-600 to-orange-600 hover:from-amber-400 hover:to-orange-500 text-stone-950 font-extrabold rounded-xl shadow-lg shadow-amber-600/30 transition-all transform hover:-translate-y-0.5 flex items-center justify-center space-x-2 text-sm tracking-wide";
                generateButton.innerHTML = '<i class="fa-solid fa-fire-flame-curved text-lg"></i><span>GENERATE MODUL PERMAINAN</span>';
                generateStatus.className = "text-center text-sm font-bold text-red-400";
                generateStatus.innerText = "Generate gagal. Silakan coba kembali.";
                alert("Modul gagal dibuat. Silakan coba kembali.");
            } finally {
                isGenerating = false;
                rerollButton.disabled = false;
            }
        }

        // HELPER DATE FORMATTER
        function formatDateIndonesian(dateString) {
            if (!dateString) return "Selasa, 20 Oktober 2026";
            const days = ["Minggu", "Senin", "Selasa", "Rabu", "Kamis", "Jumat", "Sabtu"];
            const months = ["Januari", "Februari", "Maret", "April", "Mei", "Juni", "Juli", "Agustus", "September", "Oktober", "November", "Desember"];
            const d = new Date(dateString);
            if (isNaN(d.getTime())) return "Selasa, 20 Oktober 2026";
            return `${days[d.getDay()]}, ${d.getDate()} ${months[d.getMonth()]} ${d.getFullYear()}`;
        }

        // TAB SWITCHER
        function switchTab(tab) {
            if (tab === 'generator') {
                document.getElementById('tabGenerator').classList.remove('hidden');
                document.getElementById('tabKatalog').classList.add('hidden');
                document.getElementById('tabGenBtn').className = "px-5 py-2.5 rounded-lg font-bold text-xs sm:text-sm transition-all duration-200 bg-gradient-to-r from-amber-500 to-amber-600 text-stone-950 shadow-md flex items-center gap-2";
                document.getElementById('tabKatBtn').className = "px-5 py-2.5 rounded-lg font-bold text-xs sm:text-sm transition-all duration-200 text-stone-300 hover:text-white hover:bg-stone-800 flex items-center gap-2";
            } else {
                document.getElementById('tabGenerator').classList.add('hidden');
                document.getElementById('tabKatalog').classList.remove('hidden');
                document.getElementById('tabKatBtn').className = "px-5 py-2.5 rounded-lg font-bold text-xs sm:text-sm transition-all duration-200 bg-gradient-to-r from-amber-500 to-amber-600 text-stone-950 shadow-md flex items-center gap-2";
                document.getElementById('tabGenBtn').className = "px-5 py-2.5 rounded-lg font-bold text-xs sm:text-sm transition-all duration-200 text-stone-300 hover:text-white hover:bg-stone-800 flex items-center gap-2";
                renderKatalog();
            }
        }

        function updateGroupDefaults() {
            // Can adapt default team numbers if needed
        }

        // RENDER & FILTER KATALOG
        function renderKatalog(items) {
            const container = document.getElementById('katalogContainer');
            const dataToRender = items || GAME_DATABASE;
            container.innerHTML = '';

            dataToRender.forEach(g => {
                const card = document.createElement('div');
                card.className = "bg-stone-800 p-4 rounded-xl border border-stone-700 shadow-md hover:border-amber-500/50 transition flex flex-col justify-between";
                card.innerHTML = `
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <span class="text-[10px] font-extrabold px-2 py-0.5 bg-amber-500/20 text-amber-300 rounded border border-amber-500/30">
                                ${CATEGORY_MAP[g.cat] || "Umum"}
                            </span>
                            <span class="text-[10px] text-stone-500 font-mono">ID: #${g.id}</span>
                        </div>
                        <h4 class="font-bold text-stone-100 text-sm mb-1">${g.name}</h4>
                        <p class="text-xs text-stone-400 mb-3 line-clamp-2">${g.quote || g.tools}</p>
                    </div>
                    <div class="text-[11px] text-stone-400 pt-2.5 border-t border-stone-700/80 flex justify-between items-center">
                        <span>⏱️ ${g.dur || "Tidak dicantumkan"}</span>
                        <button onclick="useGameFromCatalog(${g.id})" class="text-amber-400 hover:text-amber-300 font-bold hover:underline flex items-center gap-1">
                            <span>Gunakan</span> <i class="fa-solid fa-arrow-right text-[10px]"></i>
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function filterKatalog() {
            const search = document.getElementById('searchKatalog').value.toLowerCase();
            const cat = document.getElementById('filterKategori').value;

            const filtered = GAME_DATABASE.filter(g => {
                const searchableText = [g.name, g.tools, g.tips, ...g.steps].join(' ').toLowerCase();
                const matchSearch = searchableText.includes(search);
                const matchCat = (cat === 'ALL') || (g.cat === cat);
                return matchSearch && matchCat;
            });

            renderKatalog(filtered);
        }

        function useGameFromCatalog(id) {
            const game = GAME_DATABASE.find(g => g.id === id);
            if (!game) return;

            // Switch to generator tab and select category
            switchTab('generator');
            document.querySelectorAll('input[name="kategori"]').forEach(cb => {
                cb.checked = (cb.value === game.cat);
            });
            generateGame(null, id);
        }

        function toggleModuleEdit() {
            const button = document.getElementById('moduleEditButton');
            const isEditing = button.dataset.editing === "true";
            const editableElements = document.querySelectorAll(
                '#outGudep, #outPangkalan, #outTingkatan, #outKategori, #outDurasi, #outPeserta, #outTanggal, ' +
                '#outNamaGame, #outQuoteGame, #outGamePlayers, #outGroupTitle, #outGroupSummary, #outUnitsContainer, ' +
                '#outPeralatan, #outStepsList, #outTips, #outSafety, #outCharacter, #outSignKetua, #outSignPembina'
            );

            editableElements.forEach(element => {
                element.contentEditable = String(!isEditing);
            });

            button.dataset.editing = String(!isEditing);
            button.innerHTML = isEditing
                ? '<i class="fa-solid fa-pen-to-square"></i><span>Edit Modul</span>'
                : '<i class="fa-solid fa-check"></i><span>Selesai Edit</span>';
            button.setAttribute('aria-pressed', String(!isEditing));
        }

        function escapeWordHtml(value) {
            return String(value)
                .replace(/&/g, '&amp;')
                .replace(/</g, '&lt;')
                .replace(/>/g, '&gt;')
                .replace(/"/g, '&quot;')
                .replace(/'/g, '&#39;');
        }

        function downloadWord() {
            const getText = id => document.getElementById(id).innerText.trim();
            const text = {
                gudep: getText('outGudep'),
                pangkalan: getText('outPangkalan'),
                tingkat: getText('outTingkatan'),
                kategori: getText('outKategori'),
                durasi: getText('outDurasi'),
                peserta: getText('outPeserta'),
                tanggal: getText('outTanggal'),
                nama: getText('outNamaGame'),
                quote: getText('outQuoteGame'),
                jumlahPemain: getText('outGamePlayers').replace(/^Jumlah pemain sesuai sumber:\s*/i, ''),
                groupSummary: getText('outGroupSummary'),
                peralatan: getText('outPeralatan'),
                tips: getText('outTips'),
                ketua: getText('outSignKetua'),
                pembina: getText('outSignPembina')
            };
            const groupTitleElement = document.querySelector('#outGroupTitle span');
            const groupTitle = groupTitleElement ? groupTitleElement.innerText.trim() : 'Pembagian Kelompok';
            const units = Array.from(document.querySelectorAll('#outUnitsContainer > div'))
                .map(unit => `<td>${escapeWordHtml(unit.innerText.trim())}</td>`);
            const steps = Array.from(document.querySelectorAll('#outStepsList li'))
                .map(step => `<li>${escapeWordHtml(step.innerText.trim())}</li>`).join('');
            const safety = Array.from(document.querySelectorAll('#outSafety li'))
                .map(item => `<li>${escapeWordHtml(item.innerText.trim())}</li>`).join('');
            const character = Array.from(document.querySelectorAll('#outCharacter li'))
                .map(item => `<li>${escapeWordHtml(item.innerText.trim())}</li>`).join('');
            const metadata = [
                ['Tingkatan', text.tingkat],
                ['Kategori', text.kategori],
                ['Target durasi', text.durasi],
                ['Jumlah peserta', text.peserta],
                ['Tanggal latihan', text.tanggal]
            ];
            const metadataRows = [];
            for (let index = 0; index < metadata.length; index += 2) {
                const cells = metadata.slice(index, index + 2)
                    .map(([label, value]) => `<td><strong>${escapeWordHtml(label)}</strong><br>${escapeWordHtml(value)}</td>`)
                    .join('');
                metadataRows.push(`<tr>${cells}${metadata.length - index === 1 ? '<td></td>' : ''}</tr>`);
            }
            const optionalSourceDetails = [
                text.quote ? `<p class="quote">${escapeWordHtml(text.quote)}</p>` : '',
                text.jumlahPemain ? `<p class="source-detail"><strong>Jumlah pemain sesuai sumber:</strong> ${escapeWordHtml(text.jumlahPemain)}</p>` : ''
            ].join('');
            const unitRows = [];
            for (let index = 0; index < units.length; index += 2) {
                unitRows.push(`<tr>${units.slice(index, index + 2).join('')}${units.length - index === 1 ? '<td></td>' : ''}</tr>`);
            }
            const wordDocument = `<!DOCTYPE html>
<html xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:w="urn:schemas-microsoft-com:office:word" lang="id">
<head>
<meta charset="utf-8">
<title>${escapeWordHtml(text.nama)} - Modul Permainan Pramuka</title>
<style>
@page { size: 21cm 29.7cm; margin: 1.6cm 1.7cm; }
body { font-family: Arial, sans-serif; color: #292524; font-size: 10pt; line-height: 1.45; }
.document { width: 100%; }
.letterhead { width: 100%; border-collapse: collapse; border-bottom: 3px double #292524; margin-bottom: 16pt; }
.letterhead td { text-align: center; padding: 3pt; }
.eyebrow { font-size: 9pt; font-weight: bold; letter-spacing: 2pt; color: #57534e; }
.institution { font-size: 16pt; font-weight: bold; margin: 3pt 0; }
.pangkalan { color: #57534e; }
.module-label { display: inline-block; margin-top: 8pt; padding: 5pt 14pt; background: #292524; color: #fff; font-weight: bold; letter-spacing: 1pt; }
.metadata { width: 100%; border-collapse: collapse; margin: 12pt 0 16pt; }
.metadata td { width: 50%; border: 1px solid #d6d3d1; background: #f5f5f4; padding: 7pt 9pt; vertical-align: top; }
.metadata strong { color: #78716c; font-size: 8pt; text-transform: uppercase; }
h1 { font-size: 20pt; color: #1c1917; margin: 0 0 5pt; }
h2 { font-size: 10pt; color: #292524; text-transform: uppercase; letter-spacing: .5pt; border-bottom: 1px solid #d6d3d1; padding-bottom: 4pt; margin: 16pt 0 7pt; }
.quote { color: #57534e; font-style: italic; border-left: 3px solid #d97706; padding-left: 9pt; }
.source-detail { color: #57534e; font-size: 9pt; }
.group-table, .signatures { width: 100%; border-collapse: collapse; }
.group-table td { width: 50%; border: 1px solid #e7e5e4; padding: 5pt 7pt; }
.content-box { border: 1px solid #e7e5e4; background: #fafaf9; padding: 8pt 10pt; }
ol, ul { margin: 4pt 0; padding-left: 20pt; }
li { margin-bottom: 4pt; }
.tips { border: 1px solid #fcd34d; background: #fffbeb; padding: 8pt 10pt; }
.safety { border: 1px solid #fecaca; background: #fef2f2; padding: 8pt 10pt; }
.character { border: 1px solid #a7f3d0; background: #ecfdf5; padding: 8pt 10pt; }
.signatures { margin-top: 28pt; }
.signatures td { width: 50%; text-align: center; vertical-align: top; padding: 5pt 15pt; }
.signature-space { height: 55pt; }
tr, li { page-break-inside: avoid; }
</style>
</head>
<body><div class="document">
<table class="letterhead"><tr><td>
<div class="eyebrow">GERAKAN PRAMUKA GUGUS DEPAN</div>
<div class="institution">${escapeWordHtml(text.gudep)}</div>
<div class="pangkalan">${escapeWordHtml(text.pangkalan)}</div>
<div class="module-label">MODUL PERMAINAN LATIHAN</div>
</td></tr></table>
<table class="metadata">${metadataRows.join('')}</table>
<h1>${escapeWordHtml(text.nama)}</h1>
${optionalSourceDetails}
<h2>${escapeWordHtml(groupTitle)}</h2>
<p>${escapeWordHtml(text.groupSummary)}</p>
<table class="group-table">${unitRows.join('')}</table>
<h2>Alat &amp; Bahan yang Diperlukan</h2>
<div class="content-box">${escapeWordHtml(text.peralatan)}</div>
<h2>Langkah-langkah Pelaksanaan (Cara Main)</h2>
<ol>${steps}</ol>
<h2>Tips &amp; Variasi Pembina</h2>
<div class="tips">${escapeWordHtml(text.tips)}</div>
<h2>Instruksi Keselamatan (Panduan Umum)</h2>
<div class="safety"><ul>${safety}</ul></div>
<h2>Penanaman Nilai Kode Kehormatan Pramuka</h2>
<div class="character"><ul>${character}</ul></div>
<table class="signatures"><tr>
<td><strong>Mengetahui,</strong><br>Ketua Gudep / Kak Pembina<div class="signature-space"></div><strong><u>${escapeWordHtml(text.ketua)}</u></strong></td>
<td><strong>Pembuat Modul,</strong><br>Pelatih / Pembina Pendamping<div class="signature-space"></div><strong><u>${escapeWordHtml(text.pembina)}</u></strong></td>
</tr></table>
</div></body></html>`;
            const blob = new Blob(['\ufeff', wordDocument], { type: 'application/msword;charset=utf-8' });
            const fileName = (text.nama || 'modul-permainan-pramuka')
                .normalize('NFKD')
                .replace(/[\u0300-\u036f]/g, '')
                .replace(/[<>:"/\\|?*\x00-\x1f]/g, '')
                .trim()
                .replace(/\s+/g, '-')
                .toLowerCase() || 'modul-permainan-pramuka';
            const downloadLink = document.createElement('a');
            downloadLink.href = URL.createObjectURL(blob);
            downloadLink.download = `${fileName}.doc`;
            document.body.appendChild(downloadLink);
            downloadLink.click();
            downloadLink.remove();
            setTimeout(() => URL.revokeObjectURL(downloadLink.href), 1000);
        }

        // COPY MODULE TEXT TO CLIPBOARD
        function copyModuleText() {
            const gudep = document.getElementById('outGudep').innerText;
            const pangkalan = document.getElementById('outPangkalan').innerText;
            const tingkatan = document.getElementById('outTingkatan').innerText;
            const kategori = document.getElementById('outKategori').innerText;
            const durasi = document.getElementById('outDurasi').innerText;
            const peserta = document.getElementById('outPeserta').innerText;
            const tanggal = document.getElementById('outTanggal').innerText;
            const nama = document.getElementById('outNamaGame').innerText;
            const quote = document.getElementById('outQuoteGame').innerText;
            const jumlahPemainSumber = document.getElementById('outGamePlayers').innerText;
            const groupTitle = document.getElementById('outGroupTitle').innerText;
            const groupSummary = document.getElementById('outGroupSummary').innerText;
            const peralatan = document.getElementById('outPeralatan').innerText;
            const tips = document.getElementById('outTips').innerText;

            let stepsText = "";
            document.querySelectorAll('#outStepsList li').forEach((li, idx) => {
                stepsText += `${idx + 1}. ${li.innerText}\n`;
            });

            let safetyText = "";
            document.querySelectorAll('#outSafety li').forEach((li) => {
                safetyText += `- ${li.innerText}\n`;
            });

            let characterText = "";
            document.querySelectorAll('#outCharacter li span').forEach((span) => {
                characterText += `- ${span.innerText}\n`;
            });

            const fullText = 
`GERAKAN PRAMUKA GUGUS DEPAN
${gudep}
${pangkalan}
MODUL PERMAINAN LATIHAN

TINGKATAN: ${tingkatan}
Kategori: ${kategori}
Target Durasi: ${durasi}
Jumlah Peserta: ${peserta}
Tanggal Latihan: ${tanggal}

${nama}
${quote}
${jumlahPemainSumber}

${groupTitle}
${groupSummary}

ALAT & BAHAN YANG DIPERLUKAN:
${peralatan}

LANGKAH-LANGKAH PELAKSANAAN (CARA MAIN):
${stepsText}
Tips & Variasi Pembina:
${tips}

INSTRUKSI KESELAMATAN (SAFETY RULES):
${safetyText}
PENANAMAN NILAI KODE KEHORMATAN PRAMUKA:
${characterText}

Mengetahui,
Ketua Gudep / Kak Pembina: ${document.getElementById('outSignKetua').innerText}

Pembuat Modul,
Pelatih / Pembina Pendamping: ${document.getElementById('outSignPembina').innerText}`;

            navigator.clipboard.writeText(fullText).then(() => {
                alert("Modul Latihan berhasil disalin ke clipboard!");
            }).catch(() => {
                alert("Gagal menyalin teks.");
            });
        }
    </script>
</body>
</html>
