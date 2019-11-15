<template>
  <q-page class="flex justify-center q-my-xl q-py-xl">
    <div class="column">
      <div class="row justify-center q-ma-xs text-h2 text-weight-medium" >MicroIoT物联网平台</div>
      <div class="row justify-center q-ma-xs text-h6">软件定义物联网，极速构建你的物联网产品。</div>
      <div class="row justify-center q-gutter-sm">
        <q-input dense class="q-my-xl" outlined v-model="email" label="您的电子邮件" style="width: 300px"/>
        <q-btn class="q-my-xl" color="primary" @click="register">免费使用</q-btn>
      </div>
      <div class="row " >
        <div class="row justify-center col-xs-12 col-sm-6 col-md-4">
          <q-card flat class="q-ma-md "   style="height: 270px; max-width: 400px">
            <q-card-section class="row items-center">
              <q-icon class="text-primary" size="xl" name="devices_other"></q-icon>
              <div class="text-h5 q-ml-md">软件定义物联网</div>
            </q-card-section>
            <q-separator inset color="primary"/>
            <q-card-section>
              <div class="text-body1">从应用角度对物联网感知层硬件设施进行抽象，促进物联网虚拟化，利用软件配置和管理物联网元数据信息，并向上层提供统一的管理和编程接口，以平台为基础开发物联网产品，利用最新的软件技术，提供物联网产品的管理性，灵活性和横向扩展性。</div>
            </q-card-section>
          </q-card>
        </div>
        <div class="row justify-center col-xs-12 col-sm-6 col-md-4">
          <q-card flat class="q-ma-md "  style="height: 270px; max-width: 400px">
            <q-card-section class="row items-center no-wrap">
              <q-icon class="text-primary" size="xl" name="compare"></q-icon>
              <div class="text-h5 q-ml-md">分离基础设施和应用</div>
            </q-card-section>
            <q-separator inset color="primary"/>
            <q-card-section>
              <div class="text-body1">逻辑上集中管理物联网设备，将物联网基础设施和应用分离，屏蔽底层物联网硬件细节差异，从之前与特定的硬件的紧耦合，到现在使用通用的计算设备，使用户拥有前所未有的可编程能力、自动化和管理能力。</div>
            </q-card-section>
          </q-card>
        </div>
        <div class="row justify-center col-xs-12 col-sm-6 col-md-4">
          <q-card flat class="q-ma-md "  style="height: 270px; max-width: 400px">
            <q-card-section class="row items-center">
              <q-icon class="text-primary" size="xl" name="directions_run"></q-icon>
              <div class="text-h5 q-ml-md">加快产品上市速度</div>
            </q-card-section>
            <q-separator inset color="primary"/>
            <q-card-section>
              <div class="text-body1">MicroIoT物联网平台可以监视，控制任意类型的“物”，物联网应用与“物”之间、或者“物”与“物”之间的通信可以通过MicroIoT提供的API实现，从而可以构建一个高可扩展性且足够灵活的系统，以适应不断变化的商业需求，加快物联网产品上市速度。</div>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </div>
    <div class="q-mt-xl " style="width: 100vw;">
      <q-separator></q-separator>
      <div class="row justify-center q-mt-md">
        <img src="statics/icons/favicon-96x96.png" width="64"/>
      </div>
      <div class="row justify-center">
        <div>MicroIoT is developed and maintained by <a href="https://www.github.com/caoxinyu">caoxinyu</a></div>
      </div>
      <div class="row justify-center">
        <div >© Copyright 2019 All Rights Reserved.</div>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      email: ''
    }
  },
  methods: {
    register () {
      if (this.email.length > 0) {
        window.location.href = '/studio/#/register/' + this.email
      } else {
        window.location.href = '/studio/#/register'
      }
    }
  }
}
</script>
