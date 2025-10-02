# Fulfulde-Dictionary-
قاموس اللغة الفولانية _ فولفولدي -عربي -انجليزي 
[index.html](https://github.com/user-attachments/files/22664178/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قاموس اللغة الفولانية - Fulfulde Dictionary</title>
    <style>
        :root {
            --primary-color: #2c5e1a;
            --secondary-color: #f0f8e6;
            --accent-color: #6b8e23;
            --text-color: #333;
            --light-text: #666;
            --background: #f9f9f9;
            --card-bg: #fff;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--background);
            color: var(--text-color);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 1rem;
            text-align: center;
            border-radius: 8px 8px 0 0;
            margin-bottom: 20px;
        }
        
        h1 {
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1rem;
            opacity: 0.9;
        }
        
        .main-content {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        
        .input-section {
            flex: 1;
            min-width: 300px;
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .dictionary-section {
            flex: 2;
            min-width: 300px;
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        input, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: var(--accent-color);
        }
        
        .search-box {
            margin-bottom: 20px;
            display: flex;
        }
        
        .search-box input {
            border-radius: 4px 0 0 4px;
        }
        
        .search-box button {
            border-radius: 0 4px 4px 0;
        }
        
        .alphabet-filter {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin-bottom: 20px;
            justify-content: center;
        }
        
        .alphabet-filter button {
            padding: 5px 10px;
            background-color: var(--secondary-color);
            color: var(--primary-color);
            border: 1px solid var(--primary-color);
        }
        
        .alphabet-filter button:hover, .alphabet-filter button.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        .dictionary-list {
            max-height: 600px;
            overflow-y: auto;
        }
        
        .dictionary-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 15px;
        }
        
        .dictionary-item:last-child {
            border-bottom: none;
        }
        
        .dictionary-item:hover {
            background-color: var(--secondary-color);
        }
        
        .fulfulde-word {
            font-weight: bold;
            color: var(--primary-color);
            font-size: 1.2rem;
        }
        
        .word-meaning {
            color: var(--light-text);
        }
        
        @media (max-width: 768px) {
            .dictionary-item {
                grid-template-columns: 1fr;
            }
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px;
            background-color: var(--primary-color);
            color: white;
            border-radius: 4px;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .notification.show {
            opacity: 1;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>قاموس اللغة الفولانية</h1>
            <div class="subtitle">Fulfulde - Arabic - English Dictionary</div>
        </header>
        
        <div class="main-content">
            <section class="input-section">
                <h2>إضافة كلمة جديدة</h2>
                <form id="word-form">
                    <div class="form-group">
                        <label for="fulfulde">الكلمة الفولانية</label>
                        <input type="text" id="fulfulde" required>
                    </div>
                    <div class="form-group">
                        <label for="arabic">المعنى العربي</label>
                        <input type="text" id="arabic" required>
                    </div>
                    <div class="form-group">
                        <label for="english">المعنى الإنجليزي</label>
                        <input type="text" id="english" required>
                    </div>
                    <button type="submit">إضافة إلى القاموس</button>
                </form>
            </section>
            
            <section class="dictionary-section">
                <h2>القاموس</h2>
                
                <div class="search-box">
                    <input type="text" id="search" placeholder="ابحث في القاموس...">
                    <button id="search-btn">بحث</button>
                </div>
                
                <div class="alphabet-filter" id="alphabet-filter">
                    <!-- سيتم ملء هذا القسم بالأحرف الفولانية عبر JavaScript -->
                </div>
                
                <div class="dictionary-list" id="dictionary-list">
                    <!-- سيتم ملء هذا القسم بالكلمات عبر JavaScript -->
                </div>
            </section>
        </div>
    </div>
    
    <div class="notification" id="notification">تمت الإضافة بنجاح!</div>

    <script>
        // الأبجدية الفولانية الأساسية (يمكن توسيعها حسب الحاجة)
        const fulfuldeAlphabet = [
            'a', 'aa', 'b', 'ɓ', 'c', 'd', 'ɗ', 'e', 'ee', 'f', 'g', 'h', 'i', 
            'ii', 'j', 'k', 'l', 'm', 'n', 'ny', 'ŋ', 'o', 'oo', 'p', 'r', 's', 
            't', 'u', 'uu', 'w', 'y', 'ʼ'
        ];
        
        // عناصر DOM
        const wordForm = document.getElementById('word-form');
        const searchInput = document.getElementById('search');
        const searchBtn = document.getElementById('search-btn');
        const alphabetFilter = document.getElementById('alphabet-filter');
        const dictionaryList = document.getElementById('dictionary-list');
        const notification = document.getElementById('notification');
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', initApp);
        
        function initApp() {
            // إنشاء أزرار تصفية الأحرف
            createAlphabetFilters();
            
            // تحميل الكلمات من localStorage
            loadWords();
            
            // إضافة مستمعي الأحداث
            wordForm.addEventListener('submit', addWord);
            searchBtn.addEventListener('click', searchWords);
            searchInput.addEventListener('keyup', function(e) {
                if (e.key === 'Enter') searchWords();
            });
        }
        
        // إنشاء أزرار تصفية الأحرف
        function createAlphabetFilters() {
            fulfuldeAlphabet.forEach(char => {
                const button = document.createElement('button');
                button.textContent = char;
                button.dataset.char = char;
                button.addEventListener('click', () => filterByLetter(char));
                alphabetFilter.appendChild(button);
            });
            
            // إضافة زر لعرض كل الكلمات
            const allButton = document.createElement('button');
            allButton.textContent = 'الكل';
            allButton.classList.add('active');
            allButton.addEventListener('click', () => {
                document.querySelectorAll('#alphabet-filter button').forEach(btn => {
                    btn.classList.remove('active');
                });
                allButton.classList.add('active');
                loadWords();
            });
            alphabetFilter.appendChild(allButton);
        }
        
        // إضافة كلمة جديدة
        function addWord(e) {
            e.preventDefault();
            
            const fulfuldeWord = document.getElementById('fulfulde').value.trim();
            const arabicMeaning = document.getElementById('arabic').value.trim();
            const englishMeaning = document.getElementById('english').value.trim();
            
            if (!fulfuldeWord || !arabicMeaning || !englishMeaning) {
                showNotification('يرجى ملء جميع الحقول', 'error');
                return;
            }
            
            // الحصول على الكلمات الحالية من localStorage
            const words = JSON.parse(localStorage.getItem('fulfuldeDictionary')) || [];
            
            // التحقق من عدم وجود الكلمة مسبقاً
            if (words.some(word => word.fulfulde.toLowerCase() === fulfuldeWord.toLowerCase())) {
                showNotification('هذه الكلمة موجودة بالفعل في القاموس', 'error');
                return;
            }
            
            // إضافة الكلمة الجديدة
            words.push({
                fulfulde: fulfuldeWord,
                arabic: arabicMeaning,
                english: englishMeaning
            });
            
            // حفظ الكلمات في localStorage
            localStorage.setItem('fulfuldeDictionary', JSON.stringify(words));
            
            // إعادة تحميل القائمة
            loadWords();
            
            // إظهار رسالة النجاح
            showNotification('تمت إضافة الكلمة بنجاح');
            
            // تفريغ النموذج
            wordForm.reset();
        }
        
        // تحميل وعرض الكلمات
        function loadWords() {
            const words = JSON.parse(localStorage.getItem('fulfuldeDictionary')) || [];
            
            // ترتيب الكلمات حسب الأبجدية الفولانية
            words.sort((a, b) => {
                return customFulfuldeSort(a.fulfulde, b.fulfulde);
            });
            
            displayWords(words);
        }
        
        // دالة الترتيب المخصصة للغة الفولانية
        function customFulfuldeSort(a, b) {
            a = a.toLowerCase();
            b = b.toLowerCase();
            
            for (let i = 0; i < Math.min(a.length, b.length); i++) {
                let aChar = a[i];
                let bChar = b[i];
                
                // معالجة الأحرف الخاصة المكونة من حرفين
                if (i < a.length - 1 && fulfuldeAlphabet.includes(a.substr(i, 2))) {
                    aChar = a.substr(i, 2);
                }
                if (i < b.length - 1 && fulfuldeAlphabet.includes(b.substr(i, 2))) {
                    bChar = b.substr(i, 2);
                }
                
                const aIndex = fulfuldeAlphabet.indexOf(aChar);
                const bIndex = fulfuldeAlphabet.indexOf(bChar);
                
                if (aIndex !== -1 && bIndex !== -1) {
                    if (aIndex !== bIndex) {
                        return aIndex - bIndex;
                    }
                } else if (aIndex !== -1) {
                    return -1;
                } else if (bIndex !== -1) {
                    return 1;
                } else {
                    // إذا لم تكن الأحرف في الأبجدية الفولانية، استخدم الترتيب القياسي
                    if (aChar !== bChar) {
                        return aChar.localeCompare(bChar);
                    }
                }
                
                // إذا كان الحرف مكون من حرفين، تخطي الحرف التالي
                if (aChar.length > 1) i++;
                if (bChar.length > 1) i++;
            }
            
            return a.length - b.length;
        }
        
        // عرض الكلمات في القائمة
        function displayWords(words) {
            dictionaryList.innerHTML = '';
            
            if (words.length === 0) {
                dictionaryList.innerHTML = '<p style="text-align: center; padding: 20px;">لا توجد كلمات في القاموس بعد.</p>';
                return;
            }
            
            words.forEach(word => {
                const wordElement = document.createElement('div');
                wordElement.classList.add('dictionary-item');
                wordElement.innerHTML = `
                    <div class="fulfulde-word">${word.fulfulde}</div>
                    <div class="word-meaning">${word.arabic}</div>
                    <div class="word-meaning">${word.english}</div>
                `;
                dictionaryList.appendChild(wordElement);
            });
        }
        
        // تصفية الكلمات بحرف معين
        function filterByLetter(letter) {
            document.querySelectorAll('#alphabet-filter button').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            const words = JSON.parse(localStorage.getItem('fulfuldeDictionary')) || [];
            const filteredWords = words.filter(word => {
                return word.fulfulde.toLowerCase().startsWith(letter);
            });
            
            displayWords(filteredWords);
        }
        
        // البحث في الكلمات
        function searchWords() {
            const query = searchInput.value.trim().toLowerCase();
            
            if (!query) {
                loadWords();
                return;
            }
            
            const words = JSON.parse(localStorage.getItem('fulfuldeDictionary')) || [];
            const filteredWords = words.filter(word => {
                return word.fulfulde.toLowerCase().includes(query) ||
                       word.arabic.includes(query) ||
                       word.english.toLowerCase().includes(query);
            });
            
            displayWords(filteredWords);
        }
        
        // إظهار الإشعارات
        function showNotification(message, type = 'success') {
            notification.textContent = message;
            notification.style.backgroundColor = type === 'success' ? '#2c5e1a' : '#c0392b';
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
    </script>
</body>
</html>
