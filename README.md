<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Universal Problem Solver</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}

:root{
  --bg:#07111f;
  --card:#0d1b2e;
  --card2:#10243b;
  --text:#eef6ff;
  --muted:#9fb3c8;
  --accent:#5ee7ff;
  --accent2:#8b7cff;
  --good:#45e6a5;
  --danger:#ff6b81;
  --border:rgba(255,255,255,.1);
}

body{
  font-family:Inter,Arial,sans-serif;
  background:
    radial-gradient(circle at 15% 10%,rgba(94,231,255,.14),transparent 30%),
    radial-gradient(circle at 90% 20%,rgba(139,124,255,.16),transparent 30%),
    var(--bg);
  color:var(--text);
  min-height:100vh;
}

header{
  padding:24px;
  border-bottom:1px solid var(--border);
  background:rgba(7,17,31,.78);
  backdrop-filter:blur(15px);
  position:sticky;
  top:0;
  z-index:10;
}

.logo{
  font-size:25px;
  font-weight:900;
}

.logo span{color:var(--accent)}

header p{
  color:var(--muted);
  margin-top:5px;
}

.app{
  display:grid;
  grid-template-columns:260px 1fr;
  max-width:1500px;
  margin:auto;
}

aside{
  min-height:calc(100vh - 100px);
  padding:20px;
  border-right:1px solid var(--border);
}

.tool{
  width:100%;
  border:1px solid transparent;
  background:transparent;
  color:var(--muted);
  padding:13px;
  border-radius:12px;
  text-align:left;
  margin-bottom:7px;
  cursor:pointer;
  font-size:14px;
}

.tool:hover,.tool.active{
  color:white;
  background:linear-gradient(90deg,rgba(94,231,255,.13),rgba(139,124,255,.12));
  border-color:var(--border);
}

main{
  padding:30px;
}

.hero{
  padding:30px;
  border:1px solid var(--border);
  border-radius:24px;
  background:linear-gradient(135deg,rgba(94,231,255,.09),rgba(139,124,255,.09));
  margin-bottom:20px;
}

.hero h1{
  font-size:clamp(30px,5vw,55px);
  line-height:1;
}

.hero h1 span{
  background:linear-gradient(90deg,var(--accent),var(--accent2));
  -webkit-background-clip:text;
  color:transparent;
}

.hero p{
  margin-top:15px;
  color:var(--muted);
  max-width:800px;
  line-height:1.6;
}

.card{
  background:rgba(13,27,46,.9);
  border:1px solid var(--border);
  border-radius:20px;
  padding:22px;
  margin-bottom:18px;
  box-shadow:0 15px 40px rgba(0,0,0,.18);
}

label{
  display:block;
  color:var(--muted);
  font-size:13px;
  margin:12px 0 7px;
}

input,textarea,select{
  width:100%;
  border:1px solid var(--border);
  background:#071525;
  color:white;
  padding:13px;
  border-radius:12px;
  outline:none;
  font-size:15px;
}

textarea{
  min-height:145px;
  resize:vertical;
}

input:focus,textarea:focus,select:focus{
  border-color:var(--accent);
}

button{
  border:0;
  cursor:pointer;
}

.primary{
  margin-top:15px;
  padding:14px 22px;
  border-radius:12px;
  color:#001019;
  font-weight:900;
  background:linear-gradient(90deg,var(--accent),#a8f3ff);
}

.secondary{
  padding:10px 14px;
  border-radius:10px;
  background:#172b43;
  color:white;
}

.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(190px,1fr));
  gap:12px;
}

.result{
  border-left:4px solid var(--good);
  background:#09192a;
  padding:18px;
  border-radius:12px;
  line-height:1.7;
}

.result h3{
  color:var(--accent);
  margin-bottom:8px;
}

.error{
  border-left-color:var(--danger);
}

.step{
  padding:12px;
  margin:8px 0;
  border-radius:10px;
  background:#10243b;
}

.answer{
  font-size:25px;
  font-weight:900;
  color:var(--good);
  margin:8px 0 15px;
}

.history-item{
  padding:12px;
  border-bottom:1px solid var(--border);
  cursor:pointer;
}

.history-item:hover{
  background:#10243b;
}

.badge{
  display:inline-block;
  padding:5px 9px;
  border-radius:20px;
  background:#172b43;
  color:var(--accent);
  font-size:11px;
  margin:3px;
}

footer{
  text-align:center;
  padding:25px;
  color:var(--muted);
}

