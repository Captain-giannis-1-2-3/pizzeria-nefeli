
<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Πιτσαρία ΝΕΦΕΛΗ</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#fff8ef;color:#29231f}
header{background:#941d24;color:white;text-align:center;padding:28px 15px}
header h1{font-size:38px;margin:8px}
header p{margin:7px}
.offer{background:#ffca55;text-align:center;padding:14px;font-weight:bold}
nav{display:flex;gap:8px;overflow-x:auto;padding:12px;background:#29231f}
nav a{color:white;text-decoration:none;white-space:nowrap;padding:8px}
main{max-width:850px;margin:auto;padding:15px}
h2{color:#941d24;border-bottom:2px solid #941d24;padding-bottom:9px;margin-top:30px}
.item{background:white;border-radius:12px;padding:15px;margin:12px 0;box-shadow:0 2px 8px #0001}
.item h3{margin:0 0 7px}
.desc{font-size:14px;color:#69615b;line-height:1.5}
.price{font-weight:bold;color:#941d24;margin-top:9px}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
button{border:0;border-radius:8px;background:#941d24;color:white;padding:11px 14px;font-weight:bold;cursor:pointer}
button:active{opacity:.8}
.actions button{flex:1}
.cart,.order{background:white;border-radius:12px;padding:16px;margin:25px 0}
.cart-row{display:flex;justify-content:space-between;gap:10px;margin:12px 0;border-bottom:1px solid #eee;padding-bottom:8px}
.remove{background:#555;padding:6px 10px}
.total{font-size:22px;font-weight:bold}
input,select,textarea{width:100%;padding:12px;margin:7px 0 14px;border:1px solid #ccc;border-radius:7px;font-size:16px}
.submit{width:100%;background:#287844;font-size:17px}
footer{background:#29231f;color:white;text-align:center;padding:25px;line-height:2}
footer a{color:white}
.small{font-size:13px;color:#777}
</style>
</head>
<body>

<header>
<div style="font-size:42px">🍕</div>
<h1>ΝΕΦΕΛΗ</h1>
<p>ΠΙΤΣΑΡΙΑ</p>
<p>☎ 26810 88719 | 6971618144</p>
</header>

<div class="offer">🎉 4+1 ΔΩΡΕΑΝ ΣΕ ΟΛΕΣ ΤΙΣ ΠΙΤΣΕΣ!</div>

<nav>
<a href="#pizzas">Πίτσες</a>
<a href="#salads">Σαλάτες</a>
<a href="#pasta">Μακαρονάδες</a>
<a href="#starters">Ορεκτικά</a>
<a href="#drinks">Αναψυκτικά</a>
<a href="#beers">Μπύρες</a>
<a href="#cart">Καλάθι</a>
</nav>

<main>
<div id="pizzas">
<h2>🍕 Πίτσες – Καλτσόνε – Πεϊνερλί</h2>
<p>Όλες οι παρακάτω γεύσεις διατίθενται και ως καλτσόνε ή πεϊνερλί.</p>
<div id="pizzaList"></div>
</div>

<div id="salads">
<h2>🥗 Σαλάτες</h2>
<div id="saladList"></div>
</div>

<div id="pasta">
<h2>🍝 Μακαρονάδες</h2>
<p class="small">Όλες οι μακαρονάδες διατίθενται και στον φούρνο.</p>
<div id="pastaList"></div>
</div>

<div id="starters">
<h2>🍟 Ορεκτικά – Μερίδες</h2>
<div id="starterList"></div>
</div>

<div id="drinks">
<h2>🥤 Αναψυκτικά</h2>
<div id="drinkList"></div>
</div>

<div id="beers">
<h2>🍺 Μπύρες</h2>
<div id="beerList"></div>
</div>

<section class="cart" id="cart">
<h2>🛒 Το καλάθι σου</h2>
<div id="cartItems">Το καλάθι είναι άδειο.</div>
<p id="promoMessage"></p>
<p class="total">Σύνολο: <span id="total">0,00 €</span></p>
</section>

<section class="order">
<h2>📝 Παραγγελία</h2>
<form id="orderForm">
<label>Ονοματεπώνυμο</label>
<input id="customer" required placeholder="Το όνομά σου">

<label>Τηλέφωνο</label>
<input id="phone" type="tel" required placeholder="Το τηλέφωνό σου">

<label>Παραλαβή</label>
<select id="delivery">
<option value="Παραλαβή από το κατάστημα">Παραλαβή από το κατάστημα</option>
<option value="Delivery">Delivery</option>
</select>

<div id="addressBox" hidden>
<label>Διεύθυνση παράδοσης</label>
<input id="address" placeholder="Οδός, αριθμός, περιοχή">
</div>

<label>Τρόπος πληρωμής</label>
<select id="payment">
<option>Μετρητά</option>
<option>Κάρτα κατά την παραλαβή</option>
</select>

<label>Σχόλια</label>
<textarea id="notes" rows="3" placeholder="Σημειώσεις για την παραγγελία"></textarea>

<button class="submit" type="submit">Ολοκλήρωση παραγγελίας</button>
<p id="message"></p>
</form>
</section>
</main>

<footer>
<strong>ΠΙΤΣΑΡΙΑ ΝΕΦΕΛΗ</strong><br>
Τηλέφωνο:
<a href="tel:2681088719">26810 88719</a><br>
Κινητό:
<a href="tel:6971618144">6971618144</a><br>
Συκούλα, Αιτωλοακαρνανίας
</footer>

<script>
const pizzas=[
["Μαργαρίτα","Τυρί, σάλτσα ντομάτας",4,5.5],
["Ζαμπόν – Τυρί","Τυρί, ζαμπόν, σάλτσα",4.5,6],
["Τεμπέλη","Τυρί, πατάτες, σάλτσα",4.5,6],
["Βεζούβιος","Τυρί, ντομάτα, κρεμμύδι, πιπεριά, Tabasco",4.5,6],
["4 Τυριά","Mozzarella, φέτα, Regato, Gouda",4.5,6],
["Χωριάτικη","Τυρί, φέτα, ελιές, ντομάτα, μανιτάρια, κρεμμύδι, πιπεριά",4.5,6],
["Μπολονέζ","Τυρί, φέτα, κιμάς",5.5,6.5],
["Σπέσιαλ","Τυρί, ζαμπόν, μπέικον, μανιτάρια, πεπερόνι, πιπεριά",5.5,6.5],
["Καρμπονάρα","Τυρί, ζαμπόν, μπέικον, σάλτσα",4.5,6],
["Καρμπονάρα Λευκή","Τυρί, ζαμπόν, μπέικον, κρέμα γάλακτος",4.5,6],
["BBQ","Σάλτσα BBQ, κοτομπουκιές, μπέικον",5.5,6.5]
];

const salads=[
["Ceasar’s","Μαρούλι, ντοματίνια, παρμεζάνα, κοτόπουλο, κρουτόν",4.5],
["Μακαρονοσαλάτα","Πένες, καλαμπόκι, πιπεριά, ζαμπόν, σως",4],
["Τονοσαλάτα","Μαρούλι, καλαμπόκι, τόνος, dressing",4.5],
["Σαλάτα Chef","Μαρούλι, ντοματίνια, αγγούρι, τυρί, ζαμπόν, αυγό, σως",4.5],
["Ρόκα Παρμεζάνα","Ρόκα, ντοματίνια, παρμεζάνα, κρέμα βαλσάμικο",4]
];

const pastas=[
["Ναπολιτάνα","Σάλτσα ντομάτας",4.5],
["Μπολονέζ","Κιμάς",5.5],
["Κοτόπουλο με παρμεζάνα","Μακαρονάδα με κοτόπουλο και παρμεζάνα",5.5],
["Καρμπονάρα","",5.5],
["Ροζέ","Τυρί, ζαμπόν, μπέικον, σάλτσα ντομάτας, κρέμα γάλακτος",5]
];

const starters=[
["Φλογέρες Mozzarella","3 τεμάχια",3],
["Φλογέρες Ζαμπόν","3 τεμάχια",3.5],
["Σκορδόψωμο","Τυρί, πάστα σκόρδου",3.5],
["Σκορδόψωμο σκεπαστό","",3],
["Σκορδόψωμο με φέτα","Τυρί, φέτα, ντομάτα, πάστα σκόρδου, ρίγανη",4],
["Φέτα σαγανάκι","Φύλλο κρούστας, τυρί φέτα",4],
["Κοτομπουκιές","Σερβίρονται με πατάτες",4.5],
["Πατάτες τηγανητές","",3],
["Πατάτες με cheddar και bacon","",4],
["Πατάτες με κιμά","",3.5]
];

const drinks=[
["Coca-Cola 330ml",1.5],
["Coca-Cola 500ml",2],
["Coca-Cola Zero 330ml",1.5],
["Coca-Cola Zero 500ml",2],
["Sprite 330ml",1.5],
["Πορτοκαλάδα χωρίς ανθρακικό 330ml",1.5],
["Λεμονάδα 330ml",1.5],
["Σόδα 330ml",1.5]
];

const beers=[
["Μπύρα 330ml (Heineken, Kaiser, Fix Άνευ)",2.3],
["Μπύρα 500ml (Άλφα, Amstel, Βεργίνα)",2.5]
];

let cart=[];

const money=n=>n.toLocaleString("el-GR",{
 minimumFractionDigits:2,maximumFractionDigits:2
})+" €";

function showPizzas(){
 document.getElementById("pizzaList").innerHTML=pizzas.map((p,i)=>`
 <article class="item">
 <h3>${p[0]}</h3><div class="desc">${p[1]}</div>
 <div class="actions">
 <button onclick="addPizza(${i},0,'Πίτσα')">Πίτσα Ατομική ${money(p[2])}</button>
 <button onclick="addPizza(${i},1,'Πίτσα')">Πίτσα Οικογενειακή ${money(p[3])}</button>
 </div>
 <div class="actions">
 <button onclick="addPizza(${i},0,'Καλτσόνε')">Καλτσόνε Ατομικό ${money(p[2])}</button>
 <button onclick="addPizza(${i},1,'Καλτσόνε')">Καλτσόνε Οικογενειακό ${money(p[3])}</button>
 </div>
 <div class="actions">
 <button onclick="addPizza(${i},0,'Πεϊνερλί')">Πεϊνερλί Ατομικό ${money(p[2])}</button>
 <button onclick="addPizza(${i},1,'Πεϊνερλί')">Πεϊνερλί Οικογενειακό ${money(p[3])}</button>
 </div>
 </article>`).join("");
}

function showSimple(list,id){
 document.getElementById(id).innerHTML=list.map((p,i)=>`
 <article class="item">
 <h3>${p[0]}</h3>
 <div class="desc">${p[1]||""}</div>
 <div class="price">${money(p[2])}</div>
 <div class="actions"><button onclick="addSimple('${id}',${i})">Προσθήκη</button></div>
 </article>`).join("");
}

function showDrinks(list,id){
 document.getElementById(id).innerHTML=list.map((p,i)=>`
 <article class="item">
 <h3>${p[0]}</h3>
 <div class="price">${money(p[1])}</div>
 <div class="actions"><button onclick="addDrink('${id}',${i})">Προσθήκη</button></div>
 </article>`).join("");
}

function addPizza(i,size,type){
 cart.push({
 name:type+" "+pizzas[i][0],
 size:size===0?"Ατομικό":"Οικογενειακό",
 price:pizzas[i][size+2],
 pizza:true
 });
 renderCart();
}

function addSimple(id,i){
 const list=id==="saladList"?salads:
 id==="pastaList"?pastas:starters;
 cart.push({name:list[i][0],size:"",price:list[i][2],pizza:false});
 renderCart();
}

function addDrink(id,i){
 const list=id==="drinkList"?drinks:beers;
 cart.push({name:list[i][0],size:"",price:list[i][1],pizza:false});
 renderCart();
}

function renderCart(){
 let pizzaCount=0,total=0,freeCount=0;
 const rows=cart.map((item,i)=>{
   let free=false;
   if(item.pizza){
     pizzaCount++;
     free=pizzaCount%5===0;
   }
   if(free)freeCount++;
   else total+=item.price;
   return `<div class="cart-row">
     <span>${item.name} ${item.size}
     — ${free?"🎁 ΔΩΡΕΑΝ":money(item.price)}</span>
     <button class="remove" onclick="removeItem(${i})">✕</button>
   </div>`;
 }).join("");

 document.getElementById("cartItems").innerHTML=
 rows||"Το καλάθι είναι άδειο.";
 document.getElementById("total").textContent=money(total);
 document.getElementById("promoMessage").textContent=
 freeCount?"🎉 Εφαρμόστηκε η προσφορά 4+1!":
 "Η προσφορά εφαρμόζεται σε κάθε 5 πίτσες. Δεν αφορά άλλα προϊόντα.";
}

function removeItem(i){
 cart.splice(i,1);
 renderCart();
}

showPizzas();
showSimple(salads,"saladList");
showSimple(pastas,"pastaList");
showSimple(starters,"starterList");
showDrinks(drinks,"drinkList");
showDrinks(beers,"beerList");
renderCart();

document.getElementById("delivery").addEventListener("change",e=>{
 const yes=e.target.value==="Delivery";
 document.getElementById("addressBox").hidden=!yes;
 document.getElementById("address").required=yes;
});

document.getElementById("orderForm").addEventListener("submit",e=>{
 e.preventDefault();
 if(!cart.length){
  document.getElementById("message").textContent=
  "Πρόσθεσε πρώτα προϊόντα στο καλάθι.";
  return;
 }
 document.getElementById("message").textContent=
 "Η φόρμα είναι δοκιμαστική. Η παραγγελία δεν έχει σταλεί στο κατάστημα. Χρειάζεται σύνδεση με ασφαλές σύστημα παραγγελιών.";
});
</script>
</body>
</html>

