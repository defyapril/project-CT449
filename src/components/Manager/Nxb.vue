<script>
import { ElButton, ElInput, ElMessage } from 'element-plus';
import { nxbStore } from '@/stores/nxb';

export default {
    components: {
        ElInput,
    },
    data() {
        return {
            nxbs: nxbStore().NXB,
            search: '',
        };
    },
    computed: {
        filteredNxb() {
            if (this?.nxbs) {
                return this.nxbs.filter((book) => book.TenNxb.toLowerCase().includes(this.search.toLowerCase()));
            }
            return [];
        },
    },
    methods: {
        navigatorToAdd() {
            this.$router.push({
                name: 'add-nxb',
            });
        },
        navigatorToEdit(manxb) {
            this.$router.push({
                name: 'edit-nxb',
                params: {
                    manxb,
                },
            });
        },
        async handleDelete(manxb) {
            const result = await nxbStore().delete(manxb);
            ElMessage(result);
            this.nxbs = nxbStore().NXB;
        },
    },
};
</script>

<template>
    <div class="Book">
        <h4 class="text-center m-2">Publisher management</h4>
        <div class="container create-btn-container d-flex justify-content-end">
            <el-button type="primary" plain @click="navigatorToAdd">Add new publisher</el-button>
        </div>
        <div class="container table-container">
            <el-table :data="filteredNxb" style="width: 100%">
                <el-table-column type="index" label=""> </el-table-column>
                <el-table-column label="Name" prop="TenNxb"> </el-table-column>
                <el-table-column label="Address" prop="Diachi"> </el-table-column>
                <el-table-column align="right">
                    <template #header>
                        <el-input v-model="search" size="small" placeholder="Enter name publisher to search" />
                    </template>
                    <template #default="scope">
                        <el-button size="small" type="success" @click="navigatorToEdit(scope.row.manxb)"
                            >Update</el-button
                        >
                        <el-button size="small" type="danger" @click="handleDelete(scope.row.manxb)">Delete</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </div>
    </div>
</template>

<style lang="scss">
.book {
    .table-container {
    }
}
</style>
