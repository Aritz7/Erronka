---
layout: page
title: Sareak
---
# Sareak - Sareen Planifikazioa eta Kodifikazioa

Atal honetan, Sareak moduluan landutako plangintza, kableak lortzeko prozesua eta informazioaren kodifikazio-lanak azaltzen dira.

---

## 1. Materiala, Kableak eta Patch Panela
Prozesuari hasiera emateko, beharrezko materialak eta kableak lortu eta kokatu ditugu (*lortu/kokatu*), azpiegitura fisikoaren oinarriak ezartzeko.

![KABLEAREN IRUDIA](img/cables.jpg)

Horren ondoren, kableatze-lanak osatu ditugu:
- **Patch Panel-ean kableatzea:** Kableak patch panel-ean Behar bezala konektatu eta antolatu ditugu.

![KABLEA PATCH-PANELEAN](img/cablespatch.jpg)

- **Kable emea (RJ45 Keystone):** Era berean, kableatze hori kable/konektore eme bati lotu zaio, sare-puntuaren lotura fisikoa egoki uzteko.

![KABLE HEMBRA](img/cablehembra.jpg)

---

## 2. Pasahitza eta ASCII Biherketa
Proiekturako pasahitz bat aukeratu dugu: **`admin123`**.

Ondoren, pasahitz honen karaktere bakoitza bere balio ASCIIra (binarioan) bihurtu dugu:

* **a** --> `01100001`
* **d** --> `01100100`
* **m** --> `01101101`
* **i** --> `01101001`
* **n** --> `01101110`
* **1** --> `00110001`
* **2** --> `00110010`
* **3** --> `00110011`

---

## 3. CRC Kalkulua eta Gehitzea
Datuen osotasuna eta erroreen detekzioa bermatzeko, aukeratutako pasahitzari CRC-6 algoritmoz lortutako kodea kalkulatu eta gehitu diogu:

* **Gehitutako CRC kodea:** `001000`

Matea osoa (ASCII pasahitza + CRC) transmisiorako prest utzi dugu.

![ASCII PASAHITZA](img/asciicontra.jpg)

---

## 4. Modulazio Teknologiak
Lortutako kate osoa (ASCII testua + CRC) modulazio digital **PSK(2) ASK(2) FSK(2)**-ra pasatu dugu:

![PSKASKFSK](img/PSKASKFSK.jpg)

---

## 5. Linea-Kodifikazioak (Manchester)
Azkenik, seinalea hobeto garraiatzeko eta sinkronizazioa bermatzeko, informazio guztia bi linea-kodifikazio hauetara igaro dugu:

* **Manchester Normala**
* **Manchester Diferentziala**

![MANCHESTER](img/manchester.jpg)