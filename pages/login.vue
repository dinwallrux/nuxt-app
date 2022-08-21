<template>
	<el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="120px" label-position="top" class="demo-ruleForm">
		<el-form-item label="Name" prop="name">
			<el-input v-model="ruleForm.name"></el-input>
		</el-form-item>
		<el-form-item label="Email" prop="email">
			<el-input v-model="ruleForm.email"></el-input>
		</el-form-item>
		<el-form-item label="Password" prop="pass">
			<el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
		</el-form-item>
		<el-form-item>
			<el-button type="primary" @click="submitForm('ruleForm')">Create</el-button>
			<el-button @click="resetForm('ruleForm')">Reset</el-button>
		</el-form-item>
	</el-form>
</template>
<script>
export default {
	layout: 'auth',
  name: "Register",
	data() {
		var validatePass = (rule, value, callback) => {
			if (value === '') {
				callback(new Error('Please input the password'));
			} else {
				if (this.ruleForm.checkPass !== '') {
					this.$refs.ruleForm.validateField('checkPass');
				}
				callback();
			}
		};
		return {
			ruleForm: {
				name: '',
				email: '',
				pass: '',
			},
			rules: {
				name: [
					{ required: true, message: 'Please input Activity name', trigger: 'blur' },
					{ min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' }
				],
				email: [
					{ required: true, message: 'Please input email address', trigger: 'blur' },
					{ type: 'email', message: 'Please input correct email address', trigger: ['blur', 'change'] }
				],
				pass: [
					{ validator: validatePass, trigger: 'blur' }
				],
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
<style lang="scss">
  
</style>