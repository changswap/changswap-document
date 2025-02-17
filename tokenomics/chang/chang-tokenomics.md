# CHANG Tokenomics

## **Emission rate** <a href="#emission-rate" id="emission-rate"></a>

### **Per block**

| **Metric**             | **Emission/block (CHANG)** | **Emission/day (CHANG)** |
| ---------------------- | -------------------------: | -----------------------: |
| Emission               |                         40 |                1,152,000 |
| Burned Weekly          |                     -25.75 |                 -787,600 |
| **Effective Emission** |               **<14.25\*** |            **364,400\*** |

\*Effective Emission is in fact slightly below this amount: an additional 45,000 CHANG per day is diverted from the amount allocated to the lottery, and burned (PID 137 - Details below).

In addition to the above, a dynamic amount of CHANG is also [minted to the Dev address](https://bkcscan.com/address/0xceba60280fb0ecd9a5a26a1552b90944770a4a0e#tokentxns) at a rate of 9.09%. This means that if 100 CHANG are harvested, then 9.09 CHANG is minted in addition and sent to the Dev Address.

{% hint style="info" %}
All CHANG minted to the Dev address is burned in the weekly burn and never enters circulation.

As such, we haven't included it in the above emission rate.
{% endhint %}

## Distribution <a href="#distribution" id="distribution"></a>

| Distributed to                 | Reward/block (% of emission) | Reward/block (total CHANG) |           Reward/day |
| ------------------------------ | ---------------------------: | -------------------------: | -------------------: |
| Farms                          |                       10.62% |                       4.25 |     122,400 (approx) |
| of which diverted and burned   |                              |                            |              -46,000 |
| Brewery Pools                  |                          25% |                         10 |     288,000 (approx) |
| **Total Daily CHANG Emission** |                              |                            | **364,400 (approx)** |

## **Other Deflationary Mechanics** <a href="#other-deflationary-mechanics" id="other-deflationary-mechanics"></a>

{% hint style="info" %}
The burning process is currently manual. [View burn transactions here](https://bkcscan.com/token/0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82?a=0x000000000000000000000000000000000000dead).
{% endhint %}

As well as the above, CHANG is also burned in the following ways:

* **0.05%** of every trade made on ChangSwap V2
* **100%** of CHANG sent to the Dev address
* **100%** of CHANG performance fees from IFOs
* **100%** of CHANG spent on Profile Creation and NFT minting
* **100%** of CHANG bid during Farm Auctions
* **20%** of CHANG spent on lottery tickets
* **45,000** CHANG per day (historically assigned to the lottery) (_The CHANG for this is generated by a farm - PID 137)_
* **3%** of every Prediction markets round is used to buy CHANG for burning
* **2%** of every yield harvest in the Auto CHANG Pool
* **2%** of every NFT sale on the NFT Market is used to buy CHANG for burning

## Why is the CHANG burn manual?

To hit the ground running, ChangSwap launched as an MVP (minimum viable product) with the MasterChef contract emitting 40 CHANG per block. For that reason, the early team didn't add additional functions such as the ability to customize the CHANG minting logic. As migrating to a new MasterChef would require a lot of time and effort, the team opted to reduce CHANG emissions instead through a manual burn process by creating two pools:

* Legacy Lottery Pool - burned CHANG from the lottery
* Burn Pool - burned CHANG per block

These pools work similarly to the farms, where the Chefs can adjust the percentage of the 40 CHANG per block allocated to it after each CHANG emission reduction vote.

{% hint style="warning" %}
On the day of the burn, the supply shown on the homepage might suddenly jump by several million CHANG.

Don't worry - **THIS CHANG NEVER ACTUALLY ENTERS CIRCULATION:**
{% endhint %}

This apparent jump is just because of how all the CHANG that's allocated for the burn is stored during the week.

The CHANG sent to both pools PID-137 and PID-138 are harvested before completing the weekly token burns, and this makes the Total Supply shown on the site jumping by \~6M. This is because pending CHANG isn’t registered in the Total Supply until it's harvested on the burn day. Once the token burn transaction is completed, the \~6M is shown in the Burned to Date.

## How to Confirm CHANG Supply for yourself

To confirm that the circulating CHANG supply shown on the ChangSwap homepage is correct,

1. Head to the CHANG token contract on BkcScan and [see how much CHANG is held by the Burn Address.](https://bkcscan.com/token/0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82#balances) That's the total amount of CHANG that's been burned (removed from circulation FOREVER, and impossible to ever retrieve).
2. Then, subtract this burned amount from the "Total Supply" that BkcScan shows.
3. This gives you the actual CHANG supply.

#### **Read more about CHANG's deflationary mechanics on the next page.** <a href="#read-more-about-changs-deflationary-mechanics-on-the-next-page" id="read-more-about-changs-deflationary-mechanics-on-the-next-page"></a>
