<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="flex justify-center bg-primary text-white ">
      <q-toolbar style="width: 1200px;" >

        <q-toolbar-title @click="home"  class="cursor-pointer">
          <q-avatar>
            <img src="statics/icons/favicon-96x96.png"/>
          </q-avatar>
          MicroIoT
        </q-toolbar-title>

        <q-btn no-caps flat type="a" href="https://www.github.com/MicroIoT">
          GitHub
        </q-btn>
        <q-btn no-caps flat type="a" href="https://hub.docker.com/u/microiot">
          Docker
        </q-btn>
        <q-btn no-caps flat label="文档" type="a" href="/site/index.html"/>
        <q-btn flat type="a" href="https://www.microiot.top/studio">登录</q-btn>
        <q-btn outline color="white" type="a" href="https://www.microiot.top/studio/#/register">注册</q-btn>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MyLayout',

  data () {
    return {
      leftDrawerOpen: false
    }
  },
  methods: {
    home () {
      this.$router.push({ path: '/' })
    }
  }
}
</script>
