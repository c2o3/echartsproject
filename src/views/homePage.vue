<template>
    <div>
        <header>
            <h1>大数据可视化</h1>
        </header>
        <section class="container">
            <section class="left">
                <ItemPage>
                    <ItemOne />
                </ItemPage>
                <ItemPage>
                    <ItemTwo />
                </ItemPage>
            </section>
            <section class="center">
                <MapPage />
            </section>
            <section class="right">
                <ItemPage>
                    <ItemThree />
                </ItemPage>
                <ItemPage>
                    <ItemFour />
                </ItemPage>
            </section>
        </section>
    </div>
</template>
<script setup>
    import ItemPage from '@/components/itemPage.vue'
    import ItemOne from '@/components/itemOne.vue'
    import ItemTwo from '@/components/itemTwo.vue';
    import ItemThree from '@/components/itemThree.vue';
    import ItemFour from '@/components/itemFour.vue';
    import MapPage from '@/components/mapPage.vue';
    
</script>
<style lang="scss">
    header {
        width: 100%;
        height: 1rem;
        text-align: center;
        background-color: rgba(0,0,255,.2);
        h1{
            font-size: .375rem;
            color: #fff;
            text-align: center;
            line-height: 1rem;
        }
    }
    .container{
        min-width: 1200px;
        max-width: 2560px;
        margin: 0 auto;
        padding: .125rem .125rem 0;
        display: flex;
        .left,.right{
            flex: 3;
        }
        .center{
            flex: 5;
            height: 10.5rem;
            border: 1px solid blue;
            padding: .125rem;
            margin: .25rem;

        }
    }
</style>