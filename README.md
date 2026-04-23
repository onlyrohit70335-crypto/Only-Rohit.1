# Only-Rohit.1<!DOCTYPE html>
<html>
<head>
<title>Login</title>
</head>

<body style="background:black;color:white;text-align:center">

<h1>🔐 Admin Login</h1>

<input type="text" id="user" placeholder="Username"><br><br>
<input type="password" id="pass" placeholder="Password"><br><br>

<button onclick="login()">Login</button>

<script>
function login() {
    let u = document.getElementById("user").value;
    let p = document.getElementById("pass").value;

    if(u === "boss" && p === "1234") {
        window.location.href = "admin.html";
    } else {
        alert("Wrong login!");
    }
}
</script>

</body>
</html>
<!DOCTYPE html>
<html>
<head>
<title>Boss Dashboard</title>
</head>

<body style="background:#0f0f0f;color:white;text-align:center">

<h1>📊 Boss Dashboard</h1>

<h2 id="total">Loading...</h2>
<h2 id="today">Loading...</h2>

<script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js"></script>

<script>

const firebaseConfig = {
  apiKey: "YOUR_KEY",
  authDomain: "YOUR_DOMAIN",
  projectId: "YOUR_ID"
};

firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

// TOTAL
db.collection("clicks").get().then(snapshot => {
    document.getElementById("total").innerText =
        "🔥 Total Clicks: " + snapshot.size;
});

// TODAY
let today = new Date().toDateString();

db.collection("clicks").get().then(snapshot => {
    let count = 0;

    snapshot.forEach(doc => {
        let time = new Date(doc.data().time).toDateString();
        if(time === today) count++;
    });

    document.getElementById("today").innerText =
        "📅 Today Clicks: " + count;
});

</script>

</body>
</html>
<script>
function loadTrending() {
fetch(`https://api.themoviedb.org/3/trending/movie/day?api_key=${API_KEY}`)
.then(res => res.json())
.then(data => showMovies(data.results));
}

function showMovies(movies) {
let results = document.getElementById("results");
results.innerHTML = "";

movies.forEach(movie => {
results.innerHTML += `
<div class="movie">
<h3>${movie.title}</h3>
<p>⭐ ${movie.vote_average}</p>
<button onclick="trackClick('${movie.title}')">Download</button>
</div>`;
});
}

window.onload = loadTrending;
</script>
let earning = snapshot.size * 0.002;
💰 Estimated Earnings: ₹XXX
boss / 1234 ❌
rohitboss / mysecret999 ✅
https://boss-movies.netlify.app
