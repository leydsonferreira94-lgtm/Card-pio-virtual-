# Card-pio-virtual-
Cardápio pra escolha de produtos 
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cardápio Digital - Versão 2</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Arial,Helvetica,sans-serif;background:#f5f5f5;color:#222;padding-bottom:95px}
:root{--primary:#111;--accent:#e63946;--card:#fff;--muted:#777}
.header{background:#111;color:#fff;padding:24px 18px 20px;text-align:center;position:relative}
.logo{width:72px;height:72px;border-radius:50%;object-fit:cover;background:#333;margin:auto;display:block;border:3px solid #fff}
.business-name{font-size:25px;font-weight:800;margin:10px 0 5px}.status{font-size:13px;color:#7cff9b}.info{font-size:12px;color:#ddd;margin-top:7px}
.container{max-width:760px;margin:auto;padding:14px}
.search{width:100%;padding:14px 16px;border:1px solid #ddd;border-radius:14px;font-size:16px;background:white;outline:none}
.categories{display:flex;gap:8px;overflow-x:auto;padding:13px 0;scrollbar-width:none}.categories::-webkit-scrollbar{display:none}
.cat{border:0;background:#fff;padding:10px 15px;border-radius:20px;white-space:nowrap;font-weight:700;color:#555}.cat.active{background:#111;color:#fff}
.section-title{font-size:21px;margin:18px 2px 10px}.grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.card{background:#fff;border-radius:16px;overflow:hidden;box-shadow:0 2px 10px #0000000c}.photo{height:150px;background:#ddd;position:relative;cursor:pointer}.photo img{width:100%;height:100%;object-fit:cover}.zoom{position:absolute;right:9px;top:9px;background:#000b;color:#fff;border-radius:20px;padding:6px 9px;font-size:12px}
.card-body{padding:12px}.product-name{font-weight:800;font-size:16px}.desc{font-size:12px;color:#777;margin:5px 0 9px;line-height:1.35;min-height:32px}.price{font-weight:800;font-size:17px;margin-bottom:9px}
.qty{display:flex;align-items:center;justify-content:space-between;border:1px solid #eee;border-radius:11px;overflow:hidden}.qty button{border:0;background:#f0f0f0;width:36px;height:36px;font-size:21px}.qty span{font-weight:800;min-width:28px;text-align:center}
.cart{position:fixed;bottom:12px;left:50%;transform:translateX(-50%);width:min(92%,720px);background:#111;color:#fff;border-radius:17px;padding:13px 16px;display:flex;align-items:center;justify-content:space-between;box-shadow:0 6px 25px #0004;z-index:20;cursor:pointer}.cart small{color:#ccc}.cart strong{font-size:18px}
.modal{display:none;position:fixed;inset:0;background:#000d;z-index:50;align-items:center;justify-content:center;padding:16px}.modal.show{display:flex}.modal-box{background:#fff;border-radius:18px;width:min(720px,100%);max-height:92vh;overflow:auto;position:relative}.close{position:absolute;right:10px;top:10px;z-index:3;border:0;border-radius:50%;background:#000b;color:#fff;width:38px;height:38px;font-size:22px}
.gallery{background:#111;padding:15px}.gallery img{width:100%;height:min(55vh,430px);object-fit:contain}.gallery-controls{display:flex;justify-content:space-between;align-items:center;color:#fff;margin-top:8px}.gallery-controls button{background:#333;color:#fff;border:0;border-radius:10px;padding:10px 16px;font-size:18px}
.modal-content{padding:18px}.addon{display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid #eee}.addon label{flex:1}.modal-actions{display:flex;gap:10px;margin-top:16px}.primary,.secondary{border:0;border-radius:12px;padding:14px;font-weight:800;font-size:15px}.primary{background:#111;color:#fff;flex:1}.secondary{background:#eee}
.order-list{margin:0;padding:0;list-style:none}.order-item{padding:12px 0;border-bottom:1px solid #eee}.order-row{display:flex;justify-content:space-between;gap:8px}.order-controls{display:flex;gap:7px;align-items:center;margin-top:8px}.mini{border:0;background:#eee;border-radius:8px;width:30px;height:30px;font-size:17px}
.form label{font-size:13px;font-weight:700;display:block;margin:13px 0 6px}.form input,.form select,.form textarea{width:100%;padding:13px;border:1px solid #ddd;border-radius:11px;font-size:15px;background:#fff}.form textarea{min-height:75px;resize:vertical}.choice{display:flex;gap:8px}.choice label{flex:1;margin:0;border:1px solid #ddd;border-radius:11px;padding:12px;text-align:center;font-weight:700}.choice input{display:none}.choice input:checked+span{background:#111;color:#fff;border-radius:8px;padding:7px 10px}.choice span{display:block;padding:7px 10px}
.total-box{background:#f6f6f6;border-radius:13px;padding:14px;margin-top:15px}.line{display:flex;justify-content:space-between;margin:7px 0}.grand{font-size:20px;font-weight:800;border-top:1px solid #ddd;padding-top:10px}
.addon-group{margin:12px 0}.addon-option{display:block;padding:9px 10px;margin-top:6px;background:#f7f7f7;border-radius:10px;cursor:pointer}.addon-option span{float:right;color:#555}.sold-out{opacity:.72}.sold-badge{position:absolute;left:9px;bottom:9px;background:#555;color:#fff;border-radius:8px;padding:6px 9px;font-size:11px;font-weight:800}.unavailable{background:#eee;color:#666;border-radius:10px;text-align:center;padding:9px;font-size:12px;font-weight:800}.confirm-item{padding:10px 0;border-bottom:1px solid #eee}.confirm-item small{display:block;color:#777;margin-top:3px}.empty{text-align:center;padding:25px;color:#777}
@media(max-width:520px){.grid{grid-template-columns:1fr 1fr}.photo{height:125px}.card-body{padding:10px}.product-name{font-size:14px}.price{font-size:15px}.desc{font-size:11px}}
</style>

<style>
.footer-credit{margin:28px 0 18px;text-align:center;color:#888;font-size:12px;}
.footer-credit strong{font-weight:600;color:#666;}
</style>

<style>
.payment-options{
  display:flex;
  flex-direction:column;
  gap:10px;
  margin:8px 0 14px;
}
.payment-options label{
  display:flex;
  align-items:center;
  gap:10px;
  width:100%;
  box-sizing:border-box;
  padding:11px 14px;
  border:1px solid #ddd;
  border-radius:10px;
  cursor:pointer;
  background:#fff;
}
.payment-options input[type="radio"]{
  margin:0;
  width:18px;
  height:18px;
  flex:0 0 auto;
}
</style>
</head>
<body>

<header class="header">
  <img class="logo" id="logo" src="https://placehold.co/150x150/333/fff?text=LOGO" alt="Logo">
  <div class="business-name" id="businessName">Sabor da Casa</div>
  <div class="status">● Aberto agora</div>
  <div class="info" id="businessInfo">Seg a Dom • 11h às 23h • São Luís - MA</div>
</header>

<main class="container">
  <input class="search" id="search" placeholder="🔎 Procurar no cardápio..." oninput="renderProducts()">
  <div class="categories" id="categories"></div>
  <h2 class="section-title" id="sectionTitle">Cardápio</h2>
  <div class="grid" id="products"></div>
</main>

<div class="cart" onclick="openOrder()">
  <div><small id="cartCount">0 itens</small><br><strong>🛒 Ver pedido</strong></div>
  <strong id="cartTotal">R$ 0,00</strong>
</div>

<!-- Galeria -->
<div class="modal" id="galleryModal">
 <div class="modal-box" style="background:#111">
  <button class="close" onclick="closeGallery()">×</button>
  <div class="gallery"><img id="galleryImage"><div class="gallery-controls"><button onclick="galleryPrev()">‹</button><span id="galleryCounter">1 / 1</span><button onclick="galleryNext()">›</button></div></div>
 </div>
</div>

<!-- Produto -->
<div class="modal" id="productModal">
 <div class="modal-box">
  <button class="close" onclick="closeProduct()">×</button>
  <div class="gallery"><img id="productMainImage"></div>
  <div class="modal-content">
   <h2 id="productModalName"></h2><div id="productModalDesc" class="desc"></div>
   <div class="price" id="productModalPrice"></div>
   <h3>Adicionais</h3>
   <div id="addons"></div>
   <div class="modal-actions"><button class="secondary" onclick="closeProduct()">Cancelar</button><button class="primary" onclick="addFromModal()">Adicionar ao pedido</button></div>
  </div>
 </div>
</div>

<!-- Pedido -->
<div class="modal" id="orderModal">
 <div class="modal-box">
  <button class="close" onclick="closeOrder()">×</button>
  <div class="modal-content">
   <h2>🛒 Seu pedido</h2>
   <div id="orderItems"></div>
   <div class="form">
    <label>Seu nome</label><input id="customerName" placeholder="Digite seu nome">
    <label>Como receber?</label>
    <div class="choice">
      <label><input type="radio" name="mode" value="Entrega" checked onchange="updateDelivery()"><span>🛵 Entrega</span></label>
      <label><input type="radio" name="mode" value="Retirada" onchange="updateDelivery()"><span>🏪 Retirada</span></label>
    </div>
    <div id="deliveryFields">
      <label>Endereço</label><input id="address" placeholder="Rua, número, bairro">
      <label>Complemento</label><input id="complement" placeholder="Apartamento, ponto de referência...">
    </div>
    <label>💳 Como você vai pagar? <span style="color:#d00">*</span></label>
<div class="payment-options" id="paymentOptions">
  <label><input type="radio" name="payment" value="PIX"> PIX</label>
  <label><input type="radio" name="payment" value="Cartão na entrega/retirada"> Cartão na entrega/retirada</label>
  <label><input type="radio" name="payment" value="Dinheiro"> Dinheiro</label>
</div>
<div id="changeWrap" style="display:none;">
  <label>💵 Precisa de troco para quanto?</label>
  <input id="changeFor" type="text" inputmode="decimal" placeholder="Ex.: R$ 50,00">
</div>
<label>Observação</label><textarea id="observation" placeholder="Ex.: sem cebola, molho separado..."></textarea>
   </div>
   <div class="total-box">
     <div class="line"><span>Subtotal</span><strong id="subtotal">R$ 0,00</strong></div>
     <div class="line"><span>Taxa de entrega</span><strong id="deliveryFee">R$ 0,00</strong></div>
     <div class="line grand"><span>Total</span><strong id="grandTotal">R$ 0,00</strong></div>
   </div>
   <button class="primary" style="width:100%;margin-top:14px" onclick="openConfirmation()">📲 Conferir pedido e continuar</button>
  </div>
 </div>
</div>

<!-- Confirmação do pedido -->
<div class="modal" id="confirmModal">
 <div class="modal-box">
  <button class="close" onclick="closeConfirm()">×</button>
  <div class="modal-content">
   <h2>✅ Confira seu pedido</h2>
   <div id="confirmSummary"></div>
   <div class="total-box">
    <div class="line"><span>Subtotal</span><strong id="confirmSubtotal">R$ 0,00</strong></div>
    <div class="line"><span>Taxa de entrega</span><strong id="confirmFee">R$ 0,00</strong></div>
    <div class="line grand"><span>Total</span><strong id="confirmTotal">R$ 0,00</strong></div>
   </div>
   <div class="modal-actions">
    <button class="secondary" onclick="closeConfirm()">✏️ Alterar pedido</button>
    <button class="primary" onclick="confirmAndSend()">📲 Enviar pelo WhatsApp</button>
   </div>
  </div>
 </div>
</div>

<script>
/* ==========================================================
   CONFIGURAÇÃO RÁPIDA — para vender este modelo a clientes,
   altere principalmente esta parte.
   ========================================================== */
const CONFIG = {
  businessName: "Sabor da Casa",
  whatsapp: "5598999999999", // coloque o WhatsApp real com DDI + DDD
  logo: "https://placehold.co/150x150/333/fff?text=LOGO",
  info: "Seg a Dom • 11h às 23h • São Luís - MA",
  deliveryFee: 5.00,

  categories: ["Todos","Hambúrgueres","Porções","Bebidas"],

  products: [
    {
      id:1, name:"Hambúrguer Especial", category:"Hambúrgueres", price:25,
      desc:"Pão, carne artesanal, queijo, salada e molho especial.",
      photos:[
        "https://placehold.co/900x650/e63946/fff?text=Hambúrguer+1",
        "https://placehold.co/900x650/cb2d3e/fff?text=Hambúrguer+2",
        "https://placehold.co/900x650/8e1f2b/fff?text=Hambúrguer+3"
      ],
      addons:[["Bacon",5],["Queijo extra",3],["Ovo",2]]
    },
    {
      id:2, name:"Batata Frita", category:"Porções", price:12,
      desc:"Batata crocante, servida quentinha.",
      photos:[
        "https://placehold.co/900x650/f4a261/fff?text=Batata+1",
        "https://placehold.co/900x650/e9c46a/fff?text=Batata+2"
      ],
      addons:[["Cheddar",4],["Bacon",5]]
    },
    {
      id:3, name:"Refrigerante", category:"Bebidas", price:6,
      desc:"Lata 350 ml. Escolha a marca desejada.",
      photos:["https://placehold.co/900x650/457b9d/fff?text=Refrigerante"],
      addons:[{type:"required", name:"Qual refrigerante?", options:[["Coca-Cola",0],["Coca-Cola Zero",0],["Guaraná Antarctica",0],["Fanta Laranja",0],["Fanta Uva",0],["Sprite",0],["Pepsi",0]]}]
    },
    {
      id:4, name:"Suco Natural", category:"Bebidas", price:8,
      desc:"Suco natural preparado na hora.",
      photos:["https://placehold.co/900x650/2a9d8f/fff?text=Suco+Natural"],
      addons:[{type:"required", name:"Qual suco?", options:[["Laranja",0],["Acerola",0],["Maracujá",0],["Goiaba",0],["Abacaxi",0],["Caju",0],["Morango",0]]}]
    }
,
    {
      id:5, name:"X-Bacon", category:"Hambúrgueres", price:29,
      desc:"Pão brioche, carne artesanal, queijo, bacon crocante e molho da casa.",
      photos:[
        "https://placehold.co/900x650/6d597a/fff?text=X-Bacon+1",
        "https://placehold.co/900x650/5a4766/fff?text=X-Bacon+2"
      ],
      addons:[["Queijo extra",3],["Bacon extra",5],["Ovo",2]]
    },
    {
      id:6, name:"X-Salada", category:"Hambúrgueres", price:23,
      desc:"Carne, queijo, alface, tomate, milho e molho especial.",
      photos:["https://placehold.co/900x650/588157/fff?text=X-Salada"],
      addons:[["Bacon",5],["Queijo extra",3]]
    },
    {
      id:7, name:"Onion Rings", category:"Porções", price:18,
      desc:"Anéis de cebola empanados e crocantes.",
      photos:[
        "https://placehold.co/900x650/f6bd60/fff?text=Onion+Rings+1",
        "https://placehold.co/900x650/e09f3e/fff?text=Onion+Rings+2"
      ],
      addons:[["Cheddar",4],["Molho especial",2]]
    },
    {
      id:8, name:"Nuggets", category:"Porções", price:16,
      desc:"Porção com 10 unidades, crocantes por fora e macios por dentro.",
      photos:["https://placehold.co/900x650/bc6c25/fff?text=Nuggets"],
      addons:[["Molho barbecue",2],["Cheddar",4]]
    },
    {
      id:9, name:"Milk-shake Chocolate", category:"Bebidas", price:15,
      desc:"Milk-shake cremoso de chocolate com cobertura.",
      photos:[
        "https://placehold.co/900x650/7f5539/fff?text=Milk-shake+1",
        "https://placehold.co/900x650/9c6644/fff?text=Milk-shake+2"
      ],
      addons:[["Chantilly",2],["Nutella",4]]
    },
    {
      id:10, name:"Água Mineral", category:"Bebidas", price:4,
      desc:"Garrafa de água mineral 500 ml.",
      photos:["https://placehold.co/900x650/90caf9/fff?text=Água+Mineral"],
      addons:[]
    }
  ]
};

CONFIG.products.forEach(p => { if (typeof p.available !== "boolean") p.available = true; });
let cart = {};
let selectedCategory = "Todos";
let modalProduct = null;
let modalQty = 1;
let galleryProduct = null, galleryIndex = 0;

const money = v => v.toLocaleString("pt-BR",{style:"currency",currency:"BRL"});

document.getElementById("businessName").textContent=CONFIG.businessName;
document.getElementById("businessInfo").textContent=CONFIG.info;
document.getElementById("logo").src=CONFIG.logo;

function renderCategories(){
 const el=document.getElementById("categories");
 el.innerHTML=CONFIG.categories.map(c=>`<button class="cat ${c===selectedCategory?'active':''}" onclick="selectCategory('${c}')">${c}</button>`).join("");
}
function selectCategory(c){selectedCategory=c;renderCategories();renderProducts();}
function normalizeText(text){
 return text.toLowerCase()
   .normalize("NFD")
   .replace(/[\\u0300-\\u036f]/g,"")
   .replace(/[^a-z0-9 ]/g,"")
   .trim();
}

function searchMatch(product, term){
 if(!term) return true;

 const query=normalizeText(term);
 const name=normalizeText(product.name);
 const words=name.split(/\\s+/).filter(Boolean);

 // 1 ou 2 letras: procura pelo início de qualquer palavra do nome.
 if(query.length <= 2){
   return words.some(word => word.startsWith(query));
 }

 // A partir de 3 letras: procura no nome inteiro e também no início das palavras.
 return name.includes(query) || words.some(word => word.startsWith(query));
}

function renderProducts(){
 const term=document.getElementById("search").value;
 let list=CONFIG.products.filter(p=>(selectedCategory==="Todos"||p.category===selectedCategory)&&
   searchMatch(p, term));
 const el=document.getElementById("products");
 document.getElementById("sectionTitle").textContent=selectedCategory==="Todos"?"Cardápio":selectedCategory;
 if(!list.length){el.innerHTML='<div class="empty" style="grid-column:1/-1">Nenhum produto encontrado.</div>';return}
 el.innerHTML=list.map(p=>{
   const q=cart[p.id]?.qty||0;
   const soldOut=p.available===false;
   return `<div class="card ${soldOut?'sold-out':''}">
    <div class="photo" onclick="openGallery(${p.id})"><img src="${p.photos[0]}" alt="${p.name}"><span class="zoom">🔍 Ver fotos</span>${soldOut?'<span class="sold-badge">ESGOTADO</span>':''}</div>
    <div class="card-body"><div class="product-name">${p.name}</div><div class="desc">${p.desc}</div><div class="price">${money(p.price)}</div>
    ${soldOut?'<div class="unavailable">Produto indisponível</div>':`<div class="qty"><button onclick="changeQty(${p.id},-1)">−</button><span>${q}</span><button onclick="openProduct(${p.id})">+</button></div>`}
    </div></div>`;
 }).join("");
}
function changeQty(id,d){
 const product=CONFIG.products.find(p=>p.id==id);
 if(product && product.available===false){alert("Este produto está esgotado no momento.");return}
 if(!cart[id])cart[id]={qty:0,addons:[]};
 cart[id].qty=Math.max(0,cart[id].qty+d);
 if(cart[id].qty===0)delete cart[id];
 updateCart();renderProducts();
}
function openProduct(id){
 modalProduct=CONFIG.products.find(p=>p.id===id);modalQty=1;
 if(!modalProduct || modalProduct.available===false){alert("Este produto está esgotado no momento.");return}
 document.getElementById("productMainImage").src=modalProduct.photos[0];
 document.getElementById("productModalName").textContent=modalProduct.name;
 document.getElementById("productModalDesc").textContent=modalProduct.desc;
 document.getElementById("productModalPrice").textContent=money(modalProduct.price);
 document.getElementById("addons").innerHTML=modalProduct.addons.length
 ? modalProduct.addons.map((a,i)=>{
     if(a.type==="required") return `<div class="addon-group"><strong>${a.name}</strong>${a.options.map((o,j)=>`<label class="addon-option"><input type="radio" name="addonGroup${i}" id="addon${i}_${j}" value="${o[1]}" data-name="${o[0]}" required> ${o[0]}${o[1]?` <span>+ ${money(o[1])}</span>`:""}</label>`).join("")}</div>`;
     return `<div class="addon"><label><input type="checkbox" id="addon${i}" value="${a[1]}" data-name="${a[0]}"> ${a[0]}</label><strong>+ ${money(a[1])}</strong></div>`;
   }).join("")
 : '<div class="desc">Este produto não possui adicionais.</div>';
 document.getElementById("productModal").classList.add("show");
}
function closeProduct(){document.getElementById("productModal").classList.remove("show")}
function addFromModal(){
 let adds=[];
 for(let i=0;i<modalProduct.addons.length;i++){
   const a=modalProduct.addons[i];
   if(a.type==="required"){
     const c=document.querySelector(`input[name="addonGroup${i}"]:checked`);
     if(!c){alert(`Escolha: ${a.name}`);return;}
     adds.push({name:c.dataset.name,price:Number(c.value)});
   }else{
     const c=document.getElementById("addon"+i);
     if(c&&c.checked)adds.push({name:a[0],price:a[1]});
   }
 }
 let key=modalProduct.id;
 if(!cart[key])cart[key]={qty:0,addons:[]};
 cart[key].qty++;
 cart[key].addons.push(adds);
 closeProduct();updateCart();renderProducts();
}
function openGallery(id){galleryProduct=CONFIG.products.find(p=>p.id===id);galleryIndex=0;showGallery();document.getElementById("galleryModal").classList.add("show")}
function showGallery(){document.getElementById("galleryImage").src=galleryProduct.photos[galleryIndex];document.getElementById("galleryCounter").textContent=`${galleryIndex+1} / ${galleryProduct.photos.length}`}
function galleryNext(){galleryIndex=(galleryIndex+1)%galleryProduct.photos.length;showGallery()}
function galleryPrev(){galleryIndex=(galleryIndex-1+galleryProduct.photos.length)%galleryProduct.photos.length;showGallery()}
function closeGallery(){document.getElementById("galleryModal").classList.remove("show")}

function updateCart(){
 let count=0,total=0;
 Object.entries(cart).forEach(([id,x])=>{
   const p=CONFIG.products.find(p=>p.id==id);count+=x.qty;
   x.addons.forEach(a=>a.forEach(z=>total+=z.price));
   total+=p.price*x.qty;
 });
 document.getElementById("cartCount").textContent=`${count} ${count===1?'item':'itens'}`;
 document.getElementById("cartTotal").textContent=money(total);
}
function subtotal(){
 let total=0;
 Object.entries(cart).forEach(([id,x])=>{
   const p=CONFIG.products.find(p=>p.id==id);total+=p.price*x.qty;
   x.addons.forEach(a=>a.forEach(z=>total+=z.price));
 });
 return total;
}
function openOrder(){
 if(!Object.keys(cart).length){alert("Seu pedido está vazio. Adicione pelo menos um produto para continuar.");return}
 renderOrder();document.getElementById("orderModal").classList.add("show")
}
function closeOrder(){document.getElementById("orderModal").classList.remove("show")}
function renderOrder(){
 const el=document.getElementById("orderItems");
 if(!Object.keys(cart).length){el.innerHTML='<div class="empty">Seu pedido está vazio.</div>';return}
 el.innerHTML=Object.entries(cart).map(([id,x])=>{
   const p=CONFIG.products.find(p=>p.id==id);
   let details=x.addons.map(a=>a.length?a.map(z=>z.name).join(", "):"").filter(Boolean);
   return `<div class="order-item"><div class="order-row"><strong>${x.qty}x ${p.name}</strong><strong>${money(p.price*x.qty)}</strong></div>
   ${details.length?`<div class="desc">Adicionais: ${details.join(" | ")}</div>`:""}
   <div class="order-controls"><button class="mini" onclick="changeQty(${id},-1);renderOrder()">−</button><span>${x.qty}</span><button class="mini" onclick="changeQty(${id},1);renderOrder()">+</button><button class="mini" onclick="delete cart[${id}];updateCart();renderOrder();renderProducts()">🗑</button></div></div>`;
 }).join("");
 let sub=subtotal(), fee=getMode()==="Entrega"?CONFIG.deliveryFee:0;
 document.getElementById("subtotal").textContent=money(sub);
 document.getElementById("deliveryFee").textContent=money(fee);
 document.getElementById("grandTotal").textContent=money(sub+fee);
}
function getMode(){return document.querySelector('input[name="mode"]:checked')?.value||"Entrega"}
function updateDelivery(){document.getElementById("deliveryFields").style.display=getMode()==="Entrega"?"block":"none";renderOrder()}
function toggleChange(){document.getElementById("changeField").style.display=document.getElementById("payment").value==="Dinheiro"?"block":"none"}
function openConfirmation(){
 if(!Object.keys(cart).length){alert("Seu pedido está vazio. Adicione pelo menos um produto para continuar.");return}
 const summary=document.getElementById("confirmSummary");
 summary.innerHTML=Object.entries(cart).map(([id,x])=>{
   const p=CONFIG.products.find(p=>p.id==id); let out="";
   for(let i=0;i<x.qty;i++){ const adds=x.addons[i]||[]; out+=`<div class="confirm-item"><strong>${p.name}</strong> — ${money(p.price)}${adds.length?`<small>Adicionais: ${adds.map(a=>a.name).join(", ")}</small>`:""}</div>`; }
   return out;
 }).join("");
 const sub=subtotal(), fee=getMode()==="Entrega"?CONFIG.deliveryFee:0;
 document.getElementById("confirmSubtotal").textContent=money(sub);
 document.getElementById("confirmFee").textContent=money(fee);
 document.getElementById("confirmTotal").textContent=money(sub+fee);
 document.getElementById("confirmModal").classList.add("show");
}
function closeConfirm(){document.getElementById("confirmModal").classList.remove("show")}
function confirmAndSend(){closeConfirm();sendWhatsApp()}

function sendWhatsApp(){
 if(!Object.keys(cart).length){alert("Adicione pelo menos um item ao pedido.");return}
 const name=document.getElementById("customerName").value.trim();
 const mode=getMode(),payment=document.querySelector('input[name="payment"]:checked')?.value||"";
 if(!name){alert("Digite seu nome.");return}
 if(mode==="Entrega"&&!document.getElementById("address").value.trim()){alert("Digite o endereço para entrega.");return}
 if(!payment){alert("Selecione a forma de pagamento.");return}
 let msg=`*NOVO PEDIDO* 🍔\n\n*Cliente:* ${name}\n*Recebimento:* ${mode}\n`;
 if(mode==="Entrega"){
   msg+=`*Endereço:* ${document.getElementById("address").value.trim()}\n`;
   const comp=document.getElementById("complement").value.trim();if(comp)msg+=`*Complemento:* ${comp}\n`;
 }
 msg+=`\n*ITENS:*\n`;
 Object.entries(cart).forEach(([id,x])=>{
   const p=CONFIG.products.find(p=>p.id==id);
   for(let i=0;i<x.qty;i++){
     msg+=`• ${p.name} — ${money(p.price)}`;
     const adds=x.addons[i]||[];
     if(adds.length)msg+=` + ${adds.map(a=>`${a.name} (${money(a.price)})`).join(", ")}`;
     msg+="\n";
   }
 });
 let sub=subtotal(),fee=mode==="Entrega"?CONFIG.deliveryFee:0,total=sub+fee;
 msg+=`\n*Subtotal:* ${money(sub)}\n*Taxa de entrega:* ${money(fee)}\n*TOTAL:* ${money(total)}\n*Pagamento:* ${payment}\n`;
 const changeValue=document.getElementById("changeFor")?.value.trim()||"";
 if(payment==="Dinheiro"&&changeValue)msg+=`*Troco para:* ${changeValue}\n`;
 const obs=document.getElementById("observation").value.trim();if(obs)msg+=`*Observação:* ${obs}\n`;
 msg+=`\nAguardo a confirmação do pedido.`;
 window.open(`https://wa.me/${CONFIG.whatsapp}?text=${encodeURIComponent(msg)}`,"_blank");
}
renderCategories();renderProducts();updateCart();
</script>

<footer class="footer-credit">Feito por <strong>Leydson Ferreira</strong></footer>

<script>
(function(){
  const radios=document.querySelectorAll('input[name="payment"]');
  const wrap=document.getElementById('changeWrap');
  const change=document.getElementById('changeFor');
  radios.forEach(r=>r.addEventListener('change',()=>{
    const show=document.querySelector('input[name="payment"]:checked')?.value==='Dinheiro';
    if(wrap) wrap.style.display=show?'block':'none';
    if(!show && change) change.value='';
  }));
})();
</script>



</body>
</html>
