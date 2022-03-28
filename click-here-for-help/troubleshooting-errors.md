---
description: 常见错误信息。 使用侧边栏快速查找您的错误代码 ➡️
---

# 故障排除指南

## **交易相关问题**

### **INSUFFICIENT\_OUTPUT\_AMOUNT**

> The transaction cannot succeed due to error: ChangRouter: INSUFFICIENT\_OUTPUT\_AMOUNT. This is probably an issue with one of the tokens you are swapping.
>
> (交易由于此错误而无法成功：ChangRouter：INSUFFICIENT\_OUTPUT\_AMOUNT。问题可能出自您正在兑换的其中一个代币)

您正在尝试兑换代币，但您设置的滑点容限太低或您兑换的代币流动性太低。

{% tabs %}
{% tab title="解决方法" %}
1. 刷新页面，然后重试。
2. 尝试交易较小的金额。
3. 调高滑点容限：
   1. 点击兑换页面上的设置图标。
   2. 逐步调高滑点容限，然后重试。\
      ![](<../.gitbook/assets/image (9) (4) (2).png>)
4. 若还是不行，您可以尝试减少兑换金额的小数点位数。
{% endtab %}

{% tab title="原因" %}
**问题常见于尝试兑换流动性较低的代币时：**

换言之，您尝试兑换的代币，它的流动性池内有一个代币的数量不足以完成交易：有可能是因为该币的市值较低，或交易人数太少。

但是，您也有可能遇到无法出售的假币或诈骗币。 在这种情况下，ChangSwap 无法封锁该代币或返还资金。
{% endtab %}
{% endtabs %}

### **INSUFFICIENT\_A\_AMOUNT or INSUFFICIENT\_B\_AMOUNT**

> Fail with error 'ChangRouter: INSUFFICIENT\_A\_AMOUNT'
>
> (交易出现此错误导致失败: "ChangRouter: A代币不足")
>
> 或
>
> Fail with error 'ChangRouter: INSUFFICIENT\_B\_AMOUNT'
>
> (交易出现此错误导致失败: "ChangRouter: B代币不足")

您正在尝试从流动性池(LP)添加或解除流动性，但是该交易对中的其中一个代币不足。

{% tabs %}
{% tab title="解决方法" %}
**刷新页面，然后重试，或稍后重试。**

还是不行？

1. 点击流动性页面上的设置图标。
2.  逐步调高滑点容限，然后重试。

    ![](<../.gitbook/assets/image (9) (4) (2).png>)
{% endtab %}

{% tab title="原因" %}
该错误是由于尝试添加或解除流动性但其交易对中的A代币或B代币数量不足而引起的。

其中一个可能的情况是，当您的滑点容限设置太低时，价格更新太快导致。

