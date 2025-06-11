<template>
  <div class="layout-box">
    <div class="layout-header">
      <slot name="header" />
    </div>
    <div class="layout-content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.layout-box {
  background: white;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0,0,0,0.05);
  padding: 1rem;
}

.layout-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.layout-content {
  overflow-x: auto;
}
</style>
