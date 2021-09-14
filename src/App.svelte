<div id="app">
	<div class="top-container">
		<div class="left text">
			<h1>10,000+ of our users love our products.</h1>
			<p>
				We only provide great products combined with excellent customer service.
				See what our satisfied customers are saying about our services.
			</p>
		</div>
		<div class="right rating">
			{#each sourseList as source , index}
				<RatingCard  customClass={`rating-card-${index}`} source={source} rating={5}/>
			{/each}
		</div>
	</div>
	<div class="bottom-container">
		{#each reviewList as review , index}
			<ReviewCard customClass="review-card-{index}" user_name={review.user_name} review={review.review}/>
		{/each}
	</div>
</div>

<script>
import RatingCard from "./components/RatingCard.svelte"
import ReviewCard from "./components/ReviewCard.svelte"

let sourseList = ["Reviews","Report Guru","BestTech"]
let reviewList = [
	{ user_name: "Colton Smith",review: '"We needed the same printed design as the one we had ordered a week prior.Not only did they find the original order, but we also received it in time.Excellent!"' },
	{ user_name: "Irene Roberts",review: '"Customer service is always excellent and very quick turn around. Completely delighted with the simplicity of the purchase and the speed of delivery."' },
	{ user_name: "Anne Wallace",review: '"Put an order with this company and can only praise them for the very high standard. Will definitely use them again and recommend them to everyone!"' }
	]
</script>

<style type="text/scss">
@import "./shared";
#app {
	display: flex;
	flex-direction: column;
	gap: 100px;
	.top-container {
		display: flex;
		width: 100%;
		.left {
			color: #502050;
			h1 {
				color: hsl(300, 43%, 22%);
				padding-bottom: 20px;
			}
			p {
				color: hsl(303, 10%, 53%);
				line-height: 1.7;
			}
		}
		.right {
			display: flex;
			flex-direction: column;
			justify-content: center;
		}	
	}
	.bottom-container {
		display: flex;

		:global(.review-card-1) {
			margin-top: 20px;
		}
		:global(.review-card-2) {
			margin-top: 40px;
		}
	}
}

@include media(">tablet") {
	#app {
		padding: 120px mathFromPcToTablet(200,45);
		.top-container {
			gap: mathFromPcToTablet(200,0);
			width: fit-content;
			.left {
				h1 {
					width: mathFromPcToTablet(450,260);
					font-size: mathFromPcToTablet(50,31);
				}
				p {
					width: mathFromPcToTablet(540,368);
					font-size: mathFromPcToTablet(17,14);
				}
			}
			.right {
				gap: mathFromPcToTablet(50,35);
				:global(.rating-card-1){
					margin-left: mathFromPcToTablet(40,20);
				}
				:global(.rating-card-2) {
					margin-left: mathFromPcToTablet(80,50);
				}
			}	
		}
		.bottom-container {
			gap: mathFromPcToTablet(40,20);
		}
	}
}
@include media("<=tablet") {
	#app {
		gap: 70px;
		.top-container {
			flex-direction: column;
			text-align: center;
			gap: 60px;
			.left {
				h1 {
					width: fit-content;
					margin: auto;
				}
				p {
					margin: auto;
				}
			}
			.right {
				align-items: center;
				gap: 50px;
			}
		}
		.bottom-container {
			flex-direction: column;
			align-items: center;
		}
	}	
}
@include media("<=tablet",">phone") {
	#app {
		padding: mathFromTabletToPhone(80,50)
				 mathFromTabletToPhone(100,0);
		.top-container .left p{
			width: mathFromTabletToPhone(550,290);
			font-size: mathFromTabletToPhone(16,13);
		}
	}
}
@include media("<=phone") {
	#app {
		padding: 50px 0px;
		.top-container .left p{
			width: 290px;
			font-size: 13px;
		}
	}
}

</style>