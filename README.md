# Code-mickey-data-source.html.github.io
For data perches
from pathlib import Path

html = r"""<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Code Mickey Data Source & Trading Platform</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700;800&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Poppins,sans-serif}
body{
background:linear-gradient(135deg,#0f172a,#111827,#1e3a8a);
color:#fff;overflow-x:hidden;
}
@keyframes gradientShift{
0%{background-position:0% 50%}
50%{background-position:100% 50%}
100%{background-position:0% 50%}
}
@keyframes float{
0%,100%{transform:translateY(0px)}
50%{transform:translateY(-20px)}
}
@keyframes glow{
0%,100%{box-shadow:0 0 20px rgba(255,215,0,0.5)}
50%{box-shadow:0 0 40px rgba(255,215,0,0.8)}
}
@keyframes pulse{
0%{opacity:0.7}
50%{opacity:1}
100%{opacity:0.7}
}
.navbar{
background:rgba(0,0,0,0.3);
padding:15px 30px;
display:flex;
justify-content:space-around;
align-items:center;
position:sticky;
top:0;
z-index:100;
backdrop-filter:blur(10px);
}
.nav-btn{
color:#ffd700;
text-decoration:none;
font-weight:600;
padding:10px 20px;
border-radius:20px;
transition:all 0.3s ease;
}
.nav-btn:hover{
background:#ffd700;
color:#111;
}
.hero{
min-height:100vh;display:flex;flex-direction:column;
justify-content:center;align-items:center;text-align:center;padding:20px;
background:linear-gradient(-45deg,#0f172a,#1e3a8a,#111827,#ffd700);
background-size:400% 400%;
animation:gradientShift 15s ease infinite;
position:relative;
overflow:hidden;
}
.hero::before{
content:'';
position:absolute;
width:200%;
height:200%;
background:radial-gradient(circle,rgba(255,215,0,0.1) 1px,transparent 1px);
background-size:50px 50px;
animation:float 8s ease-in-out infinite;
top:-50%;
left:-50%;
z-index:0;
}
.hero > *{position:relative;z-index:1}
.hero h1{font-size:4rem;color:#ffd700;animation:glow 2s ease-in-out infinite}
.hero p{max-width:700px;margin:15px 0;animation:float 3s ease-in-out infinite}
.btn-group{display:flex;gap:20px;justify-content:center;flex-wrap:wrap;margin-top:30px}
.btn{
background:#ffd700;color:#111;padding:14px 30px;
border-radius:30px;text-decoration:none;font-weight:700;
transition:all 0.3s ease;
animation:float 2s ease-in-out infinite;
cursor:pointer;
border:none;
font-size:1rem;
}
.btn:hover{
transform:scale(1.1);
box-shadow:0 0 30px rgba(255,215,0,0.8);
}
.btn-secondary{
background:#f59e0b;
color:#111;
}
.flyer{
width:min(1100px,92%);margin:30px auto;
background:linear-gradient(135deg,#ffd700,#f59e0b);
color:#111;border-radius:25px;padding:40px;text-align:center;
animation:glow 2s ease-in-out infinite;
}
.cards{
display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
gap:20px;margin-top:25px;
}
.card{
background:#fff;padding:20px;border-radius:20px;
transition:all 0.3s ease;
animation:float 3s ease-in-out infinite;
}
.card:hover{
transform:translateY(-10px);
box-shadow:0 10px 30px rgba(0,0,0,0.3);
}
.price{font-size:2rem;font-weight:800;color:#f59e0b}
.trading-section{
background:linear-gradient(135deg,#1a1f3a,#2d2959);
padding:50px 20px;
border-radius:25px;
margin:30px auto;
width:min(1100px,92%);
}
.trading-title{
font-size:2.5rem;
color:#ffd700;
margin-bottom:30px;
animation:glow 2s ease-in-out infinite;
}
.trading-cards{
display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:20px;
}
.trading-card{
background:rgba(255,215,0,0.1);
border:2px solid #ffd700;
padding:25px;
border-radius:15px;
transition:all 0.3s ease;
}
.trading-card:hover{
transform:translateY(-10px);
background:rgba(255,215,0,0.2);
box-shadow:0 0 30px rgba(255,215,0,0.5);
}
.trading-card h3{
color:#ffd700;
margin-bottom:15px;
font-size:1.3rem;
}
.trading-card p{
color:#e0e0e0;
line-height:1.6;
}
.stock-ticker{
background:rgba(0,0,0,0.3);
padding:20px;
border-radius:10px;
margin:20px 0;
font-family:monospace;
}
.ticker-item{
display:flex;
justify-content:space-between;
padding:10px;
border-bottom:1px solid rgba(255,215,0,0.2);
animation:pulse 2s ease-in-out infinite;
}
.ticker-symbol{color:#ffd700;font-weight:700}
.ticker-price{color:#4ade80}
.ticker-change{color:#f87171}
.formbox{
width:min(800px,92%);margin:40px auto;
background:rgba(255,255,255,.08);
padding:30px;border-radius:20px;
backdrop-filter:blur(10px);
}
input,select,textarea{
width:100%;padding:14px;margin:10px 0;
border:none;border-radius:10px;
transition:all 0.3s ease;
}
input:focus,select:focus,textarea:focus{
outline:none;
box-shadow:0 0 20px rgba(255,215,0,0.5);
transform:scale(1.02);
}
button{
width:100%;padding:15px;border:none;
border-radius:10px;background:#ffd700;
font-weight:700;cursor:pointer;
transition:all 0.3s ease;
animation:glow 1.5s ease-in-out infinite;
color:#111;
}
button:hover{
transform:scale(1.05);
box-shadow:0 0 30px rgba(255,215,0,0.9);
}
#result{
margin-top:20px;padding:15px;border-radius:10px;
display:none;background:rgba(34,197,94,.2);
animation:float 0.5s ease-in-out;
}
footer{text-align:center;padding:30px}
</style>
</head>
<body>

<nav class="navbar">
<a href="#home" class="nav-btn">🏠 Home</a>
<a href="#data" class="nav-btn">📊 Data</a>
<a href="#trading" class="nav-btn">💹 Trading</a>
<a href="#order" class="nav-btn">🛒 Order</a>
</nav>

<section class="hero" id="home">
<h1>CODE MICKEY</h1>
<p>Premium Data & Trading Platform</p>
<div class="btn-group">
<a class="btn" href="#data">Get Data</a>
<a class="btn btn-secondary" href="#trading">Trade Now</a>
</div>
</section>

<section class="flyer" id="data">
<h2>🔥 Premium Data Deals 🔥</h2>
<div class="cards">
<div class="card"><h3>1 GB</h3><div class="price">GHS 10</div></div>
<div class="card"><h3>5 GB</h3><div class="price">GHS 40</div></div>
<div class="card"><h3>10 GB</h3><div class="price">GHS 75</div></div>
</div>
<h3 style="margin-top:20px">MTN MoMo: +233 53 037 4086</h3>
</section>

<section class="trading-section" id="trading">
<h2 class="trading-title">💹 Live Trading Dashboard</h2>

<div class="trading-cards">
<div class="trading-card">
<h3>📈 Forex Trading</h3>
<p>Trade major currency pairs with real-time market data. Minimum deposit: GHS 50</p>
<div class="stock-ticker">
<div class="ticker-item">
<span class="ticker-symbol">EUR/USD</span>
<span class="ticker-price">1.0850</span>
<span class="ticker-change">+0.52%</span>
</div>
<div class="ticker-item">
<span class="ticker-symbol">GBP/USD</span>
<span class="ticker-price">1.2680</span>
<span class="ticker-change">+0.75%</span>
</div>
</div>
</div>

<div class="trading-card">
<h3>🪙 Crypto Trading</h3>
<p>Trade Bitcoin, Ethereum, and other cryptocurrencies. Start with GHS 25</p>
<div class="stock-ticker">
<div class="ticker-item">
<span class="ticker-symbol">BTC/USD</span>
<span class="ticker-price">67,450</span>
<span class="ticker-change">+2.34%</span>
</div>
<div class="ticker-item">
<span class="ticker-symbol">ETH/USD</span>
<span class="ticker-price">3,890</span>
<span class="ticker-change">+1.89%</span>
</div>
</div>
</div>

<div class="trading-card">
<h3>📊 Stock Trading</h3>
<p>Trade global stocks from NYSE, NASDAQ, and African exchanges. Min: GHS 100</p>
<div class="stock-ticker">
<div class="ticker-item">
<span class="ticker-symbol">AAPL</span>
<span class="ticker-price">185.50</span>
<span class="ticker-change">+1.23%</span>
</div>
<div class="ticker-item">
<span class="ticker-symbol">MSFT</span>
<span class="ticker-price">425.80</span>
<span class="ticker-change">+0.95%</span>
</div>
</div>
</div>
</div>
</section>

<section class="formbox" id="order">
<h2>Live Order Form - Data & Trading</h2>

<form id="orderForm">
<input type="text" id="name" placeholder="Full Name" required>

<input type="tel" id="phone" placeholder="Phone Number" required>

<select id="service" required>
<option value="">Select Service</option>
<option value="data">📊 Data Package</option>
<option value="forex">💹 Forex Trading</option>
<option value="crypto">🪙 Crypto Trading</option>
<option value="stocks">📈 Stock Trading</option>
</select>

<select id="package" required>
<option value="">Select Package</option>
<option>1 GB - GHS 10</option>
<option>5 GB - GHS 40</option>
<option>10 GB - GHS 75</option>
<option>Forex - GHS 50</option>
<option>Crypto - GHS 25</option>
<option>Stocks - GHS 100</option>
</select>

<input type="text" id="transaction" placeholder="MoMo Transaction ID" required>

<textarea id="notes" placeholder="Additional Notes"></textarea>

<button type="submit">Submit Order</button>
</form>

<div id="result"></div>
</section>

<footer>
<h3>Code Mickey - Data & Trading Hub</h3>
<p>📞 WhatsApp: +233 53 037 4086</p>
<p>💰 Secure | 📱 Fast | 🔒 Reliable</p>
</footer>

<script>
document.getElementById("orderForm").addEventListener("submit", function(e){
e.preventDefault();

const name=document.getElementById("name").value;
const phone=document.getElementById("phone").value;
const service=document.getElementById("service").value;
const package_sel=document.getElementById("package").value;
const transaction=document.getElementById("transaction").value;

const result=document.getElementById("result");
result.style.display="block";
result.innerHTML=`
<h3>✅ Order Received!</h3>
<p><strong>Name:</strong> ${name}</p>
<p><strong>Phone:</strong> ${phone}</p>
<p><strong>Service:</strong> ${service.toUpperCase()}</p>
<p><strong>Package:</strong> ${package_sel}</p>
<p><strong>Transaction ID:</strong> ${transaction}</p>
<p>Please send these details to WhatsApp: +233530374086 for processing.</p>
`;
});
</script>

</body>
</html>
"""

path = "/mnt/data/Code_Mickey_Data_Source_Premium_Live_Order.html"
Path(path).write_text(html, encoding="utf-8")
print(path)
