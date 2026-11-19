```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أبو عبد الرحمن للعدد والحدادة | بطاقة عمل رقمية</title>
    <!-- تحميل Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- تحميل خط Cairo و Tajawal للغة العربية القوية والواضحة -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap" rel="stylesheet">
    <!-- مكتبة توليد كود QR -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    
    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #111827; /* رمادي داكن جداً */
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(249, 115, 22, 0.08), transparent 25%),
                radial-gradient(circle at 85% 30%, rgba(249, 115, 22, 0.08), transparent 25%),
                repeating-linear-gradient(45deg, rgba(255,255,255,0.02) 0px, rgba(255,255,255,0.02) 2px, transparent 2px, transparent 8px);
        }

        /* تأثير المعدن المصقول */
        .metallic-card {
            background: linear-gradient(145deg, #1f2937 0%, #111827 100%);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.7), inset 0 1px 0 0 rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(249, 115, 22, 0.3);
        }


        /* حركة دوران بطيئة للتروس في الخلفية */
        @keyframes spin-slow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        @keyframes spin-reverse-slow {
            from { transform: rotate(360deg); }
            to { transform: rotate(0deg); }
        }
        .animate-gear-1 {
            animation: spin-slow 25s linear infinite;
            transform-origin: center;
        }
        .animate-gear-2 {
            animation: spin-reverse-slow 20s linear infinite;
            transform-origin: center;
        }

        /* تنسيقات الطباعة */
        @media print {
            body {
                background: white !important;
                color: black !important;
            }
            .no-print {
                display: none !important;
            }
            .metallic-card {
                box-shadow: none !important;
                border: 2px solid #000 !important;
                background: #fff !important;
                color: #000 !important;
            }
            .print-text-dark {
                color: #000 !important;
            }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-center p-4 text-gray-100 selection:bg-orange-500 selection:text-white">

    <!-- رسالة التنبيه (Toast Notification) بديلة عن alert -->
    <div id="toast" class="fixed top-5 left-1/2 transform -translate-x-1/2 z-50 transition-all duration-300 opacity-0 pointer-events-none translate-y-[-20px]">
        <div class="bg-orange-600 text-white px-6 py-3 rounded-xl shadow-2xl flex items-center gap-3 border border-orange-400 font-bold text-sm md:text-base">
            <svg class="w-6 h-6 text-white shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
            </svg>
            <span id="toast-message">تم نسخ الرقم بنجاح!</span>
        </div>
    </div>

    <!-- الحاوية الرئيسية للبطاقة -->
    <main class="w-full max-w-md metallic-card rounded-3xl overflow-hidden relative">
        
        <!-- قسم الغلاف والشعار (Cover & Logo) -->
        <div class="relative h-56 bg-gradient-to-b from-gray-800 via-gray-900 to-[#161e2e] flex flex-col items-center justify-center overflow-hidden border-b-2 border-orange-500/40">
            
            <!-- خلفية SVG رسومية احترافية (تروس، مفاتيح ربط، ومعدات حديدية) -->
            <svg class="absolute inset-0 w-full h-full opacity-20 pointer-events-none" viewBox="0 0 400 220" fill="none" xmlns="http://www.w3.org/2000/svg">
                <!-- ترس كبير يسار -->
                <g class="animate-gear-1" style="transform-box: fill-box;">
                    <path d="M70 30L75 15H85L90 30L103 35L116 26L124 34L115 47L120 60L135 65V75L120 80L115 93L124 106L116 114L103 105L90 110L85 125H75L70 110L57 105L44 114L36 106L45 93L40 80L25 75V65L40 60L45 47L36 34L44 26L57 35L70 30Z" stroke="#F97316" stroke-width="3" fill="#374151"/>
                    <circle cx="80" cy="70" r="20" stroke="#F97316" stroke-width="3" fill="#1F2937"/>
                </g>
                
                <!-- ترس متوسط يمين -->
                <g class="animate-gear-2" style="transform-box: fill-box;">
                    <path d="M320 110L324 98H332L336 110L346 114L356 107L362 113L355 123L359 133L371 137V145L359 149L355 159L362 169L356 175L346 168L336 172L332 184H324L320 172L310 168L300 175L294 169L301 159L297 149L285 145V137L297 133L301 123L294 113L300 107L310 114L320 110Z" stroke="#9CA3AF" stroke-width="2.5" fill="#374151"/>
                    <circle cx="328" cy="141" r="14" stroke="#9CA3AF" stroke-width="2.5" fill="#1F2937"/>
                </g>

                <!-- مفتاح ربط (Wrench) متقاطع في الخلفية -->
                <path d="M140 180 L250 70 C258 75 270 72 277 65 C285 57 287 44 281 35 L268 48 L258 45 L255 35 L268 22 C259 16 246 18 238 26 C231 33 228 45 233 53 L123 163 C115 158 103 161 96 168 C88 176 86 189 92 198 L105 185 L115 188 L118 198 L105 211 C114 217 127 215 135 207 C142 200 145 188 140 180 Z" stroke="#F97316" stroke-width="2" fill="rgba(249, 115, 22, 0.15)"/>
                
                <!-- خطوط هندسية معدنية -->
                <line x1="0" y1="20" x2="400" y2="20" stroke="#4B5563" stroke-width="1" stroke-dasharray="6 6"/>
                <line x1="0" y1="200" x2="400" y2="200" stroke="#4B5563" stroke-width="1" stroke-dasharray="6 6"/>
            </svg>

            <!-- شريط علوي زخرفي -->
            <div class="absolute top-0 inset-x-0 h-1.5 bg-gradient-to-r from-gray-700 via-orange-500 to-gray-700"></div>

            <!-- الشعار الرئيسي (Logo Badge) -->
            <div class="relative z-10 flex flex-col items-center text-center px-4">
                <!-- أيقونة الشعار (درع معدني مع مطرقة ومفتاح) -->
                <div class="w-20 h-20 rounded-2xl bg-gradient-to-br from-orange-500 to-orange-700 p-0.5 shadow-lg shadow-orange-500/30 mb-3 transform hover:scale-105 transition-transform">
                    <div class="w-full h-full bg-gray-900 rounded-[14px] flex items-center justify-center relative overflow-hidden">
                        <svg class="w-12 h-12 text-orange-500" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <!-- ترس داخلي -->
                            <circle cx="32" cy="32" r="14" stroke="currentColor" stroke-width="3" stroke-dasharray="4 3"/>
                            <!-- مفتاح ربط -->
                            <path d="M44 16C40.5 16 37.5 18 36.2 21L18.5 38.7C15.5 40 13.5 43 13.5 46.5C13.5 51.2 17.3 55 22 55C25.5 55 28.5 53 29.8 50L47.5 32.3C50.5 31 52.5 28 52.5 24.5C52.5 22.8 52 21.2 51.1 19.9L45.5 25.5L41 24L39.5 19.5L45.1 13.9C44.7 13.9 44.4 16 44 16Z" fill="currentColor"/>
                            <!-- مطرقة متقاطعة -->
                            <path d="M16 20L24 12L30 18L26 22L48 44L44 48L22 26L18 30L12 24L16 20Z" fill="#E5E7EB"/>
                        </svg>
                    </div>
                </div>

                <!-- اسم العلامة التجارية -->
                <h1 class="text-3xl md:text-4xl font-black tracking-tight text-white drop-shadow-md print-text-dark">
                    أبو <span class="text-orange-500">عبد الرحمن</span>
                </h1>
                <div class="mt-1 inline-flex items-center gap-2 px-3 py-0.5 rounded-full bg-gray-800/90 border border-gray-700 text-xs md:text-sm font-semibold text-gray-300">
                    <span class="w-2 h-2 rounded-full bg-orange-500 animate-pulse"></span>
                    للعدد اليدوية والحدادة والمعدات الصناعية
                </div>
            </div>
        </div>

        <!-- محتوى البطاقة (رقم الهاتف والأزرار) -->
        <div class="p-6 space-y-6">
            
            <!-- بطاقة عرض رقم الهاتف مع زر النسخ -->
            <div class="bg-gray-800/80 border border-gray-700 rounded-2xl p-4 flex items-center justify-between shadow-inner">
                <div>
                    <span class="text-xs text-gray-400 block mb-0.5">رقم التواصل والمحفظة الإلكترونية</span>
                    <a href="tel:01282102022" id="phone-number-display" dir="ltr" class="text-2xl md:text-3xl font-black text-white tracking-wider hover:text-orange-400 transition-colors print-text-dark">
                        01282102022
                    </a>
                </div>
                
                <button onclick="copyPhoneNumber()" class="no-print bg-gray-700 hover:bg-orange-600 text-white p-3.5 rounded-xl transition-all duration-200 active:scale-95 flex flex-col items-center justify-center gap-1 border border-gray-600 hover:border-orange-400 shadow-md group" title="نسخ الرقم">
                    <svg id="copy-icon" class="w-6 h-6 text-orange-400 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path>
                    </svg>
                    <span class="text-[11px] font-bold">نسخ</span>
                </button>
            </div>

            <!-- الأزرار التفاعلية الرئيسية -->
            <div class="space-y-3 no-print">
                
                <!-- زر فتح أورنج كاش المباشر (كود #115*) -->
                <a href="tel:*115%23" onclick="handleOrangeCashClick()" class="w-full bg-gradient-to-r from-orange-600 to-orange-500 hover:from-orange-500 hover:to-orange-400 text-white font-bold py-4 px-5 rounded-2xl shadow-lg shadow-orange-600/30 flex items-center justify-between transition-all duration-200 transform hover:-translate-y-0.5 active:translate-y-0 border border-orange-400/50">
                    <div class="flex items-center gap-3.5">
                        <div class="w-11 h-11 rounded-xl bg-black/20 flex items-center justify-center shrink-0">
                            <!-- أيقونة محفظة / نقود -->
                            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z"></path>
                            </svg>
                        </div>
                        <div class="text-right">
                            <div class="text-base md:text-lg font-black leading-tight">فتح أورنج كاش (Orange Cash)</div>
                            <div class="text-xs text-orange-100 font-normal mt-0.5">طلب كود الخدمة المباشر <span dir="ltr" class="font-bold bg-black/25 px-1.5 py-0.5 rounded">#115*</span></div>
                        </div>
                    </div>
                    <svg class="w-6 h-6 text-white/80 shrink-0 rtl:rotate-180" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M9 5l7 7-7 7"></path>
                    </svg>
                </a>

                <!-- صف أزرار: اتصال مباشر + تطبيق My Orange -->
                <div class="grid grid-cols-2 gap-3">
                    <!-- اتصال مباشر -->
                    <a href="tel:01282102022" class="bg-gray-800 hover:bg-gray-750 border border-gray-700 hover:border-green-500/50 text-white font-bold py-3.5 px-4 rounded-2xl flex items-center justify-center gap-2.5 transition-all active:scale-95 shadow-md">
                        <div class="w-9 h-9 rounded-xl bg-green-500/20 text-green-400 flex items-center justify-center shrink-0">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
                            </svg>
                        </div>
                        <span class="text-sm md:text-base">اتصال مباشر</span>
                    </a>

                    <!-- فتح تطبيق My Orange -->
                    <button onclick="openMyOrangeApp()" class="bg-gray-800 hover:bg-gray-750 border border-gray-700 hover:border-orange-500/50 text-white font-bold py-3.5 px-4 rounded-2xl flex items-center justify-center gap-2.5 transition-all active:scale-95 shadow-md">
                        <div class="w-9 h-9 rounded-xl bg-orange-500/20 text-orange-400 flex items-center justify-center shrink-0 font-black text-xs">
                            My
                        </div>
                        <span class="text-sm md:text-base">تطبيق My Orange</span>
                    </button>
                </div>

                <!-- زر واتساب سريع للتواصل بخصوص العدد والحدادة -->
                <a href="https://wa.me/201282102022?text=%D8%A7%D9%84%D8%B3%D9%84%D8%A7%D9%85%20%D8%B9%D9%84%D9%8A%D9%83%D9%85%20%D8%A3%D8%A8%D9%88%20%D8%B9%D8%A8%D8%AF%20%D8%A7%D9%84%D8%B1%D8%AD%D9%85%D9%86%D8%8C%20%D8%A3%D8%B1%D9%8A%D8%AF%20%D8%A7%D9%84%D8%A7%D8%B3%D8%AA%D9%81%D8%B3%D8%A7%D8%B1%20%D8%A8%D8%AE%D8%B5%D9%88%D8%B5..." target="_blank" rel="noopener noreferrer" class="w-full bg-gray-800/90 hover:bg-emerald-950/60 border border-gray-700 hover:border-emerald-500/50 text-gray-200 hover:text-emerald-300 font-semibold py-3 px-4 rounded-2xl flex items-center justify-center gap-2 transition-all text-sm">
                    <svg class="w-5 h-5 text-emerald-500" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.069-.252-.08-.575-.187-.988-.365-1.739-.751-2.874-2.502-2.961-2.617-.087-.116-.708-.94-.708-1.793s.448-1.273.607-1.446c.159-.173.346-.217.462-.217l.332.006c.106.005.249-.04.39.298.144.347.491 1.2.534 1.287.043.087.072.188.014.304-.058.116-.087.188-.173.289l-.26.304c-.087.086-.177.18-.076.354.101.174.449.741.964 1.201.662.591 1.221.774 1.394.86s.274.072.376-.043c.101-.116.433-.506.549-.68.116-.173.231-.145.39-.087s1.011.477 1.184.564.289.13.332.202c.045.072.045.419-.1.824z"/>
                    </svg>
                    <span>مراسلة عبر واتساب (WhatsApp)</span>
                </a>
            </div>

            <!-- قسم كود QR والطباعة -->
            <div class="pt-4 border-t border-gray-800 flex flex-col items-center">
                <div class="flex items-center justify-between w-full mb-3 no-print">
                    <span class="text-xs font-bold text-gray-400">رمز الاستجابة السريعة (QR Code)</span>
                    <div class="flex gap-1 bg-gray-800 p-1 rounded-lg border border-gray-700">
                        <button onclick="generateQR('phone')" id="btn-qr-phone" class="text-xs px-2.5 py-1 rounded-md bg-orange-600 text-white font-bold transition">الرقم</button>
                        <button onclick="generateQR('ussd')" id="btn-qr-ussd" class="text-xs px-2.5 py-1 rounded-md text-gray-300 hover:text-white transition">أورنج كاش</button>
                        <button onclick="generateQR('vcard')" id="btn-qr-vcard" class="text-xs px-2.5 py-1 rounded-md text-gray-300 hover:text-white transition">جهة اتصال</button>
                    </div>
                </div>

                <!-- حاوية عرض QR -->
                <div class="bg-white p-3.5 rounded-2xl shadow-lg border-4 border-gray-700 flex flex-col items-center">
                    <div id="qrcode" class="flex items-center justify-center"></div>
                    <span id="qr-label" class="text-gray-900 font-bold text-xs mt-2">امسح الكود للاتصال: 01282102022</span>
                </div>

                <!-- أزرار حفظ ومشاركة وطباعة البطاقة -->
                <div class="grid grid-cols-2 gap-3 w-full mt-5 no-print">
                    <button onclick="downloadVCard()" class="bg-gray-800 hover:bg-gray-700 text-gray-200 font-bold py-2.5 px-4 rounded-xl border border-gray-700 flex items-center justify-center gap-2 text-xs md:text-sm transition">
                        <svg class="w-4 h-4 text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18 9v3m0 0v3m0-3h3m-3 0h-3m-2-5a4 4 0 11-8 0 4 4 0 018 0zM3 20a6 6 0 0112 0v1H3v-1z"></path>
                        </svg>
                        <span>حفظ جهة الاتصال</span>
                    </button>

                    <button onclick="window.print()" class="bg-gray-800 hover:bg-gray-700 text-gray-200 font-bold py-2.5 px-4 rounded-xl border border-gray-700 flex items-center justify-center gap-2 text-xs md:text-sm transition">
                        <svg class="w-4 h-4 text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z"></path>
                        </svg>
                        <span>طباعة البطاقة</span>
                    </button>
                </div>
            </div>

        </div>

        <!-- تذييل البطاقة -->
        <footer class="bg-gray-950/80 py-3 px-6 text-center border-t border-gray-800/80">
            <p class="text-xs text-gray-500">أبو عبد الرحمن للعدد والحدادة • جودة ومتانة تثق بها</p>
        </footer>
    </main>

    <script>
        const PHONE_NUMBER = "01282102022";
        let qrCodeInstance = null;

        // دالة إظهار الإشعارات المنبثقة (Toast)
        function showToast(message) {
            const toast = document.getElementById('toast');
            const toastMsg = document.getElementById('toast-message');
            toastMsg.textContent = message;
            
            toast.classList.remove('opacity-0', 'translate-y-[-20px]', 'pointer-events-none');
            toast.classList.add('opacity-100', 'translate-y-0');

            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-[-20px]', 'pointer-events-none');
                toast.classList.remove('opacity-100', 'translate-y-0');
            }, 3000);
        }

        // دالة نسخ رقم الهاتف باستخدام execCommand لضمان العمل في كافة البيئات
        function copyPhoneNumber() {
            const tempInput = document.createElement("input");
            tempInput.value = PHONE_NUMBER;
            document.body.appendChild(tempInput);
            tempInput.select();
            tempInput.setSelectionRange(0, 99999);
            
            try {
                document.execCommand("copy");
                showToast("تم نسخ الرقم: " + PHONE_NUMBER);
            } catch (err) {
                showToast("تعذر النسخ، يرجى نسخ الرقم يدوياً");
            }
            
            document.body.removeChild(tempInput);
        }

        // تنبيه عند الضغط على زر أورنج كاش
     
