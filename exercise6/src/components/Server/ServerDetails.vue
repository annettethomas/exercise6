<template>
    <div class="col-xs-12 col-sm-6">

        <p v-if="!server">Server Details are currently not updated</p>
        <p v-else>Server #{{ server.id }} selected, Status: {{ server.status }}</p>
        <hr>
        <button @click="resetStatus">Change to normal</button>
    </div>

</template>

<script>

    import { serverBus } from "../../main.js";

    export default {
        data () {
            return {
                server: null
            }
        },

        methods: {
            resetStatus() {
                this.server.status = "normal"
            }
        },
        created (){
            serverBus.$on('serverSelected', (server) => {
                this.server = server;
            })
        }
    }
</script>