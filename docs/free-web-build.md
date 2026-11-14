# Gratis webbuild en handmatige publicatie

De webapp is statisch; er zijn geen AI, serverfuncties, accounts of databases nodig.

## Lokaal bouwen

Vereisten: Rust 1.95+, `wasm32-unknown-unknown` target en Trunk (`cargo install trunk --locked`).

```sh
rustup target add wasm32-unknown-unknown
cd apps/pdfcraft-web
trunk build --release
cd ../..
```

De statische site staat in `dist/web/`. Controleer of `dist/web/index.html` bestaat. Test lokaal met `python3 -m http.server 8765 --directory dist/web` en open `http://localhost:8765`.

## Gratis hosten

Publiceer de **inhoud** van `dist/web/` via handmatige drag-and-drop naar een gratis statische host (bijvoorbeeld Netlify, zolang het gratis quotum volstaat). Zet automatische betaalde upgrades uit en activeer geen betaalde add-ons. Controleer de actuele hostvoorwaarden en gebruikslimieten voor publicatie. De configuratie `netlify.toml` is aanwezig voor een eventuele repository-koppeling, maar deze handleiding kiest bewust handmatige deploys om buildverbruik te vermijden.

## Testchecklist

- Open een gewone PDF en een PDF met meerdere pagina's.
- Controleer zoeken, pagina draaien, samenvoegen en splitsen.
- Download een gewijzigde PDF en open die opnieuw.
- Controleer de browserontwikkeltools op fouten en ongewenste netwerkverzoeken.
- Test op mobiel en desktop; verifieer `.wasm` MIME-type en HTTPS.
- Publiceer geen aangepaste distributie met ArtCraft-merkassets: zie `docs/brand/LICENSE-brand.txt`.

Dit is een bouwinstructie, **geen** verklaring dat de build of deployment al succesvol is uitgevoerd.
