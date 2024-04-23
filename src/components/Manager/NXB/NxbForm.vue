<script>
export default {
    components: {},
    props: {
        nxb: {
            type: Object,
            required: false,
        },
    },
    data: () => {},
    methods: {
        submit() {
            this.$emit('handleSubmit', this.nxb);
        },
    },
};
</script>

<template>
    <div class="nxb">
        <div class="d-flex flex-column">
            <label>name:</label>
            <el-input v-model="nxb.TenNxb" style="width: 300px" size="large" placeholder="Enter name of publisher" />
        </div>
        <div class="d-flex flex-column my-4">
            <label>Address:</label>
            <el-input v-model="nxb.Diachi" style="width: 300px" size="large" placeholder="Enter address of publisher" />
        </div>
        <div class="d-flex justify-content-center align-items-center">
            <el-button type="success" plain @click="submit">Save</el-button>
        </div>
    </div>
</template>

<style lang="scss">
.nxb {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
</style>
