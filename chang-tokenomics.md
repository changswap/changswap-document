# CHANG Tokenomics

###  <a href="emission-rate" id="emission-rate"></a>

###  <a href="per-block" id="per-block"></a>

\*Effective Emission is in fact slightly below this amount: an additional 45,000 CHANG per day is diverted from the amount allocated to the lottery, and burned (PID 137 - Details below).

In addition to the above, a dynamic amount of CHANG is also [minted to the Dev address](https://bkcscan.com/address/0xceba60280fb0ecd9a5a26a1552b90944770a4a0e#tokentxns) at a rate of 9.09%. This means that if 100 CHANG are harvested, then 9.09 CHANG is minted in addition and sent to the Dev Address.

All CHANG minted to the Dev address is burned in the weekly burn and never enters circulation.

As such, we haven't included it in the above emission rate.

###  <a href="distribution" id="distribution"></a>

Reward/block (% of emission)

Reward/block (total CHANG)

of which diverted and burned

Total Daily CHANG Emission

###  <a href="other-deflationary-mechanics" id="other-deflationary-mechanics"></a>

As well as the above, CHANG is also burned in the following ways:

* 0.05% of every trade made on ChangSwap V2
* 100% of CHANG sent to the Dev address
* 100% of CHANG raised in IFOs
* 100% of CHANG spent on Profile Creation and NFT minting
* 100% of CHANG bid during Farm Auctions
* 20% of CHANG spent on lottery tickets
* 45,000 CHANG per day (historically assigned to the lottery) (The CHANG for this is generated by a farm - PID 137)
* 3% of every Prediction markets round is used to buy CHANG for burning
* 2% of every yield harvest in the Auto CHANG Pool
* 2% of every NFT sale on the NFT Market is used to buy CHANG for burning

###  <a href="why-is-the-chang-burn-manual" id="why-is-the-chang-burn-manual"></a>

To hit the ground running, ChangSwap launched as an MVP (minimum viable product) with the MasterChef contract emitting 40 CHANG per block. For that reason, the early team didn't add additional functions such as the ability to customize the CHANG minting logic. As migrating to a new MasterChef would require a lot of time and effort, the team opted to reduce CHANG emissions instead through a manual burn process by creating two pools:

* Legacy Lottery Pool (PID - 137) - burned CHANG from the lottery
* Burn Pool (PID - 138) - burned CHANG per block

These pools work similarly to the farms, where the Chefs can adjust the percentage of the 40 CHANG per block allocated to it after each CHANG emission reduction vote.

On the day of the burn, the supply shown on the homepage might suddenly jump by several million CHANG.

Don't worry - THIS CHANG NEVER ACTUALLY ENTERS CIRCULATION:

This apparent jump is just because of how all the CHANG that's allocated for the burn is stored during the week.

The CHANG sent to both pools PID-137 and PID-138 are harvested before completing the weekly token burns, and this makes the Total Supply shown on the site jumping by \~6M. This is because pending CHANG isn’t registered in the Total Supply until it's harvested on the burn day. Once the token burn transaction is completed, the \~6M is shown in the Burned to Date.

###  <a href="how-to-confirm-chang-supply-for-yourself" id="how-to-confirm-chang-supply-for-yourself"></a>

To confirm that the circulating CHANG supply shown on the ChangSwap homepage is correct,

1. Then, subtract this burned amount from the "Total Supply" that BkcScan shows.
2. This gives you the actual CHANG supply.

####  <a href="read-more-about-changs-deflationary-mechanics-on-the-next-page" id="read-more-about-changs-deflationary-mechanics-on-the-next-page"></a>