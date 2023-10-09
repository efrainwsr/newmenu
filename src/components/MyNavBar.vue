<script setup>
    import { ref } from "vue";
    import Menubar from 'primevue/menubar';

    const montoDolar = ref(10)
    const montoBs = ref(370)

const montosNav = ref([
       {
        label: 'Dolar'
       }
    ])
const items = ref([
    {
        label: 'Inicio',
        icon: 'pi pi-home',
    },
    {
        label: 'Ventas',
        icon: 'pi pi-money-bill',
    },
    {
        label: 'Ordenes',
        icon: 'pi pi-list',
        items: [
            {
                label: 'New',
                icon: 'pi pi-fw pi-user-plus'
            },
            {
                label: 'Delete',
                icon: 'pi pi-fw pi-user-minus'
            }
        ]
    }
]);

</script>

<template>
<Menubar :model="items">
    <template #start>
        <!--<img alt="logo" src="" height="40" class="mr-2" />-->

    </template>
    
        
    <!--<template :model="montosNav" #end>
        <span class="montosNav">Total: </span>
        <span class="montosNav">{{montoDolar}} $</span>
        <span class="montosNav">{{montoBs}} Bs. </span>
        <i v-badge  class="pi pi-shopping-cart med-icon p-overlay-badge"></i>
    </template>-->
</Menubar>

</template>


<style scoped>
    .med-icon{
        font-size: 2rem;
    }
    .montosNav{
        padding-left: 20px;
        padding-right: 20px;
        text-size: 3rem;

    }
</style>