
<script>

    export let parentCardClicked = () => {};

    function flip_card(event){
        parentCardClicked();
        const card = event.currentTarget;
        if (card.style.transform === "rotateY(180deg)"){
            card.style.transform = "rotateY(0deg)";
        }
        else{
            card.style.transform = "rotateY(180deg)";
        }
    }

    const front_url = new URL('/static/Catan-Background.png', import.meta.url).href;
    const back_url = new URL('/static/Catan-Background-2.png', import.meta.url).href;

</script>


<div id = "catan_card" class="container">
    <div class="card" on:click={flip_card}>
        <div class="front" style="background-image: url('{front_url}') ;">
            <h2>Conquerors of Catan</h2>
        </div>
        <div class="back" style="background-image: url('{back_url}') ;">
            <h4>Conquerors of Catan</h4>
            <p>Conquerors of Catan is my final year project for my Bachelors degree.
                It aims to implement Monte Carlo Tree Search in the board game Settlers of Catan to create a strong AI player. </p>
            <p>Source Code is currently private, but will be released upon my project finishing</p>
        </div>
    </div>
</div>




<style>

    .container{
        width: 500px;
        height: 300px;
        transition: transform 500ms cubic-bezier(0.175, 0.885, 0.32, 1.275);
        margin-top: 15px;
        margin-left: 20px;
        margin-right: 20px;
        padding: 15px;
    }

    :global(.card){
        width: 100%;
        height: 100%;
        border-radius: 20px;
        transform-style: preserve-3d;
        transition: all 0.5s ease;
        cursor: pointer;
    }


    .front{
        background-size: 100% 100%;
        background-position: center;
        background-repeat: no-repeat;
        overflow: hidden;
        border-radius: 20px;
        position: absolute;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
    }

    .back{
        background-size: 100% 100%;
        overflow: hidden;
        position: absolute;
        border-radius: 20px;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
        transform: rotateY(180deg);
        color: white;
    }

    .container:hover{
        transform: scale3d(1.1, 1.1, 1.1);
    }

    h2{
        position: absolute;
        top: 0;
        left: 0;
        font-family: 'Alkalami', serif;
        font-size: calc(min(20px + 6vw, 60px));
        color: white;
        text-align: center;
        margin-top: 100px;
        backdrop-filter: blur(5px);
    }

    h4, p{
        color: white;
        text-align: center;
    }

    h4{
        font-size: 45px;
        font-weight: 600;
        font-family: 'Alkalami', serif;
        margin-bottom: 25px;
        margin-top: 40px;
    }

    p{
        margin: 12px;
        font-size: calc(min(10px + 2vw, 20px));
        font-family: 'Alkalami', serif;
    }

    @media (max-width: 600px){
        .container{
            width: 250px;
            height: 160px;
            margin-left: 0;
            margin-right: 0;
        }

    }


    @media (max-width: 700px){
        .container{
            width: 300px;
            height: 180px;
            margin-left: 0;
            margin-right: 0;
        }

    }

    @media (max-width: 768px){
        .container{
            width: 400px;
            height: 200px;
            margin-left: 0;
            margin-right: 0;
        }

        h2{
            margin-top: 60px;
        }

        h4{
            display: none;
        }

    }



</style>