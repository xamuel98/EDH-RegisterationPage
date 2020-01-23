<template>
    <div>
        <div class="form-group">
            <label for="course-email-1">Email Address</label>
            <input name="course-email" id="course-email-1" type="email" class="form-control form-control-lg" placeholder="you@yoursite.com">
        </div>
    </div>
</template>

<script>
export default {
    name: 'EmailField',
    props: {
        value: String
    },
    data() {
        return {
            form: {
                email: '',
                firstName: ''
            }
        }
    }
}
</script>

<style scoped>

</style>
