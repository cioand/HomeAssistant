Configurazione
**Materiale necessario**
- Sensore Reed (normalmente aperto o chiuso) in questo caso un contatore dell'acqua Caleffi 700053 con sensore REED
- Shelly Addon
- Shelly Plus 1 / Plus 1PM (necessario per alimentare l'Addon)

**Collegare lo Shelly Addon al Shelly Plus 1/1PM**

Il filo GND dell'Addon va al GND del Shelly.
Il filo 3.3V dell'Addon va al 3.3V del Shelly.
I fili ADC/IN1/IN2 sono gli ingressi digitali utilizzabili.
Collegare il Sensore Reed all'Addon
- Un terminale del sensore Reed va su GND dell'Addon (di solito il bianco)
- L'altro terminale va su digital-in (di solito il marrone)

**Configurazione software**:
Apri l’app Shelly e accedi al tuo dispositivo.
Vai nella sezione Addon e configura il pin DIGITAL IN come ingresso per un interruttore magnetico (Reed switch).
Scegli la modalità di funzionamento:
Normalmente aperto (NO): il circuito si chiude quando il magnete è vicino.
Normalmente chiuso (NC): il circuito si apre quando il magnete è vicino.
![Uploading image.png…]()

**Aggiungere il dispositivo Shelly a Home Assistant**
Se non lo hai già fatto:

Assicurati che il tuo Shelly Addon sia visibile in Home Assistant.
Installa l'integrazione Shelly in Impostazioni → Dispositivi & Servizi.
Se il dispositivo non viene rilevato automaticamente, aggiungilo manualmente con il suo IP.

**Creare un Sensore Contatore d’Impulsi**
Un contatore dell’acqua con contatto Reed genera 1 impulso per ogni litro (o frazione di litro) consumato (vedi il manuale per verificare il funzionamento del tuo). Nel nostro caso 1P=10Lt. Dobbiamo trasformare questi impulsi in un contatore cumulativo.
Modifica il file configuration.yaml per creare e adattare il sensore
