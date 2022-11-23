---
title: Advanced crafting
date: 2022-11-21 20:00:00 +0100
categories: [Crafting, Reinforcement]
tags: [crafting, stats, 0.4.x]
author: Legrems
math: true
mermaid: true
---

![](/assets/img/crafting/advanced_gear.png)
_This is the kind of item we want to make_

I will quickly recapitulate the basic of crafting before processing.

# Stats

Stats on the item are stated as so in the game, you have:
- Base (or normal) stats
- Magic stats
- Rare stats
- Epic stats

This does not include:
- Legendary effects (those are effects, not stats)
- Attributes on gear
- Mastery on gear
- Reaper affinity on gear
- The potential of the item

Before [The Luxuriant Update: Part I](/posts/6368680725434905917), base, magic and rare stat where dependant on the base type of the item. After this update, epic is also base type dependant.
This mean you cannot have any stat you want anywhere, refer to [this](/posts/stats/) to see what is available where.

## Stat roll

To understand more about how the game use the roll, let's take an example.

Let's say the stat you have can roll from 100-200. This number isn't actually stored anywhere, but the `range roll` is actually stored (not an official term).
Let's also say that your item have like 175 of this stat. The `range roll` stored isn't 175, but depend on the stat and the rarity.

### `range roll` for stat

The `range roll` for non-percent stat is fixed compare to the ilevel of the item.

This mean the stored roll of the item will still be in the 70-100 (for normal stat) independantly of the reinforcement level of the item. But the total amount of that stat will increase of course.

`range roll` | Minimum value | Maximum value
Normal rarity | 70 | 100
Magic rarity | 45 | 65
Rare rarity | 45 | 65
Epic rarity | 20 | 40

### `range roll` for percent (%) stat

The behaviour is different for percent stat. The possible roll stored will change if the ilvl of the item change.

`range roll` with `ilvl < 20` | Minimum value | Maximum value
Normal rarity | 14 | 20
Magic rarity | 9 | 13
Rare rarity | 9 | 13
Epic rarity | 4 | 8

`range roll` with `ilvl < 35` | Minimum value | Maximum value
Normal rarity | 28 | 40
Magic rarity | 18 | 26
Rare rarity | 18 | 26
Epic rarity | 8 | 16

`range roll` with `ilvl < 45`| Minimum value | Maximum value
Normal rarity | 42 | 60
Magic rarity | 27 | 39
Rare rarity | 27 | 39
Epic rarity | 12 | 24

`range roll` with `ilvl < 52`| Minimum value | Maximum value
Normal rarity | 56 | 80
Magic rarity | 36 | 52
Rare rarity | 36 | 52
Epic rarity | 16 | 32

`range roll` with `ilvl >= 52`| Minimum value | Maximum value
Normal rarity | 70 | 100
Magic rarity | 45 | 65
Rare rarity | 45 | 65
Epic rarity | 20 | 40

### Meaning of all of this

This mean that if you get an item ilvl 10 with Max Life and % Max Life with the best current roll possible, if you upgrade the ilvl paste 52, the Max Life stat will still be capped to the max roll, but the % Max Life will not. Since the `range roll` of this % Max Life on a ilvl 10 item was 14-20 (for normal stat), and you had the max roll, your item had 20 for the `range roll`.

But now that you have update your item, the % Max life `range roll` is 70-100, meaning that the present % Max Life will be 5 times less.

All of that is to say that it's better to craft on an high level item, instead of upgrading them after.

## Scaling

