<script setup>
import { ref } from "vue";
import axios from "axios";

const form = ref({
  name: "",
  email: "",
  contact: "",
  subject: "",
  message: ""
});

const submitForm = async () => {

  try {

    const response = await axios.post(
      "http://localhost:5000/contact",
      form.value
    );

    alert(response.data.message);

    form.value = {
      name: "",
      email: "",
      contact: "",
      subject: "",
      message: ""
    };

  } catch (error) {

    alert("Error Sending Form");

    console.log(error);
  }
};
</script>

<template>

  <div class="contactForm">

    <input
      type="text"
      placeholder="Name"
      v-model="form.name"
    />

    <input
      type="email"
      placeholder="Email"
      v-model="form.email"
    />

    <input
      type="text"
      placeholder="Contact Number"
      v-model="form.contact"
    />

    <input
      type="text"
      placeholder="Subject"
      v-model="form.subject"
    />

    <textarea
      placeholder="Message"
      v-model="form.message"
    ></textarea>

    <button @click="submitForm">
      Submit
    </button>

  </div>

</template>

<style scoped>

.contactForm{
  width:400px;
  margin:auto;
  display:flex;
  flex-direction:column;
  gap:15px;
  padding:30px;
}

input,
textarea{
  padding:12px;
}

button{
  padding:12px;
  background:black;
  color:white;
  border:none;
  cursor:pointer;
}

</style>