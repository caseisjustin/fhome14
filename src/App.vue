<script>
export default {
  data() {
    return {
      feedbackType: "",
      description: "",
      firstName: "",
      lastName: "",
      password: "",
      email: "",
      get: "",
      passwordError: false,
    };
  },
  computed: {
    isSubmitDisabled() {
     return this.password.length < 6 || !this.firstName || !this.lastName || !this.description || !this.feedbackType || !this.email;
    },
  },
  methods: {
    checkPassword() {
      this.passwordError = this.password.length < 6;
    },
    handleSubmit() {
      if (!this.isSubmitDisabled) {
        alert(`Form submitted with: 
          Feedback Type: ${this.feedbackType}
          Description: ${this.description}
          Name: ${this.firstName} ${this.lastName}
          Email: ${this.email}`);
      }
    },
  },
};
</script>


<template>
  <form action="submit">
    <h1>Feedback Form</h1>
    <p>We would love to hear your thoughts, suggestions, concerns or problems with anythingso we can improve</p>
    <div class="feedback-type">
      <h5>Feedback Type</h5>
      <input value="comment" id="comment" type="radio" v-model="get" />
      <label for="comment">Comments</label>
      <input value="suggest" id="suggest" type="radio" v-model="get" />
      <label for="suggest">Suggestions</label>
      <input value="quest" id="quest" type="radio" v-model="get" />
      <label for="quest">Questions</label>
    </div>
    <div class="desc-feedback">
      <label for="desc">Describe Your Feedback</label>
      <textarea name="description" id="desc" v-model="desc" required></textarea>
    </div>
    <div class="naming">
      <label for="firstname">first name</label>
      <input id="firstName" type="text" placeholder="FirstName" />
      <label for="lastName">last name:</label>
      <input id="lastName" type="text" placeholder="LastName" />
    </div>
    <!-- password -->
    <div class="password-field">
      <label for="password">Password:</label>
      <input type="password" id="password" v-model="password" @keyup="checkPassword" required />
      <p v-if="passwordError" class="error-message">No less than 6 chars</p>
    </div>
    <!-- email -->
    <div class="email-field">
      <label for="email">E-mail:</label>
      <input type="email" id="email" v-model="email" @keyup.enter="submitForm" required />
    </div>
    <button type="submit">submit ME</button>
  </form>
</template>

<style scoped>
.form-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
}

h1 {
  text-align: center;
}

p {
  text-align: center;
  margin-bottom: 2rem;
}

.feedback-type label {
  display: inline-block;
  margin-right: 1rem;
}

.feedback-description,
.name-fields,
.password-field,
.email-field {
  margin-bottom: 1.5rem;
}

.error-message {
  color: red;
  font-size: 0.875rem;
}

button {
  display: block;
  width: 100%;
  padding: 1rem;
  background-color: green;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1.1rem;

  &:disabled {
    background-color: gray;
    cursor: not-allowed;
  }
}
</style>
