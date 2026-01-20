<!DOCTYPE html>
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
        
        /* About Section */
        .about-section {
            padding: 50px 10%; background: #fff; text-align: center; border-bottom: 1px solid #eee;
        }
        .about-section h2 { color: var(--gold); font-size: 2rem; margin-bottom: 15px; }
        .about-section p { max-width: 800px; margin: 0 auto 25px; line-height: 1.8; color: #555; font-size: 1.1rem; }

        .btn-social {
            padding: 12px 25px; border-radius: 50px; text-decoration: none; font-weight: bold;
            display: inline-flex; align-items: center; gap: 10px; transition: 0.3s; color: white;
            background: #1877F2; margin: 5px;
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

        .img-container { width: 100%; height: 230px; background: #fff; display: flex; align-items: center; justify-content: center; }
        .img-container img { max-width: 80%; max-height: 80%; object-fit: contain; }

        .gender-tag { position: absolute; top: 12px; right: 12px; padding: 4px 12px; border-radius: 50px; color: #fff; font-size: 0.7rem; font-weight: bold; z-index: 5; }

        .product-info { padding: 15px; text-align: center; flex-grow: 1; }
        .brand { color: var(--gold); font-size: 0.8rem; font-weight: bold; }
        .name { font-size: 1.1rem; font-weight: bold; margin: 5px 0; height: 2.5em; overflow: hidden; }
        .desc { font-size: 0.75rem; color: #777; margin-bottom: 10px; height: 3em; overflow: hidden; }

        .price-list { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; }
        .price-item { background: #f9f9f9; border: 1px solid #eee; padding: 6px; border-radius: 8px; font-size: 0.7rem; cursor: pointer; text-align: center; }

        .btn-add { background: var(--gold); color: #fff; border: none; width: 100%; padding: 15px; font-weight: bold; cursor: pointer; margin-top: 10px; }

        /* Footer */
        footer { background: var(--dark); color: white; padding: 40px 10%; text-align: center; }
        .footer-contact a { color: var(--gold); text-decoration: none; font-weight: bold; font-size: 1.2rem; }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo">DIMAH fragrances</a>
    <div onclick="toggleCart()" style="cursor:pointer; font-weight:bold;">🛒 السلة (<span id="count">0</span>)</div>
</header>

<section class="about-section">
    <h2>من نحن</h2>
    <p><b>DIMAH Fragrances</b> وجهتكم للتميز. نقدم أرقى الزيوت العطرية العالمية بثبات وفوحان مذهل.</p>
    <a href="https://www.facebook.com/groups/1607807530395013/" target="_blank" class="btn-social">
        <i class="fab fa-facebook"></i> انضم لمجموعتنا
    </a>
</section>

<div style="padding: 20px 5%; text-align: center;">
    <input type="text" id="searchBar" placeholder="ابحث عن اسم العطر..." oninput="render()" style="width:100%; max-width:500px; padding:12px; border-radius:30px; border:1px solid #ddd;">
</div>

<div class="products-grid" id="grid"></div>

<div id="cartSide" style="position:fixed; left:-100%; top:0; width:300px; height:100%; background:white; z-index:2000; transition:0.4s; padding:20px; box-shadow:5px 0 15px rgba(0,0,0,0.1);">
    <h3>سلتك 🛍️</h3>
    <div id="cartItems" style="height:70%; overflow-y:auto;"></div>
    <h4>الإجمالي: <span id="total">0</span> ج.م</h4>
    <button onclick="sendWhatsApp()" style="width:100%; background:#25d366; color:white; padding:12px; border:none; border-radius:8px; font-weight:bold; cursor:pointer;">تأكيد عبر واتساب</button>
    <button onclick="toggleCart()" style="width:100%; background:none; border:none; margin-top:10px; cursor:pointer;">إغلاق</button>
</div>

<footer>
    <p>للمكالمات والاستفسارات:<br> <a href="tel:+201102302024">01102302024</a></p>
    <div style="opacity:0.5; font-size:0.8rem; margin-top:20px;">جميع الحقوق محفوظة © 2026 DIMAH Fragrances</div>
</footer>

<script>
    const perfumes = [
        // الفئة 1 (370ج لـ 50مل)
        { id: 1, b: "Nasomato", n: "Black Afgano", d: "رائحة العود والبخور المدخن.", p: [370, 260, 90, 50], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.6472.jpg" },
        
        // الفئة 2 (320ج لـ 50مل)
        { id: 2, b: "Montale", n: "Arabian Tonica", d: "توابل دافئة وعود عربي.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.44312.jpg" },
        { id: 3, b: "Creed", n: "Creed Aventus", d: "مزيج الأناناس والبتولا الفاخر.", p: [320, 220, 75, 40], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.9828.jpg" },
        { id: 4, b: "Maison Crivelli", n: "Oud Maracuja", d: "العود مع فاكهة الباشن فروت.", p: [320, 220, 75, 40], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.84411.jpg" },

        // الفئة 3 (290ج لـ 50مل)
        { id: 5, b: "Gissa", n: "Imperial Valley", d: "عطر نيش أنيق وجذاب.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.70932.jpg" },
        { id: 6, b: "Arabian Oud", n: "Madawy", d: "فخامة المسك والزهور.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.46338.jpg" },
        { id: 7, b: "Lattafa", n: "Khomra Coffee", d: "قهوة دافئة وكراميل.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.85465.jpg" },
        { id: 8, b: "YSL", n: "Libre", d: "خزامى وزهر برتقال مغربي.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.56671.jpg" },
        { id: 9, b: "Narciso Rodrigues", n: "Poudree", d: "بودرة ناعمة وأنوثة طاغية.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.36351.jpg" },
        { id: 10, b: "ELIE SAAB", n: "Elie Saab EDP", d: "ياسمين وعسل نحل صافي.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.12258.jpg" },
        { id: 11, b: "Tom Ford", n: "Black Orchid", d: "أوركيد وتوابل غامضة.", p: [290, 200, 70, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.1018.jpg" },
        { id: 12, b: "Victor & Rolf", n: "Spice Bomb Extreme", d: "انفجار توابل وتبغ.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.30443.jpg" },
        { id: 13, b: "Burberry", n: "Burberry Her", d: "توت أحمر وزهور منعشة.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.51691.jpg" },
        { id: 14, b: "Victoria Secret", n: "Love is Heavenly", d: "رقة الزهور والمسك الأبيض.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.37684.jpg" },
        { id: 15, b: "Victoria Secret", n: "Very Sexy Now", d: "جوز هند وعبير استوائي.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.30571.jpg" },
        { id: 16, b: "Victoria Secret", n: "Bomb Chill", d: "انتعاش كمثرى وزهور.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.63853.jpg" },
        { id: 17, b: "Carolina Herrera", n: "Good Girl", d: "كاكاو وتونكا جذابة.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.39688.jpg" },
        { id: 18, b: "Jean Paul Gaultier", n: "Le Male Elixir", d: "عسل ولافندر ومركّز.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.81643.jpg" },
        { id: 19, b: "Chanel", n: "Bleu de Chanel", d: "نظافة وجمال الأخشاب.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.25967.jpg" },
        { id: 20, b: "Kayali", n: "Vanilla 28", d: "سكر فانيليا صافي.", p: [290, 200, 70, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.52643.jpg" },
        { id: 21, b: "Emporio Armani", n: "Stronger With You", d: "كستناء وتوابل دافئة.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.45258.jpg" },
        { id: 22, b: "Paco Rabanne", n: "Invictus Victory Elixir", d: "بخور وفانيليا للانتصار.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.78848.jpg" },
        { id: 23, b: "Paco Rabanne", n: "One Million EDP", d: "قوة الجلد والقرفة.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.61633.jpg" },
        { id: 24, b: "Dior", n: "Sauvage EDP", d: "جاذبية ذكورية منعشة.", p: [290, 200, 70, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.49144.jpg" },

        // الفئة 4 (275ج لـ 50مل)
        { id: 25, b: "Roberto Cavalli", n: "Paradiso", d: "حمضيات وزهور صيفية.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.29381.jpg" },
        { id: 26, b: "Giorgio Armani", n: "Acqua Di Gio", d: "نسيم البحر والليمون.", p: [275, 190, 65, 35], g: "Male", gl: "رجالي", img: "https://fimgs.net/mdimg/perfume/m.342.jpg" },
        { id: 27, b: "Lattafa", n: "Yara", d: "فراولة ومارشميلو ناعم.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://lattafa.com/wp-content/uploads/2021/04/Yara-100ml.jpg" },
        { id: 28, b: "Lattafa", n: "Yara Candy", d: "حلاوة فواكه سكرية.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.93774.jpg" },
        { id: 29, b: "Paco Rabanne", n: "Olympia", d: "فانيليا مملحة فريدة.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.31666.jpg" },
        { id: 30, b: "Carolina Herrera", n: "212 Sexy", d: "جاذبية وإثارة شرقية.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.611.jpg" },
        { id: 31, b: "Billie Eilish", n: "Eilish", d: "فانيليا كاكاو دافئة.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.70275.jpg" },
        { id: 32, b: "Mancera", n: "Bianko Latte", d: "حليب وكراميل وعسل.", p: [275, 190, 65, 35], g: "Unisex", gl: "للجنسين", img: "https://fimgs.net/mdimg/perfume/m.80665.jpg" },
        { id: 33, b: "Britney Spears", n: "Fantasy", d: "حلويات وفواكه شهية.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.600.jpg" },
        { id: 34, b: "Aquolina", n: "Pink Sugar", d: "غزل بنات وسكر.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.977.jpg" },
        { id: 35, b: "Giorgio Armani", n: "My Way", d: "زهور بيضاء ومسك.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.62030.jpg" },
        { id: 36, b: "Lancome", n: "La Vie Est Belle", d: "حياة جميلة بعبير السوسن.", p: [275, 190, 65, 35], g: "Female", gl: "حريمي", img: "https://fimgs.net/mdimg/perfume/m.14982.jpg" }
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
                        <button class="btn-add" onclick="addToCart(${p.id})">إضافة للسلة</button>
                    </div>
                </div>`;
        });
    }

    function addToCart(id) {
        const item = perfumes.find(p => p.id === id);
        const sizeIdx = document.querySelector(`input[name="s-${id}"]:checked`).value;
        const sizes = ["50ml", "30ml", "10ml", "5ml"];
        cart.push({ n: item.n, b: item.b, s: sizes[sizeIdx], pr: item.p[sizeIdx] });
        updateCart();
        document.getElementById('cartSide').style.left = "0";
    }

    function updateCart() {
        document.getElementById('count').innerText = cart.length;
        const list = document.getElementById('cartItems');
        let total = 0;
        list.innerHTML = cart.map((i, idx) => {
            total += i.pr;
            return `<div style="padding:10px; border-bottom:1px solid #eee;">
                <b>${i.b} ${i.n}</b> (${i.s})<br>${i.pr} ج.م
                <span onclick="cart.splice(${idx},1);updateCart()" style="color:red; cursor:pointer; float:left;">حذف</span>
            </div>`;
        }).join('');
        document.getElementById('total').innerText = total;
    }

    function toggleCart() {
        const side = document.getElementById('cartSide');
        side.style.left = side.style.left === "0px" ? "-100%" : "0";
    }

    function sendWhatsApp() {
        if(cart.length === 0) return alert("السلة فارغة");
        let msg = "طلب جديد DIMAH:\n" + cart.map(i => `- ${i.b} ${i.n} (${i.s}): ${i.pr}ج`).join('\n') + `\nالإجمالي: ${document.getElementById('total').innerText}ج`;
        window.open(`https://wa.me/201102302024?text=${encodeURIComponent(msg)}`);
    }

    render();
</script>
</body>
</html>

