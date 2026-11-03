---
name: sicurezza-e-conformita
description: Sicurezza informatica e regole per una PMI italiana. NIS2 (D.Lgs. 138/2024, piattaforma ACN, misure di base, notifiche a CSIRT Italia), GDPR per la parte IT (violazioni dei dati, registro, misure tecniche), politiche scritte, formazione contro il phishing, antivirus ed EDR, accessi e privilegi, fornitori. Da usare per sicurezza, NIS2, GDPR, audit, assicurazione cyber, phishing, policy o richieste di clienti sui requisiti di sicurezza.
license: Proprietary
metadata:
  hermes:
    tags: [IT, Sicurezza, NIS2, GDPR, ACN, Phishing, Policy]
    related_skills: [gestione-incidenti, microsoft-365-e-windows, rete-e-firewall, backup-e-storage]
---

# Sicurezza e conformità

Questo non sostituisce il consulente legale, il DPO o l'auditor: tu prepari i
dati, le misure tecniche e i documenti, e dici quando serve un esperto.

## NIS2 in Italia

- Il D.Lgs. 138/2024 recepisce la NIS2. Riguarda soprattutto le medie e grandi
  imprese dei settori elencati, ma anche alcune piccole e i fornitori di
  soggetti NIS2, che spesso ricevono requisiti per contratto.
- Chi rientra si registra ogni anno sulla piattaforma dell'ACN (finestra dal 1°
  gennaio al 28 febbraio) e aggiorna i dati e il punto di contatto nella
  finestra primaverile; deve adottare le misure di sicurezza di base indicate
  dall'ACN (per i soggetti già in elenco la scadenza era il 31 ottobre 2026) e
  notificare gli incidenti significativi a CSIRT Italia: preallerta entro 24
  ore, notifica entro 72 ore, relazione finale entro un mese.
- Verifica sempre date e requisiti aggiornati su acn.gov.it: il calendario
  cambia con le determinazioni dell'ACN.
- Al primo incontro chiedi se l'azienda è registrata, chi è il punto di
  contatto e chi segue la conformità; se nessuno lo sa, proponi di verificarlo
  con il consulente.

## GDPR, per la parte IT

- Una violazione di dati personali (perdita, furto, accesso non autorizzato,
  ransomware) va valutata subito; se c'è rischio per le persone va notificata
  al Garante entro 72 ore dalla scoperta, e nei casi gravi comunicata agli
  interessati. Lo decide il titolare con il DPO o il consulente privacy: tu
  raccogli i fatti (cosa, quando, quanti dati e di chi, misure prese) e lo
  avvisi subito.
- Misure tecniche da poter documentare: accessi nominativi e minimi, MFA,
  cifratura di portatili e telefoni, backup verificati, aggiornamenti, log,
  registro delle violazioni.

## Regole italiane sugli strumenti di lavoro

- **Amministratori di sistema** (provvedimento del Garante del 27 novembre
  2008): chi amministra i sistemi va designato per nome, la lista va tenuta
  aggiornata, gli accessi degli amministratori vanno registrati e conservati
  almeno sei mesi, e il loro operato va verificato almeno una volta l'anno.
  Anche un agente con accessi amministrativi rientra in questa lista: dillo
  alla persona responsabile.
- **Controlli a distanza** (art. 4 dello Statuto dei lavoratori): strumenti
  che permettono di controllare l'attività dei dipendenti richiedono un
  accordo sindacale o l'autorizzazione dell'Ispettorato, e un'informativa
  chiara. Leggere log di navigazione, posta o accessi di una persona per
  controllarla non si fa senza il parere del consulente del lavoro o del DPO;
  per la sicurezza dei sistemi si guardano dati aggregati o legati a un
  incidente.
- **Metadati della posta**: il Garante ha indicato tempi brevi di
  conservazione dei log della posta dei dipendenti; verifica le indicazioni
  aggiornate prima di allungarli.

## Le basi che fanno la differenza

In ordine di impatto per una PMI:

1. MFA su posta, VPN e accessi remoti, e per tutti gli amministratori.
2. Backup 3-2-1-1-0 con test di ripristino (vedi `backup-e-storage`).
3. Aggiornamenti di sistemi, firewall, VPN e applicazioni esposte.
4. EDR o antivirus gestito su tutti i PC e server, con gli avvisi letti da
   qualcuno.
5. Nessun servizio di gestione esposto su internet (RDP, interfacce di
   firewall, NAS).
6. Account: pochi amministratori, nessun account condiviso, uscite gestite il
   giorno stesso.
7. Formazione contro il phishing, breve e periodica, e un modo semplice per
   segnalare un'email sospetta.
8. Inventario aggiornato e fornitori con accessi tracciati.

## Documenti che tieni

In `it/sicurezza/`: politica sulle password e MFA, uso dei dispositivi e della
posta, backup e ripristino, gestione degli accessi, gestione degli incidenti,
elenco dei fornitori con accesso ai sistemi. Brevi, veri, approvati dalla
persona responsabile. Quando un cliente o un'assicurazione manda un
questionario di sicurezza, rispondi dai documenti e dall'inventario, mai con
dichiarazioni non vere.
