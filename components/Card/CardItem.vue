<template>
  <div
    :class="[
      'item-task d-flex align-items-start border-bottom pt-3 pb-4 ps-0 pe-2',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
    ]"
  >
    <input
      type="checkbox"
      name="status"
      id="task"
      class="me-2 mt-2"
      :checked="task.isDone"
      v-model="task.isDone"
    />
    <div
      :class="[
        'd-flex flex-column',
        task.isDone ? 'text-decoration-line-through fst-italic' : '',
      ]"
    >
      <nuxt-link class="title-task mb-1" :to="'/taskist/detail/' + task.id">
        {{ task.title }}
      </nuxt-link>
      <div class="description-task small text-muted">
        {{ task.description }}
      </div>
      <span
        class="badge bg-secondary link-light mt-2"
        style="width: fit-content"
        >{{ task.category }}
      </span>
      <input
        type="date"
        class="form-control form-control-sm mt-2"
        style="width: fit-content"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      default: "Untitled",
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
};
</script>
