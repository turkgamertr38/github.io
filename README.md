<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>TürkGamerTR</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body,html{height:100%;font-family:Arial,sans-serif;background:url('https://seeklogo.com/images/C/cgn-logo-343599F0BA-seeklogo.com.png') center/cover no-repeat fixed;color:white;overflow-x:hidden;}
#login-screen{position:fixed;top:0;left:0;width:100%;height:100%;display:flex;flex-direction:column;justify-content:center;align-items:center;background:rgba(0,0,0,0.7);z-index:100;}
#login-box{background:rgba(34,34,34,0.95);padding:40px;border-radius:15px;text-align:center;border:3px solid #ff4500;box-shadow:0 0 30px #ff4500,0 0 50px #ff4500 inset;}
#login-box input{display:block;margin:15px auto;padding:12px;border-radius:6px;border:none;width:220px;background:#444;color:white;font-size:16px;}
#login-box button{padding:12px 25px;border:none;background:#ff4500;color:white;border-radius:6px;cursor:pointer;font-size:16px;}
#login-box button:hover{background:#ff7f50;}
#site{display:none;opacity:0;transition:opacity 0.5s ease;}
header{background:rgba(34,34,34,0.95);padding:12px;text-align:center;}
header img{height:60px;}
nav{background:rgba(51,51,51,0.95);padding:10px;text-align:center;}
nav a{text-decoration:none;font-weight:bold;margin:0 10px;color:white;transition:0.3s;}
nav a:hover{color:#ff4500;}
main{display:flex;flex-wrap:wrap;margin:20px;gap:20px;}
section{flex:3;min-width:250px;background:rgba(26,26,26,0.85);padding:20px;border-radius:12px;box-shadow:0 0 20px #ff4500;position:relative;overflow:hidden;}
aside{flex:1;min-width:200px;background:rgba(26,26,26,0.85);padding:20px;border-radius:12px;box-shadow:0 0 20px #ff4500;height:fit-content;}
#game-slider{position:relative;width:100%;height:250px;margin-top:20px;overflow:hidden;border-radius:12px;}
#game-slider img{position:absolute;width:100%;height:100%;object-fit:cover;border-radius:12px;opacity:0;transform:scale(1);transition:opacity 1s ease, transform 1s ease;}
#game-slider img.active{opacity:1;transform:scale(1.05);}
#slider-caption{position:absolute;bottom:15px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,0.6);padding:10px 20px;border-radius:8px;font-size:16px;text-align:center;max-width:90%;}
#slider-dots{position:absolute;bottom:10px;left:50%;transform:translateX(-50%);display:flex;gap:10px;}
#slider-dots span{width:12px;height:12px;background:rgba(255,255,255,0.5);border-radius:50%;cursor:pointer;transition:all 0.3s ease;}
#slider-dots span.active{background:#ff4500;transform:scale(1.2);}
@media(max-width:768px){main{flex-direction:column;}aside{margin-left:0;margin-top:20px;}#game-slider{height:200px;}#slider-caption{font-size:14px;}}
</style>
</head>
<body>

<!-- Giriş Ekranı -->
<div id="login-screen">
  <img src="https://seeklogo.com/images/C/cgn-logo-343599F0BA-seeklogo.com.png" alt="CGN Logo" style="height:100px;margin-bottom:20px;">
  <div id="login-box">
    <h2>Giriş Yap</h2>
    <input type="text" id="username" placeholder="Kullanıcı Adı">
    <input type="password" id="password" placeholder="Şifre">
    <button id="loginBtn">Giriş</button>
  </div>
</div>

<!-- Site İçeriği -->
<div id="site">
  <header>
    <img src="https://seeklogo.com/images/C/cgn-logo-343599F0BA-seeklogo.com.png" alt="CGN Logo">
  </header>
  <nav>
    <a href="#">Oyun Bölümleri</a>
    <a href="#">İpuçları</a>
    <a href="#">Forum</a>
    <a href="#">Hakkında</a>
    <a href="https://www.youtube.com/@T%C3%BCrkGamerTR-n7s">YouTube Kanalı</a>
  </nav>
  <main>
    <section>
      <h2>Oyun Bölümleri</h2>
      <p>Minecraft, küplerden oluşan sınırsız bir dünyada inşa etme, keşfetme ve hayatta kalma üzerine kurulu popüler bir oyun alanıdır...</p>
      <div id="game-slider">
        <img src="https://cdn.pixabay.com/photo/2016/03/26/22/21/minecraft-1284354_960_720.png" class="active" alt="Minecraft Yaratıcı">
        <img src="https://cdn.pixabay.com/photo/2015/11/16/16/28/minecraft-1044220_960_720.png" alt="Minecraft Keşif">
        <img src="https://cdn.pixabay.com/photo/2016/03/26/22/22/minecraft-1284355_960_720.png" alt="Minecraft Survival">
        <div id="slider-caption">Yaratıcı Mod: Hayalindeki yapıları inşa et!</div>
        <div id="slider-dots"></div>
      </div>
    </section>
    <aside>
      <h2>Hakkında</h2>
      <p>Çağan OK profesyonel bir oyuncudur.</p>
    </aside>
  </main>
</div>

<script>
// Kullanıcılar için giriş kontrolü
const users = [
  {username: "admin", password: "1234"},
  {username: "cagan", password: "2025"},
  {username: "misafir", password: "0000"}
];

document.getElementById("loginBtn").addEventListener("click", function(){
  const u=document.getElementById("username").value;
  const p=document.getElementById("password").value;
  const found = users.find(user => user.username===u && user.password===p);
  if(found){
    document.getElementById("login-screen").style.display="none";
    const site=document.getElementById("site");
    site.style.display="block";
    setTimeout(()=>site.style.opacity=1,50);
  }else{
    alert("Kullanıcı adı veya şifre hatalı!");
  }
});

// Slider
const slides=document.querySelectorAll("#game-slider img");
const captions=[
  "Yaratıcı Mod: Hayalindeki yapıları inşa et!",
  "Keşif Modu: Dünyayı keşfet ve maceraya atıl!",
  "Hayatta Kalma Modu: Düşmanlardan korun ve kaynak topla!"
];
const captionDiv=document.getElementById("slider-caption");
const dotsContainer=document.getElementById("slider-dots");
let currentIndex=0;

// Noktalar
slides.forEach((s,i)=>{
  const dot=document.createElement("span");
  if(i===0) dot.classList.add("active");
  dot.addEventListener("click",()=>{goToSlide(i);});
  dotsContainer.appendChild(dot);
});

function goToSlide(index){
  slides.forEach(s=>s.classList.remove("active"));
  slides[index].classList.add("active");
  currentIndex=index;
  captionDiv.textContent=captions[index];
  document.querySelectorAll("#slider-dots span").forEach(s=>s.classList.remove("active"));
  document.querySelectorAll("#slider-dots span")[index].classList.add("active");
}

setInterval(()=>{
  let next=(currentIndex+1)%slides.length;
  goToSlide(next);
},4000);
</script>

</body>
</html>
