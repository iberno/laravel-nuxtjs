<template>
<nav class="navbar is-transparent has-shadow">
    <div class="navbar-brand">
        <nuxt-link class="navbar-item" :to="{ name: 'index' }">
            <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
        </nuxt-link>
        <div class="navbar-burger burger" data-target="navbarExampleTransparentExample">
        <span></span>
        <span></span>
        <span></span>
        </div>
    </div>

    <div id="navbarExampleTransparentExample" class="navbar-menu">
        <div class="navbar-start">
            <!-- Links -->
        </div>
        <div class="navbar-end">
            <template v-if="!authenticated">
                <div class="navbar-item">
                    <nuxt-link :to="{ name: 'auth-signin' }" class="navbar-item">
                        Sign In
                    </nuxt-link>
                    <nuxt-link class="button is-primary" :to="{ name: 'auth-signup' }">
                        Sign Up
                    </nuxt-link>
                </div>
            </template>
            <template v-if="authenticated">
                <div class="navbar-item has-dropdown is-hoverable">
                        <a class="navbar-link" href="#"> {{ user.name }}</a>
                    <div class="navbar-dropdown is-boxed">
                        <a class="navbar-item" @click.prevent="logout">
                            LogOut
                        </a>
                    </div>
                </div>
            </template>
        </div>

        
    </div>
</nav>
</template>

<script>
export default {
    methods: {
        logout () {
            this.$auth.logout();
        }
    }
}
</script>


