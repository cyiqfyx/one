<template>
  <section class="content">
    <div class="box box-primary">
      <div class="box-header">
        <h3 class="box-title">字典信息</h3>
      </div>
      <div class="box-body">
        <form class="form-horizontal">
          <div class="row">
            <div class="col-md-6">
              <FormGroup label="字典类别" :required="true">
                <input type="text" class="form-control" v-model="obj.type" v-validate="'required'" name="字典类别" maxlength="100"/>
              </FormGroup>
            </div>
          </div>
          <div class="row">
            <div class="col-md-6">
              <FormGroup label="字典名称" :required="true">
                <input type="text" class="form-control" v-model="obj.name" v-validate="'required'" name="字典名称" maxlength="100" />
              </FormGroup>
            </div>
          </div>
          <div class="row">
            <div class="col-md-6">
              <FormGroup label="字典描述">
                <textarea class="form-control" rows="3" v-model="obj.remark" maxlength="200"></textarea>
              </FormGroup>
            </div>
          </div>
        </form>
      </div>
      <div class="box-footer">
        <div class="row">
          <div class="col-md-2 col-md-offset-2">
            <a class="btn btn-block btn-primary" @click="validAndSave()">保存</a>
          </div>
          <div class="col-md-2">
            <a class="btn btn-block btn-default" @click="$router.go(-1)">返回</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import FormMixin from '@mixins/FormMixin'

export default {
  mixins: [FormMixin],
  data: function () {
    return {
      form: {
        actions: {
          get: this.$api.system.getDict,
          save: this.$api.system.saveDict,
          update: this.$api.system.updateDict
        },
        continue: true
      },
      obj: {
        type: '',
        name: '',
        remark: ''
      }
    }
  }
}
</script>
