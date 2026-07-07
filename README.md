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

    /* ======================================================= */
    /* 📱 تحديثات الـ Phone View الشاملة لشاشات الموبايل تابت */
    /* ======================================================= */
    @media (max-width: 768px) {
        /* الهيدر: ترتيب العناصر بشكل مريح وتقليص الحجم */
        header {
            padding: 12px 4%;
        }
        .logo-text {
            font-size: 20px; /* تصغير اللوجو ليناسب المساحة */
        }
        .nav-links {
            gap: 10px; /* تقريب الأزرار من بعضها */
        }
        .fb-link {
            padding: 4px 8px;
            font-size: 0.8rem;
        }
        .cart-trigger {
            padding: 4px 10px;
            font-size: 0.85rem;
        }

        /* قسم الـ Hero: تصغير النصوص لكي لا تخرج من الشاشة */
        .hero {
            height: auto;
            padding: 40px 5%;
        }
        .hero h1 {
            font-size: 2rem; /* حجم خط متناسق جداً مع الموبايل */
        }
        .hero p {
            font-size: 0.95rem;
            margin-top: 8px;
        }

        /* خانة البحث والـ Container الرئيسي */
        .search-section {
            margin: -20px auto 30px;
            width: 92%;
        }
        #searchInput {
            padding: 12px 18px;
            font-size: 0.9rem;
        }
        .container {
            padding: 0 4% 40px;
        }

        /* شبكة المنتجات: عرض منتجين جنب بعض أو منتج واحد حسب حجم الموبايل */
        .products-grid {
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); 
            gap: 15px; /* تقليل الفراغات لاستغلال المساحة */
        }
        .p-img {
            height: 220px; /* تقليل ارتفاع الصورة ليناسب الموبايل */
            padding: 10px;
        }
        .card-body {
            padding: 15px; /* تقليل البادينج الداخلي للكارت */
        }
        .name {
            font-size: 1.15rem;
        }
        .price {
            font-size: 1.3rem;
            margin-bottom: 15px;
        }
    }

    /* شاشات الموبايل الصغيرة جداً (أقل من 480px) */
    @media (max-width: 480px) {
        .cart-sidebar { 
            width: 100%; /* السلة تأخذ الشاشة كلها في الموبايل الصغير */
            padding: 20px;
        }
        .hero h1 { 
            font-size: 1.8rem; 
        }
        /* إذا أردت جعل المنتجات تظهر كـ كارت واحد كامل العرض */
        .products-grid {
            grid-template-columns: 1fr;
        }
    }
</style>

       
