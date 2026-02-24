royal-invest-immobilier
config.php
index.php
register.php
login.php
dashboard.php
add-property.php
properties.php
messages.php
admin-approve.php
logout.php
style.css
database.sql
<?php
session_start();

$conn = new mysqli("localhost", "root", "", "royal_invest");

if ($conn->connect_error) {
    die("Connexion échouée: " . $conn->connect_error);
}
?>
CREATE DATABASE royal_invest;
USE royal_invest;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    password VARCHAR(255),
    role VARCHAR(20) DEFAULT 'agent'
);

CREATE TABLE properties (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(200),
    description TEXT,
    price VARCHAR(50),
    status VARCHAR(20) DEFAULT 'pending',
    user_id INT
);

CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    sender_id INT,
    receiver_id INT,
    message TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
<?php include 'config.php';

if($_POST){
    $name = $_POST['name'];
    $email = $_POST['email'];
    $password = password_hash($_POST['password'], PASSWORD_DEFAULT);

    $conn->query("INSERT INTO users (name,email,password) 
    VALUES ('$name','$email','$password')");
    echo "Compte créé avec succès.";
}
?>

<form method="POST">
<input type="text" name="name" placeholder="Nom" required>
<input type="email" name="email" placeholder="Email" required>
<input type="password" name="password" placeholder="Mot de passe" required>
<button>S'inscrire</button>
</form>
<?php include 'config.php';

if($_POST){
    $email = $_POST['email'];
    $password = $_POST['password'];

    $result = $conn->query("SELECT * FROM users WHERE email='$email'");
    $user = $result->fetch_assoc();

    if(password_verify($password, $user['password'])){
        $_SESSION['user'] = $user;
        header("Location: dashboard.php");
    }
}
?>

<form method="POST">
<input type="email" name="email" placeholder="Email" required>
<input type="password" name="password" placeholder="Mot de passe" required>
<button>Connexion</button>
</form>
<?php include 'config.php';

if(!isset($_SESSION['user'])){
    header("Location: login.php");
}
?>

<h2>Bienvenue <?php echo $_SESSION['user']['name']; ?></h2>

<a href="add-property.php">Ajouter un bien</a> |
<a href="properties.php">Voir les biens</a> |
<a href="messages.php">Messagerie</a> |
<a href="logout.php">Déconnexion</a>

<?php
if($_SESSION['user']['role'] == 'admin'){
    echo "<br><a href='admin-approve.php'>Valider les annonces</a>";
}
?>
<?php include 'config.php';

if($_POST){
    $title = $_POST['title'];
    $description = $_POST['description'];
    $price = $_POST['price'];
    $user_id = $_SESSION['user']['id'];

    $conn->query("INSERT INTO properties (title,description,price,user_id)
    VALUES ('$title','$description','$price','$user_id')");

    echo "Annonce envoyée en validation.";
}
?>

<form method="POST">
<input type="text" name="title" placeholder="Titre du bien" required>
<textarea name="description" placeholder="Description"></textarea>
<input type="text" name="price" placeholder="Prix">
<button>Publier</button>
</form>
<?php include 'config.php';

$result = $conn->query("SELECT * FROM properties WHERE status='pending'");

while($row = $result->fetch_assoc()){
    echo $row['title'] . " - 
    <a href='?approve=".$row['id']."'>Valider</a><br>";
}

if(isset($_GET['approve'])){
    $id = $_GET['approve'];
    $conn->query("UPDATE properties SET status='approved' WHERE id=$id");
    header("Location: admin-approve.php");
}
?>
<?php include 'config.php';

$result = $conn->query("SELECT * FROM properties WHERE status='approved'");

while($row = $result->fetch_assoc()){
    echo "<h3>".$row['title']."</h3>";
    echo "<p>".$row['description']."</p>";
    echo "<strong>".$row['price']."</strong><hr>";
}
?>
<?php include 'config.php';

if($_POST){
    $message = $_POST['message'];
    $sender = $_SESSION['user']['id'];
    $receiver = 1; // ID Admin par défaut

    $conn->query("INSERT INTO messages (sender_id,receiver_id,message)
    VALUES ('$sender','$receiver','$message')");
}

$result = $conn->query("SELECT * FROM messages");

while($row = $result->fetch_assoc()){
    echo "<p>".$row['message']."</p>";
}
?>

<form method="POST">
<textarea name="message"></textarea>
<button>Envoyer</button>
</form>
body{
    font-family: Arial;
    background:#f4f6f9;
}

button{
    background:#0d2c6c;
    color:white;
    padding:10px 15px;
    border:none;
}

h2{
    color:#0d2c6c;
}
