
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


<div class="container">
    <div class="card" on:click={flip_card}>
        <div class="front">

        </div>
        <div class="back">

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
        background: white;
        position: absolute;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
    }

    .back{
        position: absolute;
        background: blue;
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
    }



</style>