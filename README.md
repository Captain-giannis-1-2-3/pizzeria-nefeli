
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
button:disabled{opacity:.6;cursor:wait}
input,select,textarea{width:100%;padding:12px;margin:7px 0;border:1px solid #ccc;border-radius:7px;font-size:15px}
textarea{min-height:70px}
.item{display:flex;justify-content:space-between;gap:8px;padding:9px 0;border-bottom:1px solid #eee}
.item span{flex:1}
.remove{background:#555}
.total{font-size:21px;font-weight:bold;margin:16px 0}
.submit{width:100%;background:#218838;padding:14px;font-size:17px}
.status{font-size:14px;line-height:1.5;margin-top:10px}
footer{background:#29211c;color:white;text-align:center;padding:25px;line-height:1.8;margin-top:30px}
footer h2{color:white;border:0}
</style>
</head>
<body>
<header>
<img src="FB_IMG_1792954368125.jpg" alt="Λογότυπο ΝΕΦΕΛΗ">
<h1>ΠΙΤΣΑΡΙΑ Καφέ ΝΕΦΕΛΗ</h1>
<p>Καλώς ήρθατε! Για κρατήσεις τραπεζιού καλέστε μας.</p>
</header>
<div class="offer">🍕 4+1 ΔΩΡΟ — Μόνο στις κανονικές πίτσες</div>
<main>
<h2>🍕 Πίτσες – Καλτσόνε – Πεϊνερλί</h2><div id="pizzas"></div>
<h2>🥗 Σαλάτες</h2><div id="salads"></div>
<h2>🍝 Ζυμαρικά</h2><div id="pastas"></div>
<h2>🍟 Ορεκτικά</h2><div id="starters"></div>
<h2>🥤 Αναψυκτικά και μπύρες</h2><div id="drinks"></div>
<section class="cart">
<h2>🛒 Το καλάθι μου</h2>
<div id="cart">Το καλάθι είναι άδειο.</div>
<div class="total" id="total">Σύνολο: 0,00 €</div>
<p id="promoInfo" class="status"></p>
<h2>📦 Στοιχεία παραγγελίας</h2>
<form id="orderForm">
<input id="customer" placeholder="Ονοματεπώνυμο" autocomplete="name" required>
<input id="phone" type="tel" placeholder="Τηλέφωνο" autocomplete="tel" required>
<select id="delivery" required>
ο"address").value.trim();
  if(deliveryValue==="delivery"&&!addressValue){
    status.textContent="Συμπλήρωσε τη διεύθυνση για delivery.";
    status.style.color="#b00020";return;
  }
  button.disabled=true;button.textContent="Αποστολή παραγγελίας...";
  try{
    const free=freeIndexes();let total=0;
    const items=cart.map((x,i)=>{
      const isFree=free.includes(i);if(!isFree)total+=x.price;
      return {name:x.name,type:x.type,size:x.size,price:isFree?0:x.price,original_price:x.price,free:isFree};
    });
    const order={
      customer_name:document.getElementById("customer").value.trim(),
      customer_phone:document.getElementById("phone").value.trim(),
      order_type:deliveryValue,
      delivery_address:deliveryValue==="delivery"?addressValue:null,
      payment_method:document.getElementById("payment").value,
      items,
      total:Number(total.toFixed(2)),
      notes:document.getElementById("notes").value.trim(),
      status:"new"
    };
    const {error}=await db.from("orders").insert([order]);
    if(error)throw error;
    status.textContent="Η παραγγελία καταχωρήθηκε επιτυχώς! Θα επικοινωνήσουμε μαζί σας.";
    status.style.color="#16733a";
    cart.length=0;drawCart();e.target.reset();
    document.getElementById("address").required=false;
    document.getElementById("address").disabled=true;
  }catch(error){
    console.error("Order submission error:",error);
    status.textContent="Δεν έγινε η αποστολή. "+(error?.message||"Έλεγξε τη σύνδεση και τις ρυθμίσεις της βάσης.");
    status.style.color="#b00020";
  }finally{
    button.disabled=false;button.textContent="Δημιουργία παραγγελίας";
  }
});
</script>
</body>
</html>
