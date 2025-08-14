<script setup>
import { ref,computed } from 'vue'
import Home from './Home.vue'
import GetStarted from './GetStarted.vue'
import Usage from './Usage.vue'
import Translation from './Translation.vue'
import Rules from './Rules.vue'
import Custom from './Custom.vue'
import Components from './Components.vue'
import Labels from './Labels.vue'
import Demo from './Demo.vue'

let selected=ref(0)

let current= computed(() => {
  switch (selected.value) {
    case 0:
      return Home
    case 1:
      return GetStarted
    case 2:
      return Usage
    case 3:
      return Rules
    case 4:
      return Custom
    case 5:
      return Components
    case 6:
      return Labels
    case 7:
      return Translation
    case 8:
      return Demo
  }
})

</script>

<template>
  <CNavbar expand="lg" color-scheme="dark" class="bg-info">
  <CContainer fluid>
    <CNavbarBrand href="#" @click="selected=0">DjValidatorVue</CNavbarBrand>
    <CNavbarToggler aria-label="Toggle navigation" aria-expanded={visible} @click="visible = !visible"/>
    <CCollapse class="navbar-collapse" :visible="visible">
      <CNavbarNav>
        <CNavItem>
          <CNavLink href="https://www.npmjs.com/package/djvalidatorvue" active>NPM</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="https://github.com/esneyderg357/DjValidatorVue" active>GitHub</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="https://www.npmjs.com/package/djvuefileinput" active>DjVueFileinput</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="https://www.npmjs.com/package/djvalidator" active>DjValidator jquery</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="https://www.npmjs.com/package/djsonloader" active>DjsonLoader</CNavLink>
        </CNavItem>
        <CNavItem>
          <CNavLink href="https://www.linkedin.com/in/david-esneyder-jerez-garnica-84309b239/" active>Developer</CNavLink>
        </CNavItem>
      </CNavbarNav>
    </CCollapse>
  </CContainer>
</CNavbar>
  <CContainer class="mt-3">
    <CRow>
      <CCol md="4">
        <CListGroup>
          <CListGroupItem :class="{ active: selected==1 }" as="a" href="#" @click="selected=1">Get started</CListGroupItem>
          <CListGroupItem :class="{ active: selected==2 }" as="a" href="#" @click="selected=2">Usage</CListGroupItem>
          <CListGroupItem :class="{ active: selected==3 }" as="a" href="#" @click="selected=3">Validation rules</CListGroupItem>
          <CListGroupItem :class="{ active: selected==4 }" as="a" href="#" @click="selected=4">Custom validations</CListGroupItem>
          <CListGroupItem :class="{ active: selected==5 }" as="a" href="#" @click="selected=5">Components</CListGroupItem>
          <CListGroupItem :class="{ active: selected==6 }" as="a" href="#" @click="selected=6">Label Reference</CListGroupItem>
          <CListGroupItem :class="{ active: selected==7 }" as="a" href="#" @click="selected=7">Language</CListGroupItem>
          <CListGroupItem :class="{ active: selected==8 }" as="a" href="#" @click="selected=8">Demos</CListGroupItem>
        </CListGroup>
      </CCol>
      <CCol md="8">
        <component :is="current" />
      </CCol>
    </CRow>
  </CContainer>
  
</template>

<style scoped></style>
