<template>
  <div>
    <h4>Thêm Liên hệ Mới</h4>
    <ContactForm @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: { ContactForm },
  data() {
    return {
      message: "",
    };
  },
  methods: {
    async createContact(contactData) {
      try {
        await ContactService.create(contactData);
        this.message = "Liên hệ được thêm thành công.";
        this.$router.push({ name: "contactbook" });
      } catch (error) {
        console.error(error);
        this.message = "Đã xảy ra lỗi khi thêm liên hệ.";
      }
    },
  },
};
</script>
