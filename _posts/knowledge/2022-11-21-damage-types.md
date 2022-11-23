---
title: "Damage types"
date: 2022-11-21 18:00:00 +0100
categories: [Knowledge, Damage]
tags: [knowledge, damage]
author: Legrems
math: true
---

# Raw Damage

Raw Damage is the first component of your [Skill damage](#skill-damage) and is found on [Attribute](/posts/attributes), [Skill](#LINK_HERE) and [Equipment](#LINK_HERE).

$\color{white}raw_{damage} = (base_{raw_{damage}} + \sum added_{flat}) \times \sum added_{percent} \times \prod (1 + multipliers)$

# Skill Damage

Skill Damage is the sum of your [Raw Damage](#raw-damage) and [Reaper Damage](#reaper-damage), and represents the range of Damage you can deal when dealing Skill Damage.

![](/assets/img/skill_damage_example.png)
_Example of skill dealing skill damage_

The formula is this if you don't have the reaper to elemental conversion :

$\color{white}skill_{damage} = raw_{damage} + reaper_{damage}$

If you do, then:

$\color{white}skill_{damage} = raw_{damage}$

# Elemental Damage

Elemental Damage is found on [Attribute](/posts/attributes), [Skill] and [Equipment], and is used when dealing Elemental Damage.

![](/assets/img/elemental_damage_example.png)
_Example of skill dealing elemental damage_

$\color{white}ele_{damage} = (base_{ele_{damage}} + \sum added_{flat}) \times (1 + \sum added_{percent}) \times \prod (1 + multipliers) $

If you do have Reaper Damage to Elemental Damage conversion (from a reaper or the legendary amulet), the formula is applied:

$\color{white}ele_{damage} = (base_{ele_{damage}} + \sum added_{flat}) \times (1 + \sum added_{percent}) \times \prod 
(1 + multipliers) + reaper_{damage}$

# Reaper Damage

Some [Skill] deal Reaper damage. Those are based upon your [Slorm Reaper](https://cayrac.github.io/slorm-reaper/list) and can be boosted with some [Attribute](/posts/attributes), [Legendary effect], or even

![](/assets/img/reaper_damage_example.png)
_Example of skill dealing reaper damage_
