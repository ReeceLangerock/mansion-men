<script>
    import { gotoManager } from '$lib/utils/helper';
	import { getAvatarFromTeamManagers, getNestedTeamNamesFromTeamManagers } from '$lib/utils/helperFunctions/universalFunctions';
	export let podium, leagueTeamManagers;

	const { year, champion, second, third, divisions, toilet } = podium;
</script>

<style>
	* {
		color: var(--g555);
	}

	h3 {
		margin: 1.5em 0 1em; /* Reduced from 2.5em 0 1.5em */
		font-size: 1.8em; /* Added explicit size control */
	}

	.awards {
		display: block;
		position: relative;
		width: 100%;
		z-index: 1;
	}

	#podium {
		width: 500px; /* Reduced from 600px */
		height: 400px; /* Reduced from 500px */
		position: relative;
		margin: 5px auto 20px; /* Reduced margins */
	}

	.podiumImage {
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: auto;
		z-index: 3;
	}

	.champ {
		position: absolute;
		width: 18%; /* Slightly smaller */
		height: auto;
		transform: translate(-50%, -50%);
		border-radius: 100%;
		border: 1px solid var(--bbb);
		background-color: var(--fff);
	}

	.laurel {
		position: absolute;
		width: 28%; /* Reduced from 33% */
		height: auto;
		transform: translate(-50%, -50%);
		bottom: 56.6%;
		left: 50%;
		pointer-events: none;
	}

	.first {
		bottom: 70%;
		left: 50%;
	}

	.second {
		bottom: 43%;
		left: 20%;
	}

	.third {
		bottom: 39%;
		left: 80%;
	}

	h3 {
		text-align: center;
	}

	.leaderBlock {
		position: relative;
		width: 70px; /* Reduced from 80px */
		height: 100px; /* Reduced from 119px */
		margin: 10px auto; /* Reduced from 15px */
	}

	.divisions {
		display: flex;
		justify-content: space-around;
		margin: 15px 0; /* Added margin control */
	}

	.divisionLeader {
		position: absolute;
		width: 60px; /* Reduced from 70px */
		height: 60px; /* Reduced from 70px */
		transform: translate(-50%, 0%);
		top: 0;
		left: 50%;
		border-radius: 100%;
		border: 1px solid var(--bbb);
		background-color: var(--fff);
		z-index: 3;
	}

	.medal {
		position: absolute;
		width: 35px; /* Reduced from 40px */
		height: auto;
		transform: translate(-50%, 0%);
		bottom: 0;
		left: 50%;
		z-index: 2;
	}

	.toiletBowl {
		position: relative;
		width: 180px; /* Reduced from 215px */
		height: 160px; /* Reduced from 190px */
		margin: 5px auto; /* Reduced from 10px */
	}

	.toiletWinner {
		position: absolute;
		width: 55px; /* Reduced from 65px */
		height: 55px; /* Reduced from 65px */
		transform: translate(-50%, 0%);
		top: 15px; /* Reduced from 20px */
		left: 55%;
		border-radius: 100%;
		border: 1px solid var(--bbb);
		z-index: 3;
	}

	.toilet {
		position: absolute;
		width: 100%;
		height: auto;
		transform: translate(-50%, 0%);
		bottom: 0;
		left: 50%;
	}

	.label {
		white-space: nowrap;
		line-height: 1.1em;
		text-align: center;
		min-height: 30px; /* Reduced from 34px */
		display: flex;
		flex-direction: column;
		justify-content: center;
		position: absolute;
		transform: translate(-50%, -50%);
		padding: 4px 20px; /* Reduced padding */
		background-color: var(--fff);
		border: 1px solid var(--bbb);
		box-shadow: 0px 2px 2px -1px var(--boxShadowOne), 0px 2px 3px 0px var(--boxShadowTwo), 0px 1px 6px 0px var(--boxShadowThree); /* Slightly reduced shadow */
		font-size: 0.9em; /* Added font size control */
	}

	.firstLabel {
		bottom: 60%;
		left: 50%;
	}

	.secondLabel {
		bottom: 40%;
		left: 20%;
	}

	.thirdLabel {
		bottom: 36%;
		left: 80%;
	}

	.genLabel {
		white-space: nowrap;
		line-height: 1.1em;
		min-height: 30px; /* Reduced from 34px */
		display: inline-flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		margin: 10px auto 15px; /* Reduced margins */
		padding: 4px 20px; /* Reduced padding */
		background-color: var(--fff);
		border: 1px solid var(--bbb);
		box-shadow: 0px 2px 2px -1px var(--boxShadowOne), 0px 2px 3px 0px var(--boxShadowTwo), 0px 1px 6px 0px var(--boxShadowThree);
		font-size: 0.9em; /* Added font size control */
	}

	.division {
		text-align: center;
	}

	.division h6 {
		margin: 0 0 8px 0; /* Reduced margin */
		font-size: 0.95em; /* Slightly smaller */
	}

	.toiletParent {
		width: 100%;
		text-align: center;
		padding: 20px 0 30px; /* Reduced from 25px 0 40px */
		margin-top: 20px; /* Reduced from 30px */
		box-shadow: 0 8px 6px -8px rgba(0,0,0,0.4); /* Slightly reduced shadow */
	}

	.banner {
		display: block;
		width: 55%; /* Reduced from 65% */
		max-width: 380px; /* Reduced from 450px */
		margin: 15px auto 0; /* Reduced top margin */
	}

	.toilet-banner {
		display: block;
		width: 45%; /* Reduced from 50% */
		max-width: 300px; /* Reduced from 350px */
		margin: 15px auto 0; /* Reduced top margin */
	}

	.clickable {
		cursor: pointer;
	}

	:global(.curOwner) {
		font-size: 0.7em; /* Slightly smaller */
		color: var(--bbb);
		font-style: italic;
	}

	/* Updated media queries with new base sizes */
	@media (max-width: 680px) {
		.label {
			padding: 4px 6px;
		}
		.genLabel {
			padding: 4px 6px;
		}
	}

	@media (max-width: 630px) {
		.label {
			font-size: 0.8em;
		}
		.genLabel {
			font-size: 0.8em;
		}
	}

	@media (max-width: 610px) {
		#podium {
			width: 420px; /* Adjusted for new base size */
			height: 336px;
			margin: 5px auto 20px;
		}

		.firstLabel {
			bottom: 58%;
		}

		.secondLabel {
			bottom: 35%;
		}

		.thirdLabel {
			bottom: 31%;
		}
	}

	@media (max-width: 535px) {
		.label {
			font-size: 0.7em;
		}
		.genLabel {
			font-size: 0.7em;
		}
	}

	@media (max-width: 520px) {
		.label {
			font-size: 0.65em;
			padding: 2px 4px;
		}
		.genLabel {
			font-size: 0.65em;
			padding: 2px 4px;
		}
	}

	@media (max-width: 510px) {
		#podium {
			width: 350px; /* Adjusted */
			height: 280px;
		}
	}

	@media (max-width: 425px) {
		.label {
			font-size: 0.55em;
		}
		.genLabel {
			font-size: 0.55em;
		}
	}

	@media (max-width: 410px) {
		#podium {
			width: 280px; /* Adjusted */
			height: 224px;
		}

		.firstLabel {
			bottom: 53%;
		}

		.secondLabel {
			bottom: 31%;
		}

		.thirdLabel {
			bottom: 27%;
		}
	}

	@media (max-width: 329px) {
		.label {
			font-size: 0.45em;
		}
		.genLabel {
			font-size: 0.45em;
		}
	}
