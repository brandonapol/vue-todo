<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div>
      <nav>
        <div class="icon">
          <h3>TodoBot</h3>
        </div>
        <div class="links">
          <div class="link">
            <RouterLink to="/">Home</RouterLink>
          </div>
          <div class="link">
            <RouterLink to="/about">About</RouterLink>
          </div>
        </div>
      </nav>
    </div>
  </header>

  <RouterView />
</template>


