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

    .awards-container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 12px;
		padding-bottom: 32px;
		border-bottom: 2px solid var(--bbb);
    }

    .awards-header {
        text-align: center;
        margin-bottom: 2rem;
    }

    .awards-title {
        font-size: 2.5rem;
        font-weight: 700;
        background: linear-gradient(135deg, #772432, #772432, #772432);
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 0.5rem;
		color: var(--secondaryColor, #8b6e4a);

    }

    .awards-subtitle {
        font-size: 1.1rem;
		color: var(--secondaryColor, #8b6e4a);

    }

    /* Podium Section */
    .podium-section {
        margin-bottom: 3rem;

    }

    .podium-grid {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        gap: 1.5rem;
        max-width: 700px;
        margin: 0 auto;
    }

    .podium-card {
        background: var(--fff);
        border-radius: 16px;
        padding: 1.5rem;
        text-align: center;
        border: 1px solid var(--bbb);
        transition: all 0.3s ease;
        cursor: pointer;
        box-shadow: 0px 3px 3px -2px var(--boxShadowOne), 0px 3px 4px 0px var(--boxShadowTwo), 0px 1px 8px 0px var(--boxShadowThree);
    }

    .podium-card:hover {
        transform: translateY(-5px);
        border-color: var(--g555);
        box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    }

    .podium-card.second {
        order: 1;
    }

    .podium-card.first {
        order: 2;
        transform: scale(1.1);
        border: 3px solid #ffd700;
        background: linear-gradient(135deg, #fffbeb, #fef3c7);
        box-shadow: 0 0 20px rgba(255, 215, 0, 0.3), 0px 6px 6px -4px var(--boxShadowOne), 0px 6px 8px 0px var(--boxShadowTwo), 0px 2px 16px 0px var(--boxShadowThree);
        position: relative;
    }

    .podium-card.first::before {
        content: '';
        position: absolute;
        top: -3px;
        left: -3px;
        right: -3px;
        bottom: -3px;
        background: linear-gradient(45deg, #8b6e4a, #ffed4e, #ffd700, #8b6e4a);
        border-radius: 16px;
        z-index: -1;
        animation: borderGlow 3s ease-in-out infinite alternate;
    }

    @keyframes borderGlow {
        0% { opacity: 0.6; }
        100% { opacity: 1; }
    }

    .podium-card.first:hover {
        transform: scale(1.1) translateY(-5px);
    }

    .podium-card.third {
        order: 3;
    }

    .podium-avatar {
        width: 70px;
        height: 70px;
        border-radius: 50%;
        margin: 0 auto 1rem;
        display: block;
        object-fit: cover;
        border: 3px solid transparent;
        background-color: var(--fff);
        border-color: #ffd700;

    }

    .podium-card.first .podium-avatar {
        width: 80px;
        height: 80px;
    }


    .podium-rank {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        font-weight: bold;
        font-size: 0.9rem;
        margin-bottom: 1rem;
    }

    .podium-card.first .podium-rank {
        background: #ffd700;
        color: #000;
    }

    .podium-card.second .podium-rank {
        background: #c0c0c0;
        color: #000;
    }

    .podium-card.third .podium-rank {
        background: #cd7f32;
        color: #fff;
    }

    .podium-name {
        font-size: 1rem;
        font-weight: 500;
        margin-bottom: 0.25rem;
        color: var(--g555);
    }

    .podium-subtitle {
		color: var(--secondaryColor, #8b6e4a);

        font-size: 0.8rem;
    }

    /* Division Leaders */
    .divisions-section {
        margin-bottom: 3rem;
    }

    .section-title {
        font-size: 1.8rem;
        font-weight: 600;
        text-align: center;
        margin-bottom: 1.5rem;
        color: var(--g555);
    }

    .divisions-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 1.5rem;
        max-width: 800px;
        margin: 0 auto;
    }

    .division-card {
        background: var(--fff);
        border-radius: 12px;
        padding: 1.5rem;
        text-align: center;
        border: 1px solid var(--bbb);
        transition: all 0.3s ease;
        cursor: pointer;
        box-shadow: 0px 2px 2px -1px var(--boxShadowOne), 0px 2px 3px 0px var(--boxShadowTwo), 0px 1px 6px 0px var(--boxShadowThree);
    }

    .division-card:hover {
        transform: translateY(-3px);
        border-color: var(--g555);
        box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    }

    .division-avatar {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        margin: 0 auto 1rem;
        display: block;
        object-fit: cover;
        border: 2px solid #10b981;
        background-color: var(--fff);
    }

    .division-title {
        font-size: 0.9rem;
        color: #10b981;
        margin-bottom: 0.5rem;
        font-weight: 600;
    }

    .division-name {
        font-size: 1rem;
        font-weight: 500;
        margin-bottom: 0.25rem;
        color: var(--g555);
    }

    /* Toilet Bowl */
    .toilet-section {
        background: linear-gradient(135deg, #404040, #404040);
        border-radius: 12px;
        padding: 1rem;
        text-align: center;
        max-width: 300px;
        margin: 0 auto;
        border: 1px solid #772432;
        box-shadow: 0px 3px 3px -2px var(--boxShadowOne), 0px 3px 4px 0px var(--boxShadowTwo), 0px 1px 8px 0px var(--boxShadowThree);
    }

    .toilet-title {
        font-size: 1.1rem;
        color: #fff;
        margin: 0rem;
        font-weight: 600;
    }

    .toilet-avatar {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        margin: 0 auto 0.75rem;
        display: block;
        object-fit: cover;
        border: 2px solid #dc2626;
        background-color: var(--fff);
        cursor: pointer;
    }

    .toilet-name {
        font-size: 1rem;
        font-weight: 500;
        color: var(--g555);
        cursor: pointer;
        margin-bottom: 0.25rem;
    }

    .toilet-subtitle {
        color: #dc2626;
        font-size: 0.8rem;
    }

    .clickable {
        cursor: pointer;
    }

    :global(.curOwner) {
        font-size: 0.7em;
        color: var(--bbb);
        font-style: italic;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
        .podium-grid {
            grid-template-columns: 1fr;
            gap: 1rem;
        }

        .podium-card.first {
            order: 1;
            transform: none;
        }

        .podium-card.first:hover {
            transform: translateY(-5px);
        }

        .podium-card.second {
            order: 2;
        }

        .podium-card.third {
            order: 3;
        }

        .divisions-grid {
            grid-template-columns: 1fr;
            gap: 1rem;
        }

        .awards-title {
            font-size: 2rem;
        }
    }

    @media (max-width: 480px) {
        .awards-title {
            font-size: 1.8rem;
        }

        .podium-card {
            padding: 1rem;
        }

        .division-card {
            padding: 1rem;
        }

        .toilet-section {
            padding: 1.5rem;
        }
    }
</style>

<div class="awards-container">
    <!-- Header -->
    <div class="awards-header">
        <h1 class="awards-title">{year} Awards</h1>
        <p class="awards-subtitle">League Champions and Division Leaders</p>
    </div>

    <!-- Podium Section -->
    <div class="podium-section">
        <div class="podium-grid">
            <div class="podium-card second clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: second})}>
                <div class="podium-rank">2</div>
                <img src="{getAvatarFromTeamManagers(leagueTeamManagers, second, year)}" alt="Second Place" class="podium-avatar">
                <div class="podium-name">{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, second)}</div>
                <div class="podium-subtitle">Runner-up</div>
            </div>
            
            <div class="podium-card first clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: champion})}>
                <div class="podium-rank">1</div>
                <img src="{getAvatarFromTeamManagers(leagueTeamManagers, champion, year)}" alt="Champion" class="podium-avatar">
                <div class="podium-name">{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, champion)}</div>
                <div class="podium-subtitle">🏆 Champion</div>
            </div>
            
            <div class="podium-card third clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: third})}>
                <div class="podium-rank">3</div>
                <img src="{getAvatarFromTeamManagers(leagueTeamManagers, third, year)}" alt="Third Place" class="podium-avatar">
                <div class="podium-name">{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, third)}</div>
                <div class="podium-subtitle">Third Place</div>
            </div>
        </div>
    </div>

    <!-- Division Leaders -->
    {#if divisions && divisions.length > 0}
        <div class="divisions-section">
            <h2 class="section-title">Division Champions</h2>
            <div class="divisions-grid">
                {#each divisions as division}
                    {#if division.rosterID}
                        <div class="division-card clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: division.rosterID})}>
                            <img src="{getAvatarFromTeamManagers(leagueTeamManagers, division.rosterID, year)}" alt="{division.name} champion" class="division-avatar">
                            <div class="division-title">
                                {#if division.name}
                                    {division.name} Division
                                {:else}
                                    Regular Season Champion
                                {/if}
                            </div>
                            <div class="division-name">{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, division.rosterID)}</div>
                        </div>
                    {/if}
                {/each}
            </div>
        </div>
    {/if}

    <!-- Toilet Bowl -->
    {#if toilet}
        <div class="toilet-section">
            <h3 class="toilet-title">🏆 Longwell Cup</h3>
            <img src="{getAvatarFromTeamManagers(leagueTeamManagers, toilet, year)}" alt="Longwell Cup Winner" class="toilet-avatar clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: toilet})}>
            <div class="toilet-name clickable" on:click={() => gotoManager({year, leagueTeamManagers, rosterID: toilet})}>{@html getNestedTeamNamesFromTeamManagers(leagueTeamManagers, year, toilet)}</div>
        </div>
    {/if}
</div>