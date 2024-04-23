<script>
import Header from '@/components/Header.vue';
import { ElButton } from 'element-plus';
import BookList from '@/components/Home/BookList.vue';
import Footer from '@/components/Footer.vue';

export default {
    name: 'Home',
    components: {
        ElButton,
        Header,
        BookList,
        Footer,
    },
};
</script>

<template>
    <Header></Header>
    <main class="container">
        <h5 class="text-center m-2">SĐT : 0385990041</h5>
        <h5 class="text-center m-2">Email : khoib2016975@student.ctu.edu.vn</h5>
        <h5 class="text-center m-2">Name : Trần Minh Khôi</h5>
        <h5 class="text-center m-2">Class : DI20Z6A3</h5>
        <h5 class="text-center m-2">Đồ án phát triển ứng dụng web CT- 449</h5>
        <!-- <BookList></BookList> -->
    </main>
    <!-- <Footer></Footer> -->
</template>

<style lang="scss">
main {
    .pagination {
        margin-top: 12px;
        display: flex;
        align-items: center;
        justify-content: flex-end;
    }
}
</style>
