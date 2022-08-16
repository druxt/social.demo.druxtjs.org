<template>
  <DruxtRouter>
    <template #default="{ route }">
      <DruxtEntity v-bind="route.props" :settings="{ query: { include: ['group_type' ] } }">
        <template #default="{ entity }">
          <div class="hero" style="background-image: url('https://placeimg.com/640/480/arch');">
            <div class="hero-overlay bg-opacity-60"></div>
            <div class="hero-content text-center text-neutral-content py-32">
              <div class="max-w-md">
                <span class="badge mb-5 bg-opacity-80" v-text="groupType(entity).attributes.label" />
                <h1 class="mb-5 text-5xl font-bold" v-text="entity.attributes.label" />
                <!-- <p class="mb-5" v-html="entity.attributes.field_group_description.processed" /> -->
              </div>
            </div>
          </div>

          <div class="container mx-auto -mt-8">
            <div class="sm:grid grid-cols-12 gap-4">
              <DuiCard class="col-span-4">
                <DruxtView
                  view-id="upcoming_events"
                  display-id="upcoming_events_group"
                  :arguments="[id]"
                />
              </DuiCard>

              <div class="col-span-8">
                <div class="tabs tabs-boxed">
                  <NuxtLink
                    v-for="tab of tabs"
                    class="tab"
                    :class="{ 'tab-active': model === tab.id }"
                    :key="tab.id"
                    :to="`/group/${id}/${tab.id}`"
                    v-text="tab.label"
                    @click.native="model = tab.id"
                  />
                </div>

                <NuxtChild :entity="entity" :group-id="id" />
              </div>
            </div>
          </div>
        </template>
      </DruxtEntity>
    </template>
  </DruxtRouter>
</template>

<script>
export default {
  layout: 'group',

  data: ({ $route }) => ({
    model: $route.path.split('/').pop(),
  }),

  computed: {
    tabs: () => ([
      { id: 'stream', label: 'Stream' },
      { id: 'about', label: 'About' },
      { id: 'events', label: 'Events' },
      { id: 'topics', label: 'Topics' },
    ]),
    id: ({ $route }) => $route.params.id,
  },

  methods: {
    groupType(entity) {
      return entity.included.find((o) => o.type === 'group_type--group_type')
    }
  }
}
</script>
