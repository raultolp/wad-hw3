

<template>
    <main id="app">
        <Header/>
        <Content :user="user" :courses="courses" :calculate="calculateGPA"/>
        <Footer/>
    </main>
</template>

<script>
    // import Plus from './components/Courses'
    // import Plus from './components/Profile'
    // import Plus from './components/Plus'
    import Header from './components/Header'
    import Footer from "./components/Footer";
    import Content from "./components/Content";
    import Course from './models/Course'
    import User from './models/User'

    export default {
        name: 'app',
        methods: {
            calculateGPA: function () {
                let numberOfCourses = this.courses.length
                let totalPoints = 0.0
                for (let i = 0; i < numberOfCourses; i++) {
                    let points = this.courses[i].grade
                    totalPoints+=(points>90)? 4: (points>80)? 3: (points>70)? 2: (points>60)? 1: (points>50)? 0.5: 0;
                }
                this.user.gpa=(totalPoints/numberOfCourses).toFixed(2)
            }
        },
        components: {Content, Footer, Header },
        data: () => {
            return {
                user: new User("John", "Doe", "11/10/1990", "Software Engineering", 2.75),
                courses: [
                    new Course("Agile software development", 1, 82),
                    new Course("System modeling", 1, 85),
                    new Course("Object-oriented programming", 2, 99),
                    new Course("Estonian language Level A2", 2, 65)
                ]
            }
        }
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
