/* ======================================================= */
    /* 📱 تحديثات الـ Phone View لجعل الموقع "Fit" تماماً */
    /* ======================================================= */
    @media (max-width: 768px) {
        /* الهيدر: احتواء كامل بدون خروج */
        header {
            padding: 10px 4%;
            box-sizing: border-box; /* تضمن أن البادينج لا يزود حجم الهيدر */
        }
        .logo-text {
            font-size: 18px; 
        }
        .nav-links {
            gap: 8px; 
        }
        .fb-link {
            padding: 4px 6px;
            font-size: 0.75rem;
        }
        .cart-trigger {
            padding: 4px 8px;
            font-size: 0.8rem;
        }

        /* الـ Hero: متناسق ومضغوط */
        .hero {
            height: auto;
            padding: 30px 4%;
            box-sizing: border-box;
        }
        .hero h1 {
            font-size: 1.8rem; 
        }
        .hero p {
            font-size: 0.9rem;
        }

        /* خانة البحث */
        .search-section {
            margin: -20px auto 25px;
            width: 92%;
        }

        /* 🌟 ضبط شبكة المنتجات لتكون Fit 100% للموبايل */
        .container {
            padding: 0 4% 30px;
            box-sizing: border-box;
            width: 100%; /* احتواء كامل الشاشة */
        }
        
        .products-grid {
            /* هنا السحر: يجعل الكروت تأخذ العرض المتاح بالضبط وتعمل Fit تلقائي */
            grid-template-columns: repeat(auto-fit, minmax(100%, 1fr)); 
            gap: 15px; 
        }

        .product-card {
            width: 100%; /* الكارت يملأ المساحة المتاحة له بالملي */
            max-width: 100%;
            box-sizing: border-box;
        }

        /* ضبط حجم الصور لتكون احتوائية Fit داخل الكارت */
        .p-img {
            height: 240px; 
            padding: 10px;
        }
        .p-img img {
            object-fit: contain; /* تجعل الصورة تحافظ على أبعادها وتكون Fit جوة المربع */
            max-width: 100%;
        }

        .card-body {
            padding: 15px; 
        }
        .name {
            font-size: 1.2rem;
        }
        
        /* السلة في الموبايل */
        .cart-sidebar { 
            width: 100%; /* تملأ الشاشة بالكامل في الموبايل لسهولة الاستخدام */
            left: -100%;
        }
        .cart-sidebar.active { 
            left: 0; 
        }
    }

    /* لشاشات الموبايل الصغيرة جداً (أقل من 400px) */
    @media (max-width: 400px) {
        .hero h1 { 
            font-size: 1.5rem; 
        }
        .logo-text {
            font-size: 16px;
        }
    }
      
