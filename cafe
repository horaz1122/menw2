<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مینووی کافێ - سیستەمی داواکاری</title>
    <!-- وەشانی CDNـی Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- زیادکردنی کتێبخانەی QR Code -->
    <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>

    <style type="text/tailwindcss">
        @tailwind base;
        @tailwind components;
        @tailwind utilities;

        /* ... [هەموو ستایلە CSSـەکانی خۆت لێرە بوون - وەک خۆی دامناوەتەوە] ... */
        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
            @apply bg-gray-900 text-gray-200 transition-colors duration-500;
        }

        /* ستایلی بنەڕەتی (گەرم) */
        .theme-container {
            @apply bg-gray-800 shadow-2xl border-4 border-yellow-700 transition-all duration-500;
        }
        .theme-header {
            @apply bg-yellow-900/20 border-b-4 border-yellow-700 transition-all duration-500;
        }
        .theme-header-title {
            @apply text-yellow-400 transition-all duration-500;
        }
        .theme-header-subtitle {
            @apply text-yellow-200 transition-all duration-500;
        }
        .theme-nav {
            @apply bg-gray-800/90 border-b border-gray-700 transition-all duration-500;
        }
        .theme-nav-btn {
            @apply text-yellow-200 bg-yellow-800/50 hover:bg-yellow-800/80 transition-all duration-300;
        }
        .theme-nav-btn.active {
            @apply bg-yellow-400 text-gray-900 font-bold ring-2 ring-yellow-300;
        }
        .theme-section-title {
            @apply text-yellow-400 transition-all duration-500;
        }
        .theme-section-divider {
            @apply bg-yellow-700 transition-all duration-500;
        }
        .theme-item-card {
            @apply bg-gray-900/50 border border-yellow-800 hover:border-yellow-600 hover:shadow-xl transition-all duration-300;
        }
        .theme-item-image-border {
            @apply border-yellow-700 transition-all duration-500;
        }
        .theme-item-name {
            @apply text-yellow-400 transition-all duration-500;
        }
        .theme-item-price {
            @apply text-yellow-200 transition-all duration-500;
        }
        .theme-footer {
            @apply bg-yellow-900/20 border-t-4 border-yellow-700 text-yellow-200 transition-all duration-500;
        }

        /* ستایلی سارد - کاتێک کلاسی .cold-theme زیاد دەبێت */
        .cold-theme .theme-container {
            @apply bg-blue-900 border-blue-400;
        }
        .cold-theme .theme-header {
            @apply bg-blue-900/20 border-b-4 border-blue-400;
        }
        .cold-theme .theme-header-title {
            @apply text-blue-300;
        }
        .cold-theme .theme-header-subtitle {
            @apply text-blue-100;
        }
        .cold-theme .theme-nav {
            @apply bg-blue-900/90 border-b border-blue-700;
        }
        .cold-theme .theme-nav-btn {
            @apply text-blue-200 bg-blue-800/50 hover:bg-blue-800/80;
        }
        .cold-theme .theme-nav-btn.active {
            @apply bg-blue-300 text-blue-900 font-bold ring-2 ring-blue-200;
        }
        .cold-theme .theme-section-title {
            @apply text-blue-300;
        }
        .cold-theme .theme-section-divider {
            @apply bg-blue-400;
        }
        .cold-theme .theme-item-card {
            @apply bg-blue-950/50 border border-blue-700 hover:border-blue-500;
        }
        .cold-theme .theme-item-image-border {
            @apply border-blue-400;
        }
        .cold-theme .theme-item-name {
            @apply text-blue-300;
        }
        .cold-theme .theme-item-price {
            @apply text-blue-100;
        }
        .cold-theme .theme-footer {
            @apply bg-blue-900/20 border-t-4 border-blue-400 text-blue-200;
        }

        /* ستایلی تایبەت بۆ کارتی پۆلەکان لە بەشی سارددا */
        .cold-category-card {
            @apply flex-col text-center p-6 cursor-pointer bg-blue-800/50 border-blue-600 hover:bg-blue-800/80;
        }
        .cold-category-card .item-image {
            @apply w-28 h-28 rounded-lg border-blue-400;
        }
        .cold-category-card .item-name {
            @apply text-xl text-blue-200 mt-4;
        }
        .cold-category-card .item-price {
            @apply hidden; /* نرخەکان بشارەوە بۆ کارتی پۆلەکان */
        }
        
        /* شاردنەوەی بەشەکان و پۆلەکانی خواردن */
        .menu-section, .food-category {
            display: none;
        }
        .menu-section.active, .food-category.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        /* ئەنیمەیشنی هاتنەناوەوە */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* بۆ شریتی سکڕۆڵی مۆبایل */
        .category-nav::-webkit-scrollbar {
            display: none; /* شاردنەوەی سکڕۆڵبار */
        }
        .category-nav {
            -ms-overflow-style: none;  /* IE and Edge */
            scrollbar-width: none;  /* Firefox */
        }

        /* ستایلە زیادکراوەکان بۆ سیستەمی ئەدمین و سەبەتە */
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        
        #cartButton {
            @apply fixed bottom-4 left-4 z-[100] bg-yellow-400 text-gray-900 rounded-full w-16 h-16 flex items-center justify-center shadow-lg transition-transform hover:scale-110;
        }
        #cartButton.cold-theme {
             @apply bg-blue-300 text-blue-900;
        }
        #cartCount {
            @apply absolute -top-2 -right-2 bg-red-600 text-white text-xs font-bold rounded-full w-6 h-6 flex items-center justify-center;
        }

        #cartModal {
            @apply fixed inset-0 bg-black/80 z-[200] flex items-center justify-center p-4 transition-opacity duration-300;
        }
        
        /* ستایلی پسوڵەی چاپکردن */
        @media print {
            body * {
                visibility: hidden;
            }
            #receiptToPrint, #receiptToPrint * {
                visibility: visible;
            }
            #receiptToPrint {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                font-family: 'Courier New', Courier, monospace;
                padding: 10px;
                font-size: 10px;
            }
            #receiptToPrint h3 {
                font-size: 14px;
                font-weight: bold;
                text-align: center;
            }
            #receiptToPrint p {
                margin: 2px 0;
            }
            #receiptToPrint table {
                width: 100%;
                font-size: 10px;
            }
            #receiptToPrint th {
                text-align: right;
                border-bottom: 1px dashed #000;
            }
            #receiptToPrint td {
                padding: 2px 0;
            }
        }
        /* کۆتایی ستایلی چاپکردن */
        
    </style>
