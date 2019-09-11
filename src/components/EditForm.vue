<template>
    <div class="feild">
        <form @submit.prevent="setTime">
            <input class="input is-success" v-model="time" v-if="edit" type="text" name="time" placeholder="how many minutes?">
            <input type="submit" style="visibility: hidden;" />
        </form>
    </div>

</template>

<script>
export default {
    name: "EditForm",
    data() {
        return {
            time: ''
        }
    },
    methods: {
        setTime() {

            this.edit = !this.edit;
            this.$emit('set-time', Number(this.time));
            this.time = '';
        }
    },
    props: {
        edit: Boolean
    }
}
</script>

<style scoped>
.feild {
    padding-top: 10%;
    bottom: 0;
    align-items: center;
    display: flex;
    justify-content: center;
    left: 0;
    right: 0;
    top:0;
}
</style>