# MIMO LAND


const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

let level = 0;
const totalLevels = 15;
let player = { x: 50, y: 180, size: 20 };
let keys = {};

document.addEventListener("keydown", (e) => keys[e.key] = true);
document.addEventListener("keyup", (e) => keys[e.key] = false);

function drawPlayer() {
    ctx.fillStyle = "red";
    ctx.fillRect(player.x, player.y, player.size, player.size);
}

function update() {
    if (keys["ArrowRight"]) player.x += 3;
    if (keys["ArrowLeft"]) player.x -= 3;
    if (keys["ArrowUp"]) player.y -= 3;
    if (keys["ArrowDown"]) player.y += 3;

    if (player.x > canvas.width - player.size) {
        level++;
        if (level < totalLevels) {
            player.x = 50;
            player.y = 180;
            alert("Level " + level + "!");
        } else {
            alert("Du hast alle 15 Level geschafft! 🎉");
            level = 0;
            player.x = 50;
            player.y = 180;
        }
    }
}

function loop() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawPlayer();
    update();
    requestAnimationFrame(loop);
}

loop();
body {
    background: linear-gradient(to bottom, #dfe9f3, #ffffff);
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 0;
    padding: 0;
}
canvas {
    border: 2px solid #000;
    margin-top: 20px;
}
h1 {
    font-size: 36px;
    color: #003366;
}

