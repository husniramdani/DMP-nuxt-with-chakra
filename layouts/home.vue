<template>
  <div class="container">
    <CThemeProvider>
      <CColorModeProvider>
        <CBox font-family="body" as="main">
          <CReset />
          <Navbar />
          <Nuxt />
        </CBox>
      </CColorModeProvider>
    </CThemeProvider>
  </div>
</template>
<script>
import {
  CThemeProvider,
  CColorModeProvider,
  CReset,
  CBox
} from '@chakra-ui/vue'
import Navbar from '~/components/Navbar.vue'

export default {
  name: 'Home',
  components: {
    CThemeProvider,
    CColorModeProvider,
    CReset,
    CBox,
    Navbar
  }
}
</script>
