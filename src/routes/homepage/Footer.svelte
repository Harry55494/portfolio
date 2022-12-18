
<script>
    const current_year = new Date().getFullYear();
</script>

<footer class="footer border-gradient border-gradient-purple">
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
                    <li><a href="#">Home</a></li>
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
        <p style = "margin-bottom: 25px; margin-left: 10px; margin-right: 10px;">Copyright &copy {current_year} Harrison Phillingham. All Rights Reserved</p>
    </div>

</footer>


<style>

    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: Poppins, sans-serif;
    }

    .border-gradient {
        border-top: 4px solid;
        border-image-slice: 1;
    }

    .border-gradient-purple {
        border-image-source: linear-gradient(to left, #cb3ad5, #2573d9);
    }

    .footer{
        padding: 70px 0;
    }

    .container{
        max-width: 1200px;
        margin: auto;
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
        position: absolute;
        bottom: 0;
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