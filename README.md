<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>JU2paz — Marque indépendante</title>

  <!-- Style propre type GitHub / minimal street -->
  <style>
    :root {
      --black: #0f0f0f;
      --white: #ffffff;
      --gray: #f2f2f2;
      --dark-gray: #6b6b6b;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    }

    body {
      background: var(--white);
      color: var(--black);
      line-height: 1.6;
    }

    header {
      position: sticky;
      top: 0;
      background: var(--white);
      border-bottom: 1px solid #e5e5e5;
      padding: 20px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 10;
    }

    header h1 {
      font-size: 20px;
      letter-spacing: 3px;
      text-transform: uppercase;
    }

    .cart-btn {
      cursor: pointer;
      font-size: 14px;
    }

    main {
      max-width: 1200px;
      margin: auto;
      padding: 60px 40px;
    }

    .intro {
      max-width: 700px;
      margin-bottom: 80px;
    }

    .intro h2 {
      font-size: 28px;
      margin-bottom: 20px;
    }

    .intro p {
      color: var(--dark-gray);
      font-size: 16px;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 40px;
    }

    .product {
      border: 1px solid #e5e5e5;
      padding: 16px;
      transition: transform 0.2s ease;
    }

    .product:hover {
      transform: translateY(-4px);
    }

    .product img {
      width: 100%;
      height: 360px;
      object-fit: cover;
      background: var(--gray);
    }

    .product h3 {
      font-size: 16px;
      margin: 12px 0 4px;
    }

    .product p {
      font-size: 14px;
      margin-bottom: 10px;
    }

    .product button {
      width: 100%;
      padding: 10px;
      background: var(--black);
      color: var(--white);
      border: none;
      cursor: pointer;
      font-size: 14px;
    }

    .cart {
      position: fixed;
      top: 0;
      right: -360px;
      width: 360px;
      height: 100%;
      background: var(--white);
      border-left: 1px solid #e5e5e5;
      padding: 30px;
      transition: right 0.3s ease;
      z-index: 20;
    }

    .cart.open { right: 0; }

    .cart h2 {
      margin-bottom: 20px;
      font-size: 20px;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      font-size: 14px;
      margin-bottom: 10px;
    }

    .cart-total {
      margin-top: 20px;
      font-weight: bold;
    }

    .checkout {
      width: 100%;
      margin-top: 30px;
      padding: 12px;
      background: var(--black);
      color: var(--white);
      border: none;
      cursor: pointer;
    }

    footer {
      text-align: center;
      padding: 40px;
      border-top: 1px solid #e5e5e5;
      margin-top: 100px;
      font-size: 14px;
      color: var(--dark-gray);
    }
  </style>
</head>
<body>

<header>
  <h1>JU2PAZ</h1>
  <div class="cart-btn" onclick="toggleCart()">Panier (<span id="cart-count">0</span>)</div>
</header>

<main>
  <section class="intro">
    <h2>Marque française indépendante</h2>
    <p>
      JU2paz est une marque française de vêtements indépendante inspirée par la culture urbaine et l’expression personnelle.
      Des pièces sobres et affirmées, pensées en petites séries, pour affirmer son identité.
    </p>
  </section>

  <section class="products">
    <div class="product">
      <img src="image1.jpg" alt="T-shirt JU2paz" />
      <h3>T-shirt JU2paz</h3>
      <p>25 €</p>
      <button onclick="addToCart('T-shirt JU2paz', 25)">Ajouter au panier</button>
    </div>

    <div class="product">
      <img src="image2.jpg" alt="Sweat JU2paz" />
      <h3>Sweat JU2paz</h3>
      <p>45 €</p>
      <button onclick="addToCart('Sweat JU2paz', 45)">Ajouter au panier</button>
    </div>
  </section>
</main>

<div class="cart" id="cart">
  <h2>Panier</h2>
  <div id="cart-items"></div>
  <div class="cart-total">Total : <span id="total">0</span> €</div>
  <button class="checkout" onclick="checkout()">Paiement</button>
</div>

<footer>
  © 2026 JU2paz — Tous droits réservés
</footer>

<script>
  let cart = [];

  function toggleCart() {
    document.getElementById('cart').classList.toggle('open');
  }

  function addToCart(name, price) {
    cart.push({ name, price });
    updateCart();
  }

  function updateCart() {
    const cartItems = document.getElementById('cart-items');
    cartItems.innerHTML = '';
    let total = 0;

    cart.forEach(item => {
      total += item.price;
      const div = document.createElement('div');
      div.className = 'cart-item';
      div.innerHTML = `<span>${item.name}</span><span>${item.price} €</span>`;
      cartItems.appendChild(div);
    });

    document.getElementById('total').innerText = total;
    document.getElementById('cart-count').innerText = cart.length;
  }

  function checkout() {
    alert('Paiement à connecter (Stripe / PayPal)');
  }
</script>

</body>
</html>
