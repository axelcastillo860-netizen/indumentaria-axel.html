<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Indumentaria Axel</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f9f9f9; }
    header { background: #222; color: #fff; padding: 15px; text-align: center; }
    .container { width: 90%; max-width: 1100px; margin: auto; padding: 20px; }
    .productos { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; }
    .producto { background: #fff; padding: 15px; border-radius: 10px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .producto img { max-width: 100%; border-radius: 8px; }
    .producto h3 { margin: 10px 0; }
    .producto button { padding: 8px 12px; border: none; background: #222; color: #fff; border-radius: 5px; cursor: pointer; }
    .producto button:hover { background: #444; }
    #carrito { background: #fff; padding: 15px; border-radius: 10px; margin-top: 30px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    #lista-carrito li { margin: 5px 0; }
    .total { font-weight: bold; margin-top: 10px; }
  </style>
</head>
<body>

<header>
  <h1>👕 Indumentaria Axel</h1>
</header>

<div class="container">
  <h2>Catálogo</h2>
  <div class="productos">
    <div class="producto">
      <img src="https://i.ibb.co/tKQ1L5F/remera-blanca.jpg" alt="Remera Blanca">
      <h3>Remera Blanca</h3>
      <p>$2500</p>
      <button onclick="agregarAlCarrito('Remera Blanca', 2500)">Agregar al carrito</button>
    </div>
    <div class="producto">
      <img src="https://i.ibb.co/1Mk3w9s/pantalon-negro.jpg" alt="Pantalón Negro">
      <h3>Pantalón Negro</h3>
      <p>$6000</p>
      <button onclick="agregarAlCarrito('Pantalón Negro', 6000)">Agregar al carrito</button>
    </div>
    <div class="producto">
      <img src="https://i.ibb.co/7NxYtN4/campera-jeans.jpg" alt="Campera Jeans">
      <h3>Campera de Jeans</h3>
      <p>$8500</p>
      <button onclick="agregarAlCarrito('Campera de Jeans', 8500)">Agregar al carrito</button>
    </div>
  </div>

  <div id="carrito">
    <h2>🛒 Carrito</h2>
    <ul id="lista-carrito"></ul>
    <p class="total">Total: $<span id="total">0</span></p>
    <button onclick="finalizarCompra()">Finalizar compra</button>
  </div>
</div>

<script>
  let carrito = [];
  let total = 0;

  function agregarAlCarrito(producto, precio) {
    carrito.push({producto, precio});
    total += precio;
    actualizarCarrito();
  }

  function actualizarCarrito() {
    const lista = document.getElementById("lista-carrito");
    lista.innerHTML = "";
    carrito.forEach(item => {
      const li = document.createElement("li");
      li.textContent = `${item.producto} - $${item.precio}`;
      lista.appendChild(li);
    });
    document.getElementById("total").textContent = total;
  }

  function finalizarCompra() {
    if (carrito.length === 0) {
      alert("Tu carrito está vacío.");
    } else {
      alert("Gracias por tu compra! Total: $" + total);
      carrito = [];
      total = 0;
      actualizarCarrito();
    }
  }
</script>

</body>
</html>