</head>
<body class="bg-gray-900">

    <!-- پەیامی کۆتاییهاتن (وەک خۆی) -->
    <div class="expired-message fixed inset-0 bg-black/90 z-[1000] flex items-center justify-center p-4" id="expiredMessage" style="display: none;">
        <div class="expired-content bg-gray-800 rounded-lg shadow-xl p-6 md:p-8 max-w-md w-full border-4 border-red-600 text-center">
            <h2 class="expired-title text-2xl md:text-3xl font-bold text-red-400 mb-4">پەیوەندی بکە بە دروستکەری وێبسایتەکە</h2>
            <p class="expired-text text-base md:text-lg mb-6 text-gray-200">ئەم وێبسایتە ماوەی کارکردنی تەواو بووە. تکایە پەیوەندی بکە بە دروستکەری وێبسایتەکە بۆ نوێکردنەوە.</p>
            <div class="contact-info bg-gray-700/50 p-4 rounded-lg text-right text-gray-300">
                <p><strong>ناو:</strong> horaz IT</p>
                <p><strong>ژمارەی مۆبایل:</strong> 07501784002</p>
                <p><strong>خزمەتگوزاری:</strong> دروستکردنی هەموو جۆرە سیستەم و وێبسایتێک</p>
            </div>
        </div>
    </div>

    <!-- 
    ======================================
    پەڕەی چوونەژوورەوەی ئەدمین
    ======================================
    -->
    <div id="loginPage" class="page active">
        <div class="flex items-center justify-center min-h-screen bg-gray-900 p-4">
            <div class="bg-gray-800 p-8 md:p-12 rounded-lg shadow-2xl w-full max-w-md border-4 border-yellow-700">
                <h1 class="text-3xl font-bold text-yellow-400 text-center mb-6">چوونەژوورەوەی ئەدمین</h1>
                <p class="text-gray-300 text-center mb-6">تکایە وشەی نهێنی بنووسە بۆ چوونە ناو سیستەمی بەڕێوەبردن.</p>
                
                <input type="password" id="adminPassword" class="w-full p-3 rounded-lg bg-gray-900 border border-gray-700 text-white text-center focus:outline-none focus:ring-2 focus:ring-yellow-500" placeholder="••••••••">
                
                <button id="loginButton" class="w-full mt-6 bg-yellow-400 text-gray-900 font-bold p-3 rounded-lg hover:bg-yellow-300 transition-colors">
                    چوونەژوورەوە
                </button>
                
                <button id="goToMenuButton" class="w-full mt-4 bg-transparent border border-gray-700 text-gray-400 font-medium p-3 rounded-lg hover:bg-gray-700 transition-colors">
                    چوون بۆ مینووی خواردن
                </button>
            </div>
        </div>
    </div>

    <!-- 
    ======================================
    پەڕەی مینووی کڕیار (کۆدی خۆت)
    ======================================
    -->
    <div id="menuPage" class="page">
        <!-- دەفرە سەرەکییەکە -->
        <div class="container theme-container max-w-7xl mx-auto rounded-none md:rounded-lg overflow-hidden my-0 md:my-8" id="mainContainer">
            
            <!-- سەردێڕ -->
            <header class="theme-header text-center p-8 md:p-16 relative overflow-hidden">
                <!-- ئایمۆجییەکە لە پاشتەوە وەک ستایلی پێشوو -->
                <div class="absolute inset-0 flex items-center justify-center text-[200px] opacity-10" id="header-icon">☕</div>
                
                <h1 class="theme-header-title text-4xl md:text-6xl font-bold relative z-10">پاشافروتی کــافــێ</h1>
                <p class="theme-header-subtitle text-xl md:text-2xl font-light italic mt-4 relative z-10">تامی ئاسایشی ڕاستەقینە</p>

                <!-- زیادکراو: دوگمەی چوونە بەشی ئەدمین -->
                <button id="goToAdminLogin" class="absolute top-4 right-4 bg-yellow-400/30 text-yellow-200 px-3 py-1 rounded-full text-xs hover:bg-yellow-400/50 backdrop-blur-sm z-20">
                    ئەدمین
                </button>
            </header>

            <!-- ناڤیگەیشنی بەشەکان (گونجاو بۆ مۆبایل بە سکڕۆڵ) -->
            <div class="category-nav theme-nav sticky top-0 z-50 p-4 overflow-x-auto backdrop-blur-sm">
                <div class="flex gap-3 whitespace-nowrap max-w-full mx-auto justify-start md:justify-center">
                    <button class="category-btn theme-nav-btn px-5 py-2 rounded-full font-medium text-sm md:text-base active" data-category="all">هەموو</button>
                    <button class="category-btn theme-nav-btn px-5 py-2 rounded-full font-medium text-sm md:text-base" data-category="hot">خواردنەوە گەرمەکان</button>
                    <button class="category-btn theme-nav-btn px-5 py-2 rounded-full font-medium text-sm md:text-base" data-category="cold">خواردنەوە ساردەکان</button>
                    <button class="category-btn theme-nav-btn px-5 py-2 rounded-full font-medium text-sm md:text-base" data-category="dessert">کریپ نۆتێلا</button>
                    <button class="category-btn theme-nav-btn px-5 py-2 rounded-full font-medium text-sm md:text-base" data-category="drinks">کونافەکان</button>
                </div>
            </div>

            <!-- ناوەڕۆکی مینو -->
            <div class="menu-content p-4 md:p-10">
                
                <!-- خواردنەوە گەرمەکان -->
                <div class="menu-section" data-category="hot">
                    <div class="section-header text-center mb-8">
                        <h2 class="section-title theme-section-title text-3xl md:text-4xl font-bold">بەشی خواردنەوەگەرمەکان</h2>
                        <div class="section-divider theme-section-divider h-1 w-24 mx-auto mt-4"></div>
                    </div>
                    <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                        <!-- ئایتمەکان لێرە دادەنرێن -->
                        <!-- 
                            تێبینی: دوگمەی 'زیادکردن' بە شێوەی ئۆتۆماتیکی
                            لەلایەن جاڤاسکریپتەوە بۆ هەموو ئایتمەکان زیاد دەکرێت 
                        -->
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/Y72mDxH3/m1.png" alt="محەلەبی گەرم" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">محەلەبی گەرم</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/DPG04BDH/k1-387Z.png" alt="کاستەری گەرم" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کاستەری گەرم</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <!-- ... [هەموو ئایتمەکانی تری بەشی گەرم] ... -->
                         <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/RkhK7ZDX/q1-111Z.png" alt="قاوەی ئێسپرێسۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">قاوەی ئێسپرێسۆ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://images.unsplash.com/photo-1517487881594-2787fef5ebf7?w=300&h=300&fit=crop" alt="کافێ مۆکا" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کافێ مۆکا</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">4,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://images.unsplash.com/photo-1485808191679-5f86510681a2?w=300&h=300&fit=crop" alt="قاوەی تورکی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">قاوەی تورکی</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/S7tq2y6r/a1-222Z.png" alt="ئەمریکانۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئەمریکانۆ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
              _message_num_limit
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/pBLgdX8d/h1-831Z.png" alt="هۆت چوکولێت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">هۆت چوکولێت</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
        _message_num_limit
                  <img src="https://i.ibb.co/NgpL8YGV/q2-651Z.png" alt="قاوەی قەزوان" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">قاوەی قەزوان</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/n80ntPmN/k2-590Z.png" alt="کاپوچینۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کاپوچینۆ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                _message_num_limit
    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/pr6BNtyh/k3-079Z.png" alt="کافێ لاتێ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کافێ لاتێ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/gbb2tHs4/m2-631Z.png" alt="مۆکا" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکا</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/NnGCwxxw/m3-695Z.png" alt="ماکیاتۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ماکیاتۆ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/FqqSTqG0/a2-499Z.png" alt="ئەڤەگاتۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئەڤەگاتۆ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/GQTdzqqZ/f1-819Z.png" alt="فراپی یۆنانی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">فراپی یۆنانی</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    </div>
                </div>

                <!-- خواردنەوە ساردەکان -->
                <div class="menu-section" data-category="cold">
                    <div class="section-header text-center mb-8">
                        <h2 class="section-title theme-section-title text-3xl md:text-4xl font-bold">بەشی خواردنەوە ساردەکان</h2>
                        <div class="section-divider theme-section-divider h-1 w-24 mx-auto mt-4"></div>
                    </div>
                    <!-- پۆلەکانی خواردنەوە ساردەکان (وەک دوگمە دیارن) -->
                    <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                        <div class="menu-item theme-item-card cold-category-card rounded-lg shadow-lg" data-category="iced-coffee">
                            <img src="https://i.ibb.co/nN5QZf47/sh1-729Z.png" alt="شەربەتی فرێس" class="item-image theme-item-image-border" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info">
                                <div class="item-header justify-center">
                                    <h3 class="item-name theme-item-name">بەشی شەربەتی فرێس</h3>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card cold-category-card rounded-lg shadow-lg" data-category="frappe">
                            <img src="https://i.ibb.co/WpDzLwZD/sh2-040Z.png" alt="شەربەتی فرێش شەیک" class="item-image theme-item-image-border" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info">
                                <div class="item-header justify-center">
                                    <h3 class="item-name theme-item-name">بەشی شەربەتی فرێش شەیک</h3>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card cold-category-card rounded-lg shadow-lg" data-category="iced-latte">
                            <img src="https://i.ibb.co/BSNY4mF/mk1-468Z.png" alt="مۆکتێل" class="item-image theme-item-image-border" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info">
                                <div class="item-header justify-center">
                                    <h3 class="item-name theme-item-name">بەشی مۆکتێل</h3>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card cold-category-card rounded-lg shadow-lg" data-category="cold-brew">
                            <img src="https://i.ibb.co/MDfwGbNR/shm-990Z.png" alt="شیرمۆزەکان" class="item-image theme-item-image-border" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info">
                                <div class="item-header justify-center">
                                    <h3 class="item-name theme-item-name">بەشی شیرمۆزەکان</h3>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card cold-category-card rounded-lg shadow-lg" data-category="special">
                            <img src="https://i.ibb.co/wZWgjdJc/as1-264Z.png" alt="ئایسکرێمەکان" class="item-image theme-item-image-border" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info">
                                <div class="item-header justify-center">
                                    <h3 class="item-name theme-item-name">بەشی ئایسکرێمەکان</h3>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- پۆلەکانی خواردن (سەرەتا شاردراوەن) -->
                    <div class="food-category mt-8 bg-blue-950/30 p-4 md:p-6 rounded-lg" id="iced-coffee-category">
                        <h3 class="food-category-title theme-section-title text-2xl font-bold text-center mb-6">بەشی شەربەتەفرێشەکان</h3>
                        <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                            <!-- ئایتمەکانی ئەم پۆلە -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                                <img src="https://i.ibb.co/HLdqmnNt/pq-518Z.png" alt="پرتەقاڵی فرێش" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                                <div class="item-info flex-1 min-w-0">
                                    <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                        <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">پرتەقاڵی فرێش</h3>
                                        <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                    </div>
                                </div>
                            </div>
                            <!-- ... [هەموو ئایتمەکانی تری بەشی سارد - پۆلی ١] ... -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/hR0xkfXP/shs-492Z.png" alt="سێوی سەوز" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">سێوی سەوز</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/vxQp7v4v/g-019Z.png" alt="گێزەر" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">گێزەر</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/9kDcXr8V/sn-299Z.png" alt="سندی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">سندی</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/zHm38grF/ha-630Z.png" alt="هەنار" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">هەنار</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/twgTCqVV/za-582Z.png" alt="زەنجەفیل" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">زەنجەفیل</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/WvYnhCvP/ka-713Z.png" alt="کاڵەک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کاڵەک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/WpGSsLHZ/le-471Z.png" alt="لیمۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">لیمۆ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/cXSNJZBV/han-113Z.png" alt="هەنجیر" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">هەنجیر</h3>
                _message_num_limit
                      <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/nqyzcvD0/qo-164Z.png" alt="قۆخ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">قۆخ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/QFfpSv1T/shl-335Z.png" alt="شلک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شلک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/yFzGggXn/an-596Z.png" alt="ئەناناس" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئەناناس</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/r25TNK5r/ko-027Z.png" alt="کۆکتێلی میوەکان" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کۆکتێلی میوەکان</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
            _message_num_limit
              <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/03Z2sw9/ma-071Z.png" alt="مانگۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مانگۆ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">4,000 د.ع</span>
                              _message_num_limit
                      </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/Gv2P7n2t/av-417Z.png" alt="ئەڤۆگادۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئەڤۆگادۆ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        </div>
                    </div>

                    <div class="food-category mt-8 bg-blue-950/30 p-4 md:p-6 rounded-lg" id="frappe-category">
                        <h3 class="food-category-title theme-section-title text-2xl font-bold text-center mb-6">بەشی شەربەتی فرێسی شەیک</h3>
                        <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                            <!-- ئایتمەکانی ئەم پۆلە -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                                <img src="https://i.ibb.co/9HKnrRBq/ml-482Z.png" alt="میڵک شەیکی سادە" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                                <div class="item-info flex-1 min-w-0">
                                    <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                        <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">میڵک شەیکی سادە</h3>
                                        <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                    </div>
                                </div>
                            </div>
                            <!-- ... [هەموو ئایتمەکانی تری بەشی سارد - پۆلی ٢] ... -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/C38C33bg/no-767Z.png" alt="نۆتێلاشەیک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">نۆتێلاشەیک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/MxGTVThT/fs-924Z.png" alt="فستق شەیک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">فستق شەیک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/VYYrkXrj/kr-751Z.png" alt="کرامێڵ شەیک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کرامێڵ شەیک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
            _message_num_limit
                  </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/kgbPH5QM/ch-038Z.png" alt="چوکولێت شەیک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">چوکولێت شەیک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/0pwYF337/mlk-814Z.png" alt="میڵک شەیکی تایبەت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">میڵک شەیکی تایبەت</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/20ZT7ZbY/sp-204Z.png" alt="سپێشڵ نۆتێلا شەیک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">سپێشڵ نۆتێلا شەیک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">4,000 د.ع</span>
                                </div>
                            </div>
      _message_num_limit
                    </div>
                        </div>
                    </div>

                    <div class="food-category mt-8 bg-blue-950/30 p-4 md:p-6 rounded-lg" id="iced-latte-category">
                        <h3 class="food-category-title theme-section-title text-2xl font-bold text-center mb-6">بەشی خواردنەوە مۆکتێلەکان</h3>
                        <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                            <!-- ئایتمەکانی ئەم پۆلە -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                                <img src="https://i.ibb.co/XZkrz36F/tgg.png" alt="تایگەر مەکسیکی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                                <div class="item-info flex-1 min-w-0">
                                    <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                        <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">تایگەر مەکسیکی</h3>
                                        <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                    </div>
                                </div>
                            </div>
                            <!-- ... [هەموو ئایتمەکانی تری بەشی سارد - پۆلی ٣] ... -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/HTDbgz9V/tgh-179Z.png" alt="تایگەرمەکسیکی هەنار" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">تایگەرمەکسیکی هەنار</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/xtvNxvkc/tgb-394Z.png" alt="بلو تایگەر مەکسیکی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">بلو تایگەر مەکسیکی</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/xrvGRW9/gsh-777Z.png" alt="شەربەتە شینەکە بلوکۆراسۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شەربەتە شینەکە بلوکۆراسۆ</h3>
                    _message_num_limit
                      <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/V0VyQbCP/mo-334Z.png" alt="مۆهیتۆ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆهیتۆ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/C3kdzV8j/moc-764Z.png" alt="مۆکتێلی چێری" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکتێلی چێری</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                        _message_num_limit
                    </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/k6rg7Ny5/mox-825Z.png" alt="نۆکتێلی قۆخ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">نۆکتێلی قۆخ</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/FLn93fy6/tm-883Z.png" alt="مۆکتێلی تەمەرهندی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکتێلی تەمەرهندی</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/zhw6zLXb/bl-780Z.png" alt="مۆکتێلی بلاک فلاوەر" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکتێلی بلاک فلاوەر</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/YBK1Pjhd/blw-900Z.png" alt="مۆکتێلی بلوهاوای" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکتێلی بلوهاوای</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/nKg68KL/ta-896Z.png" alt="مۆکتێلی تایبەت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">مۆکتێلی تایبەت</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        </div>
                    </div>

                    <div class="food-category mt-8 bg-blue-950/30 p-4 md:p-6 rounded-lg" id="cold-brew-category">
                        <h3 class="food-category-title theme-section-title text-2xl font-bold text-center mb-6">بەشی شیر مۆزەکان</h3>
                        <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                            <!-- ئایتمەکانی ئەم پۆلە -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                                <img src="https://i.ibb.co/nq8hTKNT/she-927Z.png" alt="شیرمۆزی سادە" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                                <div class="item-info flex-1 min-w-0">
                                    <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                        <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیرمۆزی سادە</h3>
                                        <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                    </div>
                                </div>
                            </div>
                            <!-- ... [هەموو ئایتمەکانی تری بەشی سارد - پۆلی ٤] ... -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/1tfQc3SY/shx-044Z.png" alt="شیر خورما" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیر خورما</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                                </div>
                            </div>
                _message_num_limit
              </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/zTbS8b7T/shk-620Z.png" alt="شیر کاڵەک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیر کاڵەک</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/0d3btsG/sho-060Z.png" alt="شۆفان" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شۆفان</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                    _message_num_limit
    </div>
                  _message_num_limit
      <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
        _message_num_limit
          <img src="https://i.ibb.co/dwdGHjNg/shh-553Z.png" alt="شیر هەنجیر" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیر هەنجیر</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/rfQZdr5g/shf-878Z.png" alt="شیر فستق" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیر فستق</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/bq4NZrx/shot-562-Z.png" alt="شیرمۆزی تایبەت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">شیرمۆزی تایبەت</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        </div>
                    </div>

                    <div class="food-category mt-8 bg-blue-950/30 p-4 md:p-6 rounded-lg" id="special-category">
                        <h3 class="food-category-title theme-section-title text-2xl font-bold text-center mb-6">بەشی ئایسکرێمەکان</h3>
                        <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                            <!-- ئایتمەکانی ئەم پۆلە -->
                            <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                                <img src="https://i.ibb.co/v4Tz8xb5/ass-324Z.png" alt="قاپ ئایسکرێم" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                                <div class="item-info flex-1 min-w-0">
                                    <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                        <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">قاپ ئایسکرێم ٣تام</h3>
                                        <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                    </div>
                                    <p class="item-description text-sm text-gray-400 italic mt-2">تامی ئایشکرێمەکان {شیر،ڤانێلا،جوکولێت،قاوە،کرامێڵ،هەنجیر،لیمۆ،قەیسی،کاڵەک،فستق }</p>
                                </div>
                            </div>
                            <!-- ... [هەموو ئایتمەکانی تری بەشی سارد - پۆلی ٥] ... -->
                             <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/b51G75LD/assm-237-Z.png" alt="ئایسکرێم بەمیوە" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئایسکرێم بەمیوە</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/fdktvZxW/asn-419Z.png" alt="ئایسکرێم نۆتێلا" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئایسکرێم نۆتێلا</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/tw8Ysjhp/ast-584Z.png" alt="ئایسکرێم تایبەت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/1e3a5f/87ceeb?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">ئایسکرێم تایبەت</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        </div>
                    </div>
                </div>

                <!-- کریپ نوتێلا -->
                <div class="menu-section" data-category="dessert">
                    <div class="section-header text-center mb-8">
                        <h2 class="section-title theme-section-title text-3xl md:text-4xl font-bold">بەشی کریپ نۆتێلا</h2>
                        <div class="section-divider theme-section-divider h-1 w-24 mx-auto mt-4"></div>
                    </div>
                    <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                        <!-- ئایتمەکان لێرە -->
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/60B7cKcq/km1-560Z.png" alt="کریپ نۆتێلای مۆز" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلای مۆز</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <!-- ... [هەموو ئایتمەکانی تری بەشی کریپ] ... -->
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/FbYJfkK4/km3-718Z.png" alt="کریپ نۆتێلای پسکیت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلای پسکیت</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/wvVpVk6/km4-243Z.png" alt="کریپ nۆتێلا سەرقاپ" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلا سەرقاپ</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/bj275kMw/km5-599Z.png" alt="کریپ نۆتێلای مۆزوپسکیت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلای مۆزوپسکیت</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">1,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/0pwtxHW8/km6-356Z.png" alt="کریپ نۆتێلابەگوێز" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلابەگوێز</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/TqW5FzpD/km7-201Z.png" alt="کریپ نۆتێلاشلک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلاشلک</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/gZr7wBVs/km8-974Z.png" alt="کریپ نۆتێلافستق" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلافستق</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/C4njmhC/km9-903Z.png" alt="کریپ نۆتێلامۆزوفستق" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلامۆزوفستق</h3>
                    _message_num_limit
                  <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,000 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/mVwRMrD6/km0-084Z.png" alt="کریپ نۆتێلامشەکەل" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلامشەکەل</h3>
              _message_num_limit
                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                            </div>
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/Cf1spz0/km01-594-Z.png" alt="کریپ نۆتێلاشاومەیی" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلاشاومەیی</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,000 د.ع</span>
s
                        </div>
                    </div>
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/LhYGpWv5/km02-870-Z.png" alt="کریپ نۆتێلای تایبەت" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کریپ نۆتێلای تایبەت</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,500 د.ع</span>
                            </div>
                        </div>
