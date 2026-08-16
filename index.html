<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Egg Assault</title>

<style>
*{box-sizing:border-box}
html,body{
    margin:0;
    width:100%;
    height:100%;
    overflow:hidden;
    background:#111;
    font-family:Arial,sans-serif;
}
canvas{
    display:block;
    width:100%;
    height:100%;
    cursor:crosshair;
}
#hud{
    position:fixed;
    left:20px;
    bottom:20px;
    z-index:5;
    color:white;
    font-weight:bold;
    font-size:20px;
    text-shadow:2px 2px #000;
}
#ammo{
    position:fixed;
    right:25px;
    bottom:20px;
    color:white;
    font-size:28px;
    font-weight:bold;
    text-shadow:2px 2px #000;
}
#start{
    position:fixed;
    inset:0;
    z-index:10;
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    background:rgba(0,0,0,.75);
    color:white;
    text-align:center;
}
#start h1{
    font-size:60px;
    margin:0 0 10px;
}
button{
    padding:14px 25px;
    border:0;
    border-radius:8px;
    background:#ffb400;
    font-size:20px;
    font-weight:bold;
    cursor:pointer;
}
</style>
</head>

<body>

<canvas id="game"></canvas>

<div id="hud">
    ❤️ <span id="health">100</span>
    &nbsp;&nbsp;
    ☠️ <span id="kills">0</span>
</div>

<div id="ammo">
    <span id="ammoCount">12</span> / 60
</div>

<div id="start">
    <h1>🥚 EGG ASSAULT</h1>
    <p>WASD = Move &nbsp; | &nbsp; Mouse = Aim</p>
    <p>Click = Shoot &nbsp; | &nbsp; R = Reload</p>
    <button onclick="startGame()">PLAY</button>
</div>

<script>

const canvas=document.getElementById("game");
const ctx=canvas.getContext("2d");

let W,H;

function resize(){
    W=canvas.width=innerWidth;
    H=canvas.height=innerHeight;
}

addEventListener("resize",resize);
resize();

/* =========================
   GAME STATE
========================= */

let playing=false;
let dead=false;

const keys={};

let mouseX=0;
let mouseY=0;

document.addEventListener("keydown",e=>{
    keys[e.key.toLowerCase()]=true;

    if(e.key.toLowerCase()==="r"){
        reload();
    }
});

document.addEventListener("keyup",e=>{
    keys[e.key.toLowerCase()]=false;
});

/* =========================
   PLAYER
========================= */

const player={
    x:400,
    y:300,
    angle:0,
    health:100,
    ammo:12,
    reserve:60,
    kills:0
};

/* =========================
   SIMPLE MAP
========================= */

const walls=[
    {x:100,y:100,w:700,h:30},
    {x:100,y:500,w:700,h:30},

    {x:100,y:100,w:30,h:430},
    {x:770,y:100,w:30,h:430},

    {x:300,y:180,w:40,h:180},
    {x:520,y:340,w:40,h:160},

    {x:600,y:180,w:120,h:40}
];

/* =========================
   ENEMIES
========================= */

let enemies=[];

function spawnEnemies(){

    enemies=[
        {
            x:650,
            y:260,
            health:100,
            alive:true,
            cooldown:0
        },

        {
            x:200,
            y:420,
            health:100,
            alive:true,
            cooldown:0
        },

        {
            x:680,
            y:450,
            health:100,
            alive:true,
            cooldown:0
        }
    ];
}

/* =========================
   START
========================= */

function startGame(){

    playing=true;
    dead=false;

    document.getElementById("start")
        .style.display="none";

    canvas.requestPointerLock();

    spawnEnemies();
}

/* =========================
   MOUSE
========================= */

document.addEventListener("mousemove",e=>{

    if(document.pointerLockElement!==canvas)
        return;

    player.angle+=e.movementX*.003;
});

canvas.addEventListener("click",()=>{

    if(!playing) return;

    shoot();
});

