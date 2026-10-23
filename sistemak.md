---
layout: page
title: Sistemak
---
# Sistema eragileak ezartzea
<div align="left">

<img src="img/image46.png" alt="Azala" width="600" style="max-width:100%;">
</div>

# Aurkibidea

- [1. Lehen atala](#1-lehen-atala)
- [2. Sistemaren instalazioa](#2-sistemaren-instalazioa)
- [3. Oinarrizko konfigurazioak](#3-oinarrizko-konfigurazioak)
  - [IP](#ip)
  - [Erabiltzaileak eta taldeak sortzea](#erabiltzaileak-eta-taldeak-sortzea)
  - [Erabiltzaileak eta taldeak administratzea](#erabiltzaileak-eta-taldeak-administratzea)
  - [Kuotak ezartzea](#kuotak-ezartzea)
  - [RAID](#raid)
  - [Babeskopia](#babeskopia)
- [4. Zerbitzuak](#4-zerbitzuak)
  - [Instalazioak](#instalazioak)
  - [DNS](#dns)
  - [IIS](#iis)

# 1. Lehen atala

### Zer da sistema informatiko bat?

Sistema informatiko bat informazioa jaso, gorde, prozesatu eta komunikatzeko elkarrekin lan egiten duten elementu fisikoen, programen eta datuen multzoa da. Hiru atal nagusi ditu:

- **Hardwarea**: sistemaren osagai fisikoak (prozesadorea, memoria, disko gogorra, periferikoak…). Datuak prozesatu, gorde eta transmititzen ditu.
- **Softwarea**: programa eta aplikazioen multzoa (sistema eragilea, aplikazioak, utilitateak). Hardwareari zer egin behar duen esaten dio.
- **Pertsonak** (giza elementua): sistema erabili, garatu eta mantentzen dutenak (erabiltzaileak, programatzaileak, administratzaileak).

### Zer da sistema eragilea?

Hardwarearen, erabiltzaileen eta aplikazioen arteko bitartekaria den softwarea da, eta funtzio hauek ditu:

1. **Prozesuen kudeaketa**: planifikazioa, sinkronizazioa, komunikazioa.
2. **Memoriaren kudeaketa**: esleipena, memoria birtuala, babesa.
3. **Fitxategi-sistemaren kudeaketa**: fitxategiak eta direktorioak antolatu, atzitu eta babestu.
4. **Sarrera/irteeren kudeaketa**: gailuak kontrolatu (driverren bidez).
5. **Segurtasuna eta babesa**: erabiltzaileen autentifikazioa, baimenak.
6. **Erabiltzaile-interfazea**: komando-lerroa (CLI) edo interfaze grafikoa (GUI).
7. **Sareen eta baliabideen kudeaketa**: komunikazioa eta erabilera-kontabilitatea.

Sistema eragileak elkarrengandik oso ezberdinak izan daitezke, baina guztiek arkitektura hau jarraitzen dute:

1. **Nukleoa (kernel)**: sistemaren muina; hardwarearekin zuzenean lan egiten du (prozesuak, memoria, gailuak, sistema-deiak).
2. **Sistema-deiak (API)**: aplikazioek kernelaren zerbitzuak eskatzeko bidea.
3. **Shell edo interfazea**: erabiltzailearen eta kernelaren arteko komunikazioa.
4. **Aplikazioak eta erabiltzailea**.

### Sistema eragile ezberdinak

|  | **Windows** | **macOS** | **Linux (Ubuntu, Debian, RHEL…)** | **Android** | **iOS** |
|---|---|---|---|---|---|
| **Bertsio nagusiak** | Windows 10 (euskarri amaitua), Windows 11, Windows Server | Bertsio berriena: macOS 26 "Tahoe" eta ondorengoak | Ubuntu LTS (24.04, 26.04), Debian stable, RHEL | Android 14, 15, 16… | iOS 26 eta ondorengoak |
| **Lizentzia** | Jabedunekoa, ordainpekoa (OEM, retail, bolumen-lizentziak) | Jabedunekoa, Apple ekipoekin dator, eguneraketak doakoak | Software librea (GPL), doakoa. RHEL/SUSE: ordainpeko euskarria | AOSP (Apache 2.0) irekia, baina Google zerbitzuak lizentziapean | Itxia, Apple gailuetan soilik |
| **Gutxieneko eskakizunak** | 64 biteko CPU, 4 GB RAM, 64 GB disko, TPM 2.0, UEFI | Apple Silicon edo Intel Mac bateragarriak, 8 GB RAM gomendatua | Oso aldakorra: Ubuntu Desktop ≈ 4 GB RAM, 25 GB. Banaketa arinak: 512 MB-ekin | Fabrikatzailearen hardwarea (ARM batez ere) | Apple gailu bateragarriak |
| **Ezaugarriak** | Hardware- eta software-bateragarritasun handia, GUI intuitiboa, joko-euskarria | Diseinu-ekosistema integratua, UNIX oinarria, segurtasun ona | Egonkorra, segurua, pertsonalizagarria, kontsola indartsua, kodea irekia | Ukitzeko interfazea, aplikazio-denda zabala, pertsonalizagarria | Itxia, segurua, errendimendu optimizatua, eguneraketa luzeak |
| **Aplikazio-eremuak** | Etxea, bulegoa, enpresak, jokoak | Diseinua, ekoizpen multimedia, garapena | Zerbitzariak, hodeia, garapena, ikerketa, IoT, superkonputazioa | Mugikorrak, tabletak, telebistak, auto-sistemak | Mugikorrak eta tabletak (iPhone, iPad) |

# 2. Sistemaren instalazioa

Hasteko, zerbitzariarentzat zein software erabiliko dugun aukeratuko dugu. Makina birtualean dena egingo dugunez, VirtualBox erabiliko dugu, Windows Server 2025 Standard batekin.

<div style="break-inside: avoid; page-break-inside: avoid;">

Honekin hasteko, VirtualBox-en sartu eta makina berri bat sortuko dugu.

<div align="left">
<img src="img/image18.png" alt="Irudia: Honekin hasteko, VirtualBox-en sartu eta makina berri bat sortuko dugu" width="468" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehenik, makinaren izena, ISO-a eta bertsioa aukeratu beharko ditugu.

<div align="left">
<img src="img/image79.png" alt="Irudia: Lehenik, makinaren izena, ISO-a eta bertsioa aukeratu beharko ditugu" width="600" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gero, hardware-konfigurazioak ezarri behar dira, hala nola RAM-a, CPU-a eta biltegiratzea.

<div align="left">
<img src="img/image75.png" alt="Irudia: Gero, hardware-konfigurazioak ezarri behar dira, hala nola RAM-a, CPU-a eta biltegiratzea" width="600" style="max-width:100%;">
</div>

<div align="left">
<img src="img/image21.png" alt="Irudia: Gero, hardware-konfigurazioak ezarri behar dira, hala nola RAM-a, CPU-a eta biltegiratzea" width="550" style="max-width:100%;">
</div>

</div>

Hau eginda, makina abiarazteko prest egongo da.

<div style="break-inside: avoid; page-break-inside: avoid;">

Abiarazi ondoren, lehenengo gauza hizkuntza aukeratzea galdetuko dizu (ISO-aren arabera aldatzen da).

<div align="left">
<img src="img/image33.png" alt="Irudia: Abiarazi ondoren, lehenengo gauza hizkuntza aukeratzea galdetuko dizu (ISO-aren…" width="520" style="max-width:100%;">
</div>

</div>

Gero bertsioa aukeratuko dugu; gure kasuan, Standard bertsioa.

<div style="break-inside: avoid; page-break-inside: avoid;">

Bertsio bakoitzak bere eskakizunak eta ezberdintasunak ditu. Core bertsioak, alde batetik, ez dauka interfaze grafikorik, terminal huts bat baizik. Datacenter bertsioa askoz garestiagoa da, eta tarifa gailuak dituen nukleo bakoitzeko ordaintzen da, baina ez dauka mugarik birtualizazioan edo kudea dezakeen hardware kantitatean. Standard bertsioa, berriz, lizentzia ordaindu eta kito.

<div align="left">
<img src="img/image67.png" alt="Irudia: Bertsio bakoitzak bere eskakizunak eta ezberdintasunak ditu. Core bertsioak, alde…" width="499" style="max-width:100%;">
</div>

</div>

Sistemaren lizentzia eskatuko dizu; ez daukazula aukeratu beharko duzu. Gero, baldintzak onartu beharko dituzu.

<div style="break-inside: avoid; page-break-inside: avoid;">

Orri honetan, instalatzeko aukera hautatu beharko duzu, ez dugulako lehendik instalatutako sistemarik.

<div align="left">
<img src="img/image6.png" alt="Irudia: Orri honetan, instalatzeko aukera hautatu beharko duzu, ez dugulako lehendik…" width="472" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, sistema zein gailutan instalatu nahi duzun aukeratu beharko duzu. Honekin soilik EFI partizioa sortuko da diska horretan, gure sistema eragilea hau erabilita abiarazteko.

<div align="left">
<img src="img/image4.png" alt="Irudia: Orain, sistema zein gailutan instalatu nahi duzun aukeratu beharko duzu. Honekin…" width="385" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Eta pantaila honetan, instalazioa amaitu arte itxaron besterik ez duzu egin behar.

<div align="left">
<img src="img/image25.png" alt="Irudia: Eta pantaila honetan, instalazioa amaitu arte itxaron besterik ez duzu egin behar" width="414" style="max-width:100%;">
</div>

</div>

# 3. Oinarrizko konfigurazioak

Gure zerbitzariak ondo funtzionatzeko oinarrizko konfigurazio batzuk behar ditu.

## IP

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehenik, IP finko bat ezarriko dugu. Ireki "Configuración" > "Red e internet" > "Ethernet" > "Asignación IP" > "Manual", eta jarri nahi duzun IP-a. Ez badakizu zein den Gateway-aren IP-a, ireki cmd eta idatzi hau:

<div align="left">
<img src="img/image94.png" alt="Irudia: Lehenik, IP finko bat ezarriko dugu. Ireki Configuración > Red e internet > Ethernet >…" width="600" style="max-width:100%;">
</div>

<div align="left">
<img src="img/image61.png" alt="Irudia: Lehenik, IP finko bat ezarriko dugu. Ireki Configuración > Red e internet > Ethernet >…" width="384" style="max-width:100%;">
</div>

</div>

## Erabiltzaileak eta taldeak sortzea

Pertsona bat baino gehiagoko lan-eremu batean, denek erabiltzaile bera izatea kaosa izango litzateke. Horregatik, bakoitzari bere erabiltzailea sortuko diogu.

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau egiteko, sakatu `Win+X` eta ireki "Administración de equipos".

<div align="left">
<img src="img/image26.png" alt="Irudia: Hau egiteko, sakatu Win+X eta ireki Administración de equipos" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gero, joan "Usuarios y grupos locales" atalera eta, bertan, "Usuarios" karpetara.

<div align="left">
<img src="img/image15.png" alt="Irudia: Gero, joan Usuarios y grupos locales atalera eta, bertan, Usuarios karpetara" width="138" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Barruan, eskuineko klika erabilita, "Usuario nuevo" sortuko dugu.

<div align="left">
<img src="img/image19.png" alt="Irudia: Barruan, eskuineko klika erabilita, Usuario nuevo sortuko dugu" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Izen bat emango diozu; gainerakoa aukerakoa da, baina pasahitza jartzea gomendatzen da. Guk horrela egingo dugu.

<div align="left">
<img src="img/image74.png" alt="Irudia: Izen bat emango diozu; gainerakoa aukerakoa da, baina pasahitza jartzea gomendatzen…" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Erabiltzaileak sortu ondoren, taldeak sortu beharko ditugu, bakoitzari talde bidez baimen ezberdinak emateko. Horretarako, leiho berean, joan "Grupos" atalera.

<div align="left">
<img src="img/image65.png" alt="Irudia: Erabiltzaileak sortu ondoren, taldeak sortu beharko ditugu, bakoitzari talde bidez…" height="222" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image13.png" alt="Irudia: Erabiltzaileak sortu ondoren, taldeak sortu beharko ditugu, bakoitzari talde bidez…" height="222" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Taldeei izena eman eta bertan aukeratu ahal duzu nor egongo den talde bakoitzean.

<div align="left">
<img src="img/image49.png" alt="Irudia: Taldeei izena eman eta bertan aukeratu ahal duzu nor egongo den talde bakoitzean" height="222" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image5.png" alt="Irudia: Taldeei izena eman eta bertan aukeratu ahal duzu nor egongo den talde bakoitzean" height="222" style="max-width:100%;">
</div>

</div>

## Erabiltzaileak eta taldeak administratzea

Erabiltzaile hauek sortu ondoren, haien segurtasuna bermatzea izango da gure zeregina.

Lehenik, pasahitz-arauak aplikatuko ditugu, beste inork gure erabiltzailea erabili ezin dezan.

<div style="break-inside: avoid; page-break-inside: avoid;">

Ireki "Directiva de seguridad local".

<div align="left">
<img src="img/image56.png" alt="Irudia: Ireki Directiva de seguridad local" width="299" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Bilatu "Directivas de cuenta" > "Directivas de contraseñas"; hemen dituzu pasahitzentzako ezarpen guztiak. Kasu honetan, konplexutasun minimoa eta luzera minimoa aldatuko ditugu, erabiltzaileak ez beste inork pasahitza jakin ez dezan.

<div align="left">
<img src="img/image7.png" alt="Irudia: Bilatu Directivas de cuenta > Directivas de contraseñas; hemen dituzu pasahitzentzako…" width="600" style="max-width:100%;">
</div>

<div align="left">
<img src="img/image12.png" alt="Irudia: Bilatu Directivas de cuenta > Directivas de contraseñas; hemen dituzu pasahitzentzako…" height="132" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image63.png" alt="Irudia: Bilatu Directivas de cuenta > Directivas de contraseñas; hemen dituzu pasahitzentzako…" height="132" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

"Directivas de bloqueo de cuenta" atalean, pasahitz-hutsegite kopuru maximo bat ezarriko dugu; erabiltzailea ez den norbaitek behin eta berriz huts egiten badu, segurtasunagatik kontua blokeatu egingo da.

<div align="left">
<img src="img/image3.png" alt="Irudia: Directivas de bloqueo de cuenta atalean, pasahitz-hutsegite kopuru maximo bat ezarriko…" width="400" style="max-width:100%;">
</div>

</div>

Sistema eragile bat seguru izateko beste atal garrantzitsu bat erabiltzaileei baimen egokiak ematea da. Adibidez, praktikaldiko ikasle bat badugu, bere erabiltzailea izango du, baina ez du baimenik izango aldaketa garrantzitsurik egiteko, hala nola web-orriaren edukia aldatzeko.

Horretarako, bilatu baimen hauek ezarri nahi dituzun unitatea edo karpeta. Gure kasuan, `inetpub` karpetaren baimenak kudeatuko ditugu, bertan baitaude web-orrien datu guztiak.

<div style="break-inside: avoid; page-break-inside: avoid;">

Karpeta kokatu ondoren, egin eskuineko klik eta ireki "Propiedades".

<div align="left">
<img src="img/image41.png" alt="Irudia: Karpeta kokatu ondoren, egin eskuineko klik eta ireki Propiedades" width="279" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Joan "Seguridad" atalera eta sakatu "Editar" baimenak kudeatzeko tresnara sartzeko.

<div align="left">
<img src="img/image57.png" alt="Irudia: Joan Seguridad atalera eta sakatu Editar baimenak kudeatzeko tresnara sartzeko" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Nahi duzun erabiltzailea aurkitzen ez baduzu, bere baimenak "Users" taldean lehenetsita daudelako da. Ikaslearen baimenak espezifikoki kudeatzeko, "Agregar" botoiarekin gehitu beharko dugu.

<div align="left">
<img src="img/image53.png" alt="Irudia: Nahi duzun erabiltzailea aurkitzen ez baduzu, bere baimenak Users taldean lehenetsita…" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Erabiltzailearen izena idaztearekin nahikoa da; "Comprobar nombres" erabilita, bere ibilbidea automatikoki idatziko du.

<div align="left">
<img src="img/image27.png" alt="Irudia: Erabiltzailearen izena idaztearekin nahikoa da; Comprobar nombres erabilita, bere…" width="337" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau eginda, zerrendan agertu beharko litzateke, eta beheko atalean bere baimenak. Aldatu zure beharren arabera.

<div align="left">
<img src="img/image14.png" alt="Irudia: Hau eginda, zerrendan agertu beharko litzateke, eta beheko atalean bere baimenak.…" width="277" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, ikasle gisa, ez duzu baimenik izango `inetpub` karpetan aldaketarik egiteko.

<div align="left">
<img src="img/image77.png" alt="Irudia: Orain, ikasle gisa, ez duzu baimenik izango inetpub karpetan aldaketarik egiteko" width="388" style="max-width:100%;">
</div>

</div>

## Kuotak ezartzea

Sistema batean erabiltzaile bat baino gehiago daudenean, garrantzitsua da bakoitzari bere biltegiratze-zatia ematea, batak besteari ez kentzeko. Horretarako dira disko-kuotak.

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau ezartzeko, fitxategi-arakatzailean ("Explorador de archivos") joan zure diskora.

<div align="left">
<img src="img/image60.png" alt="Irudia: Hau ezartzeko, fitxategi-arakatzailean (Explorador de archivos) joan zure diskora" width="306" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Ireki "Propiedades" > "Cuota…".

<div align="left">
<img src="img/image34.png" alt="Irudia: Ireki Propiedades > Cuota…" width="277" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gaitu kuota-administrazioa eta kudeatu mugak zure gustura.

<div align="left">
<img src="img/image24.png" alt="Irudia: Gaitu kuota-administrazioa eta kudeatu mugak zure gustura" width="260" style="max-width:100%;">
</div>

</div>

## RAID

Zerbitzari batek bere datuak hutsegiteetatik ere babestu behar ditu; horretarako dago RAID teknologia. Gure kasuan, RAID-5 eta ispilatua (RAID-1) erabiliko ditugu. RAID-5ekin, disko bat galtzen denean, beste biren datuekin hirugarrenarena birkalkulatu eta berreskuratu daiteke, daturik galdu gabe.

Ispilatuan, bi disko erabiltzen dira, biak datu berberekin. Batek huts egiten badu, besteak berreskuratu ahal izango ditu datuak.

Hasteko, diskak gehitu behar ditugu gure makinara. VirtualBox-en egiteko, honela egin behar da.

<div style="break-inside: avoid; page-break-inside: avoid;">

"Medio" dagoen lekura joan eta aukeratu disko berria sortzea.

<div align="left">
<img src="img/image84.png" alt="Irudia: Medio dagoen lekura joan eta aukeratu disko berria sortzea" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, honen izena eta edukiera aukeratzeko aukera emango dizu. Horrelako 3 sortu gutxienez.

<div align="left">
<img src="img/image37.png" alt="Irudia: Orain, honen izena eta edukiera aukeratzeko aukera emango dizu. Horrelako 3 sortu…" width="315" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain makinan sartuko ditugu.

<div align="left">
<img src="img/image36.png" alt="Irudia: Orain makinan sartuko ditugu" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Sakatu "Almacenamiento" > "Añadir disco".

<div align="left">
<img src="img/image97.png" alt="Irudia: Sakatu Almacenamiento > Añadir disco" width="600" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gehitu lehen sortutako diskak.

<div align="left">
<img src="img/image42.png" alt="Irudia: Gehitu lehen sortutako diskak" width="355" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

**GOGORATU!!** Diskek funtzionatzeko, kontrolagailu birtualean SATA gehiago jarri behar dituzu.

<div align="left">
<img src="img/image96.png" alt="Irudia: GOGORATU!! Diskek funtzionatzeko, kontrolagailu birtualean SATA gehiago jarri behar dituzu" width="600" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau eginda, makina berriro abiarazi dezakegu. Sakatu `Win+X` eta ireki "Administración de discos".

<div align="left">
<img src="img/image38.png" alt="Irudia: Hau eginda, makina berriro abiarazi dezakegu. Sakatu Win+X eta ireki Administración de…" width="305" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Aurkitu orain gehitutako diskak eta aukeratu nahi duzun formatua. Orain RAID-1 azalduko dut.

<div align="left">
<img src="img/image59.png" alt="Irudia: Aurkitu orain gehitutako diskak eta aukeratu nahi duzun formatua. Orain RAID-1…" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Behin "Nuevo volumen" sakatuta, zein disko erabili galdetuko dizu.

<div align="left">
<img src="img/image40.png" alt="Irudia: Behin Nuevo volumen sakatuta, zein disko erabili galdetuko dizu" width="376" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gero, letra bat esleitzeko eskatuko dizu.

<div align="left">
<img src="img/image54.png" alt="Irudia: Gero, letra bat esleitzeko eskatuko dizu" width="345" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gero, zein sistema mota erabili eta izen bat galdetuko dizu.

<div align="left">
<img src="img/image76.png" alt="Irudia: Gero, zein sistema mota erabili eta izen bat galdetuko dizu" width="342" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau guztia jarraian eginda, bukatuta egon beharko litzateke. Menuak itxura hau izan beharko luke:

<div align="left">
<img src="img/image64.png" alt="Irudia: Hau guztia jarraian eginda, bukatuta egon beharko litzateke. Menuak itxura hau izan…" width="481" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen.

<div align="left">
<img src="img/image73.png" alt="Irudia: RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen" height="69" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image86.png" alt="Irudia: RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen" height="69" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image62.png" alt="Irudia: RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen" height="69" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image87.png" alt="Irudia: RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen" height="69" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image23.png" alt="Irudia: RAID-5erako prozesua nahiko berdina da; funtzioa baino ez da aldatzen" height="69" style="max-width:100%;">
</div>

</div>

## Babeskopia

Zerbitzaria guztiz babestuta dagoela bermatzeko, babeskopia-zerbitzu bat izatea garrantzitsua da. Horretarako, zerbitzu hau instalatzearekin hasiko gara.

<div style="break-inside: avoid; page-break-inside: avoid;">

Zerbitzari-administratzailean, klikatu "Administrar" > "Agregar roles y características".

<div align="left">
<img src="img/image20.png" alt="Irudia: Zerbitzari-administratzailean, klikatu Administrar > Agregar roles y características" width="574" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Joan "Características" atalera arte eta aukeratu "Windows Server Backup". Jarraitu eta instalatu.

<div align="left">
<img src="img/image58.png" alt="Irudia: Joan Características atalera arte eta aukeratu Windows Server Backup. Jarraitu eta…" width="437" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Instalatu ondoren, ireki segurtasun-kopien tresna.

<div align="left">
<img src="img/image16.png" alt="Irudia: Instalatu ondoren, ireki segurtasun-kopien tresna" width="401" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Klikatu "Copia de seguridad local" eta, kopiak aldizka egin nahi badituzu, "Programar copia de seguridad".

<div align="left">
<img src="img/image43.png" alt="Irudia: Klikatu Copia de seguridad local eta, kopiak aldizka egin nahi badituzu, Programar…" width="404" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Jarraitu eta aukeratu nahiago duzun aukera.

<div align="left">
<img src="img/image9.png" alt="Irudia: Jarraitu eta aukeratu nahiago duzun aukera" width="436" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, aldizkako kopiaren ordutegiak ezarri beharko dituzu.

<div align="left">
<img src="img/image72.png" alt="Irudia: Orain, aldizkako kopiaren ordutegiak ezarri beharko dituzu" width="381" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, kopia non gorde galdetuko dizu. Aukerarik onena sistematik aparte dagoen disko batean gordetzea da.

<div align="left">
<img src="img/image39.png" alt="Irudia: Orain, kopia non gorde galdetuko dizu. Aukerarik onena sistematik aparte dagoen disko…" width="334" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Nire kasuan, beste disko batean gordetzea erabaki dut. Gogoratu kasu honetan diskoak sistema dagoen diskoaren tamaina bera edo handiagoa izan behar duela.

<div align="left">
<img src="img/image35.png" alt="Irudia: Nire kasuan, beste disko batean gordetzea erabaki dut. Gogoratu kasu honetan diskoak…" width="514" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Azkenik, kopiaren xehetasunak erakutsiko dizkizu, dena ondo dagoen ikusteko.

<div align="left">
<img src="img/image10.png" alt="Irudia: Azkenik, kopiaren xehetasunak erakutsiko dizkizu, dena ondo dagoen ikusteko" width="487" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Eta horrekin amaituta egongo da.

<div align="left">
<img src="img/image81.png" alt="Irudia: Eta horrekin amaituta egongo da" width="252" style="max-width:100%;">
</div>

</div>

# 4. Zerbitzuak

## Instalazioak

Zerbitzari baten funtzio nagusia zerbitzuak eskaintzea da.

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehen urratsa zerbitzuak instalatzea da. Ireki sisteman lehenetsita datorren zerbitzari-administratzailea eta jarraitu honela: "Administrar" > "Agregar roles y características".

<div align="left">
<img src="img/image20.png" alt="Irudia: Lehen urratsa zerbitzuak instalatzea da. Ireki sisteman lehenetsita datorren…" width="574" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Jarraitu "Roles" atalera arte eta aukeratu behar dituzunak. DHCP, DNS eta IIS dira ohikoenak. "Características" atalean, "Windows Server Backup" ere ondo dator gerorako.

<div align="left">
<img src="img/image28.png" alt="Irudia: Jarraitu Roles atalera arte eta aukeratu behar dituzunak. DHCP, DNS eta IIS dira…" width="399" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau egin ondoren, jarraitu botoia sakatuz honaino iritsi arte. Dena ondo egon beharko litzateke.

<div align="left">
<img src="img/image82.png" alt="Irudia: Hau egin ondoren, jarraitu botoia sakatuz honaino iritsi arte. Dena ondo egon beharko…" width="444" style="max-width:100%;">
</div>

</div>

## DNS

Dena instalatuta dugunean, DNS-rekin hasiko gara. Zerbitzu honek izen bat IP batekin lotzen du, eta alderantziz. Horrela, erabiltzaileek errazago aurkituko dute domeinu bat edo sare bat.

<div style="break-inside: avoid; page-break-inside: avoid;">

Horretarako, zerbitzari-administratzailean, "Herramientas" > "DNS".

<div align="left">
<img src="img/image51.png" alt="Irudia: Horretarako, zerbitzari-administratzailean, Herramientas > DNS" width="419" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Barruan sartuta, klikatu zerbitzarian eta DNS konfiguratzen hasi gaitezke.

<div align="left">
<img src="img/image69.png" alt="Irudia: Barruan sartuta, klikatu zerbitzarian eta DNS konfiguratzen hasi gaitezke" width="321" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Zein funtzio konfiguratu nahi duzun galdetuko dizu. Bai bilaketa zuzena bai alderantzizkoa gomendatuko nuke, biak beharrezkoak izango direlako.

<div align="left">
<img src="img/image32.png" alt="Irudia: Zein funtzio konfiguratu nahi duzun galdetuko dizu. Bai bilaketa zuzena bai…" width="268" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Sortu zona nagusia.

<div align="left">
<img src="img/image8.png" alt="Irudia: Sortu zona nagusia" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Zure zonari izena emateko eskatuko dizu.

<div align="left">
<img src="img/image1.png" alt="Irudia: Zure zonari izena emateko eskatuko dizu" width="266" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hurrengo urratsak berdinak dira, edo automatikoki jarraitu ditzakezu.

<div align="left">
<img src="img/image70.png" alt="Irudia: Hurrengo urratsak berdinak dira, edo automatikoki jarraitu ditzakezu" height="126" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image78.png" alt="Irudia: Hurrengo urratsak berdinak dira, edo automatikoki jarraitu ditzakezu" height="126" style="max-width:100%;">&nbsp;&nbsp;<img src="img/image2.png" alt="Irudia: Hurrengo urratsak berdinak dira, edo automatikoki jarraitu ditzakezu" height="126" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Alderantzizko zonarako, zure sarearen IDa beharko duzu (IP-aren hasiera).

<div align="left">
<img src="img/image17.png" alt="Irudia: Alderantzizko zonarako, zure sarearen IDa beharko duzu (IP-aren hasiera)" width="447" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Jarraitu honela:

<div align="left">
<img src="img/image85.png" alt="Irudia: Jarraitu honela" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau ez da baliagarria Interneterik gabeko lan batean.

<div align="left">
<img src="img/image52.png" alt="Irudia: Hau ez da baliagarria Interneterik gabeko lan batean" width="260" style="max-width:100%;">
</div>

</div>

Hau egin ondoren, errore bat agertu daiteke. Lasai, konfigurazioa eskuz jarrai dezakegu.

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehenik, host bat sortu behar dugu. Ireki "Zonas de búsqueda" eta "Host nuevo".

<div align="left">
<img src="img/image29.png" alt="Irudia: Lehenik, host bat sortu behar dugu. Ireki Zonas de búsqueda eta Host nuevo" width="549" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Eman nahi duzun izena eta lotu zure zerbitzariaren IP-ra.

<div align="left">
<img src="img/image11.png" alt="Irudia: Eman nahi duzun izena eta lotu zure zerbitzariaren IP-ra" width="301" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Orain, hauek konfiguratuko ditugu:

<div align="left">
<img src="img/image71.png" alt="Irudia: Orain, hauek konfiguratuko ditugu" width="600" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehenengo orrian, hauek gure host-arekin lotu behar ditugu.

<div align="left">
<img src="img/image68.png" alt="Irudia: Lehenengo orrian, hauek gure host-arekin lotu behar ditugu" width="298" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Gero, "Servidores de nombres" atalean, zure zerbitzariaren IP-a jarri beharko duzu. Zure zerbitzariaren izena agertzen bada, "Resolver" sakatzearekin nahikoa da.

<div align="left">
<img src="img/image47.png" alt="Irudia: Gero, Servidores de nombres atalean, zure zerbitzariaren IP-a jarri beharko duzu. Zure…" width="329" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Bi urrats hauek alderantzizko zonarekin ere egin beharko dituzu.

<div align="left">
<img src="img/image22.png" alt="Irudia: Bi urrats hauek alderantzizko zonarekin ere egin beharko dituzu" width="402" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau guztia eginda, ireki cmd eta erabili komando hau zerbitzariaren IP-arekin. Dena ondo egin baduzu, horrelako zerbait agertu beharko litzateke.

<div align="left">
<img src="img/image48.png" alt="Irudia: Hau guztia eginda, ireki cmd eta erabili komando hau zerbitzariaren IP-arekin. Dena…" width="333" style="max-width:100%;">
</div>

</div>

## IIS

Bezeroek gure zerbitzuetara iristea nahi badugu, web bidezko sarbidea izatea da onena. Horretarako dago IIS zerbitzua.

<div style="break-inside: avoid; page-break-inside: avoid;">

Hau konfiguratzen hasteko, zerbitzari-administratzailean bilatu interneteko zerbitzuen administratzaile-tresna (IIS).

<div align="left">
<img src="img/image30.png" alt="Irudia: Hau konfiguratzen hasteko, zerbitzari-administratzailean bilatu interneteko zerbitzuen…" width="444" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Bilatu "Sitios" atala eta ireki zerbitzariaren adarra.

<div align="left">
<img src="img/image45.png" alt="Irudia: Bilatu Sitios atala eta ireki zerbitzariaren adarra" width="293" style="max-width:100%;">
</div>

</div>

Zure web-orria zerbitzu honetan ezartzeko, zerbitzuaren karpetara joan beharko zara eta bertan itsatsi zure kode eta eduki guztia.

<div style="break-inside: avoid; page-break-inside: avoid;">

Horretarako, "Default Web Site" gainean eskuineko klik eginda, aukeratu "Explorar".

<div align="left">
<img src="img/image31.png" alt="Irudia: Horretarako, Default Web Site gainean eskuineko klik eginda, aukeratu Explorar" width="338" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Honek `wwwroot` karpetara eramango zaitu. Bertan, zerbitzuak aurrez instalatutako web-orri txiki bat dago; hori ezabatu eta horren ordez zurea jarri dezakezu.

<div align="left">
<img src="img/image50.png" alt="Irudia: Honek wwwroot karpetara eramango zaitu. Bertan, zerbitzuak aurrez instalatutako…" width="369" style="max-width:100%;">
</div>

</div>

Hurrengoa, gure orria DNS-ra lotzea da.

<div style="break-inside: avoid; page-break-inside: avoid;">

Gure web-orrian klik eginda, eskuineko barran sakatu "Enlaces".

<div align="left">
<img src="img/image80.png" alt="Irudia: Gure web-orrian klik eginda, eskuineko barran sakatu Enlaces" width="468" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Eta gehitu zure zerbitzariaren IP-a. Garrantzitsua da "Host" atalean zure DNS zerbitzuko host-aren helbidea jartzea.

<div align="left">
<img src="img/image95.png" alt="Irudia: Eta gehitu zure zerbitzariaren IP-a. Garrantzitsua da Host atalean zure DNS zerbitzuko…" width="513" style="max-width:100%;">
</div>

<div align="left">
<img src="img/image93.png" alt="Irudia: Eta gehitu zure zerbitzariaren IP-a. Garrantzitsua da Host atalean zure DNS zerbitzuko…" width="600" style="max-width:100%;">
</div>

</div>

Hau eginda, egiaztapen-protokoloa jarraitu.

<div style="break-inside: avoid; page-break-inside: avoid;">

Lehenik, zerbitzariaren IP-a nabigatzailean jarrita:

<div align="left">
<img src="img/image66.png" alt="Irudia: Lehenik, zerbitzariaren IP-a nabigatzailean jarrita" width="268" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

DNS helbidea erabiliz:

<div align="left">
<img src="img/image44.png" alt="Irudia: DNS helbidea erabiliz" width="307" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Beste gailu batetik IP bidez:

<div align="left">
<img src="img/image88.jpg" alt="Irudia: Beste gailu batetik IP bidez" width="260" style="max-width:100%;">
</div>

</div>

<div style="break-inside: avoid; page-break-inside: avoid;">

Eta beste gailu batetik DNS bidez:

<div align="left">
<img src="img/image83.jpg" alt="Irudia: Eta beste gailu batetik DNS bidez" width="260" style="max-width:100%;">
</div>

</div>
