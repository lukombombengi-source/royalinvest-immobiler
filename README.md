# royalinvest-immobiler
Site opérant dans le domaine de l'immobilier
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Royal Invest Immobilier</title>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#f4f6f9;
}
header{
    background:#0d2c6c;
    color:white;
    padding:15px 30px;
    display:flex;
    justify-content:space-between;
    align-items:center;
}
header h1{
    margin:0;
    font-size:20px;
}
nav a{
    color:white;
    margin-left:15px;
    text-decoration:none;
    font-weight:bold;
}
.hero{
    background:url('https://images.unsplash.com/photo-1600585154340-be6161a56a0c') no-repeat center/cover;
    color:white;
    text-align:center;
    padding:120px 20px;
}
.hero h2{
    font-size:38px;
}
.btn{
    background:#d4af37;
    padding:12px 25px;
    color:white;
    text-decoration:none;
    border-radius:5px;
}
.section{
    padding:60px 20px;
    text-align:center;
}
.cards{
    display:flex;
    justify-content:center;
    flex-wrap:wrap;
    gap:20px;
}
.card{
    background:white;
    width:300px;
    border-radius:10px;
    box-shadow:0 4px 10px rgba(0,0,0,0.1);
    overflow:hidden;
}
.card img{
    width:100%;
    height:200px;
    object-fit:cover;
}
.card h3{
    margin:10px 0 5px;
}
.card p{
    margin-bottom:15px;
}
.contact{
    background:#0d2c6c;
    color:white;
    padding:40px;
}
footer{
    background:#00153a;
    color:white;
    text-align:center;
    padding:15px;
}
</style>
</head>

<body>

<header>
<h1>👑 Royal Invest Immobilier</h1>
<nav>
<a href="#">Accueil</a>
<a href="#vente">Vente</a>
<a href="#location">Location</a>
<a href="#contact">Contact</a>
</nav>
</header>

<section class="hero">
<h2>Achat • Vente • Location à Kinshasa</h2>
<p>Votre partenaire immobilier de confiance</p>
<br>
<a href="#contact" class="btn">Contactez-nous</a>
</section>

<section class="section" id="vente">
<h2>Biens en Vente</h2>
<div class="cards">
<div class="card">
<img src="https://images.unsplash.com/photo-1568605114967-8130f3a36994">
<h3>Villa Moderne - Gombe</h3>
<p>450 000 $</p>
</div>
<div class="card">
<img src="https://images.unsplash.com/photo-1500382017468-9049fed747ef">
<h3>Parcelle - Ngaliema</h3>
<p>80 $ / m²</p>
</div>
</div>
</section>

<section class="section" id="location">
<h2>Biens en Location</h2>
<div class="cards">
<div class="card">
<img src="https://images.unsplash.com/photo-1600585154526-990dced4db0d">
<h3>Appartement Moderne</h3>
<p>1 500 $ / mois</p>
</div>
<div class="card">
<img src="https://images.unsplash.com/photo-1497366216548-37526070297c">
<h3>Bureau en Ville</h3>
<p>2 000 $ / mois</p>
</div>
</div>
</section>

<section class="contact" id="contact">
<h2>Contact</h2>
<p>📞 +243 813318389</p>
<p>📧 lukombombengi@gmail.com</p>
<p>📍 Kinshasa, RDC</p>
<br>
<a href="https://wa.me/243813318389" class="btn">WhatsApp</a>
</section>

<footer>
© 2026 Royal Invest Immobilier - Tous droits réservés
</footer>

</body>
</html>
