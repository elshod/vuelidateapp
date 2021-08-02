<template>
  <div id="app">
    <div class="container">
        <div>
          <label class="form-label">Email</label>
          <input type="email" class="form-control"
            :class="{'is-invalid':$v.email.$error,'is-valid':!$v.email.$error && $v.email.$dirty}"
            v-model='email'
            @blur='$v.email.$touch()' >
          <div class="invalid-feedback" v-show='!$v.email.required'>Iltimos maydonni to'ldiring</div>
          <div class="invalid-feedback" v-show='!$v.email.email'>Maydonga email formatidagi ma'lumot kiriting</div>
        </div>
        <div>
          <label class="form-label">Ism</label>
          <input type="text"
            class="form-control"
            v-model='name'
            @blur='$v.name.$touch()'
            :class="{'is-invalid':$v.name.$error,'is-valid':!$v.name.$error && $v.name.$dirty}">
          <div class="invalid-feedback" v-show='!$v.name.required'>Iltimos maydonni to'ldiring</div>
          <div class="invalid-feedback" v-show='!$v.name.minLength'>Maydon eng kamida 5 ta simvol yozilsin</div>
        </div>
        <button class="mt-3 btn btn-primary" type="submit" :class="{'disabled':$v.$invalid}">Jo'natish</button>
        <div class="d-none">{{$v}}</div>
    </div>
  </div>
</template>
<script>
import {required, email, minLength} from 'vuelidate/lib/validators'
export default {
  name: 'App',
  data() {
    return { 
      email:'', 
      name:'' }
  },
  validations: {
    email: {  
      required, 
      email 
    },
    name: {
      required,
      minLength: minLength(5)
    }
  }
}
</script>

<style>

</style>
