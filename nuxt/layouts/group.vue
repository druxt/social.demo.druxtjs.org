<template>
  <div>
    <header class="sticky top-0 z-30 flex h-16 w-full justify-center bg-opacity-90 backdrop-blur transition-all duration-100 bg-neutral text-neutral-content shadow-sm">
      <DuiNavbar title="DruxtSocial" />
    </header>

    <Nuxt />

    <DruxtBlockRegion
      class="mt-16"
      name="footer"
      theme="socialblue"
    />
  </div>
</template>
