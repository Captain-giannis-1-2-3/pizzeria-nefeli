 
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
const SUPABASE_URL = "ΒΑΛΕ_ΕΔΩ_PROJECT_URL";https://ehngprmfejfvhawpxlqx.supabase.co
const SUPABASE_KEY = "ΒΑΛΕ_ΕΔΩ_PUBLISHABLE_KEY";sb_publishable_QCfaXHe94oDEBAlJ2f36TQ_FQFPV1oZ

const db = window.supabase.createClient(
  SUPABASE_URL, 
  SUPABASE_KEY
);
</script>

<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Πιτσαρία Καφέ ΝΕΦΕΛΗ</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#fff8ef;color:#29211c;font-family:Arial,sans-serif}
header{background:#8d1717;color:white;text-align:center;padding:22px}
header img{width:190px;max-height:150px;object-fit:contain;background:white;padding:5px;border-radius:5px}
header h1{margin:12px 0 5px}
.offer{background:#ffcf45;text-align:center;padding:14px;font-weight:bold;font-size:19px}
main{max-width:850px;margin:auto;padding:15px}
h2{color:#8d1717;border-bottom:2px solid #e4c5a7;padding-bottom:8px;margin-top:28px}
.product,.cart{background:white;padding:14px;margin:12px 0;border-radius:10px;box-shadow:0 2px 7px #0001}
.product h3{margin:0 0 7px}
.desc{font-size:14px;color:#766b63;margin-bottom:10px}
.actions{display:flex;flex-wrap:wrap;gap:7px}
button{background:#8d1717;color:white;border:0;border-radius:7px;padding:10px;cursor:pointer;font-weight:bold}
button:hover{opacity:.85}
input,select,textarea{width:100%;padding:12px;margin:7px 0;border:1px solid #ccc;border-radius:7px;font-size:15px}
textarea{min-height:70px}
.item{display:flex;justify-content:space-between;gap:8px;padding:9px 0;border-bottom:1px solid #eee}
.item span{flex:1}
.remove{background:#555}
.total{font-size:21px;font-weight:bold;margin:16px 0}
.submit{width:150%;background:#218838;padding:14px;font-size:17px}
footer{background:#29211c;color:white;text-align:center;padding:25px;line-height:1.8;margin-top:30px}
</style>
</head>
<body>

<header>
<img src="FB_IMG_1792954368125.jpg" alt="Λογότυπο ΝΕΦΕΛΗ">
<h1>ΠΙΤΣΑΡΙΑ Καφέ ΝΕΦΕΛΗ</h1>
<p>Καλώς ήρθατε! η αριθμη τηλεφώνου είναι για να κλείσετε τραπέζης στο μαγαζί </p>
</header>

<div class="offer">🍕 4+1 ΔΩΡΟ </div>

<main>
<h2>🍕 Πίτσες – Καλτσόνε – Πεϊνερλί</h2>
<div id="pizzas"></div>

<h2>🥗 Σαλάτες</h2><div id="salads"></div>
<h2>🍝 Ζυμαρικά</h2><div id="pastas"></div>
<h2>🍟 Ορεκτικά</h2><div id="starters"></div>
<h2>🥤 Αναψυκτικά και μπύρες</h2><div id="drinks"></div>

<section class="cart">
<h2>🛒 Το καλάθι μου</h2>
<div id="cart">Το καλάθι είναι άδειο.</div>
<div class="total" id="total">Σύνολο: 0,00 €</div>
<p id="promoInfo"></p>

<h2>📦 Στοιχεία παραγγελίας</h2>
<form id="orderForm">
<input id="customer" placeholder="Ονοματεπώνυμο" required>
<input id="phone" type="tel" placeholder="Τηλέφωνο" required>
<select id="delivery" required>
<option value="">Τρόπος παραγγελίας</option>
<option>Παραλαβή από το κατάστημα</option>
<option>Delivery</option>
</select>
<input id="address" placeholder="Διεύθυνση για delivery">
<select id="payment" required>
<option value="">Τρόπος πληρωμής</option>
<option>Μετρητά</option>
<option>Ηλεκτρονική πληρωμή</option>
</select>
<textarea id="notes" placeholder="Σχόλια"></textarea>
<button class="submit" type="submit">Δημιουργία παραγγελίας</button>
</form>
<p style="font-size:13px;color:#766b63">
Η αποστολή παραγγελίας και η ηλεκτρονική πληρωμή χρειάζονται σύνδεση με σύστημα καταστήματος και πάροχο πληρωμών. Αυτός ο κώδικας δημιουργεί προς το παρόν το κείμενο της παραγγελίας.
</p>
</section>
</main>

<footer>
<h2 style="color:white;border:0">ΠΙΤΣΑΡΙΑ ΝΕΦΕΛΗ</h2>
📍 Συκούλα, Αιτωλοακαρνανίας<br>
☎ 26810 88719<br>
☎ 6971618144
</footer>

<script>
const pizzas=[
["Μαργαρίτα","Τυρί, σάλτσα ντομάτας",4,5.5],
["Ζαμπόν – Τυρί","Τυρί, ζαμπόν, σάλτσα ντομάτας",4.5,6],
["Τεμπέλη","Τυρί, σάλτσα ντομάτας",4.5,6],
["Βεζούβιος","Ντομάτα, Κρανίδι, πιπεριά, Tabasco",4.5,6],
["Τέσσερα Τυριά","Mozzarella, φέτα, Regato, Gouda",4.5,6],
["Χωριάτικη","Τυρί, φέτα, ελιές, ντομάτα, μανιτάρια, κρεμμύδι, πιπεριά",4.5,6],
["Μπολονέζ","Τυρί, φέτα, κιμάς",5.5,6.5],
["Σπέσιαλ","Τυρί, ζαμπόν, μανιτάρια, πιπεριά, πεπερόνι, μπέικον",5.5,6.5],
["Καρμπονάρα","Τυρί, ζαμπόν, μπέικον, κρέμα γάλακτος",4.5,6],
["Καρμπονάρα Λευκή","Τυρί, ζαμπόν, μπέικον, κρέμα γάλακτος, χωρίς σάλτσα ντομάτας",4.5,6],
["BBQ","Σάλτσα BBQ, κοτομπουκιές, μπέικον",5.5,6.5]
];

const salads=[
["Ceasar’s","Μαρούλι, ντοματίνια, παρμεζάνα, κοτόπουλο, κρουτόν",4.5],
["Μακαρονοσαλάτα","Πέννες, καλαμπόκι, πιπεριά, ζαμπόν, σως",4],
["Τονοσαλάτα","Μαρούλι, καλαμπόκι, τόνος, dressing",4.5],
["Σαλάτα Chef","Μαρούλι, ντοματίνια, αγγούρι, τυρί, ζαμπόν, αυγό, σως",4.5],
["Ρόκα Παρμεζάνα","Ρόκα, ντοματίνια, παρμεζάνα, κρέμα βαλσάμικου",4]
];

const pastas=[
["Ναπολιτάνα","Σάλτσα ντομάτας",4.5],
["Μπολονέζ","Κιμάς",5.5],
["Μακαρονάδα με κοτόπουλο και παρμεζάνα","",5.5],
["Καρμπονάρα","",5.5],
["Ροζέ","Τυρί, ζαμπόν, μπέικον, σάλτσα ντομάτας, κρέμα γάλακτος",5]
];

const starters=[
["Φλογέρες Mozzarella","3 τεμάχια",3],
["Φλογέρες Ζαμπόν","3 τεμάχια",3.5],
["Σκορδόψωμο","Τυρί, πάστα σκόρδου",3.5],
["Σκορδόψωμο σκεπαστό","",3],
["Σκορδόψωμο με φέτα","Τυρί, φέτα, ντομάτα, πάστα σκόρδου, ρίγανη",4],
["Φέτα σαγανάκι","Φύλλο, φέτα",4],
["Κοτομπουκιές","Με πατάτες",4.5],
["Πατάτες τηγανητές","",3],
["Πατάτες με cheddar και bacon","",4],
["Πατάτες με κιμά","",3.5]
];

const drinks=[
["Coca-Cola 330ml","",1.5],["Coca-Cola 500ml","",2],
["Coca-Cola Zero 330ml","",1.5],["Coca-Cola Zero 500ml","",2],
["Sprite 330ml","",1.5],["Πορτοκαλάδα 330ml","",1.5],
["Λεμονάδα 330ml","",1.5],["Σόδα 330ml","",1.5],
["Heineken 330ml","",2.3],["Kaiser 330ml","",2.3],
["Fix Άνευ 330ml","",2.3],["Άλφα 500ml","",2.5],
["Amstel 500ml","",2.5],["Βεργίνα 500ml","",2.5]
];

const cart=[];
const money=n=>n.toFixed(2).replace(".",",")+" €";

function add(name,type,size,price,eligible=false){
 cart.push({name,type,size,price,eligible});
 drawCart();
}

function productCard(name,desc){
 const box=document.createElement("div");
 box.className="product";
 const h=document.createElement("h3");h.textContent=name;box.appendChild(h);
 if(desc){
  const p=document.createElement("div");p.className="desc";
  p.textContent=desc;box.appendChild(p);
 }
 return box;
}

pizzas.forEach(p=>{
 const box=productCard(p[0],p[1]);
 const actions=document.createElement("div");actions.className="actions";
 [
  ["Πίτσα","Ατομική",p[2],true],
  ["Πίτσα","Οικογενειακή",p[3],true],
  ["Καλτσόνε","Οικογενειακό",p[3],true],
  ["Πεϊνερλί","Οικογενειακό",p[3],true]
 ].forEach(c=>{
  const b=document.createElement("button");
  b.textContent=c[0]+" "+c[1]+" · "+money(c[2]);
  b.onclick=()=>add(p[0],c[0],c[1],c[2],c[3]);
  actions.appendChild(b);
 });
 box.appendChild(actions);
 document.getElementById("pizzas").appendChild(box);
});

function renderSimple(items,id,type){
 items.forEach(p=>{
  const box=productCard(p[0],p[1]);
  const b=document.createElement("button");
  b.textContent="Προσθήκη · "+money(p[2]);
  b.onclick=()=>add(p[0],type,"",p[2],false);
  box.appendChild(b);
  document.getElementById(id).appendChild(box);
 });
}

function freeIndexes(){
 const eligible=cart.map((x,i)=>({x,i})).filter(a=>a.x.eligible);
 const count=Math.floor(eligible.length/5);
 return eligible.slice(0,count).map(a=>a.i);
}

function drawCart(){
 const area=document.getElementById("cart");
 area.innerHTML="";
 const free=freeIndexes();
 let total=0;
 if(!cart.length)area.textContent="Το καλάθι είναι άδειο.";
 cart.forEach((x,i)=>{
  const row=document.createElement("div");row.className="item";
  const label=document.createElement("span");
  const isFree=free.includes(i);
  label.textContent=x.type+" "+x.name+
   (x.size?" ("+x.size+")":"")+" — "+
   (isFree?"ΔΩΡΕΑΝ":money(x.price));
  if(!isFree)total+=x.price;
  const b=document.createElement("button");b.className="remove";
  b.textContent="Χ";
  b.onclick=()=>{cart.splice(i,1);drawCart();};
  row.append(label,b);area.appendChild(row);
 });
 document.getElementById("total").textContent="Σύνολο: "+money(total);
 document.getElementById("promoInfo").textContent=
  "Κανονικές πίτσες: "+cart.filter(x=>x.eligible).length+
  " · Δωρεάν πίτσες: "+free.length+
  ". Η προσφορά  ισχύει για καλτσόνε και πεϊνερλί.";
}

renderSimple(salads,"salads","Σαλάτα");
renderSimple(pastas,"pastas","Ζυμαρικό");
renderSimple(starters,"starters","Ορεκτικό");
renderSimple(drinks,"drinks","Ποτό");

document.getElementById("delivery").addEventListener("change",e=>{
 document.getElementById("address").required=e.target.value==="Delivery";
});


document.getElementById("orderForm").addEventListener("submit", async e => {
  e.preventDefault();

  if (!cart.length) {
    alert("Το καλάθι είναι άδειο!");
    return;
  }

  const button = e.target.querySelector('button[type="submit"]');
  button.disabled = true;
  button.textContent = "Αποστολή...";

  try {
    const free = freeIndexes();
    let total = 0;

    const items = cart.map((x, i) => {
      const isFree = free.includes(i);
      if (!isFree) total += x.price;

      return {
        name: x.name,
        type: x.type,
        size: x.size,
        price: isFree ? 0 : x.price,
        original_price: x.price,
        free: isFree
      };
    });

    const deliveryValue =
      document.getElementById("delivery").value;

    const paymentValue =
      document.getElementById("payment").value;

    const order = {
      customer_name: document.getElementById("customer").value.trim(),
      customer_phone: document.getElementById("phone").value.trim(),
      order_type: deliveryValue === "Delivery" ? "delivery" : "pickup",
      delivery_address:
        deliveryValue === "Delivery"
          ? document.getElementById("address").value.trim()
          : null,
      payment_method:
        paymentValue === "Μετρητά" ? "cash" : "electronic",
      items: items,
      total: Number(total.toFixed(2)),
      notes: document.getElementById("notes").value.trim(),
      status: "new"
    };

    const { data, error } = await db
      .from("orders")
      .insert(order)
      .select("id")
      .single();

    if (error) throw error;

    alert("Η παραγγελία καταχωρήθηκε επιτυχώς!");

    cart.length = 0;
    drawCart();
    e.target.reset();
    document.getElementById("address").required = false;

  } catch (error) {
    console.error("Order error:", error);
    alert("Δεν έγινε η αποστολή. Έλεγξε τη σύνδεση και δοκίμασε ξανά.");
  } finally {
    button.disabled = false;
    button.textContent = "Δημιουργία παραγγελίας";
  }
});
 
 const message=[
  "ΠΑΡΑΓΓΕΛΙΑ ΠΙΤΣΑΡΙΑ ΝΕΦΕΛΗ",
  "Όνομα: "+document.getElementById("customer").value,
  "Τηλέφωνο: "+document.getElementById("phone").value,
  "Τρόπος: "+document.getElementById("delivery").value,
  "Διεύθυνση: "+document.getElementById("address").value,
  "Πληρωμή: "+document.getElementById("payment").value,
  "",
  ...lines,
  "ΣΥΝΟΛΟ: "+money(total),
  "Σχόλια: "+document.getElementById("notes").value
 ].join("\n");
 const win=window.open("","_blank");
 if(win){
  const pre=win.document.createElement("pre");
  pre.textContent=message;
  pre.style.whiteSpace="pre-wrap";
  pre.style.padding="200px";
  win.document.body.appendChild(pre);
  const copy=win.document.createElement("button");
  copy.textContent="Αντιγραφή παραγγελίας";
  copy.style.padding="15px";
  copy.onclick=()=>navigator.clipboard.writeText(message);
  win.document.body.appendChild(copy);
 }else{
  alert("Επίτρεψε τα αναδυόμενα παράθυρα και ξαναδοκίμασε.");
 }
});
</script>
</body>
</html>



