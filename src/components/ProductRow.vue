<template>
  <tr>
    <td class="judul" data-label="Produk">{{ judul }}</td>
    <td class="harga" data-label="Harga">Rp{{ harga }}</td>
    <td class="views" data-label="Views">{{ views }}</td>
    <td class="status" data-label="Status">{{ status }}</td>
    <td class="aksi" data-label="Aksi">
      <button class="edit" @click="$emit('edit')">✏️</button>
      <button class="hapus" @click="$emit('hapus')">🗑</button>
    </td>
  </tr>
</template>

<script setup>
defineProps(['judul', 'harga', 'views', 'status'])
defineEmits(['edit', 'hapus'])
</script>

<style scoped>
.judul {
  font-weight: 500;
  color: #1f2937;
}

.harga {
  color: #2563eb;
}

.views {
  color: #10b981;
}

.status {
  font-weight: 500;
  color: #6b7280;
}

.aksi {
  display: flex;
  gap: 0.5rem;
  justify-content: flex-start;
}

button {
  background-color: #e0f2fe;
  border: none;
  padding: 0.4rem 0.6rem;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

button:hover {
  background-color: #bae6fd;
  transform: scale(1.05);
}

.edit {
  color: #0284c7;
}

.hapus {
  color: #ef4444;
  background-color: #fee2e2;
}

.hapus:hover {
  background-color: #fecaca;
}
</style>

