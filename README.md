# juego-ley-signos.
Juego interactivo para aprender la ley de signos en la multiplicación de números enteros
[index.html](https://github.com/user-attachments/files/25860092/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Juego Ley de Signos</title>

<style>

body{
font-family: Arial;
background: linear-gradient(135deg,#4facfe,#00f2fe);
text-align:center;
color:white;
}

h1{
margin-top:20px;
}

#tablero{
margin-top:40px;
}

.carta{
display:inline-block;
width:140px;
height:140px;
margin:20px;
font-size:70px;
line-height:140px;
border-radius:15px;
background:white;
color:black;
cursor:pointer;
transition:0.3s;
box-shadow:0 6px 12px rgba(0,0,0,0.3);
}

.carta:hover{
transform:scale(1.1);
}

.oculta{
background:#222;
color:white;
}

#resultado{
font-size:30px;
margin-top:20px;
font-weight:bold;
}

.correcto{
color:#00ff9c;
}

.incorrecto{
color:#ff4b5c;
}

#puntajes{
margin-top:20px;
font-size:22px;
}

button{
padding:12px 25px;
font-size:18px;
margin-top:20px;
border:none;
border-radius:10px;
background:#222;
color:white;
cursor:pointer;
}

button:hover{
background:#444;
}

#ronda{
font-size:20px;
margin-top:10px;
}

</style>
</head>

<body>

<h1>🎮 Juego: Descubre el Signo Oculto</h1>

<p>Escoge un signo. Si coincide con el oculto ganas punto.</p>

<div id="ronda">Ronda: 1</div>

<div id="tablero">

<div class="carta" onclick="elegir('+')">+</div>
<div class="carta" onclick="elegir('-')">−</div>
<div class="carta oculta" id="oculta">?</div>

</div>

<div id="resultado"></div>

<div id="puntajes">
Equipo A: <span id="pA">0</span> ⭐ |
Equipo B: <span id="pB">0</span> ⭐
</div>

<button onclick="nuevaRonda()">Nueva ronda</button>

<script>

let signos = ['+','-']
let signoOculto = signos[Math.floor(Math.random()*2)]

let equipoActual = "A"
let puntosA = 0
let puntosB = 0
let ronda = 1

function elegir(signoJugador){

document.getElementById("oculta").innerText = signoOculto

if(signoJugador === signoOculto){

document.getElementById("resultado").innerHTML =
"✅ Resultado POSITIVO (+) ¡Punto para equipo "+equipoActual+"!"

document.getElementById("resultado").className="correcto"

if(equipoActual=="A"){
puntosA++
}else{
puntosB++
}

}else{

document.getElementById("resultado").innerHTML =
"❌ Resultado NEGATIVO (-) No hay punto"

document.getElementById("resultado").className="incorrecto"

}

actualizarPuntaje()

}

function actualizarPuntaje(){

document.getElementById("pA").innerText = puntosA
document.getElementById("pB").innerText = puntosB

}

function nuevaRonda(){

signoOculto = signos[Math.floor(Math.random()*2)]

document.getElementById("oculta").innerText = "?"

document.getElementById("resultado").innerText = ""

if(equipoActual=="A"){
equipoActual="B"
}else{
equipoActual="A"
}

ronda++

document.getElementById("ronda").innerText="Ronda: "+ronda+" | Turno equipo "+equipoActual

}

</script>

</body>
</html>
