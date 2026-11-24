# VPS Pay With Crypto: Which Coin and Network, How Much to Top Up, and Where Evoxt's Plans Land (Full Price Table)

Most failed crypto VPS orders don't fail because the host refuses coins. They fail inside the checkout: the wrong network selected, an amount that arrives short because the exchange took its withdrawal fee first, a rate window that closed while the transaction was still confirming. Evoxt accepts Bitcoin and USDt on Tron next to cards and PayPal, and its cheapest plan is $2.99/month, so paying a VPS with crypto is possible there. What decides whether your order goes through is the sequence you follow and the amount you actually send.

> **Most readers:** Evoxt VM-1 at $5.99/month, with one core, 2 GB RAM, 20 GB storage and 500 GB monthly transfer. Weekly offsite backup is included on every plan. That size handles a small Docker host, a WireGuard node, a monitoring box or a low-traffic site. Running one lightweight service and nothing else? VM-0.75 at $4.99 with 1 GB RAM is the cheaper call.
>
> 👉 [Check Evoxt's current plan prices and pick a size](https://bit.ly/EvoXt)

## Evoxt's full plan list

All eleven plans on Evoxt's pricing page, in USD, billed monthly.

| Plan | vCPU / RAM | Storage | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 core / 512 MB | 5 GB | 250 GB | **$2.99/mo** | [Choose VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 core / 1 GB | 10 GB | 250 GB | **$4.99/mo** | [Choose VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 core / 2 GB | 20 GB | 500 GB | **$5.99/mo** | [Choose VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 cores / 2 GB | 20 GB | 500 GB | **$6.95/mo** | [Choose VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 cores / 4 GB | 30 GB | 1000 GB | **$11.99/mo** | [Choose VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 cores / 4 GB | 30 GB | 1000 GB | **$14.99/mo** | [Choose VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 cores / 8 GB | 60 GB | 2000 GB | **$23.99/mo** | [Choose VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 cores / 8 GB | 60 GB | 2000 GB | **$29.99/mo** | [Choose VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 cores / 16 GB | 80 GB | 3000 GB | **$47.99/mo** | [Choose VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 cores / 16 GB | 80 GB | 3000 GB | **$60.95/mo** | [Choose VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 cores / 32 GB | 100 GB | 5000 GB | **$95.99/mo** | [Choose VM-16](https://bit.ly/EvoXt) |

The pricing page quotes CPU as "up to 6.0 GHz" on every tier and lists weekly backup as standard. It does not state the storage medium, so if disk type matters to your workload, confirm it before ordering rather than assuming NVMe.

A few things the table doesn't show. Billing runs from monthly up to three years, and Evoxt lets you top up account credit and have the system apply it to future invoices, which is the mechanism that makes crypto practical there. The client area also exposes floating IPs, a firewall you configure without logging into the VM, VM cloning, browser VNC and backups.

Where the money goes is a separate question from the price column. VM-1.5 costs $0.96/month more than VM-1 and gives you a second core. VM-3 costs $3.00 more than that and doubles cores again while keeping RAM flat at 4 GB. If you're choosing blind, the useful split is cores versus RAM: 1 GB plans suit a single lightweight daemon, 4 GB plans suit a small database or a couple of containers, and anything past VM-6 is priced for sustained multi-core work rather than burst.

## Paying in crypto, step by step

Evoxt's pricing page names Bitcoin and USDt on Tron as the crypto options. The paid flow follows the pattern most hosts in this segment use:

1. Open the client area and add funds to your account credit.
2. Select the coin at checkout.
3. The page returns a wallet address and a QR code.
4. Send the exact amount, on the network shown, from a wallet you control.
5. Once the transaction confirms on-chain, the balance updates and you deploy the VM from the dashboard, choosing region and image.

The part worth internalising is step 5: credit lands after confirmation, not after you press send. Bitcoin confirmations typically run 10 to 30 minutes depending on mempool conditions; USDT on Tron usually clears faster and costs less in fees. If you're deploying to a deadline, the stablecoin on Tron is the option that gets you a running server soonest.

One caveat on which coins are actually live. Evoxt's own pages aren't perfectly consistent: the pricing-page FAQ names Bitcoin and USDt on Tron, while a third-party tracker quotes an Evoxt homepage line mentioning Litecoin and Ethereum, and states that USDT and USDC are absent from the documentation it reviewed. Rather than guess which page is stale, open the client area and read the coin list on the payment screen. That list is the only authoritative answer at the moment you pay.

## Four places a crypto VPS payment goes wrong

### 1. Coin and network have to match

USDT exists on Tron, Ethereum, BNB Chain, Solana and more. Evoxt specifies Tron, which in practice means TRC-20. ERC-20 USDT sent to a Tron deposit address is a different asset on a different chain: the receiving system can't match it to your invoice, and recovery depends on someone manually intervening. The same trap exists at every host. Infrawire's payment page puts it as sending the coin shown on the network shown; that sentence is the whole rule.

### 2. The rate window

Most processors lock the crypto amount for a short window, commonly 20 minutes with an on-screen countdown. Inside it, the number is fixed. Send after it closes and the rate is no longer locked, so the amount may no longer be enough. Not every host works this way: Infrawire keeps the payment link valid for 12 hours and lets a second transaction complete an underpayment inside that window. Check the countdown on whichever checkout you land on, because a 20-minute window and a 12-hour one demand completely different behaviour if your exchange holds withdrawals for review.

### 3. What arrives versus what you send

This is the most common cause of an underpayment, and it has nothing to do with arithmetic. Exchanges and some wallets deduct their withdrawal fee from the amount you type. You send 0.001 BTC; 0.00094 arrives. Match the amount that will *land*, not the amount that leaves. If your exchange shows a "recipient gets" field, that's the number to align with the checkout total. The total displayed on the payment page usually already includes the processor's service fee, so send exactly what's shown.

### 4. Refund edges

Processor handling of mistakes is fairly standardised, and knowing it in advance saves a support ticket:

| What happened | What the processor usually does | What you do |
| --- | --- | --- |
| Underpaid, page still open | Shows what arrived and what's still due | Send the difference before the window closes |
| Underpaid, page expired | Offers a refund form; tiny shortfalls may still be accepted | Request a refund; amounts under €3 are typically not refunded |
| Overpaid | Completes the order, offers a refund form for the excess | Enter wallet address and network; an excess smaller than the network fee can't be returned |
| Paid after expiry | May complete automatically, otherwise refund | Use the form or start a new payment |
| Wrong coin sent | Can't match it to the order | Request a return from the same checkout page using the transaction hash |

Keep the checkout link, the order ID and the TXID until the credit shows. Support asks for all three.

Evoxt doesn't publish which processor handles its crypto payments, so treat the table above as the house rules you should expect to meet, and read the actual checkout page for the version that applies to your order.

## Which coin to send

**USDT on Tron** is the pragmatic default at Evoxt, because it's the stablecoin the pricing page names and Tron fees are small. You get dollar-denominated value and fast settlement. The trade-off is that USDT availability is jurisdiction-dependent across the industry, and this is where most guides mislead people. CoinGate, a Lithuania-based processor, stopped supporting USDT because of EU regulatory requirements, so hosts routing through it can't take your USDT at all, and USDT sent to a USDC checkout isn't credited. Meanwhile Arct Cloud, VPSWolf and Infrawire all still list USDT. Evoxt lists it on Tron specifically. None of these is a general rule; the coin list on your own checkout is.

**Bitcoin** works, is on-chain only as far as Evoxt documents it, and carries a fee set by block space rather than by amount. For a $5.99 monthly plan, the miner fee can be a meaningful share of the payment. If you already hold BTC and don't want to convert, fine. If you're funding a small account specifically for this, converting to a cheap-fee rail first is usually cheaper than the fee you'd pay twice.

**USDC** isn't listed in Evoxt's payment methods, so don't plan around it there. On hosts that do list it, it tracks the dollar and swings far less than a volatile coin, though the euro-dollar rate still applies to a USD-priced invoice.

## How much to top up

Two pressures pull in opposite directions. Network fees are charged per transaction and don't scale with size, which argues for fewer, larger top-ups. Account credit usually can't be withdrawn, which argues for smaller ones. A sensible middle is one to three months of expected spend per top-up. For Evoxt that means roughly $6 to $18 on a VM-1, or $36 to $108 on VM-2.

Check the minimum on the Add Funds screen before you plan a small first payment. Floors vary widely across this market: Bithost asks $20, VPSWolf $25, and Noded requires €5 of balance before an hourly VM can be created.

Refunds are the other half of that calculation. Evoxt's public pricing page doesn't state a refund or credit-withdrawal policy, and a community write-up mentions a 24-hour post-deployment refund window with non-refundable credit afterward. Verify that with support before parking a large balance there. For contrast, Infrawire advertises a 7-day money-back guarantee while Noded states plainly that top-up invoices are final and non-refundable.

👉 [Start with a small credit top-up on Evoxt](https://bit.ly/EvoXt)

## How Evoxt compares on the crypto-payment basics

| Provider | Entry price | Minimum top-up | Stated KYC position | Payment notes |
| --- | --- | --- | --- | --- |
| Evoxt | $2.99/mo (VM-0.5) | Not published | Not stated on pricing page | BTC, USDt on Tron, cards, PayPal; credit up to 3 years |
| Noded | €4/mo (VPS I, Bucharest, ex-VAT) | €5 balance for hourly VMs | ID required above €1,000/month spend | CoinGate; 20-minute rate lock; credit non-refundable |
| Bithost | From $0.015/hr (resold upstream) | $20 | "No KYC" | Resells DigitalOcean, Linode, Vultr; powered-off servers still bill |
| VPSWolf | $3.50/mo (Pup, 1 GB) | $25 | "No ID, no name, no email" | Ten tiers, unlimited traffic, Monero supported |
| Arct Cloud | $3.89/mo (cvm.pico) | Not published | Not stated | BTC, ETH, USDT, USDC, SOL; mining prohibited |
| Infrawire | €8.30/mo | Not published | Explicitly "not anonymous" | 12-hour payment link; 7-day money-back guarantee |

Two footnotes on that table. Bithost's homepage banner claims 300+ cryptocurrencies while its own FAQ lists eleven, so treat the specific list as the real answer. And "no KYC" describes what the brand asks of you, not what happens to your transaction: processors screen payments on-chain and can reject funds linked to sanctioned or illicit sources without refunding them.

## Who this isn't for

Monthly billing cuts both ways. A plan you're not using still costs its monthly price, and hosts that bill hourly are explicit that a powered-off server keeps billing until it's deleted. If your workload is a two-hour test on Sunday, an hourly provider fits better than any monthly plan, Evoxt's included.

Balance-funded accounts also punish slow reactions. On credit-billed hosts the pattern is a low-balance warning, then suspension after the balance hits zero, then termination and disk destruction after a grace period measured in hours. Because crypto takes time to confirm, that warning is your real deadline, not the invoice due date. Keep a card or PayPal option attached as a fallback and none of this matters.

On anonymity, paying in crypto changes the payment rail, not the customer relationship. Noded requires valid ID above €1,000 monthly spend and reserves the right to run KYC at any time; Infrawire states outright that crypto payments aren't anonymous. Evoxt's public pages don't describe an identity requirement, and one third-party write-up says only a name is needed to identify the account. Don't read that as a guarantee.

## FAQ

**Do I need an account with a payment processor?**
No. You pay from your own wallet or exchange account to the address the checkout generates. Some processors ask for an email so they can reach you about the payment, which is worth providing if the transaction goes sideways.

**How long until the credit shows?**
After on-chain confirmation. Tron-based USDT is usually quickest; Bitcoin on-chain typically runs 10 to 30 minutes depending on congestion. The VM itself deploys in about a minute once the balance is there.

**Can I get unused credit back?**
Evoxt's pricing page doesn't say, and policies in this market range from "final and non-refundable" to a 7-day guarantee. Ask support in writing before a large top-up, and size your first payment to one to three months of use.

**Is USDT accepted?**
Yes, on Tron, per Evoxt's own pricing FAQ. That's more than some EU-facing hosts can offer since CoinGate dropped USDT, and less than hosts listing it on several chains. Check the coin and network pair on the payment screen before sending.

**Can I prepay for a year or more?**
Yes. Evoxt offers billing terms from monthly up to three years, and credit added to the account is applied to future invoices automatically. Prepaying removes the recurring fee drag of small monthly crypto payments, at the cost of tying up money you can't withdraw.

## Picking your plan

Single service, 1 GB is enough → VM-0.75 at $4.99. A control panel, a couple of containers, a small database → VM-1 at $5.99, or VM-1.5 at $6.95 if you'd rather have a second core than another gigabyte. Multi-core builds, CI runners, anything memory-hungry → start at VM-4 and work up.

Before you send a single satoshi, confirm two things on the payment screen: the coin and network pair, and the amount after your exchange's withdrawal fee. Then keep the TXID until the balance appears. Everything else is arithmetic you can fix; those two are the ones that cost money.

👉 [Deploy an Evoxt VM and pay with Bitcoin or USDt on Tron](https://bit.ly/EvoXt)
