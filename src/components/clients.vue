<template>
  <form class="create" @submit.prevent="submitForm">
  <div class='form'>
    <div class="form-block">
      <div class="form-group">
        <label for="surname" class="form-group__label">Фамилия:</label>
        <input id="surname" class="form-group__input" type="text" v-model.trim="form.surname"
          :class="$v.form.surname.$error ? 'error' : ''" 
        >
        <p v-if='$v.form.surname.$dirty && !$v.form.surname.required' class='error_feedback'>Введите фамилию</p>
        <p v-else>Обязательное поле</p>
      </div>

      <div class="form-group">
        <label for="name" class="form-group__label">Имя:</label>
        <input id="name" class="form-group__input" type="text" v-model.trim="form.name"
        :class="$v.form.name.$error ? 'error' : ''" 
        >
        <p v-if='$v.form.name.$dirty && !$v.form.name.required' class='error_feedback'>Введите имя</p>
        <p v-else>Обязательное поле</p>
      </div>

      <div class="form-group">
        <label for="middlename " class="form-group__label">Отчество:</label>
        <input id="middlename " class="form-group__input" type="text" v-model.trim="form.middlename">
      </div> 

      <div class="form-group">
        <label for="bdate" class="form-group__label">Дата рождения:</label>
        <input id="bdate" class="form-group__input" type="date" v-model.trim="form.bdate"
        :class="$v.form.bdate.$error ? 'error' : ''" 
        >
        <p v-if='$v.form.bdate.$dirty && !$v.form.bdate.required' class='error_feedback'>Введите дату рождения</p>
        <p v-else>Обязательное поле</p>
      </div>
      
      <div class="form-group">
        <label for="tel" class="form-group__label">Номер телефона:</label>
        <input id="tel" class="form-group__input" inputmode="tel" v-model.trim="form.tel"
        :class="$v.form.tel.$error ? 'error' : ''" placeholder="79992751237">
        <p v-if='$v.form.tel.$dirty && !$v.form.tel.required' class='invalid-feedback'>Введите номер телефона</p>
        <p v-else-if='$v.form.tel.$dirty && !$v.form.tel.numeric' class='invalid-feedback'>Должен содержать только цифры</p>
        <p v-else-if='$v.form.tel.$dirty && !$v.form.tel.minLength' class='invalid-feedback'>Должен содержать 11 цифр</p>
        <p v-else-if='$v.form.tel.$dirty && !$v.form.tel.validFormat' class='invalid-feedback'>Номер должен начинаться с 7</p>
        <p v-else>Обязательное поле</p>
      </div> 

      <div class="form-group">
        <input name='gender' id='male' value='male' v-model='form.gender' class="form-group__input_radio" type="radio">
        <label for="male" class="form-group__label_radio" checked>Мужчина</label>
        
        <input name='gender' id='female' value='female' v-model='form.gender' class="form-group__input_radio" type="radio">
        <label for="female" class="form-group__label_radio">Женщина</label>
      </div>
      
      <div class="form-group">
        <label for="clients" class="form-group__label">Группа клиентов:</label>
        <select id="clients" class="form-group__input_select" multiple size="3" v-model='form.client'
          :class="$v.form.client.$error ? 'error' : ''" 
        >
          <option v-for="(client, index) in clients" 
            :value="client.value"
            :key='index'>
            {{ client.label }}
            </option>
        </select>
        <p v-if='$v.form.client.$dirty && !$v.form.client.required' class='error_feedback'>Выберите группу(ы) клиента</p>
        <p v-else>Обязательное поле</p>
      </div>

      <div class="form-group">
        <label for="doctor" class="form-group__label">Лечащий врач:</label>
        <select id="doctor" class="form-group__input_select" v-model='form.doctor'>
          <option v-for="(doctor, index) in doctors" 
            :value="doctor.value"
            :key='index'>
            {{ doctor.label }}
          </option>
        </select>
      </div>

      <div class="form-group">
        <input id='sms' class="form-group__input__checkbox" type="checkbox" v-model='form.smsDisagree'>
        <label for="sms" class="form-group__label_checkbox">Не отправлять СМС</label>
      </div>
    </div>

    <div class="form-block">
      <div class="form-group">
        <label for="index" class="form-group__label">Индекс:</label>
        <input id="index" class="form-group__input" inputmode="numeric" v-model.trim="address.index">
      </div> 

      <div class="form-group">
        <label for="country" class="form-group__label">Страна:</label>
        <input id="country" class="form-group__input" v-model.trim="address.country">
      </div> 

      <div class="form-group">
        <label for="region" class="form-group__label">Область:</label>
        <input id="region" class="form-group__input" v-model.trim="address.region">
      </div> 

      <div class="form-group">
        <label for="city" class="form-group__label">Город:</label>
        <input id="city" class="form-group__input" v-model.trim="address.city"
        :class="$v.address.city.$error ? 'error' : ''" 
        >
        <p v-if='$v.address.city.$dirty && !$v.address.city.required' class='error_feedback'>Введите город</p>
        <p v-else>Обязательное поле</p>
      </div> 

      <div class="form-group">
        <label for="street" class="form-group__label">Улица:</label>
        <textarea id="street" class="form-group__input_textarea" v-model.trim="address.street"></textarea>
      </div> 

      <div class="form-group">
        <label for="home" class="form-group__label">Дом:</label>
        <input id="home" class="form-group__input" v-model.trim="address.home">
      </div> 
    </div>

    <div class="form-block">
      <div class="form-group">
        <label for="doc" class="form-group__label">Тип документа:</label>
        <select id="doc" class="form-group__input_select" size="1" v-model='pass.doc'>
          <option v-for="(doc, index) in docs" 
            :value="doc.value"
            :key='index'>
            {{ doc.label }}
            </option>
        </select>
        <p>Обязательное поле</p>
      </div>

      <div class="form-group">
        <label for="series" class="form-group__label">Серия:</label>
        <input id="series" class="form-group__input" inputmode="numeric" v-model.trim="pass.series">
      </div>

      <div class="form-group">
        <label for="number" class="form-group__label">Номер:</label>
        <input id="nubmer" class="form-group__input" inputmode="numeric" v-model.trim="pass.number">
      </div>


      <div class="form-group">
        <label for="issued" class="form-group__label">Кем выдан:</label>
        <textarea id="issued" class="form-group__input_textarea" v-model.trim="pass.issued"></textarea>
      </div> 

      <div class="form-group">
        <label for="passdate" class="form-group__label">Дата выдачи:</label>
        <input id="passdate" class="form-group__input" type='date' v-model.trim="pass.passdate"
        :class="$v.pass.passdate.$error ? 'error' : ''" 
        >
        <p v-if='$v.pass.passdate.$dirty && !$v.pass.passdate.required' class='error_feedback'>Введите дату выдачи</p>
        <p v-else>Обязательное поле</p>
      </div> 
    </div>
  </div>
    <button type="submit" class="btn">Создать</button>
  </form>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, minLength, numeric } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  name: 'ClientForm',
  data() {
    return {
      form: {
        surname: '',
        name: '',
        middlename: '',
        bdate: '',
        tel: '',
        gender: 'male',
        doctor: 'Ivanov',
        client: [],
        smsDisagree: false,
      },
      address: {
        index: '',
        country: '',
        region: '',
        city: '',
        street: '',
        home: '',
      },
      pass: {
        doc: 'Passport',
        series: '',
        number: '',
        issued: '',
        passdate: '',
      },
      doctors: [
        {
          label: 'Иванов',
          value: 'Ivanov'
        },
        {
          label: 'Захаров',
          value: 'Zakharov'
        },
        {
          label: 'Чернышева',
          value: 'Chernysheva'
        }
      ],
      docs: [
        {
          label: 'Паспорт',
          value: 'Passport'
        },
        {
          label: 'Свидетельство о рождении',
          value: 'Birth certificate '
        },
        {
          label: 'Вод. удостоверение',
          value: 'Drivers license'
        },
      ],
      clients: [
        {
          label: 'VIP',
          value: 'VIP'
        },
        {
          label: 'Проблемные',
          value: 'Problem'
        },
        {
          label: 'ОМС',
          value: 'OMC'
        }
      ]
    }
  },
  validations: {
    form: {
      surname: { required },
      name: { required },
      bdate: { required },
      tel: { required, numeric, validFormat: val => /^[7][0-9]{10}$/.test(val), minLength: minLength(11) },
      client: { required },
    },
    address: {
      city: { required },
    },
    pass: {
      doc: { required },
      passdate: { required },
    },
  },
  methods: {
    submitForm() {
      this.$v.form.$touch()
      this.$v.address.$touch()
      this.$v.pass.$touch()
      if (!this.$v.form.$error) {
        alert('Клиент создан!');
        location.reload();
      }
    }
  }
}
</script>