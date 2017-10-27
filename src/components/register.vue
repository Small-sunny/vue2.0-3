<template>
  <el-form :model="ruleForm2" :rules="rules2" ref="ruleForm2" label-width="80px" class="eform">
    <el-form-item label="用户名" prop="uname">
      <el-input v-model="input2"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="pass">
      <el-input type="password" v-model="ruleForm2.pass" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="确认密码" prop="checkPass">
      <el-input type="password" v-model="ruleForm2.checkPass" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="电子邮箱" prop="email">
      <el-input type="email" v-model="ruleForm2.email"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm2')">注册</el-button>
      <el-button @click="resetForm('ruleForm2')">取消</el-button>
    </el-form-item>
  </el-form>
</template>
<script type="text/ecmascript-6">
  export default {
    data() {
      var checkUname = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('用户名不能为空'));
        }

      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          if (this.ruleForm2.checkPass !== '') {
            this.$refs.ruleForm2.validateField('checkPass');
          }
          callback();
        }
      };
      var validatePass2 = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请再次输入密码'));
        } else if (value !== this.ruleForm2.pass) {
          callback(new Error('两次输入密码不一致!'));
        } else {
          callback();
        }
      };
      var checkEmail=(rule, value, callback) => {
        if (!value) {
          return callback(new Error('邮箱不能为空'));
        }
      }
      return {

        ruleForm2: {
          pass: '',
          checkPass: '',
          uname: '',
          input2: '',
          email:''
        },
        rules2: {
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ],
          checkPass: [
            { validator: validatePass2, trigger: 'blur' }
          ],
          uname: [
            { validator: checkUname, trigger: 'blur' }
          ],
          email: [
            { validator: checkEmail, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style scoped>
  .eform{
    margin-top: 30px;
  }
  .el-input, .el-input__inner{
    width:400px;
  }
</style>
