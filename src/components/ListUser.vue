<template>
  <div class="row p-5">
    <button class="btn btn-success mb-5">This is another component</button>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" :key="index">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ user.first_name }} {{ user.last_name }}</td>
          <td>
            <button
              type="button"
              @click="removeUserFromChild(index)"
              class="btn btn-danger"
            >
              Remove
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  props: ["users"],
  methods: {
    removeUserFromChild(index) {
      //   alert(index)
      this.$emit("deleteObject", index);
    }
  }
};
</script>
