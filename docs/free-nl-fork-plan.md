# Gratis Nederlandstalige PDFCraft-fork — uitvoeringsplan

Status: technische verkenning (13 oktober 2026). Deze notitie is geen claim dat een deployment al werkt.

## Harde eisen

- Voor eindgebruikers gratis, zonder advertenties, abonnement, account, betaalmuur of watermerk.
- Voor de beheerder geen betaalde hosting, API, database, AI of domeinnaam.
- Geen AI-integratie.
- PDF's worden standaard lokaal in de browser verwerkt; geen serverupload.
- Gebruik alleen hosting en CI zolang ze aantoonbaar binnen gratis quota blijven. Bij risico op kosten: stop, niet automatisch upgraden.
- Bestaande broncode en licentievermeldingen behouden. Bij een aangepaste publieke distributie de ArtCraft-merkassets verwijderen/vervangen; zie `docs/brand/LICENSE-brand.txt`.

## Vastgesteld in de broncode

- Bestaande statische webbuild met Rust/WebAssembly: `apps/pdfcraft-web`.
- De distributie bestaat uit `index.html`, JavaScript, WASM en headerconfiguratie: `packaging/web/README.md`.
- `packaging/web/_headers` is bedoeld voor o.a. Netlify.
- Bestaande CI controleert de WASM-library, maar dat bewijst niet dat de volledige webapp gebouwd of gedeployed is.
- De README beschrijft het project expliciet als alpha; bestaande tekst bewerken en browserprinten hebben beperkingen.
- De bestaande lokalisatie ondersteunt Nederlands nog niet: `docs/localization.md`.

## Uitvoering en acceptatie

1. **Webbuild reproduceren.** Exacte benodigde Rust/Trunk-toolchain en buildstappen vastleggen; een volledige productie-WASM-build uitvoeren en controleren op foutmeldingen.
2. **Functionaliteit testen.** Openen, zoeken, samenvoegen, splitsen, pagina's draaien, formulierinvulling, downloaden en lokale privacy toetsen met test-PDF's. Niet-werkende functies niet als gereed presenteren.
3. **Nederlands toevoegen.** Eerst taalkeuze en kernnavigatie; vervolgens de volledige vertaalcatalogus en regressietests. Onvertaalde labels expliciet bijhouden.
4. **Branding veilig maken.** ArtCraft-merken uit gewijzigde distributie verwijderen of vervangen, licentie- en attributiebestanden behouden.
5. **Gratis hosting.** Alleen statische bestanden publiceren via een gratis host, bij voorkeur een bestaand gratis Netlify-account. Geen betaalde add-ons, buildminuten of domeinaankoop activeren. Gratis limieten vooraf controleren.
6. **Release controleren.** HTTPS, WASM MIME-type, caching, mobiele bruikbaarheid, downloads en de afwezigheid van onbedoelde documentuploads testen.

## Releasecriteria

- Productiebuild en browser-smoketests slagen.
- Er zijn geen betaalde dependencies of automatische facturatie.
- Geen AI, login, database of analytics.
- Nederlandstalige UI functioneert, inclusief taalwissel.
- Aangepaste publieke branding voldoet aan merkvoorwaarden.
- Gebruiker kan PDF's openen en opslaan zonder dat documentinhoud naar een backend wordt verstuurd.

## Beperkingen en risico's

Gratis cloudquota zijn niet onbeperkt; 0 euro kan alleen gegarandeerd worden zolang het gebruik binnen gratis limieten blijft en geen betaalde diensten geactiveerd worden. GitHub Actions op een publieke fork kan ook quota en beperkingen hebben. Een publieke site en een geslaagde build zijn nog niet geverifieerd.
