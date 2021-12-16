<template>
    <li>
        <h2>{{name}} {{isFavorite ? '(Favorite)' : ''}}</h2>
        <button @click="toggleDetails">Show Details</button>
        <button @click="toggleFavorite">Is Favorite?</button>
        <ul v-if="showDetails">
            <li>Phone {{phone}}</li>
            <li>Email {{email}}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props: [
        'id',
        'name',
        'phone',
        'email',
        'isFavorite'
    ],
    emits: [
        'toggle-favorite'
    ],
    data() {
        return {
            showDetails: false,
        }
    },
    methods: {
        toggleDetails() {
            this.showDetails = !this.showDetails;
        },
        toggleFavorite() {
            this.$emit('toggle-favorite', this.id);
        }
    },
}
</script>