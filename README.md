
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<header>
<img src="FB_IMG_1792954368125.jpg" alt="Λογότυπο ΝΕΦΕΛΗ">
<h1>ΠΙΤΣΑΡΙΑ ΝΕΦΕΛΗ</h1>
<p>Καλώς ήρθατε!</p>
</header>

<div class="offer">🍕 4+1 ΔΩΡΟ — ΜΟΝΟ ΣΤΙΣ ΠΙΤΣΕΣ!</div>

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
☎ σειντομα διαθέσιμο<br>σειντομα διαθέσιμο για 
☎ 6971618144
</footer>

<script>
const pizzas=[
["Μαργαρίτα","Τυρί, σάλτσα ντομάτας",4,5.5],
["Ζαμπόν – Τυρί","Τυρί, ζαμπόν, σάλτσα ντομάτας",4.5,6],
["Τεμπέλη","Τυρί, σάλτσα ντομάτας",4.5,6],
["Βεζούβιος 🌶️","Ντομάτα, Κρανίδι, πιπεριά, Tabasco",4.5,6],
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
  ["Καλτσόνε","Οικογενειακό",p[3],false],
  ["Πεϊνερλί","Οικογενειακό",p[3],false]
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
  ". Η προσφορά δεν ισχύει για καλτσόνε ή πεϊνερλί.";
}

renderSimple(salads,"salads","Σαλάτα");
renderSimple(pastas,"pastas","Ζυμαρικό");
renderSimple(starters,"starters","Ορεκτικό");
renderSimple(drinks,"drinks","Ποτό");

document.getElementById("delivery").addEventListener("change",e=>{
 document.getElementById("address").required=e.target.value==="Delivery";
});

document.getElementById("orderForm").addEventListener("submit",e=>{
 e.preventDefault();
 if(!cart.length){alert("Το καλάθι είναι άδειο!");return;}
 const free=freeIndexes();
 let total=0;
 const lines=cart.map((x,i)=>{
  const freeItem=free.includes(i);
  if(!freeItem)total+=x.price;
  return x.type+" "+x.name+" "+x.size+" — "+(freeItem?"ΔΩΡΕΑΝ":money(x.price));
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
  pre.style.padding="20px";
  win.document.body.appendChild(pre);
  const copy=win.document.createElement("button");
  copy.textContent="Αντιγραφή παραγγελίας";
  copy.style.padding="12px";
  copy.onclick=()=>navigator.clipboard.writeText(message);
  win.document.body.appendChild(copy);
 }else{
  alert("Επίτρεψε τα αναδυόμενα παράθυρα και ξαναδοκίμασε.");
 }
});
</script>
</body>
</html>