</style>

<div class="awards">
	<h3>{year} Awards</h3>

	<img src="/banner.png" class="banner" alt="The Champion's Cup" />

	<div id="podium">
		<img src="/podium.png" class="podiumImage" alt="podium" />

		<!-- champs -->
		<img src="{getAvatarFromTeamManagers(leagueTeamManagers, champion, year)}" class="first champ clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: champion})} alt="champion" />
		<img src="/laurel.png" class="laurel" alt="laurel" />
		<span class="label firstLabel clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: champion})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, champion)}</span>

		<img src="{getAvatarFromTeamManagers(leagueTeamManagers, second, year)}" class="second champ clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: second})} alt="2nd" />
		<span class="label secondLabel clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: second})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, second)}</span>

		<img src="{getAvatarFromTeamManagers(leagueTeamManagers, third, year)}" class="third champ clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: third})} alt="3rd" />
		<span class="label thirdLabel clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: third})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, third)}</span>
	</div>
	<div class="divisions">
		{#each divisions as division}
			{#if division.rosterID}
				<div class="division">
					{#if division.name}
						<h6>{division.name} Division</h6>
					{:else}
						<h6>Regular Season Champion</h6>
					{/if}
					<div class="leaderBlock">
						<img src="{getAvatarFromTeamManagers(leagueTeamManagers, division.rosterID, year)}" class="divisionLeader clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: division.rosterID})} alt="{division.name} champion" />
						<img src="/medal.png" class="medal" alt="champion" />
					</div>
					<span class="genLabel clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: division.rosterID})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, division.rosterID)}</span>
				</div>
			{/if}
		{/each}
	</div>

		<!-- Toilet Bowl -->
	{#if toilet}
		<div class="toiletParent">
			
			<img src="/toilet-banner.png" class="toilet-banner" alt="The Toilet Bowl" />

			<div class="toiletBowl">
				<img src="{getAvatarFromTeamManagers(leagueTeamManagers, toilet, year)}" class="toiletWinner clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: toilet})} alt="toilet bowl winner" />
				<img src="/toilet-bowl-2.png" class="toilet" alt="toilet bowl" />
			</div>
			<span class="genLabel clickable" onclick={() => gotoManager({year, leagueTeamManagers, rosterID: toilet})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, toilet)}</span>
		</div>
	{/if}
</div>