# DOCUMENTAZIONE TECNICA — Croce Verde Baggio Web Portal
## Versione: 2.1.0
 
 STRUTTURA FILE PROGETTO:
 ```text
 /
 ├── index.html
 ├── css/
 │   ├── style.css        ← questo file
 ├── images/
 │   ├── logo_cvb-150x150.png
     └── B48.webp         ← hero background (copia in /images/)

 ```

## DIPENDENZE ESTERNE (CDN, nessuna installazione richiesta):
 - Google Fonts: Open Sans (già nel <head> di index.html)
 - Nessun runtime JS per il CSS (no Tailwind CDN necessario in prod)
 
### OPZIONE A — Deploy Statico (consigliato per MVP):
 - Carica tutti i file su server Apache/Nginx o hosting statico
 - Assicurarsi che B48.webp sia in /images/ (path relativo usato nel CSS)
 - Nessun build step richiesto
 - Compatibilità: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
 
### OPZIONE B — Tailwind CSS via CDN (sviluppo/prototipo):
 - Aggiungi nel <head>: <script src="https://cdn.tailwindcss.com"></script>
 - Poi configura le custom colors nel tailwind.config:
   tailwind.config = { theme: { extend: { colors: {
     'cvb-green': '#1b9d17', 'cvb-dark': '#1b5e20'
   }}}}
 
### OPZIONE C — Tailwind CSS via PostCSS (produzione ottimizzata):
 1. npm init -y
 2. npm install -D tailwindcss postcss autoprefixer
 3. npx tailwindcss init
 4. In tailwind.config.js: content: ["./*.html", "./**/*.html"]
 5. Crea src/input.css con: @tailwind base; @tailwind components; @tailwind utilities;
 6. Build: npx tailwindcss -i ./src/input.css -o ./css/style.css --minify
 7. Per watch in dev: aggiungere --watch
 
 PHP NOTE:
 - Il footer contiene <?php echo date("Y"); ?> per l'anno dinamico
 - Richiede un server PHP (es. Apache con mod_php, o PHP-FPM)
 - Alternativa statica: sostituire con anno hardcoded o JS: 
   <span id="year"></span> + document.getElementById('year').textContent = new Date().getFullYear();
 
#### PERFORMANCE:
 - Comprimi immagini: B48.webp già in formato ottimale (WebP)
 - Abilita gzip/brotli sul server per CSS
 - Aggiungi Cache-Control headers per assets statici
 
 ============================================================ */
```

---
