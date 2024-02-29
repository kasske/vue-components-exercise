<template>
    <!-- in vue 2 the wrapping div was necessary but in vue 3 we can remove it if we like -->
    <div>
        <h2>
            Manage Goals
        </h2>
        <input type="text" ref="goal">
        <button @click="setGoal">Set goal</button>

        <!-- teleporting to css selector to html page (teleport is built in to vue) -->
        <teleport to="body">
            <error-alert v-if="inputIsInvalid">
                <h2>Input is invalid</h2>
                <p>Please enter some characters...</p>
    
                <button @click="confirmError">Ok</button>
            </error-alert>
        </teleport>
    </div>
</template>

<script>
    import ErrorAlert from './ErrorAlert.vue';
    export default {
        components: {
            ErrorAlert,
        },
        data() {
            return {
                inputIsInvalid: false,
            }
        },
        methods: {
            setGoal() {
                const enteredValue = this.$refs.goal.value;

                if (enteredValue === '') {
                    this.inputIsInvalid = true;
                }
            },

            confirmError() {
                this.inputIsInvalid = false;
            }
        }
    }
</script>