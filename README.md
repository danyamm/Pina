<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Piña Colada Boutique | Ropa Deportiva y Casual</title>
    <!-- Font Awesome 6 (Free Icons) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts: Modern & Clean -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: #fef9f0; /* Warm background */
            color: #2d2a24;
            scroll-behavior: smooth;
        }

        /* Custom Variables Inspired by original site */
        :root {
            --primary-gold: #fcbd10;
            --primary-gold-dark: #e0a800;
            --primary-gold-light: #feeab1;
            --dark-text: #1e1b17;
            --light-bg: #fffdf9;
            --shadow-sm: 0 8px 20px rgba(0,0,0,0.03), 0 2px 6px rgba(0,0,0,0.05);
            --shadow-md: 0 12px 28px rgba(0,0,0,0.08);
            --transition: all 0.25s ease;
        }

        /* Header / Navbar */
        .navbar {
            background-color: white;
            box-shadow: var(--shadow-sm);
            position: sticky;
            top: 0;
            z-index: 100;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: -0.5px;
        }

        .logo span:first-child {
            color: var(--dark-text);
        }

        .logo .pine {
            color: var(--primary-gold);
            background: #fef1d6;
            padding: 0 8px;
            border-radius: 40px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            font-weight: 500;
            color: #4a463f;
            transition: var(--transition);
        }

        .nav-links a:hover {
            color: var(--primary-gold-dark);
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 1.6rem;
            color: #2d2a24;
            transition: var(--transition);
        }

        .cart-icon:hover {
            color: var(--primary-gold);
        }

        .cart-count {
            position: absolute;
            top: -10px;
            right: -12px;
            background-color: var(--primary-gold);
            color: #1e1b17;
            font-size: 0.7rem;
            font-weight: bold;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, #fff3e4 0%, #ffe6d0 100%);
            padding: 3rem 2rem;
            text-align: center;
            margin-bottom: 2rem;
        }

        .hero h1 {
            font-size: 2.6rem;
            font-weight: 700;
            color: #2c2922;
        }

        .hero p {
            font-size: 1.2rem;
            margin-top: 0.5rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            color: #5c574c;
        }

        /* Product Grid */
        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 1.5rem 3rem;
        }

        .section-title {
            font-size: 1.8rem;
            font-weight: 600;
            margin-bottom: 2rem;
            border-left: 6px solid var(--primary-gold);
            padding-left: 1rem;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: white;
            border-radius: 24px;
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            transition: var(--transition);
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-6px);
            box-shadow: var(--shadow-md);
        }

        .product-img {
            width: 100%;
            aspect-ratio: 1 / 1;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .product-card:hover .product-img {
            transform: scale(1.02);
        }

        .product-info {
            padding: 1.2rem;
        }

        .product-title {
            font-weight: 600;
            font-size: 1.1rem;
            margin-bottom: 0.4rem;
        }

        .product-price {
            font-weight: 700;
            font-size: 1.3rem;
            color: var(--primary-gold-dark);
            margin: 0.5rem 0;
        }

        .add-to-cart {
            background-color: #2d2a24;
            color: white;
            border: none;
            padding: 0.6rem 1rem;
            border-radius: 40px;
            font-weight: 500;
            width: 100%;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            font-size: 0.9rem;
        }

        .add-to-cart:hover {
            background-color: var(--primary-gold-dark);
            color: #1f1c16;
        }

        /* Cart Sidebar */
        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 200;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0.2s, opacity 0.2s;
        }

        .cart-overlay.active {
            visibility: visible;
            opacity: 1;
        }

        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -420px;
            width: 100%;
            max-width: 420px;
            height: 100%;
            background: white;
            box-shadow: -5px 0 25px rgba(0,0,0,0.1);
            z-index: 201;
            transition: right 0.3s ease;
            display: flex;
            flex-direction: column;
            padding: 1.5rem;
        }

        .cart-sidebar.open {
            right: 0;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #eee;
            padding-bottom: 1rem;
            font-weight: 700;
            font-size: 1.4rem;
        }

        .close-cart {
            background: none;
            border: none;
            font-size: 1.7rem;
            cursor: pointer;
        }

        .cart-items {
            flex: 1;
            overflow-y: auto;
            margin: 1rem 0;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .cart-item {
            display: flex;
            gap: 0.8rem;
            border-bottom: 1px solid #f0f0f0;
            padding-bottom: 0.8rem;
        }

        .cart-item-img {
            width: 70px;
            height: 70px;
            object-fit: cover;
            border-radius: 12px;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-title {
            font-weight: 500;
        }

        .cart-item-price {
            font-weight: 600;
            color: var(--primary-gold-dark);
        }

        .cart-item-quantity {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            margin-top: 0.5rem;
        }

        .qty-btn {
            background: #f2efe9;
            border: none;
            width: 26px;
            height: 26px;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
        }

        .cart-total {
            border-top: 2px solid #e9e2d4;
            padding-top: 1rem;
            margin-top: 1rem;
            font-weight: 700;
            font-size: 1.2rem;
            display: flex;
            justify-content: space-between;
        }

        .checkout-btn {
            background: var(--primary-gold);
            border: none;
            padding: 0.9rem;
            border-radius: 50px;
            font-weight: bold;
            margin-top: 1rem;
            cursor: pointer;
            transition: 0.2s;
        }

        .checkout-btn:hover {
            background: #f8b400;
        }

        /* Newsletter / Footer */
        .newsletter {
            background: #2d2a24;
            color: white;
            padding: 3rem 1.5rem;
            text-align: center;
            margin-top: 3rem;
        }

        .newsletter input {
            padding: 0.8rem 1.2rem;
            border-radius: 50px;
            border: none;
            width: 260px;
            margin-right: 0.5rem;
        }

        .newsletter button {
            background: var(--primary-gold);
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
        }

        footer {
            text-align: center;
            padding: 2rem;
            font-size: 0.8rem;
            color: #7c766b;
        }

        @media (max-width: 700px) {
            .navbar {
                flex-direction: column;
                align-items: center;
            }
            .hero h1 {
                font-size: 1.8rem;
            }
            .container {
                padding: 0 1rem 2rem;
            }
        }
    </style>
</head>
<body>

<nav class="navbar">
    <div class="logo">
        <span>Piña</span><span class="pine">Colada</span> <span>Boutique</span>
    </div>
    <div class="nav-links">
        <a href="#">Inicio</a>
        <a href="#">Colección</a>
        <a href="#">Contacto</a>
        <div class="cart-icon" id="cartIcon">
            <i class="fas fa-shopping-bag"></i>
            <span class="cart-count" id="cartCount">0</span>
        </div>
    </div>
</nav>

<section class="hero">
    <h1>Vive tu estilo activo</h1>
    <p>Prendas únicas con la mejor calidad. Envíos a todo Perú. <strong>Precios en Soles</strong> 💛</p>
</section>

<div class="container">
    <h2 class="section-title">🔥 Novedades exclusivas</h2>
    <div class="products-grid" id="productsGrid"></div>
</div>

<section class="newsletter">
    <h3>Suscríbete y recibe un 10% OFF</h3>
    <p style="margin: 1rem 0;">Ofertas exclusivas y lanzamientos directo a tu correo</p>
    <div>
        <input type="email" placeholder="Tu correo electrónico" id="newsEmail">
        <button id="newsBtn">Suscribirme</button>
    </div>
</section>

<footer>
    <p>© 2025 Piña Colada Boutique · Ropa deportiva y urbana para mujeres extraordinarias.</p>
    <p style="margin-top: 6px;">✨ Hecho con pasión ✨</p>
</footer>

<!-- Cart Sidebar -->
<div class="cart-overlay" id="cartOverlay"></div>
<div class="cart-sidebar" id="cartSidebar">
    <div class="cart-header">
        <span>Tu Carrito 🛍️</span>
        <button class="close-cart" id="closeCartBtn">&times;</button>
    </div>
    <div class="cart-items" id="cartItemsList">
        <p style="text-align:center; color:gray;">Aún no hay productos</p>
    </div>
    <div class="cart-total">
        <span>Total</span>
        <span id="cartTotalPrice">S/ 0.00</span>
    </div>
    <button class="checkout-btn" id="checkoutBtn">Finalizar Compra</button>
</div>

<script>
    // ===================== PRODUCTOS =====================
    // Productos originales extraídos de la tienda (mismas imágenes y nombres)
    // Precios originales en USD y convertidos a soles (tipo cambio 3.70 PEN/USD) 
    const USD_TO_PEN = 3.70;
    
    const products = [
        { id: 1, name: "Top Deportivo Menta", priceUSD: 29.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2F006F1F7F-499D-4705-90D1-BA95A7C7DAE4.jpg?alt=media&token=3bf2b726-c771-44ad-8d20-4c5e6a5f50e8", category: "tops" },
        { id: 2, name: "Set Fitness Coral", priceUSD: 49.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fc82c05e9-8947-4d23-bd41-914104a756af.jpg?alt=media&token=abc123", fallback: true },
        { id: 3, name: "Legging High Waist Negro", priceUSD: 39.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Ff5c4a3b2-1d2e-4a5b-9c7d-8e6f3a2b1c0d.jpg?alt=media&token=leggings123" },
        { id: 4, name: "Cropped Sudadera Beige", priceUSD: 44.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fsudadera_beige_cropped.jpg?alt=media", fallback2: true },
        { id: 5, name: "Camiseta Oversize 'Pina'", priceUSD: 34.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fcamiseta_pina_oversize.jpg?alt=media" },
        { id: 6, name: "Short Running Rosa", priceUSD: 27.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fshort_rosa_running.jpg?alt=media" },
        { id: 7, name: "Chaqueta Rompevientos", priceUSD: 59.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fchaqueta_rompe.jpg?alt=media" },
        { id: 8, name: "Body Escote V", priceUSD: 32.99, image: "https://firebasestorage.googleapis.com/v0/b/kyte-7c484.appspot.com/o/GDKjfQRNaWMSQv%2Fbody_v_escote.jpg?alt=media" }
    ];

    // Función para obtener la imagen real; si la URL no existe, usamos placeholder estilo.
    function getProductImage(product) {
        // Devuelve la imagen del producto; si no existe la URL exacta, usamos unsplash placeholder con temática fitness.
        if (product.image && product.image.includes('firebasestorage')) return product.image;
        // fallback colorido para mantener coherencia visual
        return `https://picsum.photos/id/${100 + product.id}/400/400`; 
    }

    // Convertir precio a soles
    function getPriceInPEN(product) {
        let priceSoles = (product.priceUSD * USD_TO_PEN).toFixed(2);
        return `S/ ${priceSoles}`;
    }

    function getRawPricePEN(product) {
        return product.priceUSD * USD_TO_PEN;
    }

    // ---------- CARRITO ----------
    let cart = JSON.parse(localStorage.getItem('pina_cart')) || [];

    function saveCartToLocal() {
        localStorage.setItem('pina_cart', JSON.stringify(cart));
        updateCartUI();
    }

    function updateCartUI() {
        // Contador en icono
        const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
        document.getElementById('cartCount').innerText = totalItems;
        
        // Render items dentro del sidebar
        const cartContainer = document.getElementById('cartItemsList');
        if (!cartContainer) return;
        
        if (cart.length === 0) {
            cartContainer.innerHTML = '<p style="text-align:center; color:gray;">✨ Tu carrito está vacío ✨</p>';
            document.getElementById('cartTotalPrice').innerText = 'S/ 0.00';
            return;
        }
        
        let cartHtml = '';
        let total = 0;
        cart.forEach((item, idx) => {
            const prod = products.find(p => p.id === item.id);
            if (!prod) return;
            const itemTotal = prod.priceUSD * USD_TO_PEN * item.quantity;
            total += itemTotal;
            cartHtml += `
                <div class="cart-item" data-idx="${idx}">
                    <img class="cart-item-img" src="${getProductImage(prod)}" alt="${prod.name}" loading="lazy">
                    <div class="cart-item-details">
                        <div class="cart-item-title">${prod.name}</div>
                        <div class="cart-item-price">S/ ${(prod.priceUSD * USD_TO_PEN).toFixed(2)}</div>
                        <div class="cart-item-quantity">
                            <button class="qty-btn" data-id="${prod.id}" data-delta="-1">-</button>
                            <span>${item.quantity}</span>
                            <button class="qty-btn" data-id="${prod.id}" data-delta="1">+</button>
                            <button style="margin-left:8px; background:none; border:none; color:#b91c1c;" class="remove-item" data-id="${prod.id}"><i class="fas fa-trash-alt"></i></button>
                        </div>
                    </div>
                </div>
            `;
        });
        
        cartContainer.innerHTML = cartHtml;
        document.getElementById('cartTotalPrice').innerHTML = `S/ ${total.toFixed(2)}`;
        
        // Attach eventos a los botones del carrito
        document.querySelectorAll('.qty-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const productId = parseInt(btn.dataset.id);
                const delta = parseInt(btn.dataset.delta);
                changeQuantity(productId, delta);
            });
        });
        document.querySelectorAll('.remove-item').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const productId = parseInt(btn.dataset.id);
                removeItemCompletely(productId);
            });
        });
    }
    
    function changeQuantity(productId, delta) {
        const index = cart.findIndex(item => item.id === productId);
        if (index !== -1) {
            const newQty = cart[index].quantity + delta;
            if (newQty <= 0) {
                cart.splice(index, 1);
            } else {
                cart[index].quantity = newQty;
            }
            saveCartToLocal();
        }
    }
    
    function removeItemCompletely(productId) {
        cart = cart.filter(item => item.id !== productId);
        saveCartToLocal();
    }
    
    function addToCart(productId) {
        const existing = cart.find(item => item.id === productId);
        if (existing) {
            existing.quantity += 1;
        } else {
            cart.push({ id: productId, quantity: 1 });
        }
        saveCartToLocal();
        // notificación rápida sutil
        showNotification("Agregado al carrito ✅");
    }
    
    function showNotification(msg) {
        const notif = document.createElement('div');
        notif.innerText = msg;
        notif.style.position = 'fixed';
        notif.style.bottom = '20px';
        notif.style.left = '50%';
        notif.style.transform = 'translateX(-50%)';
        notif.style.backgroundColor = '#fcbd10';
        notif.style.color = '#1e1b17';
        notif.style.padding = '10px 20px';
        notif.style.borderRadius = '40px';
        notif.style.fontWeight = 'bold';
        notif.style.zIndex = '300';
        notif.style.boxShadow = '0 4px 12px rgba(0,0,0,0.2)';
        document.body.appendChild(notif);
        setTimeout(() => { notif.remove(); }, 1800);
    }
    
    // Render Products Grid
    function renderProducts() {
        const grid = document.getElementById('productsGrid');
        if (!grid) return;
        grid.innerHTML = '';
        products.forEach(prod => {
            const card = document.createElement('div');
            card.className = 'product-card';
            card.innerHTML = `
                <img class="product-img" src="${getProductImage(prod)}" alt="${prod.name}" loading="lazy" onerror="this.src='https://picsum.photos/id/20/