<template>

  <!-- tentativo pora investigar es el siguiente codigo que funcuona desde la localizacion o idioma del dispositivo
  con lo que podriamos detectar el idioma de dicho dispositivo y siempre brindar soporte para otros idiomas
  link documentacion: https://quasar.dev/options/app-internationalization#detecting-locale
  / outside of a Vue file
import { Quasar } from 'quasar'
Quasar.lang.getLocale() // returns a string

// inside of a Vue file
import { useQuasar } from 'quasar'

setup () {
  const $q = useQuasar()
  $q.lang.getLocale() // returns a string
} -->
  <q-page padding>

    <q-btn
    label="English"
    @click="$i18n.locale = 'en-US'"
    />
     <!-- llamas a el traductor i18n y agregas el texto apata cuando le metes en su carpeta ejemplo fr y en-us -->
     <q-btn
    label="French"
    @click="$i18n.locale = 'fr'"
    />
       <q-btn
    label="Spanish"
    @click="$i18n.locale = 'es'"
    />

    <q-separator class="q-my-lg"/>
    <!-- separador solo para prueba -->

    <q-btn :label="$t('failed')" />
    <!-- en este caso probamos con botones utilizando una propiedad para cambio de texto o idioma comprobamos que funciona -->
    <q-btn :label="$t('success')" />
    <!-- tanto como en texto como en botones -->
    <p>{{ $t('failed') }}</p>
    <p>{{ $t('success') }}</p>



  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default {
  name: "IndexPage",

  mounted() {
    //this.$t('failed')
  }
}
</script>
