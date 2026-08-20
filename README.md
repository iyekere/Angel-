<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ANGEL GIFT CARD</title>

<style>
*{box-sizing:border-box}

body{
    margin:0;
    font-family:Arial,sans-serif;
    background:linear-gradient(135deg,#080b20,#17104a,#071d35);
    color:white;
    min-height:100vh;
}

.app{
    max-width:480px;
    margin:auto;
    min-height:100vh;
    background:rgba(7,12,35,.75);
}

header{
    padding:22px 20px;
    display:flex;
    justify-content:space-between;
    align-items:center;
    border-bottom:1px solid #ffffff18;
}

.logo{
    font-weight:900;
    font-size:21px;
}

.logo span{
    color:#ffd34e;
}

main{
    padding:20px;
}

.card{
    background:linear-gradient(135deg,#705cff,#a443ff);
    border-radius:24px;
    padding:22px;
    box-shadow:0 15px 35px #0005;
    margin-bottom:18px;
}

.balance{
    font-size:38px;
    font-weight:900;
    margin:8px 0;
}

.muted{
    color:#c9c8dc;
    font-size:13px;
}

.grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:12px;
}

.action{
    border:1px solid #ffffff18;
    background:#ffffff0c;
    color:white;
    border-radius:18px;
    padding:18px 10px;
    text-align:center;
    cursor:pointer;
}

.action:hover{
    background:#ffffff16;
    transform:translateY(-2px);
}

.icon{
    font-size:25px;
    display:block;
    margin-bottom:7px;
}

.section{
    display:none;
}

.section.active{
    display:block;
}

.panel{
    background:#ffffff0b;
    border:1px solid #ffffff12;
    border-radius:20px;
    padding:18px;
}

input,select{
    width:100%;
    padding:14px;
    margin:8px 0;
    border-radius:12px;
    border:1px solid #ffffff18;
    background:#0c1230;
    color:white;
    outline:none;
}

.primary{
    width:100%;
    border:0;
    border-radius:13px;
    padding:14px;
    background:#ffd34e;
    color:#17120a;
    font-weight:800;
    cursor:pointer;
    margin-top:8px;
}

.logout-btn{
    background:#ff4e4e;
    color:white;
    border:0;
    border-radius:12px;
    padding:8px 12px;
    font-weight:bold;
    cursor:pointer;
}

.back{
    background:none;
    border:0;
    color:#ffd34e;
    padding:0 0 15px;
    cursor:pointer;
}

nav{
    position:sticky;
    bottom:0;
    background:#090d25ee;
    border-top:1px solid #ffffff14;
    display:grid;
    grid-template-columns:repeat(4,1fr);
    padding:10px;
}

nav button{
    background:none;
    border:0;
    color:#bfc0d5;
    padding:8px;
    font-size:12px;
    cursor:pointer;
}

nav button.active{
    color:#ffd34e;
}

.badge{
    background:#ffffff18;
    padding:7px 10px;
    border-radius:20px;
    font-size:12px;
}

.notice{
    font-size:12px;
    line-height:1.5;
    color:#c8c8d8;
    margin-top:12px;
}

.auth-container{
    position:fixed;
    inset:0;
    background:linear-gradient(135deg,#090b22,#30105d);
    z-index:5;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:20px;
}

.signupbox{
    width:100%;
    max-width:430px;
    background:#ffffff0b;
    border:1px solid #ffffff16;
    border-radius:26px;
    padding:25px;
}

.small{
    font-size:12px;
    color:#aaaec8;
    margin-top:10px;
}

.toggle-auth{
    color:#ffd34e;
    cursor:pointer;
    text-decoration:underline;
}
</style>
</head>

<body>

<!-- SIGN UP FORM -->

<div id="signup" class="auth-container">

    <div class="signupbox">

        <div class="logo">
            ✨ ANGEL <span>GIFT CARD</span>
        </div>

        <h1>Create your account</h1>

        <p class="muted">
            Welcome to Angel Gift Card.
        </p>

        <input
            id="signup-name"
            placeholder="Full name"
        >

        <input
            id="signup-email"
            type="email"
            placeholder="Email address"
        >

        <input
            id="signup-phone"
            placeholder="Phone number"
        >

        <input
            id="signup-password"
            type="password"
            placeholder="Password"
        >

        <button
            class="primary"
            onclick="createAccount()"
        >
            Sign Up
        </button>

        <p class="small">
            Already have an account? <span class="toggle-auth" onclick="toggleAuthScreen('login')">Log In</span>
        </p>

    </div>

</div>

<!-- LOG IN FORM -->

<div id="login" class="auth-container" style="display:none">

    <div class="signupbox">

        <div class="logo">
            ✨ ANGEL <span>GIFT CARD</span>
        </div>

        <h1>Log in to account</h1>

        <p class="muted">
            Welcome back to Angel Gift Card.
        </p>

        <input
            id="login-email"
            type="email"
            placeholder="Email address"
        >

        <input
            id="login-password"
            type="password"
            placeholder="Password"
        >

        <button
            class="primary"
            onclick="loginAccount()"
        >
            Log In
        </button>

        <p class="small">
            Don't have an account? <span class="toggle-auth" onclick="toggleAuthScreen('signup')">Sign Up</span>
        </p>

    </div>

</div>


<!-- MAIN APP -->

<div
    class="app"
    id="app"
    style="display:none"
>

<header>

    <div class="logo">
        ✨ ANGEL <span>GIFT CARD</span>
    </div>

    <div>
        <span
            class="badge"
            id="userBadge"
        >
            Member
        </span>

        <button class="logout-btn" onclick="logoutAccount()">
            Log Out
        </button>
    </div>

</header>


<main>

<!-- HOME -->

<section
    id="home"
    class="section active"
>

    <div class="card">

        <div class="muted">
            Available Balance
        </div>

        <div class="balance">
            ₦<span id="balance">0</span>
        </div>

        <div class="muted">
            Angel Gift Card Wallet
        </div>

    </div>


    <div class="grid">

        <button
            class="action"
            onclick="show('redeem')"
        >
            <span class="icon">🎁</span>
            Redeem Card
        </button>


        <button
            class="action"
            onclick="show('withdraw')"
        >
            <span class="icon">💸</span>
            Withdraw
        </button>


        <button
            class="action"
            onclick="show('trade')"
        >
            <span class="icon">🔄</span>
            Trade
        </button>


        <button
            class="action"
            onclick="show('deposit')"
        >
            <span class="icon">➕</span>
            Deposit
        </button>

    </div>

</section>


<!-- REDEEM -->

<section
    id="redeem"
    class="section"
>

<button
    class="back"
    onclick="show('home')"
>
    ← Back
</button>

<div class="panel">

    <h2>
        Redeem Gift Card
    </h2>

    <input
        id="giftcode"
        placeholder="Enter gift card code"
    >

    <button
        class="primary"
        onclick="redeemCard()"
    >
        Redeem Card
    </button>

</div>

</section>


<!-- WITHDRAW -->

<section
    id="withdraw"
    class="section"
>

<button
    class="back"
    onclick="show('home')"
>
    ← Back
</button>

<div class="panel">

    <h2>
        Withdraw
    </h2>

    <input
        id="withdrawAmount"
        type="number"
        placeholder="Amount (₦)"
    >

    <input
        placeholder="Recipient account number"
    >

    <input
        placeholder="Recipient bank"
    >

    <button
        class="primary"
        onclick="withdrawMoney()"
    >
        Request Withdrawal
    </button>

</div>

</section>


<!-- DEPOSIT -->

<section
    id="deposit"
    class="section"
>

<button
    class="back"
    onclick="show('home')"
>
    ← Back
</button>

<div class="panel">

    <h2>
        Deposit
    </h2>

    <p class="muted">
        Deposit Account Details
    </p>


    <div
        style="
        background:#ffffff0c;
        border:1px solid #ffffff18;
        border-radius:16px;
        padding:15px;
        margin-top:12px;
        "
    >

        <p>
            <span class="muted">
                Bank
            </span>
            <br>

            <b>
                FairMoney Microfinance Bank LTD
            </b>
        </p>


        <p>
            <span class="muted">
                Account Number
            </span>
            <br>

            <b
                style="font-size:22px"
            >
                2026457764
            </b>
        </p>


        <p>
            <span class="muted">
                Account Name
            </span>
            <br>

            <b>
                Sheriff Ismail
            </b>
        </p>

    </div>


    <button
        class="primary"
        onclick="copyAccount()"
    >
        Copy Account Number
    </button>

    <p
        class="notice"
    >
        Please confirm the account name and number carefully before making any transaction.
    </p>

</div>

</section>


<!-- TRADE -->

<section
    id="trade"
    class="section"
>

<button
    class="back"
    onclick="show('home')"
>
    ← Back
</button>

<div class="panel">

    <h2>
        Trade
    </h2>


    <select>

        <option>
            Gift Card → NGN
        </option>

        <option>
            NGN → Gift Card
        </option>

        <option>
            USD → NGN
        </option>

        <option>
            EUR → NGN
        </option>

    </select>


    <input
        type="number"
        placeholder="Amount"
    >


    <button
        class="primary"
        onclick="tradeNow()"
    >
        Continue
    </button>

</div>

</section>


<!-- CURRENCY -->

<section
    id="currency"
    class="section"
>

<button
    class="back"
    onclick="show('home')"
>
    ← Back
</button>

<div class="panel">

    <h2>
        Change Currency
    </h2>


    <select
        id="currencySelect"
        onchange="
        document.getElementById('currencyLabel').textContent=this.value
        "
    >

        <option>
            NGN — Nigerian Naira
        </option>

        <option>
            USD — US Dollar
        </option>

        <option>
            GBP — British Pound
        </option>

        <option>
            EUR — Euro
        </option>

        <option>
            GHS — Ghanaian Cedi
        </option>

    </select>


    <p class="muted">
        Selected:

        <span id="currencyLabel">
            NGN — Nigerian Naira
        </span>
    </p>

</div>

</section>

</main>


<!-- NAVIGATION -->

<nav>

<button
    class="active"
    onclick="show('home',this)"
>
    ⌂
    <br>
    Home
</button>


<button
    onclick="show('currency',this)"
>
    ◎
    <br>
    Currency
</button>


<button
    onclick="show('redeem',this)"
>
    🎁
    <br>
    Redeem
</button>


<button
    onclick="show('withdraw',this)"
>
    ↗
    <br>
    Withdraw
</button>

</nav>

</div>


<script>

let firstDepositMade = false;

function toggleAuthScreen(screen) {
    document.getElementById("signup").style.display = screen === 'signup' ? "flex" : "none";
    document.getElementById("login").style.display = screen === 'login' ? "flex" : "none";
}

function createAccount(){

    const name = document.getElementById("signup-name").value.trim();
    const email = document.getElementById("signup-email").value.trim();
    const phone = document.getElementById("signup-phone").value.trim();
    const password = document.getElementById("signup-password").value;

    if(!name || !email || !phone || !password){
        alert("Please complete all fields.");
        return;
    }

    document.getElementById("signup").style.display = "none";
    document.getElementById("app").style.display = "block";

    document.getElementById("userBadge").textContent = name.split(" ")[0];
    document.getElementById("balance").textContent = "13,000";

    alert("Welcome to Angel Gift Card! Your balance is ₦13,000.");
}

function loginAccount(){
    const email = document.getElementById("login-email").value.trim();
    const password = document.getElementById("login-password").value;

    if(!email || !password){
        alert("Please complete all fields.");
        return;
    }

    document.getElementById("login").style.display = "none";
    document.getElementById("app").style.display = "block";

    document.getElementById("userBadge").textContent = email.split("@")[0];
    document.getElementById("balance").textContent = "13,000";

    alert("Logged in successfully!");
}

function logoutAccount(){
    document.getElementById("app").style.display = "none";
    document.getElementById("login").style.display = "flex";
    alert("You have logged out.");
}

function show(id,btn){

    document.querySelectorAll(".section").forEach(
        section => section.classList.remove("active")
    );

    document.getElementById(id).classList.add("active");

    document.querySelectorAll("nav button").forEach(
        button => button.classList.remove("active")
    );

    if(btn){
        btn.classList.add("active");
    }

    window.scrollTo(0, 0);
}

function copyAccount(){
    navigator.clipboard.writeText("2026457764").then(() => alert("Account number copied."));
}

function redeemCard(){
    const code = document.getElementById("giftcode").value.trim();
    if(!code){
        alert("Enter a gift card code.");
        return;
    }
    alert("Gift card code received.");
}

function withdrawMoney(){
    const amount = document.getElementById("withdrawAmount").value;

    if(!amount){
        alert("Enter the withdrawal amount.");
        return;
    }

    if(!firstDepositMade){
        alert("Withdrawal blocked: Your first deposit must be at least ₦2,000 before you can make withdrawals.");
        return;
    }

    alert("Withdrawal request received.");
}

function tradeNow(){
    alert("Trade request received.");
}

</script>

</body>
</html>
