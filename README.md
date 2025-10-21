# SIFwear
টাকায় নয় পরনে জিতুন!
<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Online Shop</title>
<style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f5f5f5; }
    header { background: #ff6f61; color: white; text-align: center; padding: 20px; }
    .shop-container { display: flex; flex-wrap: wrap; justify-content: center; padding: 20px; }
    .product { background: white; margin: 10px; padding: 10px; width: 200px; border-radius: 10px; box-shadow: 0 0 5px rgba(0,0,0,0.1); text-align: center; }
    .product img { width: 100%; height: 150px; object-fit: cover; border-radius: 10px; }
    .product h3 { margin: 10px 0 5px; }
    .product p { margin: 5px 0; }
    .btn { background: #ff6f61; color: white; padding: 10px; border: none; border-radius: 5px; cursor: pointer; }
    .btn:hover { background: #ff3b2e; }
    #orderForm { display: none; position: fixed; top:0; left:0; width:100%; height:100%; background: rgba(0,0,0,0.7); justify-content: center; align-items: center; }
    #orderForm div { background: white; padding: 20px; border-radius: 10px; width: 300px; }
    #orderForm input, #orderForm select { width: 100%; padding: 10px; margin: 5px 0; }
</style>
</head>
<body>

<header>
    <h1>আমার অনলাইন শপ</h1>
</header>

<div class="shop-container" id="shop"></div>

<!-- অর্ডার ফর্ম -->
<div id="orderForm">
    <div>
        <h3>অর্ডার ফর্ম</h3>
        <input type="text" id="customerName" placeholder="আপনার নাম" required>
        <input type="text" id="customerPhone" placeholder="মোবাইল নম্বর" required>
        <select id="paymentMethod">
            <option value="bkash">বিকাশ</option>
            <option value="nagad">নগদ</option>
        </select>
        <p id="selectedProduct"></p>
        <button class="btn" onclick="submitOrder()">অর্ডার করুন</button>
        <button class="btn" style="background:#999;margin-top:5px;" onclick="closeForm()">বাতিল</button>
    </div>
</div>

<script>
// প্রোডাক্ট ডেটা
let products = [
    {id:1, name:"শার্ট", price:500, img:"https://via.placeholder.com/200x150?text=Shirt"},
    {id:2, name:"প্যান্ট", price:800, img:"https://via.placeholder.com/200x150?text=Pants"},
    {id:3, name:"শু", price:1200, img:"https://via.placeholder.com/200x150?text=Shoes"}
];

let selectedProduct = null;

function loadShop() {
    let shop = document.getElementById('shop');
    shop.innerHTML = '';
    products.forEach(product => {
        let div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
            <img src="${product.img}" alt="${product.name}">
            <h3>${product.name}</h3>
            <p>মূল্য: ${product.price} টাকা</p>
            <button class="btn" onclick="openForm(${product.id})">অর্ডার</button>
        `;
        shop.appendChild(div);
    });
}

function openForm(id){
    selectedProduct = products.find(p => p.id === id);
    document.getElementById('selectedProduct').innerText = `পণ্য: ${selectedProduct.name}, দাম: ${selectedProduct.price} টাকা`;
    document.getElementById('orderForm').style.display = 'flex';
}

function closeForm(){
    document.getElementById('orderForm').style.display = 'none';
}

function submitOrder(){
    let name = document.getElementById('customerName').value;
    let phone = document.getElementById('customerPhone').value;
    let payment = document.getElementById('paymentMethod').value;

    if(!name || !phone) { alert("সব ফিল্ড পূরণ করুন"); return; }

    alert(`অর্ডার হয়েছে!\nপণ্য: ${selectedProduct.name}\nমূল্য: ${selectedProduct.price} টাকা\nপেমেন্ট: ${payment}\nনাম: ${name}\nফোন: ${phone}`);
    closeForm();
}

window.onload = loadShop;
</script>

</body>
</html>