/* =========================
   COLLISION
========================= */

function wallCollision(x,y){

    for(const w of walls){

        if(
            x>w.x &&
            x<w.x+w.w &&
            y>w.y &&
            y<w.y+w.h
        ){
            return true;
        }
    }

    return false;
}

/* =========================
   UPDATE
========================= */

function update(){

    if(!playing||dead)
        return;

    let speed=3;

    let dx=0;
    let dy=0;

    if(keys["w"]){
        dx+=Math.cos(player.angle);
        dy+=Math.sin(player.angle);
    }

    if(keys["s"]){
        dx-=Math.cos(player.angle);
        dy-=Math.sin(player.angle);
    }

    if(keys["a"]){
        dx+=Math.cos(player.angle-Math.PI/2);
        dy+=Math.sin(player.angle-Math.PI/2);
    }

    if(keys["d"]){
        dx+=Math.cos(player.angle+Math.PI/2);
        dy+=Math.sin(player.angle+Math.PI/2);
    }

    const length=Math.hypot(dx,dy);

    if(length){

        dx/=length;
        dy/=length;

        const nx=player.x+dx*speed;
        const ny=player.y+dy*speed;

        if(!wallCollision(nx,player.y))
            player.x=nx;

        if(!wallCollision(player.x,ny))
            player.y=ny;
    }

    updateEnemies();

    document.getElementById("health")
        .textContent=Math.max(0,Math.floor(player.health));

    document.getElementById("ammoCount")
        .textContent=player.ammo;

    document.getElementById("kills")
        .textContent=player.kills;

    if(player.health<=0){
        gameOver();
    }
}

/* =========================
   ENEMY AI
========================= */

function updateEnemies(){

    for(const enemy of enemies){

        if(!enemy.alive)
            continue;

        const dx=player.x-enemy.x;
        const dy=player.y-enemy.y;

        const distance=Math.hypot(dx,dy);

        enemy.cooldown--;

        if(distance>100){

            const nx=
                enemy.x+
                dx/distance*.7;

            const ny=
                enemy.y+
                dy/distance*.7;

            if(!wallCollision(nx,enemy.y))
                enemy.x=nx;

            if(!wallCollision(enemy.x,ny))
                enemy.y=ny;
        }

        if(
            distance<400 &&
            enemy.cooldown<=0 &&
            clearShot(enemy.x,enemy.y)
        ){

            player.health-=5;

            enemy.cooldown=60;
        }
    }
}

function clearShot(x,y){

    const dx=player.x-x;
    const dy=player.y-y;

    const distance=Math.hypot(dx,dy);

    for(let i=0;i<distance;i+=10){

        const t=i/distance;

        const px=x+dx*t;
        const py=y+dy*t;

        if(wallCollision(px,py))
            return false;
    }

    return true;
}

/* =========================
   SHOOT
========================= */

function shoot(){

    if(player.ammo<=0){
        reload();
        return;
    }

    player.ammo--;

    let target=null;
    let best=Infinity;

    for(const enemy of enemies){

        if(!enemy.alive)
            continue;

        const dx=enemy.x-player.x;
        const dy=enemy.y-player.y;

        const distance=Math.hypot(dx,dy);

        let angle=
            Math.atan2(dy,dx)-player.angle;

        while(angle>Math.PI)
            angle-=Math.PI*2;

        while(angle<-Math.PI)
            angle+=Math.PI*2;

        if(
            Math.abs(angle)<.12 &&
            distance<best &&
            clearShot(enemy.x,enemy.y)
        ){

            target=enemy;
            best=distance;
        }
    }

    if(target){

        target.health-=50;

        if(target.health<=0){

            target.alive=false;
            player.kills++;
        }
    }
}

/* =========================
   RELOAD
========================= */

function reload(){

    const needed=12-player.ammo;

    const amount=Math.min(
        needed,
        player.reserve
    );

    player.ammo+=amount;
    player.reserve-=amount;
}

