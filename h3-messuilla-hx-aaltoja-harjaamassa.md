# h3 Messuilla

*Tekijä: Aapo Tavio*

*Pohjana Tero Karvinen 2025: Verkkoon tunkeutuminen ja tiedustelu 2025 syksy, [Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h3-messuilla)*

## x) Läksyksi tästä tapahtumasta teidän tulee tehdä lyhyt raportti siitä, mitä yrityksiä tapasitte, mitä mielenkiintoisia palveluita / tuotteita (max 3kpl) löysitte. (Tässä alakohdassa ei tarvitse tehdä testejä koneella.)

Tapasin Uniqkeyn, YesWeHack:n, Tietoturva ry:n ja LocateRisk:n edustajia messuilla. Mielenkiintoisina tuotteina ja palveluina löysin Uniqkeyn salasananhallintasovelluksen, YesWeHack:n Bug Bounty ohjelman sekä Locate Risk:n Security Rating palvelun.

Uniqkeyn salasananhallintasovellus oli mielenkiintoinen, koska se on eurooppalainen. Tarkalleen ottaen tanskalainen. Monet muut salasananhallintasovellukset ovat nimittäin Kanadasta, kuten 1Password tai Yhdysvalloista, kuten Bitwarden.

Uniqkeyn verkkosivuilta (sekä messujen materiaaleista) pystyi näkemään ripauksen sovelluksen käyttöliittymästä, joka miellytti ainakin itseäni väritykseltään. Väreinä on käytetty tummanharmaata, valkoista ja neonvihreää, joka erottuu mielestäni hyvin ainakin 1Passwordista ja Bitwardenista, joissa molemmissa on käytetty sinistä ja valkoista. Toki sovelluksen teemaa saa varmaan vaihdettua ainakin tummaksi ja vaaleaksi, joka vaikuttanee paljon asiaan.  

