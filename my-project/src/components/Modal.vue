<template>
    <div class="modal modal-active" id="loginmodal" tabindex="-1" role="dialog" aria-labelledby="loginmodalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-body">
                    <button type="button" @click="$emit('close')" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                    <!-- login form start -->
                    <div class="login-form border-0">
                        <div class="login-form-body">
                            <h4 class="login-form-title">Login</h4>
                            <form>
                                <div class="form-group">
                                    <label for="email">Email</label>
                                    <input type="email" class="form-control" id="email" aria-describedby="email" placeholder="example@gmail.com" required="">
                                </div>
                                <div class="form-group">
                                    <label id="password">Password</label>
                                    <input id="password-field" type="password" class="form-control" name="password" value="" placeholder="*************">
                                    <span toggle="#password-field" class="fa fa-fw fa-eye password-hide-icon showhidepassword"></span>
                                    <small>Must be 8-20 characters long.</small>
                                </div>
                                <button type="submit" class="btn btn-primary btn-block">Login</button>
                            </form>
                            <div class="login-remember-password-block">
                                <div class="custom-control custom-checkbox">
                                    <input type="checkbox" class="custom-control-input" id="rememberme">
                                    <label class="custom-control-label" for="rememberme">Remember Me</label>
                                </div>
                                <div class="forgot-password-link">
                                    <a href="forget-password-page.html"> Forgot Password?</a>
                                </div>
                            </div>
                        </div>
                        <div class="login-form-footer">
                            <p class="login-form-footer-text">Don’t have a Spacely account? <a href="register-page.html">Create Account</a> and we’ll set you up so you can list your space.</p>
                        </div>
                    </div>
                    <!-- login form close -->
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    props:['name'],
    data() {
        return {

        }
    }
}
</script>
 
<style scoped>
.modal-active{
	display:block;
}
</style>
