---
name: gestione-incidenti
description: "Cosa fare quando qualcosa va storto in IT. Guasti (server, posta, internet, gestionale fermi) e incidenti di sicurezza (account compromesso, phishing cliccato, ransomware, perdita di un portatile): contenere, capire, comunicare, ripristinare, notificare quando la legge lo chiede, e scrivere il resoconto. Da usare appena qualcuno segnala un problema grave, un'email sospetta cliccata, file cifrati, un accesso strano o un sistema fermo."
license: Proprietary
metadata:
  hermes:
    tags: [IT, Incidenti, Ransomware, Phishing, Continuità]
    related_skills: [sicurezza-e-conformita, backup-e-storage, microsoft-365-e-windows, rete-e-firewall]
---

# Gestione degli incidenti

Prima contieni, poi capisci, poi racconti. Con calma, per iscritto, un passo
alla volta. Apri subito un file `it/incidenti/<data>-<titolo>.md` e annota ogni
fatto con l'ora: servirà per le notifiche e per il resoconto.

## I primi minuti

1. **Quanto è grave?** Chi è fermo, quali dati sono a rischio, se si sta
   allargando.
2. **Avvisa** la persona responsabile e, se c'è, il fornitore IT esterno, con
   quello che sai e quello che non sai ancora.
3. **Contieni**, con il sì della persona per ogni azione che interrompe il
   lavoro:

| Caso | Contenimento |
| --- | --- |
| Account compromesso | blocca l'accesso e revoca le sessioni, cambia la password, controlla e rimuovi regole di inoltro e app autorizzate, verifica MFA e accessi recenti |
| Link di phishing cliccato o credenziali inserite | come sopra per quell'account; con il sì della persona responsabile, avvisa i colleghi di non aprire la stessa email; segnala il messaggio |
| Ransomware o file cifrati | scollega dalla rete (cavo e Wi-Fi) il PC o il server, **non spegnerlo**, non pagare, non cancellare niente; proteggi subito i backup (scollega o verifica l'immutabilità) |
| Portatile o telefono perso | blocco e cancellazione da remoto se è gestito, cambio delle password usate sul dispositivo; se non era cifrato, valuta con il titolare la violazione di dati personali |
| Sistema fermo senza attacco | verifica alimentazione, rete, spazio, servizi; ultimo cambiamento fatto; contatta l'assistenza del vendor con versione e messaggi d'errore |

## Capire

Raccogli prima di cambiare: log del firewall, dell'antivirus o EDR, accessi di
Microsoft 365, eventi di Windows e di vCenter, email originale con le
intestazioni. Rispondi a: da quando, da dove è entrato, cosa ha toccato, è
ancora dentro?

## Notifiche previste dalla legge

- Se ci sono dati personali coinvolti, il titolare valuta con il DPO o il
  consulente privacy la notifica al Garante entro 72 ore dalla scoperta.
- Se l'azienda è un soggetto NIS2 e l'incidente è significativo: preallerta a
  CSIRT Italia entro 24 ore, notifica entro 72 ore, relazione entro un mese.
- Per reati informatici (estorsione, frode), denuncia alla Polizia Postale.
- Avvisa l'assicurazione cyber, se c'è, secondo la polizza: spesso va avvisata
  subito e indica i fornitori da usare.

Tu prepari i fatti e le bozze; chi notifica e firma è l'azienda.

## Ripristinare

Si ripristina solo dopo aver tolto la causa: password cambiate, vulnerabilità
chiusa, sistemi infetti ripuliti o reinstallati. Ripristina dai backup
verificati, partendo dai sistemi essenziali concordati, e controlla che i dati
ripristinati non siano già compromessi.

## Il resoconto

Entro pochi giorni, una pagina: cosa è successo, impatto, tempi, cosa ha
funzionato, cosa no, e tre azioni per evitare che si ripeta, con chi e quando.
Aggiorna inventario, documenti di sicurezza e attività pianificate.
