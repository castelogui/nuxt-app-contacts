<template>
  <div class="w-full px-2">
    <ListItem v-for="contact in contacts" :key="contact.id">
      {{ contact.name }}
      <template #actions>
        <button
          class="p-1 bg-emerald-300 rounded"
          @click="editContact(contact.id)"
        >
          Editar
        </button>
        <button
          class="p-1 bg-red-400 text-white rounded"
          @click="removeContact(contact.id)"
        >
          Excluir
        </button>
      </template>
    </ListItem>
  </div>
</template>

<script setup>
const router = useRouter();
const { contactList, deleteContact } = useContacts();
const contacts = contactList();
const editContact = (id) => {
  router.push({ path: "/form", query: { id } });
};
const removeContact = (id) => {
  deleteContact(id);
};
</script>
