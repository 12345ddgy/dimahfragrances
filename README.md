
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
            --wa-green: #25d366;
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

        .btn-add { background: var(--gold); color: #fff; border: none; width: 100%; padding: 15px; font-weight: bold; cursor: pointer; margin-top: 10px; border-radius: 0 0 20px 20px; }

        /* Sidebar Cart */
        #cartSide {
            position: fixed; left: -100%; top: 0; width: 320px; height: 100%;
            background: #fff; z-index: 2000; transition: 0.4s; padding: 25px;
            box-shadow: 10px 0 30px rgba(0,0,0,0.1);
        }
        #cartSide.active { left: 0; }

        /* Footer & Social Buttons */
        footer { background: var(--dark); color: white; padding: 60px 10%; text-align: center; margin-top: 50px; }
        
        .footer-social-container {
            display: flex; justify-content: center; gap: 20px; margin: 25px 0; flex-wrap: wrap;
        }
        .footer-btn {
            display: flex; align-items: center; gap: 10px; padding: 15px 30px;
            border-radius: 50px; text-decoration: none; color: white; font-weight: bold;
            transition: 0.3s; font-size: 1rem;
        }
        .footer-btn.fb { background: var(--fb-blue); }
        .footer-btn.wa { background: var(--wa-green); }
        .footer-btn:hover { transform: translateY(-5px); box-shadow: 0 10px 20px rgba(0,0,0,0.3); }

        .footer-contact-info { font-size: 1.2rem; margin: 15px 0; }
        .footer-contact-info a { color: var(--gold); text-decoration: none; font-weight: bold; }
        .rights { margin-top: 30px; font-size: 0.85rem; opacity: 0.5; border-top: 1px solid #333; padding-top: 25px; }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo">DIMAH fragrances</a>
    <div class="cart-status" onclick="toggleCart()">🛒 السلة (<span id="count">0</span>)</div>
</header>

<section class="about-section">
    <h2>من نحن</h2>
    <p><b>DIMAH Fragrances</b> وجهتكم المفضلة لأرقى العطور المستوحاة عالمياً. نضمن لكم الجودة، الثبات، والفوحان في كل قطرة.</p>
</section>

<div class="search-area">
    <input type="text" id="searchBar" placeholder="ابحث عن اسم العطر أو الماركة..." oninput="render()">
</div>

<div class="products-grid" id="grid"></div>

<div id="cartSide">
    <h3>سلة الطلبات 🛍️</h3>
    <div id="cartItems" style="height:65%; overflow-y:auto; margin:15px 0;"></div>
    <div style="border-top: 2px solid #eee; padding-top: 15px;">
        <h4 style="margin-bottom: 15px;">الإجمالي: <span id="total">0</span> ج.م</h4>
        <button onclick="sendWhatsApp()" style="width:100%; background:var(--wa-green); color:white; padding:15px; border:none; border-radius:12px; font-weight:bold; cursor:pointer; font-size: 1rem;">
            تأكيد الطلب عبر واتساب
        </button>
        <button onclick="toggleCart()" style="width:100%; background:none; border:none; margin-top:15px; cursor:pointer; color:#999;">رجوع للمتجر</button>
    </div>
</div>

<footer>
    <div style="color: var(--gold); font-size: 1.8rem; font-weight: bold; margin-bottom: 10px;">DIMAH</div>
    <p>تواصل معنا مباشرة عبر القنوات التالية:</p>
    
    <div class="footer-social-container">
        <a href="https://www.facebook.com/groups/1607807530395013/" target="_blank" class="footer-btn fb">
            <i class="fab fa-facebook-f"></i> جروب الفيسبوك
        </a>
        <a href="https://wa.me/201102302024" target="_blank" class="footer-btn wa">
            <i class="fab fa-whatsapp"></i> تواصل عبر واتساب
        </a>
    </div>

    <div class="footer-contact-info">
        للمكالمات والاستفسارات: <br>
        <a href="tel:+201102302024">01102302024</a>
    </div>

    <div class="rights">
        جميع الحقوق محفوظة © 2026 لـ ديمة للعطور - DIMAH Fragrances
    </div>
</footer>

<script>
    // مصفوفة الـ 36 عطراً بالكامل مع الصور والوصف
    const perfumes = [
        { id: 1, b: "Nasomato", n: "Black Afgano", d: "رائحة العود والبخور المدخن للقوة والغموض.", p: [370, 260, 90, 50], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.6472.jpg" },
        { id: 2, b: "Montale", n: "Arabian Tonica", d: "مزيج دافئ من التوابل والعود العربي الأصيل.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.44312.jpg" },
        { id: 3, b: "Creed", n: "Creed Aventus", d: "ملك العطور، يجمع بين القوة والانتعاش.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.9828.jpg" },
        { id: 4, b: "Maison Crivelli", n: "Oud Maracuja", d: "تناقض مذهل بين العود وفاكهة الباشن فروت.", p: [320, 220, 75, 40], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.84411.jpg" },
        { id: 5, b: "Gissa", n: "Imperial Valley", d: "عطر نيش فخم يجمع بين الأناقة والجاذبية.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.70932.jpg" },
        { id: 6, b: "Arabian Oud", n: "Madawy", d: "عطر يجسد الفخامة العربية بلمسات فرنسية راقية.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.46338.jpg" },
        { id: 7, b: "Lattafa", n: "Khomra Coffee", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", d: "رائحة دافئة من القهوة والكراميل.", img: "https://fimgs.net/mdimg/perfume/m.85465.jpg" },
        { id: 8, b: "YSL", n: "Libre", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "مزيج من الخزامى وزهر البرتقال.", img: "https://fimgs.net/mdimg/perfume/m.56671.jpg" },
        { id: 9, b: "Narciso Rodrigues", n: "Poudree", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "عطر بودري ناعم يفيض بالأنوثة.", img: "https://fimgs.net/mdimg/perfume/m.36351.jpg" },
        { id: 10, b: "ELIE SAAB", n: "Elie Saab EDP", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "أناقة زهور الياسمين والعسل.", img: "https://fimgs.net/mdimg/perfume/m.12258.jpg" },
        { id: 11, b: "Tom Ford", n: "Black Orchid", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", d: "عطر فاخر يجمع بين الأوركيد والتوابل.", img: "https://fimgs.net/mdimg/perfume/m.1018.jpg" },
        { id: 12, b: "Victor & Rolf", n: "Spice Bomb Extreme", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "قنبلة من التوابل والتبغ والفانيليا.", img: "https://fimgs.net/mdimg/perfume/m.30443.jpg" },
        { id: 13, b: "Burberry", n: "Burberry Her", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "رائحة الفواكه الحمراء المنعشة والناعمة.", img: "https://fimgs.net/mdimg/perfume/m.51691.jpg" },
        { id: 14, b: "Victoria Secret", n: "Love is Heavenly", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "عطر رومانسي هادئ وحالم.", img: "https://fimgs.net/mdimg/perfume/m.37684.jpg" },
        { id: 15, b: "Victoria Secret", n: "Very Sexy Now", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "عطر استوائي صيفي بامتياز.", img: "https://fimgs.net/mdimg/perfume/m.30571.jpg" },
        { id: 16, b: "Victoria Secret", n: "Bomb Chill", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "انتعاش الزهور الباردة الفاخرة.", img: "https://fimgs.net/mdimg/perfume/m.63853.jpg" },
        { id: 17, b: "Carolina Herrera", n: "Good Girl", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "عطر جذاب يجمع بين الكاكاو والتونكا.", img: "https://fimgs.net/mdimg/perfume/m.39688.jpg" },
        { id: 18, b: "Jean Paul Gaultier", n: "Le Male Elixir", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "جاذبية الفانيليا والنعناع المركزة.", img: "https://fimgs.net/mdimg/perfume/m.81643.jpg" },
        { id: 19, b: "Chanel", n: "Bleu de Chanel", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "نظافة وانتعاش الأخشاب والحمضيات.", img: "https://fimgs.net/mdimg/perfume/m.25967.jpg" },
        { id: 20, b: "Kayali", n: "Vanilla 28", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", d: "رائحة الفانيليا الصافية والدافئة.", img: "https://fimgs.net/mdimg/perfume/m.52643.jpg" },
        { id: 21, b: "Emporio Armani", n: "Stronger With You", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "عطر دافئ برائحة الكستناء المسكرة.", img: "https://fimgs.net/mdimg/perfume/m.45258.jpg" },
        { id: 22, b: "Paco Rabanne", n: "Invictus Victory Elixir", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "قوة البخور والفانيليا المركزة.", img: "https://fimgs.net/mdimg/perfume/m.78848.jpg" },
        { id: 23, b: "Paco Rabanne", n: "One Million EDP", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "فخامة الذهب بلمسات القرفة والجلد.", img: "https://fimgs.net/mdimg/perfume/m.61633.jpg" },
        { id: 24, b: "Dior", n: "Sauvage EDP", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", d: "عطر كاريزمي ومنعش للرجل العصري.", img: "https://fimgs.net/mdimg/perfume/m.49144.jpg" },
        { id: 25, b: "Roberto Cavalli", n: "Paradiso", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "رحلة إلى شواطئ إيطاليا الساحرة.", img: "https://fimgs.net/mdimg/perfume/m.29381.jpg" },
        { id: 26, b: "Giorgio Armani", n: "Acqua Di Gio", p: [275, 190, 65, 35], g: "Male", gl: "رجالي", d: "انتعاش مياه البحر والليمون الصافي.", img: "https://fimgs.net/mdimg/perfume/m.342.jpg" },
        { id: 27, b: "Lattafa", n: "Yara", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "عطر وردي برائحة الفراولة والمارشميلو.", img: "https://lattafa.com/wp-content/uploads/2021/04/Yara-100ml.jpg" },
        { id: 28, b: "Lattafa", n: "Yara Candy", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "انفجار من السكاكر والفواكه الاستوائية.", img: "https://fimgs.net/mdimg/perfume/m.93774.jpg" },
        { id: 29, b: "Paco Rabanne", n: "Olympia", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "مزيج فريد من الياسمين والفانيليا المملحة.", img: "https://fimgs.net/mdimg/perfume/m.31666.jpg" },
        { id: 30, b: "Carolina Herrera", n: "212 Sexy", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "جاذبية لا تقاوم بلمسات الفلفل الوردي.", img: "https://fimgs.net/mdimg/perfume/m.611.jpg" },
        { id: 31, b: "Billie Eilish", n: "Eilish", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "فانيليا كاكاو دافئة ومميزة جداً.", img: "https://fimgs.net/mdimg/perfume/m.70275.jpg" },
        { id: 32, b: "Mancera", n: "Bianko Latte", p: [275, 190, 65, 35], g: "Unisex", gl: "للجنسين", d: "رائحة الحليب والعسل والفانيليا الدسمة.", img: "https://fimgs.net/mdimg/perfume/m.80665.jpg" },
        { id: 33, b: "Britney Spears", n: "Fantasy", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "عطر الفواكه والحلويات الشهير واللطيف.", img: "https://fimgs.net/mdimg/perfume/m.600.jpg" },
        { id: 34, b: "Aquolina", n: "Pink Sugar", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "عطر طفولي برائحة غزل البنات والكراميل.", img: "https://fimgs.net/mdimg/perfume/m.977.jpg" },
        { id: 35, b: "Giorgio Armani", n: "My Way", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "رحلة بين زهور مسك الروم والبرغموت.", img: "https://fimgs.net/mdimg/perfume/m.62030.jpg" },
        { id: 36, b: "Lancome", n: "La Vie Est Belle", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", d: "عطر السعادة، مزيج السوسن والحلويات الفاخر.", img: "https://fimgs.net/mdimg/perfume/m.14982.jpg" }
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
