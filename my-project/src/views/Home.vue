<template>
    <div>
        <!-- <div class="preloader">
            <div class="lds-ripple">
                <div class="lds-pos"></div>
                <div class="lds-pos"></div>
            </div>
        </div> -->
        <div aria-live="polite" aria-atomic="true" style="position: relative; min-height: 200px;">
            <div class="toast" style="position: absolute; top: 0; right: 0;">
                <div class="toast-header">
                <!-- <img src="..." class="rounded mr-2" alt="..."> -->
                <strong class="mr-auto">Bootstrap</strong>
                <small>11 mins ago</small>
                <button type="button" class="ml-2 mb-1 close" data-dismiss="toast" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
                </div>
                <div class="toast-body">
                Hello, world! This is a toast message.
                </div>
            </div>
        </div>
        <div class="main-wrapper">
            <div class="space-lg space-md space-xs">
                <div class="container">
                    <div class="row justify-content-center">
                        <div class="col-xl-5 col-lg-6 col-md-7 text-center text-lg-left mb-5 mb-lg-0">
                            <h1 class="display-3">Learn how to build better websites.</h1>
                            <!-- <div class="my-4">
                                <p class="lead">Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium.</p>
                            </div> -->
                        </div>
                        <div class="col">
                            <div class="row justify-content-center">
                                <div class="col-xl-8 col-md-10">
                                   <div class="form-group">
                                        <label for="course-email-1">Email Address</label>
                                        <input v-model="email" name="course-email" id="course-email-1" type="email" class="form-control form-control-lg" placeholder="👋 Enter your email...">
                                    </div>
                                   <div class="form-group text-center">
                                        <button class="btn btn-lg btn-primary btn-block mb-2" @click="showModal=!showModal">Sign up for free</button>
                                        <small>You’ll recieve your first newsletter via email in less than a minute.</small>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- Modal -->
        <div v-if="showModal" @close="showModal = !showModal" class="modal modal-active" id="loginmodal" tabindex="-1" role="dialog" aria-labelledby="loginmodalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-scrollable" role="document">
                <div class="modal-content">
                    <div class="modal-body">
                        <button type="button" @click="showModal = !showModal" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                        <!-- login form start -->
                        <div class="login-form border-0">
                            <div class="login-form-body">
                                <h4 class="login-form-title">Sign up to EDH</h4>
                                <form @submit="checkForm">
                                    <!-- <p v-if="errors.length">
                                        <b>Please correct the following error(s):</b>
                                        <ul>
                                            <li v-for="error in errors" :key="error.id">{{ error }}</li>
                                        </ul>
                                    </p> -->

                                    <div class="form-group">
                                        <label for="email">Email</label>
                                        <input v-model="email" type="email" class="form-control" id="email" aria-describedby="email" placeholder="example@gmail.com" required="">
                                    </div>
                                    <div class="row">
                                        <div class="col">
                                            <div class="form-group">
                                                <label class="form-control-label">First name</label>
                                                <input v-model="firstName" class="form-control" type="text" placeholder="First name">
                                            </div>
                                        </div>
                                        <div class="col">
                                            <div class="form-group">
                                                <label class="form-control-label">Last name</label>
                                                <input v-model="lastName" class="form-control" type="text" placeholder="Your last name">
                                            </div>
                                        </div>
                                    </div>
                                    <div class="row">
                                        <div class="col-12">
                                            <div class="form-group mb-1">
                                                <label>Skill Level:</label>
                                            </div>
                                        </div>
                                        <div class="col">
                                            <div class="form-group rounded bg-white p-2 border">
                                                <div class="custom-control custom-radio">
                                                    <input v-model="skill_1" type="radio" id="course-radio-beginner-1" name="course-radio-1" class="custom-control-input">
                                                    <label class="custom-control-label" for="course-radio-beginner-1">Undergraduate</label>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="col">
                                            <div class="form-group rounded bg-white p-2 border">
                                                <div class="custom-control custom-radio">
                                                    <input v-model="skill_2" type="radio" id="course-radio-advanced-1" name="course-radio-1" class="custom-control-input">
                                                    <label class="custom-control-label" for="course-radio-advanced-1">Graduate</label>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="login-remember-password-block">
                                        <div class="custom-control custom-checkbox">
                                            <input v-model="agree_policy" type="checkbox" class="custom-control-input" id="rememberme">
                                            <label class="custom-control-label" for="rememberme">I agree to the EDH terms and privacy policy.</label>
                                        </div>
                                    </div>
                                    <button type="submit" class="btn btn-primary btn-block">Sign up</button>
                                </form>
                            </div>
                        </div>
                        <!-- login form close -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Home",
    data() {
        return {
            showModal:false,
            errors: [],
            email: null,
            firstName: null,
            lastName: null,
            skill_1: false,
            skill_2: false,
            agree_policy: false
        }
    },
    methods: {
        checkForm: function (e) {
            this.errors = [];

            if (!this.firstName) {
                this.errors.push("First name required.");
            }
            if (!this.lastName) {
                this.errors.push("Last name required.");
            }
            if (!this.email) {
                this.errors.push('Email required.');
            } else if (!this.validEmail(this.email)) {
                this.errors.push('Valid email required.');
            }
            if (!this.skill_1 && !this.skill_2) {
                this.errors.push('Please select a skill!')
            }
            if (!this.agree_policy) {
                this.errors.push('Please select a agree to terms and policy.!')
            }
            if (!this.errors.length) {
                return true;
            }

            e.preventDefault();
            console.log(this.email, this.firstName, this.lastName, this.skill_1, this.skill_2, this.agree_policy)
        },
        validEmail: function (email) {
            var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(email);
        }
    }
}
</script>
 <style scoped>
 .modal-active{
	display:block;
}
 </style>
 