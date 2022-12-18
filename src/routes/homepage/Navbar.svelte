<script>

    import {onMount} from "svelte";

    function adjustNavbarTransition(){
        /**
         * Changes the navbar animation when the window is resized, to prevent it automatically sliding to the right when the page is small enough
         */
        const page_width = window.innerWidth;
        console.log(page_width);
        if (page_width < 869){
            setTimeout(function(){
                document.querySelector(".nav_links").style.transition = "transform 0.5s ease-in-out";
            }, 600);
        } else if (page_width >= 869){
            document.querySelector(".nav_links").style.transition = "transform 0s ease-in-out";
        }
    }

    window.addEventListener("resize", adjustNavbarTransition);

    function nav_slide() {

        document.querySelector(".nav_links").style.transition = "transform 0.5s ease-in-out";

        document.querySelector('.nav_links').classList.toggle('nav_active');

        document.querySelector('.burger').classList.toggle('toggle');

        const nav_links = document.querySelectorAll('.nav_links li');

        nav_links.forEach((link, index) => {
            link.style.animation = 'navLinkFade 0.5s ease forwards '+ (index / 7) + 's';
        });

        // This adjusts the ability to scroll when the navbar is open
        if (document.body.style.overflowY === 'hidden') {
            setTimeout(() => {
                document.body.style.overflowY = 'visible';
            }, 300);

        } else {
            document.body.style.overflowY = 'hidden';
        }


    }

    function hide_nav_bar() {
        document.querySelector('.nav_links').classList.remove('nav_active');

        document.querySelector('.burger').classList.remove('toggle');

        document.body.style.overflowY = 'visible';

    }

    onMount(() => {
        function scrollToElement(elementName) {
            console.log(elementName);
            const element = document.getElementById(elementName);
            element.scrollIntoView({behavior: "smooth"});
            console.log('clicked')
        }

        const links = document.getElementsByClassName("nav_links");
        const children = links[0].children;
        console.log(children);
        for (let i = 0; i < children.length; i++) {
            let elementToScrollTo = children[i].innerHTML.toLowerCase();
            if (elementToScrollTo === 'home'){
                elementToScrollTo = 'nav'
            }
            console.log(elementToScrollTo)
            children[i].addEventListener("click", hide_nav_bar);
            children[i].addEventListener("click", function() {scrollToElement(elementToScrollTo)});
        }

        console.log('done')

    });




</script>

<nav class = "border-gradient border-gradient-purple" id="nav">
    <div class = "title">
        <h4>Harrison Phillingham</h4>
    </div>
    <ul class ="nav_links">
        <li>Home</li>
        <li>About</li>
        <li>Projects</li>
        <li>Contact</li>
    </ul>
    <div class = 'burger' on:click="{nav_slide}" on:cluck>
        <div class = 'line1'></div>
        <div class = 'line2'></div>
        <div class = 'line3'></div>
    </div>
</nav>

<style>

    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .border-gradient {
        border-bottom: 4px solid;
        border-image-slice: 1;
    }

    .border-gradient-purple {
        border-image-source: linear-gradient(to left, #743ad5, #d53a9d);
    }

    nav{
        position: absolute;
        margin: 2px auto;
        top: 0;
        width: 100%;
        max-width: 1920px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        min-height: 6vh;
        font-family: 'Poppins', sans-serif;
        background: #0e0e0e;
    }

    .title{
        color: white;
        text-transform: uppercase;
        letter-spacing: 4px;
        font-size: calc(min(8px + 2vw, 22px));
    }

    .nav_links{
        display: flex;
        justify-content: space-around;
        width: 30%;
        background: #0e0e0e;
    }

    :global(.nav_links li){
        list-style: none;
        color: white;
        text-decoration: none;
        letter-spacing: 3px;
        font-weight: 400;
        cursor: pointer;
    }

    .burger div{
        width: 25px;
        height: 2px;
        color: white;
        margin: 5px;
        background-color: white;
        transition: all 0.3s ease-in-out;
    }

    .burger{
        display: none;
        cursor: pointer;
    }


    @media screen and (max-width: 1200px){
        .nav_links{
            width: 40%;
        }
    }


    @media screen and (max-width: 868px){

        :global(body){
            overflow-x: hidden;
        }

        :global(.nav_links){
            position: absolute;
            right: 0;
            height: 95vh;
            top: 7vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            transform: translateX(100%);
            transition: transform 0s ease-in-out;
            background: #0e0e0e;
            overflow: hidden;
        }

        :global(.nav_links li){
            transform: translateY(-60px);
        }

        .nav_links{
            width: 102%;
            font-size: 22px;
        }

        .burger{
            display: block;
            margin-right: 10px;
        }

    }

    :global(.nav_active){
        transform: translateX(0);
    }


    @keyframes navLinkFade {
        from{opacity: 0;
            transform: translateX(50px);
        }
        to{opacity: 1;
            transform: translateX(0px);
        }

    }

    :global(.toggle .line1) {
        transform: rotate(-45deg) translateX(-5px) translateY(5px);
    }

    :global(.toggle .line2) {
        opacity: 0;
    }

    :global(.toggle .line3) {
        transform: rotate(45deg) translateX(-5px) translateY(-5px);
    }




</style>
