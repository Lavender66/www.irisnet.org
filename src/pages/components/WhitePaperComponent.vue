<template>
	<div class="white_paper_container" ref="whitePaper">
		<div class="white_paper_wrap">
			<navigation-line/>
			<h2 class="white_paper_title">{{$store.state.messages.home.KeyInnovations.title}}</h2>
			<div class="white_paper_list_content">
				<div class="white_paper_item"
				     v-for="item in $store.state.messages.home.KeyInnovations.list"
				     :key="item.id">
					<div class="white_paper_item_image">
                        <img class="white_paper_item_icon" :src="item.imgName" alt="">
					</div>
					<div class="white_paper_item_content">{{item.msg}}</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import NavigationLine from "./NavigationLine";
	export default {
		name: "WhitePaperComponent",
		components: {NavigationLine},
		mounted(){
			this.onresize();
			window.addEventListener('resize', this.onresize);
		},
		methods:{
			onresize(){
				setTimeout(() => {
					this.$store.commit('whitePaper', this.$refs.whitePaper.offsetTop - this.$store.state.headerHeight);
				},200)
			}
		}
	}
</script>

<style scoped lang="less">
	.white_paper_container{
        box-sizing: border-box;
        padding: 0.8rem 0;
		background: rgba(21, 12, 54, 1);
		.white_paper_wrap{
			max-width: 12rem;
			margin: 0 auto;
			@media(max-width: 1200px){
				margin: 0 0.48rem;
			}
			@media(max-width: 596px){
				margin: 0 0.2rem;
			}
			.white_paper_line{
				width: 1rem;
				height: 0.08rem;
				background: rgba(46, 69, 211, 1);
			}
			.white_paper_title{
				margin-top: 0.36rem;
                font-family: ArialMT;
				font-weight: normal;
				font-size: 0.4rem;
				color: rgba(255,255,255,1);
				line-height: 0.4rem;
				@media(max-width: 768px){
                    margin-top: 0.24rem;
                    font-size: 0.32rem;
				}
			}
			.white_paper_list_content{
				margin-top: 0.68rem;
				display: grid;
				grid-template-columns: repeat(3,1fr);
				grid-template-rows:1fr;
				grid-column-gap: 0.4rem;
				@media(max-width: 1000px){
					grid-template-columns: repeat(1,1fr);
					grid-row-gap: 0.4rem;
					justify-items: center;
					margin-top: 0.48rem;
				}
				@media(max-width: 596px){
					margin-top: 0.24rem;
				}
				.white_paper_item{
					box-sizing: border-box;
					padding: 0.64rem 0.3rem 0.36rem 0.3rem;
					background: url("../../assets/white_paper.png") no-repeat center / cover;
                    border: 0.03rem solid rgba(111, 33, 193, 0.2);
					border-radius: 0.04rem;
					@media(max-width: 1000px){
						width: 5rem;
					}
					@media(max-width: 596px){
						width: 100%;
					}
					.white_paper_item_image{
                        margin: 0 auto;
                        width: 1.5rem;
                        height: 1.5rem;
						.white_paper_item_icon{
                            width: 100%;
						}
					
					}
					.white_paper_item_content{
						margin-top: 0.4rem;
						font-size: 0.2rem;
                        font-family: ArialMT;
						line-height: 0.32rem;
						color: rgba(255,255,255, 0.74);
					}
				}
				.white_paper_item:first-child{
					background: url("../../assets/white_paper_first.png") no-repeat center / cover;
				}
				.white_paper_item:last-child{
					background: url("../../assets/white_paper_last.png") no-repeat center / cover;
				}
			}
			.white_paper_button_container{
                display: flex;
                justify-content: center;
				.white_paper_button{
                    position: relative;
                    box-sizing: border-box;
					color: rgba(255,255,255,1);
					display: flex;
                    justify-content: center;
                    align-items: center;
					border-radius: 0.04rem;
                    margin-top: 0.6rem;
					padding: 0.1rem 0.31rem;
                    width: 2rem;
                    height: 0.5rem;
                    font-family: ArialMT;
                    font-size: 0.2rem;
                    line-height: 0.28rem;
                    background: linear-gradient(90deg, #7EA4FF, #A845E2, #6F21C1, #7EA4FF);
                    background-size: 400%;
                    z-index: 1;
                    &:hover {
                        animation: whitePaperAnimate 8s linear infinite;
                        box-shadow: 0px 0px 6px 3px #C965FF;
                        &::before {
                            filter: blur(0.2rem);
                            opacity: 1;
                            animation: whitePaperAnimate 8s linear infinite;
                        }
                    }
                    &::before {
                        content: '';
                        position: absolute;
                        top: -0.01rem;
                        left: -0.01rem;
                        right: -0.01rem;
                        bottom: -0.01rem;
                        z-index: -1;
                        background: linear-gradient(90deg, #7EA4FF, #A845E2, #6F21C1, #7EA4FF);
                        background-size: 400%;
                        border-radius: 0.06rem;
                        opacity: 0;
                        transition: all 0.5s linear;
                    }
					@media(max-width: 1000px){
						margin: 0.36rem auto 1rem auto;
					}
					@media(max-width: 596px){
						margin: 0.36rem auto 0.72rem auto;
					}
				}
			}
		}
	}
    @keyframes whitePaperAnimate {
        0% {
            background-position: 0%;
        }
        100% {
            background-position: 400%;
        }
    }
</style>
