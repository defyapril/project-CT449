<script>
import { ElMessage } from 'element-plus';
import NxbForm from './NxbForm.vue';
import { nxbStore } from '@/stores/nxb';

const nxb = nxbStore();

export default {
    components: {
        NxbForm,
    },

    data: () => {
        return {
            data: {},
        };
    },
    methods: {
        async submit(data) {
            const result = await nxb.add(data);
            ElMessage(result);
        },
    },
};
</script>

<template>
    <div>
        <h4 class="m-4 text-center">Add publisher</h4>
        <NxbForm :nxb="data" @handleSubmit="submit" />
    </div>
</template>

<style lang="scss"></style>
