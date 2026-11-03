---
name: rete-e-firewall
description: "Gestire rete e firewall di una PMI con i prodotti più diffusi in Italia: Fortinet FortiGate, Sophos, WatchGuard, Zyxel, SonicWall, Cisco Meraki, Check Point, Ubiquiti UniFi, TP-Link Omada, MikroTik. Accesso via API con profilo in sola lettura, firmware e avvisi PSIRT, backup della configurazione, VPN, regole, Wi-Fi, connettività, e come fare una modifica senza lasciare l'azienda offline. Da usare per firewall, VPN, Wi-Fi, switch, internet lento o assente, porte, regole o firmware di rete."
license: Proprietary
metadata:
  hermes:
    tags: [IT, Rete, Firewall, Fortinet, Sophos, WatchGuard, Zyxel, SonicWall, VPN]
    related_skills: [fonti-ufficiali-vendor, sicurezza-e-conformita, gestione-incidenti, onboarding-it]
---

# Rete e firewall

## Accesso in sola lettura

Crea, o fai creare, un accesso dedicato a te con soli permessi di lettura.
Il catalogo in `fonti-ufficiali-vendor` dice cosa esiste per ogni vendor.

| Vendor | Come |
| --- | --- |
| Fortinet FortiGate | un amministratore REST API con profilo in sola lettura e host attendibili limitati all'IP della macchina di Nadia; il token va nella sezione **Password** come chiave. Letture tipiche: `GET /api/v2/monitor/system/status`, `/api/v2/monitor/system/firmware`, `/api/v2/monitor/vpn/ipsec`, `/api/v2/cmdb/firewall/policy` |
| Sophos Firewall / Central | Sophos Central API con credenziali di sola lettura, o API XML del firewall con un amministratore di sola lettura |
| WatchGuard | WatchGuard Cloud API (ID di accesso in sola lettura) |
| Zyxel | Nebula Open API con la chiave di un amministratore in sola lettura; per i firewall locali (USG FLEX, ATP) l'interfaccia web |
| SonicWall | SonicOS API (dalla 6.5.4) con un amministratore in sola lettura |
| Cisco Meraki | server MCP ufficiale `https://mcp.meraki.com/mcp` con la chiave API di un amministratore in sola lettura |
| Check Point (anche Quantum Spark) | server MCP ufficiali di Check Point, con un utente di sola lettura |
| Ubiquiti UniFi | chiave API (Site Manager o console locale) |
| TP-Link Omada | Open API del controller |
| MikroTik | REST API di RouterOS (v7.1+) con un utente del gruppo `read` |

Se non c'è API o accesso, lavori con quello che la persona ti mostra
(schermate, esportazioni della configurazione senza segreti).

## Il controllo periodico

- **Firmware**: versione installata, ultima versione consigliata dal vendor,
  avvisi PSIRT che la riguardano (vedi `fonti-ufficiali-vendor`). Una
  vulnerabilità critica su VPN SSL o interfaccia di gestione esposta è urgente.
- **Interfaccia di gestione**: mai raggiungibile da internet; se lo è, è la
  prima cosa da segnalare.
- **VPN**: tipo (preferire IPsec o la soluzione ZTNA del vendor dove la VPN SSL
  è sconsigliata), utenti attivi, MFA per gli accessi remoti, utenti di ex
  dipendenti da rimuovere.
- **Regole**: regole "any-any", porte aperte verso server interni (RDP aperto
  su internet è un rischio grave), regole senza commento o mai usate.
- **Servizi di sicurezza**: licenze di filtro web, IPS, antivirus e sandbox
  attive e in scadenza.
- **Backup della configurazione**: esiste una copia recente, cifrata, fuori dal
  firewall.
- **Connettività**: linee, linea di backup, failover provato.

## Fare una modifica senza restare offline

1. Scarica e archivia il backup della configurazione prima di toccare.
2. Scrivi la modifica, il rischio, il ritorno indietro e la finestra (fuori
   orario per tutto ciò che può interrompere internet o la VPN).
3. Chi esegue deve avere un accesso che non passi dalla regola che si cambia
   (accesso locale o console del vendor).
4. Dove il prodotto lo permette, usa un ripristino automatico se la modifica
   non viene confermata.
5. Dopo il sì, un passo alla volta, verifica (navigazione, VPN, servizi
   pubblicati), annota in `it/registro-modifiche.md`.

## Internet lento o assente: prima diagnosi

Chi è colpito (tutti, una sede, una persona), da quando, cosa è cambiato.
Poi: stato della linea dal pannello del provider o dal firewall, uso della
banda per IP, DNS (`nslookup`), `ping` e `traceroute` verso il gateway e verso
un indirizzo esterno, errori sulle interfacce. Riferisci cosa hai visto e il
prossimo passo, e chi chiamare (provider o fornitore IT) con i dati da dare.
