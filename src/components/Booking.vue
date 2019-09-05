<template>
  <div class="booking">
    <h1>预约取件</h1>

    <a-form :form="form" @submit="handleSubmit">
      <a-form-item label="运单号" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-input
          v-decorator="[
          'waybillNum',
          {rules: [{ required: true, message: '请输入运单号!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="取件日期" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-date-picker @change="onChange" size="large" v-decorator="[
          'appointmentTime',
          {rules: [{ required: true, message: '请输入取件日期!' }]}
        ]"/>
      </a-form-item>
      <a-form-item label="取件时间" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-time-picker @change="onChange" :defaultOpenValue="moment('00:00:00', 'HH:mm:ss')" />
      </a-form-item>

      <a-form-item :wrapper-col="{ span: 15, offset: 5 }">
        <a-button type="primary" html-type="submit">Submit</a-button>
      </a-form-item>
    </a-form>
  </div>
</template>

<script>
import axios from "axios";
import moment from 'moment';

export default {
  name: "Booking",
  props: {},

  data() {
    return {
      formLayout: "horizontal",
      form: this.$form.createForm(this)
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log("Received values of form: ", values);
        //   axios
        //     .post("http://localhost:8080/percel", values)
        //     .then(function(response) {
        //       console.log(response);
        //     })
        //     .catch(function(error) {
        //       console.log(error);
        //     });
        }
      });
    },
    moment,
    onChange(date, dateString) {
      console.log(date, dateString);
    }
  }
};
</script>

<style>
.booking {
  width: 500px;
  margin: 20px auto;
}
</style>
