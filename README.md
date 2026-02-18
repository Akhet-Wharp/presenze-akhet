# Akhet - Portale Presenze

Portale per la gestione delle presenze dei dipendenti Akhet srl, integrato con SharePoint Online.

## Funzionalità

- **Dashboard**: Riepilogo mensile ore lavorate per dipendente
- **Le mie presenze**: Visualizzazione e inserimento presenze giornaliere
- **Calendario**: Vista mensile con ore per giorno
- **Team** (Supervisor): Visualizzazione presenze del team
- **Commesse** (Supervisor/Admin): Gestione commesse
- **Utenti** (Admin): Gestione utenti e ruoli
- **Presenze totali** (Admin): Vista completa tutte le presenze

## Integrazione con GDL

Il portale è sincronizzato automaticamente con il [Giornale dei Lavori](https://akhet-wharp.github.io/giornale-lavori/):
- Quando si crea un giornale GDL, le ore degli archeologi/operai vengono automaticamente registrate come presenze
- La modifica di un giornale aggiorna le presenze corrispondenti
- L'eliminazione di un giornale elimina le presenze collegate

## Struttura SharePoint

Il portale si connette a due siti SharePoint:

**Sito GDL** (`Akhet-Giornaledeilavori`):
- Lista `Cantieri` (per codici commessa)
- Lista `Utenti` (per ruoli e permessi)

**Sito Presenze** (`Akhet-Presenze`):
- Lista `Presenze` (ore giornaliere per dipendente)
- Lista `Commesse` (elenco commesse)

## Tecnologie

- **Frontend**: HTML5, CSS3, JavaScript vanilla
- **Autenticazione**: MSAL.js (Microsoft Authentication Library)
- **API**: Microsoft Graph API
- **Storage**: SharePoint Online Lists

## Deploy

Il portale è pubblicato su GitHub Pages: https://akhet-wharp.github.io/presenze-akhet/

## Configurazione Azure AD

App Registration: `Akhet GDL` (condivisa con il portale GDL)
- Client ID: `8fed6f21-2658-45d9-94dc-047ab47780c0`
- Tenant ID: `ff2b5ebb-3297-4202-8c43-427cafda806d`
- Redirect URI: `https://akhet-wharp.github.io/presenze-akhet/`

---

© 2026 Akhet srl
