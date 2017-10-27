<template>
  <el-form :model="ruleForm2" :rules="rules2" ref="ruleForm2" label-width="80px" class="eform">
    <el-form-item label="用户名" prop="uname">
      <el-input v-model="ruleForm2.uname"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="pass">
      <el-input type="password" v-model="ruleForm2.pass" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm2')">登录</el-button>
      <el-button @click="resetForm('ruleForm2')">取消</el-button>
    </el-form-item>
  </el-form>
</template>
<script type="text/ecmascript-6">
  export default {
    data() {
      var checkUname = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('请输入用户名'));
        }

      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          callback();
        }
      };
      return {

        ruleForm2: {
          pass: '',
          uname: ''
        },
        rules2: {
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ],

          uname: [
            { validator: checkUname, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('登录');
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
