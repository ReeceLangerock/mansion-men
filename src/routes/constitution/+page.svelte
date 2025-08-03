<script>
    // Variables for scrolling to sections via the Table of Contents
    let one, oneOne, oneTwo;
    let two, twoOne, twoTwo;
    let three, threeOne, threeTwo, threeThree;
    let four, fourOne, fourTwo;
    let five, fiveOne, fiveTwo, fiveThree, fiveFour, fiveFive;
    let six, sixOne, sixTwo;

    // Function to smoothly scroll to a selected section
    const goToSection = (section) => {
        if (!section) return;
        const top = section.getBoundingClientRect().top + window.pageYOffset;
        window.scrollTo({left: 0, top, behavior: 'smooth'});
    }
</script>

<style>
    .constitution {
        position: relative;
        z-index: 1;
        width: 92%;
        max-width: 800px;
        margin: 8em auto 10em;
    }

    h1 {
        font-size: 2em;
        line-height: 1.2em;
        text-align: center;
        margin: 2em 0 1.5em;
    }

    h2 {
        font-size: 1.5em;
        line-height: 1.2em;
    }

    h3 {
        text-decoration: underline;
        font-size: 1.3em;
        line-height: 1.2em;
    }

    h4 {
        text-decoration: underline;
        margin-left: 2em;
        font-size: 1.2em;
        line-height: 1.2em;
    }

    h5 {
        margin-left: 4em;
        font-size: 1.1em;
        line-height: 1.1em;
        text-decoration: underline;
    }

    .subBlock {
        margin-left: 2.4em;
    }

    .sectionHeading {
        margin: 4em 0 1.5em;
    }

    .subSectionHeading {
        margin: 1.5em 0 1.5em;
    }
    
    .p_subSectionHeading {
        margin: 1.5em 0 1.5em;
        font-weight: bold;
    }

    .underscore {
        text-decoration: underline;
    }

    .right {
        text-align: right;
    }

    .positionMaximums td {
        min-width: 3em;
    }

    .noUnderscore {
        text-decoration: none;
    }

    .clickable {
        cursor: pointer;
    }

    .clickable:hover {
        color: #00316b;
    }

    p {
        color: #777;
        margin-bottom: 1em;
    }

    li {
        color: #777;
        margin-bottom: 0.5em;
    }
</style>

