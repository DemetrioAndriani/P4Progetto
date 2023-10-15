# P4Progetto

## Descrizione

Questo README fornisce una panoramica del progetto, l'implementazione di una soluzione che combina due componenti in linguaggio P4: "Asymmetric Flow" e "My Tunnel". L'obiettivo principale del progetto è quello di consentire il monitoraggio dell'asimmetria tra flussi nel traffico IPv4 regolare senza header modificato. Inoltre, il progetto offre la possibilità di processare il traffico con un header personalizzato, noto come "My Tunnel," che contiene campi aggiuntivi come "IP Mal," "TIME," e "flag."

## Componenti principali

### Asymmetric Flow

Il programma Asymmetric Flow si comporta come segue:

1. Monitora l'asimmetria tra i flussi nel traffico IPv4 regolare senza header modificato.
2. Quando la soglia (threshold) della differenza viene raggiunta, registra i dati relativi all'ultimo pacchetto che ha causato la soglia. Questi dati includono:
   - Indirizzo IP sorgente
   - Indirizzo IP destinazione
   - Timestamp dell'ultimo pacchetto
3. Non elimina i pacchetti ma continua a instradarli correttamente.

### My Tunnel

Il programma My Tunnel è in grado di processare pacchetti con header personalizzato, che comportano le seguenti funzionalità:

1. Si comporta esattamente come My Tunnel per quanto riguarda l'indirizzamento, con la porta di destinazione specificata tramite "--dst-id."
2. Prima di accettare il pacchetto, verifica se nel registro "TRESHOLD" è stato scritto un valore che segnala il raggiungimento della soglia per un determinato flusso.
3. In caso positivo, scrive dei valori nei campi dell'header del pacchetto:
   - Scrive l'indirizzo IP di destinazione che ha raggiunto la soglia nel campo "IP Mal."
   - Imposta il valore 1 nel campo "flag."

## Topologia di Rete

Il progetto utilizza una topologia di rete composta da 3 switch e 3 host. La comunicazione tra gli host avviene attraverso i switch, e i pacchetti possono essere instradati tramite i programmi "Asymmetric Flow" e "My Tunnel" secondo le specifiche sopra descritte.

## Requisiti

- Ambiente di sviluppo P4 configurato correttamente.
- Topologia di rete conforme alle specifiche del progetto.
- Capacità di caricare e attivare i programmi P4 "Asymmetric Flow" e "My Tunnel" nei dispositivi di rete.


