<script lang="ts">
	import { onMount } from 'svelte';

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

	let intersectingClass = "non-intersecting";

	onMount(() => {
		const observer = new IntersectionObserver(entries => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					intersectingClass = "intersecting";
				} else {
					intersectingClass = "non-intersecting";
				}
			})
		})

		observer.observe(document.querySelector('two')!)
	})

</script>

<twocontainer>
	<two class={intersectingClass}>
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
</twocontainer>

<style lang="scss">
	twocontainer {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

  two {
    box-shadow: -9px 25px 36px 0px rgba(0,0,0,0.40);
    scroll-snap-align: start;

    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: nowrap;
    flex-direction: column;

		border-radius: 50px;

    height: 80vh;
    width: 80vw;

    background-color: white;

		transition: all 0.3s ease-in-out;

		&.intersecting {
      opacity: 1;
			transform: translateY(0);
    }

		&.non-intersecting {
			opacity: 0;
			transform: translateY(10%);
    }

    overflow-x: hidden;

    @keyframes up {
      from {
        transform: translateY(50%);
      }
      1% {
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
        text-align: center;
				font-size: 2vw;
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