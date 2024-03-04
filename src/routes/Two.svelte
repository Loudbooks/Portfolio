<script lang="ts">
	let quotes: string[] = [
		'"Has two personalities, jukmifuguh and angry developer" - Error_404',
		'"like quietbook, but louder" - Phalipsio',
		'"real" - Shooken',
		'"really needs a therapist" - GuildMenu'
	];

	let quotesIndex = 0;
	let hidden = false;

	setInterval(() => {
		hidden = true;

		setTimeout(() => {
			increaseIndex();
			hidden = false;
		}, 400);
	}, 3000);

	function increaseIndex() {
		quotesIndex++;

		if (quotesIndex >= quotes.length) {
			quotesIndex = 0;
		}
	}

</script>

<two>
	<scroll>
		{#each [0, 1] as _}
			<images>
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" alt="Java" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/kotlin/kotlin-original.svg" alt="Kotlin" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/gradle/gradle-original.svg" alt="Gradle" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/rust/rust-original.svg" alt="Rust" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg" alt="CSharp" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/cplusplus/cplusplus-original.svg"
						 alt="CPlusPlus" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bash/bash-original.svg" alt="Bash" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/wasm/wasm-original.svg" alt="WASM" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" alt="HTML" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" alt="CSS" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/sass/sass-original.svg" alt="SASS" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mongodb/mongodb-original.svg"
						 alt="MongoDB" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/redis/redis-original.svg" alt="Redis" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/jetbrains/jetbrains-original.svg"
						 alt="JetBrains" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" alt="GitHub" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/photoshop/photoshop-original.svg"
						 alt="Photoshop" />
				<img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fedora/fedora-original.svg"
						 alt="Fedora Linux" />
			</images>
		{/each}
	</scroll>
	<testamonies class={hidden}>
		<h1> {quotes[quotesIndex]} </h1>
	</testamonies>
</two>

<style lang="scss">
  two {
    scroll-snap-align: start;

    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: nowrap;
    flex-direction: column;

    height: 100vh;
    width: 100vw;

    background-color: white;

    view-timeline-name: --upTwo;
    view-timeline-axis: block;

    animation: up ease-in-out both;
    animation-timeline: --upTwo;
    animation-duration: 1ms;
    animation-range: cover 0% cover 40%;

    overflow-x: hidden;

    @keyframes up {
      from {
        transform: translateY(50%);
      }
      to {
        transform: translateY(0);
      }
    }

    scroll {
      position: relative;
      display: flex;
      width: 90vw;
      overflow: hidden;

      mask-image: linear-gradient(90deg, transparent 5%, rgba(0, 0, 0, 1) 25%, rgba(0, 0, 0, 1) 75%, transparent 95%);

      images {
        white-space: nowrap;
        animation: scrollText1 20s linear infinite;
        animation-delay: -20s;

        img {
          height: 10vw;
          width: 10vw;

          padding-left: 10px;
        }
      }

      images:nth-child(2) {
        animation: scrollText2 20s linear infinite;
        animation-delay: -10s;

        img {
          height: 10vw;
          width: 10vw;

          padding-left: 10px;
        }
      }
    }

    testamonies {
      &.true {
        opacity: 0;
      }

      &.false {
        opacity: 1;
      }

      opacity: 1;

      transition: opacity 0.5s ease-in-out;

      h1 {
        font-family: "Gabarito", sans-serif;
        font-weight: 400;
      }
    }

    @keyframes scrollText1 {
      from {
        transform: translateX(100%);
      }
      to {
        transform: translateX(-100%);
      }
    }

    @keyframes scrollText2 {
      from {
        transform: translateX(0);
      }
      to {
        transform: translateX(-200%);
      }
    }

    @keyframes scrollSpeed {
      from {
        animation-duration: 0s;
      }
      to {
        animation-duration: 40s;
      }
    }

    @keyframes move {
      to {
        transform: translateX(calc(-100% + 100vw));
      }
    }
  }
</style>