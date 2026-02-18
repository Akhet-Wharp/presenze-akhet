# Istruzioni Deploy Portale Presenze

## 1. Crea repository GitHub

1. Vai su https://github.com/new
2. **Repository name**: `presenze-akhet`
3. **Description**: `Portale gestione presenze Akhet srl`
4. **Public** (selezionato)
5. **NON** aggiungere README, .gitignore o license (già inclusi)
6. Click **Create repository**

## 2. Carica i file

Apri PowerShell nella cartella dove hai estratto questi file:

```powershell
# Inizializza git
git init

# Aggiungi tutti i file
git add .

# Primo commit
git commit -m "Initial commit - Portale Presenze Akhet"

# Rinomina branch in main
git branch -M main

# Collega al repository GitHub (sostituisci con il tuo URL)
git remote add origin https://github.com/Akhet-Wharp/presenze-akhet.git

# Push
git push -u origin main
```

**In caso di errore di autenticazione**:
- Usa un Personal Access Token invece della password
- Vai su GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
- Generate new token → seleziona `repo` → copia il token
- Usalo come password quando Git lo richiede

## 3. Attiva GitHub Pages

1. Vai sul repository: https://github.com/Akhet-Wharp/presenze-akhet
2. Click su **Settings** (in alto a destra)
3. Nel menu laterale, click su **Pages**
4. Sotto "Build and deployment":
   - **Source**: `Deploy from a branch`
   - **Branch**: seleziona `main` e `/root`
   - Click **Save**
5. Aspetta 1-2 minuti
6. La pagina si ricaricherà e mostrerà: "Your site is live at https://akhet-wharp.github.io/presenze-akhet/"

## 4. Configura Azure AD

1. Vai su [Azure Portal](https://portal.azure.com)
2. Azure Active Directory → App registrations → "Akhet GDL"
3. **Authentication** → **Platform configurations** → **Single-page application**
4. Click **Add URI**
5. Aggiungi: `https://akhet-wharp.github.io/presenze-akhet/`
6. Click **Save**

## 5. Aggiungi colonna GiornaleId su SharePoint

Se non l'hai già fatto:

1. Vai su SharePoint: https://akhet.sharepoint.com/sites/Akhet-Presenze
2. Apri la lista **Presenze**
3. Click sull'icona ingranaggio (⚙️) → **List settings**
4. Sotto "Columns", click **Create column**
5. Compila:
   - **Column name**: `GiornaleId`
   - **Type**: Number
   - **Minimum value**: 0
   - **Decimal places**: 0
6. Click **OK**

## 6. Testa il portale

1. Vai su https://akhet-wharp.github.io/presenze-akhet/
2. Click "Accedi con Microsoft 365"
3. Autorizza l'accesso
4. Verifica che carichi correttamente

## 7. Test sincronizzazione GDL → Presenze

1. Vai sul portale GDL: https://akhet-wharp.github.io/giornale-lavori/
2. Crea un nuovo giornale con un archeologo (es. "Giulio Punzo", 8 ore)
3. Vai sul portale Presenze
4. Verifica che appaia automaticamente una presenza per quella data

---

## Troubleshooting

**"Failed to fetch" o errore CORS**:
- Controlla che l'URL sia esattamente `https://akhet-wharp.github.io/presenze-akhet/` (senza `/index.html`)
- Aspetta qualche minuto dopo l'attivazione di GitHub Pages

**"Accesso negato al sito SharePoint"**:
- Verifica che il tuo utente abbia accesso ai siti SharePoint
- Controlla i permessi dell'app Azure AD

**Presenze non sincronizzate dal GDL**:
- Verifica che la colonna `GiornaleId` esista nella lista Presenze
- Controlla la console del browser (F12) per errori
- Verifica che entrambi i portali usino lo stesso Client ID Azure AD

---

Per supporto: contatta l'amministratore SharePoint
