# 🍕 Pizzeria Delivery Tracker (Sabba & Betto Edition)

Questo è un Blueprint avanzato per Home Assistant che gestisce le consegne delle pizze in modo automatico.

## ✨ Funzionalità
* 🛑 **Rilevamento Consegna:** Capisce quando ti fermi dal cliente (> 1 min).
* 🗣️ **Annunci Vocali:** Alexa ti dice "Consegna effettuata in Via Roma 10".
* ⛽ **Rilevamento Benzina:** Riconosce se ti fermi al distributore e ti avvisa.
* 📡 **GPS Intelligente:** Attiva l'alta precisione su Android solo durante l'orario di lavoro.
* 🏠 **Rientro in Sede:** Avviso specifico quando torni in pizzeria.

## 🚀 Installazione Veloce
Clicca il pulsante qui sotto per installare questo Blueprint direttamente nel tuo Home Assistant:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FGiorgio866%2FConsegne-pizze-a-domicilio%2Fblob%2Fmain%2FPizzeria.yaml)

## ⚙️ Requisiti
* Un sensore di posizione (es. telefono Android con app Companion).
* Un Helper (Input Boolean) per la memoria (crealo in Impostazioni -> Dispositivi -> Aiutanti).
* Aver configurato le zone (Pizzeria e Benzinai).
