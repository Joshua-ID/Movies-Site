<template>
  <div class="nav-section">
    <div class="nav-wrapper">
      <h4 class="logo-style"><span>cloud</span>9 Movies</h4>
    </div>
  </div>
</template>

<script setup></script>

<style>
.nav-section {
  background: var(--primary-color);
  padding: 0.1rem 2.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo-style {
  color: #fff;
  font-size: 2rem;
  font-family: var(--style-font);
}
span {
  font-size: 1.5rem;
  margin-right: -3px;
  color: rgb(10, 77, 29);
}

.search-btn {
  padding: 9px;
  outline: none;
  border: none;
  min-width: 230px;
  border-radius: 9px;
}
</style>
