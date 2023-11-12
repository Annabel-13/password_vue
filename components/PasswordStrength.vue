<template>
	<div>
	  <label for="password">Password:</label>
	  <input type="password" id="password" v-model="password" @input="checkPassword">
	  <div v-if="password.length > 0">
		<strong>Password Strength:</strong> {{ passwordStrength }}
	  </div>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		password: '',
		passwordStrength: '',
	  };
	},
	methods: {
	  checkPassword() {
		// Check password strength based on certain criteria
		const lengthRegex = /^.{8,}$/;
		const uppercaseRegex = /[A-Z]/;
		const lowercaseRegex = /[a-z]/;
		const digitRegex = /\d/;
		const specialCharRegex = /[!@#$%^&*()_+{}\[\]:;<>,.?~\\/-]/;
  
		let strength = 0;
  
		if (lengthRegex.test(this.password)) {
		  strength++;
		}
  
		if (uppercaseRegex.test(this.password)) {
		  strength++;
		}
  
		if (lowercaseRegex.test(this.password)) {
		  strength++;
		}
  
		if (digitRegex.test(this.password)) {
		  strength++;
		}
  
		if (specialCharRegex.test(this.password)) {
		  strength++;
		}
  
		// Determine password strength level
		if (strength === 0) {
		  this.passwordStrength = 'Very Weak';
		} else if (strength === 1) {
		  this.passwordStrength = 'Weak';
		} else if (strength === 2) {
		  this.passwordStrength = 'Moderate';
		} else if (strength === 3) {
		  this.passwordStrength = 'Strong';
		} else {
		  this.passwordStrength = 'Very Strong';
		}
	  },
	},
  };
  </script>