<template>
  <!-- <DruxtBlockRegion name="header" /> -->
  <nav class="navbar">
    <div class="flex-1">
      <!-- <DruxtBlock id="socialblue_sitebranding" /> -->
      <NuxtLink class="btn btn-ghost normal-case text-xl" to="/" v-text="title" />

      <!-- <DruxtBlock id="socialblue_mainnavigation" /> -->
      <DruxtMenu name="main">
        <template #default="{ items }">
          <ul class="menu menu-horizontal p-0">
            <li v-for="item of items" :key="item.entity.id">
              <NuxtLink v-if="!item.children.length" :to="item.entity.attributes.url" v-text="item.entity.attributes.title" />
              <template v-else>
                <a>
                  {{ item.entity.attributes.title }}
                  <svg class="fill-current" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path d="M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z"/></svg>
                </a>
                <ul class="p-2 bg-neutral">
                  <li v-for="child of item.children" :key="child.entity.id">
                    <NuxtLink :to="child.entity.attributes.url" v-text="child.entity.attributes.title" />
                  </li>
                </ul>
              </template>
            </li>
          </ul>
        </template>
      </DruxtMenu>

    </div>
    <div class="flex-none">
      <!-- The account menu errors once user is logged in, needs investigation. -->
      <!-- <DruxtBlock v-if="!$auth.loggedIn" id="socialblue_account_menu" /> -->
      <DruxtMenu v-if="!$auth.loggedIn" name="account">
        <template #default="{ items }">
          <ul class="menu menu-horizontal p-0">
            <li v-for="item of items" :key="item.entity.id">
              <NuxtLink :to="item.entity.attributes.url" v-text="item.entity.attributes.title" />
            </li>
          </ul>
        </template>
      </DruxtMenu>
      <div v-else class="dropdown dropdown-end">
        <label tabindex="0" class="btn btn-ghost btn-circle avatar">
          <div class="w-10 rounded-full">
            <img src="https://placeimg.com/80/80/people" />
          </div>
        </label>
        <ul tabindex="0" class="mt-3 p-2 shadow menu menu-compact dropdown-content bg-base-100 rounded-box w-52">
          <li><a @click.prevent="$nuxt.$auth.logout()">Logout</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>
