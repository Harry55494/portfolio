

<script>

    export let title;
    export let image;
    export let rating;
    export let colour1;
    export let colour2;

    let tile;


    function tileMouseEnter(event){
        tile = event.currentTarget;
        SetTransition();
        //tile.style.cursor = 'none';

    }


    function tileMouseMove(event){
        tile = event.currentTarget;
        const tileBound = tile.getBoundingClientRect();
        const tileWidth = tile.offsetWidth;
        const tileHeight = tile.offsetHeight;
        const centerX = tileBound.left + (tileWidth / 2);
        const centerY = tileBound.top + (tileHeight / 2);
        const mouseX = event.clientX - centerX;
        const mouseY = event.clientY - centerY;
        const rotateX = ((-1)*25*mouseY/(tileHeight/2)).toFixed(2);
        const rotateY = ((+1)*25*mouseX/(tileWidth/2)).toFixed(2);
        tile.style.transform = 'perspective(1000px) rotateX(' + rotateX + 'deg) rotateY(' + rotateY + 'deg) scale3d(1.1, 1.1, 1.1)';
    }

    function tileMouseLeave(event){
        tile = event.currentTarget;
        tile.style.transform = 'perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)';
        tile.style.cursor = 'default';
    }

    function SetTransition(){
        tile.style.transition = 'transform 300ms cubic-bezier(0.175, 0.885, 0.32, 1.275)';
    }


</script>

<!--https://devicon.dev-->

<div class="tile" style="background: linear-gradient(90deg, {colour1} 0%, {colour2} 100% )"
     on:mouseenter={tileMouseEnter}
     on:mousemove={tileMouseMove}
     on:mouseleave={tileMouseLeave}>
    <div style="height:30px;"></div>
    {#if title === 'Cloudflare'}
        <i class="fa-brands fa-cloudflare"></i>
    {/if}
    {#if title !== 'Cloudflare'}
        <i class={image}></i>
    {/if}
    <h3 class = "title">{title}</h3>
    <h3 class = "subtitle"> {rating}</h3>
</div>



<style>

    :global(.tile){
        border-radius: 35px;
        background: black;
        width: 220px;
        height: 220px;
        margin: 8px;
        transform: perspective(1000px);
        overflow: hidden;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        cursor: default;
    }


    .tile:before{
        content: '';
        position: absolute;
        height: 250px;
        width: 20px;
        background: white;
        box-shadow: 0 0 10px #fff;
        filter: blur(1px);
        opacity: 0.9;
        top: -30px;
        transform: rotate(-20deg) translateX(-150px);
    }

    .tile:hover:before{

        transition: 1.3s;
        transition-delay: 0.3s;
        transform: rotate(-20deg) translate(300px, 70px);
    }

    :global(i){
        font-size: 60px;
        color: white;
        margin-top: 80px;
        margin-left: 15px;
        transform: translateZ(20px);
    }

    :global(img){
        height: 60px;
        width: auto;
        color: white;
        margin-top: 0px;
        margin-left: 15px;
        transform: translateZ(20px);
    }

    :global(.title){
        color: white;
        font-size: 30px;
        margin-top: 15px;
        margin-left: 15px;
        transform: translateZ(20px);
    }

    :global(.subtitle){
        color: white;
        font-size: 22px;
        margin-top: -15px;
        margin-left: 15px;
        font-weight: 600;
        transform: translateZ(20px);

    }


    @media (max-width: 768px) {
        :global(.tile){
            width: 140px;
            height: 140px;
            margin: 6px;
        }

        :global(i){
            font-size: 35px;
            margin-top: 60px;
        }

        :global(.title){
            font-size: 20px;
            margin-top: 10px;
        }

        :global(.subtitle){
            margin-top: -15px;
            font-size: 15px;
        }

    }



</style>