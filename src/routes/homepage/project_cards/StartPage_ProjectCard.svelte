
<script>

    import StartPageParticles from "./StartPageParticles.svelte";
    import {onMount} from "svelte";

    export var width = 500
    export var height = 300

    // get width of page

    onMount(() => {
        const card = document.getElementById('start_page_card')
        width = card.offsetWidth
        height = card.offsetHeight
    });

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


<div id="start_page_card" class="container">
    <div class="card" on:click={flip_card}>
        <div class="front">
            <StartPageParticles width ={width} height = {height} />
        </div>
        <div class="back">
            <h5>Start Page</h5>
            <p>Start Page is a small and simple Svelte-based web page which I used to get a handle on Svelte. It includes Svelte stores for setting storage,
                an animated particle background, and a device-based dark mode.</p>
            <p>View it live here: <a href="https://start.phillingham.com" target="_blank">start.phillingham.com</a></p>
            <p>Source Code: <a href="https://github.com/Harry55494/Start-page" target="_blank">github.com/Harry55494/start-page</a></p>
        </div>
    </div>
</div>




<style>

    @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@600&display=swap');

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
    }

    .front{
        position: absolute;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
    }

    .back{
        position: absolute;
        background: white;
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

    h5{
        font-size: 35px;
        margin-top: 35px;
        margin-bottom: 30px;
        font-weight: 600;
        font-family: 'Fira Code', monospace, sans-serif;
    }

    p{
        font-size: calc(min(6px + 2vw, 18px));
        font-weight: 300;
        margin: 14px;
    }

    a {
        color: black;
    }

    h5, p{
        color: black;
        text-align: center;
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

        p{
            margin: 12px;
        }

    }

    @media (max-width: 768px){
        .container{
            width: 400px;
            height: 200px;
            margin-left: 0;
            margin-right: 0;
        }

        h5{
            display: none;
        }

    }



</style>