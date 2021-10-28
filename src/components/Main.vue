<template>
	<div id="vue-rolling-marquee" ref="rolling-marquee-container">
		<div class="rolling-content" ref="rolling-marquee-content" :style="{ transform: `translate(calc(-50% + ${startPoint.x}px),calc(-50% + ${startPoint.y}px))`, animationDuration }">
			<slot />
		</div>
	</div>
</template>

<script>
	export default {
		name: "vue-rolling-marquee",
		props: {
			direction: {
				type: String,
				validator: val => ["top", "right", "bottom", "left"].includes(val) || /(?<=^\s*)[+-]?\d*\.?\d+deg(?=\s*)/.test(val),
				default: "left"
			},
			speed: {
				type: [Number, String],
				validator: val => typeof val == "number" || val == "30s",
				default: "30s"
			},
			duration: Number
		},
		data() {
			return {
				absX: undefined,
				absY: undefined,
				absZ: undefined,
				style: null
			};
		},
		computed: {
			localDirection() {
				let dir = this.direction;
				if (!this.regVal("deg").test(dir)) {
					switch (dir) {
						case "top":
							dir = "0deg";
							break;
						case "right":
							dir = "90deg";
							break;
						case "bottom":
							dir = "180deg";
							break;
						case "left":
							dir = "270deg";
					}
				}
				let reg = this.regVal("", "deg");
				let num = 90 - Number(dir.match(reg)[0]);
				num = num >= 0 ? num % 360 : 360 + (num % 360);
				let quadrant = (Math.ceil(num / 90) || 1) - 1;
				return {
					x: (0b1001 >> quadrant) & 1 || -1,
					y: (0b1100 >> quadrant) & 1 || -1,
					angle: (Math.PI * 2 * num) / 360
				};
			},
			startPoint() {
				return {
					x: ~(this.localDirection.x * this.absX) + 1 || 0,
					y: ~(this.localDirection.y * this.absY) + 1 || 0
				};
			},
			endPoint() {
				return {
					x: this.localDirection.x * this.absX || 0,
					y: this.localDirection.y * this.absY || 0
				};
			},
			animationDuration() {
				if (this.speed != "30s") return (2 * this.absZ) / this.speed + "s";
				else if (this.duration) return this.duration / 1000 + "s";
				return this.absZ / 15 + "s";
			}
		},
		watch: {
			localDirection(val) {
				this.init(val);
			}
		},
		methods: {
			regVal(usefulUnit = "", uselessUnit = "") {
				return new RegExp(`(?<=^\\s*)[+-]?\\d*\\.?\\d+${usefulUnit}(?=${uselessUnit}\\s*)`);
			},
			init(localDirection = this.localDirection) {
				this.$nextTick(() => {
					let container = this.$refs["rolling-marquee-container"],
						content = this.$refs["rolling-marquee-content"],
						W = container.clientWidth,
						H = container.clientHeight,
						w = content.clientWidth,
						h = content.clientHeight,
						angle = localDirection.angle,
						radian = Math.atan(H / W);
					if ((angle >= radian && angle <= Math.PI - radian) || (angle >= Math.PI + radian && angle <= 2 * Math.PI - radian)) {
						this.absY = (H + h) / 2;
						this.absX = Math.abs(this.absY / Math.tan(angle));
					} else {
						this.absX = (W + w) / 2;
						this.absY = Math.abs(this.absX * Math.tan(angle));
					}
					this.absZ = Math.pow(this.absX ** 2 + this.absY ** 2, 0.5);
					this.registAnimation();
				});
			},
			registAnimation() {
				if (this.style) this.style.remove();
				let style = (this.style = document.createElement("style"));
				style.innerHTML = `
					@keyframes vue-rolling-marquee {
						0% {
							transform: translate(calc(-50% + ${this.startPoint.x}px),calc(-50% + ${this.startPoint.y}px))
						}
						100% {
							transform: translate(calc(-50% + ${this.endPoint.x}px),calc(-50% + ${this.endPoint.y}px))
						}
					}
				`;
				document.body.appendChild(style);
			}
		},
		mounted() {
			this.init();
		}
	};
</script>

<style lang="sass" scoped>
	#vue-rolling-marquee
		position: relative
		overflow: hidden
		.rolling-content
			position: absolute
			top: 50%
			left: 50%
			animation-name: vue-rolling-marquee
			animation-timing-function: linear
			animation-iteration-count: infinite
			animation-delay: 0s
</style>
