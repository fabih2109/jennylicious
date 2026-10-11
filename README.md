## V0.21.0 – Rezeptbewertungen

Basis: V0.20.0. Keine Datenbankmigration, kein Reset.

Neu:
- Optionale Rezeptbewertung von 1 bis 5 Sternen; ohne Bewertung werden keine Sterne angezeigt.
- In Rezeptkacheln werden nur die tatsächlich vergebenen goldenen Sterne angezeigt (z. B. ★★★ statt ★★★☆☆).
- Im geöffneten Rezept wird die Bewertung auf dem Rezeptbild angezeigt.
- Im Rezepteditor kann die Bewertung oben gesetzt, geändert oder vollständig entfernt werden.
- Nach „Kochen beenden“ wird bei noch unbewerteten Rezepten gefragt, ob das Rezept jetzt geöffnet werden soll, um es anschließend manuell zu bewerten.
- Mit „Später“ wird genau eine lokale In-App-Erinnerung für den nächsten App-Start gespeichert.
- Beim nächsten Öffnen erscheint ausschließlich innerhalb von Jennylicious die Frage, ob die fehlende Bewertung nachgeholt werden soll. „Ja“ öffnet das Rezept, „Nein“ verwirft die Erinnerung.
- Keine Apple-/Android-Push-Nachrichten und keine externe Benachrichtigung.
- Bereits bewertete Rezepte erzeugen nach erneutem Kochen keine Bewertungsaufforderung.
- Bewertungsstatus und einmalige Erinnerung werden im bestehenden lokalen Speicher/Backup mitgeführt.

Unverändert:
- Data-Safety- und Backup-Logik.
- Bildspeicherung und Performance-Optimierungen.
- Einkaufsliste aus V0.20.0.
- Wochenplan und optionale Zusatzslots.
