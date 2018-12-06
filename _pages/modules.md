---
permalink: /modules
title: Module Directory
classes: page--modules

categories:
- header: Skill Predictors
  description: "Simulates skills client-side so you can evade taxes of the ping variety."
  modules:
  - repo: tera-mods/skill-prediction
    desc: The big one. Supports most skills.    **Pinkie's Proxy**
  - repo: SaltyMonkey/skill-prediction
    desc: The Cloned one. Supports most skills. **Caali's Proxy**
- header: Notable Modules
  description: "The big guns. These modules are more than simple scripts."
  modules:
  - repo: caali-hackerman/battle-notify
    desc: Shows text notifications on configurable in-game events.
- header: Quality of Life
  description: "These modules are relatively benign, and there's likely little risk to using these. But they *will* make your life better, probably."
  modules:
  - repo: TeraProxy/AFKer
    desc: Prevents the client from going back to character selection.
  - repo: tera-mods/auto-vanguard
    desc: Automatically turns in Vanguard quests upon completion.
  - repo: teralove/camera-distance
    desc: Removes limit on the camera's max range.
  - repo: teralove/channel-command
    desc: Switch channels via chat command.
  - repo: TeraProxy/EnrageNotifier
    desc: Shows private party notices for enrage & next enrage percentage.
  - repo: teralove/exit-command
    desc: Exit the game via chat command.
  - repo: teralove/exit-instantly
    desc: Exit the game without having to wait 10 seconds.
  - repo: teralove/lobby-command
    desc: Return to lobby (character select) via chat command.
  - repo: Mister-Kay/no-more-crazy-capes
    desc: Removes exploding physics glitch from some back items.
  - repo: teralove/parcel-helper
    desc: Instantly accept all parcels and delete all read messages.
  - repo: teralove/party-death-markers
    desc: Shows rare item beacon on party member corpses.
  - repo: Snugglez/relog
    desc: Switch character via chat command.
  - repo: caali-hackerman/skill-resets
    desc: Pops up a message whenever a skill resets.
  - repo: tera-mods/no-cutscenes
    desc: No more mashing Esc after killing a boss; Pretend cutscenes don't exist.
  - repo: Saegusae/looks
    desc: Copies the character's appearance of yourself or other nearby players.
- header: The Questionable Ones
  description: "Where the line starts getting blurred. If you use these and it gets noticed... Well, no promises."
  modules:
  - repo: tera-mods/auto-negotiate
    desc: Automatically accepts or declines broker negotiations. Configurable.
  - repo: TeraProxy/Essentials
    desc: Automatically uses Nostrum/Battle Solution" and Complete Crystalbind.
  - repo: TeraProxy/Cosplayer
    desc: Allows wearing anything client-sided through UI selection.
  - repo: tera-mods/fly-forever
    desc: Ignores flying mount stamina for infinite flying.
  - repo: Risenio/fps-utils
    desc: A compilation of utilities to improve fps.
  - repo: Risenio/let-me-pot
    desc: ~~Auto uses HP or MP potions at certain % you choose & has slay support.~~
  - repo: Risenio/let-me-drink
    desc: ~~Automatically uses "Lein's Dark Root Beer" at certain usage of skills.~~
  - repo: Risenio/let-me-lock
    desc: ~~Auto locks on players for healing/cleansing \| npcs for debuff/dps purposes.~~
  - repo: teralove/auto-heal
    desc: Automatically skips lockons and instantly heals and cleanses party members.
  - repo: TeraProxy/Teabagger
    desc: Allows you teabag people. but rly tho?
  - repo: Saegusae/loot
    desc: Automatically loots items in a radius.
---

Here is a directory with links to a number of GitHub projects and developers who work with tera-proxy or other TERA modding programs. That means **all projects directly linked here are free and open source**.

