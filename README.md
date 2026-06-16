[n.html](https://github.com/user-attachments/files/28997148/n.html)
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Kayıt Formu</title>

<style>
body {
    font-family: Arial;
    background: #111;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
}

.form-box {
    background: #222;
    padding: 20px;
    border-radius: 10px;
    width: 300px;
    text-align: center;
}
input {
    width: 90%;
    padding: 10px;
    margin: 8px 0;
    border-radius: 6px;
    border: none;
}

button {
    width: 95%;
    padding: 10px;
    margin-top: 10px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 15px;
}

.save-btn {
    background: limegreen;
    color: black;
}

.menu-btn {
    background: dodgerblue;
    color: white;
}
</style>
</head>

<body>

<div class="form-box">
    <h2>Kayıt Ol</h2>

    <input id="adsoyad" placeholder="Ad Soyad">
    <input id="takim" placeholder="Takım">
    <input id="sifre" type="password" placeholder="Şifre">

    <button class="save-btn" onclick="kaydet()">Kaydet</button>

    <a href="index.html">
    <button style="width: 200px; height:40px;">Ana Menüye Dön</button>


<script>
function kaydet(){
    let adsoyad = document.getElementById("adsoyad").value;
    let takim = document.getElementById("takim").value;
    let sifre = document.getElementById("sifre").value;

    if(adsoyad === "" || takim === "" || sifre === ""){
        alert("Lütfen tüm alanları doldur!");
        return;
    }

    let user = {
        adsoyad: adsoyad,
        takim: takim,
        sifre: sifre
    };

    localStorage.setItem("kullanici", JSON.stringify(user));

    alert("Kayıt başarılı!");
}

function anamenu(){
    // buraya kendi ana sayfa linkini koyabilirsin
    window.location.href = "index.html";
}
</script>
<script type="module">

import { initializeApp } from "https://www.gstatic.com/firebasejs/12.14.0/firebase-app.js";

import { getFirestore, collection, addDoc }
from "https://www.gstatic.com/firebasejs/12.14.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "BURAYA",
  authDomain: "BURAYA",
  projectId: "BURAYA",
  storageBucket: "BURAYA",
  messagingSenderId: "BURAYA",
  appId: "BURAYA"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

window.kaydet = async function() {

  let isim = document.getElementById("isim").value;

  await addDoc(collection(db, "uyeler"), {
    isim: isim,
    tarih: new Date()
  });

  alert("Kayıt başarılı!");
};

</script>
</body>
</html>

   
