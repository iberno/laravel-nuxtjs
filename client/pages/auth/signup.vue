<template>
    <section class="hero">
        <div class="hero-body">
            <div class="container has-text-centered">
                <div class="column is-4 is-offset-4">
                    <h1 class="title has-text-grey">Register</h1>
                    <div class="box">
                        <form method="" @submit.prevent="register">
                            <div class="field">
                                <div class="control has-icons-left">
                                    <input class="input is-large" :class="{'is-danger': errors.email }" type="email" placeholder="email@email.com" autofocus="" v-model="form.email">
                                    <span class="icon is-small is-left">
                                        <i class="fas fa-envelope"></i>
                                    </span>
                                    <p class="help is-danger" v-if="errors.email">
                                        {{ errors.email[0] }}
                                    </p>
                                </div>
                            </div>
                            <div class="field">
                                <div class="control has-icons-left">
                                    <input class="input is-large" :class="{'is-danger': errors.name }" type="text" placeholder="Name" autofocus="" v-model="form.name">
                                    <span class="icon is-small is-left">
                                        <i class="fas fa-user"></i>
                                    </span>

                                    <p class="help is-danger" v-if="errors.name">
                                        {{ errors.name[0] }}
                                    </p>
                                </div>
                            </div>
                            <div class="field">
                                <div class="control has-icons-left">
                                    <input class="input is-large" :class="{'is-danger': errors.password }" type="password" placeholder="Password" v-model="form.password">
                                    <span class="icon is-small is-left">
                                        <i class="fas fa-lock"></i>
                                    </span>

                                    <p class="help is-danger" v-if="errors.password">
                                        {{ errors.password[0] }}
                                    </p>
                                </div>

                            </div>
                            <button class="button is-info is-block is-large is-fullwidth">Register</button>
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
                name: '',
                password: ''
            }
        }
    },
    methods: {
       async register () {
            await this.$axios.post('register', this.form)

            await this.$auth.login({
                data: {
                    email: this.form.email,
                    password: this.form.password
                }
            })

            this.$router.push({
                name: 'index'
            })
        }
    }
}
</script>