@media(max-width:800px){
  .app{grid-template-columns:1fr}
  aside{
    min-height:auto;
    border-right:0;
    border-bottom:1px solid var(--border);
    overflow-x:auto;
    display:flex;
    gap:7px;
  }
  .tool{
    min-width:max-content;
    margin:0;
  }
  main{padding:15px}
}
</style>
</head>

<body>

<header>
  <div class="logo">ðŸ§  Universal<span>Solver</span></div>
  <p>One powerful offline toolkit for mathematics, science, finance and everyday calculations.</p>
</header>

<div class="app">

<aside>
  <button class="tool active" onclick="setTool('smart',this)">âœ¨ Smart Solver</button>
  <button class="tool" onclick="setTool('algebra',this)">ðŸ“ Algebra</button>
  <button class="tool" onclick="setTool('quadratic',this)">ðŸ”¢ Quadratic</button>
  <button class="tool" onclick="setTool('calculus',this)">âˆ« Calculus</button>
  <button class="tool" onclick="setTool('matrix',this)">â–¦ Matrices</button>
  <button class="tool" onclick="setTool('geometry',this)">ðŸ“ Geometry</button>
  <button class="tool" onclick="setTool('trig',this)">ðŸ“ Trigonometry</button>
  <button class="tool" onclick="setTool('statistics',this)">ðŸ“Š Statistics</button>
  <button class="tool" onclick="setTool('probability',this)">ðŸŽ² Probability</button>
  <button class="tool" onclick="setTool('physics',this)">âš¡ Physics</button>
  <button class="tool" onclick="setTool('chemistry',this)">ðŸ§ª Chemistry</button>
  <button class="tool" onclick="setTool('finance',this)">ðŸ’° Finance</button>
  <button class="tool" onclick="setTool('conversion',this)">ðŸ”„ Converter</button>
  <button class="tool" onclick="setTool('percentage',this)">ï¼… Percentage</button>
  <button class="tool" onclick="setTool('history',this)">ðŸ•˜ History</button>
</aside>

<main>

<section class="hero">
  <h1>Universal <span>Problem Solver</span></h1>
  <p>
    Enter a supported problem and get a calculated answer with
    understandable steps. Designed for students, learners and everyday calculations.
  </p>
</section>

<div id="workspace"></div>

</main>
</div>

<footer>
  UniversalSolver â€¢ Runs entirely in your browser â€¢ Educational calculator
</footer>

<script>
let currentTool="smart";
let historyData=[];

const $=id=>document.getElementById(id);

function setTool(tool,button){
  currentTool=tool;
  document.querySelectorAll(".tool").forEach(x=>x.classList.remove("active"));
  if(button)button.classList.add("active");
  render();
}

