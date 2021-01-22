<template>
  <q-page style="padding: 15px 20px 5px 20px; background: rgb(10,159,178);background: linear-gradient(180deg, rgba(10,159,178,1) 0%, rgba(8,174,195,1) 23%, rgba(0,229,255,1) 100%);">
    <div style="width: 100%">
      <q-card style="background-color: inherit" class="q-pt-none q-pb-xs" flat>
        <q-card-section horizontal class="q-pb-none">
          <q-item style="padding: 0px">
            <q-item-section avatar class="justify-end q-pt-xs">
              <q-btn class="q-mr-none q-ml-md" style="border: solid 2px;color: #888384" round outline dense size="25px" icon="person"/>
            </q-item-section>
          </q-item>
          <q-card-section class="q-pt-md q-pl-none">
            <div style="color: #344151">
              <span>{{form.proyect}}</span>
              <br/>
              <span>{{form.id}}</span>
              <br/>
              <span>{{form.address}}</span>
            </div>
          </q-card-section>
          <q-separator vertical/>
          <q-card-section class="q-pt-md q-pl-md">
            <div style="color: #344151">
              <span>{{form.description}}</span>
              <br/>
              <span>Fecha Inicio: {{form.dateIn}}</span>
              <br/>
              <span>Fecha Termino: {{form.dateOut}}</span>
            </div>
          </q-card-section>
          <q-separator vertical/>
          <q-card-section class="q-pt-md q-pl-md">
            <div style="color: #344151">
              <span>Superficie: {{form.area}}</span>
              <br/>
              <span>Encargado Proyecto: {{form.boss}}</span>
              <br/>
              <span>Presupuesto Estimado: {{form.value}}</span>
              <br/>
              <span>{{form.company}}</span>
            </div>
          </q-card-section>
          <q-card-section class="q-ml-xl justify-center">
            <img class="col-1" style="height: 60px" src="~assets/VIIA SUR.png" />
            <img class="col-1" style="height: 60px" src="~assets/v1.jpeg" />
            <img class="col-1" style="height: 60px" src="~assets/VIIA SUR.png" />
            <img class="col-1" style="height: 60px" src="~assets/v1.jpeg" />
            <img class="col-1" style="height: 60px" src="~assets/VIIA SUR.png" />
            <img class="col-1" style="height: 60px" src="~assets/v1.jpeg" />
          </q-card-section>

        </q-card-section >
      </q-card>
    </div>
    <div class="row justify-center example-container full-width">
      <div class="example-cel col-md-2" v-for="(button, index) in buttons" :key="index" tabindex="0">
        <q-btn class="q-mx-xs" size="10px" :text-color="button.color" padding="0px 0px" no-caps style="background-color: #455264; height: 25px; max-width: 100%; min-width: 140px; width: 95%" :label="button.text" @click="changeColor(index)"/>
      </div>
    </div>
    <hr style="border: 1px dashed #455264" class="q-mt-sm"/>
    <div class="full-width">
      <q-card>
        <q-bar style="background-color: #455264;" class="justify-center"><span style="font-size: 10pt" class="text-grey-3">{{ panel.description }}</span></q-bar>
        <q-card-section horizontal class="q-py-sm">
          <div class="row justify-evenly full-width">
            <div class="col q-pa-xs">
              <q-bar style="background-color: #455264;" class="justify-center"><span style="font-size: 10pt" class="text-grey-3">{{ panel.team.title }}</span></q-bar>
              <q-card>
                <q-scroll-area style="height: 265px">
                  <q-list bordered class="bg-light-blue-1">
                    <q-item v-for="contact in contacts" :key="contact.id" class="q-my-md bg-white q-mx-sm" clickable v-ripple>
                      <q-item-section avatar class="q-pt-xs">
                        <q-btn class="q-ma-none" style="border: solid 2px;color: #888384" round outline dense size="md" icon="person"/>
                      </q-item-section>

                      <q-item-section>
                        <q-item-label style="word-wrap: break-word;">{{ contact.name }}</q-item-label>
                      </q-item-section>

                      <q-item-section side>
                        <div class="row items-center">
                          <q-btn text-color="grey-3" style="background-color: #888384; height: 25px; widht: 30px; font-size: 8pt; display: flex; justify-content: center; align-items: center;" label="Ficha" no-caps/>
                          <q-checkbox v-model="contact.val" />
                        </div>
                      </q-item-section>

                    </q-item>
                  </q-list>
                </q-scroll-area>
              </q-card>
            </div>
            <div class="col q-pa-xs">
              <q-bar style="background-color: #455264;" class="justify-center"><span style="font-size: 10pt" class="text-grey-3">{{ panel.team.title }}</span></q-bar>
              <q-card>
                <q-scroll-area style="height: 265px">
                  <q-list bordered class="bg-light-blue-1">
                    <q-item v-for="contact in contacts" :key="contact.id" class="q-my-md bg-white q-mx-sm" clickable v-ripple>
                      <q-item-section avatar class="q-pt-xs">
                        <q-btn class="q-ma-none" style="border: solid 2px;color: #888384" round outline dense size="md" icon="person"/>
                      </q-item-section>

                      <q-item-section>
                        <q-item-label style="word-wrap: break-word;">{{ contact.name }}</q-item-label>
                      </q-item-section>

                      <q-item-section side>
                        <div class="row items-center">
                          <q-btn text-color="grey-3" style="background-color: #888384; height: 25px; widht: 30px; font-size: 8pt; display: flex; justify-content: center; align-items: center;" label="Ficha" no-caps/>
                          <q-checkbox v-model="contact.val" />
                        </div>
                      </q-item-section>

                    </q-item>
                  </q-list>
                </q-scroll-area>
              </q-card>
            </div>
            <div class="col q-pa-xs">
              <q-bar style="background-color: #455264;" class="justify-center"><span style="font-size: 10pt" class="text-grey-3">{{ panel.team.title }}</span></q-bar>
              <q-card>
                <q-scroll-area style="height: 265px">
                  <q-list bordered class="bg-light-blue-1">
                    <q-item v-for="contact in contacts" :key="contact.id" class="q-my-md bg-white q-mx-sm" clickable v-ripple>
                      <q-item-section avatar class="q-pt-xs">
                        <q-btn class="q-ma-none" style="border: solid 2px;color: #888384" round outline dense size="md" icon="person"/>
                      </q-item-section>

                      <q-item-section>
                        <q-item-label style="word-wrap: break-word;">{{ contact.name }}</q-item-label>
                      </q-item-section>

                      <q-item-section side>
                        <div class="row items-center">
                          <q-btn text-color="grey-3" style="background-color: #888384; height: 25px; widht: 30px; font-size: 8pt; display: flex; justify-content: center; align-items: center;" label="Ficha" no-caps/>
                          <q-checkbox v-model="contact.val" />
                        </div>
                      </q-item-section>

                    </q-item>
                  </q-list>
                </q-scroll-area>
              </q-card>
            </div>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
