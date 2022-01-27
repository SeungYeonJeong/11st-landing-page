<template>
  <LNB />
  <TheHeader />
  <Billboard />
</template>

<script>
import LNB from '~/components/LNB'
import TheHeader from '~/components/TheHeader'
import Billboard from '~/components/Billboard'

export default {
  components: {
    LNB, // 지역등록
    TheHeader,
    Billboard
  }
}
</script>

<style lang="scss" scoped>
  @import "~/scss/main";
</style>
