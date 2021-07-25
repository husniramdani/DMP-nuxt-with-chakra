<template>
  <c-box overflow="hidden" d="flex" bg="tomato" p="5">
      <nuxt-link to="/">Home</nuxt-link>
      <nuxt-link to="/login">
        <c-button variant="link" ml="5">Login</c-button>
      </nuxt-link>
  </c-box>
</template>

<script>
import {
  CBox,
  CButton
} from '@chakra-ui/vue'

export default {
  name: "Navbar",
  data() {
    return {
    };
  }
};
</script>
