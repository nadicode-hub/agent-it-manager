---
name: microsoft-365-e-windows
description: Gestire Microsoft 365, Entra ID, Intune, Exchange Online, Teams, SharePoint, Active Directory e Windows Server in una PMI. Utenti e licenze, MFA e accesso condizionale, dispositivi, posta, condivisioni, aggiornamenti mensili di Windows, controller di dominio, con Microsoft Graph, i moduli PowerShell ufficiali, i server MCP Microsoft e la documentazione di Microsoft Learn. Da usare per tutto ciò che riguarda Microsoft, Office, Outlook, Teams, OneDrive, account aziendali, PC Windows o server Windows.
license: Proprietary
metadata:
  hermes:
    tags: [IT, Microsoft 365, Entra ID, Intune, Exchange, Windows Server, Active Directory]
    related_skills: [fonti-ufficiali-vendor, sicurezza-e-conformita, gestione-incidenti, onboarding-it]
---

# Microsoft 365 e Windows

## Documentazione prima di tutto

Usa il server MCP **Microsoft Learn** per cercare e leggere la documentazione
aggiornata prima di dare una procedura, e il server **Release Communications**
per sapere cosa cambia nei prossimi mesi in Microsoft 365. I nomi dei portali,
dei cmdlet e delle impostazioni cambiano spesso: verifica, non ricordare.

## Accesso al tenant

In ordine di preferenza:

1. **Microsoft MCP Server for Enterprise** (ufficiale, sola lettura su utenti,
   gruppi, dispositivi, accesso condizionale, licenze e log): richiede che un
   amministratore registri un'app nel tenant e conceda gli scope `MCP.*`.
   Prepara tu i passaggi con la documentazione Learn e guida la persona un
   passo alla volta.
2. **Microsoft Graph PowerShell SDK** (`Connect-MgGraph` con scope minimi in
   lettura come `User.Read.All`, `Directory.Read.All`, `Policy.Read.All`,
   `DeviceManagementManagedDevices.Read.All`, `AuditLog.Read.All`) e
   **Exchange Online PowerShell** (`Connect-ExchangeOnline`). Li esegui tu con
   l'accesso tramite codice del dispositivo (`Connect-MgGraph -UseDeviceCode`,
   `Connect-ExchangeOnline -Device`): mostri alla persona l'indirizzo e il
   codice, lei accede con il suo account e l'MFA, e tu leggi.
3. I portali (admin.microsoft.com, entra.microsoft.com, intune.microsoft.com)
   nel tuo browser, con l'accesso della persona, quando non c'è un'altra via.

Mai un account amministratore globale tuo e senza MFA. Le modifiche si fanno
dopo un sì, con l'account di un amministratore.

## Il controllo di sicurezza del tenant

Riferisci con priorità:

- MFA per tutti, e metodi resistenti al phishing per gli amministratori;
  impostazioni predefinite di sicurezza o criteri di accesso condizionale
  attivi; autenticazione legacy bloccata.
- Quanti amministratori globali (pochi, due almeno, nominativi e con MFA) e
  account di emergenza.
- Utenti disattivati che hanno ancora licenze o caselle inoltrate all'esterno;
  ex dipendenti ancora attivi.
- Regole di inoltro automatico verso domini esterni nelle caselle (segnale
  tipico di account compromesso).
- Licenze assegnate e non usate, rinnovi in arrivo.
- Dispositivi non conformi o non aggiornati in Intune.
- Condivisioni esterne in SharePoint e OneDrive aperte a "chiunque abbia il
  link".
- Punteggio di sicurezza (Secure Score) e le raccomandazioni principali.
- Dominio: record SPF, DKIM e DMARC della posta.

## Lavori ricorrenti

- **Nuovo dipendente:** account, licenza, gruppi, casella, MFA al primo
  accesso, dispositivo registrato in Intune, accesso alle cartelle giuste.
- **Uscita di un dipendente:** blocco dell'accesso e revoca delle sessioni
  il giorno stesso, cambio della password, casella disattivata con una risposta automatica
  che indica l'indirizzo a cui scrivere, recupero dei file di lavoro di
  OneDrive,
  rimozione da gruppi e dispositivi, licenza liberata. Mai cancellare dati
  senza il sì scritto del responsabile. Non inoltrare e non leggere la posta
  di un ex dipendente senza il parere del DPO o del consulente privacy: il
  Garante ha sanzionato più volte aziende che lo facevano.
- **Aggiornamenti di Windows:** il secondo martedì del mese Microsoft rilascia
  le patch. Leggi la Security Update Guide, segnala le vulnerabilità sfruttate
  attivamente, controlla in Intune o WSUS che i PC e i server si aggiornino, e
  pianifica il riavvio dei server in una finestra concordata.

## Active Directory e Windows Server

- Lettura con il modulo `ActiveDirectory` di PowerShell (`Get-ADUser`,
  `Get-ADComputer`, `Search-ADAccount -AccountInactive`), `dcdiag` e
  `repadmin /replsummary` per la salute dei controller di dominio.
- Controlla: almeno due controller di dominio o un backup dello stato del
  sistema verificato, account amministratori di dominio pochi e nominativi,
  account inattivi, password che non scadono sugli account di servizio,
  versione di Windows Server ancora supportata.
- Le date di fine supporto di Windows e Windows Server sono nella pagina
  Microsoft Lifecycle: segnala con un anno di anticipo. Da controllare
  subito: Windows Server 2016 esce dal supporto esteso il 12 gennaio 2027;
  Windows 10 riceve aggiornamenti solo con l'ESU; Exchange Server 2016 e 2019
  e Office 2016 e 2019 sono fuori supporto dal 14 ottobre 2025.