(Uniqkey. URL: [Uniqkey](https://www.uniqkey.eu/)

1Password. URL: [1Password](https://1password.com/)

Bitwarden. URL: [Bitwarden](https://bitwarden.com/).)

YesWeHackin Bug Bounty ohjelma puolestaan tarjoaa yrityksille yksityisiä ja julkisia ohjelmia sekä reaaliaikaisia hakkeritapahtumia.

(YESWEHACK. URL: [YesWeHack Bug Bounty](https://www.yeswehack.com/product/bug-bounty-program).)

LocateRisk-yritys tarjoaa Security Rating palvelua, jolla voidaan tarkastella yrityksen IT-ratkaisuja tietoturvan kannalta kokonaisvaltaisesti. Sovellus tarjoaa myös korjaavia toimenpiteitä havaittuihin heikkouksiin, jotta hyökkäyspinta-alaa voitaisiin pienentää.

(LocateRisk. URL: [Ihre IT-Risikoanalyse - LocateRisk](https://locaterisk.com/en/landing/it-risikoanalyse/).)

## Käytettävän ympäristön ominaisuudet

- Isäntä
  
  - Koneen malli: HP Laptop 15s-eq3xxx
  
  - Käyttöjärjestelmä: Ubuntu 24.04.3 LTS
  
  - Prosessori: AMD Ryzen™ 7 5825U with Radeon™ Graphics × 16
  
  - Muisti: 16.0 GiB
  
  - Verkkokortti: Realtek Semiconductor Co., 802.11ax Wireless
  
  - Arkkitehtuuri: x86_64
  
  - Firmware version: F.20
  
  - Kernel Version: Linux 6.14.0-35-generic

- Paikallinen virtuaalikone
  
  - Virtualisointi: Virtualbox
  
  - Käyttöjärjestelmä: Kali GNU/Linux Rolling 2025.3
  
  - Xfce Versio: 4.20

# hx Aaltoja harjaamassa

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

- Hubacek 2019: [Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs](https://youtu.be/sbqMqb6FVMY?t=199) (Video, alkaen 3:19 ja päättyen 7:40. Yhteensä noin 4 min.)
  
  - URH (Universal Radio Hacker) on työkalu, jolla voidaan analysoida radiosignaaleja
  - Radiosignaalit voidaan muuttaa bittimuotoon URH:lla, jotta niitä voidaan tulkita

- Cornelius 2022: [Decode 433.92 MHz weather station data](https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html)
  
  - rtl_433 ohjelmalla voidaan avata koodia radiosignaaleista
  
  - URH:lla tavallinen "workflow" on käyttää
    
    1. Spektrin analysaattoria
    
    2. Kaapata signaalia
    
    3. Demodulointia

- Vapaaehtoinen, vaikeahko: Lohner 2019: [Decoding ASK/OOK_PPM Signals with URH and rtl_433](https://github.karllohner.com/SDR/Decoding/Example_2019-01-24/)

## a) WebSDR. Etäkäytä WebSDR-ohjelmaradiota, joka on kaukana sinusta ja kuuntele radioliikennettä. Radioliikenne tulee siepata niin, että radiovastaanotin on joko eri maassa tai vähintään 400 km paikasta, jossa teet tätä tehtävää. Käytä esimerkkinä julkista, suurelle yleisölle tarkoitettua viestiä, esimerkiksi yleisradiolähetystä. Kerro löytämäsi taajuus, aallonpituus ja modulaatio. Kuvaile askeleet ja ota ruutukaappaus. (Tehtävässä ei saa ilmaista sellaisen viestin sisältöä tai olemassaoloa, joka ei ole tarkoitettu julkiseksi. Voit sen sijaan kuvailla, miten sait julkisen radiolähetyksen kuulumaan kaiuttimistasi. Julkisten, esimerkiksi yleisradiolähetysten sisältöä saa tietysti kuvailla.)

**8.11.2025 Klo 18.21**

Tutkin tunnin signaaleja osoitteesta websdr.org. Löysin erilaisia yhdistelmiä koittamalla jotain ääntä, mutta en mitään kunnollisia kanavia. Kokeilin Utahissa ja Bordeauxissa olevia vastaanottimia.

![Bordeaux websdr](bordeaux-sdr.png)

**Kuva 1.** Bordeauxissa sijaitsevan vastaanottimen verkkosivu

Taajuus kuvassa on 3600.70 khz. Modulaatio oli LSB.

## b) rtl_433. Asenna rtl_433 automaattista analyysia varten. Kokeile, että voit ajaa sitä. './rtl_433' vastaa "rtl_433 version 25.02 branch..."

**8.11.2025 Klo 19.56**

Asensin rtl_433 ohjelman komennoilla

```bash
sudo apt-get update

sudo apt-get install rtl-433
```

## c) Automaattinen analyysi. Mitä tässä näytteessä tapahtuu? Mitä tunnisteita (id yms) löydät? [Converted_433.92M_2000k.cs8](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/samples/Converted_433.92M_2000k.cs8). Analysoi näyte 'rtl_433' ohjelmalla.

Kysyin ChatGPT:ltä "how to run file with rtl_433" ja sain vastauksena komennon

```bash
rtl_433 -r (tiedostopolku)
```

**9.11.2025 Klo 09.00**

![Tiedosto rtl-433](rtl-433-tiedosto-1.png)

**Kuva 2.** Osa tarkasteltavasta tiedostosta

Tiedostossa oli todennäköisesti jokin kodin turvajärjestelmä, koska "model: Proove-Security" ja "model: Nexa-Security" kohdissa olivat kentät "House Code". Löysinkin Nexa Systemin kotisivut, jotka liittyivätkin kodin IoT-laitteisiin (NEXA SYSTEMS. URL: [NexaSystem](https://nexasystem.com/)).

![Nexan ja prooven osa](nexa-proove.png)

**Kuva 3.** Nexa-Security ja Proove-Security sarakkeet

En löytänyt oikein hakukoneiden kautta tietoa, mikä oli "Group Call" sarake, mutta ChatGPT sanoi sen olevan broadcast-viestiin liittyvä. Eli jos arvona on "Yes" viesti on broadcast ja jos arvona on "No" viesti ei ole broadcast.

(ChatGPT. Syöte: what is group call in rtl_433)

![Group call sarake](group-call.png)

**Kuva 4.** Viesti ei ollut broadcast

## d) Too compex 16? Olet nauhoittanut näytteen 'urh' -ohjelmalla .complex16s-muodossa. Muunna näyte rtl_433-yhteensopivaan muotoon ja analysoi se. Näyte [Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/samples/Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s)

**9.11.2025 Klo 09.50**

Sain avattua tiedoston muuttamalla tiedostopäätteen tiedoston nimessä komennolla

```bash
mv Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.cs8
```

Minun piti toisinsanoen vaihtaa ".complex16s" muotoon ".cs8". Löysin ohjeen GitHubin keskustelusta.  

(GitHub. URL: [BMW GEN 3 TPMS signal decoding · Issue #2893 · merbanan/rtl_433 · GitHub](https://github.com/merbanan/rtl_433/issues/2893))

![Tiedosto auki](cs8.png)

**Kuva 5.** Alkuperäisellä tiedostopäätteellä tiedosto ei avautunut

Tiedosto "Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s", jonka sai ladattua tehtävän linkistä, on sama kuin "Converted_433.92M_2000k.cs8", joka oli tarkasteltavana c-kohdassa.

## e) Ultimate. Asenna URH, the Ultimate Radio Hacker.

**9.11.2025 Klo 13.44**

Katsoin tehtävän vinkeistä mallia, miten URH asennetaan. Siellä käytettiin pipx:ää.

Sain kuitenkin virheilmoituksen asennettaessa sitä.

![Virheilmoitus asennettaessa ohjelmaa](error-urh.png)

**Kuva 6.** Virheilmoitus asennettaessa URH ohjelmaa

Lähdin katsomaan lokitiedostoa, joka luki virheilmoituksessa.

![Lokitiedoston virheilmoitus](urh-error-log.png)

**Kuva 7.** Virheilmoitus lokitiedostossa

Lokitiedostossa luki, että tarvitsisin Cythonin. Latasin sen komennolla, joka luki virheilmoituksessa.

```bash
python3 -m pip install cython
```

Sain uudestaan virheilmoituksen

![Virheilmoitus asennettaessa cythonia](cython-error.png)

**Kuva 8.** Virheilmoitus asennettaessa Cythonia

Tajusin hieman surffailtuani netissä, että minun pitäisi varmaan laittaa komentoon "pip" sijaan "pipx". Sillä se onnistuikin.

![Pipx cythonin lataaminen](pipx-cython.png)

**Kuva 9.** Cythonin asennus onnistui

Mutta sama virheilmoitus edelleen

![Sama virheilmoitus asennettaessa](error-urh-2.png)

**Kuva 10.** Virheilmoitus jälleen asennettaessa URH:a

Kävin katsomassa jälleen virhelokia, mutta samanlainen ilmoitus sielläkin.

![Lokitiedoston samanlainen virheilmoitus](error-urh-log-2.png)

**Kuva 11.** Uusin virheilmoitus lokitiedostossa

Katsoin vielä ohjeita sivustolta [GitHub - jopohl/urh: Universal Radio Hacker: Investigate Wireless Protocols Like A Boss](https://github.com/jopohl/urh). Minulla alkoi aika loppumaan, joten päätin tehtävän tähän pisteeseen.

## Tarkastele näytettä [1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/samples/1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s). Siinä Nexan pistorasian kaukosäätimen valon 1 ON -nappia on painettu kolmesti. Käytä Ultimate Radio Hacker 'urh' -ohjelmaa.

En tehnyt kyseistä tehtävää.

## f) Yleiskuva. Kuvaile näytettä yleisesti: kuinka pitkä, millä taajuudella, milloin nauhoitettu? Miltä näyte silmämääräisesti näyttää?

En tehnyt kyseistä tehtävää.

## g) Bittistä. Demoduloi signaali niin, että saat raakabittejä. Mikä on oikea modulaatio? Miten pitkä yksi raakabitti on ajassa? Kuvaile tätä aikaa vertaamalla sitä johonkin. (Monissa singaaleissa on line encoding, eli lopullisia bittejä varten näitä "raakabittejä" on vielä käsiteltävä)

En tehnyt kyseistä tehtävää.

## h) Vapaaehtoinen: Sdr++. Kokeile [sdr++](https://www.sdrpp.org/) -sovellusta ja esittele sillä jokin "hei maailma" -tyyppinen esimerkki.

En tehnyt kyseistä tehtävää.

## i) Vapaaehtoinen, vaikeahko: GNU Radio. Asenne [GNU Radio](https://www.gnuradio.org/) ja tee sillä yksinkertainen "Hei maailma".

En tehnyt kyseistä tehtävää.

## Lähteet

Uniqkey. Password and Access Management for Businesses. European and Secure, as it should be. Luettavissa: [Uniqkey](https://www.uniqkey.eu/). Luettu: 7.11.2025.

1Password. Secure all sign-ins to every application from any device. Luettavissa: [1Password](https://1password.com/). Luettu: 7.11.2025.

Bitwarden. The most trusted password manager. Luettavissa: [Bitwarden](https://bitwarden.com/). Luettu: 7.11.2025.

YESWEHACK. UNLEASH THE POWER OF OUR HUNTERS WITH BUG BOUNTY. Luettavissa: [YesWeHack Bug Bounty](https://www.yeswehack.com/product/bug-bounty-program). Luettu: 7.11.2025.

LocateRisk. Security Rating. Luettavissa: [Ihre IT-Risikoanalyse - LocateRisk](https://locaterisk.com/en/landing/it-risikoanalyse/). Luettu: 7.11.2025.

ChatGPT. Kielimalli: GPT-5. Syöte: how to run file with rtl_433. Generoitu: 8.11.2025.

NEXA SYSTEM. Luettavissa: [NexaSystem](https://nexasystem.com/). Luettu: 9.11.2025.

ChatGPT. Kielimalli: GPT-5. Syöte: what is group call in rtl_433. Generoitu: 9.11.2025.

GitHub. 5.4.2024. BMW GEN 3 TPMS signal decoding #2893. Luettavissa: [BMW GEN 3 TPMS signal decoding · Issue #2893 · merbanan/rtl_433 · GitHub](https://github.com/merbanan/rtl_433/issues/2893). Luettu: 9.11.2025.

jopohl. GitHub. Luettavissa: [GitHub - jopohl/urh: Universal Radio Hacker: Investigate Wireless Protocols Like A Boss](https://github.com/jopohl/urh). Luettu: 9.11.2025.

<br>

<br>

<br>

<br>

<br>

<br>

*Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 3 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html*
