<script lang="ts">
	const MAX_WIDTH = 100;
	let leftBarWidth = 50;
	let rightBarWidth = 50;
	let left_count = 0;
	let right_count = 0;

	function reset() {
		leftBarWidth = 50;
		rightBarWidth = 50;
		left_count = 0;
		right_count = 0;
	}

	function handleClick(side) {
		if (side === "left" && leftBarWidth < MAX_WIDTH) {
			leftBarWidth += 1;
			rightBarWidth -= 1;
			left_count += 1;
		} else if (side === "right" && rightBarWidth < MAX_WIDTH) {
			leftBarWidth -= 1;
			rightBarWidth += 1;
			right_count += 1;
		}
	}

	(() => {
		//on the key 'k' clicked, handleClick('left') will be called, for key 'l' clicked, handleClick('right') will be called
		document.addEventListener("keydown", (e) => {
			if (e.key === "k") {
				handleClick("left");
			} else if (e.key === "l") {
				handleClick("right");
			}
		});
	})();
</script>

<div>
	<div class="top">
		<div>{left_count}</div>
		<div>{right_count}</div>
	</div>
	<div class="container">
		<div class="left-bar tran" style="width: {leftBarWidth}%;" />
		<div class="right-bar tran" style="width: {rightBarWidth}%;" />
	</div>
	<div class="btn-container">
		<button class="text" on:click={() => handleClick("left")}>Yes</button>
		<button class="text" on:click={() => handleClick("right")}>No</button>
	</div>
	<div>
		<button class="reset" on:click={reset}>Reset</button>
	</div>
</div>

<style lang="sass">
.top
  display: flex
  justify-content: space-around
  font-size: 2rem
  font-weight: 700
  margin-top: 2rem
.container 
  display: flex
  width: 100%
  height: 50px
  .left-bar 
    height: 100%
    background-color: blue
  .right-bar 
    height: 100%
    background-color: red
  .tran 
    transition: all 0.3s ease

.btn-container 
  margin-top: 3rem
  display: flex
  justify-content: space-around
  .text 
    width: 50% !important
    color: white
    font-weight: 700 !important
    font-size: 5rem !important

.reset
  font-size: 2rem
  margin-top: 2rem
  font-weight: 700
</style>