s
                    <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                        <img src="https://i.ibb.co/TDqsJg4B/km03-812-Z.png" alt="پانکێک" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                        <div class="item-info flex-1 min-w-0">
                            <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">پانکێک</h3>
                                <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,000 د.ع</span>
                            </div>
                        </div>
          _message_num_limit
                </div>
                    </div>
                </div>

                <!-- بەشی کونافەکان -->
                <div class="menu-section" data-category="drinks">
                    <div class="section-header text-center mb-8">
                        <h2 class="section-title theme-section-title text-3xl md:text-4xl font-bold">بەشی کونافە</h2>
                        <div class="section-divider theme-section-divider h-1 w-24 mx-auto mt-4"></div>
                    </div>
                    <div class="items-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                        <!-- ئایتمەکان لێرە -->
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/Y4sHpVFV/kw-936Z.png" alt="کونافەی پەنیر بەئایسکرێم" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کونافەی پەنیر بەئایسکرێم</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">2,500 د.ع</span>
                                </div>
                            </div>
                        </div>
                        <div class="menu-item theme-item-card rounded-lg shadow-lg overflow-hidden flex items-center gap-4 p-4">
                            <img src="https://i.ibb.co/6RdXvCHj/kwf-886Z.png" alt="کونافەی فستق زادەبەئایسکرێم" class="item-image theme-item-image-border w-20 h-20 md:w-24 md:h-24 rounded-full object-cover border-4 flex-shrink-0" onerror="this.src='https://placehold.co/100x100/3e2723/d4a574?text=وێنە'">
                            <div class="item-info flex-1 min-w-0">
                                <div class="item-header flex flex-col sm:flex-row justify-between items-start sm:items-center gap-1 sm:gap-2">
                                    <h3 class="item-name theme-item-name text-lg md:text-xl font-semibold truncate">کونافەی فستق زادەبەئایسکرێم</h3>
                                    <span class="item-price theme-item-price text-base md:text-lg font-bold whitespace-nowrap">3,000 د.ع</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>

            <!-- فووتەر -->
            <footer class="theme-footer text-center p-8 md:p-12">
                <div class="footer-content max-w-3xl mx-auto">
                    <div class="coffee-beans text-3xl mb-6 opacity-50" id="footer-icon">☕ ☕ ☕</div>
                    <p class="footer-info text-lg md:text-xl mb-2">کاتەکانی کارکردن: ٨:٠٠ بەیانی - ١٢:٠٠ شەو</p>
                    <p class="footer-info text-lg md:text-xl">هەموو ڕۆژێک</p>
                    <p class="mt-8 opacity-70 text-sm">
                        horaz IT <br>
                        ئامادەی بۆ دروست کردنی هەموو جۆرە سیستەمێکو وێب سایتەک <br>
                        07501784002
                    </p>
                </div>
            </footer>
        </div>

        <!-- 
        ======================================
        زیادکراوەکان: سەبەتەی کڕین و مۆداڵ
        ======================================
        -->
        <button id="cartButton" class="" title="سەبەتەی کڕین">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            <span id="cartCount" class="hidden">0</span>
        </button>

        <!-- مۆداڵی سەبەتە -->
        <div id="cartModal" class="hidden" style="opacity: 0; pointer-events: none;">
            <div class="theme-container w-full max-w-lg bg-gray-800 rounded-lg shadow-2xl p-6 relative transition-transform duration-300" style="transform: scale(0.95);">
                <!-- دوگمەی داخستن -->
                <button id="closeCartButton" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>

                <h2 class="theme-section-title text-yellow-400 text-3xl font-bold text-center mb-6">سەبەتەی داواکاری</h2>
                
                <div id="cartItemsContainer" class="max-h-64 overflow-y-auto divide-y divide-gray-700 pr-2">
                    <!-- ئایتمەکانی سەبەتە لێرە زیاد دەبن -->
                    <p class="text-gray-400 text-center py-4">سەبەتەکەت بەتاڵە.</p>
                </div>

                <div class="mt-6 border-t border-gray-700 pt-4">
                    <div class="flex justify-between items-center text-xl font-bold">
                        <span class="theme-item-name text-yellow-400">کۆی گشتی:</span>
                        <span id="cartTotal" class="theme-item-price text-yellow-200">0 د.ع</span>
                    </div>
                </div>

                <button id="submitOrderButton" class="w-full mt-6 bg-yellow-400 text-gray-900 font-bold p-3 rounded-lg hover:bg-yellow-300 transition-colors disabled:opacity-50" disabled>
                    ناردنی داواکاری
                </button>
            </div>
        </div>

    </div> <!-- کۆتایی menuPage -->


    <!-- 
    ======================================
    پەڕەی ئەدمین
    ======================================
    -->
    <div id="adminPage" class="page">
        <div class="container mx-auto p-4 md:p-8 bg-gray-900 min-h-screen">
            <header class="flex flex-col md:flex-row justify-between items-center mb-8 pb-4 border-b border-gray-700">
                <h1 class="text-4xl font-bold text-yellow-400">پەڕەی ئەدمین</h1>
                <button id="logoutButton" class="w-full md:w-auto mt-4 md:mt-0 bg-red-600 text-white font-bold p-3 rounded-lg hover:bg-red-700 transition-colors">
                    دەرچوون
                </button>
            </header>

            <!-- بەشی دروستکردنی بارکۆد -->
            <div class="bg-gray-800 p-6 rounded-lg shadow-lg mb-8 border border-yellow-700">
                <h2 class="text-2xl font-semibold text-yellow-400 mb-4">دروستکردنی بارکۆد (QR Code) بۆ مێزەکان</h2>
                <div class="flex flex-col md:flex-row gap-4">
                    <input type="text" id="tableIdInput" class="flex-1 p-3 rounded-lg bg-gray-900 border border-gray-700 text-white focus:outline-none focus:ring-2 focus:ring-yellow-500" placeholder="نا یان ژمارەی مێز بنووسە (بۆ نموونە: مێزی ٥)">
                    <button id="generateQrButton" class="bg-yellow-400 text-gray-900 font-bold p-3 rounded-lg hover:bg-yellow-300 transition-colors">
                        دروستکردن
                    </button>
                </div>
                <div class="mt-6 p-4 bg-white rounded-lg flex justify-center items-center" id="qrcodeContainer" style="display: none;">
                    <div id="qrcode" class="border-4 border-gray-800 p-2"></div>
                </div>
                <p id="qrText" class="text-yellow-200 text-center mt-2 font-semibold"></p>
            </div>

            <!-- بەشی داواکارییە نوێیەکان -->
            <div class="bg-gray-800 p-6 rounded-lg shadow-lg border border-blue-400">
                <h2 class="text-2xl font-semibold text-blue-300 mb-4">داواکارییە نوێیەکان</h2>
                <div id="ordersContainer" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- نموونەی داواکاری -->
                    <p class="text-gray-400 text-center col-span-full">هێشتا هیچ داواکارییەکی نوێ نییە...</p>
                    
                </div>
            </div>
        </div>
    </div> <!-- کۆتایی adminPage -->

    <!-- 
    ======================================
    پسوڵەی چاپکردن (شاردراوە)
    ======================================
    -->
    <div id="receiptToPrint" class="hidden">
        <h3>پسوڵەی داواکاری</h3>
        <p><strong>کافێی پاشافروت</strong></p>
        <p id="receiptTable"></p>
        <p id="receiptDate"></p>
        <hr>
        <table>
            <thead>
                <tr>
                    <th style="text-align: right;">خواردن</th>
                    <th style="text-align: center;">ژمارە</th>
                    <th style="text-align: left;">نرخ</th>
                </tr>
            </thead>
            <tbody id="receiptItems">
                <!--
                <tr>
                    <td>قاوە</td>
                    <td style="text-align: center;">2</td>
                    <td style="text-align: left;">3,000</td>
                </tr>
                -->
            </tbody>
        </table>
        <hr>
        <p style="font-weight: bold; text-align: left;" id="receiptTotal"></p>
        <hr>
        <p style="text-align: center; font-size: 9px; margin-top: 10px;">سوپاس بۆ داواکارییەکەت!</p>
    </div>


    <!-- 
    ======================================
    سکریپتەکان
    ======================================
    -->

    <!-- Firebase SDK -->
    <script type="module">
        // Importa a função initializeApp
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, addDoc, collection, query, where, onSnapshot, serverTimestamp, updateDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- 1. دەستپێکردنی Firebase ---
        console.log("دەستپێکردنی Firebase...");
        
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let db, auth, app, userId;
        let ordersCollection; // کۆڵەکشنی داواکارییەکان
        let unsubscribeOrders = null; // بۆ ڕاگرتنی گوێگرتن لە داواکارییەکان

        try {
            app = initializeApp(firebaseConfig);
            auth = getAuth(app);
            db = getFirestore(app);
            setLogLevel('Debug'); // بۆ نیشاندانی لۆگەکان لە کۆنسۆڵ
            console.log("Firebase بە سەرکەوتوویی دەستپێکرا");
        } catch (e) {
            console.error("کێشە لە دەستپێکردنی Firebase:", e);
            alert("کێشەیەک لە پێکەوەبەستنی سێرڤەر ڕوویدا. تکایە لاپەڕەکە نوێ بکەرەوە.");
            return;
        }

        // --- 2. سیستەمی Authentication ---
        onAuthStateChanged(auth, async (user) => {
            if (user) {
                userId = user.uid;
                console.log("بەکارهێنەر داخڵ بوو:", userId);
            } else {
                console.log("بەکارهێنەر دەرچوو، هەوڵی چوونەژوورەوەی Anonymous دەدرێت...");
                try {
                    if (initialAuthToken) {
                        await signInWithCustomToken(auth, initialAuthToken);
                        console.log("چوونەژوورەوە بە Custom Token سەرکەوتوو بوو.");
                    } else {
                        await signInAnonymously(auth);
                        console.log("چوونەژوورەوەی Anonymous سەرکەوتوو بوو.");
                    }
                } catch (error) {
                    console.error("کێشە لە چوونەژوورەوە:", error);
                }
            }
            
            // دڵنیابوونەوە لە پێناسەکردنی کۆڵەکشن دوای بوونی appId
            if (appId !== 'default-app-id') {
                ordersCollection = collection(db, 'artifacts', appId, 'public', 'data', 'orders');
                console.log("ڕێڕەوی کۆڵەکشنی داواکارییەکان:", 'artifacts', appId, 'public', 'data', 'orders');
            } else {
                console.warn("appId دیاری نەکراوە، لەوانەیە کۆڵەکشنەکان بە باشی کار نەکەن.");
                // وەک چارەسەرێکی کاتی
                ordersCollection = collection(db, 'public_orders');
            }
        });

        // --- 3. لۆژیکی بنەڕەتی پەڕەکان (کۆدی خۆت + گۆڕانکاری) ---
        document.addEventListener('DOMContentLoaded', function() {
            // --- بەشی کۆدی مینووەکەی خۆت ---
            const categoryBtns = document.querySelectorAll('.category-btn');
            const menuSections = document.querySelectorAll('.menu-section');
            const coldMenuItems = document.querySelectorAll('.menu-section[data-category="cold"] .menu-item');
            const foodCategories = document.querySelectorAll('.food-category');
            
            const mainContainer = document.getElementById('mainContainer');
            const body = document.body;
            const headerIcon = document.getElementById('header-icon');
            const footerIcon = document.getElementById('footer-icon');
            const cartButton = document.getElementById('cartButton'); // زیادکراو
            
            // سیستەمی بەروار
            const expirationDate = new Date('2025-12-2'); 
            const currentDate = new Date();
            const expiredMessage = document.getElementById('expiredMessage');
            
            if (currentDate > expirationDate) {
                expiredMessage.style.display = 'flex'; // گۆڕا بۆ flex
                // شاردنەوەی هەموو پەڕەکان
                document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
            } else {
                expiredMessage.style.display = 'none';
            }

            // نمایشی بەشی 'هەموو'
            showSection('all');
            document.querySelector('.category-btn[data-category="all"]').classList.add('active');
            
            hideAllFoodCategories();
            
            categoryBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    const category = this.getAttribute('data-category');
                    categoryBtns.forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    showSection(category);
                    
                    if (category !== 'cold') {
                        hideAllFoodCategories();
                    }
                    
                    if (category === 'cold') {
                        mainContainer.classList.add('cold-theme');
                        body.classList.add('cold-theme');
                        cartButton.classList.add('cold-theme'); // زیادکراو
                        headerIcon.textContent = '❄️';
                        footerIcon.textContent = '❄️ ❄️ ❄️';
                    } else {
                        mainContainer.classList.remove('cold-theme');
                        body.classList.remove('cold-theme');
                        cartButton.classList.remove('cold-theme'); // زیادکراو
                        headerIcon.textContent = '☕';
                        footerIcon.textContent = '☕ ☕ ☕';
                    }
                    
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                });
            });
            
            coldMenuItems.forEach(item => {
                item.addEventListener('click', function() {
                    const category = this.getAttribute('data-category');
                    hideAllFoodCategories();
                    const selectedCategory = document.getElementById(`${category}-category`);
                    if (selectedCategory) {
                        selectedCategory.classList.add('active');
                        selectedCategory.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    }
                });
            });
            
            function showSection(category) {
                menuSections.forEach(section => section.classList.remove('active'));
                if (category === 'all') {
                    menuSections.forEach(section => section.classList.add('active'));
                } else {
                    const sectionToShow = document.querySelector(`.menu-section[data-category="${category}"]`);
                    if (sectionToShow) sectionToShow.classList.add('active');
                }
            }
            
            function hideAllFoodCategories() {
                foodCategories.forEach(foodCat => foodCat.classList.remove('active'));
            }
            // --- کۆتایی کۆدی مینووەکەی خۆت ---


            // --- 4. لۆژیکی گواستنەوەی پەڕەکان (Page Navigation) ---
            const loginPage = document.getElementById('loginPage');
            const menuPage = document.getElementById('menuPage');
            const adminPage = document.getElementById('adminPage');
            
            const loginButton = document.getElementById('loginButton');
            const adminPassword = document.getElementById('adminPassword');
            const goToMenuButton = document.getElementById('goToMenuButton');
            const goToAdminLogin = document.getElementById('goToAdminLogin');
            const logoutButton = document.getElementById('logoutButton');

            function showPage(pageId) {
                [loginPage, menuPage, adminPage].forEach(page => {
                    page.classList.remove('active');
                });
                document.getElementById(pageId).classList.add('active');
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }

            // لۆگینی ئەدمین
            loginButton.addEventListener('click', () => {
                // وشەی نهێنی کاتی، تکایە بیگۆڕە
                if (adminPassword.value === 'admin123') {
                    console.log("چوونەژوورەوەی ئەدمین سەرکەوتوو بوو");
                    showPage('adminPage');
                    listenForOrders(); // دەستپێکردنی گوێگرتن بۆ داواکارییەکان
                } else {
                    alert("وشەی نهێنی هەڵەیە!");
                    console.warn("هەوڵی چوونەژوورەوەی هەڵە درا");
                }
                adminPassword.value = '';
            });

            // چوون بۆ مینو
            goToMenuButton.addEventListener('click', () => {
                showPage('menuPage');
                // زیادکردنی دوگمەکانی "زیادکردن بۆ سەبەتە"
                addOrderButtonsToItems();
            });

            // گەڕانەوە بۆ لۆگینی ئەدمین
            goToAdminLogin.addEventListener('click', () => showPage('loginPage'));

            // دەرچوون
            logoutButton.addEventListener('click', () => {
                if (unsubscribeOrders) {
                    unsubscribeOrders(); // ڕاگرتنی گوێگرتن
                    unsubscribeOrders = null;
                    console.log("گوێگرتن لە داواکارییەکان ڕاگیرا.");
                }
                showPage('loginPage');
            });
            
            // --- 5. لۆژیکی سەبەتە (Cart) ---
            let cart = []; // { name, price, quantity }
            const cartButtonUI = document.getElementById('cartButton');
            const cartCountUI = document.getElementById('cartCount');
            const cartModal = document.getElementById('cartModal');
            const closeCartButton = document.getElementById('closeCartButton');
            const cartItemsContainer = document.getElementById('cartItemsContainer');
            const cartTotalUI = document.getElementById('cartTotal');
            const submitOrderButton = document.getElementById('submitOrderButton');

            // زیادکردنی دوگمەی "زیادکردن" بۆ هەموو ئایتمەکان
            function addOrderButtonsToItems() {
                const menuItems = document.querySelectorAll('.menu-item:not(.cold-category-card)');
                menuItems.forEach(item => {
                    // دڵنیابوونەوە کە دوگمە زیاد نەکراوە پێشتر
                    if (item.querySelector('.add-to-cart-btn')) return;

                    const itemName = item.querySelector('.item-name')?.innerText;
                    const itemPriceText = item.querySelector('.item-price')?.innerText;
                    
                    if (itemName && itemPriceText) {
                        const addButton = document.createElement('button');
                        addButton.innerText = '+';
                        addButton.className = 'add-to-cart-btn theme-nav-btn !px-3 !py-1 !rounded-full text-lg font-bold ml-2';
                        addButton.title = `زیادکردنی ${itemName} بۆ سەبەتە`;

                        // زیادکردنی دوگمە لەناو item-info
                        const itemInfo = item.querySelector('.item-info');
                        if (itemInfo) {
                            itemInfo.classList.add('flex-row', 'items-center');
                            itemInfo.appendChild(addButton);
                        }

                        addButton.addEventListener('click', (e) => {
                            e.stopPropagation(); // ڕێگرتن لە کاریگەری کلیکی باوک
                            const price = parseInt(itemPriceText.replace(/[^0-9]/g, ''));
                            addToCart(itemName, price);
                        });
                    }
                });
            }

            function addToCart(name, price) {
                const existingItem = cart.find(item => item.name === name);
                if (existingItem) {
                    existingItem.quantity++;
                } else {
                    cart.push({ name, price, quantity: 1 });
                }
                console.log("سەبەتە نوێکرایەوە:", cart);
                updateCartUI();
            }

            function updateCartUI() {
                if (cart.length === 0) {
                    cartItemsContainer.innerHTML = '<p class="text-gray-400 text-center py-4">سەبەتەکەت بەتاڵە.</p>';
                    cartCountUI.classList.add('hidden');
                    submitOrderButton.disabled = true;
                } else {
                    cartItemsContainer.innerHTML = '';
                    let total = 0;
                    cart.forEach((item, index) => {
                        const itemElement = document.createElement('div');
                        itemElement.className = 'flex justify-between items-center py-3';
                        itemElement.innerHTML = `
                            <div>
                                <p class="theme-item-name text-yellow-400 font-semibold">${item.name}</p>
                                <p class="theme-item-price text-yellow-200 text-sm">${item.price.toLocaleString()} د.ع</p>
                            </div>
                            <div class="flex items-center gap-2">
                                <button class="cart-qty-btn bg-gray-700 rounded-full w-6 h-6" data-index="${index}" data-action="decrease">-</button>
                                <span class="font-bold">${item.quantity}</span>
                                <button class="cart-qty-btn bg-gray-700 rounded-full w-6 h-6" data-index="${index}" data-action="increase">+</button>
                                <button class="cart-remove-btn text-red-400 hover:text-red-300 ml-2" data-index="${index}">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" /></svg>
                                </button>
                            </div>
                        `;
                        cartItemsContainer.appendChild(itemElement);
                        total += item.price * item.quantity;
                    });
                    
                    cartTotalUI.innerText = `${total.toLocaleString()} د.ع`;
                    cartCountUI.innerText = cart.reduce((sum, item) => sum + item.quantity, 0);
                    cartCountUI.classList.remove('hidden');
                    submitOrderButton.disabled = false;
                }
            }
            
            // کارکردنی دوگمەکانی ناو سەبەتە ( زیادکردن، کەمکردن، سڕینەوە)
            cartItemsContainer.addEventListener('click', (e) => {
                const target = e.target.closest('button');
                if (!target) return;

                const index = parseInt(target.dataset.index);
                
                if (target.classList.contains('cart-qty-btn')) {
                    const action = target.dataset.action;
                    if (action === 'increase') {
                        cart[index].quantity++;
                    } else if (action === 'decrease') {
                        cart[index].quantity--;
                        if (cart[index].quantity === 0) {
                            cart.splice(index, 1); // سڕینەوەی ئایتم
                        }
                    }
                } else if (target.classList.contains('cart-remove-btn')) {
                    cart.splice(index, 1); // سڕینەوەی ئایتم
                }
                
                updateCartUI();
            });

            // کردنەوە و داخستنی مۆداڵی سەبەتە
            cartButtonUI.addEventListener('click', () => {
                cartModal.classList.remove('hidden');
                setTimeout(() => {
                    cartModal.style.opacity = 1;
                    cartModal.style.pointerEvents = 'auto';
                    cartModal.querySelector('.theme-container').style.transform = 'scale(1)';
                }, 10);
            });
            
            closeCartButton.addEventListener('click', () => {
                cartModal.style.opacity = 0;
                cartModal.style.pointerEvents = 'none';
                cartModal.querySelector('.theme-container').style.transform = 'scale(0.95)';
                setTimeout(() => cartModal.classList.add('hidden'), 300);
            });

            // ناردنی داواکاری
            submitOrderButton.addEventListener('click', async () => {
                if (!ordersCollection) {
                    alert("کێشە لە ناردنی داواکاری. بنکەی داتا ئامادە نییە.");
                    console.error("کۆڵەکشنی داواکارییەکان پێناسە نەکراوە.");
                    return;
                }

                const tableNumber = prompt("تکایە ژمارە یان ناوی مێزەکەت بنووسە:");
                if (!tableNumber) {
                    alert("تکایە ژمارەی مێز بنووسە بۆ ناردنی داواکاری.");
                    return;
                }

                submitOrderButton.disabled = true;
                submitOrderButton.innerText = "تکایە چاوەڕێ بکە...";

                try {
                    const orderData = {
                        table: tableNumber,
                        items: cart, // لیستی ئایتمەکان
                        total: cart.reduce((sum, item) => sum + (item.price * item.quantity), 0),
                        status: "pending", // دۆخی داواکاری: چاوەڕێکراو
                        createdAt: serverTimestamp() // کاتی دروستکردن
                    };
                    
                    const docRef = await addDoc(ordersCollection, orderData);
                    console.log("داواکاری نێردرا بە سەرکەوتوویی:", docRef.id);
                    alert(`داواکارییەکەت بۆ مێزی ${tableNumber} بە سەرکەوتوویی نێردرا.`);
                    
                    // بەتاڵکردنەوەی سەبەتە
                    cart = [];
                    updateCartUI();
                    closeCartButton.click(); // داخستنی مۆداڵ

                } catch (e) {
                    console.error("کێشە لە ناردنی داواکاری:", e);
                    alert("کێشەیەک ڕوویدا لە کاتی ناردنی داواکارییەکەت. تکایە دووبارە هەوڵبدەرەوە.");
                } finally {
                    submitOrderButton.disabled = false;
                    submitOrderButton.innerText = "ناردنی داواکاری";
                }
            });

            // --- 6. لۆژیکی پەڕەی ئەدمین ---
            const tableIdInput = document.getElementById('tableIdInput');
            const generateQrButton = document.getElementById('generateQrButton');
            const qrcodeContainer = document.getElementById('qrcodeContainer');
            const qrcodeDiv = document.getElementById('qrcode');
            const qrText = document.getElementById('qrText');
            const ordersContainer = document.getElementById('ordersContainer');

            // دروستکردنی QR Code
            generateQrButton.addEventListener('click', () => {
                const text = tableIdInput.value;
                if (!text) {
                    alert("تکایە ناوێک یان ژمارەیەک بۆ مێزەکە بنووسە.");
                    return;
                }
                
                qrcodeDiv.innerHTML = ''; // پاککردنەوەی QR کۆنی
                try {
                    new QRCode(qrcodeDiv, {
                        text: text,
                        width: 200,
                        height: 200,
                        colorDark : "#000000",
                        colorLight : "#ffffff",
                        correctLevel : QRCode.CorrectLevel.H
                    });
                    qrText.innerText = `بارکۆد بۆ: ${text}`;
                    qrcodeContainer.style.display = 'flex';
                    console.log(`بارکۆد دروستکرا بۆ: ${text}`);
                } catch(e) {
                    console.error("کێشە لە دروستکردنی بارکۆد:", e);
                    alert("کێشەیەک ڕوویدا. تکایە دڵنیابە لە نووسینەکەت.");
                }
            });

            // گوێگرتن بۆ داواکارییە نوێیەکان
            function listenForOrders() {
                if (!ordersCollection) {
                    console.error("کۆڵەکشنی داواکارییەکان ئامادە نییە بۆ گوێگرتن.");
                    ordersContainer.innerHTML = '<p class="text-red-400 text-center col-span-full">کێشە لە پەیوەندی بە بنکەی داتاوە هەیە.</p>';
                    return;
                }

                // ستۆپکردنی گوێگری پێشوو ئەگەر هەبێت
                if (unsubscribeOrders) {
                    unsubscribeOrders();
                }

                console.log("دەستپێکردنی گوێگرتن بۆ داواکارییە نوێیەکان...");
                
                // فلتەرکردن تەنها بۆ داواکارییە چاوەڕێکراوەکان
                const q = query(ordersCollection, where("status", "==", "pending"));
                
                unsubscribeOrders = onSnapshot(q, (snapshot) => {
                    console.log(`داواکاری نوێ وەرگیرا: ${snapshot.docs.length} داواکاری`);
                    if (snapshot.empty) {
                        ordersContainer.innerHTML = '<p class="text-gray-400 text-center col-span-full">هێشتا هیچ داواکارییەکی نوێ نییە...</p>';
                        return;
                    }

                    ordersContainer.innerHTML = ''; // پاککردنەوەی داواکارییە کۆنەکان
                    
                    // لیستی داواکارییەکان ڕێکبخە بەپێی کات (نوێترین لە پێشەوە)
                    // Firestore orderBy پێویستی بە ئیندێکس هەیە، بۆیە لێرە بە جاڤاسکریپت ڕێکی دەخەین
                    const docs = snapshot.docs.sort((a, b) => {
                        const timeA = a.data().createdAt?.seconds || 0;
                        const timeB = b.data().createdAt?.seconds || 0;
                        return timeB - timeA; // نوێترین لە پێشەوە
                    });

                    docs.forEach(doc => {
                        const order = doc.data();
                        const orderId = doc.id;
                        const orderCard = document.createElement('div');
                        orderCard.className = 'order-card bg-gray-900 p-5 rounded-lg shadow-lg border border-gray-700 animate-pulse-fast'; // animate-pulse-fast بۆ سەرنجڕاکێشان
                        orderCard.dataset.id = orderId;
                        
                        // کاتی داواکاری
                        const timestamp = order.createdAt?.toDate ? order.createdAt.toDate().toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit' }) : 'N/A';
                        
                        // لیستی ئایتمەکان
                        let itemsHtml = order.items.map(item => `
                            <li class="flex justify-between items-center">
                                <span class="font-medium">${item.name}</span>
                                <span class="text-gray-400">x ${item.quantity}</span>
                            </li>
                        `).join('');

                        orderCard.innerHTML = `
                            <div class="flex justify-between items-center mb-3">
                                <h3 class="text-2xl font-bold text-yellow-300">مێزی: ${order.table}</h3>
                                <span class="text-sm font-semibold text-gray-400">${timestamp}</span>
                            </div>
                            <ul class="divide-y divide-gray-800 mb-4">
                                ${itemsHtml}
                            </ul>
                            <div class="border-t border-gray-800 pt-3 flex justify-between items-center mb-4">
                                <span class="text-lg font-bold text-gray-300">کۆی گشتی:</span>
                                <span class="text-lg font-bold text-yellow-300">${order.total.toLocaleString()} د.ع</span>
                            </div>
                            <div class="flex flex-col gap-2">
                                <button class="print-receipt-btn w-full bg-blue-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-600 transition-colors">
                                    چاپکردنی پسوڵە
                                </button>
                                <button class="complete-order-btn w-full bg-green-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-green-700 transition-colors">
                                    تەواوکردنی داواکاری
                                </button>
                            </div>
                        `;
                        
                        ordersContainer.appendChild(orderCard);
                        
                        // لابردنی ئەنیمەیشن دوای ماوەیەک
                        setTimeout(() => orderCard.classList.remove('animate-pulse-fast'), 2000);
                    });

                }, (error) => {
                    console.error("کێشە لە وەرگرتنی داواکارییەکان:", error);
                    ordersContainer.innerHTML = '<p class="text-red-400 text-center col-span-full">کێشە لە پەیوەندی ڕوویدا. تکایە لاپەڕەکە نوێ بکەرەوە.</p>';
                });
            }

            // کارکردنی دوگمەکانی سەر کارتی داواکاری (چاپکردن و تەواوکردن)
            ordersContainer.addEventListener('click', async (e) => {
                const target = e.target;
                if (!target) return;

                const card = target.closest('.order-card');
                if (!card) return;
                
                const orderId = card.dataset.id;
                
                if (target.classList.contains('complete-order-btn')) {
                    // تەواوکردنی داواکاری (گۆڕینی دۆخ بۆ 'completed')
                    try {
                        target.disabled = true;
                        target.innerText = "تەواو کرا...";
                        const orderRef = doc(db, 'artifacts', appId, 'public', 'data', 'orders', orderId);
                        await updateDoc(orderRef, { status: "completed" });
                        console.log(`داواکاری ${orderId} تەواو کرا.`);
                        // کاردەکە خۆی نامێنێت لە گوێگری داهاتوودا
                    } catch (err) {
                        console.error("کێشە لە تەواوکردنی داواکاری:", err);
                        alert("کێشەیەک ڕوویدا.");
                        target.disabled = false;
                        target.innerText = "تەواوکردنی داواکاری";
                    }
                }
                
                if (target.classList.contains('print-receipt-btn')) {
                    // چاپکردنی پسوڵە
                    console.log(`چاپکردنی پسوڵە بۆ: ${orderId}`);
                    // دۆزینەوەی داتای داواکارییەکە (پێویستە داتاکە هەڵبگرین یان دووبارە بیخوێنینەوە)
                    // ڕێگای ئاسان: داتاکە لە کاردەکەوە وەربگرین
                    const table = card.querySelector('h3').innerText.replace('مێزی: ', '');
                    const total = card.querySelector('.text-yellow-300').innerText;
                    const itemsHtml = Array.from(card.querySelectorAll('ul li')).map(li => {
                        const name = li.querySelector('.font-medium').innerText;
                        const qty = li.querySelector('.text-gray-400').innerText.replace('x ', '');
                        return { name, qty };
                    }).join(''); // پێویستە ئەمە باشتر بکەین

                    // ناردنی داتا بۆ فەنکشنی چاپکردن
                    printReceiptForOrder(card);
                }
            });
            
            // --- 7. لۆژیکی چاپکردنی پسوڵە ---
            const receiptToPrint = document.getElementById('receiptToPrint');
            const receiptTable = document.getElementById('receiptTable');
            const receiptDate = document.getElementById('receiptDate');
            const receiptItems = document.getElementById('receiptItems');
            const receiptTotal = document.getElementById('receiptTotal');

            function printReceiptForOrder(orderCard) {
                // وەرگرتنی داتا لە کارتی HTML
                const table = orderCard.querySelector('h3').innerText;
                const totalText = orderCard.querySelector('.text-lg.font-bold.text-yellow-300').innerText;
                
                // پاککردنەوەی پسوڵەی کۆن
                receiptItems.innerHTML = '';
                
                // پڕکردنەوەی داتای پسوڵە
                receiptTable.innerText = table;
                receiptDate.innerText = `کات: ${new Date().toLocaleString('en-US', { hour: '2-digit', minute: '2-digit', day: '2-digit', month: '2-digit' })}`;
                receiptTotal.innerText = `کۆی گشتی: ${totalText}`;
                
                // زیادکردنی ئایتمەکان
                const items = orderCard.querySelectorAll('ul li');
                items.forEach(li => {
                    const name = li.querySelector('.font-medium').innerText;
                    const qty = li.querySelector('.text-gray-400').innerText.replace('x ', '');
                    
                    // لێرە پێویستمان بە نرخە، کە لە کاردەکەدا نییە.
                    // دەبێت نرخی تاکەکەسی لە داتابەیسەوە بهێنین یان لێرە حساباتی بۆ بکەین
                    // بۆ سادەیی، تەنها ناو و ژمارە دادەنێین
                    
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${name}</td>
                        <td style="text-align: center;">${qty}</td>
                        <td style="text-align: left;">...</td> 
                    `;
                    receiptItems.appendChild(row);
                });

                // چاپکردن
                window.print();
            }

            // لەکۆتاییدا، پاش چاکسازی، پەیجی لۆگین نیشان بدە
            // showPage('loginPage'); // یان 'menuPage' ئەگەر دەتەوێت ڕاستەوخۆ مینو نیشان بدات
            // گۆڕیم بۆ ئەوەی سەرەتا لۆگین نیشان بدات
            showPage('loginPage');

        }); // کۆتایی DOMContentLoaded

    </script>
</body>
</html>
