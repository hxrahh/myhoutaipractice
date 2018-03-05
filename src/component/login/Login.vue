<template>
    <div class="login">
        <section>
            <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm2" label-width="100px" class="demo-ruleForm">
                <el-form-item label="用户名" prop="uname">
                    <el-input type="text" v-model="ruleForm2.uname" auto-complete="off"></el-input>
                </el-form-item>

                <el-form-item label="密码" prop="upwd">
                    <el-input type="password" v-model="ruleForm2.upwd" auto-complete="off"></el-input>
                </el-form-item>

                <el-form-item>
                    <el-button type="primary" @click="submitForm('ruleForm2')">提交</el-button>
                    <el-button @click="resetForm('ruleForm2')">重置</el-button>
                </el-form-item>
            </el-form>
        </section>

    </div>
</template>

<script>
export default {
    data() {
        return {
            ruleForm2: {
                uname: '',
                upwd: ''
            },
            rules2: {
                uname: [
                    { required: true, message: '请输入用户名', trigger: 'blur' }
                ],
                upwd: [
                    { required: true, message: '请输入密码', trigger: 'blur' },
                ],
            }
        };
    },
    methods: {
        login() {
            this.$http.post(this.$api.login, this.ruleForm2).then((res) => {
                console.log(res)

                if (res.data.status == 0) {
                    this.$alert('登录成功', '哈哈', {
                        callback: () => {
                            localStorage.setItem('uname',res.data.message.uname)
                            this.$router.push({name:'admin'});
                        }
                    });
                } else {
                    this.$alert('登录失败')

                }
            })
        },
        submitForm(formName) {
            this.$refs[formName].validate(valid => {
                if (valid) {
                    this.login();
                } else {
                    this.$alert('账号或密码不合格')
                }
            });
        },
        resetForm(formName) {
            this.$refs[formName].resetFields();
        }
    }
}
</script>


<style scoped lang="less">
.login {
    // width: 100%;
    height: 100%;
    background-color: aqua;
    section {
        width: 400px; // height: 300px;
        margin: 0 auto;
        position: relative;
        top: 50%;
        transform: translateY(-50%);
        border: 3px solid #000;
        border-radius: 5px;
    }
}
</style>