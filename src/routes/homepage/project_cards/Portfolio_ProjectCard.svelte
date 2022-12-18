
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

    function onScroll(){
        const doc = document.documentElement;
        const scrollPos = (window.pageYOffset || doc.scrollTop) - (doc.clientTop || 0);
        document.querySelector('.front_portfolio_card').style.background = 'linear-gradient(' + (scrollPos/3) + 'deg, rgba(0, 219, 222, 0.95), rgba(252, 0, 255, 0.9)) right';
        document.querySelector('.back_portfolio_card').style.background = 'linear-gradient(' + (-(scrollPos/3)) + 'deg, rgba(0, 219, 222, 0.95), rgba(252, 0, 255, 0.9)) right';

    }

    import { browser } from '$app/environment';

    if (browser) {
        window.addEventListener('scroll', onScroll);
    }

</script>


<div id ="portfolio_card" class="container">
    <div class="card" on:click={flip_card}>
        <div class="front_portfolio_card">
            <h2>Portfolio Website</h2>
        </div>
        <div class="back_portfolio_card">
            <h3>Portfolio Website</h3>
            <p>This website is built using Svelte, and the source code is available to view on my GitHub profile. It uses no libraries, and all the code was written by me.</p>
            <p>Source Code: <a href="https://github.com/Harry55494/portfolio" target="_blank">github.com/Harry55494/<br>portfolio</a></p>
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

    .front_portfolio_card{
        border-radius: 20px;
        position: absolute;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
    }

    .back_portfolio_card{
        position: absolute;
        background: linear-gradient(60deg, rgba(252, 0, 255, 0.9), rgba(0, 219, 222, 0.95)) left;
        border-radius: 20px;
        backface-visibility: hidden;
        width: 100%;
        height: 100%;
        transform: rotateY(180deg);
        overflow: hidden;
    }

    h2{
        font-family: 'Poppins', sans-serif;
        padding: 20px;
        font-size: calc(min(28px + 5vw, 65px));
        text-align: center;
        margin-top: 65px;
    }

    p  {
        text-align: center;
        margin: 15px;
        font-size: calc(min(8px + 2vw, 18px));
    }

    a{
        color: #ffffff;
    }

    p:not(:last-child){
        padding-top: 15px;
    }

    h3{
        text-align: center;
        font-size: 40px;
        font-weight: 600;
        font-family: 'Poppins', sans-serif;
        margin-bottom: 25px;
        margin-top: 40px;
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

        h2{
            margin-top: 20px;
        }

        h3{
            display: none;
        }


    }



</style>