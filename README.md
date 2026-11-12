# GymManager

Gestionale per palestre: anagrafiche, abbonamenti, certificati medici, schede di allenamento e una **PWA per i clienti** installabile sullo smartphone. Ogni palestra ha la propria installazione dedicata (non SaaS).

Progettato e sviluppato da me come full-stack, dalla prima migrazione alla PWA.

> Il codice è in un repository privato: posso mostrarlo durante un colloquio.

**Stack:** Laravel 12 · PHP 8.2 · Inertia.js 2 · Vue 3 (Composition API) · Tailwind CSS · Vite 7 · PWA (Workbox) · Spatie Permission · Sanctum · PHPUnit 11 · MySQL/PostgreSQL (produzione), SQLite (sviluppo)

## Cosa fa
- **Clienti e trainer:** anagrafiche complete, assegnazione trainer–cliente, stati attivo/disattivo.
- **Abbonamenti:** mensile, a pacchetto, annuale, con avvisi di scadenza in dashboard e contatori in tempo reale nel menu.
- **Certificati medici:** caricamento file, storico, stato valido / in scadenza / scaduto con avvisi automatici.
- **Archivio esercizi:** esercizi predefiniti più quelli personalizzati di ogni palestra, con immagini e filtri per gruppo muscolare.
- **Schede di allenamento:** il trainer compone la scheda con serie, ripetizioni, recupero, carico e note; il cliente registra le serie svolte.
- **Dashboard per ruolo:** statistiche reali, scadenze critiche, prossimi appuntamenti, clienti senza scheda attiva.
- **PWA per il cliente:** interfaccia mobile-first installabile, navigazione in basso, service worker con precaching; scheda, abbonamento, certificato e appuntamenti sempre a portata di mano.
- **Accesso tramite QR code:** l'amministratore genera un QR per ogni cliente, che lo scansiona, imposta la password ed entra nella PWA; il token scade dopo 7 giorni e si invalida dopo il primo uso.

## Architettura
- **SPA ibrida con Inertia.js:** routing lato server Laravel e rendering Vue lato client, senza un'API REST separata.
- **Rotte per ruolo** (`/admin`, `/trainer`, `/me`) con 3 ruoli e permessi granulari; ogni query è filtrata per palestra.
- **Autorizzazione su più livelli:** middleware sulle rotte, controlli nei controller e filtro dei dati per palestra; registrazione pubblica disattivata di proposito.
- **PWA con layout dedicato** e service worker generato da Vite.
- **Test automatici** con PHPUnit.

## Stato
8 milestone su 10 completate; in pianificazione dati demo, copertura completa dei test e messa in produzione.

---
**Filippo Bonanno** · sviluppatore web (PHP, Laravel, Vue, PrestaShop) · altri progetti: [PadelCue](https://github.com/FilippoBonanno/padelcue), [gestionale multi shop](https://github.com/FilippoBonanno/gestionale-multi-shop), [NexGest](https://github.com/FilippoBonanno/nexgest)
