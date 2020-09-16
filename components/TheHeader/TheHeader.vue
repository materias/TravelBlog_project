<template>
    <header class="main-header">
        <nav class="main-nav">
            <ul class="nav-links">
                <nuxt-link to="/" tag="li" class="nav-link"><a>Explore</a></nuxt-link>
                <nuxt-link to="/about" tag="li" class="nav-link"><a>About</a></nuxt-link>
                <nuxt-link to="/next" tag="li" class="nav-link"><a>Where Should I Go Next?</a></nuxt-link>
                <nuxt-link to="/contact" tag="li" class="nav-link"><a>Contact Us</a></nuxt-link>
            </ul>
        </nav>
    </header>
</template>

<style scoped>
.main-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: #f7b654;
    height: 4.5rem;
}

.main-nav {
    height: 100%;
    margin-left: 20px;
}


.nav-links {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    height: 100%;
}

.nav-link {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 1rem;
    padding: 0.3rem;
}

.nav-link a {
    display: block;
    text-decoration: none;
    color: white;
}

.nav-link.nuxt-link-exact-active {
    border-bottom: 3px solid #42403a;
}

.nav-link a:hover,
.nav-link a:active,
.nav-link.nuxt-link-exact-active a {
    color: #4e4d45;
}

</style>