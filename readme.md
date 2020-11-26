# Let op:
- Voor alle projecten voor 25/11/2020, gebruik config-0.5.0.yml
- Voor alle nieuwere projecten, gebruik condig-1.0.0.yml

Bij gebruik hernoemen naar `config.yml` en in de map `.circleci` te plaatsen in de root van het thema (niet nodig voor gebruik laatste versie base-theme).

**Config 0.4.5**
Dit is de configuratie voor CircleCi via de Bastion Jump Host via rSync naar de server. Deze config triggert builds op basis van tagging.

**Config 1.0.0**
Dit is de nieuwere configuratie voor CircleCi, ook middels een Bastion Jump Host, triggering van builds gebeurt hier op basis van het branching model, beschreven in [de readme van het base-theme](https://github.com/burovoordeboeg/wordpress-base-theme).
