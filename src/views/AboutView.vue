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
        <h5 class="text-center m-2">Đây là trang web phục vụ cho project CT449 - Phát triển ứng dụng web</h5>
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
