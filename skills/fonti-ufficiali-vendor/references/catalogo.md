# Catalogo delle fonti ufficiali (verificato al 3 novembre 2026)

"Ufficiale" segue la verifica della skill. "Comunità" vuol dire non del vendor.
Ricontrolla prima di collegare: nomi di pacchetti, indirizzi e permessi
cambiano.

## Senza credenziali, sempre utili

| Fonte | Indirizzo | Cosa dà |
| --- | --- | --- |
| Microsoft Learn MCP (ufficiale) | `https://learn.microsoft.com/api/mcp` (HTTP) | ricerca e lettura della documentazione Microsoft, Azure, Windows, M365 |
| Microsoft Release Communications MCP (ufficiale) | `https://www.microsoft.com/releasecommunications/mcp` (HTTP) | roadmap Microsoft 365 e novità Azure |

## VMware (Broadcom)

- **Nessuna raccolta ufficiale di skill o server MCP per gestire vSphere.**
- Broadcom: VCF Agentic AI Hub (Fling, ottobre 2026), un'appliance che aiuta a
  scrivere codice PowerCLI e Python; pesante (16 vCPU, 32 GB) e non gestisce i
  sistemi. Documentazione API: developer.broadcom.com.
- SDK e CLI ufficiali: `vmware/govmomi` (CLI `govc`, Apache-2.0),
  `vmware/pyvmomi`, PowerCLI, `vmware/vcf-sdk-python`.
- Comunità: `github.com/vmware-skills` (di un ingegnere Broadcom, "non un
  prodotto VMware ufficiale"). `VMware-Monitor` è in sola lettura e con
  licenza MIT (server MCP `vmware-monitor mcp`, pacchetto PyPI `vmware-monitor`);
  `VMware-AIops` fa anche modifiche (MIT). Diversi altri repository
  dell'organizzazione non hanno licenza: non copiarli.

## Microsoft

| Fonte | Tipo | Accesso | Note |
| --- | --- | --- | --- |
| MCP Server for Enterprise | MCP remoto `https://mcp.svc.cloud.microsoft/enterprise` | registrazione di un'app nel tenant e consenso agli scope `MCP.*` | solo lettura: utenti, gruppi, dispositivi, accesso condizionale, licenze, log di accesso; anteprima |
| Azure MCP Server | MCP locale `npx -y @azure/mcp@latest server start` | login Azure e ruoli RBAC | ha la modalità in sola lettura; MIT |
| Sentinel MCP | MCP remoto | Entra, Sentinel data lake | solo per chi ha Sentinel |
| Lokka (comunità, autore dipendente Microsoft) | MCP locale `npx -y @merill/lokka` | app registrata con permessi Graph limitati | anche scrittura: Intune ed Exchange tramite Graph |
| MicrosoftDocs/Agent-Skills | skill (CC BY 4.0 + MIT) | nessuno | solo servizi Azure (backup, site recovery, Arc, update manager, AVD) |
| microsoft/azure-skills | skill (MIT) | nessuno | include `entra-app-registration`, utile per l'app dell'MCP for Enterprise |

Nessun server MCP ufficiale per Intune, Exchange Online, Defender, Windows
Server o PowerShell: si usano Microsoft Graph (PowerShell SDK o REST), i moduli
PowerShell ufficiali e la documentazione via Learn MCP.

## Rete e sicurezza

| Vendor | Ufficiale per agenti | API documentata | Comunità |
| --- | --- | --- | --- |
| Fortinet (FortiGate) | nessun MCP per FortiGate e FortiManager (annunciato, "non ancora rilasciato"); MCP solo in FortiSIEM 7.5.1 | FortiOS REST API, token di un amministratore REST con profilo in sola lettura | `ry-ops/fortigate-mcp-server` (MIT) |
| Sophos | nessuno | Sophos Central API (OAuth2) | `rijul170/sophos-central-mcp` |
| WatchGuard | MCP annunciato senza documentazione | WatchGuard Cloud API | |
| Zyxel (Nebula) | nessuno | Nebula Open API (`api.nebula.zyxel.com`, chiave per amministratore) | |
| SonicWall | nessuno | SonicOS 7 API (dalla 6.5.4) | |
| Cisco Meraki | **MCP ufficiale** `https://mcp.meraki.com/mcp`, chiave API di un amministratore in sola lettura | Dashboard API | `meraki-magic-mcp-community` |
| Check Point | **MCP ufficiali** `CheckPointSW/mcp-servers` (npm `@chkp/*`, anche Quantum Spark per le PMI), MIT | Management API | |
| Stormshield | nessuno | SNS API | |
| Ubiquiti UniFi | nessuno | Site Manager API e Network Integration API (`X-API-Key`) | `sirkirby/unifi-mcp` (MIT, molto attivo) |
| TP-Link Omada | nessuno | Omada Open API sul controller | |
| MikroTik | nessuno | RouterOS REST API (v7.1+) con gruppo in sola lettura | `wiresage/mikrotik-mcp` (MIT) |
| HPE Aruba Instant On | nessuna API pubblica | | |

Raccolta della comunità da usare solo come riferimento: `Servosity/msp-skills`
(Apache-2.0), in gran parte non verificata dal vivo.

## Backup e storage

| Vendor | Ufficiale per agenti | Note |
| --- | --- | --- |
| Veeam | **MCP ufficiale** `veeam-ai/veeam-mcp-server`: `vi-mcp` (VBR, Veeam ONE, VSPC; sola lettura salvo abilitazione) e `vbr-mcp` (REST di VBR; limitarlo con il ruolo) | API REST di VBR 13 sulla porta 9419 |
| NetApp | **MCP ufficiali**: ONTAP MCP (con modalità in sola lettura), Harvest MCP, Digital Advisor (Active IQ) MCP, MCP della documentazione; catalogo `NetApp/mcp` | |
| HPE | **MCP ufficiali** GreenLake (`HewlettPackard/gl-mcp`, sola lettura); nessuno per Alletra, MSA, StoreOnce | API su developer.greenlake.hpe.com |
| Dell | server iDRAC di riferimento senza autenticazione (da non usare in produzione); MCP per lo storage annunciato per fine 2026 | API REST di PowerStore e Unity |
| Pure Storage | **MCP ufficiale** Fusion (`PureStorage-OpenConnect/fusion-mcp-server`), sola lettura predefinita | |
| Synology | nessuno | DSM Web API; comunità `cmeans/mcp-synology` (Apache-2.0, con livelli di permesso) |
| QNAP | nessuno | |
| Acronis | MCP annunciato a ottobre 2026 senza documentazione | Acronis Cyber Platform API |

## Organizzazioni GitHub da controllare ogni mese

vmware, Broadcom, microsoft, MicrosoftDocs, Azure, CiscoDevNet, CheckPointSW,
fortinet, NetApp, dell, HewlettPackard, PureStorage-OpenConnect, veeam-ai,
sophos, ZyxelNetworks. Per ognuna verifica che il sito dell'organizzazione sia
il dominio del vendor.
