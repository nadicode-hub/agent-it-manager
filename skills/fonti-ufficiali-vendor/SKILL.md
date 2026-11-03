---
name: fonti-ufficiali-vendor
description: Dove trovare e come verificare gli strumenti ufficiali dei vendor IT per un agente (server MCP, skill, API, documentazione) per VMware, Microsoft, Fortinet, Sophos, WatchGuard, Zyxel, SonicWall, Cisco Meraki, Check Point, Ubiquiti, MikroTik, Veeam, Synology, QNAP, NetApp, HPE, Dell, Pure e Acronis, e come tenere aggiornato l'elenco. Da usare prima di lavorare su un prodotto di un vendor, quando si collega un nuovo sistema, e ogni mese per l'aggiornamento delle fonti.
license: Proprietary
metadata:
  hermes:
    tags: [IT, Vendor, MCP, API, Documentazione]
    related_skills: [onboarding-it, vmware-vsphere, microsoft-365-e-windows, rete-e-firewall, backup-e-storage]
---

# Fonti ufficiali dei vendor

Su un prodotto di un vendor lavori con le sue fonti, non con la memoria:
documentazione, avvisi di sicurezza, API e, quando esistono, server MCP e skill
pubblicati dal vendor. Il catalogo è in [references/catalogo.md](references/catalogo.md),
verificato al 3 novembre 2026. Il catalogo invecchia: la tua copia aggiornata,
con solo i prodotti presenti in azienda, è `it/fonti-vendor.md` nella tua
cartella.

## Ufficiale o no

Un server MCP, una skill o un repository è **ufficiale** solo se:

1. sta nell'organizzazione GitHub del vendor, e il sito dell'organizzazione è
   il dominio del vendor (per esempio `github.com/NetApp`, sito netapp.com); o
2. la documentazione o il blog del vendor ci rimandano; o
3. nel registro MCP ufficiale ha un nome verificato sul dominio del vendor
   (`com.microsoft/...`).

Un progetto scritto da un dipendente del vendor in un'organizzazione propria è
**della comunità**, anche se usa il nome del prodotto (è il caso di
`vmware-skills`, che dichiara di non essere un prodotto VMware ufficiale).
Usalo solo se la licenza lo permette, dicendo alla persona che è della
comunità, e preferisci la modalità in sola lettura.

## Usare un server MCP

- Prima la sola lettura: credenziali di un utente o profilo in sola lettura
  creato apposta, mai l'amministratore principale.
- Un server MCP si aggiunge dalla sezione **MCP** della tua pagina **Modifica**;
  i segreti vanno nella sezione **Password** come chiavi. Prepara tu i valori
  (indirizzo, nome della chiave) e di' alla persona esattamente cosa inserire.
- Dopo l'aggiunta, verifica con una lettura innocua (elenco dispositivi,
  versione) e annota in `it/fonti-vendor.md` cosa funziona e con quali permessi.
- Dove non esiste un server MCP, usa le API documentate del vendor dal
  terminale o dal browser, sempre con un utente in sola lettura per le
  verifiche.

## Tenere aggiornato l'elenco (ogni mese)

1. Per ogni vendor presente in azienda, cerca nel registro MCP ufficiale:
   `https://registry.modelcontextprotocol.io/v0/servers?search=<vendor>`. Il
   registro è incompleto: molti server ufficiali non ci sono.
2. Guarda i repository aggiornati di recente nelle organizzazioni GitHub dei
   vendor (elenco in fondo al catalogo) e i cataloghi dei vendor
   (`microsoft/mcp`, `NetApp/mcp`, `CheckPointSW/mcp-servers`, i repository
   `*-mcp-official` di `CiscoDevNet`).
3. Per ogni novità, applica la verifica "Ufficiale o no", leggi licenza,
   trasporto, autenticazione e se esiste una modalità in sola lettura.
4. Aggiorna `it/fonti-vendor.md` e riferisci in poche righe: cosa è nuovo, se
   conviene usarlo, cosa serve per collegarlo.

## Avvisi di sicurezza da leggere

Ogni settimana, per i prodotti presenti in azienda: Fortinet PSIRT
(fortiguard.com/psirt), avvisi Broadcom per VMware (VMSA), Microsoft Security
Update Guide (il secondo martedì del mese), Sophos, WatchGuard, SonicWall
(psirt.global.sonicwall.com), Zyxel, Cisco, Veeam KB, Synology e QNAP Security
Advisories, e gli avvisi di CSIRT Italia (csirt.gov.it) e del catalogo CISA
delle vulnerabilità sfruttate (KEV). Per ogni avviso che riguarda una versione
presente nell'inventario: gravità, se è sfruttato attivamente, cosa fare, entro
quando.
