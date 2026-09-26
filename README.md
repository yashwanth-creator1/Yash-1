```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>yash AI — Future Technology</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:Arial,Helvetica,sans-serif;
}

:root{
  --bg:#05060a;
  --card:#0d1018;
  --text:#f5f7ff;
  --muted:#9ba3b8;
  --accent:#7c5cff;
  --accent2:#00e5ff;
  --border:rgba(255,255,255,.1);
}

body{
  background:var(--bg);
  color:var(--text);
  overflow-x:hidden;
}

/* Animated background */
body::before{
  content:"";
  position:fixed;
  width:500px;
  height:500px;
  background:var(--accent);
  filter:blur(180px);
  opacity:.18;
  top:-200px;
  left:-150px;
  z-index:-1;
}

body::after{
  content:"";
  position:fixed;
  width:500px;
  height:500px;
  background:var(--accent2);
  filter:blur(200px);
  opacity:.12;
  right:-200px;
  bottom:-200px;
  z-index:-1;
}

/* NAVBAR */
nav{
  width:100%;
  padding:20px 7%;
  display:flex;
  justify-content:space-between;
  align-items:center;
  position:sticky;
  top:0;
  z-index:100;
  backdrop-filter:blur(20px);
  background:rgba(5,6,10,.7);
  border-bottom:1px solid var(--border);
}

.logo{
  font-size:25px;
  font-weight:900;
  letter-spacing:2px;
}

.logo span{
  color:var(--accent2);
}

nav ul{
  display:flex;
  gap:30px;
  list-style:none;
}

nav a{
  color:var(--muted);
  text-decoration:none;
  transition:.3s;
}

nav a:hover{
  color:white;
}

.theme{
  border:1px solid var(--border);
  background:transparent;
  color:white;
  padding:9px 13px;
  border-radius:10px;
  cursor:pointer;
}

/* HERO */
.hero{
  min-height:88vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
  padding:70px 20px;
}

.badge{
  padding:9px 18px;
  border:1px solid rgba(124,92,255,.5);
  border-radius:50px;
  background:rgba(124,92,255,.08);
  color:#cfc7ff;
  margin-bottom:25px;
}

.hero h1{
  font-size:clamp(48px,9vw,100px);
  line-height:.95;
  max-width:1000px;
  background:linear-gradient(90deg,#fff,#9c8cff,#00e5ff);
  -webkit-background-clip:text;
  color:transparent;
}

.hero p{
  max-width:700px;
  margin:30px auto;
  color:var(--muted);
  font-size:18px;
  line-height:1.7;
}

.buttons{
  display:flex;
  gap:15px;
  flex-wrap:wrap;
  justify-content:center;
}

.btn{
  padding:15px 25px;
  border-radius:12px;
  text-decoration:none;
  font-weight:bold;
  cursor:pointer;
  border:none;
  transition:.3s;
}

.primary{
  background:linear-gradient(90deg,var(--accent),var(--accent2));
  color:white;
}

.secondary{
  background:rgba(255,255,255,.05);
  color:white;
  border:1px solid var(--border);
}

.btn:hover{
  transform:translateY(-4px);
  box-shadow:0 15px 40px rgba(124,92,255,.25);
}

/* STATS */
.stats{
  display:flex;
  justify-content:center;
  gap:70px;
  flex-wrap:wrap;
  padding:30px;
  border-top:1px solid var(--border);
  border-bottom:1px solid var(--border);
}

.stat{
  text-align:center;
}

.stat h2{
  font-size:35px;
}

.stat p{
  color:var(--muted);
}

/* SECTION */
section{
  padding:100px 7%;
}

.section-title{
  text-align:center;
  margin-bottom:55px;
}

.section-title h2{
  font-size:45px;
}

.section-title p{
  color:var(--muted);
  margin-top:15px;
}

/* CARDS */
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
  gap:22px;
}

.card{
  background:linear-gradient(145deg,rgba(255,255,255,.06),rgba(255,255,255,.02));
  border:1px solid var(--border);
  border-radius:20px;
  padding:30px;
  transition:.35s;
  position:relative;
  overflow:hidden;
}

.card::before{
  content:"";
  position:absolute;
  width:120px;
  height:120px;
  background:var(--accent);
  filter:blur(70px);
  opacity:0;
  transition:.3s;
}

.card:hover::before{
  opacity:.5;
}

.card:hover{
  transform:translateY(-8px);
  border-color:rgba(124,92,255,.5);
}

.icon{
  font-size:40px;
  margin-bottom:20px;
}

.card h3{
  font-size:22px;
  margin-bottom:12px;
}

.card p{
  color:var(--muted);
  line-height:1.6;
}

/* AI CHAT */
.ai-box{
  max-width:850px;
  margin:auto;
  border:1px solid var(--border);
  background:#090b11;
  border-radius:25px;
  padding:25px;
  box-shadow:0 20px 80px rgba(0,0,0,.4);
}

.chat{
  height:320px;
  overflow-y:auto;
  padding:15px;
}

.message{
  margin:12px 0;
  padding:13px 16px;
  border-radius:14px;
  max-width:80%;
  line-height:1.5;
}

.ai{
  background:#151a27;
  color:#dce1f2;
}

.user{
  background:linear-gradient(90deg,#6246e8,#007e91);
  margin-left:auto;
}

.chat-input{
  display:flex;
  gap:10px;
  margin-top:15px;
}

.chat-input input{
  flex:1;
  padding:15px;
  border-radius:12px;
  border:1px solid var(--border);
  outline:none;
  background:#10131c;
  color:white;
}

.chat-input button{
  padding:0 22px;
  border:none;
  border-radius:12px;
  background:var(--accent);
  color:white;
  cursor:pointer;
}

/* TECHNOLOGY */
.tech{
  display:flex;
  justify-content:center;
  gap:20px;
  flex-wrap:wrap;
}

.tech span{
  padding:13px 20px;
  border:1px solid var(--border);
  border-radius:50px;
  color:#cdd2e4;
  background:rgba(255,255,255,.03);
}

/* FOOTER */
footer{
  padding:40px 7%;
  border-top:1px solid var(--border);
  text-align:center;
  color:var(--muted);
}

footer strong{
  color:white;
}

/* LIGHT MODE */
.light{
  --bg:#f4f7fb;
  --card:white;
  --text:#10131c;
  --muted:#596174;
  --border:rgba(0,0,0,.1);
}

.light nav{
  background:rgba(244,247,251,.8);
}

.light .ai-box,
.light .chat-input input{
  background:white;
}

.light .ai{
  background:#edf0f7;
  color:#222;
}

/* MOBILE */
@media(max-width:700px){
  nav ul{
    display:none;
  }

  .hero{
    min-height:80vh;
  }

  .stats{
    gap:35px;
  }

  section{
    padding:70px 5%;
  }

  .section-title h2{
    font-size:35px;
  }
}
</style>
</head>

<body>

<nav>
  <div class="logo">NEXORA<span>AI</span></div>

  <ul>
    <li><a href="#features">Features</a></li>
    <li><a href="#ai">AI Lab</a></li>
    <li><a href="#tech">Technology</a></li>
  </ul>

  <button class="theme" onclick="toggleTheme()">☀️</button>
</nav>

<!-- HERO -->
<div class="hero">

  <div class="badge">✦ THE NEXT GENERATION OF TECHNOLOGY</div>

  <h1>Build Beyond<br>Imagination.</h1>

  <p>
    Welcome to Nexora AI — an experimental technology hub
    where artificial intelligence, automation and futuristic
    digital experiences come together.
  </p>

  <div class="buttons">
    <a href="#ai" class="btn primary">Launch AI Lab →</a>
    <a href="#features" class="btn secondary">Explore Technology</a>
  </div>

</div>

<!-- STATS -->
<div class="stats">
  <div class="stat">
    <h2>24/7</h2>
    <p>AI Availability</p>
  </div>

  <div class="stat">
    <h2>99.9%</h2>
    <p>Platform Uptime</p>
  </div>

  <div class="stat">
    <h2>∞</h2>
    <p>Ideas Possible</p>
  </div>
</div>

<!-- FEATURES -->
<section id="features">

  <div class="section-title">
    <h2>Powerful Technology</h2>
    <p>Explore the digital systems behind the future.</p>
  </div>

  <div class="grid">

    <div class="card">
      <div class="icon">🤖</div>
      <h3>AI Intelligence</h3>
      <p>
        Create intelligent experiences using natural-language
        interfaces and machine-learning powered systems.
      </p>
    </div>

    <div class="card">
      <div class="icon">⚡</div>
      <h3>Automation</h3>
      <p>
        Turn repetitive digital tasks into fast automated
        workflows.
      </p>
    </div>

    <div class="card">
      <div class="icon">🧠</div>
      <h3>Smart Systems</h3>
      <p>
        Design applications capable of processing information
        and generating useful responses.
      </p>
    </div>

    <div class="card">
      <div class="icon">🔐</div>
      <h3>Secure Design</h3>
      <p>
        Build privacy-conscious interfaces with secure-by-design
        principles.
      </p>
    </div>

    <div class="card">
      <div class="icon">🌐</div>
      <h3>Cloud Technology</h3>
      <p>
        Connect applications and services through modern
        cloud-based architectures.
      </p>
    </div>

    <div class="card">
      <div class="icon">🚀</div>
      <h3>Future Interfaces</h3>
      <p>
        Create futuristic interfaces designed for the next
        generation of digital products.
      </p>
    </div>

  </div>
</section>

<!-- AI LAB -->
<section id="ai">

  <div class="section-title">
    <h2>AI Lab</h2>
    <p>Try the interactive AI assistant.</p>
  </div>

  <div class="ai-box">

    <div class="chat" id="chat">

      <div class="message ai">
        🤖 Hello! I'm Nexora AI. Ask me something about
        technology, programming or the future.
      </div>

    </div>

    <div class="chat-input">

      <input
        id="question"
        type="text"
        placeholder="Ask Nexora AI..."
        onkeydown="if(event.key==='Enter') askAI()"
      >

      <button onclick="askAI()">Send</button>

    </div>

  </div>

</section>

<!-- TECHNOLOGY -->
<section id="tech">

  <div class="section-title">
    <h2>Technology Stack</h2>
    <p>Modern technologies for modern experiences.</p>
  </div>

  <div class="tech">
    <span>HTML5</span>
    <span>CSS3</span>
    <span>JavaScript</span>
    <span>AI</span>
    <span>Cloud</span>
    <span>APIs</span>
    <span>Automation</span>
    <span>Cybersecurity</span>
  </div>

</section>

<footer>
  <strong>NEXORA AI</strong>
  <br><br>
  Building tomorrow's digital experiences.
  <br><br>
  © 2026 Nexora AI
</footer>

<script>

/* DARK / LIGHT MODE */
function toggleTheme(){

  document.body.classList.toggle("light");

}

/* SIMPLE AI DEMO */
function askAI(){

  const input = document.getElementById("question");
  const chat = document.getElementById("chat");

  const question = input.value.trim();

  if(!question) return;

  const userMessage = document.createElement("div");

  userMessage.className = "message user";
  userMessage.textContent = question;

  chat.appendChild(userMessage);

  input.value = "";

  setTimeout(() => {

    const aiMessage = document.createElement("div");

    aiMessage.className = "message ai";

    let answer =
      "Interesting question! Nexora AI is currently running in demo mode. Connect this interface to an AI API to generate real AI responses.";

    const q = question.toLowerCase();

    if(q.includes("html")){
      answer =
      "HTML creates the structure of a website. CSS controls its appearance and JavaScript adds interaction.";
    }

    else if(q.includes("javascript")){
      answer =
      "JavaScript lets websites respond to users, manipulate content, communicate with APIs and build interactive applications.";
    }

    else if(q.includes("ai")){
      answer =
      "AI systems can analyze information, generate content, recognize patterns and assist users with many digital tasks.";
    }

    else if(q.includes("future")){
      answer =
      "The future of technology is likely to involve increasingly capable AI, automation, spatial interfaces and smarter connected systems.";
    }

    aiMessage.textContent = "🤖 " + answer;

    chat.appendChild(aiMessage);

    chat.scrollTop = chat.scrollHeight;

  },700);

}

/* Smooth scrolling */
document.querySelectorAll('a[href^="#"]').forEach(link => {

  link.addEventListener("click", function(e){

    e.preventDefault();

    document.querySelector(this.getAttribute("href"))
      .scrollIntoView({
        behavior:"smooth"
      });

  });

});

</script>

</body>
</html>
```
