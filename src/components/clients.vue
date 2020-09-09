<template>
  <form class="create">
  <div class='form'>
    <div class="form-block">
      <div class="form-group">
        <label for="surname" class="form-group__label">Фамилия:</label>
        <input id="surname" class="form-group__input" type="text" v-model.trim="surname">
      </div>

      <div class="form-group">
        <label for="name" class="form-group__label">Имя:</label>
        <input id="name" class="form-group__input" type="text" v-model.trim="name">
      </div>

      <div class="form-group">
        <label for="middlename " class="form-group__label">Отчество:</label>
        <input id="middlename " class="form-group__input" type="text" v-model.trim="middlename">
      </div> 

      <div class="form-group">
        <label for="bdate" class="form-group__label">Дата рождения:</label>
        <input id="bdate" class="form-group__input" type="date" v-model.trim="bdate">
      </div>
      
      <div class="form-group">
        <label for="tel" class="form-group__label">Номер телефона:</label>
        <input id="tel" class="form-group__input" inputmode="tel" v-model.trim="tel">
      </div> 

      <div class="form-group">
        <input name='sex' id='male' class="form-group__input_radio" type="radio">
        <label for="male" class="form-group__label_radio" checked>Мужчина</label>
        
        <input name='sex' id='female' class="form-group__input_radio" type="radio">
        <label for="female" class="form-group__label_radio">Женщина</label>
      </div>
      
      <div class="form-group">
        <label for="clients" class="form-group__label">Группа клиентов:</label>
        <select id="clients" class="form-group__input_select" multiple size="3">
          <option>VIP</option>
          <option>Проблемные</option>
          <option>ОМС</option>
        </select>
      </div>

      <div class="form-group">
        <label for="doctor" class="form-group__label">Лечащий врач:</label>
        <select id="doctor" class="form-group__input_select" v-model='doctor'>
          <option v-for="(doctor, index) in doctors" 
            :value="doctor.value"
            :key='index'>
            {{ doctor.label }}
          </option>
        </select>
      </div>

      <div class="form-group">
        <input id='sms' class="form-group__input__checkbox" type="checkbox">
        <label for="sms" class="form-group__label_checkbox">Не отправлять СМС</label>
      </div>
    </div>

    <div class="form-block">
      <div class="form-group">
        <label for="index" class="form-group__label">Индекс:</label>
        <input id="index" class="form-group__input" inputmode="numeric" v-model.trim="index">
      </div> 

      <div class="form-group">
        <label for="country" class="form-group__label">Страна:</label>
        <input id="country" class="form-group__input" v-model.trim="country">
      </div> 

      <div class="form-group">
        <label for="region" class="form-group__label">Область:</label>
        <input id="region" class="form-group__input" v-model.trim="region">
      </div> 

      <div class="form-group">
        <label for="city" class="form-group__label">Город:</label>
        <input id="city" class="form-group__input" v-model.trim="city">
      </div> 

      <div class="form-group">
        <label for="street" class="form-group__label">Улица:</label>
        <textarea id="street" class="form-group__input_textarea" v-model.trim="street"></textarea>
      </div> 

      <div class="form-group">
        <label for="home" class="form-group__label">Дом:</label>
        <input id="home" class="form-group__input" v-model.trim="home">
      </div> 
    </div>

    <div class="form-block">
      <div class="form-group">
        <label for="doc" class="form-group__label">Тип документа:</label>
        <select id="doc" class="form-group__input_select" size="1" v-model='doc'>
          <option v-for="(doc, index) in docs" 
            :value="doc.value"
            :key='index'>
            {{ doc.label }}
            </option>
        </select>
      </div>

      <div class="form-group">
        <label for="series" class="form-group__label">Серия:</label>
        <input id="series" class="form-group__input" inputmode="numeric" v-model.trim="series">
      </div>

      <div class="form-group">
        <label for="number" class="form-group__label">Номер:</label>
        <input id="nubmer" class="form-group__input" inputmode="numeric" v-model.trim="number">
      </div>


      <div class="form-group">
        <label for="issued" class="form-group__label">Кем выдан:</label>
        <textarea id="issued" class="form-group__input_textarea" v-model.trim="issued"></textarea>
      </div> 

      <div class="form-group">
        <label for="passdate" class="form-group__label">Дата выдачи:</label>
        <input id="passdate" class="form-group__input" type='date' v-model.trim="passdate">
      </div> 
    </div>
  </div>
    <button type="submit" class="btn" @click="show()">Создать</button>
  </form>
</template>

<script>
export default {
  name: 'ClientForm',
  data() {
    return {
      surname: '',
      name: '',
      middlename: '',
      tel: '',
      index: '',
      country: '',
      region: '',
      city: '',
      street: '',
      home: '',
      series: '',
      number: '',
      issued: '',
      doctor: 'Ivanov',
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
      doc: 'Passport',
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
      ]
    }
  }
}
</script>