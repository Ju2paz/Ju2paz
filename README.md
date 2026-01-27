<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>JU2paz – Boutique Officielle</title>
  <style>
    * { box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }
    body { margin: 0; background: #f6f6f6; color: #222; }
    header { background: #000; color: #fff; padding: 20px; display: flex; justify-content: space-between; align-items: center; }
    header h1 { margin: 0; letter-spacing: 2px; }
    .cart-btn { cursor: pointer; }

    main { padding: 40px; }
    .products { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 30px; }

    .product { background: #fff; border-radius: 12px; padding: 15px; box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
    .product img { width: 100%; border-radius: 10px; height: 300px; object-fit: cover; }
    .product h3 { margin: 10px 0 5px; }
    .product p { margin: 0 0 10px; font-weight: bold; }
    .product button { width: 100%; padding: 10px; border: none; border-radius: 8px; background: #000; color: #fff; cursor: pointer; }
    .product button:hover { opacity: 0.85; }

    .cart { position: fixed; top: 0; right: -400px; width: 350px; height: 100%; background: #fff; box-shadow: -4px 0 12px rgba(0,0,0,0.2); padding: 20px; transition: 0.3s; }
    .cart.open { right: 0; }
    .cart h2 { margin-top: 0; }
    .cart-item { display: flex; justify-content: space-between; margin-bottom: 10px; }
    .cart-total { font-weight: bold; margin-top: 20px; }
    .checkout { margin-top: 20px; width: 100%; padding: 12px; border: none; background: #000; color: #fff; border-radius: 8px; cursor: pointer; }

    footer { text-align: center; padding: 20px; background: #000; color: #fff; margin-top: 40px; }
  </style>
</head>
<body>

<header>
  <h1>JU2paz</h1>
  <div class="cart-btn" onclick="toggleCart()">🛒 Panier (<span id="cart-count">0</span>)</div>
</header>

<main>
  <section class="intro">
    <h2>Marque française indépendante</h2>
    <p>
      JU2paz est une marque de vêtements française indépendante, née d’une envie simple : créer des pièces fortes,
      authentiques et accessibles, sans compromis sur le style ni sur l’identité. Inspirée par la rue, la culture urbaine
      et l’expression personnelle, la marque s’adresse à celles et ceux qui veulent porter plus qu’un vêtement : un état d’esprit.
    </p>
    <p>
      Chaque création JU2paz est pensée avec soin, en petites séries, pour garantir une identité unique et une vraie différence.
      Ici, pas de production de masse impersonnelle, mais une vision indépendante, libre et assumée.
    </p>
    <p>
      JU2paz, c’est l’équilibre entre sobriété et caractère, entre modernité et authenticité. Une marque faite pour se démarquer,
      avancer à son rythme et rester fidèle à soi-même.
    </p>
  </section>

  <section class="products">
    <!-- PRODUIT 1 -->
    <div class="product">
      <img src="image1.jpg" alt="Produit JU2paz">
      <h3>T-shirt JU2paz</h3>
      <p>25 €</p>
      <button onclick="addToCart('T-shirt JU2paz', 25)">Ajouter au panier</button>
    </div>

    <!-- PRODUIT 2 -->
    <div class="product">
      <img src="image2.jpg" alt="Produit JU2paz">
      <h3>Sweat JU2paz</h3>
      <p>45 €</p>
      <button onclick="addToCart('Sweat JU2paz', 45)">Ajouter au panier</button>
    </div>

    <!-- Tu peux dupliquer ces blocs -->
  </section>
</main>

<div class="cart" id="cart">
  <h2>Panier</h2>
  <div id="cart-items"></div>
  <div class="cart-total">Total : <span id="total">0</span> €</div>
  <button class="checkout" onclick="checkout()">Passer au paiement</button>
</div>

<footer>
  © 2026 – JU2paz. Tous droits réservés.
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
    alert('Paiement prêt à être connecté (Stripe / PayPal).');
  }
</script>

</body>
</html>
