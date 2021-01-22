<template>
  <q-layout view="lHh Lpr lFf" style="font-size: 8pt">
    <q-header elevated>
      <q-toolbar class="bg-brand">
        <q-btn
          flat
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-input
          v-model="search"
          rounded
          standout="bg-white text-dark"
          label="Buscar"
          input-class="text-dark"
          dense
          bg-color="white"
          class="q-ma-xs col-xs-4 text-dark"
        >
          <template v-slot:prepend>
            <q-icon v-if="search === ''" name="search" class="cursor-pointer" color="black"/>
            <q-icon v-else name="close" class="cursor-pointer" color="black"/>
          </template>
        </q-input>

        <q-space />
        <q-avatar>
          <img src="~assets/charly-face.png">
        </q-avatar>
        <div style="display: flex;justify-content: center;align-items: center;margin-top: 0px; margin-left: 5px"><span style="display: inline-block; vertical-align: top;font-size: 9pt;" class="bg-brand">{{ user }}</span></div>
      </q-toolbar>

      <q-bar inset class="bg-grey-9" style="padding: 5px 2% 5px 2%;height: 40px">
        <div class="row full-width" style="display: flex;">
          <div class="col-auto">
            <q-btn size="10px" padding="0px 15px" outline color="grey-3" label="Crear nuevo encargo" icon-right="add" no-caps style="height: 30px;"/>
            <q-btn size="10px" padding="0px 15px" outline color="grey-3" label="Seleccionar Cliente" icon-right="mdi-database" no-caps class="q-ml-md" style="height: 30px;" />
          </div>
          <div class="col-md" style="display: flex;justify-content: center;align-items: center;margin-top: 0px;"><span style="font-size: 9pt">{{ title }}</span></div>
          </div>
          <div class="col-auto" style="margin-top: 0px;">
            <q-btn size="14px" padding="0px 15px" style="position: relative;float: right;height: 30px;" outline color="grey-3" label="Cerrar Sesion" no-caps class="q-ml-md"  />
          </div>
      </q-bar>
    </q-header>
    <q-footer elevated>
      <q-bar class="bg-brand">
        <img src="~assets/copyright.png">
        <q-space/>
        <q-icon name="ion-logo-facebook" size="xs" class="text-teal-5"/>
        <q-icon name="ion-logo-pinterest" size="xs" class="text-teal-5"/>
        <q-icon name="ion-logo-instagram" size="xs" class="text-teal-5"/>
        <q-icon name="ion-logo-twitter" size="xs" class="text-teal-5"/>
        <q-icon name="ion-logo-youtube" size="xs" class="text-teal-5"/>
        <q-icon name="ion-logo-linkedin" size="xs" class="text-teal-5"/>
      </q-bar>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-brand"
      :width="250"
    >
      <q-list align="center" dense>
        <img class="q-ma-md" src="~assets/example1.png"/>
        <q-item
          clickable
          v-for="(menu, index) of essentialLinks"
          :key="index"
        >
          <q-item-section avatar top>
            <q-avatar class="text-dark" size="md">
              <q-icon v-if="!menu.noAssets" size="md">
                <img :src="menu.icon" />
              </q-icon>
              <q-icon v-else color="grey-4" size="sm" :name="menu.icon"/>
            </q-avatar>
          </q-item-section>
          <q-item-section>
            <q-item-label class="text-left text-grey-4">{{ menu.title }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

const linksData = [
  {
    title: 'Home',
    icon: require('../assets/example2.png')
  },
  {
    title: 'VIIA Diseño',
    icon: require('../assets/example3.png')
  },
  {
    title: 'VIIA Movilida',
    icon: require('../assets/example4.png')
  },
  {
    title: 'VIIA Nativo',
    icon: require('../assets/example5.png')
  },
  {
    title: 'VIIA Moduliar',
    icon: require('../assets/example6.png')
  },
  {
    title: 'VIIA Sur',
    icon: require('../assets/example7.png')
  },
  {
    title: 'VIIA Inventor',
    icon: require('../assets/example8.png')
  },
  {
    title: 'Perfil de Usuario',
    icon: 'folder',
    noAssets: true
  },
  {
    title: 'Contratos',
    icon: 'close',
    noAssets: true
  },
  {
    title: 'Estados de Pago',
    icon: 'close',
    noAssets: true
  },
  {
    title: 'Encargo',
    icon: 'add',
    noAssets: true
  },
  {
    title: 'Planificacion & Requerimientos',
    icon: 'mdi-database',
    noAssets: true
  },
  {
    title: 'Networking',
    icon: 'emoji_objects',
    noAssets: true
  },
  {
    title: 'Cerrar Sesion',
    icon: 'close',
    noAssets: true
  }
]

export default {
  name: 'MainLayout',
  data () {
    return {
      search: '',
      title: 'Administrador Cuenta Cliente',
      user: 'Benito Reyes',
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
<style lang="stylus">
.bg-brand {
  background: #363536;
}
.bg-second {
  background: #363535;
}
</style>
