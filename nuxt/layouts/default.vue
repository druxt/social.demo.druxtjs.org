<template>
  <div>
    <header class="sticky top-0 z-30 flex h-16 w-full justify-center bg-opacity-90 backdrop-blur transition-all duration-100 bg-neutral text-neutral-content shadow-sm">
      <DuiNavbar title="DruxtSocial" />
    </header>

    <main class="container mx-auto">
      <DruxtBlockRegion name="hero" theme="socialblue" />

      <DruxtBlockRegion name="title" theme="socialblue" />

      <div class="sm:grid grid-cols-12 gap-4">
        <Nuxt class="col-span-8" />

        <aside class="col-span-4">
          <DruxtBlockRegion
            name="complementary_top"
            theme="socialblue"
          />
        </aside>
      </div>
    </main>

    <DruxtBlockRegion
      class="mt-16"
      name="footer"
      theme="socialblue"
    />
  </div>
</template>
