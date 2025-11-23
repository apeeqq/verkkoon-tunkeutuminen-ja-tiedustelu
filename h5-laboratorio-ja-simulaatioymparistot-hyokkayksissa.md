# h5 Laboratorio- ja simulaatioympäristöt hyökkäyksissä

*Tekijä: Aapo Tavio*

*Pohjana Tero Karvinen 2025: Verkkoon tunkeutuminen ja tiedustelu 2025 syksy*, [Verkkoon tunkeutuminen ja tiedustelu - Network Attacks and Reconnaissance](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h5-laboratorio--ja-simulaatioymparistot-hyokkayksissa)





## a) Tutustu seuraavaan työkaluun [GitHub - kgretzky/evilginx2: Standalone man-in-the-middle attack framework used for phishing login credentials along with session cookies, allowing for the bypass of 2-factor authentication](https://github.com/kgretzky/evilginx2) . Vastaa seuraaviin kysymyksiin

- Asensitko työkalun, jos asensit niin kirjoita miten sen teit.
- Mitä teit työkalun kanssa?
- Onnistuitko huijaamaan liikennettä



Päätin etten asenna työkalua, koska mininet harjoitusten kanssa minulla meni 10h jo aiemmin. Minulla ei ollut aikaisempaa kokemusta mininetin käytöstä, joten siihen tutustuminen vei jo paljon aikaa. Puhumattakaan yhteyksien saamisesta xtermin kautta hosteihin.



## b) Sinulla on käytössäsi mininet-ympäristö. Luo ympäristö, jossa voit tehdä TCP SYN-Flood hyökkäyksen.

- Kirjoita miten loit mininet ympäristön ja miten toteutit hyökkäyksen. 

**23.11.2025 Klo 19.45**

Lähdin ensimmäiseksi etsimään tietoa ohjelmasta, jolla voisi suorittaa TCP SYN-Flood hyökkäyksen. Löysinkin melko nopeasti linoden sivustolta artikkelin, jossa kerrottiin "hping3" ohjelmasta. Päätin kokeilla sitä.

(Novotny. URL: [How to Emulate a SYN Flood Attack With Kali Linux](https://www.linode.com/docs/guides/emulate-syn-flood-attack-with-kali-linux/))



Ajoin ensimmäiseksi komennot:

```bash
mininet@mininet-vm:~$ sudo apt-get update #Päivittää saatavien pakettien listan


mininet@mininet-vm:~$ sudo apt-get install hping3 #Lataa ja asentaa hping3-ohjelman
```



Loin helpoimman ja nopeimman tavan mukaan mininet ympäristön komennolla

```bash
sudo mn #Luo yhden OpenFlow kernel kytkimen liitettynä kahteen isäntään (päätteeseen) sekä kontrollerin
```

(Mininet. URL: [Mininet Walkthrough](http://mininet.org/walkthrough/#interact-with-hosts-and-switches))



Tämän jälkeen ajattelin, että saisin varmaan helpoiten python-demonilla kokeiltua TCP SYN-Flood hyökkäystä. Laitoin ensimmäiseksi python-demonin pystyyn.



![](/home/aapo/.config/marktext/images/2025-11-23-20-35-20-python-server.png)

**Kuva 1.** h2-päätteessä python-demoni pystyyn taustalle



Seuraavaksi katsoin top-ohjelmalla resurssien käyttöä h2-päätteellä, josta ilmeni varsinkin prosessorin vähäinen käyttö.



![](/home/aapo/.config/marktext/images/2025-11-23-20-36-43-top-before.png)

**Kuva 2.** Resurssien käyttö oli maltillista ennen hyökkäystä



Yllä olevassa kuvassa en ollut siis vielä ajanut hping3-ohjelmaa.

Aloitin hyökkäyksen, jonka jälkeen näkikin selvästi, kuinka erityisesti prosessorin kuormitus kasvoi olennaisesti.

![](/home/aapo/.config/marktext/images/2025-11-23-20-39-55-top-while-attack.png)

**Kuva 3.** Resurssien käyttöä hyökkäyksen aikana



Hyökkäyksessä toteutetulla ohjelmalla voisi säätää parametrejä, jolloin saisi vielä korkeamman kuormituksen. Aion kokeilla joskus apachen kanssakin hyökkäyksen simulointia, koska siinä saisi graafisen käyttöliittymän mukaan.

Kokeilin testien jälkeen, että itse asiassa minun ei olisi tarvinnut edes laittaa python-demonia pystyyn testatakseni hyökkäystä, koska paketit menivät silti perille saakka kohteeseen. En ole varma, mistä tämä johtui, mutta luulisin asian johtuvan palomuurin puutteesta, jolloin kaikki sisälle päin tuleva liikenne sallitaan kaikkiin portteihin.













## Lähteet

Mininet. Mininet Walkthrough. Luettavissa: [Mininet Walkthrough](http://mininet.org/walkthrough/#interact-with-hosts-and-switches). Luettu: 23.11.2025.

Novotny, J. 9.5.2024. How to Emulate a SYN Flood Attack With Kali Linux. Luettavissa: [How to Emulate a SYN Flood Attack With Kali Linux](https://www.linode.com/docs/guides/emulate-syn-flood-attack-with-kali-linux/). Luettu: 23.11.2025.

<br>

<br>

<br>

<br>

<br>

<br>

*Tätä dokumenttia saa kopioida ja muokata GNU General Public License (versio 3 tai uudempi) mukaisesti. http://www.gnu.org/licenses/gpl.html*










