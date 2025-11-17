<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>VoyageFlow — Interactive Travel Experience Simulator</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<style>
 body {
 font-family: 'Poppins', sans-serif;
 margin:0;
 background:#f5f5f5;
 color:#333;
 }
 header {
 background:#004aad;
 color:#fff;
 padding:20px;
 text-align:center;
 font-size:28px;
 font-weight:600;
 letter-spacing:1px;
 }
 .page {
 display:none;
 max-width:900px;
 margin:40px auto;
 background:#fff;
 padding:30px;
 border-radius:12px;
 box-shadow:0 0 15px rgba(0,0,0,0.1);
 }
 .active { display:block; }
 .hero-img {
 width:100%;
 height:250px;
 object-fit:cover;
 border-radius:12px;
 margin-bottom:20px;
 }
 button {
 padding:10px 20px;
 border:none;
 border-radius:8px;
 background:#004aad;
 color:#fff;
 cursor:pointer;
 font-size:16px;
 }
 button:hover { background:#003580; }
 .optionBox {
 padding:12px;
 border-radius:8px;
 border:1px solid #ccc;
 display:flex;
 justify-content:space-between;
 margin-bottom:10px;
 }
 #modal {
 position:fixed;
 top:0; left:0;
 width:100%; height:100%;
 background:rgba(0,0,0,0.6);
 display:flex;
 justify-content:center;
 align-items:center;
 z-index:999;
 }
 #modal.hidden { display:none; }
 #modalContent {
 background:#fff;
 padding:20px;
 border-radius:12px;
 width:90%; max-width:400px;
 text-align:center;
 }
</style>
</head>
<body>
<header>VoyageFlow — Travel Experience Simulator</header>

<!-- Register Page -->
<div id="register" class="page active">
 <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e" class="hero-img" />
 <h2>Register to Begin</h2>
 <form id="regForm">
 <label>Email:</label><br>
 <input type="email" id="email"><br><br>
 <label>Phone:</label><br>
 <input type="text" id="phone"><br><br>
 <label>Pincode:</label><br>
 <input type="text" id="pincode"><br><br>
 <button type="button" id="regSubmit">Continue</button>
 </form>
</div>

<!-- Blog Page -->
<div id="blog" class="page">
 <img src="https://images.unsplash.com/photo-1488646953014-85cb44e25828" class="hero-img" />
 <h2>Explore Travel Inspirations</h2>
 <p>Read curated travel blogs and ideas before planning!</p>
 <button id="toPlanner">Plan Your Trip</button>
</div>

<!-- Planner Page -->
<div id="planner" class="page">
 <img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee" class="hero-img" />
 <h2>Select Your Travel Options</h2>
 <form id="plannerForm">
 <div class="optionBox">
 <span>Flight Booking</span><span>$300</span>
 <input type="checkbox" class="optionCheckbox" data-price="300" data-name="Flight" />
 </div>
 <div class="optionBox">
 <span>Hotel Stay</span><span>$150</span>
 <input type="checkbox" class="optionCheckbox" data-price="150" data-name="Hotel" />
 </div>
 <div class="optionBox">
 <span>Local Tour</span><span>$80</span>
 <input type="checkbox" class="optionCheckbox" data-price="80" data-name="Local Tour" />
 </div>
 </form>
 <p><strong>Total: $</strong><span id="totalPrice">0</span></p>
 <p><strong>Selected:</strong> <span id="selectedList">None</span></p>
 <button id="confirmPlan">Confirm</button>
</div>

<!-- Confirmation Page -->
<div id="confirm" class="page">
 <img src="https://images.unsplash.com/photo-1526778548025-fa2f459cd5c1" class="hero-img" />
 <h2>Your Trip Summary</h2>
 <p id="summaryText"></p>
 <button id="backToBlog">Back to Blog</button>
 <button id="startOver">Start Over</button>
</div>

<!-- Modal -->
<div id="modal" class="hidden">
 <div id="modalContent">
 <h3 id="modalTitle"></h3>
 <p id="modalMessage"></p>
 <button id="modalClose">OK</button>
 </div>
</div>

<script>
function showPage(id){
 document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
 document.getElementById(id).classList.add('active');
}

function openModal(title, msg, onClose){
 document.getElementById('modalTitle').textContent = title;
 document.getElementById('modalMessage').textContent = msg;
 document.getElementById('modal').classList.remove('hidden');
 document.getElementById('modalClose').onclick = () => {
 document.getElementById('modal').classList.add('hidden');
 if(onClose) onClose();
 };
}

// Registration
const email = document.getElementById('email');
const phone = document.getElementById('phone');
const pin = document.getElementById('pincode');

function validateEmail(v){ return /.+@.+\..+/.test(v); }
function validatePhone(v){ return /^[0-9]{10}$/.test(v); }
function validatePin(v){ return /^[0-9]{6}$/.test(v); }

document.getElementById('regSubmit').addEventListener('click', () => {
 const emailOK = validateEmail(email.value);
 const phoneOK = validatePhone(phone.value);
 const pinOK = validatePin(pin.value);

 if (!(emailOK && phoneOK && pinOK)) {
 openModal('Invalid Input', 'Please correct your details.');
 return;
 }

 openModal('Registration Successful', 'Welcome to VoyageFlow! Preparing your travel content...', () => showPage('blog'));
 setTimeout(() => document.getElementById('modalClose').click(), 1200);
});

// Planner logic
const checkboxes = Array.from(document.querySelectorAll('.optionCheckbox'));
const totalEl = document.getElementById('totalPrice');
const selectedList = document.getElementById('selectedList');

function updateTotal(){
 let total = 0;
 const names = [];
 checkboxes.forEach(cb=>{
 if(cb.checked){ total += Number(cb.dataset.price); names.push(cb.dataset.name); }
 });
 totalEl.textContent = total;
 selectedList.textContent = names.length ? names.join(', ') : 'None';
}

checkboxes.forEach(cb=>cb.addEventListener('change', updateTotal));
updateTotal();

document.getElementById('confirmPlan').addEventListener('click', () => {
 const selected = checkboxes.filter(c=>c.checked).map(c=>({ name:c.dataset.name, price:Number(c.dataset.price) }));
 if(selected.length===0){
 openModal('No Selection', 'Please choose at least one option.');
 setTimeout(()=>document.getElementById('modalClose').click(),1000);
 return;
 }

 const sum = selected.reduce((s,it)=>s+it.price,0);
 const message = `You selected ${selected.length} item(s). Total: $${sum}. Proceeding...`;

 openModal('Trip Confirmed', message, () => {
 const summaryText = document.getElementById('summaryText');
 const lines = selected.map(it=>`${it.name} — $${it.price}`);
 summaryText.innerHTML = `<strong>Items:</strong><br>${lines.join('<br>')}<br><strong>Total:</strong> $${sum}`;
 showPage('confirm');
 });
 setTimeout(() => document.getElementById('modalClose').click(), 1200);
});

document.getElementById('toPlanner').addEventListener('click', () => showPage('planner'));
document.getElementById('backToBlog').addEventListener('click', () => showPage('blog'));
document.getElementById('startOver').addEventListener('click', () => {
 document.getElementById('regForm').reset();
 document.getElementById('plannerForm').reset();
 updateTotal();
 showPage('register');
});
</script>
</body>
</html>
