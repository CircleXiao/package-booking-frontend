<template>
  <div class="package-put-in">
    <h1>包裹入库</h1>

    <a-form :form="form" @submit="handleSubmit">
      <a-form-item label="运单号" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-input
          v-decorator="[
          'note',
          {rules: [{ required: true, message: '请输入运单号!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="收件人" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-input
          v-decorator="[
          'note',
          {rules: [{ required: true, message: '请输入收件人姓名!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="电话" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-input
          v-decorator="[
          'note',
          {rules: [{ required: true, message: '请输入收件人联系电话!' }]}
        ]"
        />
      </a-form-item>
      <a-form-item label="重量" :label-col="{ span: 6 }" :wrapper-col="{ span: 14 }">
        <a-input
          v-decorator="[
          'note',
          {rules: [{ required: true, message: '请输入包裹重量!' }]}
        ]"
        />
      </a-form-item>

      <a-form-item :wrapper-col="{ span: 15, offset: 5 }">
        <a-button type="primary" html-type="submit">Submit</a-button>
      </a-form-item>
    </a-form>
  </div>
</template>

<script>
export default {
  name: "PackagePutIn",
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
        }
      });
    },
    handleSelectChange(value) {
      console.log(value);
      this.form.setFieldsValue({
        note: `Hi, ${value === "male" ? "man" : "lady"}!`
      });
    }
  }
};
</script>

<style>
.package-put-in {
  width: 500px;
  margin: 20px auto;
}
</style>
