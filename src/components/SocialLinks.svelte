<script>
const data = [
    {
        path: "https://github.com/samsour",
        icon: "github"
    },
    {
        path: "https://twitter.com/qwerfeldein",
        icon: "twitter"
    },
    {
        path: "https://www.xing.com/profile/Sam_Sauer",
        icon: "xing"
    },
    {
        path: "https://www.linkedin.com/in/samsauer/",
        icon: "linkedin"
    },
    {
        path: "hi@samsour.de",
        type: "mailto:",
        target: "_self",
        icon: "mail"
    },
]
</script>

<ul>
{#each data as link}
    <li>
        <a href="{link.type || ''}{link.path}" target="{link.target || '_blank'}">
            <img alt="{link.icon}" src="./svg/social-icons/{link.icon}.svg">
        </a>
    </li>
{/each}
</ul>

<style lang="scss">
ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    position: relative;
    flex-flow: row wrap;
    // overflow-x: scroll;
}

li {
    display: block;
    
    &:not(:last-of-type) {
        margin-right: 40px;
    }
}

a {
    padding: 30px;
    display: block;
    width: 48px;
    height: 48px;
    transition: transform ease-out 0.2s;

    &:hover {
        transform: scale(1.2);
    }
}
</style>