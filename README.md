# pizzeria-nefeli

<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Πιτσαρία ΝΕΦΕΛΗ</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#fff8ef;color:#29231f}
header{background:#a51d20;color:white;text-align:center;padding:25px 12px}
header h1{font-size:36px;margin:5px}
header p{margin:8px}
.offer{background:#ffca55;color:#29231f;padding:12px;text-align:center;font-weight:bold}
main{max-width:850px;margin:auto;padding:16px}
h2{border-bottom:2px solid #a51d20;padding-bottom:8px}
.pizza{background:white;border-radius:12px;padding:14px;margin:12px 0;box-shadow:0 2px 8px #0001}
.pizza h3{margin:0 0 8px}
.desc{color:#68605a;font-size:14px}
.prices{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
button{border:0;border-radius:8px;padding:11px;background:#a51d20;color:white;font-weight:bold;cursor:pointer}
button:active{opacity:.8}
.prices button{flex:1;min-width:130px}
.cart,.order{background:white;border-radius:12px;padding:16px;margin:22px 0}
input,select,textarea{width:100%;padding:12px;margin:7px 0 12px;border:1px solid #ccc;border-radius:7px;font-size:16px}
.cart-item{display:flex;justify-content:space-between;gap:8px;margin:10px 0}
.remove{padding:5px 9px;background:#555}
.total{font-size:22px;font-weight:bold}
.submit{width:100%;font-size:17px;background:#287844}
footer{background:#29231f;color:white;text-align:center;padding:24px;line-height:1.8}
a{color:inherit}
</style>
</head>
<body>

<header>
  <div style="font-size:42px">🍕</div>
  <h1>ΝΕΦΕΛΗ</h1>
  <p>Πιτσαρία • Φρέσκια γεύση σε κάθε μπουκιά!</p>
  <p>☎ 26810 88719 · 6971618144</p>
</header>

<div class="offer">🎉 ΠΡΟΣΦΟΡΑ: 4+1 ΠΙΤΣΑ ΔΩΡΕΑΝ!</div>

<main>
<h2>🍕 Οι πίτσες μας</h2>
<p>Διάλεξε ατομική ή κανονική πίτσα και πρόσθεσέ την στο καλάθι σου.</p>
<div id="menu"></div>

<section class="cart">
<h2>🛒 Το καλάθι σου</h2>
<div id="items">Δεν έχεις προσθέσει προϊόντα.</div>
<p id="promo"></p>
<p class="total">Σύνολο: <span id="total">0,00 €</span></p>
</section>

<section class="order">
<h2>📝 Στοιχεία παραγγελίας</h2>
<form id="orderForm">
<label>Ονοματεπώνυμο</label>
<input id="customer" required placeholder="Το όνομά σου">

<label>Τηλέφωνο</label>
<input id="phone" required type="tel" placeholder="Το τηλέφωνό σου">

<label>Τρόπος παραλαβής</label>
<select id="delivery">
<option value="Παραλαβή από το κατάστημα">Παραλαβή από το κατάστημα</option>
<option value="Delivery">Delivery</option>
</select>

<div id="addressBox" style="display:none">
<label>Διεύθυνση παράδοσης</label>
<input id="address" placeholder="Οδός, αριθμός, περιοχή">
</div>

<label>Πληρωμή</label>
<select id="payment">
<option>Μετρητά</option>
<option>Κάρτα κατά την παραλαβή</option>
<option disabled>Online κάρτα — σύντομα διαθέσιμο</option>
</select>

<label>Σχόλια για την παραγγελία</label>
<textarea id="notes" rows="3" placeholder="Π.χ. χωρίς μανιτάρια"></textarea>

<button class="submit" type="submit">Συνέχεια παραγγελίας</button>
<p id="message"></p>
</form>
</section>
</main>

<footer>
<strong>ΠΙΤΣΑΡΙΑ ΝΕΦΕΛΗ</strong><br>
☎ <a href="tel:2681088719">26810 88719</a><br>
☎ <a href="tel:6971618144">6971618144</a><br>
Συκούλα, Αιτωλοακαρνανίας
</footer>

<script>
const pizzas = [
["Μαργαρίτα","Τυρί, σάλτσα ντομάτας",4,5.5],
["Ζαμπόν – Τυρί","Τυρί, ζαμπόν, σάλτσα ντομάτας",4.5,6],
["Τεμπέλη","Τυρί, πράσο, σάλτσα ντομάτας",4.5,6],
["Βεζούβιος 🌶️","Ντομάτα, Κρανίδι, πιπεριά, Tabasco",4.5,6],
["Σπέσιαλ","Τυρί, ζαμπόν, μανιτάρια, πιπεριά, πεπερόνι, μπέικον",5.5,6.5],
["Καρμπονάρα Λευκή","Τυρί, ζαμπόν, μπέικον, κρέμα γάλακτος, χωρίς σάλτσα ντομάτας",4.5,6],
["Καρμπονάρα","Τυρί, ζαμπόν, μπέικον, κρέμα γάλακτος",4.5,6],
["BBQ","Σάλτσα BBQ, κοτομπουκιές, μπέικον",5.5,6.5],
["Χωριάτικη","Τυρί, φέτα, ελιές, ντομάτα, μανιτάρια, κρεμμύδι, πιπεριά",4.5,6],
["Μπολονέζ","Τυρί, φέτα, κιμάς",5.5,6.5],
["Τέσσερα Τυριά","Mozzarella, φέτα, Regato, Gouda",4.5,6]
];

let cart = [];

const money = n => n.toLocaleString("el-GR", {
  minimumFractionDigits:2, maximumFractionDigits:2
}) + " €";

document.getElementById("menu").innerHTML = pizzas.map((p,i)=>`
  <article class="pizza">
    <h3>${p[0]}</h3>
    <div class="desc">${p[1]}</div>
    <div class="prices">
      <button type="button" onclick="add(${i},0)">
        Ατομική ${money(p[2])} +
      </button>
      <button type="button" onclick="add(${i},1)">
        Κανονική ${money(p[3])} +
      </button>
    </div>
  </article>
`).join("");

function add(i,size){
  cart.push({
    name:pizzas[i][0],
    size:size===0?"Ατομική":"Κανονική",
    price:pizzas[i][size+2],
    free:false
  });
  renderCart();
}

function renderCart(){
  // Κάθε 5 πίτσες, η φθηνότερη από τις 5 είναι δωρεάν.
  const sorted = cart.map((x,i)=>({...x,index:i}))
    .sort((a,b)=>a.price-b.price);
  sorted.forEach(x=>x.free=false);
  for(let start=0;start+4<sorted.length;start+=5){
    sorted[start].free=true;
  }
  const freeIndexes = new Set(sorted.filter(x=>x.free).map(x=>x.index));
  const total = cart.reduce((sum,x,i)=>
    sum+(freeIndexes.has(i)?0:x.price),0);

  document.getElementById("items").innerHTML = cart.length
    ? cart.map((x,i)=>`
      <div class="cart-item">
        <span>${x.name} (${x.size}) — ${
          freeIndexes.has(i)
          ? '<strong>ΔΩΡΕΑΝ</strong>'
          : money(x.price)
        }</span>
        <button class="remove" type="button"
          onclick="removeItem(${i})">✕</button>
      </div>`).join("")
    : "Δεν έχεις προσθέσει προϊόντα.";

  document.getElementById("promo").textContent =
    freeIndexes.size
    ? "🎉 Εφαρμόστηκε η προσφορά 4+1 στις πίτσες!"
    : "Πρόσθεσε 5 πίτσες για να εφαρμοστεί η προσφορά.";

  document.getElementById("total").textContent=money(total);
}

function removeItem(i){
  cart.splice(i,1);
  renderCart();
}

document.getElementById("delivery").addEventListener("change",e=>{
  const isDelivery=e.target.value==="Delivery";
  document.getElementById("addressBox").style.display=
    isDelivery?"block":"none";
  document.getElementById("address").required=isDelivery;
});

document.getElementById("orderForm").addEventListener("submit",e=>{
  e.preventDefault();
  if(!cart.length){
    document.getElementById("message").textContent=
      "Πρόσθεσε πρώτα προϊόντα στο καλάθι.";
    return;
  }
  document.getElementById("message").textContent=
    "Η φόρμα λειτουργεί ως δοκιμή, αλλά η παραγγελία δεν έχει σταλεί στο κατάστημα. Χρειάζεται σύνδεση με σύστημα παραγγελιών.";
});
</script>
</body>
</html>
