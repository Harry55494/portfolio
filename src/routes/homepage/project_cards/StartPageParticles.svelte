<script>

    import {onMount} from "svelte";

    export let width;
    export let height;

    let particleColor = "rgba(0, 0, 0)";
    
    onMount(() => {

        function background () {
            const canvas = document.getElementById('canvas');
            const ctx = canvas.getContext('2d');
            console.log(width);
            canvas.width = width;
            ctx.canvas.width = width;
            ctx.canvas.height = height;

            let particlesArray;


            class Particle {
                constructor(x, y, directionX, directionY, size, colour) {
                    this.x = x;
                    this.y = y;
                    this.speedX = directionX;
                    this.speedY = directionY;
                    this.size = size;
                    this.colour = colour;
                }

                draw() {
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2, false);
                    ctx.fillStyle = this.colour;
                    ctx.fill();
                }

                update() {
                    if (this.x - 50 > canvas.width || this.x + 50 < 0) {
                        this.speedX = -this.speedX;
                    }
                    if (this.y - 50 > canvas.height || this.y + 50 < 0) {
                        this.speedY = -this.speedY;
                    }

                    this.x += this.speedX;
                    this.y += this.speedY;

                    this.colour = particleColor;

                    this.draw();

                }

            }

            function init() {
                particlesArray = [];
                let numberOfParticles = (canvas.height * canvas.width) / 1500;
                for (let i = 0; i < numberOfParticles; i++) {
                    let size = Math.random() + 1.5;
                    let x = ((Math.random() * (canvas.width + 30)) - 15);
                    let y = ((Math.random() * (canvas.height + 30)) - 15);
                    let speedX = ((Math.random() * size) - 0.75) * (1 / (1.5*size));
                    let speedY = ((Math.random() * size) - 0.75) * (1 / (1.5*size));
                    particlesArray.push(new Particle(x, y, speedX, speedY, size, particleColor));
                }
            }

            function animate() {
                requestAnimationFrame(animate);
                ctx.clearRect(0, 0, innerWidth*2, innerHeight*2);
                for (let i = 0; i < particlesArray.length; i++) {
                    particlesArray[i].update();

                }

                ctx.font = "50px Fira Code";
                ctx.fillStyle = particleColor;
                ctx.fillText("Start Page", ctx.canvas.width / 2 - 145, ctx.canvas.height / 2 + 15);
                connect();
            }

            function connect(){
                let opacity = 1;
                for (let a = 0; a < particlesArray.length; a++) {
                    for (let b = a; b < particlesArray.length; b++) {
                        let distance = ((particlesArray[a].x - particlesArray[b].x) * (particlesArray[a].x - particlesArray[b].x)) + ((particlesArray[a].y - particlesArray[b].y) * (particlesArray[a].y - particlesArray[b].y));
                        if (distance < (canvas.width/4) * (canvas.height/4)) {
                            opacity = 1 - (distance / 2000);
                            ctx.strokeStyle = (particleColor.substring(0, particleColor.length - 1)) + ',' + opacity + ')';
                            ctx.lineWidth = 1;
                            ctx.beginPath();
                            ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                            ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                            ctx.stroke();
                        }
                    }
                }
            }

            init();
            animate();
        }

        background();

    });

</script>

<main>

    <div id="container">
        <canvas id = "canvas"></canvas>
        <p id="start_page_title">Start <br>Page</p>
    </div>


</main>


<style>

    #container{
        position: absolute;
        width: 100%;
        height: 100%;
        border-radius: 20px;
        background-color: white;
        backface-visibility: hidden;
    }

    #canvas {
        position: absolute;
        width: 100%;
        height: 100%;
        border-radius: 20px;
        background-color: white;
        backface-visibility: hidden;
    }

    #start_page_title {
        display: none;
        font-family: 'Fira Code', monospace, sans-serif;
        color: black;
        font-size: calc(min(30px + 4vw, 40px));
        justify-content: center;
        align-items: center;
        text-align: center;
        font-weight: 400;
        height: 100%;
        width: 100%;
        transform: translateY(-40px);
    }

    @media (max-width: 600px) {
        #canvas {
            display: none;
        }
        #start_page_title {
            display: flex;
        }
    }

</style>