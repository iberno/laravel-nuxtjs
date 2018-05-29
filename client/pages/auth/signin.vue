<template>
    <section class="hero">
        <div class="hero-body">
            <div class="container has-text-centered">
                <div class="column is-4 is-offset-4">
                    <h1 class="title has-text-grey">Sign in</h1>
                    <div class="box">
                        <form action="#" @submit.prevent="submit">
                            <div class="field">
                                <div class="control has-icons-left has-icons-right">
                                    <input class="input is-large" :class="{'is-danger': errors.email }" type="email" placeholder="email@email.com" autofocus="" v-model="form.email">
                                    <span class="icon is-small is-left">
                                        <i class="fas fa-envelope"></i>
                                    </span>
                                    <span class="icon is-small is-right">
                                        <i class="fas fa-check"></i>
                                    </span>
                                    <p class="help is-danger" v-if="errors.email">{{ errors.email[0] }}</p>
                                </div>
                            </div>
                            <div class="field">
                                <div class="control has-icons-left">
                                    <input class="input is-large" :class="{'is-danger': errors.password }" type="password" placeholder="Password" v-model="form.password">
                                    <span class="icon is-small is-left">
                                        <i class="fas fa-lock"></i>
                                    </span>
                                    <p class="help is-danger" v-if="errors.password">{{ errors.password[0] }}</p>
                                </div>
                            </div>
                            <button class="button is-info is-block is-large is-fullwidth">Login</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    middleware: 'guestMiddleware',
    data () {
        return {
            form: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
       async submit () {
            await this.$auth.login({
                data: this.form
            })

            this.$router.push({
                path: this.$route.query.redirect || '/'
            })
        }
    }
}
</script>

