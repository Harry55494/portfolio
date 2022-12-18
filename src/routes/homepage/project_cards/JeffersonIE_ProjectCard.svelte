
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

</script>


<div id ="jie_card" class="container">
    <div class="card" on:click={flip_card}>
        <div class="front">
           <h2>Jefferson-IE</h2>
            <h3>A Neural Network Crypto Trader</h3>
        </div>
        <div class="back">
            <h4>Jefferson Investment Engine</h4>
            <p>Jefferson-IE is a Python program that utilises TensorFlow and Neural Networks to predict crypto-currency prices,
                and buy or sell based on these predictions. Current simulations predict a 17% monthly return when live trading.</p>
            <p>Source Code is private for this project, but some parts can be shown upon request.</p>
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
        border-radius: 20px;
        background-color: rgb(255, 210, 85);
        position: absolute;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
    }

    .back{
        position: absolute;
        background-color: rgb(255, 210, 85);
        border-radius: 20px;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
        transform: rotateY(180deg);
        overflow: hidden;
    }

    .container:hover{
        transform: scale3d(1.1, 1.1, 1.1);
    }

    h2{
        font-family: 'League Spartan', serif;
        font-size: calc(min(20px + 6vw, 65px));
        color: black;
        text-align: center;
        margin-top: 90px;
    }

    h3{
        font-size: calc(min(10px + 2vw, 25px));
        color: black;
        text-align: center;
        margin-top: -30px;
        font-weight: 500;
    }

    h4, p{
        color: black;
        text-align: center;
    }

    h4{
        font-size: 35px;
        font-weight: 600;
        font-family: 'League Spartan', serif;
        margin-bottom: 15px;
        margin-top: 40px;
    }

    p{
        margin: 12px;
        font-size: calc(min(7px + 2vw, 18px));
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
            margin-top: 50px;
        }

        h4{
            display: none;
        }

    }





</style>