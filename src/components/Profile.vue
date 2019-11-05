<template>
    <div id="profile-container" :class="{active: this.activeTab === 'profile'}" class="tab">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">John Doe</li>
                    <li id="birthdate">11/10/1990</li>
                    <li id="faculty">Software Engineering</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>2.75</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Profile"
    }
</script>

<style scoped>
    .clear-fix {
        clear: both;
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

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .content .tab.active {
        display: block;
    }

</style>