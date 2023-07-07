<template>
  <q-layout view="hhh lpR fFf" class="bg-grey-9">
    <q-header elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title class="row justify-center">
          <h6 class="q-ma-none text-weight-medium">
            Todo List
          </h6>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
</script>
