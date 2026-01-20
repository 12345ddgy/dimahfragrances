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
            --text: #2c2c2c;
            --fb-color: #1877F2;
        }

        body { margin: 0; font-family: 'Segoe UI', sans-serif; background-color: #f4f4f4; color: var(--text); }

        /* الهيدر */
        header {
            background: rgba(255, 255, 255, 0.95);
            padding: 10px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--gold);
            position: sticky; top: 0; z-index: 1000;
        }

        .logo { color: var(--gold); font-size: 1.4rem; font-weight: bold; text-decoration: none; }

        /* الواجهة الرئيسية مع الصورة كخلفية كاملة */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), 
                        url('blob:https://web.whatsapp.com/7bc102c2-3463-4fcd-956a-0c3d87cbfd92') center/cover no-repeat fixed;
            display: flex; align-items: center; justify-content: center; text-align: center;
        }

        .hero-glass {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            padding: 50px;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            color: white;
        }

        /* قسم عن البراند */
        .about-section {
            padding: 80px 10%; text-align: center; background: var(--white);
        }

        .fb-btn {
            background: var(--fb-color); color: white; padding: 15px 35px;
            border-radius: 30px; text-decoration: none; font-weight: bold; 
            display: inline-block; transition: 0.3s;
        }

        /* البحث والمنتجات */
        .search-area { padding: 40px 10%; background: #fff; text-align: center; }
        #searchBar {
            width: 100%; max-width: 600px; padding: 15px;
            border: 2px solid var(--gold); border-radius: 30px; outline: none;
            font-size: 1.1rem;
        }

        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px; padding: 40px 10%; background: #f9f9f9;
        }

        .product-card {
            background: white; border: 1px solid #ddd; border-radius: 15px;
            overflow: hidden; transition: 0.4s;
        }
        .product-card:hover { transform: translateY(-10px); border-color: var(--gold); }
        
        .btn-add {
            background: var(--gold); color: white; border: none;
            padding: 15px; width: 100%; cursor: pointer; font-weight: bold;
        }

        /* مودال السلة */
        #cartModal {
            position: fixed; left: -400px; top: 0; width: 350px; height: 100%;
            background: white; z-index: 2000; padding: 25px; transition: 0.5s;
            box-shadow: 10px 0 30px rgba(0,0,0,0.2);
        }
        #cartModal.active { left: 0; }

        footer { padding: 50px; background: #222; color: #fff; text-align: center; }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo">DIMAH FRAGRANCES</a>
    <button onclick="toggleCart()" style="background:var(--gold); color:white; border:none; padding:10px 20px; border-radius:20px; cursor:pointer;">
        🛒 السلة (<span id="cartCount">0</span>)
    </button>
</header>

<section class="hero">
    <div class="hero-glass">
        <h1 style="font-size: 3rem; margin: 0;">DIMAH FRAGRANCES</h1>
        <p style="font-size: 1.5rem; letter-spacing: 2px;">عالم من السحر والجاذبية</p>
        <a href="#shop" style="background:var(--gold); color:white; padding:10px 30px; text-decoration:none; border-radius:5px; margin-top:20px; display:inline-block;">اكتشف العطور</a>
    </div>
</section>

<section class="about-section">
    <h2 style="color:var(--gold)">من نحن</h2>
    <p style="max-width: 800px; margin: 20px auto; font-size: 1.2rem; line-height: 1.8;">
        نحن متخصصون في تركيب أرقى العطور العالمية المستوحاة من الماركات الكبرى، نستخدم زيوتًا فرنسية خام بتركيزات عالية لضمان أفضل ثبات وفوحان.
    </p>
    <a href="https://www.facebook.com/groups/1607807530395013" target="_blank" class="fb-btn">انضم لمجتمعنا على فيسبوك</a>
</section>

<div class="search-area" id="shop">
    <input type="text" id="searchBar" placeholder="ابحث عن عطرك المفضل الآن..." onkeyup="filterProducts()">
</div>

<section class="products-grid" id="productContainer"></section>

<div id="cartModal">
    <h2 style="color:var(--gold)">طلبك الحالي</h2>
    <div id="cartItems" style="height: 70vh; overflow-y: auto;"></div>
    <div style="border-top: 2px solid var(--gold); padding-top: 15px;">
        <p><b>الإجمالي: </b><span id="cartTotal">0</span> EGP</p>
        <button class="btn-add" onclick="checkout()">إتمام الطلب عبر واتساب</button>
        <button onclick="toggleCart()" style="width:100%; margin-top:10px; background:none; border:none; color:red; cursor:pointer;">إغلاق السلة</button>
    </div>
</div>

<footer>
    <h3>DIMAH FRAGRANCES</h3>
    <p>جميع عطورنا مستوحاة من الماركات العالمية الأصلية.</p>
    <p>واتساب: 01102302024</p>
</footer>

<script>
    // جميع العطور الـ 36 والأسعار مستخرجة من القائمة
    const perfumes = [
        { id: 1, brand: "Nasomato", name: "Black Afgano", prices: { "50ml": 355, "30ml": 250, "10ml": 80, "5ml": 40 }, img: "https://fimgs.net/images/perfume/m.6472.jpg" },
        { id: 2, brand: "Montale", name: "Arabian Tonica", prices: { "50ml": 355, "30ml": 250, "10ml": 80, "5ml": 40 }, img: "https://fimgs.net/images/perfume/m.56637.jpg" },
        { id: 3, brand: "Creed", name: "Creed Aventus", prices: { "50ml": 330, "30ml": 225, "10ml": 70, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.9828.jpg" },
        { id: 4, brand: "Maison Crivelli", name: "Oud Maracuja", prices: { "50ml": 330, "30ml": 225, "10ml": 70, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.84478.jpg" },
        { id: 5, brand: "Gissa", name: "Immperial Valley", prices: { "50ml": 280, "30ml": 190, "10ml": 65, "5ml": 35 }, img: "https://fimgs.net/images/perfume/m.73024.jpg" },
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
        { id: 17, brand: "CH", name: "Good Girl", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.39688.jpg" },
        { id: 18, brand: "Jean Paul Gaultier", name: "Le Male Elixir", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.81640.jpg" },
        { id: 19, brand: "Chanel", name: "Bleu de Chanel EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.25967.jpg" },
        { id: 20, brand: "Kayali", name: "Kayali Vanilla 28", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.52554.jpg" },
        { id: 21, brand: "Armani", name: "Stronger With You", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.45258.jpg" },
        { id: 22, brand: "Paco Rabanne", name: "Invictus Victory Elixir", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.79153.jpg" },
        { id: 23, brand: "Paco Rabanne", name: "One Million EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.61902.jpg" },
        { id: 24, brand: "Dior", name: "Sauvage EDP", prices: { "50ml": 265, "30ml": 180, "10ml": 55, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.31861.jpg" },
        { id: 25, brand: "Roberto Cavalli", name: "Roberto Cavalli EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.13892.jpg" },
        { id: 26, brand: "Armani", name: "Acqua Di Gio EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.3428.jpg" },
        { id: 27, brand: "Lattafah", name: "Yara", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.63488.jpg" },
        { id: 28, brand: "Lattafah", name: "Yara Candy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.92429.jpg" },
        { id: 29, brand: "Paco Rabanne", name: "Olymbia", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.31661.jpg" },
        { id: 30, brand: "CH", name: "212 Sexy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.611.jpg" },
        { id: 31, brand: "Billie Eilish", name: "Billie Eilish", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.70034.jpg" },
        { id: 32, brand: "Mancera", name: "Bianko Latte", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.85404.jpg" },
        { id: 33, brand: "Britney Spears", name: "Fantazy", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.600.jpg" },
        { id: 34, brand: "Aquolina", name: "Pink Sugar", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.976.jpg" },
        { id: 35, brand: "Armani", name: "My Way EDP", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.62035.jpg" },
        { id: 36, brand: "Lancome", name: "La Vie Est Belle", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.14982.jpg" },
        { id: 37, brand: "Bath & Body Works", name: "Jabanese Cherry Blsoom", prices: { "50ml": 250, "30ml": 170, "10ml": 50, "5ml": 30 }, img: "https://fimgs.net/images/perfume/m.1130.jpg" }
    ];

    let cart = [];

    function renderProducts(data) {
        const grid = document.getElementById('productContainer');
        grid.innerHTML = data.map(p => `
            <div class="product-card">
                <img src="${p.img}" alt="${p.name}">
                <div style="padding:15px">
                    <small>${p.brand}</small>
                    <h4>${p.name}</h4>
                    <select id="size-${p.id}" style="width:100%; padding:10px; margin-bottom:15px;">
                        ${Object.entries(p.prices).map(([size, price]) => `<option value="${size}">${size} - ${price} EGP</option>`).join('')}
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
        toggleCart();
    }

    function updateCartUI() {
        document.getElementById('cartCount').innerText = cart.length;
        const items = document.getElementById('cartItems');
        let total = 0;
        items.innerHTML = cart.map((item, idx) => {
            total += item.price;
            return `<div style="padding:10px; border-bottom:1px solid #eee;">
                        <b>${item.name}</b> (${item.size}) <br> ${item.price} EGP
                        <button onclick="remove(${idx})" style="color:red; background:none; border:none; cursor:pointer; float:left;">حذف</button>
                    </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = total;
    }

    function remove(idx) { cart.splice(idx, 1); updateCartUI(); }
    function toggleCart() { document.getElementById('cartModal').classList.toggle('active'); }
    function filterProducts() {
        const q = document.getElementById('searchBar').value.toLowerCase();
        const filtered = perfumes.filter(p => p.name.toLowerCase().includes(q) || p.brand.toLowerCase().includes(q));
        renderProducts(filtered);
    }

    function checkout() {
        if(cart.length === 0) return alert("السلة فارغة!");
        let msg = "مرحباً Dimah Fragrances، أود طلب العطور التالية:\n";
        cart.forEach(i => msg += `• ${i.name} (${i.size}) - ${i.price} EGP\n`);
        msg += `\nالإجمالي: ${document.getElementById('cartTotal').innerText} EGP`;
        window.open(`https://wa.me/2011020302042?text=${encodeURIComponent(msg)}`);
    }

    renderProducts(perfumes);
</script>
</body>
</html>
