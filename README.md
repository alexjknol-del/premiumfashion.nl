# Premium Fashion — premiumfashion.nl

Statische website (losse HTML/CSS/JS bestanden, geen buildstap nodig).

## Inhoud

- `index.html` — homepage met merkuitlichting
- `over-ons.html` — over Premium Fashion + persona Noor Willemsen
- `nieuws.html` — overzicht blogartikelen
- `nieuws-*.html` — losse blogartikelen
- `contact.html` — contactpagina (mailto, geen formulier)
- `privacybeleid.html`, `cookiebeleid.html` — juridische pagina's
- `404.html` — foutpagina
- `assets/` — stylesheet, script, favicon en de illustratie van Noor
- `robots.txt`, `sitemap.xml` — voor zoekmachines
- `_headers` — beveiligingsheaders voor Cloudflare Pages

## Publiceren via GitHub + Cloudflare Pages

**Stap 1 — GitHub repository aanmaken**

1. Ga naar github.com en log in (of maak een gratis account aan).
2. Klik rechtsboven op **New repository**.
3. Geef de repo een naam, bijvoorbeeld `premiumfashion-website`, en kies **Private** of **Public**.
4. Maak de repository aan zonder README (deze bestaat al).

**Stap 2 — bestanden naar GitHub pushen**

Deze map is al een git-repository met een eerste commit. Open een terminal in deze projectmap en voer uit:

```bash
git branch -M main
git remote add origin https://github.com/<jouw-gebruikersnaam>/premiumfashion-website.git
git push -u origin main
```

(Was de map al eerder ergens anders geïnitialiseerd of wil je opnieuw beginnen, dan werkt ook de standaard volgorde: `git init`, `git add .`, `git commit -m "..."`, gevolgd door de branch- en push-commando's hierboven.)

**Stap 3 — Cloudflare Pages koppelen**

1. Log in op dash.cloudflare.com.
2. Ga naar **Workers & Pages** > **Create application** > **Pages** > **Connect to Git**.
3. Selecteer de zojuist aangemaakte GitHub repository.
4. Bij de buildinstellingen:
   - **Framework preset:** None
   - **Build command:** (leeg laten)
   - **Build output directory:** `/` (de hoofdmap zelf)
5. Klik op **Save and Deploy**. Na een paar seconden staat de site live op een `*.pages.dev` adres.

**Stap 4 — eigen domein koppelen**

1. Ga in het Cloudflare Pages project naar **Custom domains** > **Set up a custom domain**.
2. Vul `premiumfashion.nl` in (en eventueel `www.premiumfashion.nl`).
3. Als het domein al bij Cloudflare als DNS-zone staat, worden de benodigde DNS-records automatisch toegevoegd. Staat het domein bij een andere provider, verhuis dan eerst de nameservers naar Cloudflare via **DNS** > **Nameservers** in het Cloudflare dashboard.
4. Na de DNS-verificatie is de site bereikbaar op premiumfashion.nl, inclusief automatisch SSL-certificaat.

Vanaf dit moment zorgt elke `git push` naar de `main`-branch automatisch voor een nieuwe deploy.

## Let op vóór livegang

- **Privacybeleid en cookiebeleid** zijn geschreven op basis van de huidige, eenvoudige opzet van de site (geen eigen cookies, geen formulieren, geen analytics). Voeg later analytics of andere cookies toe, werk dan eerst het cookiebeleid bij en plaats een cookiemelding waar nodig.
- In het privacybeleid is bewust geen KvK-nummer of vestigingsadres opgenomen omdat dat niet is aangeleverd. Voeg dit toe als daar voor de eigen situatie een wettelijke verplichting toe bestaat.
- Laat de juridische pagina's bij twijfel nog even beoordelen door een jurist, dit is een zorgvuldig opgestelde basis maar geen juridisch advies.
