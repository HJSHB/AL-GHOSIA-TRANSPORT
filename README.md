<!DOCTYPE html>
<html lang="fr">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>ALGHOSIATRANSPORT - Chauffeur Privé</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<header>

<h1>ALGHOSIATRANSPORT</h1>

<nav>
<a href="#cars">Véhicules</a>
<a href="#reservation">Réservation</a>
<a href="#contact">Contact</a>
</nav>

</header>

<section class="hero">

<h2>Chauffeur privé premium</h2>
<p>Confort • Luxe • Disponibilité 24/7</p>

<a href="#reservation" class="btn">Réserver maintenant</a>

</section>

<section id="cars" class="cars">

<h2>Nos Véhicules</h2>

<div class="car">

<img src="images/byd.jpg">

<h3>BYD SEAL 2025</h3>

<p>Berline électrique silencieuse et luxueuse.</p>

</div>

<div class="car">

<img src="images/amg.jpg">

<h3>MERCEDES AMG 2025</h3>

<p>Performance et prestige pour vos déplacements VIP.</p>

</div>

</section>

<section id="reservation" class="reservation">

<h2>Réservation</h2>

<form id="bookingForm">

<input type="text" placeholder="Nom" required>

<input type="text" placeholder="Lieu de départ" required>

<input type="text" placeholder="Destination" required>

<input type="date" required>

<input type="time" required>

<select id="car">
<option value="seal">BYD SEAL 2025</option>
<option value="amg">Mercedes AMG 2025</option>
</select>

<input type="number" id="distance" placeholder="Distance (km)" required>

<button type="button" onclick="calculate()">Estimer le prix</button>

<h3 id="price"></h3>

<button type="submit">Confirmer réservation</button>

</form>

</section>

<section id="contact" class="contact">

<h2>Contact</h2>

<p>Disponible 24h/24</p>

<a class="whatsapp" href="https://wa.me/">Réserver via WhatsApp</a>

</section>

<footer>

<p>© 2025 ALGHOSIATRANSPORT</p>

</footer>

<script src="script.js"></script>

</body>

</html>
