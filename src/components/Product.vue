<template>
<div id="product" class="product">
					<h2 class="rt-post-title"> {{ post.title.rendered }} </h2>
					<div class="rt-meta">
						<span class="posted-on">
							Posted On
							<span class="date" v-text="formatDate( post )">
							</span>
						</span>
					</div>
					
					<div class="progressive full" v-if="post.featured_image_src['full'][0]">

						<img class="lazy" v-progressive="post.featured_image_src['full'][0]" :data-srcset="post.featured_image_src['srcset']" :src="post.featured_image_src['full'][0]" />
						
					</div>

					<div class="rt-post-excerpt rt-content" v-html="post.excerpt.rendered" > </div>

				</div>
</template>
<script>
export default {
    name: 'product',
    props: {
	Posts: Object
	},
	methods: {
		formatDate: function( value ) {
			value = value.date;
			if ( value ) {
				const date = new Date( value );
				const monthNames = [ "January", "February", "March",
					"April", "May", "June", "July",
					"August", "September", "October",
					"November", "December" ];
				const day = date.getDate();
				const monthIndex = date.getMonth();
				const year = date.getFullYear();
				return monthNames[ monthIndex ] + ',' + day + ' ' + year;
			}
		}
	}
}
</script>
<style scoped>
.product {
    text-align:left;
    border:1px solid red;
    padding:1em;
    margin:2em 1em;
}
.product:after {
    content:"";
    display:block;
    clear:both;
}
.product_title {
    color: #666;
    font-size:200%;
    margin-bottom:0;
}
.product_price {
    margin-top:0;
}
.product_img {
    float:right;
    max-width:100%;
    height:auto;
}
</style>
