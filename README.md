:root {
    --gold: #c5a059;
    --dark: #1a1a1a;
    --white: #ffffff;
    --shadow: 0 10px 30px rgba(0,0,0,0.1);
}

body { margin: 0; font-family: 'Segoe UI', sans-serif; background: #fdfdfd; color: var(--dark); direction: rtl; }

/* هيدر عصري */
header {
    background: white; padding: 15px 5%; display: flex; justify-content: space-between;
    align-items: center; border-bottom: 2px solid var(--gold); position: sticky; top: 0; z-index: 1000;
}

.logo { font-size: 1.8rem; font-weight: 800; color: var(--gold); text-decoration: none; letter-spacing: 1px; }

/* قسم الواجهة */
.hero {
    height: 60vh; background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), 
    url('https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&w=1000&q=80') center/cover;
    display: flex; align-items: center; justify-content: center; color: white; text-align: center;
}

.hero-glass { padding: 40px; background: rgba(255,255,255,0.1); backdrop-filter: blur(10px); border-radius: 20px; border: 1px solid rgba(255,255,255,0.2); }

/* البحث */
.search-container { padding: 40px 10%; background: #fff; position: sticky; top: 70px; z-index: 900; }
#searchBar {
    width: 100%; padding: 18px; border: 2px solid #eee; border-radius: 50px; 
    font-size: 1.1rem; outline: none; transition: 0.3s; text-align: center;
}
#searchBar:focus { border-color: var(--gold); box-shadow: var(--shadow); }

/* شبكة المنتجات */
.products-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 25px; padding: 20px 10% 80px;
}

.product-card {
    background: white; border-radius: 15px; overflow: hidden; 
    box-shadow: 0 4px 15px rgba(0,0,0,0.05); transition: 0.3s; border: 1px solid #f0f0f0;
    display: flex; flex-direction: column;
}
.product-card:hover { transform: translateY(-5px); border-color: var(--gold); }

.product-info { padding: 20px; text-align: center; }
.brand-name { color: var(--gold); font-size: 0.9rem; font-weight: bold; margin-bottom: 5px; }
.perfume-name { font-size: 1.2rem; font-weight: bold; margin-bottom: 15px; }

.size-selector { 
    display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 15px;
}
.size-option {
    background: #f8f8f8; padding: 8px; border-radius: 8px; font-size: 0.85rem;
    cursor: pointer; border: 1px solid #eee; transition: 0.2s;
}
.size-option:hover { background: #eee; }
.size-option input { margin-left: 5px; accent-color: var(--gold); }

.btn-add {
    background: var(--gold); color: white; border: none; padding: 12px;
    font-weight: bold; cursor: pointer; transition: 0.3s; width: 100%; margin-top: auto;
}
.btn-add:hover { background: #a68545; }

/* سلة التسوق الجانبية */
#cartModal {
    position: fixed; left: -100%; top: 0; width: 350px; height: 100%;
    background: white; z-index: 2000; transition: 0.4s; padding: 20px;
    box-shadow: 5px 0 20px rgba(0,0,0,0.2);
}
#cartModal.active { left: 0; }
.cart-header { display: flex; justify-content: space-between; border-bottom: 2px solid var(--gold); padding-bottom: 10px; margin-bottom: 20px; }

.checkout-btn {
    background: #25d366; color: white; width: 100%; padding: 15px; 
    border-radius: 10px; border: none; font-size: 1.1rem; font-weight: bold;
    cursor: pointer; margin-top: 20px; display: flex; align-items: center; justify-content: center; gap: 10px;
}
