<template>
    <li>
        <h2>{{name}} {{favorite ? '(Favorite)' : ''}}</h2>
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
        'name',
        'phone',
        'email',
        'isFavorite'
    ],
    data() {
        return {
            showDetails: false,
            favorite: this.isFavorite
        }
    },
    methods: {
        toggleDetails() {
            this.showDetails = !this.showDetails;
        },
        toggleFavorite() {
            this.favorite = !this.favorite;
        }
    },
}
</script>