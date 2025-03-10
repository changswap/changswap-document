# 🚜 Yield Farming

![](../../.gitbook/assets/yieldfarms.png)

Yield Farms allow users to earn CHANG while supporting ChangSwap by staking LP Tokens.

Check out our [How to Use Farms guide](https://docs.changswap.com/products/yield-farming/how-to-use-farms) to get started with farming.

{% hint style="warning" %}
Yield farming can give better rewards than Brewery Pools, but it comes with a risk of **Impermanent Loss**. It’s not as scary as it sounds, but it is worth learning about the concept before you get started.
{% endhint %}

## Reward calculations

Yield Farm APR calculations include both:

* **LP rewards APR** earned through providing liquidity and;
* **Farm base rewards APR** earned staking LP Tokens in the Farm.

Why? Because when you stake your LP tokens in a farm to earn CHANG, you're still providing liquidity to the liquidity pool, so you earn LP rewards as well!

### Calculating Farm Base Reward APR

The **Farm Base APR** is calculated according to the farm multiplier and the total amount of liquidity in the farm -- this is the amount of CHANG distributed to the farm.

### Calculating LP Reward APR

WKUB/BUSD pair as example, we see these values:

**Liquidity:** $387.42M\
**Volume 24H:** $96.97M\
**Volume 7D:** 709.73M

* Calculate yearly fees
  * Use the 24H volume to calculate the **fee share** of liquidity providers in the pool (based on the 0.17% trading fee structure):\
    $96,970,000\*0.17/100 = **$164,849**
  * Next, use that **fee share** to estimate the projected **yearly fees** earned by the pool (based on the current 24h volume):\
    $164,849\*365 = **$60,169,885**
* We can now use the yearly fees to calculate the **LP rewards APR:** That's **yearly fees** divided by **liquidity:**\
  ($60,169,885/$387,420,000)\*100 = **15.53% LP reward APR**
