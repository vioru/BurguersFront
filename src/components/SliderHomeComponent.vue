<template>
<div class="container">
				<!-- Start Carousel -->
				<div id="carousel-demo" class="carousel">
					<div class="item-1">
						<img alt="Vue logo" src="../assets/logo.png">
					</div>
					<div class="item-2">
						<img alt="Vue logo" src="../assets/logo.png">
					</div>
					<div class="item-3">
						<img alt="Vue logo" src="../assets/logo.png">
					</div>
				</div>
				<!-- End Carousel -->
			</div>

            
</template>

<script>


export default{
    name: "SliderHomeComponent",
    data() {
        return {
            slides: [
                "https://www.bostonmagazine.com/wp-content/uploads/sites/2/2022/11/fresh-boston-900px.jpg",
                "https://img.freepik.com/fotos-premium/hamburguesa-ternera-artesanal-papas-fritas-sobre-fondo-negro_73989-21204.jpg",
                "https://crehana-blog.imgix.net/media/filer_public/6f/3e/6f3e8760-aeff-4b1c-baa3-85a05b95ea40/restaurantes-de-hamburguesas.png"
        ],
        };
    },
    methods: {
        CreateBurguer() {
            console.log("uso de modal");
            this.isActive = true;
        },
        closeModal() {
            this.isActive = false;
        },
        sendInfo(id){
        
                console.log(id);
            
            
        }
    },
    components: {  }
}

</script>

<style>
.slider{
    height: 108vh;

}
</style>