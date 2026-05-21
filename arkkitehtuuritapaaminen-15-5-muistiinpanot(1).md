# Arkkitehtuuritapaamisessa 15.5. käsiteltyjä aiheita.

### Projektin scope
- Mikä on MVP?
    
    - Käyttäjä CRUD, login/logout
    - Kerho CRUD
    - Kirja CRUD
    - Äänestyssykli CRUD
	    1. Ehdota kirjoja
    	2. Ehdotus päättyy, äänestys alkaa
    	3. Äänestys päättyy, valitaan kirja luettavaksi

- Kuinka MVP siirtyy tietokantaskeemaan?

    - Hertta laittoi kommentteja tietokantatiedostoon, lisätkää mahdollisesti sykli-table?
        
- Kuinka tietokantaskeema siirtyy endpointteihin?

    **TEHTY**
    GET /books
    POST /books
    		
    		
    **TODO**
    /user
        POST
        GET -> auth
        PUT -> auth
        DELETE -> auth
    /bookclub -> auth
        POST -> auth
        GET -> auth
        PUT -> auth
        DELETE -> auth
    /book
        POST -> auth
        GET -> auth
        PUT -> auth
        DELETE -> auth
    	
    /bookClubMember
        POST -> auth
        GET -> auth
        PUT -> auth
        DELETE -> auth
    /cycle
        POST -> auth
        GET -> auth
        DELETE -> auth
        (ei tarvii PUT, koska ehdotuksen voi vain poistaa)

### Backend ja frontend autentikaatio

#### Backend
- JWT tai sessions -pohjainen ratkaisu
- Käyttäkää backendissä middlewarea, esim. jsonwebtoken

#### Frontend
- Tehkää fronttiin ProtectedRoute komponentti, jolla suojellaan autentikoidut reitit https://www.geeksforgeeks.org/reactjs/what-are-protected-routes-in-react-js/
- Frontissa auth state käyttäen esim. ContextAPI

### Datan validaatio
- Backendin validaatio PAKOLLISTA! Frontend suositeltavaa. Ei voi luottaa vain frontin validaatioon.
- Zod voisi olla hyvä Typescriptin kanssa https://zod.dev/
- Myös yup toimii sekä backissa että frontissa

### Frontend: reititys ja komponenttihierarkkia?
- Käytä React Routeria. Mieti mitkä komponentit on kaikilla sivuilla, esim. Footer, NavBar, SideBar ym. Nämä eivät mene reittien sisään. Routejen autentikaatio, esim. kirjautumisen ja kerhoon kuulumisen suhteen? Esimerkkireititys:

    <Footer/>
    <NavBar/>
    <SideBar/>
    <Routes>
        <Route
            path="/"
                element={
                    user ? <UserHomePage/> : <MainPage/>
                }
        />
        <Route
            path="/login"
                element={
                    user ? <UserHomePage/> : <LoginPage />
                }
        />
        <Route
            path="/"
                element={
                    user && user.isInClub ? <ClubView /> : <Navigate to="/" />
                }
        />
    </Routes>
    
Esimerkkirakenne:

### Testaaminen
- Aloittakaa heti projektin alusta
- Tehkää eniten unit-testejä, sitten integraatio, vähiten end-to-end
- Alottakaa backendin APIn unit-testaamisesta, sit frontendin komponentteja
- Esim. Jest on hyvä kirjasto

### CI/CD
Jos haluatte pelata varman päälle, ajakaa workflow kun mihin tahansa branchiin tulee push. Tää on safety first approach:

on:
    push:
        branches:
        - "**" 

Ajakaa ainakin näitä jobeja
    - testit ja lint -> varmistaa koodin laadun
    - build -> tehdään docker image
    - pushataan image image registryyn, jos workflow triggeröityi main branchista
        - Openshiftissä staging ja prod saa imagen täältä

Image registrynä voi käyttää esim. DockerHub, quay.io, Github Packages

### Saavutettavuus ja responsiivisuus
- Saavutettavuus auttaa ihmisiä jotka käyttää screen readereitä
- Semantic HTML
    - Esim. <footer> mielummin kuin <div>
https://www.w3schools.com/html/html5_semantic_elements.asp

- ARIA labels React componenteille
    - Esim. "aria-label: Click-Me"
https://www.geeksforgeeks.org/reactjs/aria-attributes-in-react-accessibility/

- Eslint pluginien käyttö. Eli lint antaa virheviestejä, jos et ole muistanut vaikka aria-labelia.
    - https://github.com/infofarmer/eslint-plugin-jsx-a11y
    - https://web.dev/articles/accessibility-auditing-react

- Reponsiivisuus: CSS media queryt eri ruutukoille

### Koodin laatu
- Strict Typescript
- Eslint

### Openshift deployment
- Ks. https://github.com/HY-TKTL/TKT20007-Ohjelmistotuotantoprojekti/blob/master/openshift/README.md
    - HUOM! HY asiakas varmaan haluaa että sovellus on tuotannossa myös kurssin jälkeen. Tällöin deploymentteihin ei käytetä OhTuprojektin **okd-cs-test-0** klusteria joka nuketetaan, vaan Tietotekniikkakeskuksen Openshiftiä https://onify.it.helsinki.fi/guide/openshift-guide?h=openshift-guide
        - Luukkaisen ohjeet tähän:
        "oleelliset: https://idm.helsinki.fi/web/portal/desktop.htm tulee luoda email-ryhmä jossa opiskelijat jäsenenä, suosittelen että ryhmän luo asiakas tai joku muu joka ei häivy yliopistolta lähiaikoina WBS (HY:n sisäinen tilinumero) asiakas kaivaa jostain, velotusta ei ole joten ei väliä onko websillä rahaa quotaan joku pienempi luku, vaikkapa 0.1 riittää, muistiin joku randomarvo vaikkapa 10[11:29 AM]kaikkea voi modata jälkikäteen, pääasia tehdä nopeesti, lomake ei miettimällä parane"

- Käytä Dockerfilessä multi-stage builds, koska pienempi tiedosto, parempi tuotannossa
https://www.geeksforgeeks.org/devops/what-is-an-multistage-dockerfile/
https://docs.docker.com/build/building/multi-stage/

- Voitte ottaa mallia MuViCon manifesteista, kuinka staging setupataan
https://github.com/MuViCo/MuViCo/tree/main/manifests


