<template>
    <li>
        <h2>{{ name }} {{ isFavourite ? ' ( Favourite )' : '' }}</h2>
        <button @click="toggleDetails"> {{ detailsAreVisible ? 'Hide': 'Show' }} Details </button><br/>
        <button @click="toggleFavourite()"> Toggle Favourite </button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone: </strong> {{ phoneNumber }}</li>
            <li><strong>Email: </strong> {{ emailAddress }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    // props: [
    //     'name',
    //     'phoneNumber',
    //     'email',
    //     'id',
    //     'isFavourite'
    // ],
    props: {
        id: {
            type: String,
            required: true,
        },
        name: {
            type: String,
            required: true,
        },
        phoneNumber: {
            type: String,
            required: true,
        },
        emailAddress: {
            type: String,
            required: true,
        },
        isFavourite: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    emits: ['toggle-favourite'],
    // emits: {
    //     'toggle-favourite': function(id) {
    //         if (id) {
    //             return true;
    //         } else {
    //             return false;
    //         }
    //     }
    // },
    data() {
        return {
            detailsAreVisible: true,
            // friendIsFavourite: this.isFavourite,
            friend: {
                id: 'manuel',
                name: 'Manuel Lorenz',
                phone: '00123455',
                email: 'manuel@localhost.comm'
            }
        }
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite() {
            // this.friendIsFavourite = !this.friendIsFavourite;
            this.$emit('toggle-favourite', this.id);
        }
    }
};
</script>
<style>

</style>