<template>
    <div id="login" class="login vh-100 d-flex align-items-center">
        <div class="container">
            <div class="row d-flex justify-content-center">
                <div class="col-md-6">
                    <div class="col-12">
                        <div class="col-lg-8 d-flex material-box login-form bg-white shadow rounded">
                            <form class="ml-2 mr-2 mt-4 mb-5 w-100" method="POST" @submit.prevent="enviar()">
                                <h1 class="h3 mb-2 text-primary">Login</h1>
                                <hr class="hr"/>
                                <div class="input-group mb-3">
                                    <div class="input-group-prepend">
                                        <span class="input-group-text text-primary">
                                            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="1em" height="1em" fill-rule="evenodd" version="1.1" viewBox="0 0 448 512">
                                                <path fill="currentColor" d="M224 256c70.7 0 128-57.3 128-128S294.7 0 224 0 96 57.3 96 128s57.3 128 128 128zm89.6 32h-16.7c-22.2 10.2-46.9 16-72.9 16s-50.6-5.8-72.9-16h-16.7C60.2 288 0 348.2 0 422.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-41.6c0-74.2-60.2-134.4-134.4-134.4z"></path>
                                            </svg>
                                        </span>
                                    </div>
                                    <input type="text" class="form-control" name="username" v-model="username" placeholder="Username" required autocomplete="off">
                                </div>
                                <div class="input-group mb-3">
                                    <div class="input-group-prepend">
                                        <span class="input-group-text text-primary">
                                            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="1em" height="1em" fill-rule="evenodd" version="1.1" viewBox="0 0 448 512">
                                                <path fill="currentColor" d="M400 224h-24v-72C376 68.2 307.8 0 224 0S72 68.2 72 152v72H48c-26.5 0-48 21.5-48 48v192c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48V272c0-26.5-21.5-48-48-48zm-104 0H152v-72c0-39.7 32.3-72 72-72s72 32.3 72 72v72z" class=""></path>
                                            </svg>
                                        </span>
                                    </div>
                                    <input type="password" class="form-control" name="password" v-model="password" placeholder="Password" required>
                                </div>
                                <button type="submit" class="btn btn-primary btn-block mt-1 text-uppercase font-weight-light" name="login">Entrar</button>
                            </form>
                        </div>
                        <div class="col-lg-2"></div>
                    </div>
                </div>
                <div class="col-md-6"></div>
            </div>
        </div>
    </div>
</template>

<script>
    import swal from 'sweetalert';
    export default {
        name: "login",
        data: function () {
            return {
                username: null,
                password: null
            }
        },
        methods: {
            enviar: function () {
                $.post("https://cors-anywhere.herokuapp.com/http://desenvolvertecnologia.com/api/public/login", {user: this.username, password: this.password}, function(data) {
                    if (data){
                        swal({
                            title: "Sucesso",
                            icon: "success",
                            text: data._token
                        });
                    } else {
                        swal({
                            title: "Algo errado não estar certo",
                            icon: "error"
                        });
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .login {
        background: linear-gradient(110deg, #fbc2eb 60%, #067eff 60%);
    }
</style>