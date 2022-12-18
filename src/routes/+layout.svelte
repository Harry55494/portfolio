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

    import { browser } from '$app/environment';

    if (browser) {
        // client-only code here
        window.addEventListener("resize", adjustNavbarTransition);
    }


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

    const current_year = new Date().getFullYear();


</script>

<nav class = "border-gradient-bottom" id="nav">

    <!-- TODO - Migrate to better links -->

    <div class = "title">
        <a href="/"><h4>Harrison Phillingham</h4></a>
    </div>
    <ul class ="nav_links">
        <li>Home</li>
        <li>About</li>
        <li>Projects</li>
        <li>Contact</li>
    </ul>
    <div class = 'burger' on:click="{nav_slide}" on:keypress="{nav_slide}" on:cluck>
        <div class = 'line1'></div>
        <div class = 'line2'></div>
        <div class = 'line3'></div>
    </div>
</nav>


<slot></slot>


<footer class="footer border-gradient-top">
    <div class="container">
        <div class="row">
            <div class="footer-col">
                <h4>Socials</h4>
                <ul>
                    <li><a href="https://github.com/harry55494" target="_blank">GitHub</a></li>
                    <li><a href="https://www.linkedin.com/in/harrison-phillingham-2614b81ba/" target="_blank">LinkedIn</a></li>
                    <li><a href="mailto:harrison@phillingham.com">Email</a></li>
                </ul>
            </div>

            <div class="footer-col">
                <h4>Site Map</h4>
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="#about_container">About</a></li>
                    <li><a href="#projects_container">Projects</a></li>
                    <li><a href="#contact_container">Contact</a></li>
                </ul>
            </div>
            <div class="footer-col">
                <h4>Website</h4>
                <ul>
                    <li><a href="https://github.com/Harry55494/portfolio">Source Code</a></li>
                </ul>
            </div>
        </div>
        <p>Copyright &copy {current_year} Harrison Phillingham. All Rights Reserved</p>
    </div>



</footer>

<style>

    :global(body){
        /* This is global styling for the entire body */
        font-family: "Poppins", sans-serif;
        background: #0e0e0e;
        user-select: none;
        min-height: 110%;
        color: white;
    }

    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    a {
        text-decoration: none;
        color: white;
    }


    .border-gradient-bottom {
        border-bottom: 4px solid;
        border-image-slice: 1;
        border-image-source: linear-gradient(to left, #743ad5, #d53a9d);

    }

    :global(nav){
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

    :global(.nav_links li, .nav_links a){
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







    .footer{
        margin: 50px 0;
        padding: 40px 0 0 0;
    }

    .container{
        max-width: 1200px;
        margin: auto;
    }


    .border-gradient-top {
        border-top: 4px solid;
        border-image-slice: 1;
        border-image-source: linear-gradient(to left, #cb3ad5, #2573d9);

    }

    .row{
        display: flex;
        flex-wrap: wrap;
    }

    .footer-col{
        width: 25%;
        padding: 0 15px 10px;
    }

    .footer-col h4{
        font-size: 18px;
        color: white;
        text-transform: capitalize;
        margin-bottom: 30px;
        font-weight: 500;
        position: relative;
    }

    .footer-col h4::before{
        content: '';
        position: absolute;
        box-sizing: border-box;
        height: 2px;
        background: #fff;
        bottom: -10px;
        left: 0;
        width: 50px;
    }

    ul{
        list-style: none;
    }

    li :not(:last-child){
        margin-bottom: 10px;
    }

    .footer-col ul li a{
        font-size: 15px;
        text-transform: capitalize;
        text-decoration: none;
        font-weight: 300;
        color: #a6a5a5;
        display: block;
        transition: all 0.3s;
    }

    .footer-col ul li a:hover{
        color: #fff;
    }

    p{
        margin-top: 25px;
        color: #7e7d7d;
        font-weight: 300;
    }

    @media(max-width: 768px){
        .footer-col{
            width: 50%;
            margin-bottom: 30px;
        }
    }


</style>
