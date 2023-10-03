<template>
  <div class="container">
    <div v-for="task in tasks" :key="task.id">
      <div
        class="item-task d-flex align-items-start pt-3 pb-4 border-bottom"
        v-if="task.id == paramId"
      >
        <input
          type="checkbox"
          name="status"
          id="task"
          class="me-2 mt-2"
          :checked="task.isDone"
          v-model="task.isDone"
        />
        <div>
          <div class="title-task mb-1">
            {{ task.title }}
          </div>
          <div class="description-task small text-muted mb-3">
            {{ task.description }}
          </div>
          <input
            class="form-control form-control-sm"
            type="date"
            style="width: fit-content"
          />
        </div>
      </div>
    </div>
    <div class="action mt-4">
      <div
        class="btn btn-outline-secondary btn-sm px-3 mb-3"
        @click="$router.go(-1)"
      >
        Back
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout(_) {
    return "custom";
  },

  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "Hello Taskist 1",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic, ducimus? Aut, reiciendis consectetur exercitationem nesciunt sunt perferendis ratione ab expedita?",
          category: "tips",
          isDone: false,
        },
        {
          id: 2,
          title: "Ini judul task 2",
          description:
            "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Quae sit asperiores vel omnis eum expedita amet itaque, debitis quidem inventore totam consequuntur cupiditate eveniet numquam est.",
          category: "berita",
          isDone: false,
        },
        {
          id: 3,
          title: "Ini judul task ke-III",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Corrupti fuga perferendis quo molestiae aperiam soluta labore, sint unde ipsa in!",
          category: "tips",
          isDone: false,
        },
        {
          id: 4,
          title: "Judul task keempat",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos, vitae nihil quas quisquam quae laudantium consequuntur mollitia voluptatem culpa autem, impedit tempore in facilis!",
          category: "berita",
          isDone: false,
        },
        {
          id: 5,
          title: "Ini Contoh Judul Task ke-5",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic, ducimus? Aut, reiciendis consectetur exercitationem nesciunt sunt perferendis ratione ab expedita?",
          category: "berita",
          isDone: false,
        },
      ],
      paramId: this.$route.params.id,
    };
  },
};
</script>
