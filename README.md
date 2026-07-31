# NVHP consumentenartikelen — GitHub Pages

Statische site voor maandelijkse consumentenartikelen waarbij elke hypothecair
planner via zijn persoonlijke link (`?advisor=nummer`) als afzender verschijnt,
met eigen contactblok (naam, kantoor, telefoonnummer, e-mail).

## Structuur

```
index.html                          Artikeloverzicht (openbaar)
artikelen/
  2026-08-verduurzaming.html        Voorbeeldartikel met fictieve planners (101, 102, 103)
beheer/
  generator.html                    Maakt van CSV + artikeltekst een nieuwe artikelpagina
  deellinks.html                    Maakt per planner persoonlijke links + Facebook/LinkedIn-deellinks + mails
  handleiding.html                  Volledige handleiding (werkwijze, testchecklist, AVG/Wft)
.nojekyll                           Zorgt dat GitHub Pages alle bestanden ongewijzigd serveert
```

## Eenmalige inrichting (± 5 minuten)

1. Maak op github.com een nieuwe repository, bijvoorbeeld `nvhp-artikelen`
   (publiek; privé + Pages vereist een betaald abonnement — zie AVG-punt onderaan).
2. Upload de volledige inhoud van deze map: **Add file → Upload files**,
   sleep alle bestanden en mappen erin, klik **Commit changes**.
3. Ga naar **Settings → Pages**. Kies bij *Source*: **Deploy from a branch**,
   branch `main`, map `/ (root)`. Klik **Save**.
4. Na 1–10 minuten staat de site live op:
   `https://<gebruikersnaam>.github.io/nvhp-artikelen/`

## Testen

- Overzicht: `https://<gebruikersnaam>.github.io/nvhp-artikelen/`
- Artikel zonder afzender (toont zoeker-fallback):
  `…/artikelen/2026-08-verduurzaming.html`
- Artikel mét afzenderblok (fictieve planner):
  `…/artikelen/2026-08-verduurzaming.html?advisor=101`
  (probeer ook `102`, `103` en een niet-bestaand nummer)
- De overzichtspagina geeft `?advisor=…` automatisch door aan de artikellinks.

## Maandelijkse werkwijze

1. Open `beheer/generator.html` lokaal in de browser (of via de live site).
2. Plak de leden-CSV, vul het artikel in, download `artikel.html`.
3. Hernoem het bestand (bijv. `2026-09-rentevast.html`) en upload het naar de
   map `artikelen/` in de repository.
4. Voeg op `index.html` een blok toe voor het nieuwe artikel (voorbeeldblok
   staat in het bestand; nieuwste bovenaan).
5. Mail elke planner zijn persoonlijke link via `beheer/deellinks.html`
   (bulk-tab: `Naam;Nummer;E-mail` plakken → per planner "Mail adviseur";
   gemiste planner: knop "Herinnering").

Wijziging in plannerdata (nummer erbij, telefoonnummer gewijzigd): CSV
aanpassen, hetzelfde artikel opnieuw genereren en het bestand in `artikelen/`
overschrijven. Oude artikelen laten staan zodat gedeelde links blijven werken.

## Eigen domein (aanbevolen voor productie)

`github.io` in de adresbalk oogt niet professioneel bij financiële content.
Koppel een subdomein, bijv. `artikelen.hypothecairplanner.nl`:

1. Laat de DNS-beheerder een CNAME-record aanmaken:
   `artikelen.hypothecairplanner.nl → <gebruikersnaam>.github.io`
2. Vul het subdomein in bij **Settings → Pages → Custom domain** en zet
   **Enforce HTTPS** aan zodra het certificaat is uitgegeven.

## AVG en compliance

- Alle gekoppelde CSV-velden staan in de broncode van de openbare pagina's.
  Neem alleen planners op met vastgelegde toestemming, per planner alleen de
  velden die hij/zij wil publiceren.
- **Let op bij een publieke repository:** de git-historie bewaart ook oude
  versies. Gegevens van een planner die zich terugtrekt verdwijnen dus niet
  door alleen te overschrijven. Praktische omgang: beperk de ingesloten data
  tot wat toch al openbaar is (naam, kantoor, zakelijk telefoonnummer), en
  gebruik bij een verwijderverzoek een nieuwe repository of herschrijf de
  historie. Alternatief: betaald GitHub-abonnement met privé-repository.
- De artikelen zijn openbare informatieve uitingen over financiële producten
  (Wft): laat elk artikel plus disclaimer vóór publicatie beoordelen door de
  compliance-verantwoordelijke. Zie `beheer/handleiding.html` voor het
  volledige overzicht.
