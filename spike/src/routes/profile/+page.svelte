<script>
	import {ComponentBox} from '$lib';
	import {totalScore} from '$lib/stores'
    import { WinC,Button } from '$lib';


	/** @type {{data: any}} */
	let { data } = $props();
	let person = data.person
	
	// import '../../styles/profile.css'
	// import { error } from './+error.svelte';
	// import { page } from '$app/stores';


	let text;
	let context1;
	let context2;
	let background;

	
	

</script>

<!-- external head  -->
<svelte:head>
	<title>profile of {person}</title>
	<link rel="preload" href="{person.avatar}" as="image">
	
</svelte:head>

<section data-sveltekit-preload-data="false" >

	<WinC 
		
		title="profile"
		context=""
		role="header"
		class="top-c"
	>
	</WinC>

	<div class="profile-detail">
		<WinC
		title=""
		context=""
		role="child"
		class="box1"
		>
		
		<article class="imgBox">
			<h1>naam</h1>
			<figure>
				<!-- profile image -->
			</figure>

			<div class="buttonBox">
				<Button
				text="logout"
				color="red"
				type="/"
				class="logout"
				/>
			</div>

			

		</article>


		</WinC>


		<ComponentBox
		heading="Persoonlijke gegevens"
		context1="bekijk je persoonlijke gegevens"
		context2=""
		display="flex"
		titleAlign=""
		class="box2"
		>

		{#if $totalScore == 300}
		<p>{$totalScore} is cash</p>
		{:else if $totalScore == 400 }
		<p>{$totalScore} is bike</p>
		{:else}
		<p> score is {$totalScore}</p>
		{/if}

		<form action="">


			<label for="Full-name">
				<input type="text" id="Full-name" placeholder="naam">
			</label>
			
			<label for="email">
				<input type="email" name="" id="email" placeholder="email">
			</label>
			
			<label for="job">
				<input type="text" name="" id="job" placeholder="Job title">
			</label>
			
			<label for="MP">
				<input type="text" id="MP" placeholder="mobilteit pakket">
			</label>
		</form>

		<WinC 
		role="child"
		title="WinC"
		>
			<WinC 
			role='header'
			title="WinC"

			>
				<h1>WinC</h1>
				
			</WinC>
		</WinC>


		<div class="buttonBox">

			
			
			<Button
			text="upload"
			color="black"
			type="submit"
			class=""
			/>
		</div>

		
		</ComponentBox>

	</div>


</section>


<style>

*{
	/* transition */
	--pageDelay: .5s;
	--pageDuration: .5s;
	--pageTransTiming: linear;
	--pageTrans: var(--pageDuration) var(--pageTransTiming) var(--pageDelay);

	/* outline */
	--Ol-color:var(--D-base-bk);
	--Ol-size:2px;
	--Ol-style:solid;
	--outline: var(--Ol-style) var(--Ol-size) var(--Ol-color); 

	gap: 3%;
}




section{

	position: relative;
	align-items:center;
	overflow: visible;
	perspective: 3000px;
	
}	


/* /////////////////////////// */
/* general content container */
/* /////////////////////////// */

.profile-detail{
	display: flex;
	flex-direction: row;
	width: 100%;
	height: fit-content;

}

@media (width < 870px){
	.profile-detail{
		flex-direction: column;
	}
}


/* /////////////////////////// */

.profile-detail{

 & > div:nth-of-type(1){
	padding: 3.5%;
	height: fit-content;

	
 }
}
.imgBox{
	flex: 1;
	display: flex;
	flex-direction: column;
	height: 100%;
	width: 100%;
	justify-content: center;
	align-items: center;
	border-radius: 18px;
}

.imgBox h1{
	font-size: 2rem;
	margin-bottom: 3%;
	flex-basis: 10%;
}

.imgBox figure{
	display: flex;
	flex-direction: column;
	background-color: var(--D-mid-bk);
	width: 60%;
	height: 100px;
	border-radius: 5%;
	aspect-ratio: 1;
	flex: 1;
}

.imgBox .buttonBox {
	place-content: center;
	/* height: fit-content; */
	flex-basis: 10%;

	& button,a{
		width: 7rem;
		height: 2rem;
		place-content: center;
	}
}

label{
	
}

.buttonBox{
    display: flex;
    flex-direction: row;
    align-self: center;
	justify-content: space-between;
    /* gap: 15%; */
    width: 100%;
    height: 3rem;
    margin-top: 20px;

	
    & button,a {
		width: fit-content;
    	padding-inline: 5%;
		text-align: center;
    }
  }

  /* ---- */

  .top-c{
        margin-bottom: 2%;
		display: flex;
		align-items: center;
		background-color: var(--LD-background);
		width: 100%;

		& h1{
		color: var(--D-t-support);
		font-size: 3rem;
		}
    }

	.box1{
		/* outline: solid purple; */
		flex: 0 0 30%;
		background-color: var(--LD-background);
		min-height: fit-content;
	}

	.box2{
		/* outline: solid blue; */
		flex-grow:1 0 40%;
		background-color: var(--LD-background);
		min-height: fit-content;

		& h1{
			color: var(--LD-text);
			font-size: 2rem;
			font-weight: 500;
			margin-bottom: 1rem;
		}

		& p{
			color: var(--LD-text);
			margin-bottom: .5rem;
		}

		& form{
			display: flex;
			flex-direction: column;
			/* gap:17%; */
		}

		& form label{
			color: var(--LD-text);
			width: 55%;
			height: 2rem;
			margin-bottom: 3%;
		}
		
		& form input{
			height: 100%;
			width: fit-content;
			padding: 5%;
			font-size: clamp(10px, 50vw - 1rem, 130%);
			border-radius: .5rem;
		}
	}



</style>