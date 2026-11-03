---
name: backup-e-storage
description: Backup, ripristino e storage di una PMI. Regola 3-2-1-1-0, Veeam, Acronis, NAS Synology e QNAP, storage NetApp, HPE, Dell e Pure, copie immutabili e fuori sede, controllo quotidiano dei job, test di ripristino mensile, spazio e salute dei dischi, difesa dal ransomware. Da usare per backup, ripristini, NAS, storage, dischi, spazio esaurito o file persi.
license: Proprietary
metadata:
  hermes:
    tags: [IT, Backup, Storage, Veeam, Synology, QNAP, NetApp, Ransomware]
    related_skills: [fonti-ufficiali-vendor, vmware-vsphere, gestione-incidenti, sicurezza-e-conformita]
---

# Backup e storage

Un backup vale solo se si ripristina. Il tuo lavoro è sapere, ogni giorno, che
l'azienda potrebbe ripartire da un disastro, e quanto tempo e quanti dati
perderebbe.

## La regola

**3-2-1-1-0**: tre copie dei dati, su due supporti diversi, una fuori sede, una
immutabile o scollegata, zero errori nella verifica del ripristino. Per ogni
sistema importante scrivi in `it/inventario.md`: cosa si salva, con cosa, ogni
quanto, dove, per quanto tempo, quanto dati si possono perdere al massimo (RPO)
e in quanto tempo si deve ripartire (RTO), concordati con la persona.

## Strumenti

| Prodotto | Come leggi lo stato |
| --- | --- |
| Veeam Backup & Replication | server MCP ufficiale `veeam-ai/veeam-mcp-server` (`vi-mcp`, sola lettura) o API REST di VBR (porta 9419) con un utente dal ruolo limitato |
| Acronis | Acronis Cyber Platform API |
| Synology | DSM (Hyper Backup, Active Backup for Business, snapshot) dall'interfaccia o dalla DSM Web API; comunità `cmeans/mcp-synology` |
| QNAP | QTS (HBS 3, snapshot) dall'interfaccia |
| NetApp ONTAP | server MCP ufficiale ONTAP in sola lettura, Digital Advisor (Active IQ) MCP |
| HPE, Dell, Pure | vedi `fonti-ufficiali-vendor` |

## Ogni giorno (o al controllo pianificato)

- Esito dei job della notte: riusciti, con avvisi, falliti. Un job fallito
  due volte di fila è urgente.
- VM o cartelle importanti senza un backup riuscito nelle ultime 24 ore.
- Spazio sui repository e sui NAS (avviso sotto il 20% libero).
- Copia fuori sede e copia immutabile aggiornate.

## Ogni mese

- **Test di ripristino**: a rotazione, ripristina un file, una cartella, una
  VM intera in un ambiente isolato (o con la funzione di verifica del prodotto)
  e misura il tempo. Annota esito e tempo: è la prova che la persona può
  mostrare a un cliente, a un'assicurazione o a un controllo.
- Salute dei dischi (SMART, stato del RAID), firmware di NAS e storage e
  avvisi di sicurezza.
- Utenti con accesso ai backup: pochi, con MFA, separati dagli account di
  dominio quando possibile.

## Contro il ransomware

- Il server di backup non è nel dominio, o ha credenziali separate.
- Almeno una copia immutabile (repository immutabile Veeam, snapshot immutabili
  di Synology o QNAP, storage a oggetti con blocco) o scollegata.
- Interfacce di gestione di NAS e backup mai esposte su internet.
- Allarme se spariscono snapshot o backup, o se crescono all'improvviso i file
  modificati.

## Ripristinare

Prima di ripristinare chiedi cosa, di quando, dove. Ripristina in un percorso
diverso quando possibile, per non sovrascrivere. Dopo un attacco, non
ripristinare finché la causa non è stata trovata e contenuta (vedi
`gestione-incidenti`).
