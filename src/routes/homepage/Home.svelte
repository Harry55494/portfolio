
<script>

    function onScroll(){
        const doc = document.documentElement;
        const scrollPos = (window.scrollY || doc.scrollTop) - (doc.clientTop || 0);
        document.querySelector('.gradient_background').style.background = 'linear-gradient(' + ((scrollPos/2)+120) + 'deg, #00dbde, #fc00ff) left';
        document.querySelector('.gradient_background').style.webkitBackgroundClip = 'text';
        document.querySelector('.gradient_background').style.webkitTextFillColor = 'transparent';

    }

    import { browser } from '$app/environment';

    if (browser) {
        window.addEventListener('scroll', onScroll);
    }

    const portrait_url = new URL('/static/Portrait.png', import.meta.url).href;

</script>

<div class="container" id = "home">
    <div class="flex_element">
        <h2><span class="waving_emoji">👋</span> Hey! I'm</h2>
        <div class = "gradient_background">
            <h1 class = "line1">Harrison</h1>
            <h1 class = "line2">Phillingham</h1>
        </div>
        <h3>A Student and Full Stack Developer from 🇬🇧</h3>
    </div>
    <div class="flex_element">
        <img src="{portrait_url}" alt = "Harrison">
    </div>

</div>


<style>

    .container{
        margin: 14vh 4vw 8vw 4vw;
        color: white;
        line-height: 1.1;
        max-width: 1800px;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
        column-gap: 70px;
        row-gap: 40px;
        overflow-x: hidden;
    }

    h2{
        font-size:calc(min(14px + 3vw, 50px));
        width: 100%;
        font-weight: 400;
        margin: 0 auto;
        padding: 0;
    }


    .gradient_background{
        background: linear-gradient(120deg, #00dbde, #fc00ff) right;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        transition: background-position 0.5s ease;
        width: 650px;
    }

    .gradient_background:hover{
        background-position: left;
    }


    h1{
        font-size:calc(min(26px + 5vw, 100px));
        line-height: 1.5;
        font-weight: bold;
        margin: 0 0 -40px 0;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        text-transform: capitalize;
        transition: background 1s ease-in-out;
    }

    .line2 {
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        text-transform: capitalize;
        margin: 0;
    }

    h3{
        line-height: 2;
        font-size:calc(min(10px + 3vw, 30px));
        font-weight: 300;
        margin: 0 auto;
        padding: 0;
        width: 100%;
    }

    img{
        width: calc(min(50px + 50vw, 350px));
        height: auto;
        border-bottom: white solid 4px;
        border-bottom-left-radius: 3px;
        border-bottom-right-radius: 3px;
        padding: 0 0.7em 0 0.5em;
        transform: translateZ(0);
    }

    .waving_emoji{
        animation: waving 5s infinite;
        animation-delay: 1s;
        transform-origin: 70% 70%;
        display: inline-block;
    }

    @keyframes waving {
        0% {
            transform: rotate(0deg);
        }
        5% {
            transform: rotate(14deg);
        }
        10% {
            transform: rotate(-8deg);
        }
        15%{
            transform: rotate(14deg);
        }
        20%{
            transform: rotate(-4deg);
        }
        25%{
            transform: rotate(10deg);
        }
        30%{
            transform: rotate(0deg);
        }
        100%{
            transform: rotate(0deg);
        }

    }

    @media(max-width: 768px){
        h1, h2, h3{
            text-align: center;
        }

        h1 {
            margin: 0 0 -20px 0;
        }

        h2{
            width: 50%;
        }

        h3{
            line-height: 1.2;
            margin-top: 10px;
            width: 50%;
        }

        .container{
            margin: 13vh 4vw 8vw 4vw;
        }

    }

</style>