<template>
  <TheCard image-name="reg_form_img.png">
      <AppForm @submit="submitForm" >
        <h3>RECORDUM</h3>
        <h1 style="margin: 40px 0">Авторизация</h1>

        <InputRows>
          <div class="input-row">
            <AppInput
              v-model="form.email"
              :type="`text`"
              :name="`email`"
              :rules="`required|email`"
              :placeholder="`Email`"
            >
            </AppInput>
          </div>

          <div class="input-row">
            <AppInput
              v-model="form.password"
              :type="`password`"
              :name="`password`"
              :rules="`required`"
              :placeholder="`Пароль`"
            >
            </AppInput>
          </div>
        </InputRows>

        <AppPrimaryBtn style="margin-top: 30px" type="submit">
          Войти
        </AppPrimaryBtn>

        <p style="text-align: center; margin-top: 40px">
          Нет аккаунта?
          <router-link class="colored-link" to="/register"
          >Зарегистрируйтесь</router-link
          >
        </p>
      </AppForm>
  </TheCard>

</template>

<script>
import { useStore } from 'vuex'
import AppInput from '@/components/UI/AppInput.vue'
import AppPrimaryBtn from '@/components/UI/AppPrimaryButton.vue'
import AppForm from '@/components/AppForm.vue'
import InputRows from '@/components/UI/InputRows.vue'
import TheCard from '@/components/TheCard.vue'

export default {
  components: {
    TheCard,
    InputRows,
    AppForm,
    AppPrimaryBtn,
    AppInput
  },
  setup () {
    const store = useStore()

    const form = {
      email: '',
      password: ''
    }

    const submitForm = () => {
      const payload = {
        email: form.email,
        password: form.password
      }
      store.dispatch('auth/login', payload)
    }

    return {
      form,
      submitForm
    }
  }
}
</script>

<style scoped lang="less">
form {
  width: 400px;
}
</style>
