# CircleCi setup

We volgen voor deze geautomatiseerde CI/CD pipeline een git-branching model, uitgaande dat:
- Je een production, staging en develop branch hebt opgezet
- De production branch ingesteld hebt als 'default branch'
- Je werkt in je eigen branch, of eventueel feature-branches voor het ontwikkelen van extra features, je werkt nooit direct in de production of staging branch
- Je merged features naar de develop branch
- De develop branch merge je vervolgens middels een release naar staging. In de staging branch maak je een versienummer aan
- Zodra de staging omgeving akkoord is, maak je een merge naar de production branch, en ook daar maak je een versienummer aan

Builds triggeren automatisch, zo triggert:
- Bij elke commit en PR de jsLint en sassLint
- Bij elke release op de staging branch een staging-deploy
- Bij elke release op de master branch een master-deploy

Om je CircleCi omgeving op te zetten voer je de volgende stappen uit:
1. Ga naar CircleCi en klik aan de linkerzijde op projects, zoek de juiste repository en klik op "set up project", of klik op "follow" als dit erbij staat (in dat geval zijn onderstaande stappen wellicht overbodig)
2. Klik in het vervolgscherm op "Use existing config" (als je dit scherm niet krijgt, ga naar stap 3), en klik de waarschuwing door "Start building"
3. De lint-workflow loopt nu automatisch.
4. Klik rechtsboven op "Project settings", en ga naar de tab SSH-Keys
5. Klik bij "Additional SSH Keys"  op "Add SSH Key". 
6. Hostnaam: s01.burovoordeboeg.nl, vervolgens zoek je in Dashlane de "Private Server Key voor CircleCi"
7. Voeg een tweede SSH Key toe: hostnaam: circleci.burovoordeboeg.nl en zoek in Dashlane naar "Private Bastion Key voor CircleCi"
8. Ga nu naar de Buro voor de Boeg server, en maak daar de user aan. Vergeet niet deze user SSH-access te verlenen.
9. Na het aanmaken van de user op de server ga je naar de optie "SSH Keys", onderaan staat "Paste Authorized Key", plaats daar de inhoud van de Dashlane kaart "Public Server Key voor DirectAdmin"
11. Ga terug naar CircleCi
11. Ga naar de tab "Environment variables"
12. Maak drie variabelen aan:
    - USER > Hier vul je de DirectAdmin gebruikersnaam in
    - STAGING_PATH > Dit is het pad van het staging-domein, vanaf de domeinnaam, bijvoorbeeld: test.staging.burovoordeboeg.dev/public_html/content/themes/test/
    - Production_PATH > Dit is het pad van het production-domein, vanaf de domeinnaam, bijvoorbeeld: test.nl/public_html/content/themes/test/
13. Je kunt nu een build triggeren met een merge vanaf develop naar staging en het toevoegen van een tag. 