<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dimah Fragrances | ديمة للعطور</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;700&family=Playfair+Display:ital,wght=0,700;1,700&display=swap" rel="stylesheet">
    <style>
        /* الهوية البصرية: أبيض، ذهبي، ولمسات سوداء */
        :root { 
            --gold: #d4af37; 
            --gold-dark: #aa841b;
            --bg-main: #ffffff; 
            --card-bg: #ffffff; 
            --text-dark: #111111; 
            --text-muted: #666666;
            --black-accent: #000000;
        }
        
        body { 
            font-family: 'Cairo', sans-serif; 
            background-color: var(--bg-main); 
            color: var(--text-dark); 
            margin: 0; 
            padding: 0; 
            line-height: 1.6; 
        }
        
        /* الهيدر */
        header { 
            background-color: var(--black-accent); 
            padding: 15px 5%; 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            border-bottom: 3px solid var(--gold); 
            position: sticky; 
            top: 0; 
            z-index: 1000; 
        }
        .logo-text { font-family: 'Playfair Display', serif; font-size: 26px; color: var(--gold); text-decoration: none; font-weight: bold; letter-spacing: 2px; }
        .nav-links { display: flex; align-items: center; gap: 20px; }
        .fb-link { color: #ffffff; text-decoration: none; font-size: 0.95rem; display: flex; align-items: center; gap: 5px; transition: 0.3s; border: 1px solid #333; padding: 5px 12px; border-radius: 4px; }
        .fb-link:hover { border-color: var(--gold); color: var(--gold); }
        .cart-trigger { cursor: pointer; color: var(--gold); font-weight: bold; background: #111; padding: 5px 15px; border-radius: 4px; border: 1px solid var(--gold); }
        
        /* قسم العرض الرئيسي */
        .hero { 
            height: 35vh; 
            background: linear-gradient(rgba(255,255,255,0.9), rgba(255,255,255,0.95)), 
                        url('https://images.unsplash.com/photo-1592945403244-b3fbafd7f539?q=80&w=1000') center/cover no-repeat; 
            display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 0 10%;
            border-bottom: 1px solid #eaeaea;
        }
        .hero h1 { font-family: 'Playfair Display', serif; font-size: 3.5rem; margin: 0; color: var(--black-accent); font-weight: 700; }
        .hero p { font-size: 1.2rem; max-width: 700px; margin-top: 10px; color: var(--text-muted); }

        /* البحث */
        .search-section { margin: -30px auto 40px; width: 90%; max-width: 600px; position: relative; z-index: 10; }
        #searchInput { width: 100%; padding: 15px 25px; border-radius: 8px; border: 2px solid var(--black-accent); background: #ffffff; color: #000; outline: none; box-shadow: 0 10px 25px rgba(0,0,0,0.05); font-family: 'Cairo'; font-size: 1rem; }
        #searchInput:focus { border-color: var(--gold); }

        /* شبكة المنتجات */
        .container { padding: 0 5% 50px; }
        .products-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .product-card { background: var(--card-bg); border-radius: 4px; overflow: hidden; box-shadow: 0 4px 20px rgba(0,0,0,0.05); border: 1px solid #eee; transition: 0.4s; display: flex; flex-direction: column; }
        .product-card:hover { transform: translateY(-5px); box-shadow: 0 12px 30px rgba(0,0,0,0.1); border-color: var(--gold); }
        
        /* ضبط وتوسيط صور الزجاجات الأصلية بشكل احترافي */
        .p-img { height: 300px; background: #ffffff; display: flex; align-items: center; justify-content: center; padding: 20px; overflow: hidden; border-bottom: 1px solid #f5f5f5; }
        .p-img img { max-width: 100%; max-height: 100%; object-fit: contain; transition: 0.5s; }
        .product-card:hover .p-img img { transform: scale(1.05); }

        .card-body { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
        .tag { font-size: 0.75rem; color: #fff; background: var(--black-accent); padding: 2px 12px; border-radius: 2px; align-self: flex-start; margin-bottom: 12px; font-weight: bold; }
        .brand { font-size: 0.85rem; color: var(--gold-dark); text-transform: uppercase; font-weight: 700; }
        .name { font-size: 1.4rem; margin: 3px 0 12px 0; font-weight: 700; color: var(--black-accent); }
        
        /* خانة المكونات */
        .notes-box { background: #fafafa; border-right: 3px solid var(--gold); padding: 10px 12px; margin-bottom: 15px; border-radius: 2px; font-size: 0.85rem; color: #444; }

        select { background: #ffffff; color: var(--text-dark); border: 1px solid #ccc; padding: 12px; width: 100%; border-radius: 4px; margin-bottom: 15px; font-family: 'Cairo'; cursor: pointer; font-size: 0.95rem; }
        select:focus { border-color: var(--gold); }
        .price { font-size: 1.6rem; color: var(--black-accent); font-weight: bold; margin-bottom: 20px; border-bottom: 1px dashed #eee; padding-bottom: 10px; }
        
        .buy-btn { background: var(--black-accent); color: #fff; border: 1px solid var(--black-accent); padding: 14px; font-weight: bold; border-radius: 4px; cursor: pointer; transition: 0.3s; width: 100%; font-family: 'Cairo'; font-size: 1rem; }
        .buy-btn:hover { background: var(--gold); color: #fff; border-color: var(--gold); }

        /* السلة */
        .cart-sidebar { position: fixed; top: 0; left: -100%; width: 400px; height: 100%; background: #ffffff; z-index: 2000; transition: 0.5s; padding: 30px; box-sizing: border-box; box-shadow: 10px 0 30px rgba(0,0,0,0.1); border-right: 3px solid var(--gold); }
        .cart-sidebar.active { left: 0; }
        .cart-item { border-bottom: 1px solid #eee; padding: 15px 0; display: flex; justify-content: space-between; align-items: center; }

        .wa-order { background: #25d366; color: white; text-align: center; padding: 15px; border-radius: 4px; text-decoration: none; display: block; font-weight: bold; margin-top: 20px; font-size: 1.1rem; }
        
        footer { background: var(--black-accent); text-align: center; padding: 35px; color: #888; border-top: 3px solid var(--gold); }
        footer a { color: var(--gold); text-decoration: none; font-weight: bold; }

        @media (max-width: 480px) { .cart-sidebar { width: 100%; } .hero h1 { font-size: 2.2rem; } }
    </style>
</head>
<body>

    <header>
        <div class="logo-text">DIMAH FRAGRANCES</div>
        <div class="nav-links">
            <a href="https://www.facebook.com/share/12E8LwV2vG/" target="_blank" class="fb-link">🔵 Facebook</a>
            <div onclick="toggleCart()" class="cart-trigger">🛒 السلة (<span id="count">0</span>)</div>
        </div>
    </header>

    <section class="hero">
        <h1>DIMAH FRAGRANCES</h1>
        <p>مجموعتنا المحددة والفاخرة المستوحاة من أرقى الزجاجات العطرية العالمية وبأعلى ثبات وجودة.</p>
    </section>

    <div class="search-section">
        <input type="text" id="searchInput" placeholder="ابحث عن العطر المفضل لديك..." onkeyup="search()">
    </div>

    <div class="container">
        <div class="products-grid" id="grid"></div>
    </div>

    <div class="cart-sidebar" id="cart">
        <div style="display:flex; justify-content:space-between; align-items:center; border-bottom: 2px solid var(--black-accent); padding-bottom:15px;">
            <h2 style="margin:0; color:var(--black-accent); font-weight: 700;">حقيبة التسوق</h2>
            <span onclick="toggleCart()" style="cursor:pointer; font-size:24px; color: var(--text-muted);">✕</span>
        </div>
        <div id="items" style="height: calc(100% - 200px); overflow-y:auto;"></div>
        <div style="padding-top:20px;">
            <div style="display:flex; justify-content:space-between; font-size:1.4rem; font-weight:bold; border-top: 1px solid #eee; padding-top: 15px;">
                <span>الإجمالي:</span>
                <span id="total" style="color:var(--gold-dark);">0 ج.م</span>
            </div>
            <a href="#" class="wa-order" onclick="sendOrder()">تأكيد الطلب عبر واتساب 💬</a>
        </div>
    </div>

    <footer>
        <p style="margin: 0; color: #fff;">جميع الحقوق محفوظة © 2026 لـ DIMAH FRAGRANCES</p>
        <p style="margin: 5px 0 0 0;">تابعنا عبر <a href="https://www.facebook.com/share/12E8LwV2vG/" target="_blank">Facebook</a></p>
    </footer>

    <script>
        // مصفوفة المنتجات الحصرية والمعتمدة من طرفك فقط
        const data = [
            // القائمة الرجالية المعتمدة (4 أنواع فقط)
            { id: 1, brand: "Paco Rabanne", name: "Invictus Victory Elixir", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Male", img: " https://fimgs.net/mdimg/perfume-thumbs/375x500.78575.jpg   ", notes: "العنبر الغني، اللابدانوم، الفانيليا الدافئة، الليمون المنعش، البخور الغامض" },
            { id: 2, brand: "Emporio Armani", name: "Stronger With You", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Male", img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSEybC-4O58bIE9IwVHi-sCEB7XhyIheFusoz7A2C3ojw&s=10   ", notes: "الكستناء (أبو فروة)، الكراميل، الفانيليا، القرفة، الميرمية، الفلفل الوردي" },
            { id: 3, brand: "Xerjoff", name: "Erba Pura", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Unisex", img: " https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcREzE7GrDJq3pj5i5MOL9kFJh8iNkNX2Dejk2ebaQQJuYdDakr-zk_gfnSV&s=10  ", notes: "البرغموت الصقلي، البرتقال، الليمون، الفواكه الاستوائية الحلوة، المسك الأبيض، العنبر، الفانيليا" },
            { id: 4, brand: "Creed", name: "Creed Aventus", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Male", img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRJNGyjs-FpvS8sM0YUGvwewodQlRGhAIuk3lNI0i5Ugw&s=10  ", notes: "الأناناس، الكشمش الأسود، التفاح، الأخشاب، الياسمين، المسك، الفانيليا الفاخرة" },
            
            // القائمة الحريمية بالكامل من المجموعة الأصلية
            { id: 5, brand: "Lancôme", name: "Idôle EDP", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img:"https://www.faces.eg/dw/image/v2/BJSM_PRD/on/demandware.static/-/Sites-faces-master-catalog/default/dwd3c534a1/images/019315158131_1.jpg?sw=800&sh=800       ", notes: "الورد التركي، ورد دي ماي، الياسمين الهندي، الكمثرى المقرمشة، البرغموت، المسك الأبيض اللطيف" },
            { id: 6, brand: "Yves Saint Laurent", name: "Libre", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "  https://m.media-amazon.com/images/I/718V2iBFBkL.jpg  ", notes: "اللافندر (الخزامى)، الماندارين، زهر البرتقال، الياسمين، فانيليا مدغشقر، المسك" },
            { id: 7, brand: "Narciso Rodrigues", name: "Narciso Poudree", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSy96G8sO4PANZPHbtk1LjCcKwA6oyT1e_iDLQzvXZwse01ql_QcosRUFmp&s=10  ", notes: "النوتات البودرية الناعمة، الياسمين، الورد الأبيض، المسك، خشب الأرز" },
            { id: 8, brand: "ELIE SAAB", name: "Elie Saab EDP", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img:"https://www.truperfumes.com.au/cdn/shop/files/Le_Parfum_Elie_Saab_50ml_EDP_for_Women_by_Elie_Saab.jpg?v=1759900325", notes: "زهر البرتقال الأفريقي، الياسمين النقي، عسل الأبيض، الباتشولي، الورد" },
            { id: 9, brand: "Burberry", name: "Burberry Her", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://www.faces.eg/dw/image/v2/BJSM_PRD/on/demandware.static/-/Sites-faces-master-catalog/default/dw859d3013/images/005217610758_7.jpg?sw=800&sh=800", notes: "الفراولة، التوت الأسود، الكرز، الياسمين، البنفسج، العنبر، الأخشاب، المسك" },
            { id: 10, brand: "Victoria Secret", name: "Love is Heavenly", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://images-na.ssl-images-amazon.com/images/I/41bxM8aJSdL._SL500_._AC_SL500_.jpg", notes: "زهر التوت، الكيوي، زنبق الماء، الفريزيا، المسك، خشب الصندل" },
            { id: 11, brand: "Victoria Secret", name: "Very Sexy Now", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://cdn.salla.sa/ypRXO/MRMmmZ5k2lsutF2megniwEqYVqfdcozcU7WmbRj6.jpg", notes: "جوز الهند الاستوائي، الفواكه الاستوائية، الجوافة، اللوتس، الأخشاب الدافئة" },
            { id: 12, brand: "Victoria Secret", name: "Bomb Chill", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://www.myperfumeshop.bh/cdn/shop/files/Spicebomb-infrared-eau-de-parfum-viktor-rolf.webp?v=1707119464&width=1500", notes: "الكمثرى المثلجة، زهور الفاوانيا الشتوية، الأخشاب النظيفة، إحساس منعش" },
            { id: 13, brand: "Carolina Herrera", name: "Good Girl", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/cXYAAeSwCDpqRUp0/s-l960.jpg", notes: "اللوز، القهوة، الياسمين، التونكا، الكاكاو، الفانيليا، خشب الصندل" },
            { id: 14, brand: "Kayali", name: "Kayali Vanilla 28", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img:"https://i.ebayimg.com/images/g/hTcAAOSwNt9n4LYQ/s-l960.jpg" , notes: "أوركيد الفانيليا، الياسمين، السكر البني، خشب التونكا، المسك، العنبر" },
            { id: 15, brand: "Roberto Cavalli", name: "Roberto Cavalli EDP", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSko-uZfIizyvRlOZsSlXWEGyTQ6DLIqhZEWiNoyBYFFik9ClUXSfRRTZO0&s=10", notes: "الفلفل الوردي، زهر البرتقال الأفريقي، الفانيليا، الجاوي، التونكا" },
            { id: 16, brand: "Lattafa", name: "Yara", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: 'https://m.media-amazon.com/images/I/71FXvCbczdL._AC_UF350,350_QL80_.jpg', notes: "الأوركيد، الفواكه الاستوائية، الفانيليا، السكاكر، خشب الصندل، المسك" },
            { id: 17, brand: "Lattafa", name: "Yara Candy", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/T4EAAeSwQWtpaUkb/s-l960.jpg", notes: "الحلوى السكرية، الفراولة، المانجو، الكومثرى، الفانيليا الناعمة، المسك" },
            { id: 18, brand: "Paco Rabanne", name: "Olympia", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/jYkAAeSwuxZqI0PV/s-l960.jpg", notes: "الفانيليا المالحة، الياسمين المائي، الماندارين الأخضر، زهر الزنجبيل، الكشمير" },
            { id: 19, brand: "Carolina Herrera", name: "212 Sexy", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/aRkAAOSwsFZd-7RB/s-l960.jpg", notes: "الفلفل الوردي، الماندارين، غزل البنات، الجاردينيا، الفانيليا، خشب الصندل" },
            { id: 20, brand: "Billie Eilish", name: "Eilish Eilish", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://zacshop.com/cdn/shop/files/L1914048.jpg?v=1739190599", notes: "السكر، الكاكاو، الفانيليا، التوت الأحمر.. توليفة ساحرة" },
            { id: 21, brand: "Britney Spears", name: "Fantasy Britney", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://fathyibrahim.com/cdn/shop/files/Fantasy-by-Britney-Spears-for-Women-Eau-de-Parfum-100ml-2.jpg?v=1742213084&width=900", notes: "الكيوي، الليتشي، الشوكولاتة البيضاء، الكب كيك، الأوركيد، الياسمين" },
            { id: 22, brand: "Aquolina", name: "Pink Sugar", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/~YUAAeSwWhto9Yrp/s-l960.jpg", notes: "غزل البنات، التوت الأحمر، العرقسوس، الفراولة، الكراميل، الفانيليا" },
            { id: 23, brand: "Giorgio Armani", name: "My Way EDP", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://www.lojaglamourosa.com/resources/medias/shop/products/thumbnails/shop-brand-large/shop-pf-03531-03-my-way-le-parfum---90ml--1.jpg", notes: "زهر البرتقال، البرغموت، مسك الروم، الياسمين الهندي، فانيليا بوربون" },
            { id: 24, brand: "Lancome", name: "La Vie Est Belle", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://i.ebayimg.com/images/g/9VIAAeSw431phvFp/s-l1600.jpg", notes: "الكشمش الأسود، الكمثرى، زهر البرتقال، الياسمين، حلويات البخاخ، التونكا" },
            { id: 25, brand: "Bath & Body Works", name: "Japanese Cherry Blossom", p: { "30ml": 210, "50ml": 300, "10ml": 70 }, g: "Female", img: "https://f.nooncdn.com/p/v1638883312/N51944748A_2.jpg?width=480", notes: "أزهار الكرز اليابانية، الأرز، الميموزا، زهر البتلة، خشب الصندل، العنبر" }
        ];

        let cartArr = [];

        function render() {
            const grid = document.getElementById('grid');
            grid.innerHTML = data.map(item => `
                <div class="product-card">
                    <div class="p-img"><img src="${item.img}" alt="${item.name}"></div>
                    <div class="card-body">
                        <span class="tag">${item.g === 'Male' ? 'FOR HIM' : item.g === 'Female' ? 'FOR HER' : 'UNISEX'}</span>
                        <div class="brand">${item.brand}</div>
                        <div class="name">${item.name}</div>
                        
                        <div class="notes-box"><b>المكونات العطرية:</b> ${item.notes}</div>

                        <select id="size-${item.id}" onchange="updatePrice(${item.id})">
                            <option value="30ml" selected>30 مل - ${item.p['30ml']} ج.م</option>
                            <option value="50ml">50 مل - ${item.p['50ml']} ج.م</option>
                            <option value="10ml">10 مل - ${item.p['10ml']} ج.م</option>
                        </select>
                        <div class="price" id="pr-${item.id}">${item.p['30ml']} ج.م</div>
                        <button class="buy-btn" onclick="add(${item.id})">إضافة إلى حقيبة التسوق 🛒</button>
                    </div>
                </div>
            `).join('');
        }

        function updatePrice(id) {
            const size = document.getElementById(`size-${id}`).value;
            const item = data.find(x => x.id === id);
            document.getElementById(`pr-${id}`).innerText = item.p[size] + " ج.م";
        }

        function toggleCart() { document.getElementById('cart').classList.toggle('active'); }

        function add(id) {
            const size = document.getElementById(`size-${id}`).value;
            const item = data.find(x => x.id === id);
            cartArr.push({ name: item.name, size: size, price: item.p[size] });
            updateCart();
            if(!document.getElementById('cart').classList.contains('active')) toggleCart();
        }

        function updateCart() {
            document.getElementById('count').innerText = cartArr.length;
            const itemsDiv = document.getElementById('items');
            itemsDiv.innerHTML = cartArr.map((x, i) => `
                <div class="cart-item">
                    <div><b>${x.name}</b><br><small>${x.size}</small></div>
                    <div>${x.price} ج.م <span onclick="cartArr.splice(${i},1);updateCart()" style="color:red;cursor:pointer;margin-right:10px;">✕</span></div>
                </div>
            `).join('');
            const total = cartArr.reduce((a, b) => a + b.price, 0);
            document.getElementById('total').innerText = total + " ج.م";
        }

        function sendOrder() {
            if(cartArr.length === 0) return alert('السلة فارغة');
            let text = "طلب جديد من DIMAH:\n\n";
            cartArr.forEach((x, i) => text += `${i+1}. ${x.name} (${x.size}) - ${x.price} ج.م\n`);
            text += `\nالإجمالي: ${document.getElementById('total').innerText}`;
            window.open(`https://wa.me/201102302024?text=${encodeURIComponent(text)}`);
        }

        function search() {
            const q = document.getElementById('searchInput').value.toLowerCase();
            document.querySelectorAll('.product-card').forEach(card => {
                card.style.display = card.innerText.toLowerCase().includes(q) ? 'flex' : 'none';
            });
        }

        render();
    </script>
</body>
</html>