/* =========================
   DRAW
========================= */

function draw(){

    /* sky */

    ctx.fillStyle="#6bc9ff";
    ctx.fillRect(0,0,W,H/2);

    /* ground */

    ctx.fillStyle="#4d553d";
    ctx.fillRect(0,H/2,W,H/2);

    /* horizon */

    ctx.fillStyle="#ddd";
    ctx.fillRect(0,H/2-5,W,10);

    /*
       This is a simple 2D arena rendered
       from a top-down perspective.
    */

    const scale=.8;

    ctx.save();

    ctx.translate(
        W/2-player.x*scale,
        H/2-player.y*scale
    );

    ctx.scale(scale,scale);

    /* walls */

    for(const w of walls){

        ctx.fillStyle="#777";

        ctx.fillRect(
            w.x,
            w.y,
            w.w,
            w.h
        );

        ctx.fillStyle="#aaa";

        ctx.fillRect(
            w.x,
            w.y,
            w.w,
            8
        );
    }

    /* enemies */

    for(const enemy of enemies){

        if(!enemy.alive)
            continue;

        drawEgg(
            enemy.x,
            enemy.y,
            "#ff4141"
        );
    }

    /* player */

    drawEgg(
        player.x,
        player.y,
        "#fff"
    );

    /* player direction */

    ctx.strokeStyle="#222";
    ctx.lineWidth=6;

    ctx.beginPath();

    ctx.moveTo(
        player.x,
        player.y
    );

    ctx.lineTo(
        player.x+
        Math.cos(player.angle)*45,

        player.y+
        Math.sin(player.angle)*45
    );

    ctx.stroke();

    ctx.restore();

    /* crosshair */

    ctx.strokeStyle="white";
    ctx.lineWidth=2;

    ctx.beginPath();

    ctx.moveTo(W/2-8,H/2);
    ctx.lineTo(W/2+8,H/2);

    ctx.moveTo(W/2,H/2-8);
    ctx.lineTo(W/2,H/2+8);

    ctx.stroke();

    /* gun */

    drawGun();
}

/* =========================
   EGG
========================= */

function drawEgg(x,y,color){

    ctx.save();

    ctx.translate(x,y);

    ctx.fillStyle=color;

    ctx.beginPath();

    ctx.ellipse(
        0,
        0,
        20,
        27,
        0,
        0,
        Math.PI*2
    );

    ctx.fill();

    /* eyes */

    ctx.fillStyle="#111";

    ctx.beginPath();

    ctx.arc(
        -7,
        -5,
        3,
        0,
        Math.PI*2
    );

    ctx.arc(
        7,
        -5,
        3,
        0,
        Math.PI*2
    );

    ctx.fill();

    ctx.restore();
}

/* =========================
   GUN
========================= */

function drawGun(){

    const gunW=220;
    const gunH=100;

    const x=W/2-gunW/2;
    const y=H-gunH+20;

    ctx.fillStyle="#222";

    ctx.fillRect(
        x+70,
        y,
        80,
        100
    );

    ctx.fillStyle="#555";

    ctx.fillRect(
        x+95,
        y-35,
        30,
        65
    );

    ctx.fillStyle="#111";

    ctx.fillRect(
        x+25,
        y+35,
        170,
        25
    );

    ctx.fillStyle="#c88b52";

    ctx.fillRect(
        x+70,
        y+65,
        80,
        45
    );
}

/* =========================
   GAME OVER
========================= */

function gameOver(){

    dead=true;
    playing=false;

    document.getElementById("start")
        .style.display="flex";

    document.querySelector("#start h1")
        .textContent="💀 GAME OVER";

    document.querySelector("#start p")
        .textContent=
        "Kills: "+player.kills;

    document.querySelector("#start button")
        .textContent="PLAY AGAIN";
}

/* =========================
   LOOP
========================= */

function loop(){

    update();
    draw();

    requestAnimationFrame(loop);
}

loop();

</script>

</body>
</html>
