---
type: Zettel
title: Nushell
description: null
modificationDate: 2025-11-06 03:47
tags: [coding]
coverImage: null
---

[https://www.nushell.sh](https://www.nushell.sh)

**Puoi avere ENTRAMBE le shell installate e funzionanti contemporaneamente!** 😊

## **Come funziona su Mac:**

### **Installazione di Nushell** (non rimuove Bash)

```bash
# Con Homebrew (raccomandato)
brew install nushell
# Oppure con cargo
cargo install nushell
```

**L'installazione di Nushell NON sostituisce Bash** - semplicemente aggiunge un'altra shell al tuo sistema.

## **Come alternare tra le shell:**

### **1. Temporaneamente (solo per la sessione corrente)**

```bash
# Da Bash → Nushell
nu
# Da Nushell → Bash
bash
# Per uscire e tornare alla shell precedente
exit
```

### **2. Cambiare shell predefinita**

```bash
# Verifica le shell disponibili
cat /etc/shells
# Cambia a Nushell come predefinita
chsh -s (which nu)        # Se sei in Nushell
chsh -s /usr/local/bin/nu # Se sei in Bash
# Per tornare a Bash come predefinita
chsh -s /bin/bash
```

### **3. Usare script specifici**

Puoi eseguire script direttamente con l'interprete desiderato:

```bash
# Esegui script Nushell
nu script.nu
# Esegui script Bash
bash script.sh
# Oppure rendi eseguibile e usa shebang
chmod +x script.nu
./script.nu
```

## **Scenario tipico di utilizzo:**

```bash
# Terminale apre con Bash (predefinito)
# Vuoi provare Nushell:
nu
# Ora sei in Nushell, fai quello che devi...
# Quando hai finito:
exit
# Sei tornato in Bash!
```

## **Esempio pratico con il tuo script:**

```bash
# Salva come analisi.nu
# Rendilo eseguibile
chmod +x analisi.nu
# Esegui con Nushell
./analisi.nu
# Oppure esegui esplicitamente
nu analisi.nu
# Nel frattempo, i tuoi script Bash continuano a funzionare!
chmod +x analisi.sh
./analisi.sh
```

## **Verifica quale shell stai usando:**

```bash
# In qualsiasi momento, per sapere che shell stai usando:
echo $SHELL
# Per vedere il processo effettivo:
ps -p $$
```

## **Raccomandazione per iniziare:**

1. **Installa Nushell** con Homebrew

2. **Provalo temporaneamente** con `nu`

3. **Torna a Bash** con `exit` quando vuoi

4. **Solo quando ti trovi bene**, considera di cambiare shell predefinita

**Il tuo Mac avrà sempre Bash disponibile** - è integrato nel sistema e Nushell non lo rimuove. Sono strumenti che coesistono pacificamente! 🐚✨


