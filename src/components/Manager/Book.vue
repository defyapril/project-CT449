<script>
import { ElButton, ElInput, ElMessage } from 'element-plus';
import { useBookStore } from '@/stores/book';
export default {
    components: {
        ElInput,
    },
    data() {
        return {
            books: useBookStore().books,
            search: '',
        };
    },
    computed: {
        filteredBooks() {
            if (this?.books) {
                return this.books.filter((book) => book.tensach.toLowerCase().includes(this.search.toLowerCase()));
            }
            return [];
        },
    },
    methods: {
        handleNavigateToAddBook() {
            this.$router.push({
                name: 'add-book',
            });
        },
        navigatorToEdit(masach) {
            this.$router.push({
                name: 'edit-book',
                params: {
                    masach,
                },
            });
        },
        async handleDelete(masach) {
            const result = await useBookStore().delete(masach);
            (this.books = useBookStore().books), ElMessage(result);
        },
    },
};
</script>

<template>
    <div class="Book">
        <h4 class="text-center m-2">Book management</h4>
        <div class="container create-btn-container d-flex justify-content-end">
            <el-button class="bg-primary text-white" type="primary" plain @click="handleNavigateToAddBook"
                >Add book</el-button
            >
        </div>
        <div class="container table-container">
            <el-table :data="filteredBooks" style="width: 100%">
                <el-table-column type="expand">
                    <template #default="scope">
                        <div class="row">
                            <div class="col-6">
                                <p class="text-decoration-none" m="t-0 b-2">Name: {{ scope.row?.tensach }}</p>
                                <p m="t-0 b-2">Price: {{ scope.row?.dongia }}</p>
                                <p m="t-0 b-2">Total: {{ scope.row?.soquyen }}</p>
                                <p m="t-0 b-2">Year-Public: {{ new Date(scope.row?.namxuatban).getFullYear() }}</p>
                            </div>
                            <div class="col-6">
                                <p m="t-0 b-2">Publisger: {{ scope.row?.manxb?.TenNxb }}</p>
                                <p m="t-0 b-2">Author: {{ scope.row?.tacgia }}</p>
                                <p m="t-0 b-2">Amount: {{ scope.row?.soquyendamuon }}</p>
                            </div>
                        </div>
                    </template>
                </el-table-column>
                <el-table-column type="index" label=""> </el-table-column>
                <el-table-column label="ID " prop="masach" />
                <el-table-column label="Name" prop="tensach">
                    <template #default="scope">
                        <router-link to="/book/1" class="text-decoration-none text-black">
                            {{ scope.row.tensach }}
                        </router-link>
                    </template>
                </el-table-column>
                <el-table-column label="Price" prop="dongia" />
                <el-table-column label="Remaining">
                    <template #default="scope">
                        {{ scope?.row?.soquyen - scope.row?.soquyendamuon || 0 }}
                    </template>
                </el-table-column>
                <el-table-column align="right">
                    <template #header>
                        <el-input v-model="search" size="small" placeholder="Enter name to search" />
                    </template>
                    <template #default="scope">
                        <el-button size="small" type="success" @click="navigatorToEdit(scope.row.masach)"
                            >Edit</el-button
                        >
                        <el-button size="small" type="danger" @click="handleDelete(scope.row.masach)">Delete</el-button>
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
