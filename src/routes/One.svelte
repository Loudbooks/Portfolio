<script lang="ts">
	let styles: string[] = [];

	const updateStyles = () => {
		for (let i = 0; i < 8; i++) {
			styles[i] = transformStyle();
		}
	};

	updateStyles();

	$: {
		setInterval(updateStyles, 3000);
	}

	function randomMovement() {
		const random = Math.floor(Math.random() * 60);
		return random + 1;
	}

	function randomRotation() {
		const random = Math.floor(Math.random() * 15);
		return random + 1;
	}

	function transformStyle() {
		return `transform: translate(${randomMovement() / 100}vh, ${(30 - randomMovement()) / 25}vh) rotate(${15 / 2 - randomRotation()}deg);`;
	}
</script>

<hellogroup>
	<hello>
		<span style={styles[0]}>L</span>
		<span style={styles[1]}>o</span>
		<span style={styles[2]}>u</span>
		<span style={styles[3]}>d</span>
		<span style={styles[4]}>b</span>
		<span style={styles[5]}>o</span>
		<span style={styles[6]}>o</span>
		<span style={styles[7]}>k</span>
	</hello>
	<arrowcontainer>
		<arrow></arrow>
	</arrowcontainer>
</hellogroup>

<style lang="scss">
  hello {
    scroll-snap-align: start;
    height: 100vh;

    display: flex;

    justify-content: center;
    align-items: center;

    font-size: 19vw;

    span {
      display: inline-block;
      transition: transform 3s ease-in-out;

      text-shadow: -50px 60px 200px rgba(0, 0, 0, 0.75);
      font-family: "Gabarito", sans-serif;
      color: white;
      font-weight: 900;

      padding-left: 0.3vw;
      padding-right: 0.3vw;
    }
    
    @keyframes gradient {
      0% {
        background-position: 0 50%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0 50%;
      }
    }
  }

  arrowcontainer {
    overflow: visible;
    scroll-snap-align: start;

    display: flex;
    align-content: center;
    justify-content: center;

      view-timeline-name: --up;
      view-timeline-axis: block;
      animation: ease-in-out up45 both;

      animation-timeline: --up;
      animation-duration: 1ms;
      animation-range: cover 0% cover 40%;

    arrow {
      overflow: visible;

      transition: transform 3s ease-in-out, opacity 3s ease-in-out;

      display: block;
      bottom: 50px;
      position: absolute;
      width: 2vw;
      height: 2vw;
      border-bottom: 6px solid #fff;
      border-right: 6px solid #fff;

      scroll-snap-align: end;

      animation: fade 4s ease-in-out infinite;
    }

    @keyframes fade {
      0% {
        transform: translate(0, -12px) rotate(45deg);
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        transform: translate(0, 12px) rotate(45deg);
        opacity: 0;
      }
    }

    @keyframes up {
      from {
        transform: translateY(50%);
      }
      to {
        transform: translateY(0);
      }
    }

    @keyframes up45 {
      10% {
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
  }
</style>