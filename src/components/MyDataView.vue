<script setup>
import { ref, onMounted } from "vue";
import { ProductService } from '@/service/ProductService';

import axios from 'axios'
  const url = 'https://bcv-api-vnzw.onrender.com/bcv';
  const urlMenu = 'https://bcv-api-vnzw.onrender.com/menu';

  const bcvPrice = ref(0);
  const menu = ref(0);
  const total = ref (0)
  const totalBs = ref (0)

   const obtenerBcv = onMounted( async ()=>{
   const { data } = await axios.get(url);
   bcvPrice.value = data;
  })

  const sumarAlTotal = (precio,precioBs) => {
    total.value += precio;
    totalBs.value += precioBs;
    menu.push
  };

  const restarAlTotal = (precio,precioBs) => {
    total.value -= precio;
    totalBs.value -= precioBs; 
  };

  const borrarCuenta = () =>{
    total.value=0;
    totalBs.value=0;
  };

   const getMenu = onMounted( async ()=>{
    const { data } = await axios.get(urlMenu);
    menu.value = data;
    console.log(menu.value)
   })

/*
onMounted(() => {
    ProductService.getProductsSmall().then((data) => (products.value = data));
});*/

//const products = ref();
/*const getSeverity = (product) => {
    switch (product.inventoryStatus) {
        case 'INSTOCK':
            return 'success';

        case 'LOWSTOCK':
            return 'warning';

        case 'OUTOFSTOCK':
            return 'danger';

        default:
            return null;
    }};*/
</script>

<template>
    <div>
        <Divider/>
        $ <Chip :label="total.toFixed(2)" icon=""/>
        Bs. <Chip :label="totalBs.toFixed(2)" icon=""/>
        <Button @click="borrarCuenta" icon="pi pi-times" class="p-ml-auto" severity="danger"  rounded aria-label="Cancel" />
        <i   class="pi pi-shopping-cart p-overlay-badge" style="float:right;"></i>
        <Divider/>
    </div>
    <div class="card">
        <DataView :value="menu" paginator :rows="5">
            <template #list="slotProps">
                <div class="col-12">
                    <div class="flex flex-column xl:flex-row xl:align-items-start p-4 gap-2">
                        <!--<img class="w-9 sm:w-16rem xl:w-10rem shadow-2 block xl:block mx-auto border-round" :src="`https://primefaces.org/cdn/primevue/images/product/${slotProps.data.image}`" :alt="slotProps.data.name" />-->
                        <div class="flex flex-column sm:flex-row justify-content-between align-items-center xl:align-items-start flex-1 gap-2">

                            <div class="flex flex-column align-items-center sm:align-items-start">
                                <div class="text-1x1 font-bold text-900">{{ slotProps.data.nombre }} {{slotProps.data.desc}}</div>
                                <p>Q: 3</p>
                                <!--<Rating :modelValue="slotProps.data.rating" readonly :cancel="false"></Rating>-->
                                <div class="flex align-items-center gap-2">
                                    <span class="flex align-items-center gap-2">
                                        
                                        <span class="text-1xl font-semibold">{{ slotProps.data.precio }}
                                        <i class="pi pi-dollar"></i></span>
                                    </span>
                                    <span class="flex align-items-center gap-2">
                                        <i class=""></i>
                                        <span class="text-1xl font-semibold">{{ slotProps.data.precioBs }} Bs.</span>
                                    </span>
                                    <!--<Tag :value="slotProps.data.inventoryStatus" :severity="getSeverity(slotProps.data)"></Tag>-->
                                </div>
                            </div>

                            <div class="flex sm:flex-column align-items-center sm:align-items-end gap-2 sm:gap-2">
                                <!--<span class="text-2xl font-semibold">${{ slotProps.data.price }}</span>-->
                                <Button @click="sumarAlTotal(slotProps.data.precio,slotProps.data.precioBs)" icon="pi pi-plus"  rounded></Button>
                                <Button @click="restarAlTotal(slotProps.data.precio,slotProps.data.precioBs)" icon="pi pi-minus" rounded :disabled="total <= '0'" class="icon-med"></Button>
                            </div>
                        </div>
                    </div>
                </div>
            </template>
        </DataView>
    </div>
</template>