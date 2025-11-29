# h4 NFC ja RFID

*Tekijä: Aapo Tavio*

*Pohjana Tero Karvinen 2025: Verkkoon tunkeutuminen ja tiedustelu 2025 syksy, [Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance]([Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h4-nfc-ja-rfid))*

## a) Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?

Minulla on RFID-laitteita ainakin puhelin, erilaisia kortteja ja passi. Puhelimessa ainakin Google Pay käyttää virtuaalista korttinumeroa, joka suojaa oikean kortinnumeron päätymisen vääriin käsiin. Lisäksi näytön lukituksen avaaminen ennen maksamista luo yhden kerroksen turvallisuudesta. (Google. URL: [Keep your payment info safe - Google Pay Help](https://support.google.com/googlepay/answer/7643925?hl=en#zippy=%2Cvirtual-cards).) Muuten en kauheasti RFID-tekniikkaa hyödynnä puhelimessani.

Kortit ovat suojattuna ainakin lompakossani olevan RFID-suojauksen ansiosta. Ainakin hiconsumptionin sivuilla olevan artikkelin mukaan RFID-suojaukset lompakoissa toimivat. Lompakoissa voidaan käyttää erilaisia materiaaleja suojaamaan RFID-urkinnalta, joita ovat ainakin metalli, vahvistettu nahka ja metalleilla käsiteltyjä kankaita. (Brehm. URL: [Tested: The 9 Best RFID-Blocking Wallets For EDC | HiConsumption](https://hiconsumption.com/style/best-rfid-blocking-wallets/#Do_RFID-Blocking_Wallets_Really_Work).) Toisaalta tässä blogikirjoituksessa sanotaan, että olisi paras testata kaikki korttipaikat, koska vain osa saattaa olla suojattuna (Pavlysko. URL: [How to Check If Your Wallet Has RFID Protection? | hidemont.com](https://hidemont.com/blog/post/how-to-check-if-your-wallet-has-rfid-protection)).

Passia en juuri koskaan kanna mukana. Tietenkin ulkomaille matkustettaessa se on mukana, joka voisikin teoriassa olla hyvin kriittinen urkinnalle. Ottaen huomioon passin olevan kuitenkin arvostetuin henkilöllisyystodistus, jonka myöntää Suomessa Poliisi, oletan passissa olevan hyvät suojaukset. Lentokentätkin olisivat teoriassa ainakin hyviä kohteita kalastella RFID-signaaleja, mutta onneksi turvatoimet ovat lentokentillä tiukkoja ja ottaen huomioon RFID:n lyhyen kantomatkan, tuskin tarvitsee kovin huolissaan olla. Aina on tietenkin hyvä noudattaa varovaisuutta ja tarkkailla ympäristöä.

## b) Tutustu APDU komentojen rakenteeseen (voit käyttää tekoälyä tutustumiseen)

Lähdin selvittämään ensimmäiseksi, mikä on APDU? APDU on lyhenne sanoista "application protocol data unit", joka on kommunikaatio yksikkö älykortin lukijan ja älykortin välillä älykorttien kontekstissa (Wikipedia. URL: [Smart card application protocol data unit - Wikipedia](https://en.wikipedia.org/wiki/Smart_card_application_protocol_data_unit)).

Teknisemmin ottaen APDU on taulukko tavuista. Tavut sisältävät tietoa, jotka ovat määritelty ISO 7816 standardissa. APDU-tyyppejä on olemassa kaksi, jotka ovat komento (command) ja vastaus (response). (Yubico. URL: [APDUs](https://docs.yubico.com/yesdk/users-manual/yubikey-reference/apdu.html).)

Kysyin lisäksi ChatGPT:ltä "what are APDU commands". Vastauksena sain samanlaista vastausta kuin Yubicolta ja Wikipediasta, mutta lisäksi tekoäly kertoi hyvin ja selkeästi komentojen ja vastausten rakenteesta. Vastauksessaan tekoäly kertoi APDU-komennon olevan strukturoitu paketti, joka lähetetään vastaanottavalle laitteelle (kortti). Komento kertoo vastaanottavalle laitteelle, mitä toimintoja vastaanottavan laitteen pitäisi suorittaa?

APDU-vastaus on tekoälyn mukaan vastaus komentoon. Yhdessä komento ja vastaus muodostavat APDU-keskustelun (APDU exchange). APDU-komento sisältää yleensä seitsemän kenttää, jotka ovat

- CLA = Luokka tavu (Class byte)

- INS = Komento/Ohjaus tavu (Instruction byte)

- P1 = Parametri 1

- P2 = Parametri 2

- Lc = Vastaanottavalle laitteelle lähetettävän datan pituus (Length of data sent to the card)

- Data = Komennon data (data field)

- Le = Vastauksen odotettu datan pituus (Expected length of data in response)

Valinnaisia kenttiä ovat Lc, Data ja Le. Toisinsanoen CLA, INS, P1 ja P2 ovat pakollisia kenttiä. Kenttien arvot muodostuvat heksadesimaaleista.

APDU-vastaus puolestaan sisältää datan (valinnainen) ja kaksi tilakoodia. Molemmat tilakoodit ovat yhden tavun kummatkin, joten yhteensä tilakoodit ovat vastauksessa kaksi tavua. Sain käsityksen tekoälyn vastauksesta, että tilakoodit ovat samankaltaisia tarkoitukseltaan kuin http-vastauksen tilakoodit.

Palasin tarkastelemaan aikaisemmin viittaamaani Yubicon sivua asiasta, joka tuki myös tekoälyn vastausta, koska tällä kertaa osasin yhdistellä eri tavalla asioita tekoälyn vastauksen perusteella. Yubicon sivulla todettiin, että maksimikoko yhdelle APDU-komennolle on 260 ja APDU-vastaukselle 258, jonka myötä ketjutus (chaining) on tarpeen, jos APDU-viesti ylittää maksimikoon. Oletan maksimikokojen yksiköiden olevan tavuja, koska kaikki yksiköt artikkelissa ovat tavuja.

## c) Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. (Vinkki, useimmat liittyvät henkilökortteihin)



Löysin mielenkiintoisen uutisen Fox Newsin sivuilta, joka kertoo "ghost tapping" nimisestä huijauksesta. Kyseessä on ainakin mielestäni vähän useampien huijauksien yhdistelmä kyseessä, kuin vain yksi. Perinteinen kohdelaitteen lähelle pääseminen ja sen luvatta lukeminen on yksi tapa.

Toinen on pahantahtoisen toimijan tekeytyminen hyväntekeväisyyden nimissä toimivaksi myyjäksi tai joksikin muuksi myyjäksi, joka ei ota vastaan kuin lähimaksulla suoritettavaa maksua. Myyjät veloittavat suuremman summan, josta on sovittu tai he veloittavat ensin pienemmän summan ja heti perään suuremman summan. Joillakin voi olla jopa lukijoita, joilla he yrittävät saada lompakon sisältä tai laukusta napattua signaaleja.

Suojautumiseen annetaan ohjeeksi yhdeksän kohdan lista, joka sisältää

1. RFID-suojaus teknologian hyödyntäminen

2. Varmista ennen kuin maksat

3. Ota välittömät ilmoitukset käyttöön

4. Ole hereillä paikoissa joissa on paljon väkeä

5. Seuraa tiliäsi säännöllisesti

6. Käytä maksusovellusten turvaominaisuuksia

7. Pidä maksusovellukset ja laitteet päivitettynä

8. Tallenna maksusovelluksiin vain tarpeelliset kortit

9. Raportoi epäilyttävästä toiminnasta välittömästi

(Knutsson. URL: [How to protect yourself from ghost-tapping payment card scams nationwide | Fox News](https://www.foxnews.com/tech/ghost-tapping-scam-targets-tap-to-pay-users).)



Artikkeli oli mielestäni mielenkiintoinen, koska siinä oli melko perinteinen tapa toteuttaa rikollista toimintaa, toisinsanoen mennä lähelle kohdelaitetta, joka on omistajan hallussa. Ja toisaalta artikkelissa oli ainakin itselleni tuntemattomampi tapa toteuttaa rikollista toimintaa, joka oli puolestaan tekeytyminen myyjäksi ja kiertelemällä julkisilla paikoilla keräämässä maksuja. Kaiken lisäksi uutinen oli hyvin tuore, joka osoittaa perinteisen tavan ja uudemman tavan olevan läsnä nykypäivän maailmassa.

Suojautumiskeinotkin ovat mielestäni melko perustavanlaatuisia, joista usein kuuluu puhuttavan, mutta tämä taas merkitsee mielestäni vain sitä, kuinka paljon suojautuminen ns. tavallisen tallaajan näkökulmasta perustuu perusasioihin? Perusasioilla pääsee usein jo pitkälle. Mielestäni myös uudenlainen hyökkäysmalli kiertelevänä myyjänä osoittaa toteen nykypäivänä usein kuultavaan väitteeseen, että tekniset laitteet ovat jo lähtökohtaisesti melko hyvin suojattuja, joten käyttäjä on heikoin lenkki kyberrikollisuudessa. Myyjä yrittää käyttää ihmisen heikkouksia hyväkseen, kuten aikaa, tarkkaavaisuutta ja huolimattomuutta.









## Lähteet

Brehm, E. 29.8.2024. Tested: The Best RFID-Blocking Wallets for Theft Prevention. Luettavissa: [Tested: The 9 Best RFID-Blocking Wallets For EDC | HiConsumption](https://hiconsumption.com/style/best-rfid-blocking-wallets/#Do_RFID-Blocking_Wallets_Really_Work). Luettu: 28.11.2025.

ChatGPT. Kielimalli: GPT-4o mini. Syöte: "what are APDU commands". Generoitu: 28.11.2025.

Google. Keep your payment info safe. Luettavissa: [Keep your payment info safe - Google Pay Help](https://support.google.com/googlepay/answer/7643925?hl=en#zippy=%2Cvirtual-cards). Luettu: 28.11.2025.

Knutsson, K. 4.11.2025. Ghost-tapping scam targets tap-to-pay users. Luettavissa: [How to protect yourself from ghost-tapping payment card scams nationwide | Fox News](https://www.foxnews.com/tech/ghost-tapping-scam-targets-tap-to-pay-users). Luettu: 29.11.2025.

Pavlysko, D. 13.3.2025. How to Check If Your Wallet Has RFID Protection?. Luettavissa: [How to Check If Your Wallet Has RFID Protection? | hidemont.com](https://hidemont.com/blog/post/how-to-check-if-your-wallet-has-rfid-protection). Luettu: 28.11.2025.

Wikipedia. 25.11.2025. Smart card application protocol data unit. Luettavissa: [Smart card application protocol data unit - Wikipedia](https://en.wikipedia.org/wiki/Smart_card_application_protocol_data_unit). Luettu: 28.11.2025.

Yubico. APDUs. Luettavissa: [APDUs](https://docs.yubico.com/yesdk/users-manual/yubikey-reference/apdu.html). Luettu: 28.11.2025.

<br>

<br>

<br>

<br>

<br>

<br>

*Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 3 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html*
