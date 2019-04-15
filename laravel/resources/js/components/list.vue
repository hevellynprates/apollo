<template>
    <div class="main">
        <section class="webdesigntuts-workshop">
            <form action="" @submit.prevent="start()" method="GET">
                <button>Iniciar</button>
            </form>
        </section>
        <section class="listagem" v-show="listagem.length">
            <div class="container">
                <div class="row justify-content-center">
                    <div class="col-8 mb-4">
                        <table class="table table-hover table-bordered bg-light rounded overflow-hidden">
                            <thead>
                            <tr>
                                <th scope="col">Estado</th>
                                <th scope="col">Sigla</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="estados in listagem">
                                <td>{{estados.nome}}</td>
                                <td>{{estados.sigla}}</td>
                            </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import swal from 'sweetalert';

    export default {
        name: "list",
        data: function () {
            return {
                listagem: []
            }
        },
        methods: {
            start: function () {
                const self = this;
                $.get("https://cors-anywhere.herokuapp.com/http://desenvolvertecnologia.com/api/public/list", function (data) {
                    if (data) {
                        self.listagem = data
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
    .main {
        background: #151515;
        background: linear-gradient(#1b1b1b, #111);
        min-height: 100vh   ;
    }
    .swal-text {
        background-color: #FEFAE3;
        padding: 17px;
        border: 1px solid #F0E1A1;
        display: block;
        margin: 22px;
        text-align: center;
        color: #61534e;
    }

    .webdesigntuts-workshop {
        text-align: center;
    }

    .webdesigntuts-workshop form {
        animation: glow 800ms ease-out infinite alternate;
        border: 1px solid #000;
        border-radius: 5px;
        box-shadow: inset 0 0 0 1px #272727;
        display: inline-block;
        font-size: 0px;
        margin: 150px auto 40px;
        padding: 20px;
    }

    .webdesigntuts-workshop button {
        background: #222;
        background: linear-gradient(#333, #222);
        box-sizing: border-box;
        border: 1px solid #444;
        border-radius: 5px;
        box-shadow: 0 2px 0 #000;
        color: #fff;
        display: block;
        font-family: 'Cabin', helvetica, arial, sans-serif;
        font-size: 13px;
        font-weight: 400;
        height: 40px;
        line-height: 40px;
        margin: 0;
        padding: 0;
        position: relative;
        text-shadow: 0 -1px 0 #000;
        width: 130px;
    }

    .webdesigntuts-workshop button:hover,
    .webdesigntuts-workshop button:focus {
        background: #292929;
        background: linear-gradient(#393939, #292929);
        color: #5f5;
        outline: none;
    }

    .webdesigntuts-workshop button:active {
        background: #292929;
        background: linear-gradient(#393939, #292929);
        box-shadow: 0 1px 0 #000, inset 1px 0 1px #222;
        top: 1px;
    }

    @keyframes glow {
        0% {
            border-color: #393;
            box-shadow: 0 0 5px rgba(0, 255, 0, .2), inset 0 0 5px rgba(0, 255, 0, .1), 0 2px 0 #000;
        }
        100% {
            border-color: #6f6;
            box-shadow: 0 0 20px rgba(0, 255, 0, .6), inset 0 0 10px rgba(0, 255, 0, .4), 0 2px 0 #000;
        }
    }
</style>