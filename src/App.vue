<template>
    <div id="app">
        <div id="nav"
             class="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white border-bottom box-shadow">
            <h5 class="my-0 mr-md-auto font-weight-normal">Shmotenki ot Artemki!</h5>
            <nav class="my-2 my-md-0 mr-md-3">
                <router-link class="p-2 text-dark" :to="{ name: 'product-list' }">
                    Product List
                </router-link>
                <router-link class="p-2 text-dark" :to="{ name: 'product-create' }">
                    Create Product
                </router-link>
                <router-link class="p-2 text-dark" :to="{ name: 'charts-page' }">
                    Charts Examples
                </router-link>
                <router-link class="p-2 text-dark" :to="{ name: 'money-charts-page' }">
                    Money Chart
                </router-link>
            </nav>
            <div class="btn btn-outline-primary">
                <span>Cart({{ inCart.length }})</span>
            </div>
        </div>
        <router-view/>
    </div>
</template>

<script>
    import {EventBus} from './main'

    export default {
        name: "App",
        data() {
            return {
                inCart: []
            }
        },
        mounted() {
            EventBus.$on('add-to-cart', inCart => {
                this.inCart.push(inCart)
            })
        }
    }
</script>

<style>
    body {
        font-family: tahoma;
        color: #282828;
        margin: 0px;
    }

    .nav-bar {
        background: linear-gradient(-90deg, #84CF6A, #16C0B0);
        height: 60px;
        margin-bottom: 15px;
    }

    .cart {
        margin-right: 25px;
        float: right;
        border: 1px solid #d8d8d8;
        padding: 5px 20px;
    }

    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
</style>
