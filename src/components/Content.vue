<template>
    <section id="container">
        <section id="main">
            <div class="content">
                <div id="profile-container" :class="{active: this.activeTab === 'profile'}" class="tab">
                    <div id="profile">
                        <div class="avatar">
                            <img src="../assets/me.png" id="picture" alt="My picture">
                        </div>
                        <div class="info">
                            <ul>
                                <li id="name">{{user.firstname}} {{user.lastname}}</li>
                                <li id="birthdate">{{user.birthdate}}</li>
                                <li id="faculty">{{user.faculty}}</li>
                            </ul>
                        </div>
                        <div id="gpa">
                            <strong>{{user.gpa}}</strong>
                        </div>
                        <div class="clear-fix"></div>
                    </div>
                </div>
                <div id="courses-container" :class="{active: this.activeTab === 'courses'}" class="tab">
                    <h1 class="title">Courses</h1>
                    <span>
                    <table id="courses">
                        <thead>
                        <tr>
                            <th>#</th>
                            <th>Course Title</th>
                            <th>Semester</th>
                            <th>Grade</th>
                        </tr>
                        </thead>
                        <tbody>
                        <tr v-for="(course, index) in courses" :key="index">
                            <td>{{index + 1}}</td>
                            <td>{{course.title}}</td>
                            <td>{{course.semester}}</td>
                            <td>{{course.grade}}</td>
                        </tr>
                        </tbody>
                    </table>
                    </span>
                    <br>
                    <br>
                    <div>
                        <button id="add-course-button" class="blue-button" @click="isShowing ^= true">+</button>
                        <span v-show="isShowing" id="add-course">
                            <input class="input" type="text" placeholder="Course title" v-model="title">
                            <input class="input" type="number" min="1" max="8" placeholder="Semester" v-model="semester">
                            <input class="input" type="number" min="0" max="100" placeholder="Grade" v-model="grade">
                            <button class="green-button" id="save-course" @click="addCourse(true)">Save</button>
                            <button class="grey-button" id="cancel-course" @click="addCourse(false)">Cancel</button>
                        </span>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button id="profile-button" :class="{active: this.activeTab === 'profile'}" class="pill" @click="togglePanel('profile')">Profile</button>
                <button id="courses-button" :class="{active: this.activeTab === 'courses'}" class="pill" @click="togglePanel('courses')">Courses</button>
            </div>
        </section>
    </section>
</template>

<script>
    import Course from "../models/Course";

    export default {
        name: "Content",
        // el: "#add-course",

        data: () => {
            return {
                activeTab: "profile",
                isShowing: false,
                title: "",
                semester: "",
                grade: "",
            }
        },
        methods: {
            togglePanel: function (name) {
                this.activeTab = name;
            },
            addCourse: function (add) {
                if (add === true)
                    this.courses.push(new Course(this.title, this.semester, this.grade));
                this.title = "";
                this.semester = "";
                this.grade = "";
                this.isShowing = false;
            },
        },
        props: {
            user: Object,
            courses: Array
        }
    }
</script>

<style scoped>
    .clear-fix {
        clear: both;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
    }

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

    /*#add-course {display: none;}*/
</style>