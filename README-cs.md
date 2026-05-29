[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE)
[![hacs][hacs_badge]][hacs]
[![BuyMeCoffee][buymecoffeebadge]][buymecoffee]

# Versatile Thermostat

Tento README soubor je k dispozici v následujících
jazycích: [Angličtina](README.md) | [Francouzština](README-fr.md) | [Němčina](README-de.md) | [Čeština](README-cs.md)

<p align="center">
<img src="https://github.com/jmcollin78/versatile_thermostat/blob/main/images/icon.png" />
</p>

> ![Tip](images/tips.png) Tato termostatická integrace má za cíl výrazně zjednodušit vaše automatizace kolem správy vytápění. Protože všechny typické události kolem vytápění (nikdo doma?, detekována aktivita v místnosti?, otevřené okno?, omezení spotřeby energie?) jsou nativně spravovány termostatem, nemusíte se zabývat komplikovanými skripty a automatizacemi pro správu vašich termostatů. ;-).

Tato vlastní komponenta pro Home Assistant je vylepšením a kompletním přepsáním komponenty "Awesome thermostat" (viz [Github](https://github.com/dadge/awesome_thermostat)) s přidanými funkcemi.

# Snímky obrazovky

Versatile Thermostat UI Card (K dispozici na [Github](https://github.com/jmcollin78/versatile-thermostat-ui-card)) :

![Card1](https://github.com/jmcollin78/versatile-thermostat-ui-card/raw/master/assets/1.png) ![Card2](https://github.com/jmcollin78/versatile-thermostat-ui-card/raw/master/assets/7.png)

# Co je nového?
![Nové](images/new-icon.png)

## Verze 10.0
Zavedení mechanismu pluginů. Umožňuje používat externí integrace jako pluginy pro _VTherm_. Seznam dostupných pluginů je na [webu Versatile Thermostat](https://www.versatile-thermostat.org/en/plugins).

## Verze 9.3 (stabilní)
> 1. **Detekce zaseknutého ventilu**: významné vylepšení detekce poruch vytápění. Při anomálii u _VTherm_ typu `over_climate_valve` termostat diagnostikuje, zda je příčinou zaseknutý TRV ventil (zaseknutý otevřený/zavřený), a pošle `root_cause` v události. Více informací [zde](documentation/cs/feature-heating-failure-detection.md),
> 2. **Automatické opětovné zamčení po odemčení**: přidán parametr `auto_relock_sec` ve funkci zámku. Při nastavení se termostat po odemčení automaticky znovu zamkne po zadaném počtu sekund. Více informací [zde](documentation/cs/feature-lock.md),
> 3. **Opětovné odeslání příkazu**: nová funkce, která detekuje a opravuje nesoulad mezi požadovaným stavem termostatu a skutečným stavem podkladových zařízení. Pokud se příkaz neprovede správně, odešle se znovu. Více informací [zde](documentation/cs/feature-advanced.md),
> 4. **Obnovení časovaného presetu po restartu**: časovaný preset se po restartu termostatu nebo Home Assistant obnoví a pokračuje normálně. Více informací [zde](documentation/cs/feature-timed-preset.md),
> 5. **Přesnější řízení výkonu**: práh aktivace kotle (`power_activation_threshold`) nově přijímá desetinné hodnoty (0.1, 0.5, ...), což umožňuje jemnější řízení spotřeby. Více informací [zde](documentation/cs/feature-power.md),
> 6. **Zlepšení dostupnosti senzorů**: lepší určování dostupnosti teplotních senzorů přes metadata `last_updated` v Home Assistant.

# 🍻 Děkuji za piva 🍻
[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/jmcollin78)

Velké díky všem mým donátorům za jejich příspěvky a povzbuzování. Je to pro mě velmi potěšující a motivuje mě to pokračovat! Pokud vám tato integrace pomohla ušetřit, kupte mi malé pivo na oplátku, budu vám velmi vděčný!

# Slovník

  `VTherm` : Versatile Thermostat v následujícím textu tohoto dokumentu

  `TRV` : termostatická hlavice vybavená ventilem. Ventil se otevírá nebo zavírá, čímž umožňuje průchod teplé vody

  `AC` : klimatizace. Zařízení je AC, pokud chladí. Teploty jsou pak obrácené: Eco je teplejší než Komfort, který je teplejší než Boost. Algoritmy tuto informaci berou v úvahu.

  `EMA` : Exponential Moving Average. Používá se k vyhlazení měření teplot senzorů. Odpovídá klouzavému průměru teploty místnosti. Používá se k výpočtu sklonu křivky teploty (slope), který by byl na surové křivce příliš nestabilní.

  `slope` : sklon křivky teploty. Měří se v °(C nebo K)/h. Je pozitivní, pokud teplota stoupá, a negativní, pokud klesá. Tento sklon se počítá na `EMA`

  `PAC` : tepelné čerpadlo

  `HA` : Home Assistant

  `underlying`: zařízení ovládané `VTherm`

# Dokumentace

Dokumentace je nyní rozdělena do několika stránek pro snadnější čtení a vyhledávání:
1. [Úvod](documentation/cs/presentation.md)
2. [Instalace](documentation/cs/installation.md)
3. [Rychlý start](documentation/cs/quick-start.md)
4. [Výběr typu VTherm](documentation/cs/creation.md)
5. [Základní atributy](documentation/cs/base-attributes.md)
6. [Konfigurace VTherm na `spínači`](documentation/cs/over-switch.md)
7. [Konfigurace VTherm na `klimatizaci`](documentation/cs/over-climate.md)
8. [Konfigurace VTherm na ventilu](documentation/cs/over-valve.md)
9. [Předvolby](documentation/cs/feature-presets.md)
10. [Správa oken](documentation/cs/feature-window.md)
11. [Správa přítomnosti](documentation/cs/feature-presence.md)
12. [Správa pohybu](documentation/cs/feature-motion.md)
13. [Správa energie](documentation/cs/feature-power.md)
14. [Auto start a stop](documentation/cs/feature-auto-start-stop.md)
15. [Centralizované řízení všech VTherm](documentation/cs/feature-central-mode.md)
16. [Řízení ústředního vytápění](documentation/cs/feature-central-boiler.md)
17. [Pokročilé aspekty, bezpečnostní režim](documentation/cs/feature-advanced.md)
18. [Detekce poruchy vytápění](documentation/cs/feature-heating-failure-detection.md)
19. [Samoregulace](documentation/cs/self-regulation.md)
20. [Auto TPI učení](documentation/cs/feature-autotpi.md)
21. [Algoritmy](documentation/cs/algorithms.md)
22. [Zamknutí / odemknutí](documentation/cs/feature-lock.md)
23. [Synchronizace teploty](documentation/cs/feature-sync_device_temp.md)
24. [Časovaný preset](documentation/cs/feature-timed-preset.md)
25. [Referenční dokumentace](documentation/cs/reference.md)
26. [Příklady ladění](documentation/cs/tuning-examples.md)
27. [Řešení problémů](documentation/cs/troubleshooting.md)
28. [Poznámky k verzím](documentation/cs/releases.md)

# Některé výsledky

**Stabilita teploty kolem cíle nakonfigurovaného předvolbou**:

![image](documentation/en/images/results-1.png)

**Cykly zapnutí/vypnutí vypočítané integrací `over_climate`**:

![image](documentation/en/images/results-2.png)

**Regulace s `over_switch`**:

![image](documentation/en/images/results-4.png)

**Silná regulace v `over_climate`**:

![image](documentation/en/images/results-over-climate-1.png)

**Regulace s přímým řízením ventilu v `over_climate`**:

![image](documentation/en/images/results-over-climate-2.png)

Užijte si to!

# Příspěvky jsou vítány!

Pokud si přejete přispět, přečtěte si prosím [pokyny pro přispívání](CONTRIBUTING-cs.md).

***

[versatile_thermostat]: https://github.com/jmcollin78/versatile_thermostat
[buymecoffee]: https://www.buymeacoffee.com/jmcollin78
[buymecoffeebadge]: https://img.shields.io/badge/Buy%20me%20a%20beer-%245-orange?style=for-the-badge&logo=buy-me-a-beer
[commits-shield]: https://img.shields.io/github/commit-activity/y/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[commits]: https://github.com/jmcollin78/versatile_thermostat/commits/master
[hacs]: https://github.com/custom-components/hacs
[hacs_badge]: https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[forum]: https://community.home-assistant.io/
[license-shield]: https://img.shields.io/github/license/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-Joakim%20Sørensen%20%40ludeeus-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[releases]: https://github.com/jmcollin78/versatile_thermostat/releases
