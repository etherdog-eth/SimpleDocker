<template>
    <div id="loginContainer">
        <div id="loginForm">
            <img src="../assets/logo-tm.png" alt="" style="width: 300px">
            <a-form-model :form="loginForm">
                <a-input placeholder="请输入账号" class="loginInput" type="text" :allowClear="true" v-focus
                         @keydown.enter="login"
                         v-model="loginForm.username">
                    <a-icon slot="prefix" type="user"/>
                </a-input>
                <a-input placeholder="请输入密码" class="loginInput" type="password" :allowClear="true"
                         @keydown.enter="login"
                         v-model="loginForm.password">
                    <a-icon slot="prefix" type="lock"/>
                </a-input>


                <div id="loginCtl">
                    <a-button type="primary" class="button" @click="login">
                        <a-icon type="login"/>
                        登录
                    </a-button>

                    <a-button type="danger" class="button" @click="reset">
                        <a-icon type="reload"/>
                        重置
                    </a-button>

                    <a-button class="button" @click="openSourcePage">
                        <a-icon type="star"></a-icon>
                        关于
                    </a-button>
                </div>
            </a-form-model>
        </div>
    </div>
</template>


<script>

    import authApi from '../api/AuthApi'

    export default {
        data() {
            return {
                loginForm: {
                    username: '',
                    password: ''
                }
            }
        }, beforeMount() {
        }, methods: {
            login() {
                authApi.login(this.loginForm)
                    .then(res => {
                        let {Code, Data} = res.data
                        if (Code === 'OK') {
                            localStorage.setItem('token', `Bearer ${Data}`)
                            this.$router.push("/content")
                        }
                    })
            },
            reset() {
                this.loginForm = {}
            }, openSourcePage() {
                window.open('https://gitee.com/taoes_admin/SimpleDocker', '_blank')
            }
        }
    }
</script>

<style scoped>
    #loginContainer {
        width: 100%;
        height: 100%;
        background-color: lightgrey;
        flex-direction: column;
        display: flex;
        align-items: center;
        justify-content: center;

    }

    #loginForm {
        height: 350px;
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: white;
        margin-top: -100px;
        padding: 30px;
        border-radius: 10px;

    }

    #loginCtl {
        margin-top: 40px;
        width: 400px;
        display: flex;
        justify-content: space-around;
    }

    .loginInput {
        margin-top: 30px;
    }
</style>
