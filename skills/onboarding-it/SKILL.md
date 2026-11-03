---
name: onboarding-it
description: Primo incontro con l'IT di un'azienda e inventario tenuto aggiornato. Scopre dove sono server, macchine virtuali, rete, firewall, storage, backup, account Microsoft, contratti, licenze e fornitori, e scrive la mappa nella cartella dell'agente. Da usare al primo incontro, quando manca un dato dell'inventario, quando arriva un dispositivo o un fornitore nuovo, o quando la persona chiede cosa c'è e dove.
license: Proprietary
metadata:
  hermes:
    tags: [IT, Inventario, Onboarding, PMI]
    related_skills: [fonti-ufficiali-vendor, gestione-incidenti, backup-e-storage, rete-e-firewall, microsoft-365-e-windows, vmware-vsphere]
---

# Onboarding IT e inventario

Non si gestisce quello che non si conosce. Il primo lavoro è una mappa vera,
scritta, che tutti possono leggere e che tu tieni aggiornata.

## Dove scrivi

Nella tua cartella di lavoro tieni:

- `it/inventario.md`: l'inventario, nelle sezioni sotto.
- `it/registro-modifiche.md`: ogni modifica fatta, con data, chi l'ha
  approvata, cosa è cambiato e come si torna indietro.
- `it/scadenze.md`: licenze, garanzie, certificati, domini, contratti, con data
  e preavviso.
- `it/fornitori.md`: chi segue cosa, contatti, contratto, orari, come aprire
  un ticket.
- `it/fonti-vendor.md`: le skill, i server MCP e le API ufficiali dei prodotti
  presenti (vedi `fonti-ufficiali-vendor`).

Non scrivi mai password, token o chiavi in questi file. Scrivi dove stanno
(per esempio "nella sezione Password dell'agente, voce FortiGate sede") e chi
le custodisce.

## Il primo incontro

Fai le domande a gruppi piccoli, in quest'ordine, e scrivi le risposte man mano.
Quando la persona non sa, annota "da verificare" e chi può saperlo (spesso il
fornitore IT esterno). Chiedi documenti esistenti prima di fare domande: un
vecchio inventario, un foglio Excel, un contratto di assistenza, uno schema di
rete valgono più di dieci domande.

1. **Persone e accessi.** Quante persone usano un computer? Chi è il referente
   IT interno e chi è il fornitore esterno? Chi può approvare una modifica?
2. **Posta e identità.** Microsoft 365, Google Workspace o posta del provider?
   Chi è amministratore del tenant? C'è un dominio Active Directory locale o
   Entra ID? L'MFA è attiva per tutti?
3. **Server e virtualizzazione.** Ci sono server in azienda? VMware vSphere,
   Hyper-V, Proxmox? Quanti host, quale vCenter, quali macchine virtuali
   importanti (gestionale, file server, controller di dominio)?
4. **Rete e sicurezza.** Marca e modello del firewall (Fortinet, SonicWall,
   Zyxel, WatchGuard, Sophos...), connettività e provider, VPN per chi lavora
   fuori, Wi-Fi, switch, sedi collegate.
5. **Storage e backup.** NAS o storage (Synology, QNAP, NetApp, HPE, Dell...),
   software di backup (Veeam, Acronis, nativo del NAS), dove vanno le copie,
   se c'è una copia fuori sede o immutabile, quando è stato fatto l'ultimo test
   di ripristino.
6. **Postazioni e periferiche.** Sistemi operativi, antivirus o EDR,
   stampanti e multifunzione, telefoni e centralino.
7. **Applicazioni.** Gestionale (Zucchetti, TeamSystem, SAP B1...), CRM,
   software di settore: dove girano e chi li assiste.
8. **Contratti e scadenze.** Licenze, garanzie, domini, certificati SSL,
   contratti di assistenza e connettività.
9. **Regole.** L'azienda rientra nella NIS2? C'è un DPO o un consulente
   privacy? Ci sono policy scritte (password, uso dei dispositivi, backup)?

## Verifica quello che puoi

Dove hai un accesso in lettura, verifica invece di fidarti della memoria di
qualcuno: elenco degli host e delle VM dal vCenter, versione del firmware dal
firewall, utenti e licenze dal portale Microsoft 365, stato degli ultimi job di
backup. Segna nell'inventario la fonte e la data di ogni dato verificato.

## Le sezioni dell'inventario

Per ogni voce: nome, ruolo, marca e modello, versione o firmware, dove si
trova, chi la assiste, scadenza di garanzia o supporto, fonte e data del dato.

- Identità e posta
- Server fisici e host di virtualizzazione
- Macchine virtuali
- Rete: connettività, firewall, switch, Wi-Fi, VPN
- Storage e backup
- Postazioni e periferiche
- Applicazioni
- Domini e certificati

## Alla fine del primo incontro

Riassumi in poche righe: cosa c'è, i tre rischi più seri che hai visto (per
esempio "nessun test di ripristino da un anno", "firewall con firmware fuori
supporto", "MFA non attiva per gli amministratori") e cosa proponi di fare per
primo. Proponi anche i compiti pianificati utili, che la persona attiva dalla
sezione **Attività pianificate**.

## Tenerlo aggiornato

- Ogni volta che scopri o cambi qualcosa, aggiorni la voce e la data.
- Una volta al mese rileggi le scadenze dei prossimi 60 giorni e avvisi.
- Un dato più vecchio di sei mesi su un sistema critico lo riverifichi.
