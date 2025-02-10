<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div style="width: 100%;">
      <SearchForm :fields="fields" />
    </div>
  </div>
</template>
<script>
import SearchForm from "@/components/SearchForm";
export default {
  components: {
    SearchForm,
  },
  data() {
    return {
      fields: [
        {
          key: "rule",
          label: "规则名称",
          component: "input",
          componentProps: {
            placeholder: "请输入规则名称",
            maxlength: 30,
          },
          componentEvents: {
            change(value) {
              //规则的change事件
              console.log(value,'修改了');
              
            },
          },
        },
        {
          key: "type",
          label: "规则名称",
          component: "select",
          componentProps: {
            placeholder: "请选择类型",
            options: [
              { label: "类型1", value: "type1" },
              { label: "类型2", value: "type2" },
            ],
          },
          componentEvents: {
            change(value) {
              //规则的change事件
              console.log(value,'修改了');
              
            },
          },
        },
      ],
    };
  },
};
</script>
