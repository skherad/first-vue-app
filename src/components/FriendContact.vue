<template>
  <li>
    <h2>{{ name }} {{ isFavorite === false ? '' : '(Favorite)' }}</h2>
    <button @click="toggleDetail">
      {{ detailsAreVisible ? "hide" : "Show" }} Details
    </button>
    <button @click="toggleFav">Favorite</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>email:</strong>{{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete', id)">Delete Friend</button>
  </li>
</template>
<script>
export default {
  // props: ["name", "phoneNumber", "emailAddress"],
  props: {
    id: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      require: true,
    },
    emailAddress: {
      type: String,
      require: true,
    },
    isFavorite: {
      type: Boolean,
      require: false,
      default: false,
      validator: function (value) {
        return value === true || value === false
      }
    },
  },
  // emits: ['toggle-favorite'],
  emits: {
    'toggle-favorite': function (id) {
      if (id) {
        return true
      } else {
        console.log('id is missing')
        return false
      }
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetail() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFav() {
      this.$emit('toggle-favorite', this.id)
    }
  },
};
</script>
