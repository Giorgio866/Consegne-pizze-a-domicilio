# 🍕 Pizzeria Delivery Tracker (Sabba & Betto Edition)

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FGiorgio866%2FConsegne-pizze-a-domicilio%2Fblob%2Fmain%2FPizzeria.yaml)

> **Il sistema definitivo per gestire le consegne con Home Assistant.**

Questo Blueprint trasforma Home Assistant in un gestore avanzato per la flotta consegne. Rileva automaticamente quando il fattorino si ferma da un cliente, invia notifiche Telegram dettagliate e fa parlare Alexa in pizzeria.

---

## ✨ Funzionalità Principali

* 🛑 **Rilevamento Intelligente:** Capisce quando l'auto è in consegna (sosta > 1 minuto) e ignora traffico e semafori.
* 📍 **Indirizzo Preciso:** Notifica su Telegram con la via esatta della consegna (Geocoded Location).
* 🔋 **Stato Veicolo:** Include livello batteria telefono e consumo dati (GB) nel report.
* 🗣️ **Annunci Vocali Alexa:**
    * *Dal cliente:* "Consegna effettuata in Via Roma 10".
    * *In pizzeria:* "Attenzione: La Panda è rientrata in sede".
* ⛽ **Filtro Benzinai:** Riconosce se l'auto è ferma per fare rifornimento e **non** invia la notifica di "Consegna effettuata".
* 🤖 **Gestione GPS (Android):** Attiva automaticamente l'alta precisione durante l'orario di lavoro e la spegne la notte.

---

## ⚙️ Prerequisiti (Da fare prima!)

Prima di installare il Blueprint, assicurati di avere queste 3 cose pronte:

### 1. App Home Assistant (Android/iOS)
Il telefono nell'auto deve avere l'app installata con i sensori di posizione attivi.
* **Android:** Impostazioni App -> Gestione Sensori -> *Abilita "Sensori di posizione" e "Posizione Geocodificata"*.
* **iOS:** Privacy e Sicurezza -> Localizzazione -> Home Assistant -> *Imposta su "SEMPRE"*.

### 2. Le Zone
Configura le zone nella mappa di Home Assistant:
* **Zona Pizzeria:** La sede centrale.
* **Zone Benzinai:** (Opzionale) I distributori dove fate rifornimento abitualmente.

### 3. L'Aiutante (Helper) - FONDAMENTALE ⚠️
Il sistema ha bisogno di una "memoria" per sapere se l'auto è ferma. Devi crearne uno per ogni auto.
1.  Vai su **Impostazioni** -> **Dispositivi e Servizi** -> **Aiutanti**.
2.  Clicca **+ CREA AIUTANTE**.
3.  Scegli **Interruttore** (Input Boolean).
4.  Nome: `Panda in Consegna` (o nome della tua auto).
5.  Icona: `mdi:pizza`.

---

## 🚀 Installazione

1.  Clicca sul pulsante **"Import Blueprint"** blu in alto in questa pagina.
2.  Si aprirà il tuo Home Assistant: clicca su **Anteprima** e poi **Importa**.
3.  Ora vai su **Impostazioni** -> **Automazioni e Scene** -> **+ CREA AUTOMAZIONE**.
4.  Seleziona dalla lista: **Pizzeria Delivery Tracker (Sabba & Betto Edition)**.

---

## 📝 Configurazione Passo-Passo

Compila i campi richiesti con le entità della tua auto:

| Campo | Cosa inserire | Esempio |
| :--- | :--- | :--- |
| **Veicolo (Tracker)** | Il device_tracker del telefono | `device_tracker.panda` |
| **Sensore Batteria** | Il livello batteria | `sensor.panda_battery_level` |
| **Sensore Indirizzo** | Il sensore Geocoded (Indirizzo) | `sensor.panda_geocoded_location` |
| **Sensore Dati GB** | (Opzionale) Consumo dati | `sensor.panda_total_tx_gb` |
| **Zona Pizzeria** | La zona della tua sede | `zone.pizzeria` |
| **Zone Distributori** | Seleziona le zone benzina | `zone.distributore_eni` |
| **Dispositivo Telegram** | Il servizio di notifica | `notify.telegram_sabba` |
| **Dispositivi Alexa** | Dove vuoi sentire gli annunci | `notify.echo_dot_cucina` |
| **Helper Memoria** | **L'aiutante creato al punto 3** | `input_boolean.panda_in_consegna` |
| **Servizio Notifica App** | Per comandi GPS (solo Android) | `notify.mobile_app_panda` |

---

## ❓ Domande Frequenti

**Posso gestire più auto?**
Sì! Basta creare una **nuova automazione** per ogni auto.
Esempio:
1. Crea automazione "Gestione Panda" -> Seleziona Blueprint -> Imposta sensori Panda.
2. Crea automazione "Gestione Punto" -> Seleziona Blueprint -> Imposta sensori Punto.
*(Ricorda di creare un Helper memoria diverso per ogni auto!)*

**Perché non mi arriva la notifica quando mi fermo?**
Il sistema ha un filtro di sicurezza:
1. Devi essere lontano almeno **100 metri** dalla pizzeria.
2. Devi stare fermo per almeno **60 secondi**.
3. Il GPS deve inviare la posizione (verifica che l'alta precisione sia attiva).

---

Made with ❤️ by **Sabba & Betto**
