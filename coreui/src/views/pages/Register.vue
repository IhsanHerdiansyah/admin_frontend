<template>
  <div class="d-flex align-items-center min-vh-100">
    <CContainer fluid>
      <CRow class="justify-content-center">
        <CCol md="6">
          <CCard class="mx-4 mb-0">
            <CCardBody class="p-4">
              <CForm @submit.prevent="register" method="POST">
                <h1>Forgot Password</h1>
                <p class="text-muted">Enter your email adress below to reset passsword</p>
                <CInput
                  placeholder="Email"
                  prepend="@"
                  autocomplete="email"
                  v-model="email"
                />
                <CButton type="submit" color="success" block>Reset Password</CButton>
              </CForm>
            </CCardBody>
          </CCard>
        </CCol>
      </CRow>
    </CContainer>
  </div>
</template>

  <script>
    import axios from 'axios'
    export default {
      data() {
        return {
          name: '',
          email: '',
          password: '',
          password_confirmation: ''
        }
      },    
      methods: {
        register() {
          var self = this;
          axios.post(  this.$apiAdress + '/api/register', {
            name: self.name,
            email: self.email,
            password: self.password,
            password_confirmation: self.password_confirmation
          }).then(function (response) {
            self.name = '';
            self.email = '';
            self.password = '';
            self.password_confirmation = '';
            console.log(response);
            self.$router.push({ path: '/login' });
          })
          .catch(function (error) {
            console.log(error);
          });
  
        }
      }
    }
  
  </script>