<div class="constitution">
    <h1 class="noUnderscore">Mansion Men League Bylaws</h1>
    
    <h2 class="noUnderscore">TABLE OF CONTENTS</h2>
    
    <h3 class="noUnderscore clickable" on:click={() => goToSection(one)}>Section 1: Governance</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(oneOne)}>1.1 Preamble & Membership</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(oneTwo)}>1.2 Amending Bylaws</h4>
    
    <h3 class="noUnderscore clickable" on:click={() => goToSection(two)}>Section 2: League Finances</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(twoOne)}>2.1 Buy-in</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(twoTwo)}>2.2 Payouts</h4>
    
    <h3 class="noUnderscore clickable" on:click={() => goToSection(three)}>Section 3: League Year & Playoffs</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(threeOne)}>3.1 League Year</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(threeTwo)}>3.2 Championship Tournament</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(threeThree)}>3.3 Consolation Tournament</h4>
    
    <h3 class="noUnderscore clickable" on:click={() => goToSection(four)}>Section 4: The Draft</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fourOne)}>4.1 Draft Format</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fourTwo)}>4.2 Determining Draft Position</h4>

    <h3 class="noUnderscore clickable" on:click={() => goToSection(five)}>Section 5: Keepers</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fiveOne)}>5.1 General Rules</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fiveTwo)}>5.2 Franchise Player</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fiveThree)}>5.3 Non-Franchise Rookies</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fiveFour)}>5.4 Previously Undrafted Players</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(fiveFive)}>5.5 General Clarifications</h4>

    <h3 class="noUnderscore clickable" on:click={() => goToSection(six)}>Section 6: Transactions</h3>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(sixOne)}>6.1 Free Agency</h4>
        <h4 class="noUnderscore clickable" on:click={() => goToSection(sixTwo)}>6.2 Trades</h4>
    
    <hr />
    
    <h2 class="sectionHeading" bind:this={one}>Section 1: Governance</h2>
    
    <h3 class="subSectionHeading" bind:this={oneOne}>1.1 Preamble & Membership</h3>
    <p>All 12 of the following individuals (Charles Coxe, Kevin Dobkin, Jason Knaak, Jeffery Douglas Langefeld, Stephan Langerock, James Ouska, Sean Quill, Matthew Reschke, Bryan Steger, Michael Unverricht, Alex Warner and Thomas Ward III) hereby agree to participate perpetually in a competitive fantasy football keeper league.</p>
    
    <h3 class="subSectionHeading" bind:this={oneTwo}>1.2 Amending Bylaws</h3>
    <ul>
        <li>Offseason changes to this document shall be made according to the simple majority decision of all participating individuals. If a vote results in a tie, it shall equate to an unsuccessful change to the document.</li>
        <li>In-season changes to this document shall only occur when there is a consensus vote, or if some voters abstain and all participating voters agree.</li>
    </ul>

    <h2 class="sectionHeading" bind:this={two}>Section 2: League Finances</h2>

    <h3 class="subSectionHeading" bind:this={twoOne}>2.1 Buy-in</h3>
    <p>The buy-in for the Mansion Men Fantasy Football League will be increased to $150, effective for the 2015 league year.</p>
    
    <h3 class="subSectionHeading" bind:this={twoTwo}>2.2 Payouts</h3>
    <p>The total prize pool of $1,800 is distributed as follows:</p>
    <ul>
        <li><strong>Weekly Point Champ - $25/week ($325 total):</strong> Each regular season week (13 total) will have a $25 payout to the team who scores the most total points. Ties will split.</li>
        <li><strong>Top Regular Season Record - $275</strong></li>
        <li><strong>Regular Season Points Champ - $175</strong></li>
        <li><strong>Playoff Points Championship - $100:</strong> This will go to the team that accumulates the most total points in all playoff matchups. All 12 teams are eligible. Ties split.</li>
        <li><strong>League Tournament Champ - $550</strong></li>
        <li><strong>League Tournament 2nd - $225</strong></li>
        <li><strong>League Tournament 3rd - $150</strong></li>
    </ul>

    <h2 class="sectionHeading" bind:this={three}>Section 3: League Year & Playoffs</h2>

    <h3 class="subSectionHeading" bind:this={threeOne}>3.1 League Year</h3>
    <p>The League Year shall commence once all owners have a complete roster and all individuals have agreed there are no amendments to be made to this document, or at the beginning of the 1st game of the 1st week of the NFL Regular Season, whichever is sooner. The League Champion shall be decided at the conclusion of the 16th week of the NFL Regular Season.</p>
    <p>The first 13 weeks shall make up the Regular Season. The final 3 weeks (14, 15, 16) shall consist of a Championship Tournament and a Consolation Tournament.</p>

    <h3 class="subSectionHeading" bind:this={threeTwo}>3.2 Championship Tournament</h3>
    <p>The Championship Tournament shall consist of the 6 teams with the best Regular Season record. Tiebreaker is total points scored. The teams with the 2 best records shall have a bye week in the first round. Seeding is 1 through 6 based on record.</p>
    <p class="p_subSectionHeading noUnderscore">Championship Tournament Bracket:</p>
    <ul>
        <li><strong>Round 1 (NFL Week 14):</strong><br/>#3 seed vs #6 seed<br/>#4 seed vs #5 seed</li>
        <li><strong>Round 2 (NFL Week 15):</strong><br/>#1 seed vs Lowest Remaining Seed<br/>#2 seed vs Highest Remaining Seed</li>
        <li><strong>Championship (NFL Week 16):</strong><br/>One Remaining Team vs Other Remaining Team</li>
    </ul>
    <p>The winner of the Championship matchup is the Mansion Men League Champion. There will be additional matchups to determine 3rd-6th places.</p>

    <h3 class="subSectionHeading" bind:this={threeThree}>3.3 Consolation Tournament</h3>
    <p>The Consolation Tournament shall consist of the 6 teams who do not participate in the Championship Tournament. These 6 teams shall participate in a tournament that is logistically identical to the Championship Tournament, where the team with the best regular season record (among this group) is the #1 seed and the team with the worst record is the #6 seed.</p>

    <h2 class="sectionHeading" bind:this={four}>Section 4: The Draft</h2>

    <h3 class="subSectionHeading" bind:this={fourOne}>4.1 Draft Format</h3>
    <p>The league shall use a 16-round snake style draft. Each owner must draft a roster which shall satisfy the requirements of a starting lineup (meaning must select at least 1 Kicker and 1 Def/ST).</p>

    <h3 class="subSectionHeading" bind:this={fourTwo}>4.2 Determining Draft Position</h3>
    <p>Draft position is determined on a year-by-year basis by allowing teams to choose their draft slot for the following season. The order in which teams get to choose is determined by the prior season's playoff results:</p>
    <ul>
        <li>The winner of the Consolation Tournament will be the first to choose their draft position.</li>
        <li>The 2nd place finisher of the Consolation Tournament will be the second to choose.</li>
        <li>...This continues down to the 6th place finisher in the Consolation Tournament, who is sixth to choose.</li>
        <li>The 6th place finisher in the Championship Tournament will be the seventh to choose.</li>
        <li>...This continues in reverse order of finish, until finally the League Champion fills in the last remaining draft position.</li>
    </ul>

    <h2 class="sectionHeading" bind:this={five}>Section 5: Keepers</h2>
    
    <h3 class="subSectionHeading" bind:this={fiveOne}>5.1 General Rules</h3>
    <p>Each team may keep up to 4 players from one League Year to the next. The cost to "protect" a player is the round in which they were drafted in the previous year, minus 2. For example, a player drafted in the 10th round would cost an 8th round pick to keep.</p>
    
    <h3 class="subSectionHeading" bind:this={fiveTwo}>5.2 Franchise Player</h3>
    <p>If a team drafts a rookie in the 1st round, that player gains "Franchise Player" status for that team only. This allows the player to be protected in the 16th round of all subsequent drafts.</p>
    <p>Franchise Player status is surrendered, and never regained, immediately and indefinitely, at the moment the player leaves the roster of the initial, drafting, team for any reason (trade, drop, etc.).</p>
    <h5 class="noUnderscore">Surrendered Franchise Player Amendment (7/31/14):</h5>
    <div class="subBlock">
        <p>If a team with a Franchise Player drafts a new rookie in the 1st round, they have two options:</p>
        <ol>
            <li>Continue to protect the original Franchise Player. The new rookie is unprotectable.</li>
            <li>Use the Franchise status on the new rookie. The previous Franchise Player's status is "surrendered".</li>
        </ol>
        <p>A surrendered Franchise Player's new keeper cost is calculated as: Round 16 - (3 x Years Protected). So if he was protected for 2 seasons, he now costs a 10th round pick (16 - (3*2) = 10).</p>
        <ul>
            <li>If the original team keeps that player, his cost increases by 3 rounds each subsequent year (e.g., 10th -> 7th -> 4th).</li>
            <li>If another team acquires him, his cost increases by 2 rounds each year (the standard rule).</li>
        </ul>
    </div>

    <h3 class="subSectionHeading" bind:this={fiveThree}>5.3 Non-Franchise Rookies</h3>
    <p>When a rookie is drafted in any round other than the first, he has +1-round protectability for his initial, drafting team only. This means he costs the round he was drafted in, minus one. e.g., Unvy drafted Rookie Tyler Eifert in the 10th round of the 2013 draft and could protect him in the 9th Round of the 2014 draft.</p>
    <p>This +1 status is surrendered in the same way Franchise status is (if traded or dropped). Once surrendered, he is protectable under the standard -2 round rule for all teams. e.g., Reece drafted Rookie Cordarelle Patterson in the 11th round, but he changed teams during the season. He surrendered his +1 status and was protectable in the 9th round for the 2014 draft.</p>

    <h3 class="subSectionHeading" bind:this={fiveFour}>5.4 Previously Undrafted Players</h3>
    <p>Players who were not selected in the draft immediately preceding the current League Year shall be "Protectable" in the 10th round of the next year’s draft and would follow the standard +2 rule in all subsequent drafts (updated 8/7/2017).</p>

    <h3 class="subSectionHeading" bind:this={fiveFive}>5.5 General Clarifications</h3>
    <p>If a player is not on any team's roster at the conclusion of the League Year, he cannot be protected and enters the draft pool.</p>
    <p>Unless otherwise applicable, a player's keeper cost is determined by the round in which their name appears on the Draft Board of the most recent draft, regardless of how they were acquired (drafted or kept).</p>

    <h2 class="sectionHeading" bind:this={six}>Section 6: Transactions</h2>

    <h3 class="subSectionHeading" bind:this={sixOne}>6.1 Free Agency</h3>
    <p>Players are acquired via a waiver bid process. Each team is allocated $133 waiver dollars at the start of the season. Dollars may be traded, but no new dollars are added to the league pool. Waiver dollars do not carry over to the next season.</p>
    <p>Every day (except Tuesdays), teams can place bids on free agents. The deadline for bids is 12pm Eastern Time. The highest bidder is awarded the player. A player released to add the new player becomes available at the next waiver deadline.</p>

    <h3 class="subSectionHeading" bind:this={sixTwo}>6.2 Trades</h3>
    <p>Players involved in trades will exchange rosters at the time the trade is executed and approved.</p>
    <h5 class="noUnderscore">Expediting Trades:</h5>
    <div class="subBlock">
        <p>A trade can be expedited and pushed through immediately (bypassing the standard review period) if an email vote (or other reasonable means) results in a simple majority of team owners being in favor of expediting it.</p>
        <p><i>A historical note to remember when voting on expediting trades: Half of the players that have been exchanged in expedited trades, from the time of the League's inception to the date of this memo, remained eligible for transaction under the automatically built in 2 day review period. The other 50% (or less) of the players in the trade were delaying the trade from being automatically processed until the following week of competition. (10/21/2016)</i></p>
    </div>
</div>