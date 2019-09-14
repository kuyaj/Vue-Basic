<template>
    <div id="registrations">
        <div class="summary">
            <h3>Registered</h3>
            <h5>{{ total }}</h5>
        </div>
        <hr>
        <div class="row" v-for="(registration, key) in registrations" :key="key">
            <h4>{{ registration.name }}</h4>
            <span @click="unregister(registration)">(Unregister)</span>
            <div class="date">{{ registration.date }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['registrations'],
        methods: {
            unregister(registration) {
                this.$emit('userUnregistered', registration);
            }
        },
        computed: {
            total() {
                return this.registrations.length;
            }
        }
    }
</script>

<style scoped>
    #registrations {
        box-shadow: 1px 1px 2px 1px #ccc;
        margin: 20px;
        padding: 20px;
        display: inline-block;
        width: 350px;
        vertical-align: top;
        text-align: left;
    }

    .summary {
        text-align: center;
    }

    h3 {
        color: #303952;
    }

    .row h4 {
        display: inline-block;
        width: 30%;
        margin: 0 0 10px 0;
        box-sizing: border-box;
    }

    .row span {
        width: 30%;
        color: #c44569;
        cursor: pointer;
        font-weight: bold;
        font-size: 14px;
    }

    .row span:hover {
        color: #d63031;
    }

    .date {
        display: inline-block;
        width: 38%;
        text-align: right;
        box-sizing: border-box;
    }
</style>