<template>

	<div>
		<ul class="list-group">
		<li class="list-group-item" v-for="item in products" :key="item.id">
			{{ item.title}} - $ {{ item.price }}
			<button @click="$emit('remove-from-cart', item)" class="btn badge-danger float-right">
			Remove from Cart
			</button>
		</li>
		</ul>
		<div class="card p-3 my-5">
			<h4 class="text-center">$ {{ total }}</h4>
		</div>

		<button :disabled="products.length === 0" @click="$emit('pay')" class="btn btn-info form-control">Pay Now</button>
	</div>
</template>

<script>
	
	export default {

		props: ['products'],
		computed: {
			total(){
				return this.products.reduce((acc, item) => acc + Number(item.price), 0)
			}
		}

	}
</script>