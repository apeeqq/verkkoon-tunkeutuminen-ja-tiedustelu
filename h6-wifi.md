# h6 WiFi

*Tekijä: Aapo Tavio*

*Pohjana Tero Karvinen 2025: Verkkoon tunkeutuminen ja tiedustelu 2025 syksy, [Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h6-wifi)*

## a) Tutustu wifi challenge lab 2.1 harjoitus ympäristöön ja käytä tarvittaessa hyväksesi jo olemassa olevia ohjeita.

## b) Kirjoita raportti siitä mitä opit ja mitkä asia yllättivät sinut kun tutustuit harjoitukseen.

En ehtinyt tekemään kaikkia tehtäviä labista, mutta kuitenkin ainakin puolet. Opin uusia tapoja tarkkailla langattomia verkkoja. Tarkkailin niitä mm. aircrack-ng:n työkaluilla.

Yhdistin myös manuaalisesti langattomaan verkkoon laitteeni konfigurointitiedoston avulla, jonka jälkeen hain IP-osoitteen laitteelleni dhcp-asiakas ohjelmalla. Lisäksi muutin MAC-osoitteeni ja kaappasin liikennettä tunkeutuakseni reitittimen hallintaan.

Verkkojen salasanoja tuli murrettua aircrackillä tekstitiedostoa yleisistä salasanoista hyödyntäen. Wiresharkillakin tuli tarkasteltua kaapattua liikennettä selvittääkseni, mikä oli weppipalvelin tietyssä verkossa. Sain sen selville, koska pystyin kaappaamaan weppipalvelimen tunnistautumiseen käytettyä liikennettä.

Asetin rogue access pointin, eli valheellisen tukiaseman, kaappaamaan tunnistautumispyyntöjä. Nämä olivat salattuja, joten yritin hashcat ohjelmaa hyödyntämällä murtaa salauksen, mutta en saanut pitkien selvittelyjenkään jälkeen murrettua, koska ilmeisesti kaappaamani tiedosto oli väärässä muodossa.

Minua yllätti erityisesti, kuinka haavoittuva langaton verkko on. Tiesin olevan mahdollista murtaa langattomia verkkoja, mutta se että murtautuminen oli näinkin helppoa, oli yllätys.

### SSID, ESSID ja BSSID

Opin, että SSID on "Service Set Identifier", joka on langattoman verkon nimi, jota lähetetään yleensä broadcast-viestinä päätelaitteille. SSID helpottaa käyttäjien liittymistä langattomaan verkkoon.

ESSID on puolestaan "Extended Service Set Identifier", joka kertoo laajemmin monen AP:n (Access Point) verkon nimen. ESSID mahdollistaa helposti kantaman laajentamisen useata AP:ta hyödyntämällä.

BSSID on "Basic Service Set Identifier", joka kertoo jokaisen AP:n fyysisen ja uniikin osoitteen, toisinsanoen MAC-osoitteen. BSSID on hyödyllinen verkkojen hallinnoinnissa.

(Sainikhil. URL: [Understanding SSID, BSSID, and ESSID in Wi-Fi Networks](https://www.linkedin.com/pulse/understanding-ssid-bssid-essid-wi-fi-networks-kola-sainikhil-is7bc).)

## c) Miten suhtautumisesi WLanin turvallisuuteen muuttui sen jälkeen kun teit harjoitukset?

Suhtautumiseni on todella paljon skeptisempi langattomia verkkoja kohtaan, kuin ennen harjoitusta. Minun pitääkin tulevaisuudessa opiskella vielä lisää keinoja, joilla voin vahvistaa langattomien verkkojen turvallisuutta. Tekniikat toki kehittyvät kovin, joten onkin itsestäänselvää, että uusia keinoja puolustautumiseen on syytä opetella ikuisesti. Suojautuminen on kuitenkin aina kilpajuoksua pahantahtoisten toimijoiden kanssa. On pysyttävä toisinsanoen aina askeleen edellä heitä.

<br>

<br>

<br>

<br>

<br>

<br>

## Lähteet

Sainikhil, K. 29.12.2024. Understanding SSID, BSSID, and ESSID in Wi-Fi Networks. LinkedIn. Luettavissa: [Understanding SSID, BSSID, and ESSID in Wi-Fi Networks](https://www.linkedin.com/pulse/understanding-ssid-bssid-essid-wi-fi-networks-kola-sainikhil-is7bc). Luettu: 14.11.2025.

*Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 3 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html*
