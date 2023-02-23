<template>
    <div>
          <HeaderPage></HeaderPage>

    <ContainerPage></ContainerPage>
    </div>
  
</template>

<script>
import HeaderPage from '../../components/Header.vue'
import ContainerPage from '../../components/Container.vue'
export default {
    name: 'HomePage',
    components: {
        HeaderPage, 
        ContainerPage
    },
    data() {
        return {
            dialog: false,
        }
    },
}
</script>

<style lang="scss" scoped>
.header-page {
    display: flex;
    justify-content: center;
    height: 50px;
    background-color: #d3a1eb;
    line-height: 1.5;
    font-family: cursive;
    font-size: 16px;
    position: relative;

    >.title {
        color: #fff;
        font-weight: 700;
    }

    >.icon {
        position: absolute;
        left: 10px;
        margin-top: 14px;
    }
}
</style>