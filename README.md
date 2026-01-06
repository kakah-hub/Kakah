<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Mensagem pro Primo</title>

<style>
body{
    margin:0;
    height:100vh;
    background:linear-gradient(135deg,#000,#1a0033);
    display:flex;
    align-items:center;
    justify-content:center;
    font-family:'Segoe UI',sans-serif;
    color:white;
    overflow:hidden;
}

.box{
    background:rgba(255,255,255,0.06);
    backdrop-filter:blur(10px);
    border-radius:25px;
    padding:40px;
    max-width:650px;
    text-align:center;
    box-shadow:0 0 35px rgba(255,0,150,0.25);
    animation:fade 3s;
}

h1{
    color:#ff77ff;
    margin-bottom:20px;
}

#texto{
    font-size:18px;
    line-height:1.7;
    white-space:pre-line;
    min-height:260px;
}

button{
    margin-top:30px;
    padding:15px 35px;
    border:none;
    border-radius:40px;
    background:#ff77ff;
    color:#000;
    font-size:17px;
    cursor:pointer;
    transition:0.3s;
}

button:hover{
    transform:scale(1.1);
}

.final{
    font-size:23px;
    color:#8fd3ff;
    margin-top:25px;
    animation:pulse 1.4s infinite;
}

@keyframes fade{
    from{opacity:0; transform:translateY(40px);}
    to{opacity:1; transform:translateY(0);}
}

@keyframes pulse{
    0%{transform:scale(1);}
    50%{transform:scale(1.08);}
    100%{transform:scale(1);}
}

.emoji{
    position:absolute;
    font-size:22px;
    animation:float 6s linear infinite;
}

@keyframes float{
    from{transform:translateY(100vh);}
    to{transform:translateY(-10vh);}
}
</style>
</head>

<body>

<div class="box">
    <h1>Ei primo… 👀</h1>
    <div id="texto"></div>
    <button onclick="iniciar()">Clica aqui</button>
    <div id="final"></div>
</div>

<audio id="musica" src="https://cdn.pixabay.com/audio/2022/03/15/audio_4c38d6e25a.mp3"></audio>

<script>
const mensagens = [
"Calma aí antes de rir 😂\n\n",
"Isso aqui NÃO é vírus.\n",
"Não vai explodir seu celular.\n\n",
"Mas confessa...\n",
"você achou que era pegadinha né? 😏\n\n",
"Aliás...\n",
"desde pequeno você sempre foi meio doido.\n",
"Me zoava, brigava, ria alto demais...\n\n",
"E mesmo assim...\n\n",
"era você que estava comigo nas horas boas.\n\n",
"Quando ninguém entendia,\n",
"você estava lá.\n\n",
"Primo não é só parente.\n",
"Às vezes é irmão escolhido.\n\n",
"Obrigado por cada risada,\n",
"por cada zoeira,\n",
"e por nunca virar as costas.\n"
];

let i = 0, j = 0;

function iniciar(){
    document.getElementById("texto").innerHTML = "";
    document.getElementById("final").innerHTML = "";
    document.getElementById("musica").play();
    digitar();
    setInterval(criarEmoji, 500);
}

function digitar(){
    if(i < mensagens.length){
        if(j < mensagens[i].length){
            document.getElementById("texto").innerHTML += mensagens[i].charAt(j);
            j++;
            setTimeout(digitar, 50);
        } else {
            i++;
            j = 0;
            setTimeout(digitar, 700);
        }
    } else {
        setTimeout(()=>{
            document.getElementById("final").innerHTML =
            "<div class='final'>Te amo, seu idiota ❤️😂</div>";
        }, 1200);
    }
}

function criarEmoji(){
    const emojis = ["😂","🔥","😎","❤️","🤜🤛"];
    const e = document.createElement("div");
    e.className = "emoji";
    e.innerHTML = emojis[Math.floor(Math.random()*emojis.length)];
    e.style.left = Math.random()*100 + "vw";
    document.body.appendChild(e);
    setTimeout(()=>e.remove(),6000);
}
</script>

</body>
</html>