Stats scale of multiple thing:
- Level of the item (will be called ilevel in this guide), most of the time, this is assumed to be the max possible (60 at the time of this post)
- Reinforcement level of the item (will be called level later in this guide)
- Pureness, is whatever the stat is pure or not. See [Pure stat](#pure-stat) for more informations
- The roll of the stat

### ilevel scaling

Each stat scale differently with the ilevel, but all according to the same formula. Each stat does have a `score`. The higher the score, the higher the in-game stat value.

The formula for non-percent stat:
$max_{value} = stat_{score} \times \frac{100 + ilevel \times 30}{100}$


The formula for percent stat:
$max_{value} = stat_{score} \times score_{level} \times 20 / 100$

Where `score_level` is determined by the ilevel of the item

ilevel | `score_level`
`0 <= ilevel < 20` | 1
`20 <= ilevel < 35` | 2
`35 <= ilevel < 45` | 3
`45 <= ilevel < 52` | 4
`52 <= ilevel < ?` | 5

#### Example

Max Life has a score of 34 at the time of this post, meaning that the max value at 60 with no reinforcement is $34 \times \frac{100 + 60 \times 30}{100} = 646$

This is the top-end of the stat. The bottom range is defined with the [`range roll`](#range-roll-for-stat). If the Max Life stat is in a normal stat in ilevel 60, the range is
$$646 \times range_{roll_{low}} / 100 = 646 \times 70 / 100 = 452$$ up to $$646 \times range_{roll_{high}} / 100 = 646 \times 100 / 100 = 646$$

The range for Max Life in a normal stat is `452-646` (rounded).

#### Example

For an item ilevel 49 with % Max Life on a magic slot, the top end of the range would then be $10 \times 4 \times 20 / 100 = 8$$

So for a magic slot: $$low_{end} = 8 \times 45 / 100 = 3.6$$ and $$high_{end} = 8 \times 65 / 100 = 5.2$$

![](/assets/img/crafting/gear_max_life_percent_example.png)
_If you round those value, you get a range of `3.5%-5%`_

I won't get into the rounded stuff here :D


# Reinforcement

The reinforcement process let you upgrade your gear by making the stats and the legendary effect (not all of them) more efficient.

Each new level of reinforcement add a little less of the power each time.

Reinforcement level | Current level bonus | Total bonus | % bonus compare to prec. level
1 | 15% | 15% | 15.0%
2 | 14% | 29% | 12.2%
3 | 13% | 42% | 10.1%
4 | 12% | 54% | 8.5%
5 | 11% | 65% | 7.1%
6 | 10% | 75% | 6.1%
7 | 9% | 84% | 5.1%
8 | 8% | 92% | 4.3%
9 | 7% | 99% | 3.6%
10 | 6% | 105% | 3.0%
11 | 5% | 110% | 2.4%
12 | 4% | 114% | 1.9%
13 | 3% | 117% | 1.4%
14 | 2% | 119% | 0.9%
15 | 1% | 120% | 0.5%
16 | 1% | 121% | 0.5%
17 | 1% | 122% | 0.5%
18 | 1% | 123% | 0.5%
19 | 1% | 124% | 0.4%
20 | 1% | 125% | 0.4%

Yes, there is no maximum for reinforcement level, you can go paste 15.

Reinforcement does *NOT*:
- Upgrade by any kind attribute on gear
- Upgrade by any kind mastery on gear
- Upgrade by any kind reaper affinity on gear

## Example

An item +10 (= an item with 10 reinforce level) will give a little more than double the standard stats. (Range of `927-1324` for a Max Life normal stat)

## Reinforcement on legendary effect

Most legendary are affected by the reinforce effect (some don't at all), but the dimnishing return isn't present here!

You get X% (stated on the legendary effect) each reinforce level on the legendary effect (if the effect stacks of course). This is the main reason of grinding insane amount of reinforce level on an item.

# Pure stat

![](/assets/img/crafting/good_pure_stat.png){: .right}
Pure stat are highlighted in the game as cyan, with a little `!` (or more than one) on the stat and are basically a multiplier of the value of the stat. If you didn't max out the temple upgrade, the default range is from 100% to 110% of the stat value.

Once you've maxed the temple upgrade, the multiplier of base stat goes up to 200%. This mean with extreme luck, you can have a stat with twice the value (but it's 1/100 chance of dropping when you drop a pure stat).

You can *NOT*:
- Update the roll of a pure stat, or you will loose the purity
- Reforge the pure stat into another, or you will loose the purity
- Add a pure stat into an existing item in any way. With that said, well-rolled pure stat item are very rare and valuable

You can:
- Reinforce you gear, this will increase even more the pure stat
- Lock the pure stat, this will prevent you to accidently modify and loose your pure stat
- Unlock the pure stat. You won't loose the purity, but i don't really know why you would do that, except from removing the pure stat


## Disclaimer

*I want to say that ZERO pure stat is required in order to farm efficiently in W10 (Wrath 10)*

# Reinforce methods
# Crafting methods
Those methods are only the one that I used. I do not claim those are the most efficient way of doing things, just that I know the average cost and outcome of each one.

First step in the crafting process is to know where you want to be. A great help is to use the [planner](https://cayrac.github.io).

## The "From scratch"

This method will probably describe most of your gear.

1. Level the stuff to the reinforce level you want to achieve. You can use [some reinforce methods](#reinforce-methods)
2. Reforge normal stat until at least one you want
. Reforge magic stat until the one you want
. Reforge rare stat until the one you want
. Add if not present an epic stat (if you're lucky, you can get multiple)
. Preventing step: if you did get some acceptable roll for your item, consider locking it before moving on
. Reforge all Scores until one is within your acceptable range
. Lock this acceptable stat
. Repeat ^x2 until your magic/rare stats are locked
. Now your item has magic/rare stats locked. Reforge normal stat if necessary until you get the second one you want
. Reforge all Scores until the last normal stat has a good roll, the lock it
. Now your item should have normal/magic/rare stats fully locked. We're gonna work on epic stat
. If there is an unlocked wanted epic stat, reforge all Scores until you get the desired score
. The lock this stat.
. Reforge Epic stats. By doing this, if you have less than 3 stats, there is a chance that it will add (or remove the unlocked one) stat. The goal is to reforge epic stat until you get a second (or third) one you want.
. Once you've reached another epic stat, again reforce all Score until the wanted score.
. The lock it and repeat until you get your 3 wanted epic stat

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

## The "I'm lucky with my epic drops"

This method happend sometimes with great drops

## The "I really want those juicy pure stats"

See [the disclaimer first](#disclaimer)

This method is focused on item with good pure stat, since those can enable (or at least make it way easier) builds in the late game.
