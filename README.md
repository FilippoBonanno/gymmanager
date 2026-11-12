# GymCore

Gestionale completo per palestre con una **PWA per gli atleti** installabile sullo smartphone: anagrafiche, abbonamenti, certificati medici, schede di allenamento, appuntamenti, corsi di gruppo, comunicazioni e report. Ogni palestra ha la propria installazione dedicata (non SaaS).

**Progettato e sviluppato interamente da me** come full-stack: architettura, modello dati, backend, frontend, PWA, test e CI. Da maggio a luglio 2026, 28 milestone documentate nel changelog.

> Il codice è in un repository privato: posso mostrarlo durante un colloquio.

**Stack:** Laravel 12 · PHP 8.2 · Inertia.js 2 · Vue 3 (Composition API) · Tailwind CSS · Vite 7 · PWA (Workbox, push notification) · Spatie Permission · Sanctum · PHPUnit · Pint + Larastan · GitHub Actions · MySQL / PostgreSQL / SQLite

## Area gestionale (amministratori e trainer)
- **Clienti e trainer:** anagrafiche con foto, assegnazione trainer–cliente, anamnesi, misurazioni con grafico dei progressi, foto dei progressi.
- **Abbonamenti e catalogo pacchetti:** mensile, a ingressi, annuale; avvisi di scadenza in dashboard e contatori nel menu.
- **Certificati medici:** caricamento, storico, stati valido / in scadenza / scaduto con notifiche.
- **Archivio esercizi:** oltre 350 esercizi predefiniti con immagini di inizio e fine movimento, esercizi personalizzati della palestra, video YouTube, filtro anatomico per gruppo muscolare.
- **Schede di allenamento:** editor con serie, ripetizioni, recupero, carico, note in evidenza e **tecniche avanzate** (superserie, recuperi doppi), modelli condivisi, export PDF.
- **Appuntamenti** con calendario mensile e **corsi di gruppo**.
- **Comunicazioni:** messaggio del coach, avvisi con popup nella PWA, **sondaggi** con risultati in percentuale, notifiche push.
- **Report:** dashboard per ruolo, report operativi, presenze dei trainer, export CSV di clienti e presenze.
- **Permessi del trainer** configurabili su certificati e abbonamenti; setup guidato per una palestra nuova.
- **GDPR:** consenso privacy al primo accesso, export dei dati del cliente in ZIP (anche self-service), anonimizzazione, cancellazione automatica dei certificati scaduti con comando schedulato.

## Area atleta (PWA)
- Installabile su smartphone, con service worker, notifiche push e tema scuro.
- **Modalità allenamento:** esercizio per esercizio, con anteprima del movimento, selettore delle serie, cronometro di recupero e registrazione di carichi e ripetizioni.
- Scheda, abbonamento, certificato, appuntamenti, corsi e avvisi sempre a portata di mano.
- **Accesso con QR code:** l'amministratore genera un QR per ogni cliente, che imposta la password e entra; il token scade dopo 7 giorni e si invalida dopo il primo uso.

## Architettura e qualità
- **SPA ibrida con Inertia.js:** routing Laravel lato server, rendering Vue lato client, senza un'API REST separata.
- **3 ruoli** con permessi granulari; rotte separate (`/admin`, `/trainer`, `/me`) e ogni query filtrata per palestra.
- **Autorizzazione su più livelli:** middleware, controlli nei controller, filtro dei dati; registrazione pubblica disattivata di proposito.
- **Test** PHPUnit sui CRUD principali e sui controller, **analisi statica** (Larastan) e stile (Pint) in CI con GitHub Actions; audit di sicurezza e di accessibilità (WCAG).
- Dati demo completi (trainer, clienti, esercizi, schede, abbonamenti, certificati) per provare l'app in pochi minuti.

---
**Filippo Bonanno** · sviluppatore web (PHP, Laravel, Vue, PrestaShop) · altri progetti: [PadelCue](https://github.com/FilippoBonanno/padelcue), [gestionale multi shop](https://github.com/FilippoBonanno/gestionale-multi-shop), [NexGest](https://github.com/FilippoBonanno/nexgest)
