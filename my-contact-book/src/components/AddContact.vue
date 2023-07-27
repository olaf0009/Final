<template>
    <div>
      <h1>Add Contact</h1>
      <form @submit.prevent="addContact">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name" required>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
        <button type="submit">Save</button>
        <router-link to="/">Cancel</router-link>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: '',
      };
    },
    methods: {
      addContact() {
        const newContact = {
          id: new Date().getTime(),
          name: this.name,
          email: this.email,
        };

        // Save the new contact to local storage
      const storedContacts = localStorage.getItem('contacts');
      const contacts = storedContacts ? JSON.parse(storedContacts) : [];
      contacts.push(newContact);
      localStorage.setItem('contacts', JSON.stringify(contacts));

      // Reset the form fields
      this.name = '';
      this.email = '';

      // Navigate back to the contact list
      this.$router.push('/');
    },
  },
};
</script>