If you want to be added to this list, or you think a module has been miscategorized, [submit a issue](https://github.com/Risenio/_/issues/new) or DM me on discord `@Risenio#1785`.

{% for category in page.categories %}
{% assign names = "" | split: "" | where_exp: "item", "false" %}
{% for module in category.modules %}
{% assign repo = module.repo | split: "/" | last | downcase %}
{% assign names = names | push: repo %}
{% endfor %}
{% assign names = names | uniq | sort %}

## {{ category.header }}

{{ category.description }}

| Module | Description |
| --- | --- |{% for name in names %}{% for module in category.modules %}{% assign repo = module.repo | split: "/" %}{% assign test = repo | last | downcase %}{% if test != name %}{% continue %}{% endif %}{% assign user = module.author %}{% unless user %}{% assign user = repo[0] %}{% endunless %}
| [{% avatar user=user %}][@{{ user }}] [{{ repo[1] }}](https://github.com/{{ module.repo }}) | {{ module.desc }} |{% endfor %}{% endfor %}

{% endfor %}

## Module Developers

For any other kind of module, you may want to take a look at public repositories or websites. Below is a list of module developers on GitHub, along with links to other sources where you may find more information or modules not publicly posted.

* [{% avatar pinkipi %} Pinkie Pie][@tera-mods] &ndash; [Discord](https://discord.gg/RR9zf85)
* [{% avatar caali-hackerman %} Caali][@caali-hackerman] &ndash; [Discord](https://discord.gg/dUNDDtw)
* [{% avatar Saegusae %} Saegusae][@Saegusae]
* [{% avatar teralove %} teralove][@teralove]
* [{% avatar TeraProxy %} Dureal][@TeraProxy]

## Related Projects

tera-proxy is just one of many projects aimed at modding and extending TERA functionality. These related projects are not modules; they are standalone programs that do their own thing with or without tera-proxy.

* [ShinraMeter](https://github.com/neowutran/ShinraMeter) ([@neowutran], [@Gl0]): A TERA DPS meter. &ndash; [Discord](https://discord.gg/anUXQTp)
* [Tera Custom Cooldowns](https://github.com/Foglio1024/Tera-custom-cooldowns) ([@Foglio1024]): Replaces some TERA UI elements with sleek and responsive designs.



[//]: # (GitHub @mention link references go below.)

[@alexrp]: <https://github.com/alexrp> "Alex Rønne Petersen @Zor#0001"
[@ayylmar]: <https://github.com/ayylmar>
[@beng-mods]: <https://github.com/beng-mods> "Beng @beng#5950"
[@Bernkastel]: <https://github.com/Bernkastel-0> "Bernkastel @Bernkastel#5066"
[@caali-hackerman]: <https://github.com/caali-hackerman> "Caali @Caali#4766"
[@Chocoooo]: <https://github.com/Chocoooo> "Choco @Choso#7233"
[@codeagon]: <https://github.com/codeagon> "Pentagon @Pentagon#0099"
[@eemj]: <https://github.com/eemj> "Jamie @"
[@Foglio1024]: <https://github.com/Foglio1024> "Foglio @Foglio();#3430"
[@Fukki]: <https://github.com/Fukki> "Fukki @"
[@Gl0]: <https://github.com/Gl0> "Gl0 @Gl0#0588"
[@GoneUp]: <https://github.com/GoneUp> "GoneUp @GoneUp#1810"
[@HakuryuuDom]: <https://github.com/HakuryuuDom> "Haku @Haku#1983"
[@hugedong69]: <https://github.com/codeagon> "Pentagon @Pentagon#0099"
[@iribae]: <https://github.com/iribae> "Xiphion @Xiphion#4197"
[@jenoveil]: <https://github.com/jenoveil>
[@Juju-s]: <https://github.com/Juju-s>
[@Kaseaa]: <https://github.com/Kaseaa> "Kasea @Kasea#0676"
[@Leyki]: <https://github.com/Leyki> "Zelekie @Leiki#8317"
[@loggeru]: <https://github.com/loggeru>
[@lunyx]: <https://github.com/lunyx> "Daniel @"
[@luxurymini]: <https://github.com/luxurymini>
[@maizuru]: <https://github.com/maizuru> "Zefiris @"
[@Mathicha]: <https://github.com/Mathicha> "Mathi @Mathi#6969"
[@meishuu]: <https://github.com/meishuu> "Meishu @Meishu#0001"
[@Mirrawrs]: <https://github.com/Mirrawrs> "Mir @"
[@Mister-Kay]: <https://github.com/mister-kay> "Kourinn @Kourinn#6001"
[@mopihu]: <https://github.com/mopihu> "M0py @m0py#5785"
[@neowutran]: <https://github.com/neowutran> "Yukikoo @Yukikoo/Neowutran#0894"
[@Nxlllp]: <https://github.com/Nxlllp> "Oっぱい @"
[@Owyn]: <https://github.com/Owyn> "Owyn @Owyn#1028"
[@pinkipi]: <https://github.com/tera-mods> "Pinkie Pie @Pinkie Pie#7969"
[@Risenio]: <https://github.com/Risenio> "Risenio @Risenio#1785"
[@Saberawr]: <https://github.com/Saberawr> "Erin @"
[@Saegusae]: <http://github.com/saegusae> "Seagoose @Saegusa#3195"
[@SaltyMonkey]: <https://github.com/SaltyMonkey> "Salty @Powah#0001"
[@seraphinush-gaming]: <https://github.com/seraphinush-gaming> "Seraph @seraphinush#5417"
[@SerenTera]: <https://github.com/SerenTera> "Seren @Seren#7182"
[@Shinoyx]: <https://github.com/Shinoyx> "Shino @Sasha#2674"
[@Snugglez]: <https://github.com/Snugglez> "Snug @Snug ⚣#5452"
[@soler91]: <https://github.com/soler91> "Fruit @Fruit#6746"
[@Some-AV-Popo]: <https://github.com/Some-AV-Popo>
[@spaacecats]: <https://github.com/spaacecats> "Shapi @Shapi#4624"
[@Sunpui]: <https://github.com/Sunpui> "Bubble @"
[@tera-mods]: <https://github.com/tera-mods> "Pinkie Pie @Pinkie Pie#7969"
[@Tera-Shiraneko]: <https://github.com/Tera-Shiraneko> "Shalltearz @"
[@teralove]: <https://github.com/teralove> "Teralove @teralove#5955"
[@TeraProxy]: <https://github.com/TeraProxy> "Dureal @Dureal#3052"
[@terastuff]: <https://github.com/terastuff> "KTC @"
[@undefjs]: <https://github.com/undefjs> "Undef @undef#3394"
[@valkyr1e-tera]: <https://github.com/valkyr1e-tera> "Valkyr1e @valkyrie#7092"
[@VenoMKO]: <https://github.com/VenoMKO>
[@wuaw]: <https://github.com/wuaw> "Wuaw @"
[@xmljson]: <https://github.com/xmljson> "Rickhyun @Party timu~#3425"
[@Xtortion]: <https://github.com/Xtortion> "Xtortion @Xtortion#0007"
[@Yuyuko-sama]: <https://github.com/Yuyuko-sama> "Yuyuko @༺ཌༀൢYUYUKO༒SAMAൢༀད༻#4941"
[@zc149352394]: <https://github.com/zc149352394> "海比丶天蓝 @海比丶天蓝#9978"

[//]: # (I couldn't find a references for the below people/developers.)
[@//]: # "gievepix#1130"
[@//]: # "topi#8789"
[@//]: # "Bobbuz#0891"
[@//]: # "GIOGIO#2244"
[@//]: # "Chaos#6677"
[@//]: # "Herysia#4293"
[@//]: # "Melen#7658"
[@//]: # "Menma#8261"
[@//]: # "Mominon#9633"
[@//]: # "Panty#1583"
[@//]: # "Roukanken#0001"
[@//]: # "Loli#3361"
[@//]: # "Aru#9995"
[@//]: # "JustPassingBy#4413"
[@//]: # "radasuka#1657"
[@//]: # "teri#9999"
[@//]: # "InTheShadow#2633"
[@//]: # "Seyuna#0001"
[@//]: # "Eternal, the Everlasting#5996"
[@//]: # "Vani#9101"
[@//]: # "e"
[@//]: # "e"
[@//]: # "e"
[@//]: # "e"
[@//]: # "e"
[@//]: # "e"
[@//]: # "e"
[@//]: # "Germy#9001"

