<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sifwear Online Shop</title>
<style>
  body { font-family: Arial, sans-serif; margin:0; padding:0; background:#f9f9f9; }
  header { background:#222; color:white; padding:20px; text-align:center; }
  h1 { margin:0; }
  .products { display:flex; flex-wrap:wrap; justify-content:center; padding:20px; gap:20px; }
  .product { background:white; padding:15px; border-radius:10px; box-shadow:0 2px 8px rgba(0,0,0,0.2); width:200px; text-align:center; }
  .product img { width:100%; border-radius:10px; }
  .product button { margin-top:10px; padding:10px; width:100%; background:#222; color:white; border:none; border-radius:5px; cursor:pointer; }
  form { max-width:400px; margin:20px auto; background:white; padding:20px; border-radius:10px; box-shadow:0 2px 8px rgba(0,0,0,0.2); }
  input, select { width:100%; padding:10px; margin:10px 0; border-radius:5px; border:1px solid #ccc; }
  button.submit { background:#222; color:white; border:none; padding:10px; width:100%; border-radius:5px; cursor:pointer; }
</style>
</head>
<body>

<header>
  <h1>Sifwear</h1>
  <p>Professional Online Clothing Shop</p>
</header>

<section class="products">
  <div class="product">
    <img src="https://via.placeholder.com/200x200.png?text=T-Shirt" alt="T-Shirt">
    <h3>T-Shirt</h3>
    <p>৳500</p>
    <button onclick="order('T-Shirt',500)">Order Now</button>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/200x200.png?text=Hoodie" alt="Hoodie">
    <h3>Hoodie</h3>
    <p>৳1200</p>
    <button onclick="order('Hoodie',1200)">Order Now</button>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/200x200.png?text=Pant" alt="Pant">
    <h3>Pant</h3>
    <p>৳800</p>
    <button onclick="order('Pant',800)">Order Now</button>
  </div>
</section>

<form id="orderForm" style="display:none;">
  <h2>Complete Your Order</h2>
  <input type="text" id="productName" readonly>
  <input type="number" id="productPrice" readonly>
  <input type="text" placeholder="Your Name" id="name" required>
  <input type="text" placeholder="Phone Number" id="phone" required>
  <input type="text" placeholder="Address" id="address" required>
  <select id="payment" required>
    <option value="">Select Payment Method</option>
    <option value="bKash">bKash</option>
    <option value="Nagad">Nagad</option>
    <option value="Cash on Delivery">Cash on Delivery</option>
  </select>
  <button class="submit" type="button" onclick="submitOrder()">Place Order</button>
</form>

<script>
  function order(name, price) {
    document.getElementById('orderForm').style.display='block';
    document.getElementById('productName').value = name;
    document.getElementById('productPrice').value = price;
    window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
  }

  function submitOrder() {
    const name = document.getElementById('name').value;
    const phone = document.getElementById('phone').value;
    const address = document.getElementById('address').value;
    const product = document.getElementById('productName').value;
    const price = document.getElementById('productPrice').value;
    const payment = document.getElementById('payment').value;

    if(!name || !phone || !address || !payment){
      alert('Please fill all fields!');
      return;
    }

    alert(`Order Placed!\n\nProduct: ${product}\nPrice: ৳${price}\nName: ${name}\nPhone: ${phone}\nAddress: ${address}\nPayment: ${payment}\n\nWe will contact you soon!`);
    
    // Clear form
    document.getElementById('orderForm').reset();
    document.getElementById('orderForm').style.display='none';
  }
</script>

</body>
</html>