function render(){

  if(currentTool==="history"){
    $("workspace").innerHTML=`
      <div class="card">
        <h2>ðŸ•˜ Solution History</h2>
        <div id="history">
        ${historyData.length?
          historyData.map((x,i)=>`
          <div class="history-item" onclick="restoreHistory(${i})">
            <b>${x.type}</b><br>
            <small>${escapeHTML(x.input)}</small>
          </div>`).join("")
          :"No problems solved yet."}
        </div>
        <br>
        <button class="secondary" onclick="clearHistory()">Clear History</button>
      </div>`;
    return;
  }

  let html="";

  if(currentTool==="smart"){
    html=`
    <div class="card">
      <h2>âœ¨ Smart Solver</h2>
      <p style="color:var(--muted);margin-top:7px">
      Try examples such as:
      <span class="badge">2x + 5 = 17</span>
      <span class="badge">xÂ² - 5x + 6 = 0</span>
      <span class="badge">mean 10,20,30</span>
      <span class="badge">15% of 240</span>
      <span class="badge">sqrt(144)</span>
      </p>
      <textarea id="smartInput" placeholder="Type your problem here..."></textarea>
      <button class="primary" onclick="smartSolve()">ðŸš€ Solve Problem</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="algebra"){
    html=`
    <div class="card">
      <h2>ðŸ“ Algebra Solver</h2>
      <label>Equation</label>
      <input id="algInput" placeholder="Example: 3x + 7 = 22">
      <button class="primary" onclick="algebraSolve()">Solve</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="quadratic"){
    html=`
    <div class="card">
      <h2>ðŸ”¢ Quadratic Equation</h2>
      <p style="color:var(--muted)">Solve axÂ² + bx + c = 0</p>
      <div class="grid">
        <input id="qa" type="number" placeholder="a">
        <input id="qb" type="number" placeholder="b">
        <input id="qc" type="number" placeholder="c">
      </div>
      <button class="primary" onclick="quadraticSolve()">Solve</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="calculus"){
    html=`
    <div class="card">
      <h2>âˆ« Calculus</h2>
      <label>Polynomial</label>
      <input id="calcInput" placeholder="Example: 3x^3 + 2x^2 - 5x + 7">
      <div class="grid">
        <button class="primary" onclick="derivative()">Derivative</button>
        <button class="primary" onclick="integral()">Integral</button>
      </div>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="matrix"){
    html=`
    <div class="card">
      <h2>â–¦ 2Ã—2 Matrix Calculator</h2>
      <div class="grid">
        <input id="m11" type="number" placeholder="a">
        <input id="m12" type="number" placeholder="b">
        <input id="m21" type="number" placeholder="c">
        <input id="m22" type="number" placeholder="d">
      </div>
      <button class="primary" onclick="matrixSolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="geometry"){
    html=`
    <div class="card">
      <h2>ðŸ“ Geometry</h2>
      <select id="shape" onchange="geometryFields()">
        <option value="circle">Circle</option>
        <option value="rectangle">Rectangle</option>
        <option value="triangle">Triangle</option>
        <option value="sphere">Sphere</option>
        <option value="cylinder">Cylinder</option>
      </select>
      <div id="geoFields"></div>
      <button class="primary" onclick="geometrySolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
    $("workspace").innerHTML=html;
    geometryFields();
    return;
  }

  if(currentTool==="trig"){
    html=`
    <div class="card">
      <h2>ðŸ“ Trigonometry</h2>
      <input id="trigValue" type="number" placeholder="Angle in degrees">
      <select id="trigFunction">
        <option value="sin">sin</option>
        <option value="cos">cos</option>
        <option value="tan">tan</option>
      </select>
      <button class="primary" onclick="trigSolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="statistics"){
    html=`
    <div class="card">
      <h2>ðŸ“Š Statistics</h2>
      <textarea id="statsInput" placeholder="Enter numbers separated by commas&#10;Example: 10,20,20,30,40"></textarea>
      <button class="primary" onclick="statisticsSolve()">Analyze</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="probability"){
    html=`
    <div class="card">
      <h2>ðŸŽ² Probability</h2>
      <div class="grid">
        <input id="fav" type="number" placeholder="Favorable outcomes">
        <input id="total" type="number" placeholder="Total outcomes">
      </div>
      <button class="primary" onclick="probabilitySolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="physics"){
    html=`
    <div class="card">
      <h2>âš¡ Physics</h2>
      <select id="physicsType">
        <option value="speed">Speed = distance / time</option>
        <option value="force">Force = mass Ã— acceleration</option>
        <option value="work">Work = force Ã— distance</option>
        <option value="kinetic">Kinetic Energy = Â½mvÂ²</option>
        <option value="potential">Potential Energy = mgh</option>
        <option value="ohm">Ohm's Law V = IR</option>
      </select>
      <div id="physicsFields"></div>
      <button class="primary" onclick="physicsSolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
    $("workspace").innerHTML=html;
    physicsFields();
    return;
  }

  if(currentTool==="chemistry"){
    html=`
    <div class="card">
      <h2>ðŸ§ª Chemistry Calculator</h2>
      <select id="chemType">
        <option value="moles">Moles = mass / molar mass</option>
        <option value="mass">Mass = moles Ã— molar mass</option>
        <option value="molarity">Molarity = moles / litres</option>
        <option value="dilution">Dilution Câ‚Vâ‚ = Câ‚‚Vâ‚‚</option>
      </select>
      <div id="chemFields"></div>
      <button class="primary" onclick="chemistrySolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
    $("workspace").innerHTML=html;
    chemistryFields();
    return;
  }

  if(currentTool==="finance"){
    html=`
    <div class="card">
      <h2>ðŸ’° Finance</h2>
      <select id="financeType">
        <option value="simple">Simple Interest</option>
        <option value="compound">Compound Interest</option>
        <option value="discount">Discount</option>
      </select>
      <div id="financeFields"></div>
      <button class="primary" onclick="financeSolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
    $("workspace").innerHTML=html;
    financeFields();
    return;
  }

  if(currentTool==="conversion"){
    html=`
    <div class="card">
      <h2>ðŸ”„ Unit Converter</h2>
      <select id="convType">
        <option value="kmmi">Kilometres â†’ Miles</option>
        <option value="mikm">Miles â†’ Kilometres</option>
        <option value="kgp">Kilograms â†’ Pounds</option>
        <option value="pkg">Pounds â†’ Kilograms</option>
        <option value="cmft">Centimetres â†’ Feet</option>
        <option value="ftcm">Feet â†’ Centimetres</option>
        <option value="cfin">Celsius â†’ Fahrenheit</option>
        <option value="finc">Fahrenheit â†’ Celsius</option>
        <option value="mft">Metres â†’ Feet</option>
        <option value="ftm">Feet â†’ Metres</option>
      </select>
      <input id="convValue" type="number" placeholder="Value">
      <button class="primary" onclick="convertSolve()">Convert</button>
    </div>
    <div id="output"></div>`;
  }

  if(currentTool==="percentage"){
    html=`
    <div class="card">
      <h2>ï¼… Percentage</h2>
      <label>What is X% of Y?</label>
      <div class="grid">
        <input id="px" type="number" placeholder="X">
        <input id="py" type="number" placeholder="Y">
      </div>
      <button class="primary" onclick="percentageSolve()">Calculate</button>
    </div>
    <div id="output"></div>`;
  }

  $("workspace").innerHTML=html;
}