![](https://lh5.googleusercontent.com/T1KMtz2ILDVHljGw1iLbIv0W1KVl7qXL8zU2nLFHkUvDb5oMw9mpUzzBwWmIBz15XDsxZ5w7wsaqAwCs\_pxdobz\_kY\_7BhcZhYtpqWuQGFs23DZq98-SVInlfsS07WzxFPLIYXHt)



![](https://lh5.googleusercontent.com/7aspaCCvDjzxbJxngqwgeq737LB3OUNcAs592QqlEkyrAOTfKsrt\_FAwpEylaIJhff5ZcYlzB\_r0v1JZwfj3j8Ah6jlUbRoMrAqVfTb3cwDI7B1i5HJtZSQOsTPrv7l7SaclC3BV)
{% endtab %}

{% tab title="给学霸的解决方法" %}
好的，您或许坚决要解决此问题。但除非您知道自己在做什么，否则我们真的不建议您这样做。

ChangSwap的网站目前没有解决此问题的简单方法：您需要直接调用智能合约。 您可以直接通过Router合约添加或解除流动性，同时将amountAMin或amountBMin设置为很小的数目。

### **批准并授权合约提取您的钱包里的LP代币**

浏览您要授权的LP代币合约地址。 \
以下示范例子是ETH/WKUB对：[https://bscscan.com/address/0x70d8929d04b60af4fb9b58713ebcf18765ade422](https://bscscan.com/address/0x70d8929d04b60af4fb9b58713ebcf18765ade422)

1. 选择 “**Write Contract”** (写入合约)**，**然后点击 “**Connect to Web3”** (连接至Web3)以连接您的钱包。\
   ![](https://lh6.googleusercontent.com/-\_sNkO1gcOOJXkduDEUzbExKE2mNxBOR0f86Lpp3BBuPbIcmAHsfuvpF-hKqRn4oID5QzdGkk\_1dTHkPuCmE50vpNNZxEqoM5nPmE\_12k3-8Q8YYoRYqJ\_VGjxJ03YPRuVQ1O5ME)
2. 在第一项**"1. approve"**，通过输入以下内容批准Router合约提取您的LP代币。输入完毕后点击 **Write** 按钮。
   1. spender (address): 输入Router合约地址
   2. value (uint256): -1

### 查询LP余额"balanceOf"

1. 选择 **“Read Contract”** (读取合约)
2. 在第五项 **"5. balanceOf"**，输入您的钱包地址然后点击 **Query** 按钮。
3. 记下显示的余额。这余额显示的格式是uint256。您的下一个步骤需要输入这余额。

![](<../.gitbook/assets/image (7).png>)

### 添加或解除流动性

浏览以下Router合约网址: [https://bscscan.com/address/0x05ff2b0db69458a0750badebc4f9e13add608c7f#writeContract](https://bscscan.com/address/0x05ff2b0db69458a0750badebc4f9e13add608c7f#writeContract)

1. 跟之前一样，选择 **“Write Contract”** 然后点击 **“Connect to Web3”**。
2. 寻找 **addLiquidity** 或 **removeLiquidity** (根据当下你想做的操作)
3. 输入LP的两个代币地址，即代币A与代币B的合约地址。
4. 在 **“liquidity (uint256)”** 这一栏位，输入您从之前的步骤获得的uint256格式LP余额(即"balanceOf")。
5. 设置低额的 **amountAMin** 或 **amountBMin**: 两个都尝试 “1” 这个值。
6. 在 **“to (address)”** 这一栏位输入您的钱包地址。
7. **Deadline** (截止时间)必须是大于执行此交易的纪元(epoch)时间。

![](<../.gitbook/assets/image (5).png>)

{% hint style="warning" %}
这可能会导致很高的滑点，并且如果被机器人抢跑，可能会导致您损失一些资金。
{% endhint %}
{% endtab %}
{% endtabs %}

### ChangRouter: EXPIRED

> The transaction cannot succeed due to error: ChangRouter: EXPIRED. This is probably an issue with one of the tokens you are swapping.
>
> (交易由于此错误而无法成功: ChangRouter: 逾期。 这可能是因为您正在兑换的一个代币存在某些问题)

再试一次，但是在交易产生后立即确认(即签名并往链上广播)该交易。&#x20;

发生这种情况是因为您在交易产生后，没有足够快地点击“确认”按钮，而是等到期限过后才进行签名与链上广播。&#x20;

### Chang: K

> The transaction cannot succeed due to error: Chang: K. This is probably an issue with one of the tokens you are swapping.

尝试更改「到」一栏的数量，让「（估计）」标志出现在「从」一栏中，然后立刻开始交易，保持该标志一直在「从」一栏。

这通常发生在含有自身交易手续费的代币上。

![](../.gitbook/assets/chang-k-error.png)

### Chang: TRANSFER\_FAILED

> The transaction cannot succeed due to error: execution reverted: Chang: TRANSFER\_FAILED.

在交易前，请确保您有额外 30% 数量的代币在您的钱包内。或者，尝试交易一个较少的数额。如果您想卖出最大可能的数目，请尝试设置数量为总数的 70% 或者 69%，不要设置为 100%。这个问题导致的原因是类似 tDoge 和 tBTC 代币所实行的「实时恢复性调整」。\
[点击此处了解弹性调整代币](https://btcst.medium.com/stp-8-restorative-rebase-b4fbbdfd96c)。

另一个可能的原因是：该恶意代币的项目方暂停了所有的交易，或者设置为仅允许买入不允许卖出，或者仅允许部分地址卖出。任何人都可以发行 KEP-20 代币并在 ChangSwap 上交易。所以，在交易任何代币前，请充分做好调查，谨防受骗上当。如果您尝试卖出但失败的代币来自于空投，这很可能是诈骗。请不要进行任何授权操作，更不要跟随任何提示跳转到第三方网站操作，您钱包内的资产将由被盗风险。

### Transaction cannot succeed

尝试减少交易的数量，点击设置按钮并增加滑点容差，然后重试。导致该错误的原因是流动性太少。

### **Price Impact too High**

尝试减少交易的数量，点击设置按钮并增加滑点容差，然后重试。导致该错误的原因是流动性太少。

### estimateGas failed

> This transaction would fail. Please contact support

{% tabs %}
{% tab title="解决方法" %}
**如果您是在解除与 KUB 组合的流动性对时遇到该错误：**

请选择「接收 WKUB」然后重试。

**如果您是在交易时遇到该错误：**

请联系您交易的代币发行方，这个问题只能由他们解决。
{% endtab %}

{% tab title="原因" %}
**在交易时遇到该错误，是因为发行方将 V1 ChangSwap 交易路由写死在了他们的代币合约中。**

虽然这种做法非常不明智，但项目方们这样做的原因可能是因为他们的代币经济模型所需。他们的代币，通常会在交易时扣除一部分百分比，并用于添加流动性。

这类受影响的项目代币不太可能会在 V2 交易路由上正常工作，他们需要创建一个新的代币合约，并指向我们的新交易路由地址，然后让现有的代币持有者迁移到新合约。

我们强烈建议任何投放该类代币的项目方做好宣传，以防用户在 V2 上添加流动性。

最新的[最新的交易路由地址：](https://bscscan.com/address/0x10ED43C718714eb63d5aA57B78B54704E256024E)\
[https://bscscan.com/address/0x10ED43C718714eb63d5aA57B78B54704E256024E](https://bscscan.com/address/0x10ED43C718714eb63d5aA57B78B54704E256024E)
{% endtab %}
{% endtabs %}

### Cannot read property 'toHexString' of undefined

> "Unknown error: "Cannot read property 'toHexString' of undefined"

在交易时，上链操作出错并显示该错误代码。这类错误常见于使用 Trust 钱包的移动设备。

{% tabs %}
{% tab title="解决方法" %}
1. 点击设置按钮，增加滑点容差并重试。
2. 若上述方法没用，请尝试使用别的钱包软件，导入相同助记词并重试。例如 SafePal。
{% endtab %}

{% tab title="原因" %}
**这通常发生在使用 Trust 交易代币，但滑点容差不够的情况下。**

发生该问题的详细原因仍在调查中。
{% endtab %}
{% endtabs %}

### **Execution reverted: TransferHelper: TRANSFER\_FROM\_FAILED.**

> The transaction cannot succeed due to error: execution reverted: TransferHelper: TRANSFER\_FROM\_FAILED.

{% tabs %}
{% tab title="解决方法" %}
1. 请检查您有足够的代币余额用于交易。
2. 请确保该代币授权于交易路由地址的数量，大于您正在尝试交易的数量。若您不确定，请尝试取消、并重新授权。
{% endtab %}

{% tab title="原因" %}
该错误的常见原因为代币授权额度不足，或者没有足够的余额用于交易。

若您正在交易的代币有「弹性调整机制」，例如 tDoge 或 tBTC。请先 [点击此处](https://btcst.medium.com/stp-8-restorative-rebase-b4fbbdfd96c) 了解他们的机制。
{% endtab %}
{% endtabs %}

## **酿酒池相关问题**

### KEP20: burn amount exceeds balance

> Fail with error 'KEP20: burn amount exceeds balance'
>
> (交易出现此错误导致失败: “KEP20: 销毁数量超出余额”)

您的钱包中没有足够的 BREWERY 代币，无法从 CHANG-CHANG 池中解除质押以提出 CHANG。

{% tabs %}
{% tab title="解决方法(一)" %}
**购买跟您想解除质押 CHANG 同等数量的 BREWERY 代币。**

1. 在交易所上购买 BREWERY 代币。如果您想解除质押 100 个 CHANG，您需要购买对应数量（100 个）BREWERY 代币。
2. 再次尝试解除质押。
{% endtab %}

{% tab title="解决方法(二)" %}
如果还是失败，您可以直接调用合约的「紧急提取」(emergencyWithdraw) 以紧急解除质押您正在质押的代币。

1. 浏览以下网址：\
   [https://bscscan.com/address/0x73feaa1eE314F8c655E354234017bE2193C9E24E#writeContract ](https://bscscan.com/address/0x73feaa1eE314F8c655E354234017bE2193C9E24E#writeContract)
2. 点击 **“Connect to Web3”** （连接至 Web3）以连接您的钱包。\
   ![](https://lh6.googleusercontent.com/-\_sNkO1gcOOJXkduDEUzbExKE2mNxBOR0f86Lpp3BBuPbIcmAHsfuvpF-hKqRn4oID5QzdGkk\_1dTHkPuCmE50vpNNZxEqoM5nPmE\_12k3-8Q8YYoRYqJ\_VGjxJ03YPRuVQ1O5ME)
3. 在第 4 项：**“4. emergencyWithdraw”**，输入“0”，然后点击 **Write** 按钮。

虽然紧急提取成功让您解除质押，但这也会导致您失去任何尚未收割的奖励代币（即 CHANG）收益。

{% hint style="warning" %}
**紧急提出会导致您失去尚未收割的奖励代币。**
{% endhint %}
{% endtab %}

{% tab title="原因" %}
若想防止这种情况再次发生，**请不要出售您的 BREWERY 代币**。 您仍然需要 BREWERY 代币来帮助您从「质押 CHANG 获取 CHANG」酿酒池中解除质押。

发生此错误的原因是您已经出售或转账了您的 BREWERY 代币。 当您在 CHANG-CHANG 酿酒池中质押您的 CHANG 时，BREWERY 会根据 CHANG 的数量，以 “1:1” 的比例被铸造出来。在调用 leavesStaking （即解除 CHANG 质押）函数时，合约会销毁与 CHANG 数量同等的 BREWERY 代币数量。因此，如果您没有足够的 BREWERY 代币，您将不能成功解除质押。

![](https://lh4.googleusercontent.com/KchAcnM6cpX2BotEGppAxPAnY4Xbona6yI6ZWg9FlUUBfPi\_YO9ulM1s6htXJVXMzEwl0Uxcvdk8o4yhI7ar5g0TRpLVFjkS4YLKL7FS8Z4uFqeC37sw-TIkrPr7BCZQVpuD-5jO)
{% endtab %}
{% endtabs %}

### Out of Gas error

> Warning! Error encountered during contract execution \[out of gas]
>
> (警告！合约执行过程中遇到错误\[矿工费已用尽])

您设置的**Gas Limit**(矿工费限制/网络费用限制)过低。

{% tabs %}
{% tab title="解决方法" %}
在点击交易确认前，手动调高 **Gas 限制（**注意！不是 Gas 价格！）

一般而言，限制设为 200000 就足够了。

![](<../.gitbook/assets/image (2).png>)

以上的例子取自 Metamask 截图。 如果不确定如何设置 Gas 限制，请查看您钱包的文档。
{% endtab %}

{% tab title="原因" %}
基本上，您的钱包（Metamask, Trust Wallet等）无法使用预估的 Gas 限制，完成其尝试执行的操作。

您的钱包所建议的 Gas 限制太低，因此在合约函数调用完成之前，矿工费已用尽。\

{% endtab %}
{% endtabs %}

### KEP20: transfer amount exceeds allowance

> Fail with error 'KEP20: transfer amount exceeds allowance'

{% tabs %}
{% tab title="Solution" %}
1. 使用 unrekt.net 解除您正在操作酿酒池的合约授权（您可在各酿酒池详情中找到它们的地址）
2. 重新授权（点击「启用」）合约，不要更改默认的授权数量。
3. 重试您正在尝试的操作。
{% endtab %}

{% tab title="Reason" %}
该错误的原因是您在最初授权时，设置了一个过低的数量。后期操作时，操作的代币数量超过了剩余授权允许数目。
{% endtab %}
{% endtabs %}

### KEP20: transfer amount exceeds balance

> Fail with error 'KEP20: transfer amount exceeds balance'
>
> (交易出现此错误导致失败: “KEP20: 转出数额超出余额”)

您正试图从奖励代币不足的酿酒池中解除质押。

{% tabs %}
{% tab title="解决方法" %}
您可以直接调用合约的「紧急提取」 (emergencyWithdraw) 以对您质押着的代币解除质押。

1. 查找您要解除质押的酿酒池的合约地址。您可以在各酿酒池详情中找到他们的 BscScan 页面。
2. 点击进入，或浏览 [https://bscscan.com/](https://bscscan.com/address/0x73feaa1eE314F8c655E354234017bE2193C9E24E#writeContract) 然后在搜索栏中输入酿酒池的合约地址。
3. 选择 **“Write Contract”（**写入合约）。
4. 点击 **"Connect to Web3"（**连接 Web3）以便连接您的钱包。![](https://lh6.googleusercontent.com/-\_sNkO1gcOOJXkduDEUzbExKE2mNxBOR0f86Lpp3BBuPbIcmAHsfuvpF-hKqRn4oID5QzdGkk\_1dTHkPuCmE50vpNNZxEqoM5nPmE\_12k3-8Q8YYoRYqJ\_VGjxJ03YPRuVQ1O5ME)
5. 在第4项：**“4. emergencyWithdraw”**，点击 **Write** 按钮。

虽然紧急提取允许您成功解除质押，但这也会导致您失去任何尚未收割的奖励代币。

{% hint style="warning" %}
**紧急提出会导致您失去尚未收割的奖励代币。**
{% endhint %}
{% endtab %}

{% tab title="原因" %}
当您尝试从已结束很久的酿酒池中解除质押时，一般会出现此错误。其原因是因为该池中没有足够的奖励代币供您收割。 这会导致解除质押操作失败。
{% endtab %}
{% endtabs %}

## 其他错误

### Provider Error

> Provider Error\
> No provider was found
>
> 提供商错误\
> 未找到提供商

该错误常见于：点击「浏览器钱包插件连接」，例如 MetaMask 或 Binance Chain Wallet，但您未安装插件时。

{% tabs %}
{% tab title="解决方法" %}
安装浏览器插件，并正确连接。请查阅我们关于 [如何正确连接钱包的教程](https://docs.changswap.finance/get-started/connection-guide)。
{% endtab %}
{% endtabs %}

### Unsupported Chain ID

不支持的链 ID

请更换您的钱包网络（区块链）到 Binance Smart Chain （Bitkub链），如果您不知道如何切换，请查阅您的钱包指南或教程。

### 购买 SAFEMOON 或类似分红代币时遇到错误

要交易 SAFEMOON，您必须点击设置按钮，**并设置您的滑点容差至 12% 或更高。**\
这是因为 **SafeMoon 每一个交易都会收取 10% 的税：**

* 5% 手续费 = 分红给当前所有持有者
* 5% 手续费 = 用于添加流动性

这也是为什么您在交易时可能不会收到预计数量的代币的原因。\
阅读更多关于 [如何交易 SafeMoon](https://community.trustwallet.com/t/how-to-buy-safemoon/155742) 。

### Internal JSON-RPC errors

> "MetaMask - RPC Error: Internal JSON-RPC error. estimateGas failed removeLiquidityETHWithPermitSupportingFeeOnTransferTokens estimateGas failed removeLiquidityETHWithPermit "

常见于使用 MetaMask 解除部分代币的流动性时，具体原因未知，请尝试用别的钱包 App 进行该操作。

> Internal JSON-RPC error. { "code": -32000, "message": "insufficient funds for transfer" } - Please try again.

您没有足够的 KUB 来支付交易矿工费，您的钱包需要更多 KEP-20 网络的 KUB。

### Error: \[ethjs-query]

> Error: \[ethjs-query] while formatting outputs from RPC '{"value":{"code":-32603,"data":{"code":-32000,"message":"transaction underpriced"}}}"

在确认交易前，增加 Gas 限制。请查看您钱包的指南，了解如何增加 Gas 限制（注意！不是 Gas 价格）

> Swap failed: Error: \[ethjs-query] while formatting outputs from RPC '{"value":{"code":-32603,"data":{"code":-32603,"message":"handle request error"}}}'

原因未知。请尝试以下步骤并重试：

1. 增加 Gas 限制
2. 增加滑点容差
3. 清除缓存及交易记录
