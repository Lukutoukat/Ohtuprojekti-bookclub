Miten mennyt

- otettiin likaa hommaa viime 
- syklin toiminta liian iso user story

- virheviestejä korjattu
- ehdotusvaihe jäi kesken
- äänestysvaihetta ei päästy aloittamaan
- salasanan palautusta ei saatu aloitettua

- UIn siistimistä



DEMO

- openshift toimii!!! Osa ongelmista itse aiheutettua, osa on ollut laitokselta.

- Käytetään shadcn komponentteja muokattavuuden vuoksi. Osaa komponenteista muokattu itse.

- Playwright fontti on hyvä! Teemaan on otettu vaikutteita kirjaston tunnelmasta.

- Invitet toimii koodilla

- kirjoja voi tallentaa formilla
    - toisteiset kuvaustekstit poistettu
    - mobiilinäkymä ja desktop otettu huomioon
        - menu palkki erilainen mobiililla


- kirjakerhon luominen onnistuu
    - kirjakerhoon voi lisätä syklin päivämäärillä
        - kalenterinäkymä hyvä
        - 24h aikavalinta pitää olla
    - kutsukoodilla voi liittyä kerhoon
    - kirjan ehdottaminen onnistuu tallennetuista kirjoista dropdownista
        - formilla ehdottaminen on tulossa
        - adminille näkyvät komponentit pitää näkyä vain adminille
    - dark theme
        - ruskehtava tumma teema on hyvä, erottuu muista harmaista teemoista
    - kerhoon liittyminen selkeämpään paikkaan

- etenkin fontti on hyvä, ulkonäkö ei näytä vibekoodatulta. Kalenteri on hyvä.
    kiillotusta: 
    - Book club kirjoitettu epäkonsistentisti
    - Väliotsikot konsistenteiksi
    - käyttäjähallinta/profiili sivupalkkiin
        - oonko kirjautunut? Miten kirjaudun ulos? Yms. sivupalkkiin
        - käyttäjäikoni tms.
    - favicon    
    - Yläpalkkiin oikeat routet/sivun nimet.
    - Sovellukselle joku hauska nimi
    - navigaatiopalkki, sivun sisältö, footeri
        - footeriin linkki githubiin, lisenssi, versionumero, yms.
        - footeri saa sivun näyttämään asiallisemmalta


TOIVEITA:

- toiseksi tullut kirja voisi tulla automaattisesti seuraavaan sykliin


Seuraava sprintti:

- pidetään sykli user story
- pitää siistiä olemassaolevaa koodia.
- Lisää testejä
-


TESTAAMINEN:

testit Jestillä ja vitest

    - Otetaan Playwright testaamiseen käyttöön, ainakin muutama testi



HUOMIOITA: 

- Elementtien välinen spacing vaikuttaa jotenkin väärältä
- miten marginit ja spacingit määritelty
    - teemaan voi määritellä elementtien väliset etäisyydet
    - raot voi määritellä 8px välisiksi kertoimiksi
        - esim 1=8px, 2=16px jne...
    - tällä hetkellä näyttää siltä että väleissä on random pikselimäärät
- ikonit palkissa aika kivat
    - voisiko nappulat sivupalkissa olla erivärisiä, esim logout punainen tms.
    - esim 4 eri väriä eri tyyppisille napeille
- saavutettavuus otettava huomioon
    - toimiiko sovellus mustavalkoisena
    - error viesteissä voisi lukea "error:"
- Yleisesti hyvää työtä
- 3 sprinttiä jäljellä
- paljon kiillotettavaa
- dokumentaatio laitettava kuntoon
    - mahdollinen jatkokehitys syksyllä
- seuraava sprintti hiomista, katsotaan sitten miten menee
- onko helmet integraatio mahdollinen?
    - ehkä? Optimistisuutta löytyy, mutta API vaikuttaa osittain vähän hankalalta.
    - Jos pakolliset toiminnot saadaan valmiiksi, voitaisiin siirtyä tähän

- jos kirja tulee toiseksi, kuka sen omistaa, kuka voi muokata yms.
    - tähän keksitään ratkaisut

- gittiin voi laittaa keskeneräistä kamaa, nyt rikkinäisellä koneella on UI uudistuksia.

- Tiimityö toimii hyvin kun ollaan läsnä. Sprintit on yleisesti parantuneet. Viimeisin sprintti oli hankala liian ison user storyn vuoksi.
    - onko tullut omia rooleja?
        - hertta ei ole johtaja.
        - kommunikaatio toimii
        - nea ja hertta tehnyt paljon yhdessä
        - frontend on matiaksella parhaiten hanskassa
        - openshift eemilillä parhaiten hanskassa
        - kaikki tehnyt hyvin hommia

- production openshiftiin
    - tässä vielä ongelmia


mielummin vähemmän koodia joka toimii kuin paljon jota ei toimi. Vajavainen toiminnallisuus korjattava ja sykli toimimaan.

Ei oteta stressiä, esim jos ei kerkeä helmet integraatiota

seuraava tapaaminen Maanantaina: Riku 14.30 toivottavasti kirjastossa

Vikalla sprintillä ei kannata ottaa uusia ominaisuuksia.

Voidaan olla ylpeitä tehdystä työstä.