function out(title,answer,steps=[]){
  $("output").innerHTML=`
  <div class="card">
    <div class="result">
      <h3>${title}</h3>
      <div class="answer">${answer}</div>
      ${steps.map((s,i)=>`<div class="step"><b>Step ${i+1}:</b> ${s}</div>`).join("")}
    </div>
  </div>`;
}

function fail(msg){
  $("output").innerHTML=`
  <div class="card">
    <div class="result error">
      <h3>âš ï¸ Cannot solve</h3>
      ${msg}
    </div>
  </div>`;
}

function num(id){
  return Number($(id).value);
}

function cleanNumber(x){
  if(!Number.isFinite(x))return "Undefined";
  return Math.abs(x-Math.round(x))<1e-10
    ? Math.round(x)
    : Number(x.toFixed(8));
}

/* SMART SOLVER */

function smartSolve(){
  let q=$("smartInput").value.trim();
  if(!q)return fail("Enter a problem first.");

  let l=q.toLowerCase();

  if(/^\s*[-+]?[\d.]+%?\s+of\s+[-+]?[\d.]+/.test(l)){
    let m=l.match(/([-+]?\d*\.?\d+)%?\s+of\s+([-+]?\d*\.?\d+)/);
    let ans=Number(m[1])*Number(m[2])/100;
    out("Percentage",cleanNumber(ans),[
      `${m[1]}% Ã— ${m[2]}`,
      `${m[1]} Ã· 100 Ã— ${m[2]} = ${cleanNumber(ans)}`
    ]);
    saveHistory(q,"Smart Solver");
    return;
  }

  if(l.includes("mean ")){
    let nums=l.replace("mean","").split(",").map(Number);
    if(nums.every(Number.isFinite)){
      let mean=nums.reduce((a,b)=>a+b,0)/nums.length;
      out("Mean",cleanNumber(mean),[
        `Add all values = ${nums.reduce((a,b)=>a+b,0)}`,
        `Divide by ${nums.length}`,
        `Mean = ${cleanNumber(mean)}`
      ]);
      return;
    }
  }

  if(/sqrt\s*\(/.test(l)){
    let m=l.match(/sqrt\s*\(\s*([-\d.]+)\s*\)/);
    if(m){
      let x=Number(m[1]);
      out("Square Root",cleanNumber(Math.sqrt(x)),[
        `âˆš${x}`,
        `Answer = ${cleanNumber(Math.sqrt(x))}`
      ]);
      return;
    }
  }

  if(l.includes("=") && /x/.test(l)){
    $("algInput") && ($("algInput").value=q);
    solveLinear(q);
    return;
  }

  if(/x\s*(\^?2|Â²)/.test(l)){
    solveQuadraticText(q);
    return;
  }

  try{
    let result=safeCalculate(q);
    out("Calculated Result",cleanNumber(result),[
      `Expression = ${q}`,
      `Result = ${cleanNumber(result)}`
    ]);
  }catch{
    fail("I don't recognize this problem yet. Try a supported mathematical or scientific format.");
  }
}

/* SAFE BASIC CALCULATOR */

function safeCalculate(expr){
  expr=expr
    .replace(/Ã—/g,"*")
    .replace(/Ã·/g,"/")
    .replace(/\^/g,"**")
    .replace(/Ï€/g,"Math.PI")
    .replace(/sqrt/gi,"Math.sqrt")
    .replace(/sin/gi,"Math.sin")
    .replace(/cos/gi,"Math.cos")
    .replace(/tan/gi,"Math.tan");

  if(!/^[0-9+\-*/().,%\sA-Za-z_*]+$/.test(expr))
    throw Error("Invalid");

  if(expr.includes("%"))
    expr=expr.replace(/(\d+(?:\.\d+)?)%/g,"($1/100)");

  return Function('"use strict";return ('+expr+')')();
}

/* ALGEBRA */

function algebraSolve(){
  solveLinear($("algInput").value);
}

function solveLinear(text){
  let parts=text.split("=");
  if(parts.length!==2)return fail("Use an equation such as 3x + 7 = 22.");

  let L=parseLinear(parts[0]);
  let R=parseLinear(parts[1]);

  let coefficient=L.a-R.a;
  let constant=R.b-L.b;

  if(Math.abs(coefficient)<1e-12)
    return fail("This equation does not have one unique x solution.");

  let x=constant/coefficient;

  out("Linear Equation",`x = ${cleanNumber(x)}`,[
    `Move x terms to one side.`,
    `Move constants to the other side.`,
    `${cleanNumber(coefficient)}x = ${cleanNumber(constant)}`,
    `x = ${cleanNumber(constant)} Ã· ${cleanNumber(coefficient)}`,
    `x = ${cleanNumber(x)}`
  ]);

  saveHistory(text,"Algebra");
}

function parseLinear(s){
  s=s.replace(/\s+/g,"").replace(/âˆ’/g,"-");
  let a=0,b=0;

  let terms=s.replace(/-/g,"+-").split("+").filter(Boolean);

  terms.forEach(t=>{
    if(t.includes("x")){
      let c=t.replace("x","");
      if(c===""||c==="+")c="1";
      if(c==="-")c="-1";
      a+=Number(c);
    }else{
      b+=Number(t);
    }
  });

  return {a,b};
}

/* QUADRATIC */

function quadraticSolve(){
  let a=num("qa"),b=num("qb"),c=num("qc");
  solveQuadraticABC(a,b,c);
}

function solveQuadraticText(text){
  let s=text.replace(/\s+/g,"").replace(/Â²/g,"^2");
  let m=s.match(/^([+-]?\d*\.?\d*)x\^2([+-]\d*\.?\d*)x([+-]\d+\.?\d*)=0$/i);

  if(!m)return fail("Use format like xÂ² - 5x + 6 = 0.");

  let a=m[1]===""||m[1]==="+"?1:m[1]==="-"?-1:Number(m[1]);
  let b=m[2]===""||m[2]==="+"?1:m[2]==="-"?-1:Number(m[2]);
  let c=Number(m[3]);

  solveQuadraticABC(a,b,c);
}

function solveQuadraticABC(a,b,c){
  if(a===0)return fail("a cannot be zero.");

  let D=b*b-4*a*c;

  if(D>0){
    let x1=(-b+Math.sqrt(D))/(2*a);
    let x2=(-b-Math.sqrt(D))/(2*a);

    out("Quadratic Equation",`xâ‚ = ${cleanNumber(x1)}, xâ‚‚ = ${cleanNumber(x2)}`,[
      `Discriminant D = bÂ² âˆ’ 4ac = ${cleanNumber(D)}`,
      `xâ‚ = (âˆ’b + âˆšD) / 2a`,
      `xâ‚‚ = (âˆ’b âˆ’ âˆšD) / 2a`
    ]);
  }
  else if(D===0){
    let x=-b/(2*a);
    out("Quadratic Equation",`x = ${cleanNumber(x)}`,[
      `D = 0, therefore there is one repeated root.`,
      `x = âˆ’b / 2a`,
      `x = ${cleanNumber(x)}`
    ]);
  }
  else{
    let real=-b/(2*a);
    let imag=Math.sqrt(-D)/(2*a);

    out("Quadratic Equation",
      `${cleanNumber(real)} Â± ${cleanNumber(Math.abs(imag))}i`,
      [
        `D = ${cleanNumber(D)}`,
        `The roots are complex.`,
        `Real part = ${cleanNumber(real)}`,
        `Imaginary part = ${cleanNumber(Math.abs(imag))}`
      ]);
  }
}

/* CALCULUS */

function polynomialTerms(s){
  s=s.replace(/\s+/g,"").replace(/-/g,"+-");
  return s.split("+").filter(Boolean);
}

function derivative(){
  let s=$("calcInput").value;
  let terms=polynomialTerms(s);
  let result=[];

  for(let t of terms){
    let m=t.match(/^([+-]?\d*\.?\d*)x(?:\^(\d+))?$/i);

    if(m){
      let c=m[1]===""||m[1]==="+"?1:m[1]==="-"?-1:Number(m[1]);
      let p=m[2]?Number(m[2]):1;

      if(p===1) result.push(String(c));
      else{
        let nc=c*p;
        let np=p-1;
        result.push(`${nc===1?"":nc===-1?"-":nc}x${np===1?"":"^"+np}`);
      }
    }else{
      if(!isNaN(Number(t)))continue;
      return fail("Use a polynomial such as 3x^3 + 2x^2 - 5x + 7.");
    }
  }

  out("Derivative",result.join(" + ").replace(/\+\s-/g,"- "),[
    "Apply the power rule: d/dx(xâ¿) = nÂ·xâ¿â»Â¹.",
    "Differentiate each polynomial term.",
    `Result = ${result.join(" + ").replace(/\+\s-/g,"- ")}`
  ]);
}

function integral(){
  let s=$("calcInput").value;
  let terms=polynomialTerms(s);
  let result=[];

  for(let t of terms){
    let m=t.match(/^([+-]?\d*\.?\d*)x(?:\^(\d+))?$/i);

    if(m){
      let c=m[1]===""||m[1]==="+"?1:m[1]==="-"?-1:Number(m[1]);
      let p=m[2]?Number(m[2]):1;
      let np=p+1;
      let nc=c/np;

      result.push(`${nc===1?"":nc===-1?"-":nc}x^${np}`);
    }else{
      if(!isNaN(Number(t))){
        let c=Number(t);
        result.push(`${c}x`);
      }else return fail("Use a polynomial.");
    }
  }

  result.push("C");

  out("Indefinite Integral",result.join(" + ").replace(/\+\s-/g,"- "),[
    "Apply âˆ«xâ¿ dx = xâ¿âºÂ¹/(n+1).",
    "Integrate every term.",
    "Add the constant of integration C."
  ]);
}

/* MATRIX */

function matrixSolve(){
  let a=num("m11"),b=num("m12"),c=num("m21"),d=num("m22");
  let det=a*d-b*c;

  if(det===0)
    return fail("The determinant is zero, so this matrix has no inverse.");

  let inverse=`
  [ ${cleanNumber(d/det)}   ${cleanNumber(-b/det)} ]<br>
  [ ${cleanNumber(-c/det)}   ${cleanNumber(a/det)} ]
  `;

  out("2Ã—2 Matrix",`Determinant = ${cleanNumber(det)}`,[
    `det(A) = ad âˆ’ bc`,
    `det(A) = ${a}Ã—${d} âˆ’ ${b}Ã—${c}`,
    `det(A) = ${cleanNumber(det)}`,
    `<b>Inverse:</b><br>${inverse}`
  ]);
}

/* GEOMETRY */

function geometryFields(){
  let type=$("shape").value;

  let html="";

  if(type==="circle")
    html=`<input id="g1" type="number" placeholder="Radius">`;

  if(type==="rectangle")
    html=`<div class="grid"><input id="g1" type="number" placeholder="Length"><input id="g2" type="number" placeholder="Width"></div>`;

  if(type==="triangle")
    html=`<div class="grid"><input id="g1" type="number" placeholder="Base"><input id="g2" type="number" placeholder="Height"></div>`;

  if(type==="sphere")
    html=`<input id="g1" type="number" placeholder="Radius">`;

  if(type==="cylinder")
    html=`<div class="grid"><input id="g1" type="number" placeholder="Radius"><input id="g2" type="number" placeholder="Height"></div>`;

  $("geoFields").innerHTML=html;
}

function geometrySolve(){
  let type=$("shape").value;
  let a=Number($("g1").value);
  let b=$("g2")?Number($("g2").value):0;

  if(type==="circle"){
    out("Circle",
      `Area = ${cleanNumber(Math.PI*a*a)}`,
      [
        `Area = Ï€rÂ²`,
        `Circumference = ${cleanNumber(2*Math.PI*a)}`
      ]);
  }

  if(type==="rectangle"){
    out("Rectangle",
      `Area = ${cleanNumber(a*b)}`,
      [
        `Area = length Ã— width`,
        `Perimeter = ${cleanNumber(2*(a+b))}`
      ]);
  }

  if(type==="triangle"){
    out("Triangle",
      `Area = ${cleanNumber(.5*a*b)}`,
      [
        `Area = Â½ Ã— base Ã— height`,
        `Area = ${cleanNumber(.5*a*b)}`
      ]);
  }

  if(type==="sphere"){
    out("Sphere",
      `Volume = ${cleanNumber(4/3*Math.PI*a**3)}`,
      [
        `V = 4/3Ï€rÂ³`,
        `Surface area = ${cleanNumber(4*Math.PI*a*a)}`
      ]);
  }

  if(type==="cylinder"){
    out("Cylinder",
      `Volume = ${cleanNumber(Math.PI*a*a*b)}`,
      [
        `V = Ï€rÂ²h`,
        `V = ${cleanNumber(Math.PI*a*a*b)}`
      ]);
  }
}

/* TRIG */

function trigSolve(){
  let x=num("trigValue");
  let fn=$("trigFunction").value;
  let rad=x*Math.PI/180;
  let ans=Math[fn](rad);

  out("Trigonometry",
    `${fn}(${x}Â°) = ${cleanNumber(ans)}`,
    [
      `Convert degrees to radians: ${x} Ã— Ï€ / 180`,
      `Radians = ${cleanNumber(rad)}`,
      `${fn}(${x}Â°) = ${cleanNumber(ans)}`
    ]);
}

/* STATISTICS */

function statisticsSolve(){
  let arr=$("statsInput").value.split(",").map(Number).filter(Number.isFinite);

  if(!arr.length)return fail("Enter numbers separated by commas.");

  let sorted=[...arr].sort((a,b)=>a-b);
  let sum=arr.reduce((a,b)=>a+b,0);
  let mean=sum/arr.length;

  let median=sorted.length%2
    ? sorted[Math.floor(sorted.length/2)]
    : (sorted[sorted.length/2-1]+sorted[sorted.length/2])/2;

  let freq={};
  arr.forEach(x=>freq[x]=(freq[x]||0)+1);
  let maxFreq=Math.max(...Object.values(freq));
  let modes=Object.keys(freq).filter(x=>freq[x]===maxFreq);

  let variance=arr.reduce((s,x)=>s+(x-mean)**2,0)/arr.length;
  let sd=Math.sqrt(variance);

  out("Statistics",
    `Mean = ${cleanNumber(mean)}`,
    [
      `Sorted data: ${sorted.join(", ")}`,
      `Median = ${cleanNumber(median)}`,
      `Mode = ${maxFreq>1?modes.join(", "):"No repeated mode"}`,
      `Population variance = ${cleanNumber(variance)}`,
      `Population standard deviation = ${cleanNumber(sd)}`,
      `Minimum = ${sorted[0]}`,
      `Maximum = ${sorted[sorted.length-1]}`
    ]);
}

/* PROBABILITY */

function probabilitySolve(){
  let fav=num("fav"),total=num("total");

  if(total<=0 || fav<0 || fav>total)
    return fail("Check your outcomes.");

  let p=fav/total;

  out("Probability",
    `${cleanNumber(p)} (${cleanNumber(p*100)}%)`,
    [
      `P(E) = favorable outcomes / total outcomes`,
      `P(E) = ${fav}/${total}`,
      `P(E) = ${cleanNumber(p)}`
    ]);
}

/* PHYSICS */

function physicsFields(){
  let type=$("physicsType").value;

  const fields={
    speed:["Distance","Time"],
    force:["Mass","Acceleration"],
    work:["Force","Distance"],
    kinetic:["Mass","Velocity"],
    potential:["Mass","Height"],
    ohm:["Resistance","Current"]
  };

  $("physicsFields").innerHTML=`
    <div class="grid">
      ${fields[type].map((x,i)=>`
        <input id="ph${i}" type="number" placeholder="${x}">
      `).join("")}
    </div>`;
}

document.addEventListener("change",e=>{
  if(e.target.id==="physicsType")physicsFields();
  if(e.target.id==="chemType")chemistryFields();
  if(e.target.id==="financeType")financeFields();
});

function physicsSolve(){
  let type=$("physicsType").value;
  let a=num("ph0"),b=num("ph1");
  let ans,formula;

  if(type==="speed"){ans=a/b;formula="v=d/t";}
  if(type==="force"){ans=a*b;formula="F=ma";}
  if(type==="work"){ans=a*b;formula="W=Fd";}
  if(type==="kinetic"){ans=.5*a*b*b;formula="KE=Â½mvÂ²";}
  if(type==="potential"){ans=a*9.80665*b;formula="PE=mgh";}
  if(type==="ohm"){ans=a*b;formula="V=IR";}

  out("Physics",cleanNumber(ans),[
    `Formula: ${formula}`,
    `Substitute the given values.`,
    `Answer = ${cleanNumber(ans)}`
  ]);
}

/* CHEMISTRY */

function chemistryFields(){
  let type=$("chemType").value;

  let html="";

  if(type==="moles")
    html=`<div class="grid"><input id="ch0" type="number" placeholder="Mass (g)"><input id="ch1" type="number" placeholder="Molar mass (g/mol)"></div>`;

  if(type==="mass")
    html=`<div class="grid"><input id="ch0" type="number" placeholder="Moles"><input id="ch1" type="number" placeholder="Molar mass"></div>`;

  if(type==="molarity")
    html=`<div class="grid"><input id="ch0" type="number" placeholder="Moles"><input id="ch1" type="number" placeholder="Volume (L)"></div>`;

  if(type==="dilution")
    html=`<div class="grid">
      <input id="ch0" type="number" placeholder="C1">
      <input id="ch1" type="number" placeholder="V1">
      <input id="ch2" type="number" placeholder="C2">
    </div>`;

  $("chemFields").innerHTML=html;
}

function chemistrySolve(){
  let type=$("chemType").value;
  let a=Number($("ch0").value);
  let b=Number($("ch1").value);
  let ans;

  if(type==="moles")ans=a/b;
  if(type==="mass")ans=a*b;
  if(type==="molarity")ans=a/b;
  if(type==="dilution"){
    let c2=Number($("ch2").value);
    ans=(a*b)/c2;
  }

  out("Chemistry",cleanNumber(ans),[
    "Apply the selected chemistry formula.",
    `Answer = ${cleanNumber(ans)}`
  ]);
}

/* FINANCE */

function financeFields(){
  let type=$("financeType").value;

  if(type==="simple"||type==="compound"){
    $("financeFields").innerHTML=`
      <div class="grid">
        <input id="fi0" type="number" placeholder="Principal">
        <input id="fi1" type="number" placeholder="Annual rate %">
        <input id="fi2" type="number" placeholder="Time in years">
      </div>`;
  }else{
    $("financeFields").innerHTML=`
      <div class="grid">
        <input id="fi0" type="number" placeholder="Original price">
        <input id="fi1" type="number" placeholder="Discount %">
      </div>`;
  }
}

function financeSolve(){
  let type=$("financeType").value;
  let P=num("fi0"),r=num("fi1"),t=num("fi2");

  if(type==="simple"){
    let interest=P*r/100*t;
    out("Simple Interest",
      `Amount = ${cleanNumber(P+interest)}`,
      [
        `I = Prt`,
        `Interest = ${cleanNumber(interest)}`,
        `Final amount = ${cleanNumber(P+interest)}`
      ]);
  }

  if(type==="compound"){
    let amount=P*(1+r/100)**t;
    out("Compound Interest",
      `Amount = ${cleanNumber(amount)}`,
      [
        `A = P(1+r/100)^t`,
        `A = ${cleanNumber(amount)}`,
        `Interest = ${cleanNumber(amount-P)}`
      ]);
  }

  if(type==="discount"){
    let discount=P*r/100;
    out("Discount",
      `Final Price = ${cleanNumber(P-discount)}`,
      [
        `Discount = ${cleanNumber(discount)}`,
        `Final price = original price âˆ’ discount`,
        `Final price = ${cleanNumber(P-discount)}`
      ]);
  }
}

/* CONVERTER */

function convertSolve(){
  let v=num("convValue");
  let type=$("convType").value;
  let ans,unit;

  const data={
    kmmi:[0.621371,"miles"],
    mikm:[1.609344,"km"],
    kgp:[2.2046226218,"lb"],
    pkg:[0.45359237,"kg"],
    cmft:[0.032808399,"ft"],
    ftcm:[30.48,"cm"],
    cfin:[null,"Â°F"],
    finc:[null,"Â°C"],
    mft:[3.280839895,"ft"],
    ftm:[0.3048,"m"]
  };

  if(type==="cfin"){
    ans=v*9/5+32;
  }else if(type==="finc"){
    ans=(v-32)*5/9;
  }else{
    ans=v*data[type][0];
  }

  unit=data[type][1];

  out("Unit Conversion",
    `${cleanNumber(ans)} ${unit}`,
    [
      `Input = ${v}`,
      `Conversion completed.`,
      `Result = ${cleanNumber(ans)} ${unit}`
    ]);
}

/* PERCENTAGE */

function percentageSolve(){
  let x=num("px"),y=num("py");
  let ans=x*y/100;

  out("Percentage",
    `${cleanNumber(ans)}`,
    [
      `${x}% of ${y}`,
      `${x}/100 Ã— ${y}`,
      `Answer = ${cleanNumber(ans)}`
    ]);
}

/* HISTORY */

function saveHistory(input,type){
  historyData.unshift({input,type});
  if(historyData.length>20)historyData.pop();
}

function restoreHistory(i){
  let item=historyData[i];
  setTool("smart");
  render();
  $("smartInput").value=item.input;
}

function clearHistory(){
  historyData=[];
  render();
}

function escapeHTML(str){
  return str.replace(/[&<>"']/g,m=>({
    "&":"&amp;",
    "<":"&lt;",
    ">":"&gt;",
    '"':"&quot;",
    "'":"&#039;"
  }[m]));
}

/* INITIALIZE */

render();
</script>

</body>
</html>
