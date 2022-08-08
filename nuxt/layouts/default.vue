<template>
  <div>
    <header>
      <!-- <DruxtBlockRegion name="header" /> -->
      <!-- The account menu errors once user is logged in, needs investigation. -->
      <DruxtBlock v-if="!$auth.loggedIn" id="socialblue_account_menu" />
      <DruxtBlock id="socialblue_sitebranding" />
      <DruxtBlock id="socialblue_mainnavigation" />
    </header>

    <Nuxt />
  </div>
</template>