const contacts = [
  {
    id: 1,
    name: 'Ruddy Jedrzej',
    email: 'rjedrzej0@discuz.net',
    val: false
  },
  {
    id: 2,
    name: 'Mallorie Alessandrini',
    email: 'malessandrini1@marketwatch.com',
    val: false
  },
  {
    id: 3,
    name: 'Elisabetta Wicklen',
    email: 'ewicklen2@microsoft.com',
    val: false
  },
  {
    id: 4,
    name: 'Seka Fawdrey',
    email: 'sfawdrey3@wired.com',
    val: false
  }
]

const offline = [
  {
    id: 5,
    name: 'Brunhilde Panswick',
    email: 'bpanswick4@csmonitor.com',
    avatar: 'avatar2.jpg'
  }, {
    id: 6,
    name: 'Winfield Stapforth',
    email: 'wstapforth5@pcworld.com',
    avatar: 'avatar6.jpg'
  }
]

export default {
  name: 'PageIndex',
  data () {
    return {
      val: false,
      contacts,
      offline,
      buttons: [
        { text: 'Encargo', color: 'teal-5' },
        { text: 'Admi. Networking', color: 'teal-5' },
        { text: 'Productos Paypal', color: 'teal-5' },
        { text: 'Planificacion', color: 'teal-5' },
        { text: 'Notificaciones', color: 'teal-5' },
        { text: 'Filtro Comunicaciones', color: 'teal-5' }
      ],
      form: {
        proyect: 'Proyecto Casa Vera & Del Barrio',
        id: '01-000-000',
        address: 'Urb. Quincheumo',
        description: 'Predio PL-03',
        dateIn: '15/08/2020',
        dateOut: '15/12/2020',
        area: '500m2',
        boss: 'Pablo Aristia',
        value: 3000 + ' UF',
        company: 'VIIA Diseño'
      },
      panel: {
        description: 'Detalle Panel Experto',
        customers: {
          title: 'Clientes',
          data: [
            {
              name: 'Experto A.',
              id: 1,
              val: false
            },
            {
              name: 'Experto A.',
              id: 2,
              val: false
            },
            {
              name: 'Experto A.',
              id: 3,
              val: false
            },
            {
              name: 'Experto A.',
              id: 4,
              val: false
            },
            {
              name: 'Experto A.',
              id: 5,
              val: false
            },
            {
              name: 'Experto A.',
              id: 6,
              val: false
            }
          ]
        },
        team: {
          title: 'Equipo'
        },
        advisers: {
          title: 'Asesores'
        }
      }
    }
  },
  methods: {
    changeColor (id) {
      return this.buttons.forEach((ele, index) => { if (index === id) ele.color = 'grey-3'; else ele.color = 'teal-5'; return ele })
    }
  }
}
</script>
<style lang="sass" scoped>
.example-container

  .example-cell
    margin: 1px
    padding: 2px 8px
    box-shadow: inset 0 0 0 2px $grey-6
  .bg-brand
    background: #363536

</style>
