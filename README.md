
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DIMAH Fragrances | ديمة للعطور</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --gold: #c5a059;
            --dark: #1a1a1a;
            --fb-blue: #1877F2;
            --male: #2c3e50;
            --female: #d81b60;
            --unisex: #673ab7;
        }

        body { margin: 0; font-family: 'Segoe UI', sans-serif; background: #fdfdfd; color: var(--dark); direction: rtl; scroll-behavior: smooth; }

        header {
            background: #fff; padding: 15px 5%; display: flex; 
            justify-content: space-between; align-items: center;
            border-bottom: 2px solid var(--gold); position: sticky; top: 0; z-index: 1000;
        }
        .logo { font-size: 1.8rem; font-weight: bold; color: var(--gold); text-decoration: none; }
        
        .cart-status { cursor: pointer; background: var(--gold); color: white; padding: 8px 18px; border-radius: 50px; font-weight: bold; }

        /* About Us */
        .about-section {
            padding: 50px 10%; background: #fff; text-align: center; border-bottom: 1px solid #eee;
        }
        .about-section h2 { color: var(--gold); font-size: 2rem; margin-bottom: 15px; }
        .about-section p { max-width: 800px; margin: 0 auto 25px; line-height: 1.8; color: #555; font-size: 1.1rem; }

        .social-btns { display: flex; justify-content: center; gap: 15px; flex-wrap: wrap; }
        .btn-social {
            padding: 12px 25px; border-radius: 50px; text-decoration: none; font-weight: bold;
            display: inline-flex; align-items: center; gap: 10px; transition: 0.3s; color: white;
        }
        .btn-fb { background: var(--fb-blue); }
        .btn-call { background: #25d366; }
        .btn-social:hover { transform: translateY(-3px); opacity: 0.9; }

        /* Search Area */
        .search-area { padding: 30px 5%; text-align: center; background: #f9f9f9; }
        #searchBar {
            width: 100%; max-width: 600px; padding: 15px; border-radius: 50px; border: 1px solid #ddd; outline: none; font-size: 1rem;
        }

        /* Products Grid */
        .products-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px; padding: 40px 5%;
        }

        .product-card {
            background: #fff; border-radius: 20px; border: 1px solid #eee;
            overflow: hidden; transition: 0.4s; position: relative;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05); display: flex; flex-direction: column;
        }

        .img-container { width: 100%; height: 250px; background: #fff; display: flex; align-items: center; justify-content: center; }
        .img-container img { max-width: 85%; max-height: 85%; object-fit: contain; }

        .gender-tag { position: absolute; top: 12px; right: 12px; padding: 4px 12px; border-radius: 50px; color: #fff; font-size: 0.7rem; font-weight: bold; z-index: 5; }

        .product-info { padding: 15px; text-align: center; flex-grow: 1; }
        .brand { color: var(--gold); font-size: 0.85rem; font-weight: bold; }
        .name { font-size: 1.2rem; font-weight: bold; margin: 5px 0; }
        .desc { font-size: 0.8rem; color: #777; margin-bottom: 15px; height: 3em; overflow: hidden; }

        .price-list { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; }
        .price-item { background: #f9f9f9; border: 1px solid #eee; padding: 8px; border-radius: 8px; font-size: 0.75rem; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 4px; }

        .btn-add { background: var(--gold); color: #fff; border: none; width: 100%; padding: 15px; font-weight: bold; cursor: pointer; }

        /* Sidebar Cart */
        #cartSide {
            position: fixed; left: -100%; top: 0; width: 320px; height: 100%;
            background: #fff; z-index: 2000; transition: 0.4s; padding: 25px;
            box-shadow: 10px 0 30px rgba(0,0,0,0.1);
        }
        #cartSide.active { left: 0; }

        /* Footer */
        footer { background: var(--dark); color: white; padding: 40px 10%; text-align: center; }
        .footer-logo { color: var(--gold); font-size: 1.5rem; font-weight: bold; margin-bottom: 10px; }
        .footer-contact { margin: 15px 0; font-size: 1.1rem; }
        .footer-contact a { color: white; text-decoration: none; font-weight: bold; }
        .rights { margin-top: 25px; font-size: 0.8rem; opacity: 0.5; border-top: 1px solid #333; padding-top: 20px; }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo">DIMAH</a>
    <div class="cart-status" onclick="toggleCart()">🛒 السلة (<span id="count">0</span>)</div>
</header>

<section class="about-section">
    <h2>من نحن</h2>
    <p><b>DIMAH Fragrances</b> تقدم لكم نخبة من العطور المستوحاة من الماركات العالمية، تم اختيارها وتركيبها بدقة لتمنحكم التميز والثبات الذي تستحقونه.</p>
    <div class="social-btns">
        <a href="https://www.facebook.com/groups/1607807530395013/" target="_blank" class="btn-social btn-fb">
            <i class="fab fa-facebook"></i> جروب الفيسبوك
        </a>
        <a href="tel:+201102302024" class="btn-social btn-call">
            <i class="fas fa-phone-alt"></i> اطلب الآن: 01102302024
        </a>
    </div>
</section>

<div class="search-area">
    <input type="text" id="searchBar" placeholder="ابحث عن عطرك المفضل (مثال: Sauvage)..." oninput="render()">
</div>

<div class="products-grid" id="grid"></div>

<div id="cartSide">
    <h3>سلة المشتريات 🛍️</h3>
    <div id="cartItems" style="height:65%; overflow-y:auto; margin:15px 0;"></div>
    <div style="border-top: 2px solid #eee; padding-top: 15px;">
        <h4 style="margin-bottom: 15px;">الإجمالي: <span id="total">0</span> ج.م</h4>
        <button onclick="sendWhatsApp()" style="width:100%; background:#25d366; color:white; padding:15px; border:none; border-radius:12px; font-weight:bold; cursor:pointer; font-size: 1rem;">
            <i class="fab fa-whatsapp"></i> إرسال الطلب للواتساب
        </button>
        <button onclick="toggleCart()" style="width:100%; background:none; border:none; margin-top:15px; cursor:pointer; color:#999;">استكمال التسوق</button>
    </div>
</div>

<footer>
    <div class="footer-logo">DIMAH Fragrances</div>
    <div class="footer-contact">
        للمكالمات والاستفسارات: <br>
        <a href="tel:+201102302024">01102302024</a>
    </div>
    <div class="rights">
        جميع الحقوق محفوظة © 2026 لـ ديمة للعطور - DIMAH Fragrances
    </div>
</footer>

<script>
    // قائمة العطور المحدثة (أمثلة من القائمة الكاملة)
    const perfumes = [
        { id: 1, b: "Nasomato", n: "Black Afgano", d: "رائحة العود والبخور المدخن للقوة والغموض.", p: [370, 260, 90, 50], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.6472.jpg" },
        { id: 2, b: "Montale", n: "Arabian Tonica", d: "مزيج دافئ من التوابل والعود العربي الأصيل.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.44312.jpg" },
        { id: 3, b: "Creed", n: "Creed Aventus", d: "ملك العطور، يجمع بين القوة والانتعاش.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.9828.jpg" },
        { id: 8, b: "YSL", n: "Libre", d: "عطر الحرية، يجمع بين الخزامى وزهر البرتقال.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.56671.jpg" },
        { id: 24, b: "Dior", n: "Sauvage EDP", d: "عطر كاريزمي ومنعش للرجل العصري.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.49144.jpg" },
        { id: 27, b: "Lattafa", n: "Yara", d: "عطر وردي برائحة الفراولة والحلويات.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://lattafa.com/wp-content/uploads/2021/04/Yara-100ml.jpg" },
        { id: 36, b: "Lancome", n: "La Vie Est Belle", d: "عطر السعادة، مزيج السوسن والحلويات.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.14982.jpg" }
        // أضف باقي الـ 36 هنا بنفس التنسيق
    ];

    let cart = [];

    function render() {
        const query = document.getElementById('searchBar').value.toLowerCase();
        const grid = document.getElementById('grid');
        grid.innerHTML = "";

        perfumes.filter(p => p.n.toLowerCase().includes(query) || p.b.toLowerCase().includes(query)).forEach(p => {
            const color = p.g === 'Male' ? 'var(--male)' : p.g === 'Female' ? 'var(--female)' : 'var(--unisex)';
            grid.innerHTML += `
                <div class="product-card">
                    <span class="gender-tag" style="background:${color}">${p.gl}</span>
                    <div class="img-container"><img src="${p.img}" alt="${p.n}"></div>
                    <div class="product-info">
                        <div class="brand">${p.b}</div>
                        <div class="name">${p.n}</div>
                        <div class="desc">${p.d}</div>
                        <div class="price-list">
                            <label class="price-item"><input type="radio" name="s-${p.id}" value="0" checked> 50ml (${p.p[0]}ج)</label>
                            <label class="price-item"><input type="radio" name="s-${p.id}" value="1"> 30ml (${p.p[1]}ج)</label>
                            <label class="price-item"><input type="radio" name="s-${p.id}" value="2"> 10ml (${p.p[2]}ج)</label>
                            <label class="price-item"><input type="radio" name="s-${p.id}" value="3"> 5ml (${p.p[3]}ج)</label>
                        </div>
                    </div>
                    <button class="btn-add" onclick="addToCart(${p.id})">إضافة للسلة 🛒</button>
                </div>`;
        });
    }

    function addToCart(id) {
        const item = perfumes.find(p => p.id === id);
        const sizeIdx = document.querySelector(`input[name="s-${id}"]:checked`).value;
        const sizes = ["50ml", "30ml", "10ml", "5ml"];
        cart.push({ name: item.n, brand: item.b, size: sizes[sizeIdx], price: item.p[sizeIdx] });
        updateCart();
        document.getElementById('cartSide').classList.add('active');
    }

    function updateCart() {
        document.getElementById('count').innerText = cart.length;
        const list = document.getElementById('cartItems');
        let total = 0;
        list.innerHTML = cart.map((i, idx) => {
            total += i.price;
            return `<div style="padding:12px; border-bottom:1px solid #eee; display:flex; justify-content:space-between; align-items:center;">
                <div><b>${i.brand} ${i.name}</b><br><small>${i.size} - ${i.price} ج.م</small></div>
                <span onclick="cart.splice(${idx},1);updateCart()" style="color:#ff4d4d; cursor:pointer; font-weight:bold;">حذف</span>
            </div>`;
        }).join('');
        document.getElementById('total').innerText = total;
    }

    function toggleCart() { document.getElementById('cartSide').classList.toggle('active'); }

    function sendWhatsApp() {
        if(cart.length === 0) return alert("السلة فارغة!");
        let msg = "*طلب جديد من DIMAH Fragrances*\n\n" + cart.map(i => `- ${i.brand} ${i.name} (${i.size}): ${i.price}ج`).join('\n') + `\n\n*الإجمالي النهائي:* ${document.getElementById('total').innerText} ج.م`;
        window.open(`https://wa.me/201102302024?text=${encodeURIComponent(msg)}`);
    }

    render();
</script>

</body>
</html>
