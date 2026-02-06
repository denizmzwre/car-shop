<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>بازاڕی ئۆتۆمبێل</title>
    <style>
        :root {
            --primary: #007aff; --success: #34c759; --danger: #ff3b30; --vip: #ffcc00;
            --bg: #f2f2f7; --card-bg: #ffffff; --text: #1c1c1e; --border: #d1d1d6;
        }
        [data-theme="dark"] {
            --bg: #1c1c1e; --card-bg: #2c2c2e; --text: #f2f2f7; --border: #3a3a3c;
        }
        body { font-family: -apple-system, Tahoma, sans-serif; background: var(--bg); margin: 0; direction: rtl; color: var(--text); transition: 0.3s; padding-bottom: 90px; }
        header { background: var(--card-bg); padding: 10px 15px; border-bottom: 1px solid var(--border); position: sticky; top: 0; z-index: 1000; display: flex; justify-content: space-between; align-items: center; backdrop-filter: blur(10px); }
        .logo-container { display: flex; align-items: center; gap: 8px; cursor: pointer; user-select: none; }
        .logo-svg { width: 30px; height: 30px; fill: var(--primary); }
        .logo-text { font-weight: 800; font-size: 16px; color: var(--primary); }
        .nav-btns { display: flex; gap: 8px; align-items: center; }
        .icon-btn { background: var(--bg); border: 1px solid var(--border); width: 35px; height: 35px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 13px; font-weight: bold; color: var(--text); padding: 0; transition: 0.2s; }
        .container { max-width: 500px; margin: auto; padding: 15px; }
        .card { background: var(--card-bg); padding: 20px; border-radius: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); margin-bottom: 20px; border: 1px solid var(--border); }
        select, input, textarea { width: 100%; padding: 12px; margin: 8px 0; border: 1px solid var(--border); border-radius: 12px; background: var(--bg); color: var(--text); font-size: 16px; outline: none; }
        .main-btn { width: 100%; padding: 14px; border: none; border-radius: 12px; background: var(--primary); color: white; font-weight: bold; cursor: pointer; }
        .car-item { background: var(--card-bg); border-radius: 20px; overflow: hidden; margin-bottom: 25px; border: 2px solid var(--border); position: relative; }
        .car-item.is-vip { border-color: var(--vip); }
        .car-item img.main-img { width: 100%; height: 230px; object-fit: cover; }
        .vip-tag { position: absolute; top: 10px; right: 10px; background: var(--vip); color: #000; padding: 3px 10px; border-radius: 8px; font-weight: bold; font-size: 11px; }
        .price { color: var(--success); font-weight: bold; font-size: 20px; margin: 5px 0; }
        .admin-support-btn { position: fixed; bottom: 20px; left: 20px; background: #25d366; color: white; padding: 12px 18px; border-radius: 50px; text-decoration: none; font-weight: bold; box-shadow: 0 4px 15px rgba(0,0,0,0.2); z-index: 2000; display: flex; align-items: center; gap: 8px; font-size: 13px; }
    </style>
</head>
<body>

<header>
    <div class="nav-btns">
        <button class="icon-btn" onclick="toggleTheme()" id="theme-icon">🌙</button>
        <button class="icon-btn" onclick="toggleLang()" id="lang-btn">AR</button>
    </div>
    <div class="logo-container" onclick="secretAdminAccess()">
        <span class="logo-text" id="site-title">بازاڕی ئۆتۆمبێل</span>
        <svg class="logo-svg" viewBox="0 0 24 24"><path d="M18.92 6.01C18.72 5.42 18.16 5 17.5 5h-11c-.66 0-1.21.42-1.42 1.01L3 12v8c0 .55.45 1 1 1h1c.55 0 1-.45 1-1v-1h12v1c0 .55.45 1 1 1h1c.55 0 1-.45 1-1v-8l-2.08-5.99zM6.5 16c-.83 0-1.5-.67-1.5-1.5S5.67 13 6.5 13s1.5.67 1.5 1.5S7.33 16 6.5 16zm11 0c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5zM5 11l1.5-4.5h11L19 11H5z"/></svg>
    </div>
</header>

<div class="container">
    <div class="card">
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
            <select id="filter-brand" onchange="applyFilters()">
                <option value="all" id="lang-all-brands">هەموو براندەکان</option>
                <option value="Dodge">Dodge</option><option value="Toyota">Toyota</option>
                <option value="Mercedes Benz">Mercedes Benz</option><option value="BMW">BMW</option>
                <option value="Mazda">Mazda</option><option value="BYD">BYD</option>
                <option value="MG">MG</option><option value="Kia">Kia</option>
                <option value="Hyundai">Hyundai</option>
            </select>
            <select id="filter-year" onchange="applyFilters()"><option value="all" id="lang-year">ساڵ</option></select>
        </div>
    </div>

    <div class="card">
        <h3 id="lang-form-title">بڵاوکردنەوەی ڕیکلام</h3>
        <select id="car-brand">
            <option value="" id="lang-select-brand">هەڵبژاردنی براند</option>
            <option value="Dodge">Dodge</option><option value="Toyota">Toyota</option>
            <option value="Mercedes Benz">Mercedes Benz</option><option value="BMW">BMW</option>
            <option value="Mazda">Mazda</option><option value="BYD">BYD</option>
            <option value="MG">MG</option><option value="Kia">Kia</option>
            <option value="Hyundai">Hyundai</option>
        </select>
        <input type="text" id="car-model" placeholder="مۆدێل">
        <input type="number" id="car-year-in" placeholder="ساڵ">
        <input type="number" id="car-price" placeholder="نرخ ($)">
        <input type="tel" id="car-phone" placeholder="واتسئاپ">
        <textarea id="car-damage" placeholder="تێبینی..."></textarea>
        <div style="font-size:11px; margin-top:5px;" id="lang-img-car">وێنەی سەیارە:</div>
        <input type="file" id="car-img" accept="image/*">
        <div style="font-size:11px; margin-top:5px;" id="lang-img-receipt">وێنەی پسوڵە:</div>
        <input type="file" id="receipt-img" accept="image/*">
        <button class="main-btn" id="send-btn" onclick="handleUpload()">ناردن</button>
    </div>

    <div id="cars-display"></div>
</div>

<a href="https://wa.me/964750XXXXXXX" class="admin-support-btn" target="_blank" id="support-btn">
    <span>پشتیوانی ئەدمین</span>
</a>

<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
    import { getFirestore, collection, addDoc, getDocs, query, orderBy, doc, updateDoc, deleteDoc, increment } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";
    import { getStorage, ref, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-storage.js";

    // --- Firebase Configuration (لێرە هی خۆت دابنێ) ---
    const firebaseConfig = {
        apiKey: "AIza...",
        projectId: "...",
        storageBucket: "...",
        appId: "..."
    };

    const app = initializeApp(firebaseConfig);
    const db = getFirestore(app);
    const storage = getStorage(app);

    // --- لۆجیکی زمان ---
    const i18n = {
        ku: { title: "بازاڕی ئۆتۆمبێل", all: "هەموو براندەکان", yr: "ساڵ", fTitle: "بڵاوکردنەوەی ڕیکلام", selB: "هەڵبژاردنی براند", mod: "مۆدێل", pr: "نرخ ($)", wa: "واتسئاپ", dam: "تێبینی...", imgC: "وێنەی سەیارە:", imgR: "وێنەی پسوڵە:", send: "ناردن بۆ ئەدمین", supp: "پشتیوانی ئەدمین", ln: "AR" },
        ar: { title: "سوق السيارات", all: "جميع الماركات", yr: "السنة", fTitle: "نشر إعلان", selB: "اختر الماركة", mod: "الموديل", pr: "السعر ($)", wa: "واتساب", dam: "ملاحظات...", imgC: "صورة السيارة:", imgR: "صورة الوصل:", send: "إرسال للمسؤول", supp: "دعم المسؤول", ln: "KU" }
    };

    let currentLang = localStorage.getItem('lang') || 'ku';
    window.toggleLang = () => { currentLang = currentLang === 'ku' ? 'ar' : 'ku'; localStorage.setItem('lang', currentLang); applyLang(); };
    
    function applyLang() {
        const t = i18n[currentLang];
        document.getElementById('site-title').innerText = t.title;
        document.getElementById('lang-btn').innerText = t.ln;
        document.getElementById('lang-all-brands').innerText = t.all;
        document.getElementById('lang-year').innerText = t.yr;
        document.getElementById('lang-form-title').innerText = t.fTitle;
        document.getElementById('lang-select-brand').innerText = t.selB;
        document.getElementById('car-model').placeholder = t.mod;
        document.getElementById('car-year-in').placeholder = t.yr;
        document.getElementById('car-price').placeholder = t.pr;
        document.getElementById('car-phone').placeholder = t.wa;
        document.getElementById('car-damage').placeholder = t.dam;
        document.getElementById('lang-img-car').innerText = t.imgC;
        document.getElementById('lang-img-receipt').innerText = t.imgR;
        document.getElementById('send-btn').innerText = t.send;
        document.getElementById('support-btn').querySelector('span').innerText = t.supp;
    }
    applyLang();

    // --- لۆجیکی ئەدمینی نهێنی ---
    let isAdmin = false, clickCount = 0, clickTimer;
    window.secretAdminAccess = () => {
        clickCount++; clearTimeout(clickTimer);
        clickTimer = setTimeout(() => { clickCount = 0; }, 2000);
        if(clickCount === 3) {
            if(prompt("Code:") === "2024") { isAdmin = true; renderAds(); }
        }
    };

    // --- لۆجیکی مۆدی شەو ---
    window.toggleTheme = () => {
        const theme = document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
        document.documentElement.setAttribute('data-theme', theme);
        document.getElementById('theme-icon').innerText = theme === 'dark' ? '☀️' : '🌙';
        localStorage.setItem('theme', theme);
    };
    if(localStorage.getItem('theme') === 'dark') toggleTheme();

    // --- فایەربەیس: ناردن ---
    window.handleUpload = async () => {
        const cF = document.getElementById('car-img').files[0], rF = document.getElementById('receipt-img').files[0];
        if(!cF || !rF) return alert("Please select images");
        document.getElementById('send-btn').disabled = true;
        try {
            const cU = await up(cF, 'cars/'), rU = await up(rF, 'receipts/');
            await addDoc(collection(db, "ads"), {
                brand: document.getElementById('car-brand').value, model: document.getElementById('car-model').value,
                year: document.getElementById('car-year-in').value, price: document.getElementById('car-price').value,
                phone: document.getElementById('car-phone').value, damage: document.getElementById('car-damage').value,
                image: cU, receipt: rU, approved: false, isVip: false, views: 0, createdAt: Date.now()
            });
            alert("Sent!"); location.reload();
        } catch(e) { alert(e.message); document.getElementById('send-btn').disabled = false; }
    };

    async function up(file, path) {
        const sRef = ref(storage, path + Date.now() + "_" + file.name);
        await uploadBytes(sRef, file); return getDownloadURL(sRef);
    }

    // --- فایەربەیس: نیشاندان و فلتەر ---
    const fY = document.getElementById('filter-year');
    for(let y=2026; y>=1995; y--) fY.innerHTML += `<option value="${y}">${y}</option>`;

    window.applyFilters = () => {
        const b = document.getElementById('filter-brand').value, y = document.getElementById('filter-year').value;
        document.querySelectorAll('.car-item').forEach(el => {
            el.style.display = ((b==='all'||el.dataset.brand===b) && (y==='all'||el.dataset.year===y)) ? "block" : "none";
        });
    };

    window.approve = async (id) => { await updateDoc(doc(db, "ads", id), { approved: true }); renderAds(); };
    window.del = async (id) => { if(confirm("Delete?")) { await deleteDoc(doc(db, "ads", id)); renderAds(); } };
    window.setVip = async (id, s) => { await updateDoc(doc(db, "ads", id), { isVip: s }); renderAds(); };

    async function renderAds() {
        const q = query(collection(db, "ads"), orderBy("isVip", "desc"), orderBy("createdAt", "desc"));
        const snap = await getDocs(q);
        const disp = document.getElementById('cars-display'); disp.innerHTML = "";
        snap.forEach(async d => {
            const ad = d.data(); if(!ad.approved && !isAdmin) return;
            disp.innerHTML += `
                <div class="car-item ${ad.isVip?'is-vip':''}" data-brand="${ad.brand}" data-year="${ad.year}">
                    <img class="main-img" src="${ad.image}">
                    ${ad.isVip?'<div class="vip-tag">⭐️ VIP</div>':''}
                    <div style="padding:15px;">
                        <div style="font-size:11px; opacity:0.6;">👁️ ${ad.views} | 📅 ${ad.year}</div>
                        <h3 style="margin:5px 0;">${ad.brand} ${ad.model}</h3>
                        <div class="price">$${ad.price}</div>
                        <p style="font-size:14px; opacity:0.8;">${ad.damage}</p>
                        <a href="https://wa.me/${ad.phone}" style="display:block; background:#25d366; color:white; text-align:center; padding:12px; border-radius:12px; text-decoration:none; font-weight:bold;">WhatsApp</a>
                        ${isAdmin ? `<div style="margin-top:10px; border-top:1px solid var(--border); padding-top:10px;">
                            <img src="${ad.receipt}" style="width:100%; height:100px; object-fit:contain; background:#000; border-radius:8px;">
                            <button onclick="approve('${d.id}')" style="background:var(--success); margin-top:5px; padding:8px; border-radius:8px; width:100%; color:white;">Approve</button>
                            <button onclick="setVip('${d.id}', ${!ad.isVip})" style="background:var(--vip); margin-top:5px; padding:8px; border-radius:8px; width:100%;">VIP</button>
                            <button onclick="del('${d.id}')" style="background:var(--danger); margin-top:5px; padding:8px; border-radius:8px; width:100%; color:white;">Delete</button>
                        </div>` : ''}
                    </div>
                </div>`;
            if(ad.approved && !isAdmin) await updateDoc(doc(db, "ads", d.id), { views: increment(1) });
        });
    }
    renderAds();
</script>
</body>
</html>
