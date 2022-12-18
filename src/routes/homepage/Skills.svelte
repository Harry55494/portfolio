
<script>
    import SkillTile from "./SkillTile.svelte";

    let languages = [{
        title: "Python",
        image: "devicon-python-plain",
        rating: "Advanced",
        colour1: "#3572A5",
        colour2: "#24679b",
        },{
        title: "Java",
        image: "devicon-java-plain",
        rating: "Intermediate",
        colour1: "#c5373c",
        colour2: "#b2282d",
        },{
        title: "HTML",
        image: "devicon-html5-plain",
        rating: "Intermediate",
        colour1: "#ea491d",
        colour2: "#f3a245",
        },{
        title: "CSS",
        image: "devicon-css3-plain",
        rating: "Intermediate",
        colour1: "#2d6ccb",
        colour2: "#2e5a7e",
        },{
        title: "JavaScript",
        image: "devicon-javascript-plain",
        rating: "Intermediate",
        colour1: "#ceb91c",
        colour2: "#c4ad1b",
        },{
        title: "SvelteKit",
        image: "devicon-svelte-plain",
        rating: "Intermediate",
        colour1: "#e56926",
        colour2: "#ea5708",
        },{
        title: "C++",
        image: "devicon-cplusplus-plain",
        rating: "Intermediate",
        colour1: "#25b9f9",
        colour2: "#24d0a2",
        },{
        title: "PHP",
        image: "devicon-php-plain",
        rating: "Beginner",
        colour1: "#4f5d75",
        colour2: "#3c5a6b",
        },{
        title: "Swift",
        image: "devicon-swift-plain",
        rating: "Beginner",
        colour1: "#ec8318",
        colour2: "#e16113",
        }
    ]

    let skills = [{
        title: "TensorFlow",
        image: "devicon-tensorflow-original",
        rating: "Intermediate",
        colour1: "#d5872c",
        colour2: "#de6816",
        },{
        title: "Jira",
        image: "devicon-jira-plain",
        rating: "Intermediate",
        colour1: "#00a1e4",
        colour2: "#00b5e2",
        },{
        title: "Git",
        image: "devicon-git-plain",
        rating: "Intermediate",
        colour1: "#d92828",
        colour2: "#e04646",
        },{
        title: "GitHub",
        image: "devicon-github-plain",
        rating: "Intermediate",
        colour1: "#2e23c9",
        colour2: "#561098",
        }, {
        title: 'GitLab',
        image: 'devicon-gitlab-plain',
        rating: 'Beginner',
        colour1: '#d04d16',
        colour2: '#d46a00',
        }, {
        title: "AWS",
        image: "devicon-amazonwebservices-plain",
        rating: "Beginner",
        colour1: "#253842",
        colour2: "#37464b",
        },{
        title: "Docker",
        image: "devicon-docker-plain",
        rating: "Beginner",
        colour1: "#11a0cc",
        colour2: "#0b95c4",
        },{
        title: "Matlab",
        image: "devicon-matlab-plain",
        rating: "Beginner",
        colour1: "#9f281d",
        colour2: "#f89910",
        }]

</script>

<div class="container" id = "skills_container">
    <h2>Programming Languages / Frameworks</h2>
    <div class="tile_container">
        {#each languages as language}
            <SkillTile title={language.title} image={language.image} rating ={language.rating} colour1={language.colour1} colour2={language.colour2}></SkillTile>
        {/each}
    </div>
    <h2 style="padding-top: 40px">Other Skills</h2>
    <div class="tile_container">
        {#each skills as skill}
            <SkillTile title={skill.title} image={skill.image} rating={skill.rating} colour1={skill.colour1} colour2={skill.colour2}></SkillTile>
        {/each}
    </div>

</div>


<style>

    .container{
        margin: 2vh 4vw 0vw 4vw;
        color: white;
        line-height: 1.1;
    }

    h2 {
        font-size:calc(min(10px + 3vw, 40px));
        font-weight: 500;
        text-align: center;
        letter-spacing: 2px;

    }

    .tile_container{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        margin: 0 auto;
    }

    a{
        text-decoration: underline;
        color: white;
    }

    p {
        margin-left:calc(min(-10px + 10vw, 150px));
        margin-right:calc(min(-10px + 10vw, 150px));
        font-size: calc(min(15px + 1vw, 22px));
        text-align: left;
        line-height: 1.5;
        font-weight: 300;
    }

</style>