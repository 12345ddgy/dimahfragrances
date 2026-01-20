<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DIMAH FRAGRANCES | فخامة العطور</title>
    <style>
        :root {
            --gold: #d4af37;
            --dark-gold: #b38f2d;
            --white: #ffffff;
            --bg: #fdfdfd;
            --text: #2c2c2c;
            --fb-color: #1877F2;
        }

        body { margin: 0; font-family: 'Segoe UI', sans-serif; background-color: var(--bg); color: var(--text); }

        /* الهيدر */
        header {
            background: var(--white);
            padding: 10px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--gold);
            position: sticky; top: 0; z-index: 1000;
        }

        .logo { color: var(--gold); font-size: 1.4rem; font-weight: bold; text-decoration: none; }

        /* سلة المشتريات */
        .cart-toggle {
            background: var(--gold); color: white; border: none;
            padding: 8px 18px; border-radius: 20px; cursor: pointer; font-weight: bold;
        }

        /* واجهة الموقع (الصورة المرفقة) */
        .hero {
            height: 85vh;
            background: linear-gradient(rgba(0,0,0,0.1), rgba(0,0,0,0.1)), 
                        url('image_8acb3c.jpg') center/cover no-repeat;
            display: flex; align-items: center; justify-content: center; text-align: center;
        }

        .hero-content {
            background: rgba(255, 255, 255, 0.9);
            padding: 40px; border: 2px solid var(--gold); box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        /* قسم عن ديمة */
        .about-section {
            padding: 60px 10%; text-align: center; background: var(--white);
        }

        .about-text h2 { color: var(--gold); margin-bottom: 20px; }
        .about-text p { max-width: 800px; margin: 0 auto 30px; line-height: 1.8; font-size: 1.1rem; }

        .fb-btn {
            background: var(--fb-color); color: white; padding: 12px 30px;
            border-radius: 25px; text-decoration: none; font-weight: bold; display: inline-block;
            transition: 0.3s;
        }
        .fb-btn:hover { opacity: 0.9; transform: scale(1.05); }

        /* البحث والمنتجات */
        .search-container { padding: 40px 10% 0; text-align: center; }
        #searchBar {
            width: 100%; max-width: 500px; padding: 12px;
            border: 1px solid var(--gold); border-radius: 25px; outline: none;
        }

        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 25px; padding: 40px 10%;
        }

        .product-card {
            background: var(--white); border: 1px solid #eee; border-radius: 10px;
            overflow: hidden; transition: 0.3s; text-align: center;
        }
        .product-card:hover { border-color: var(--gold); box-shadow: 0 5px 15px rgba(0,0,0,0.05); }
        .product-card img { width: 100%; height: 230px; object-fit: contain; padding: 10px; }

        .btn-add {
            background: var(--gold); color: white; border: none;
            padding: 12px; width: 100%; cursor: pointer; font-weight: bold;
        }

        /* مودال السلة */
        #cartModal {
            position: fixed; left: -400px; top: 0; width: 320px; height: 100%;
            background: white; box-shadow: 5px 0 15px rgba(0,0,0,0.2);
            transition: 0.4s; z-index: 2000; padding: 20px;
        }
        #cartModal.active { left: 0; }

        footer { background: #fff; border-top: 3px solid var(--gold); padding: 40px; text-align: center; }

    </style>
</head>
<body>

<header>
    <a href="#" class="logo">DIMAH FRAGRANCES</a>
    <button class="cart-toggle" onclick="toggleCart()">🛒 السلة (<span id="cartCount">0</span>)</button>
</header>

<section class="hero">
    <div class="hero-content">
        <h1 style="color:var(--gold); margin:0; letter-spacing: 2px;">DIMAH FRAGRANCES</h1>
        <p style="font-weight: bold; margin-top: 10px;">حيث تلتقي الفخامة بالرائحة</p>
    </div>
</section>

<section class="about-section">
    <div class="about-text">
        <h2>قصة ديمة للعطور</h2>
        <p>
            نحن في <b>Dimah Fragrances</b> نؤمن أن العطر هو التوقيع الخفي لكل شخصية. 
            نسعى جاهدين لتقديم أجود تركيبات الزيوت العطرية العالمية المستوحاة من دور الأزياء الفاخرة، 
            بتركيز عالٍ وثبات مذهل يرافقك طوال اليوم.
        </p>
        <a href="https://www.facebook.com/groups/1607807530395013" target="_blank" class="fb-btn">
            زيارة صفحتنا على فيسبوك 
        </a>
    </div>
</section>

<div class="search-container">
    <h3 style="color:var(--gold)">استكشف مجموعتنا الفاخرة</h3>
    <input type="text" id="searchBar" placeholder="ابحث عن عطر (مثال: Sauvage أو Yara)..." onkeyup="filterProducts()">
</div>

<section class="products-grid" id="productContainer"></section>

<div id="cartModal">
    <h2 style="color:var(--gold)">طلباتك</h2>
    <div id="cartItems" style="max-height: 70vh; overflow-y: auto;"></div>
    <hr>
    <p><b>الإجمالي: </b><span id="cartTotal">0</span> EGP</p>
    <button class="btn-add" onclick="checkout()">إتمام الطلب عبر واتساب</button>
    <button onclick="toggleCart()" style="background:none; border:none; color:red; cursor:pointer; margin-top:15px; width:100%;">إغلاق</button>
</div>

<footer>
    <p>© 2026 DIMAH FRAGRANCES - جميع الحقوق محفوظة</p>
    <p style="color: #888;">خدمة العملاء: 011020302042</p>
</footer>

<script>
    // قائمة الـ 36 عطر المحدثة بأسعارها وصورها
    const perfumes = [
        { id: 1, brand: "Nasomato", name: "Black Afgano", prices: { "50ml": 355, "30ml": 250, "10ml": 80, "5ml": 40 }, img: "https://fimgs.net/images/perfume/m.6472.jpg" },
        { id: 2, brand: "Montale", name: "Arabian Tonica", prices: { "50ml": 355, "30ml": 250, "10ml": 80, "5ml": 40 }, img: "https://fimgs.net/images/perfume/m.56637.jpg" },
        { id: 3, brand: "Creed", name: "Creed Aventus", prices: { "50ml": 330, "30ml": 225, "10ml": 70, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.9828.jpg" },
        { id: 4, brand: "Maison Crivelli", name: "Oud Maracuja", prices: { "50ml": 330, "30ml": 225, "10ml": 70, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.84478.jpg" },
        { id: 5, brand: "Gissa", name: "Imperial Valley", prices: { "50ml": 280, "30ml": 190, "10ml": 65, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.73024.jpg" },
        { id: 6, brand: "Arabian Oud", name: "Madawy", prices: { "50ml": 280, "30ml": 190, "10ml": 65, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.46333.jpg" },
        { id: 7, brand: "Lattafah", name: "Khomra Coffee", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.85465.jpg" },
        { id: 8, brand: "YSL", name: "Libre", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.56077.jpg" },
        { id: 9, brand: "Narciso", name: "Narciso Poudree", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.36355.jpg" },
        { id: 10, brand: "Elie Saab", name: "Elie Saab EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.12258.jpg" },
        { id: 11, brand: "Tom Ford", name: "Black Orchid", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.1018.jpg" },
        { id: 12, brand: "Victor & Rolf", name: "Spice Bomb Extreme", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.30459.jpg" },
        { id: 13, brand: "Burberry", name: "Burberry Her", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.51697.jpg" },
        { id: 14, brand: "Victoria Secret", name: "Love is Heavenly", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.15017.jpg" },
        { id: 15, brand: "Victoria Secret", name: "Very Sexy Now", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.44521.jpg" },
        { id: 16, brand: "Victoria Secret", name: "Bomb Chill", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.63183.jpg" },
        { id: 17, brand: "Carolina Herrera", name: "Good Girl", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.39688.jpg" },
        { id: 18, brand: "Jean Paul Gaultier", name: "Le Male Elixir", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.81640.jpg" },
        { id: 19, brand: "Chanel", name: "Bleu de Chanel EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.25967.jpg" },
        { id: 20, brand: "Kayali", name: "Kayali Vanilla 28", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.52554.jpg" },
        { id: 21, brand: "Armani", name: "Stronger With You", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.45258.jpg" },
        { id: 22, brand: "Paco Rabanne", name: "Invictus Victory Elixir", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.79153.jpg" },
        { id: 23, brand: "Paco Rabanne", name: "One Million EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.61902.jpg" },
        { id: 24, brand: "Dior", name: "Sauvage EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.31861.jpg" },
        { id: 25, brand: "Roberto Cavalli", name: "Roberto Cavalli EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.13892.jpg" },
        { id: 26, brand: "Giorgio Armani", name: "Acqua Di Gio EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.3428.jpg" },
        { id: 27, brand: "Lattafah", name: "Yara", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.63488.jpg" },
        { id: 28, brand: "Lattafah", name: "Yara Candy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.92429.jpg" },
        { id: 29, brand: "Paco Rabanne", name: "Olympia", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.31661.jpg" },
        { id: 30, brand: "CH", name: "212 Sexy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.611.jpg" },
        { id: 31, brand: "Billie Eilish", name: "Eilish", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.70034.jpg" },
        { id: 32, brand: "Mancera", name: "Bianko Latte", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.85404.jpg" },
        { id: 33, brand: "Britney Spears", name: "Fantasy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.600.jpg" },
        { id: 34, brand: "Aquolina", name: "Pink Sugar", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.976.jpg" },
        { id: 35, brand: "Armani", name: "My Way EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.62035.jpg" },
        { id: 36, brand: "Lancome", name: "La Vie Est Belle", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.14982.jpg" }
    ];

    let cart = [];

    function renderProducts(data) {
        const grid = document.getElementById('productContainer');
        grid.innerHTML = data.map(p => `
            <div class="product-card">
                <img src="${p.img}" alt="${p.name}">
                <div style="padding:15px">
                    <small style="color:#999">${p.brand}</small>
                    <h4 style="margin:5px 0">${p.name}</h4>
                    <select id="size-${p.id}" style="width:100%; padding:8px; margin:10px 0;">
                        ${Object.entries(p.prices).map(([size, pr]) => `<option value="${size}">${size} - ${pr} EGP</option>`).join('')}
                    </select>
                    <button class="btn-add" onclick="addToCart(${p.id})">إضافة للسلة</button>
                </div>
            </div>
        `).join('');
    }

    function addToCart(id) {
        const p = perfumes.find(item => item.id === id);
        const size = document.getElementById(`size-${id}`).value;
        const price = p.prices[size];
        cart.push({ name: p.name, size, price });
        updateCartUI();
        if(!document.getElementById('cartModal').classList.contains('active')) toggleCart();
    }

    function updateCartUI() {
        document.getElementById('cartCount').innerText = cart.length;
        const list = document.getElementById('cartItems');
        let total = 0;
        list.innerHTML = cart.map((item, idx) => {
            total += item.price;
            return `<div style="padding:10px; border-bottom:1px solid #eee;">
                        <b>${item.name}</b> (${item.size}) - ${item.price} EGP
                        <button onclick="removeItem(${idx})" style="color:red; float:left; background:none; border:none; cursor:pointer;">حذف</button>
                    </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = total;
    }

    function removeItem(idx) { cart.splice(idx, 1); updateCartUI(); }
    function toggleCart() { document.getElementById('cartModal').classList.toggle('active'); }

    function filterProducts() {
        const q = document.getElementById('searchBar').value.toLowerCase();
        const filtered = perfumes.filter(p => p.name.toLowerCase().includes(q) || p.brand.toLowerCase().includes(q));
        renderProducts(filtered);
    }

    function checkout() {
        if(cart.length === 0) return alert("السلة فارغة!");
        let msg = "مرحباً Dimah Fragrances، أود طلب الآتي:\n";
        cart.forEach(i => msg += `• ${i.name} (${i.size}) - ${i.price} EGP\n`);
        msg += `\nالإجمالي: ${document.getElementById('cartTotal').innerText} EGP`;
        window.open(`https://wa.me/2011020302042?text=${encodeURIComponent(msg)}`);
    }

    renderProducts(perfumes);
</script>
</body>
</html>
