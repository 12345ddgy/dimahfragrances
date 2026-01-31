<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dimah Fragrances | ديمة للعطور</title>
    <link href="https://fonts.googleapis.com/css2?family=Alexandria:wght@300;500;700&family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #005696;
            --accent-gold: #c5a059;
            --bg-light: #fdfdfd;
            --text-main: #222;
            --white: #ffffff;
        }

        body {
            font-family: 'Alexandria', sans-serif;
            background-color: var(--bg-light);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }

        /* Top Bar */
        .top-announcement {
            background: var(--primary-blue);
            color: white;
            text-align: center;
            padding: 10px 0;
            font-size: 0.85rem;
            letter-spacing: 1px;
            font-weight: 500;
        }

        /* Navbar */
        header {
            background: rgba(255, 255, 255, 0.98);
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 15px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-container img {
            height: 60px; /* شعار ديمة */
            transition: 0.3s;
        }

        .nav-tools {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .social-link {
            color: var(--primary-blue);
            font-size: 1.5rem;
            transition: 0.3s;
        }

        .social-link:hover { color: var(--accent-gold); }

        /* Hero Section */
        .main-banner {
            height: 50vh;
            background: linear-gradient(rgba(255,255,255,0.7), rgba(255,255,255,0.7)), 
                        url('https://lens.usercontent.google.com/image?vsrid=CK2ZodqHoJCqfRACGAEiJDZjYTg0N2JhLWViYWMtNDRkZS1iMTBkLWU2NzYxZjNiOWNkOTIGIgJlaCgfOOLNj7PFtZID&gsessionid=sAIEum9A8pNdzFAaxiVUdpA0o3I_ZvBbnPQbTAYcuvW5CJfM2TuDFg');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            border-bottom: 4px solid var(--accent-gold);
        }

        .main-banner h1 {
            font-size: 3rem;
            color: var(--primary-blue);
            margin: 0;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        /* Products Grid */
        .content-wrapper { padding: 40px 5%; }

        .search-box {
            max-width: 600px;
            margin: -30px auto 50px;
            position: relative;
        }

        #searchInput {
            width: 100%;
            padding: 18px 25px;
            border-radius: 50px;
            border: none;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            font-family: 'Cairo';
            font-size: 1rem;
            outline: none;
        }

        .perfume-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 35px;
        }

        .perfume-card {
            background: var(--white);
            border-radius: 4px;
            overflow: hidden;
            transition: 0.4s;
            border: 1px solid #eee;
            position: relative;
        }

        .perfume-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
        }

        .img-container {
            height: 320px;
            background: #f9f9f9;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .img-container img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }

        .badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--accent-gold);
            color: white;
            padding: 5px 15px;
            font-size: 0.7rem;
            border-radius: 2px;
            text-transform: uppercase;
        }

        .details {
            padding: 20px;
            text-align: center;
        }

        .brand-name {
            color: #888;
            font-size: 0.8rem;
            text-transform: uppercase;
            margin-bottom: 5px;
        }

        .fragrance-name {
            font-weight: 700;
            font-size: 1.2rem;
            color: var(--primary-blue);
            margin-bottom: 10px;
        }

        .price-tag {
            font-size: 1.3rem;
            color: #d0021b;
            font-weight: 700;
            margin: 15px 0;
        }

        .add-to-cart {
            background: var(--primary-blue);
            color: white;
            border: none;
            width: 100%;
            padding: 15px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .add-to-cart:hover { background: #003d6b; }

        /* Floating Cart */
        .cart-trigger {
            position: fixed;
            bottom: 30px;
            left: 30px;
            background: var(--accent-gold);
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            z-index: 1001;
        }

        /* Mobile Adjustments */
        @media (max-width: 600px) {
            .main-banner h1 { font-size: 1.8rem; }
            .perfume-grid { grid-template-columns: repeat(2, 1fr); gap: 10px; }
            .img-container { height: 200px; }
            .fragrance-name { font-size: 0.9rem; }
            .details { padding: 10px; }
        }
    </style>
</head>
<body>

    <div class="top-announcement">توصيل سريع لجميع المحافظات | جودة تثبت حضورك</div>

    <header>
        <div class="logo-container">
            <h2 style="color: var(--primary-blue); margin: 0;">DIMAH fragrances</h2>
        </div>
        <div class="nav-tools">
            <a href="https://www.facebook.com/your-page-link" class="social-link" target="_blank">
                <i class="fab fa-facebook"></i>
            </a>
            <div onclick="toggleCart()" style="cursor:pointer; position:relative;">
                <i class="fas fa-shopping-bag" style="font-size: 1.5rem; color: var(--primary-blue);"></i>
                <span id="cart-count" style="position:absolute; top:-10px; right:-10px; background:red; color:white; border-radius:50%; padding:2px 6px; font-size:0.7rem;">0</span>
            </div>
        </div>
    </header>

    <section class="main-banner">
        <h1 style="font-family: 'Cairo'">مجموعتنا الكاملة</h1>
        <p>36 عبيرًا ساحرًا يروي قصة أناقتك</p>
    </section>

    <div class="content-wrapper">
        <div class="search-box">
            <input type="text" id="searchInput" placeholder="ابحث عن عطرك المفضل (مثلاً: Sauvage, Black Afgano)..." onkeyup="filterItems()">
        </div>

        <div class="perfume-grid" id="perfumeGrid">
            </div>
    </div>

    <div class="cart-trigger" onclick="toggleCart()">
        <i class="fas fa-shopping-cart"></i>
    </div>

    <script>
        const perfumes = [
            { id: 1, brand: "Nasomatto", name: "Black Afgano", price: 250, img: "https://fimgs.net/images/perfume/m.6472.jpg", tag: "رجالي" },
            { id: 2, brand: "Montale", name: "Arabian Tonica", price: 250, img: "https://fimgs.net/images/perfume/m.4431.jpg", tag: "رجالي" },
            { id: 3, brand: "Creed", name: "Aventus", price: 225, img: "https://fimgs.net/images/perfume/m.9828.jpg", tag: "رجالي" },
            { id: 4, brand: "Maison Crivelli", name: "Oud Maracuja", price: 225, img: "https://fimgs.net/images/perfume/m.80635.jpg", tag: "للجنسين" },
            { id: 5, brand: "Gissa", name: "Imperial Valley", price: 190, img: "https://fimgs.net/images/perfume/m.70298.jpg", tag: "للجنسين" },
            { id: 6, brand: "Arabian Oud", name: "Madawy", price: 190, img: "https://fimgs.net/images/perfume/m.46332.jpg", tag: "للجنسين" },
            { id: 7, brand: "Lattafa", name: "Khamrah Qahwa", price: 180, img: "https://fimgs.net/images/perfume/m.87823.jpg", tag: "للجنسين" },
            { id: 8, brand: "YSL", name: "Libre", price: 180, img: "https://fimgs.net/images/perfume/m.56077.jpg", tag: "حريمي" },
            { id: 9, brand: "Narciso", name: "Narciso Poudree", price: 180, img: "https://fimgs.net/images/perfume/m.37624.jpg", tag: "حريمي" },
            { id: 10, brand: "Elie Saab", name: "Elie Saab EDP", price: 180, img: "https://fimgs.net/images/perfume/m.12258.jpg", tag: "حريمي" },
            { id: 11, brand: "Tom Ford", name: "Black Orchid", price: 180, img: "https://fimgs.net/images/perfume/m.1018.jpg", tag: "للجنسين" },
            { id: 12, brand: "V&R", name: "Spicebomb Extreme", price: 180, img: "https://fimgs.net/images/perfume/m.30499.jpg", tag: "رجالي" },
            { id: 13, brand: "Burberry", name: "Burberry Her", price: 180, img: "https://fimgs.net/images/perfume/m.51697.jpg", tag: "حريمي" },
            { id: 14, brand: "Victoria Secret", name: "Love is Heavenly", price: 180, img: "https://fimgs.net/images/perfume/m.14445.jpg", tag: "حريمي" },
            { id: 15, brand: "Victoria Secret", name: "Very Sexy Now", price: 180, img: "https://fimgs.net/images/perfume/m.44318.jpg", tag: "حريمي" },
            { id: 16, brand: "Victoria Secret", name: "Bombshell Celebration", price: 180, img: "https://fimgs.net/images/perfume/m.63004.jpg", tag: "حريمي" },
            { id: 17, brand: "CH", name: "Good Girl", price: 180, img: "https://fimgs.net/images/perfume/m.39688.jpg", tag: "حريمي" },
            { id: 18, brand: "JPG", name: "Le Male Elixir", price: 180, img: "https://fimgs.net/images/perfume/m.81643.jpg", tag: "رجالي" },
            { id: 19, brand: "Chanel", name: "Bleu de Chanel", price: 180, img: "https://fimgs.net/images/perfume/m.25967.jpg", tag: "رجالي" },
            { id: 20, brand: "Kayali", name: "Vanilla 28", price: 180, img: "https://fimgs.net/images/perfume/m.52554.jpg", tag: "حريمي" },
            { id: 21, brand: "Armani", name: "Stronger With You", price: 180, img: "https://fimgs.net/images/perfume/m.45258.jpg", tag: "رجالي" },
            { id: 22, brand: "Paco Rabanne", name: "Invictus Victory", price: 180, img: "https://fimgs.net/images/perfume/m.79255.jpg", tag: "رجالي" },
            { id: 23, brand: "Paco Rabanne", name: "One Million EDP", price: 180, img: "https://fimgs.net/images/perfume/m.61902.jpg", tag: "رجالي" },
            { id: 24, brand: "Dior", name: "Sauvage EDP", price: 180, img: "https://fimgs.net/images/perfume/m.49159.jpg", tag: "رجالي" },
            { id: 25, brand: "Roberto Cavalli", name: "Cavalli EDP", price: 170, img: "https://fimgs.net/images/perfume/m.13875.jpg", tag: "حريمي" },
            { id: 26, brand: "Armani", name: "Acqua di Gio", price: 170, img: "https://fimgs.net/images/perfume/m.71754.jpg", tag: "رجالي" },
            { id: 27, brand: "Lattafa", name: "Yara Pink", price: 170, img: "https://fimgs.net/images/perfume/m.65215.jpg", tag: "حريمي" },
            { id: 28, brand: "Lattafa", name: "Yara Candy", price: 170, img: "https://fimgs.net/images/perfume/m.92641.jpg", tag: "حريمي" },
            { id: 29, brand: "Paco Rabanne", name: "Olympea", price: 170, img: "https://fimgs.net/images/perfume/m.31661.jpg", tag: "حريمي" },
            { id: 30, brand: "CH", name: "212 Sexy", price: 170, img: "https://fimgs.net/images/perfume/m.611.jpg", tag: "حريمي" },
            { id: 31, brand: "Billie Eilish", name: "Eilish No.1", price: 170, img: "https://fimgs.net/images/perfume/m.70054.jpg", tag: "حريمي" },
            { id: 32, brand: "Mancera", name: "Bianco Latte", price: 170, img: "https://fimgs.net/images/perfume/m.64756.jpg", tag: "للجنسين" },
            { id: 33, brand: "Britney Spears", name: "Fantasy", price: 170, img: "https://fimgs.net/images/perfume/m.600.jpg", tag: "حريمي" },
            { id: 34, brand: "Aquolina", name: "Pink Sugar", price: 170, img: "https://fimgs.net/images/perfume/m.976.jpg", tag: "حريمي" },
            { id: 35, brand: "Armani", name: "My Way", price: 170, img: "https://fimgs.net/images/perfume/m.62030.jpg", tag: "حريمي" },
        { id: 36, brand: "Bath & Body", name: "Japanese Cherry Blossom", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, gender: "Female", desc: "عبير الزهور اليابانية الكلاسيكي." }
          
            // أضف باقي الـ 36 هنا بنفس الترتيب
        ];

        function renderProducts() {
            const container = document.getElementById('perfumeGrid');
            container.innerHTML = perfumes.map(p => `
                <div class="perfume-card">
                    <span class="badge">${p.tag}</span>
                    <div class="img-container">
                        <img src="${p.img}" alt="${p.name}">
                    </div>
                    <div class="details">
                        <div class="brand-name">${p.brand}</div>
                        <div class="fragrance-name">${p.name}</div>
                        <select style="width:100%; padding:8px; margin-bottom:10px; border:1px solid #ddd;">
                            <option>حجم 50 مل</option>
                            <option>حجم 30 مل</option>
                            <option>حجم 10 مل</option>
                        </select>
                        <div class="price-tag">${p.price} ج.م</div>
                        <button class="add-to-cart" onclick="addToCart(${p.id})">أضف للحقيبة</button>
                    </div>
                </div>
            `).join('');
        }

        function filterItems() {
            const val = document.getElementById('searchInput').value.toLowerCase();
            document.querySelectorAll('.perfume-card').forEach(card => {
                card.style.display = card.innerText.toLowerCase().includes(val) ? 'block' : 'none';
            });
        }

        // تشغيل الوظائف عند التحميل
        window.onload = renderProducts;

        function toggleCart() {
            // كود السلة الاحترافي (يمكن دمجه مع الكود السابق)
            alert("سيتم نقلك لصفحة إتمام الطلب عبر واتساب");
        }
    </script>
</body>
</html>
