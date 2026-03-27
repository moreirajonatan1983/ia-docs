# Billing — Kiro CLI

> **Source:** [kiro.dev/docs/cli/billing/](https://kiro.dev/docs/cli/billing/)

---

Kiro CLI uses the same plan and credit system as the IDE. Refer to the [Kiro plans page](https://kiro.dev/docs/billing/) for current pricing and tier details.

---

## Billing Practices

The following rules apply when subscribing, upgrading, downgrading, or incurring overages:

### Upgrading from Free → Paid (first time)

If you are on the **Kiro Free tier**, have never upgraded before, and upgrade to Pro, Pro+, or Power mid-month:
- You are charged a **prorated fee** for the remainder of the month
- You immediately get access to your new plan's **full credit limits**
- If you upgrade again in the same month, fees are backdated proportionally as if you had chosen the higher tier from day one

### Upgrading Between Paid Tiers

If you upgrade from one paid tier to a higher paid tier mid-month:
- You are charged a **retroactive fee for the entire month** based on the price difference
- Kiro recalculates the entire month's usage under the new tier's credits
- Example: If you used 1,010 credits (10 over the Pro cap) and then upgraded to Pro+, the overage charge is eliminated under the new tier's limits

### Downgrading

- Downgrades **take effect in the following month** (upgrades are effective immediately)
- If you downgrade mid-month (e.g., Pro+ → Pro on June 2nd), you are charged the **full fee for that month** (full Pro+ fee for June), then the new tier fee from the next cycle onward

### Overages

- If you incur overages, you are charged the total overage fees for the month **at the end of the billing cycle**

### Credit Renewal

- For **all tiers**, your usage cap renews at the beginning of the **next billing cycle**

---

## Next Steps

- [Managing your Kiro CLI subscription →](https://kiro.dev/docs/cli/billing/subscription-portal/)
- [Plans and billing (IDE) →](https://kiro.dev/docs/billing/)
