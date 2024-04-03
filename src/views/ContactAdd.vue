<template>
    <div v-if="contact" class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="addContact"
            />
        <p>{{ message }}</p>
    </div>
</template>
<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    export default {
        components: {
            ContactForm,
        },
       
        data() {
            return {
                contact: {
                    name: "",
                    phone: "",
                    email: "",
                    address: "",
                },
                message: "",
        
            };
        },

        methods: {
             
            async addContact(data) {
                try {
                    await ContactService.create(data);
                    this.message = "Thêm liên hệ thành công.";
                } catch (error) {
                    console.log("Thêm liên hệ thất bại.");
                }
            },
            
        },
        
        
    };
</script>