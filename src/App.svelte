<script>
	import Input from './Input.svelte'
</script>

<main>
	<section>

		<img class="logo" src="./images/logo.svg" alt="logo">

		<img class="hero" id="mobile" src="./images/hero-mobile.jpg" alt="hero">

		<h1>
			<span>we're</span> coming soon
		</h1>

		<p>
			Hello fello shoppers! We're currently building our new
			fashion store. Add your email below to stay up-to-date with
			announcements and our launch deals.
		</p>


		<Input />
		
	</section>

	<img class="hero" id="desktop" src="./images/hero-desktop.jpg" alt="hero">
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;600&display=swap');
	
	:global(:root) {
		--red-600: hsl(0, 6%, 24%); 
		--red-500: hsl(0, 93%, 68%);
		--red-300: hsl(0, 36%, 70%);
		--family: 'Josefin Sans', sans-serif;

		--grad-white: linear-gradient(135deg, hsl(0, 0%, 100%), hsl(0, 100%, 98%));
		--grad-red: linear-gradient(135deg, hsl(0, 80%, 86%), hsl(0, 74%, 74%));
	}

	:global(:root), :global(body), :global(*) {
		margin: 0;
		padding: 0;
	}

	main {
		width: 100%;
		height: 100%;
		display: grid;
		grid-template: 1fr / 1fr 610px;
		grid-template: "section hero";
		overflow: hidden;
	}

	section {
		background-image: url(../images/bg-pattern-desktop.svg);
		background-size: cover;
		padding: 65px 165px;

		display: grid;
		grid-area: section;
		grid-template: repeat(4, min-content) / 1fr;
		grid-template-areas: 
							"logo"
							"header"
							"content"
							"contact";
	}

	.logo {
		grid-area: logo;
		margin-bottom: 135px;
	}

	section > h1 {
		grid-area: header;
		line-break: strict;
		text-transform: uppercase;
		letter-spacing: 16px;
		line-height: 1.1;
		font-family: var(--family);
		font-size: 4rem;
		color: var(--red-600);
		margin-bottom: 20px;
	}

	section > h1 span {
		font-weight: 300;
		color: var(--red-300);
	} 

	section > p {
		grid-area: content;
		display: block;
		width: 43ch;
		line-height: 1.75;
		color: var(--red-300);
		font-family: var(--family);
		margin-bottom: 30px;
	}

	.hero {
		grid-area: hero;
		object-fit: cover;
		object-position: center;
	}

	#desktop.hero {
		width: min-content;
		height: 100%;
	}
	
	#mobile.hero {
		display: none;
		width: min-content;
		height: min-content;
	}
	
	@media (max-width: 675px) {
		main {
			grid-template: 1fr / 1fr;
			grid-template-areas: "section";
		}

		section {
			background: var(--grad-white);
			grid-template: repeat(5, min-content) / 1fr;
			padding: 35px 0;
			height: 100%;
			width: 100vw;
			overflow: hidden;
			grid-template-areas: 
								"logo"
								"hero"
								"header"
								"content"
								"contact";
		}

		#mobile.hero {
			display: initial;
			margin-bottom: 60px;
			width: 100%;
			height: 250px;
			object-position: top;
		}

		#desktop.hero { display: none; }
		
		.logo {
			width: 25%;
			margin-left: 30px;
			margin-bottom: 35px;
		}

		section > h1 {
			font-size: 2.5rem;
			letter-spacing: 10px;
			width: 10ch;
			text-align: center;
			place-self: center;
			margin-bottom: 10px;
		}

		section > p {
			font-size: 0.85rem;
			width: 35ch;
			place-self: center;
			text-align: center;
		}
	}
</style>