<template>
    <div>
      <h1>Contact List</h1>
      <ul>
        <li v-for="contact in contacts" :key="contact.id">{{ contact.name }}</li>
      </ul>
      <router-link to="/add">Add Contact</router-link>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        contacts: [],
      };
    },
    mounted() {
      // Fetch contacts from local storage
      const storedContacts = localStorage.getItem('contacts');
      this.contacts = storedContacts ? JSON.parse(storedContacts) : [];
    },
  };
  </script>