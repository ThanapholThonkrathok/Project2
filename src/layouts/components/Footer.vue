<template>
  <div class="h-100 d-flex flex-wrap align-center justify-space-between">
    <!-- 👉 Footer: left content -->
    <span class="d-flex align-center">
      &copy;
      {{ new Date().getFullYear() }}
      Made With
      By <a
        href="https://themeselection.com"
        target="_blank"
        rel="noopener noreferrer"
        class="text-primary ms-1"
      />
    </span>
    <span class="d-flex align-center">
      Distributed By <a
        href="https://themewagon.com"
        target="_blank"
        rel="noopener noreferrer"
        class="text-primary ms-1"
      />
    </span>
    <!-- 👉 Footer: right content -->
    <span class="d-md-flex gap-x-4 text-primary d-none">
      <a
        href="https://themeselection.com/license/"
        target="noopener noreferrer"
      />
      <a
        href="https://themeselection.com/"
        target="noopener noreferrer"
      />
      <a
        href="https://demos.themeselection.com/sneat-vuetify-vuejs-admin-template/documentation/"
        target="noopener noreferrer"
      />
    </span>
  </div>
</template>
