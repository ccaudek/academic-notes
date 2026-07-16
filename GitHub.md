GitHub richiede un token al posto della password per Git via HTTPS, e il token va inserito come “password” quando Git chiede le credenziali.
Quando cambio il fine-grained token è necessario seguire la procedura indicata di seguito.
### 1) Pulisci le credenziali vecchie salvate localmente

Nel repository locale:

```bash
git remote -v
git remote set-url origin https://github.com/ccaudek/utet-companion.git
```

Poi cancella le credenziali GitHub in cache:

```bash
printf "protocol=https\nhost=github.com\n\n" | git credential reject
```

Se sei su **Windows** e continua a usare il token vecchio: vai in **Credential Manager → Windows Credentials**, cerca la voce GitHub e cancellala. GitHub documenta proprio questo caso: credenziali errate o vecchie in Windows Credential Manager fanno fallire l’accesso. ([GitHub Docs](https://docs.github.com/get-started/git-basics/caching-your-github-credentials-in-git "Caching your GitHub credentials in Git - GitHub Docs"))

### 2) Rifai il push e inserisci il token come password

```bash
git push origin main
```

Quando chiede:

```text
Username: ccaudek
Password: <incolla il fine-grained token, non la password GitHub>
```

GitHub specifica che il nome utente va comunque inserito, ma l’autenticazione avviene tramite il token; senza username può restituire credenziali invalide. ([GitHub Docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens "Managing your personal access tokens - GitHub Docs"))

### 3) Se vuoi evitare problemi futuri

La soluzione più pulita è usare GitHub CLI o Git Credential Manager; GitHub li raccomanda per salvare le credenziali in modo sicuro con HTTPS. ([GitHub Docs](https://docs.github.com/get-started/git-basics/caching-your-github-credentials-in-git "Caching your GitHub credentials in Git - GitHub Docs"))

```bash
gh auth login
gh auth setup-git
```

Poi riprova:

```bash
git push origin main
```

Non mettere il token dentro l’URL remoto tipo `https://TOKEN@github.com/...`: funziona in certi casi, ma rischia di finire in log/config.

# Non è necessario ripetere la procedura per tutti i repository

## Stesso account GitHub e stesso token valido per più repo

Se hai configurato Git Credential Manager / cache credenziali per `github.com`, Git userà lo stesso login HTTPS per tutti i repository GitHub che hanno remote tipo:

```bash
https://github.com/OWNER/REPO.git
```

Quindi, per gli altri repo, di solito basta provare:

```bash
git push
```

Se il token ha accesso anche a quel repository, funzionerà.
