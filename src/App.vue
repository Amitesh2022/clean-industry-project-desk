<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">CleanIndustryEU<span>PROJECT DELIVERY</span></div><nav><RouterLink to="/">decarbonisation projects</RouterLink><RouterLink to="/insights">Investment guidance</RouterLink></nav><div class="health"><i /> Java Clean industry project service connected</div></aside><main><header><div><span class="eyebrow">Coordinate investment-ready clean industry projects for competitive decarbonisation</span><h1>Clean Industry Project Desk</h1></div><button @click="store.addOffer">Add decarbonisation project</button></header><section class="summary"><article><small>Projects investment-ready</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>decarbonisation projects tracked</small><strong>{{ offers.length }}</strong><p>Shared investment view</p></article><article><small>Delivery risks</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
