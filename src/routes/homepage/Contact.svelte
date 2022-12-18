
<script>

    const download_url = new URL('/CV.pdf', import.meta.url).href

</script>

<div class = 'container' id ="contact">
    <h1>Contact & More</h1>

    <p>Have more questions? Want to see more? <br>
    </p>

    <div style="display:flex; justify-content: center; align-items: center; padding-bottom: 40px; flex-wrap: wrap;">
        <div class="contact_a_border">
            <a class="contact_a" href="https://github.com/harry55494">
                <i class="fa-brands fa-github font_awesome_icon"></i>
                <p class="contact_p">GitHub</p>
            </a>
        </div>
        <div class="contact_a_border">
            <a class="contact_a" href="https://www.linkedin.com/in/harrison-phillingham-2614b81ba/">
                <i class="fa-brands fa-linkedin font_awesome_icon"></i>
                <p class="contact_p">LinkedIn</p>
            </a>
        </div>
        <div class="contact_a_border">
            <a class="contact_a" href="mailto:harrison@phillingham.com">
                <i class="fa-solid fa-envelope font_awesome_icon"></i>
                <p class="contact_p">Email</p>
            </a>
        </div>

    </div>

    <div style="display:flex;justify-content: center;">
        <a href="{download_url}" download="{download_url}">
            <div id = "download_border">
                <div class="cv_download">
                    ⬇️  Download CV
                </div>
            </div>
        </a>
    </div>
</div>


<style>
    .container{
        margin: 2vh 4vw 4vw 4vw;
        color: white;
        line-height: 1.1;
    }

    h1 {
        font-size: calc(min(25px + 8vw, 80px));
        font-weight: 600;
        text-align: center;
        letter-spacing: 2px;
    }

    a {
        text-decoration: none;
        color: white;
    }

    p {
        margin-left:calc(min(0px + 10vw, 200px));
        margin-right:calc(min(0px + 10vw, 200px));
        font-size: calc(min(15px + 1vw, 22px));
        text-align: center;
        line-height: 1.5;
        font-weight: 300;
    }

    .contact_a_border {
        height: 130px;
        width: 130px;
        background:linear-gradient(210deg, #00dbde, #fc00ff) right;
        border-radius: 10px;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 20px;
        transition: transform 500ms cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }



    .contact_a {
        display: flex;
        flex-direction: column;
        align-items: center;
        background: #0e0e0e;
        border-radius: 10px;
        height: 125px;
        width: 125px;
    }

    .font_awesome_icon{
        padding-top: 5px;
        margin: 10px;
    }

    .contact_p {
        font-size: 20px;
        font-weight: 400;
        text-align: center;
        width: 100%;
        padding-bottom: 5px;
        transform: translateY(-50%);
    }

    #download_border{
        height: 75px;
        width: 225px;
        background:linear-gradient(330deg, #00dbde, #fc00ff) right;
        border-radius: 10px;
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: transform 500ms cubic-bezier(0.175, 0.885, 0.32, 1.275);
        margin-bottom: 30px;

    }

    #download_border:hover, #download_border:focus, .contact_a_border:hover, .contact_a_border:focus{
        transform: scale3d(1.1, 1.1, 1.1);

    }

    #download_border:active, .contact_a_border:active{
        transform: scale(0.9);
        transition: 0.4s;
    }

    .cv_download{
        text-align: center;
        display: flex;
        justify-content: center;
        align-items:center;
        font-size: 22px;
        font-weight: 600;
        height: 70px;
        width: 220px;
        background: #0e0e0e;
        border-radius: 10px;
    }

    @media (max-width: 768px) {
        .contact_a_border {
            height: 110px;
            width: 110px;
        }

        .contact_a {
            height: 105px;
            width: 105px;
        }
    }




</style>