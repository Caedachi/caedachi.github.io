---
layout: page
title: Email Threat Model
permalink: /email-threat-model/
---

I like email, but I don't like data breaches. 
This is an email threat model I came up with to address the problem of emails being leaked in data breaches (and also spam, because eff spam).

## Primer
Implementing this threat model requires an email provider that supports email aliases. 
You can technically implement this with multiple accounts, but that more than likely isn't very convenient compared to having all your aliases in one spot.

"*Don't have all your eggs in one basket!*", you might say. 
Yeah yeah, I get it, but this is the trade-off I'm willing to make for the convenience of managing this model.
This threat model is meaningless to you if, for example, you're using the same password across multiple websites. 
In that case, you should probably be using a password manager.

## How does it work?
The premise behind the **B**ig **S**hark **T**houghts™ **E**mail **T**hreat **M**odel (**B**<sub>e</sub>**ST** **E**mail<sup>**T**hreat **M**odel</sup>) is as follows: 
**organize buckets of email aliases in a way that's meaningful to you. I'll refer to these buckets as "tiers".**

# Tiers
Tiers define *how you compartmentalize your online accounts*. You may have one tier for shopping accounts and another for social media, perhaps one for banking; the list goes on. This *isn't* how I've personally implemented my email threat model, since that can be potentially many tiers to keep track of (which would then become an inconvenience).

Instead, I've implemented a 5 tier system, labeled 0 from 4 (the numbering doesn't matter as long as it's meaningful to you). 
Each tier represents how much of an inconvenience it would be if they were compromised.

My tiers are labeled like so:
- 0: catastrophically inconvenient if compromised
- 1: significantly inconvenient if compromised
- 2: moderately inconvenient if compromised, but not the end of the world
- 3: not very inconvenient if compromised
- 4: absolute garbage; I don't care if these are compromised

Based on how I have my tiers setup, the majority of my accounts are within tiers 2 and 3, while a handful of accounts are in tiers 1 and 4.
Tier 0 has very few accounts.

The benefit of this convention for me is that, before I create a new account at some xyz website, I ask myself, *how important is this account I'm making?* 
At which point, I decide which tier to which the account should belong. 
This brings me to the critical piece of the threat model.

# Aliases
Email aliases are pretty self explanatory: 
they help mask your underlying email address and--depending on your email provider--you can have many aliases for your one email account. 
Each tier has a pool of **mutually exclusive** aliases (that means aliases in one tier cannot belong to another tier).

After picking a tier for a new account, I then pick an alias from that tier.
The one I pick is *usually* random, but we're not good at being random, so in all likelihood, there are a handful of aliases within a tier that are used more than others.

And that's it, that's the threat model.

## Advantages
Off the top of my head, and in no particular order, these are the benefits of this threat model for me. These are personal opinions; some (or a lot of these) may not matter to you:
- It helps limit potential spam. By siloing each tiers' aliases, there's little-to-no risk of a compromised alias affecting other aliases in a tier, or between tiers.
- If an alias does get spam, deactivating it and remaking a new alias is far easier than deleting and creating a new email account. While spam filters are (in general) very good, wouldn't it be nice to not get spam at all?
- It increases overall online security by not sharing email addresses across different kinds of accounts. You wouldn't want your `xtremeCoolPerson@coolmail.dog` to be compromised along with your password, if that email was your username for your one-off shopping accounts and also your bank accounts.
- It's a *really* nice supplement to a password manager. You can tag which accounts belong to which tiers, useful for understanding the breadth and depth of your online account presence.

## Disadvantages
No threat model is without its disadvantages; this model is no exception.
- *Not* having a pool of aliases per tier kinda renders this threat model moot. One alias should not be assigned to many accounts to a tier.
- We're lazy and sometimes we forget about things; implementing this email isn't entirely one-and-done, we need to actively put it into practice and make sure that we stick to the conventions defined by the tiers. All of which is to say that we're the weakest link.
- If you have existing email addresses and hundreds of accounts, implementing this threat model from scratch is **a pretty big hassle**. I went through it anyways because I wanted to consolidate my emails to one service provider. This meant updating at least over a hundred accounts; it took at least several days to fully implement it. The worst part is that some accounts don't let you change your email address after creating your account.
- It doesn't replace a password manager; of course it wouldn't, it's not its intent.

## Final Thoughts
If I had to do it all over again, I probably would've just setup email forwarding for my existing accounts to my primary service provider, and then assign those emails to a tier (3 or 4).