---
name: vmware-vsphere
description: Gestire VMware vSphere (ESXi e vCenter) in una PMI. Stato di host, macchine virtuali, datastore e allarmi in sola lettura con govc, PowerCLI o il server MCP vmware-monitor, snapshot e loro pulizia, aggiornamenti di ESXi e vCenter con gli avvisi VMSA, licenze Broadcom, e cosa fare prima di ogni modifica. Da usare per tutto ciò che riguarda VMware, vSphere, ESXi, vCenter, macchine virtuali o datastore.
license: Proprietary
metadata:
  hermes:
    tags: [IT, VMware, vSphere, ESXi, vCenter, Virtualizzazione]
    related_skills: [fonti-ufficiali-vendor, backup-e-storage, gestione-incidenti, onboarding-it]
---

# VMware vSphere

## Accesso

- Chiedi un utente vCenter dedicato a te con il ruolo **Read-Only** a livello
  di vCenter, propagato. Per le operazioni approvate si usa un secondo utente
  con un ruolo limitato a quello che serve (per esempio snapshot e accensione
  delle VM), mai `administrator@vsphere.local`.
- Le credenziali vanno nella sezione **Password** della tua pagina **Modifica**
  (indirizzo del vCenter, utente, password come chiavi, per esempio
  `VCENTER_URL`, `VCENTER_USER`, `VCENTER_PASSWORD`).

## Strumenti, in ordine di preferenza

1. **govc** (CLI ufficiale di `vmware/govmomi`, un solo eseguibile): legge
   `GOVC_URL`, `GOVC_USERNAME`, `GOVC_PASSWORD`, `GOVC_INSECURE` (solo se il
   certificato è autofirmato e la persona lo accetta). Esempi in sola lettura:
   `govc about`, `govc ls /*/host/*`, `govc host.info -r`,
   `govc vm.info -r '*'`, `govc datastore.info`, `govc snapshot.tree -vm <vm>`,
   `govc events -n 50`, `govc tasks`.
2. **PowerCLI** (modulo PowerShell ufficiale `VCF.PowerCLI` o `VMware.PowerCLI`
   secondo la versione): `Connect-VIServer`, `Get-VMHost`, `Get-VM`,
   `Get-Datastore`, `Get-Snapshot`, `Get-VIEvent`.
3. **Server MCP `vmware-monitor`** (comunità, MIT, sola lettura, vedi
   `fonti-ufficiali-vendor`): utile per controlli frequenti. Spiega alla
   persona che non è un prodotto VMware ufficiale prima di proporlo.

Installare uno strumento sul computer dell'azienda richiede il sì della
persona.

## Il controllo periodico

Riferisci in una tabella breve:

- versione e build di vCenter e di ogni ESXi, rispetto all'ultima patch
  disponibile e agli avvisi VMSA che le riguardano;
- host: stato, connessione, modalità manutenzione, allarmi, uso di CPU e RAM;
- datastore: spazio libero (avviso sotto il 20%, urgente sotto il 10%);
- VM spente da più di 30 giorni, VM con VMware Tools non aggiornati o non in
  esecuzione;
- **snapshot più vecchi di 3 giorni o più grandi di qualche decina di GB**: uno
  snapshot non è un backup e se dimenticato riempie il datastore e rallenta la
  VM;
- certificati di vCenter e degli host in scadenza;
- ultimo backup riuscito di ogni VM importante (vedi `backup-e-storage`).

## Prima di ogni modifica

1. Descrivi la modifica, il rischio, come si torna indietro, la finestra.
2. Verifica che esista un backup recente e ripristinabile della VM o della
   configurazione (backup di vCenter dalla VAMI per gli aggiornamenti di
   vCenter).
3. Per una VM: snapshot prima, rimosso dopo la verifica (entro 72 ore).
4. Dopo il sì, esegui un passo alla volta e verifica.
5. Annota in `it/registro-modifiche.md`.

## Aggiornamenti

- L'ordine è: vCenter prima, poi gli host ESXi uno alla volta (modalità
  manutenzione con le VM spostate o spente), poi VMware Tools e versione
  hardware delle VM quando serve.
- Controlla la matrice di compatibilità e le note di rilascio nella
  documentazione Broadcom, e la compatibilità del software di backup con la
  nuova versione prima di aggiornare.
- Un avviso VMSA critico e sfruttato attivamente su una versione presente va
  segnalato subito, con la patch o la mitigazione ufficiale.

## Fine del supporto

Il supporto generale di vSphere 7 è finito il 2 ottobre 2025; quello di
vSphere 8 finisce l'11 ottobre 2027 (Broadcom). Un'azienda ancora su 6.7 o 7
riceve correzioni di sicurezza solo con un supporto esteso a pagamento: va
detto al primo incontro e pianificato.

## Licenze e contratti

Dal 2024 Broadcom vende vSphere solo in abbonamento (pacchetti VMware vSphere
Foundation e VMware Cloud Foundation, con condizioni che cambiano). Le
edizioni Essentials ed Essentials Plus non si vendono più, c'è un minimo di
core per processore e il rinnovo in ritardo costa di più: verifica sempre con
il partner le condizioni del momento. Tieni in `it/scadenze.md` la data di
scadenza dell'abbonamento o del supporto e avvisa con almeno 90 giorni di
anticipo. Se la persona valuta alternative (Proxmox VE,
Microsoft Hyper-V, Nutanix), prepara un confronto onesto su costi, migrazione,
backup compatibile e competenze del fornitore, senza decidere al posto suo.
