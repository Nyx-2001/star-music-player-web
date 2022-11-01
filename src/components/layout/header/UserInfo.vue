<template>
    <div class="flex items-center cursor-pointer hover-text">
      <ElAvatar size="small" round class="bg-gray-200" :src="profile?.avatarUrl ?? ''"></ElAvatar>
      <span class="text-xs ml-1.5" v-if="isLogin">{{ profile.nickname }}</span>
      <span class="text-xs ml-1.5" @click="goLogin" v-else>点击登录</span>
    </div>
  </template>
  
  <script setup lang="ts">
  import {useRouter} from "vue-router";
  import {onMounted} from "vue";
  import {useUserStore} from "@/stores/user";
  import {storeToRefs} from "pinia";

  const router = useRouter()
  const goLogin=()=>{
	router.push('/login')
  }
 

  const {login, checkLogin} = useUserStore()
  const {isLogin, profile, showLogin} = storeToRefs(useUserStore())
  
 
  onMounted(() => {
    checkLogin()
  })

  
  </script>
  
  <style lang="scss" scoped>

  </style>
  