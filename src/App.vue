<template>
    <main id="app">
        <Header/>
        <Content/>
        <Footer/>
    </main>
</template>

<script>
    // import Course from './models/Course'
    // import User from './models/User'
    // import Plus from './components/Courses'
    // import Plus from './components/Profile'
    // import Plus from './components/Plus'
    import Header from './components/Header'
    import Footer from "./components/Footer";
    import Content from "./components/Content";

    export default {
        name: 'app',
        components: {Content, Footer, Header },
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }
</style>
