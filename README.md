# analytics

questo repository contiene la configurazione dell'infrastruttura di analytics utilizzata da insidegubbio.com.

## cosa usiamo

utilizziamo **[Umami](https://umami.is)**, uno strumento di analytics open source, privacy-friendly e conforme al GDPR.

## cosa raccogliamo

umami raccoglie solo dati aggregati e anonimi:

- Numero di visitatori e pagine viste
- Paese e città di provenienza (basato su IP, non conservato)
- Dispositivo utilizzato (mobile, desktop, tablet)
- Browser e sistema operativo
- Sorgente del traffico (da dove arrivano i visitatori)
- Pagine più visitate

## cosa NON raccogliamo

- Nessun dato personale identificabile
- Nessun indirizzo IP conservato
- Nessun cookie di tracciamento
- Nessun fingerprinting del dispositivo
- Nessun dato condiviso con piattaforme pubblicitarie

maggiori info nella [privacy policy](https://insidegubbio.com/privacy)

---

## architettura

```
InsideGubbio.com
      │
      │  Script tracking (~2kb)
      ▼
Umami (analytics.insidegubbio.com)
      │
      │  Dati anonimi aggregati
      ▼
PostgreSQL (Neon)
Francoforte, Germania
```

### variabili d'ambiente richieste

| Variabile | Descrizione |
|---|---|
| `DATABASE_URL` | Stringa di connessione PostgreSQL (Neon) |
| `APP_SECRET` | Chiave segreta per la cifratura delle sessioni |
