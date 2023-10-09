

<template>
    <div class="card xl:flex xl:justify-content-center">
        <OrderList v-model="products" listStyle="height:auto" dataKey="id">
            <template #header> List of Products </template>
            <template #item="slotProps">
                <div class="flex flex-wrap p-2 align-items-center gap-3">
                    <!--<img class="w-4rem shadow-2 flex-shrink-0 border-round" :src="'https://primefaces.org/cdn/primevue/images/product/' + slotProps.item.image" :alt="slotProps.item.name" />-->
                    <div class="flex-1 flex flex-column gap-2">
                        <span class="font-bold">{{ slotProps.item.name }}</span>
                        <div class="flex align-items-center gap-2">
                            <i class="pi pi-tag text-sm"></i>
                            <span>{{ slotProps.item.category }}</span>
                        </div>
                    </div>
                    <span class="font-bold text-900">$ {{ slotProps.item.price }}</span>
                </div>
            </template>
        </OrderList>
    </div>
</template>

