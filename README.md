
<html lang="de">
<head>
    
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kantine</title>
    <style>
        /* ========================================
           DESIGN: SCHLICHTES GRAU
           ======================================== */
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #f5f5f5;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            min-height: 600px;
        }
        /*überschrift*/
        h1 {
            color: #2c3e50;
            margin-bottom: 30px;
            text-align: center;
            font-size: 36px;
            font-weight: 300;
        }

        h2 {
            color: #34495e;
            margin: 25px 0 15px 0;
            font-size: 24px;
            font-weight: 400;
        }

        /* Schulden-Warnung (klein oben) */
        .schulden-warnung {
            background: #fff5f5;
            border: 2px solid #d98880;
            padding: 12px 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            text-align: center;
            font-size: 14px;
            color: #943126;
        }

        .schulden-warnung strong {
            color: #c0392b;
            font-size: 16px;
        }

        /* Header-Buttons oben RECHTS untereinander */
        .header-buttons-container {
            position: absolute;
            top: 40px;
            right: 40px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            align-items: flex-end;
        }

        .header-btn {
            background: #34495e;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            font-size: 15px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            white-space: nowrap;
        }

        .header-btn:hover {
            background: #2c3e50;
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }

        /* Sortier-Button */
        .sortier-info {
            text-align: center;
            color: #7f8c8d;
            font-size: 14px;
            margin-bottom: 15px;
            font-style: italic;
        }

        /* Hauptbuttons (Wachabteilung, B-Dienst, Gäste) */
        .kategorie-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin: 50px 0;
        }

        .kategorie-btn {
            background: white;
            border: 3px solid #bdc3c7;
            padding: 60px 30px;
            border-radius: 12px;
            font-size: 24px;
            font-weight: 500;
            color: #2c3e50;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }

        .kategorie-btn:hover {
            border-color: #34495e;
            background: #ecf0f1;
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        /* ========================================
           BENUTZER-GRID - NORMALE KARTEN (KEIN SCROLL-CONTAINER)
           ======================================== */
        
        .benutzer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .benutzer-karte {
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #bdc3c7;
            cursor: pointer;
            transition: all 0.3s;
        }

        .benutzer-karte:hover {
            border-color: #34495e;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .benutzer-karte.platzhalter {
            opacity: 0.4;
            border-style: dashed;
        }

        /* NAME GRÖßER */
        .benutzer-name {
            font-size: 18px;
            font-weight: 600;
            color: #2c3e50;
            margin-bottom: 8px;
        }

        /* GUTHABEN KLEINER + DEZENTE FARBEN */
        .benutzer-guthaben {
            font-size: 16px;
            font-weight: 500;
        }

        .guthaben-positiv {
            color: #27ae60; /* Sanftes Grün statt knallgrün */
        }

        .guthaben-negativ {
            color: #c0392b; /* Gedämpftes Rot statt knallrot */
        }

        /* Buttons */
        button {
            background: #7f8c8d;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
            margin: 5px;
        }

        button:hover {
            background: #95a5a6;
            transform: translateY(-2px);
        }

        button.primary {
            background: #34495e;
            font-weight: 500;
        }

        button.primary:hover {
            background: #2c3e50;
        }

        button.danger {
            background: #e74c3c;
        }

        button.danger:hover {
            background: #c0392b;
        }

        button.success {
            background: #27ae60;
        }

        button.success:hover {
            background: #229954;
        }

        /* Eingabefelder */
        input, select {
            padding: 12px;
            border: 2px solid #bdc3c7;
            border-radius: 8px;
            font-size: 16px;
            width: 100%;
            margin: 8px 0;
            background: white;
            transition: border 0.3s;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #34495e;
        }

        /* ========================================
           PRODUKTLISTE - KATEGORISIERT
           ======================================== */
        
        .produkt-kategorie {
            margin: 25px 0;
        }

        .produkt-kategorie h3 {
            color: #34495e;
            font-size: 20px;
            font-weight: 500;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #bdc3c7;
        }

        .produkt-liste {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 15px;
            margin-bottom: 15px;
        }

        .produkt-karte {
            background: white;
            padding: 20px;
            border-radius: 12px;
            border: 2px solid #bdc3c7;
            transition: all 0.3s;
        }

        .produkt-karte:hover {
            border-color: #34495e;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .produkt-name {
            font-weight: 500;
            color: #2c3e50;
            margin-bottom: 8px;
            font-size: 17px;
        }

        .produkt-preis {
            color: #34495e;
            font-size: 19px;
            font-weight: bold;
            margin-bottom: 12px;
        }

        /* Individueller Betrag */
        .individueller-betrag {
            background: #fff9e6;
            border: 2px solid #f39c12;
            padding: 20px;
            border-radius: 12px;
            margin: 25px 0;
        }

        .individueller-betrag h3 {
            color: #d68910;
            margin-bottom: 15px;
        }

        .betrag-eingabe-container {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .betrag-eingabe-container input {
            flex: 1;
            margin: 0;
        }

        .betrag-eingabe-container button {
            margin: 0;
            background: #f39c12;
        }

        .betrag-eingabe-container button:hover {
            background: #d68910;
        }

        /* Guthaben-Anzeige */
        .guthaben-box {
            background: #34495e;
            color: white;
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            margin: 20px 0;
        }

        .guthaben-betrag {
            font-size: 32px;
            font-weight: bold;
            margin-top: 10px;
        }

        /* Warenkorb */
        .warenkorb-item {
            background: white;
            padding: 15px;
            margin: 10px 0;
            border-radius: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 4px solid #34495e;
        }

        /* Einkaufsliste */
        .einkaufsliste {
            background: white;
            padding: 25px;
            border-radius: 12px;
            margin: 20px 0;
            border: 2px solid #bdc3c7;
        }

        .einkaufsitem {
            display: flex;
            justify-content: space-between;
            padding: 12px;
            margin: 8px 0;
            background: #ecf0f1;
            border-radius: 6px;
        }

        .einkaufsitem-name {
            font-weight: 500;
            color: #2c3e50;
        }

        .einkaufsitem-menge {
            font-weight: bold;
            color: #34495e;
        }

        /* Schulden-Box */
        .schulden-box {
            background: white;
            padding: 25px;
            border-radius: 12px;
            margin: 20px 0;
            border: 2px solid #e74c3c;
            text-align: center;
        }

        .schulden-betrag {
            font-size: 48px;
            font-weight: bold;
            color: #c0392b;
            margin: 15px 0;
        }

        /* Versteckte Bereiche */
        .hidden {
            display: none;
        }

        /* Meldungen */
        .meldung {
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            display: none;
        }

        .meldung.erfolg {
            background: #d4edda;
            color: #155724;
            border: 2px solid #c3e6cb;
        }

        .meldung.fehler {
            background: #f8d7da;
            color: #721c24;
            border: 2px solid #f5c6cb;
        }

        /* Mengen-Steuerung */
        .menge-steuerung {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }

        .menge-btn {
            width: 40px;
            height: 40px;
            padding: 0;
            font-size: 20px;
            font-weight: bold;
            background: #34495e;
        }

        .menge-btn:hover {
            background: #2c3e50;
        }

        .menge-anzeige {
            font-size: 18px;
            font-weight: bold;
            min-width: 30px;
            text-align: center;
            color: #2c3e50;
        }

        /* Admin-Bereich */
        .admin-section {
            background: white;
            padding: 25px;
            border-radius: 12px;
            margin: 20px 0;
            border: 2px solid #bdc3c7;
        }

        .form-group {
            margin: 15px 0;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #2c3e50;
            font-weight: 500;
        }

        /* Gast-Eingabe */
        .gast-eingabe {
            background: white;
            padding: 20px;
            border-radius: 12px;
            margin: 20px 0;
            border: 2px solid #bdc3c7;
        }

        .zurück-btn {
            background: #95a5a6;
            margin-bottom: 20px;
        }

        .zurück-btn:hover {
            background: #7f8c8d;
        }

        /* Guthaben-Verwaltungs-Karte */
        .guthaben-verwaltung-karte {
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #bdc3c7;
            margin-bottom: 12px;
        }

        .guthaben-verwaltung-karte h3 {
            color: #2c3e50;
            margin-bottom: 12px;
            font-size: 16px;
        }

        .guthaben-eingabe {
            display: flex;
            gap: 10px;
            align-items: center;
            margin-top: 10px;
        }

        .guthaben-eingabe input {
            flex: 1;
            margin: 0;
        }

        .guthaben-eingabe button {
            margin: 0;
        }

        /* ========================================
           PREISVERWALTUNG
           ======================================== */
        
        .preis-kategorie {
            background: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            border: 2px solid #bdc3c7;
        }

        .preis-kategorie h3 {
            color: #34495e;
            font-size: 18px;
            font-weight: 500;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #ecf0f1;
        }

        .preis-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 12px;
        }

        .preis-item {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            border: 2px solid #e0e0e0;
            transition: all 0.3s;
        }

        .preis-item:hover {
            border-color: #34495e;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .preis-item-name {
            font-weight: 500;
            color: #2c3e50;
            margin-bottom: 8px;
            font-size: 15px;
        }

        .preis-item-aktuell {
            color: #7f8c8d;
            font-size: 13px;
            margin-bottom: 10px;
        }

        .preis-eingabe {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .preis-eingabe input {
            flex: 1;
            padding: 8px;
            font-size: 14px;
            margin: 0;
        }

        .preis-eingabe button {
            padding: 8px 15px;
            font-size: 14px;
            margin: 0;
            background: #34495e;
        }

        .preis-eingabe button:hover {
            background: #2c3e50;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header-Buttons oben RECHTS untereinander -->
        <div class="header-buttons-container">
            <button class="header-btn" onclick="kochBereichOeffnen()">👨‍🍳 Küche</button>
            <button class="header-btn" onclick="guthabenVerwaltungLoginOeffnen()">⚙️ Verwaltung</button>
        </div>

        <!-- ===== STARTSEITE: KATEGORIE AUSWÄHLEN ===== -->
        <div id="startseite">
            <h1>🍽️ Kantine</h1>
            
            <div class="kategorie-grid">
                <button class="kategorie-btn" onclick="kategorieAuswaehlen('wachabteilung')">
                    Wachabteilung
                </button>
                <button class="kategorie-btn" onclick="kategorieAuswaehlen('bdienst')">
                    B-Dienst
                </button>
                <button class="kategorie-btn" onclick="kategorieAuswaehlen('gaeste')">
                    Gäste
                </button>
            </div>
        </div>

        <!-- ===== BENUTZER-AUSWAHL FÜR BESTELLUNG ===== -->
        <div id="benutzer-auswahl" class="hidden">
            <button class="zurück-btn" onclick="zurückZurStartseite()">← Zurück</button>
            
            <!-- Schulden-Warnung (nur bei Wachabteilung) -->
            <div id="schulden-warnung-box" class="hidden"></div>
            
            <h1 id="kategorie-titel">Benutzer auswählen</h1>
            
            <!-- Info: Automatisch sortiert 
            <div class="sortier-info">
                📋 Sortiert nach Nachnamen (A-Z)
            </div>
            -->

            
            <!-- Benutzer-Liste (normale Seiten-Scroll) -->
            <div class="benutzer-grid" id="benutzer-liste"></div>
            
            <!-- Nur bei Gästen: Name eingeben -->
            <div id="gast-bereich" class="hidden">
                <div class="gast-eingabe">
                    <h2>Gastname eingeben</h2>
                    <input type="text" id="gast-name-input" placeholder="Name des Gastes">
                    <button class="success" onclick="gastNameSetzen()">Name speichern & weiter</button>
                </div>
            </div>
        </div>

        <!-- ===== BESTELL-SEITE ===== -->
        <div id="bestell-bereich" class="hidden">
            <button class="zurück-btn" onclick="zurückZuBenutzerauswahl()">← Zurück</button>
            
            <div class="guthaben-box">
                <div>Angemeldet als: <strong id="aktueller-benutzer"></strong></div>
                <div class="guthaben-betrag" id="guthaben-anzeige">0.00 €</div>
            </div>

            <h2>Produkte auswählen</h2>
            
            <!-- KATEGORISIERTE PRODUKTE -->
            <div id="produkte-container"></div>

            <!-- INDIVIDUELLER BETRAG -->
            <div class="individueller-betrag">
                <h3>💶 Individueller Betrag</h3>
                <p style="color: #7f8c8d; font-size: 14px; margin-bottom: 10px;">
                    Für Sonderartikel oder manuelle Beträge
                </p>
                <div class="betrag-eingabe-container">
                    <input type="number" id="individueller-betrag-input" placeholder="Betrag in € (z.B. 2.50)" step="0.01">
                    <input type="text" id="individueller-bezeichnung-input" placeholder="Bezeichnung (optional)">
                    <button onclick="individuellenBetragHinzufugen()">Hinzufügen</button>
                </div>
            </div>

            <h2>Warenkorb</h2>
            <div id="warenkorb"></div>
            <div style="text-align: right; margin-top: 20px;">
                <strong style="font-size: 24px; color: #2c3e50;">Summe: <span id="summe-anzeige">0.00</span> €</strong>
            </div>
            
            <button class="primary" onclick="bestellungAbschliessen()" style="width: 100%; padding: 20px; font-size: 20px; margin-top: 20px;">
                Jetzt bestellen
            </button>
        </div>

        <!-- ===== KOCH-BEREICH (OHNE PASSWORT) ===== -->
        <div id="koch-bereich" class="hidden">
            <button class="zurück-btn" onclick="zurückZurStartseite()">← Zurück</button>
            
            <h1>👨‍🍳 Küchen-Bereich</h1>

            <!-- Einkaufsliste -->
            <div class="einkaufsliste">
                <h2>📋 Einkaufsliste</h2>
                <div id="einkaufsliste-anzeige"></div>
                <button class="danger" onclick="tagesabschluss()" style="margin-top: 20px; width: 100%; padding: 15px;">
                    🗑️ Tagesabschluss (Liste auf 0 setzen & Backup)
                </button>
            </div>

            <!-- Schulden-Übersicht (GESAMT) -->
            <div class="schulden-box">
                <h2>💰 Gesamtschulden</h2>
                <div class="schulden-betrag" id="schulden-betrag">0.00 €</div>
            </div>

        </div>

        <!-- ===== GUTHABEN-VERWALTUNG LOGIN ===== -->
        <div id="guthaben-login" class="hidden">
            <button class="zurück-btn" onclick="zurückZurStartseite()">← Zurück</button>
            
            <h1>⚙️ Verwaltung</h1>
            
            <div class="admin-section">
                <h2>Passwort eingeben</h2>
                <input type="password" id="admin-passwort" placeholder="Passwort">
                <button class="primary" onclick="guthabenVerwaltungLogin()">Anmelden</button>
            </div>
        </div>

        <!-- ===== GUTHABEN-VERWALTUNG KATEGORIE-AUSWAHL ===== -->
        <div id="guthaben-kategorie" class="hidden">
            <button class="zurück-btn" onclick="guthabenVerwaltungAbmelden()">← Guthaben-Verwaltung verlassen</button>
            
            <h1>💳 Guthaben verwalten</h1>
            
            <div class="kategorie-grid">
                <button class="kategorie-btn" onclick="guthabenKategorieAuswaehlen('wachabteilung')">
                    Wachabteilung
                </button>
                <button class="kategorie-btn" onclick="guthabenKategorieAuswaehlen('bdienst')">
                    B-Dienst
                </button>
                <button class="kategorie-btn" onclick="guthabenKategorieAuswaehlen('gaeste')">
                    Gäste
                </button>
            </div>
            
            <!-- Preisverwaltung-Button (zentriert, etwas abgesetzt) -->
            <div style="text-align: center; margin-top: 30px;">
                <button class="kategorie-btn" onclick="preisverwaltungOeffnen()" style="max-width: 400px; background: #ecf0f1; border-color: #95a5a6;">
                    💶 Preisverwaltung
                </button>
            </div>
        </div>

        <!-- ===== GUTHABEN-VERWALTUNG PERSONEN-LISTE ===== -->
        <div id="guthaben-personen" class="hidden">
            <button class="zurück-btn" onclick="zurückZuGuthabenKategorie()">← Zurück zu Kategorien</button>
            
            <h1 id="guthaben-kategorie-titel">Guthaben verwalten</h1>
            
            <div id="guthaben-personen-liste"></div>
        </div>

        <!-- ===== PREISVERWALTUNG (SEPARATE SEITE) ===== -->
        <div id="preisverwaltung" class="hidden">
            <button class="zurück-btn" onclick="zurückZuGuthabenKategorie()">← Zurück</button>
            
            <h1>💶 Preisverwaltung</h1>
            <p style="text-align: center; color: #7f8c8d; font-size: 14px; margin-bottom: 25px;">
                
            </p>
            
            <div id="preisverwaltung-liste"></div>
        </div>

        <!-- Meldungen -->
        <div id="meldung" class="meldung"></div>
    </div>

    <script>
        /* ========================================
           JAVASCRIPT - HIER BEGINNT DIE LOGIK
           ======================================== */

        // ===== KONFIGURATION =====
        const ADMIN_PASSWORT = "admin123"; // WICHTIG: Ändere das Passwort hier!

        /* ========================================
           DATEN-STRUKTUR
           
           Hier werden alle Daten der App gespeichert:
           - produkte: Liste aller kaufbaren Artikel
           - benutzer: Alle Personen nach Kategorien sortiert
           - einkaufsliste: Zählt die bestellten Mengen
           ======================================== */
        
         // PRODUKTE - NACH KATEGORIEN ORGANISIERT
        let produktKategorien = [
            {
                name: "Brötchen",
                produkte: [
                    { id: 1, name: "Normal", preis: 1.30, typ: "brötchen_normal" },
                    { id: 2, name: "Mehrkorn", preis: 1.70, typ: "brötchen_mehrkorn" },
                    { id: 3, name: "Sunny", preis: 1.50, typ: "brötchen_sunny" },
                    { id: 4, name: "Roggen", preis: 1.70, typ: "brötchen_roggen" }
                ]
            },
            {
                name: "Eier",
                produkte: [
                    { id: 5, name: "Ei", preis: 0.40, typ: "ei" }
                ]
            },
            {
                name: "Abendessen",
                produkte: [
                    { id: 6, name: "Normal", preis: 6.00, typ: "abendessen_normal" },
                    { id: 7, name: "Vegetarisch", preis: 6.00, typ: "abendessen_vegetarisch" }
                ]
            },
             {
                name: "Getränke",
                produkte: [
                    { id: 8, name: "Kaffeeflatrate", preis: 1.00, typ: "sonstiges" },
                    { id: 9, name: "Cola/Fanta/Limo", preis: 1.30, typ: "sonstiges" },
                    
                    
                ]
            },
            {
                name: "Kuchen & Eis",
                produkte: [
                    { id: 11, name: "Kuchen/Eis", preis: 1.20, typ: "sonstiges" }
                ]
            },
            {
                name: "Süßigkeiten",
                produkte: [
                    { id: 12, name: "Süßes Klein", preis: 0.40, typ: "sonstiges" },
                    { id: 13, name: "Süßes Groß", preis: 0.80, typ: "sonstiges" }
                ]
            }
        ];

        // Flache Produkt-Liste für einfachen Zugriff (wird automatisch erstellt)
        let alleProdukteFlach = [];
        produktKategorien.forEach(kategorie => {
            alleProdukteFlach = alleProdukteFlach.concat(kategorie.produkte);
        });

        // BENUTZER - VIELE PERSONEN IN JEDER KATEGORIE
        let benutzer = {
            wachabteilung: [
                { id: "w1", name: "Stüwe", guthaben: 0.00 },
                { id: "w2", name: "Wilhelmi", guthaben: 0.00 },
                { id: "w3", name: "Ridder", guthaben: 0.00 },
                { id: "w4", name: "Felker", guthaben: 0.00 },
                { id: "w5", name: "Propenauer", guthaben: 0.00 },
                { id: "w6", name: "Wunderlich", guthaben: 0.00 },
                { id: "w7", name: "Nahrup", guthaben: 0.00 },
                { id: "w8", name: "Henning", guthaben: 0.00 },
                { id: "w9", name: "Fries", guthaben: 0.00 },
                { id: "w10", name: "Nelle", guthaben: 0.00 },
                { id: "w11", name: "Lechelt", guthaben: 0.00 },
                { id: "w12", name: "Schiefer", guthaben: 0.00 },
                { id: "w13", name: "Lewandrowska", guthaben: 0.00 },
                { id: "w14", name: "Klauke", guthaben: 0.00 },
                { id: "w15", name: "Baake", guthaben: 0.00 },
                { id: "w16", name: "Grundkötter", guthaben: 0.00 },
                { id: "w17", name: "Petrich", guthaben: 0.00 },
                { id: "w18", name: "Augustin", guthaben: 0.00 },
                { id: "w19", name: "Bertram", guthaben: 0.00 },
                { id: "w20", name: "Bücker", guthaben: 0.00 },
                { id: "w21", name: "Bulla", guthaben: 0.00 },
                { id: "w22", name: "Ebbing", guthaben: 0.00 },
                { id: "w23", name: "Pankratz", guthaben: 0.00 },
                { id: "w24", name: "Stegemann", guthaben: 0.00 },
                { id: "w25", name: "Reckendrees", guthaben: 0.00 },
                { id: "w26", name: "Rohrbach", guthaben: 0.00 }
                
            ],
            bdienst: [
                { id: "b1", name: "Henning", guthaben: 0.00 },
                { id: "b2", name: "Leitlof", guthaben: 0.00 },
                { id: "b3", name: "König", guthaben: 0.00 },
                { id: "b4", name: "Gräfe", guthaben: 0.000 },
                { id: "b5", name: "Hülsmann", guthaben: 0.00 },
                { id: "b6", name: "Hüsemann", guthaben: 0.00 },
                { id: "b7", name: "Schilp", guthaben: 0.00 },
                { id: "b8", name: "Vornholt", guthaben: 0.00 },
                { id: "b9", name: "Graf", guthaben: 0.00 },
                { id: "b10", name: "Pyka", guthaben: 0.00 },
                { id: "b11", name: "Neuhaus", guthaben: 0.00 },
                { id: "b12", name: "Hüttmann", guthaben: 0.00 },
                { id: "b13", name: "Güldner", guthaben: 0.00 },
                { id: "b14", name: "Dörk", guthaben: 0.00 },
                { id: "b15", name: "Hansmeyer", guthaben: 0.00 },
                { id: "b16", name: "Gehle", guthaben: 0.00 },
                { id: "b17", name: "Tente", guthaben: 0.00 },
                { id: "b18", name: "Kiunke", guthaben: 0.00 },
                { id: "b19", name: "Helmig", guthaben: 0.00 },
                { id: "b20", name: "Woydak", guthaben: 0.00 },
                { id: "b21", name: "Pieper", guthaben: 0.00 },
                { id: "b22", name: "Arens", guthaben: 0.00 },
                { id: "b23", name: "Juckel", guthaben: 0.00 },
                { id: "b24", name: "Haase", guthaben: 0.00 },
                { id: "b25", name: "Röhren", guthaben: 0.00 },
                { id: "b26", name: "Epp", guthaben: 0.00 },
                { id: "b27", name: "Zoller", guthaben: 0.00 },
                { id: "b28", name: "Bartsch", guthaben: 0.00 }
            ],
            gaeste: [
                // 12 leere Platzhalter für Gäste
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true },
                { name: "", guthaben: 0.00, istPlatzhalter: true }
            ]
        };

        // EINKAUFSLISTE - Zählt bestellte Mengen
        let einkaufsliste = {
            brötchen_normal: 0,
            brötchen_mehrkorn: 0,
            brötchen_sunny: 0,
            brötchen_roggen: 0,
            ei: 0,
            abendessen_normal: 0,
            abendessen_vegetarisch: 0
        };

        // AKTUELLER ZUSTAND - Merkt sich wo der Benutzer gerade ist
        let aktuelleKategorie = null;      // Welche Kategorie gewählt? (wachabteilung/bdienst/gaeste)
        let aktuellerBenutzer = null;      // Wer ist angemeldet?
        let aktuellerGastIndex = null;     // Bei Gästen: Welcher Platz?
        let warenkorb = [];                // Was liegt im Warenkorb?
        let guthabenVerwaltungKategorie = null; // Im Admin-Bereich: Welche Kategorie?

        /* ========================================
           DATEN SPEICHERN & LADEN
           
           Diese Funktionen speichern alle Daten
           im Browser (localStorage).
           So bleiben die Daten auch nach einem
           Neustart der App erhalten!
           ======================================== */
        
        function datenSpeichern() {
            // Speichere alle wichtigen Daten als Text im Browser
            localStorage.setItem('benutzer', JSON.stringify(benutzer));
            localStorage.setItem('produktKategorien', JSON.stringify(produktKategorien));
            localStorage.setItem('einkaufsliste', JSON.stringify(einkaufsliste));
            
            console.log('✅ Daten wurden gespeichert!');
        }

        function datenLaden() {
            // Lade gespeicherte Daten aus dem Browser
            const gespeicherteBenutzer = localStorage.getItem('benutzer');
            const gespeicherteKategorien = localStorage.getItem('produktKategorien');
            const gespeicherteEinkaufsliste = localStorage.getItem('einkaufsliste');

            // Wenn Daten vorhanden sind, lade sie
            if (gespeicherteBenutzer) {
                benutzer = JSON.parse(gespeicherteBenutzer);
            }
            if (gespeicherteKategorien) {
                produktKategorien = JSON.parse(gespeicherteKategorien);
                // Flache Liste neu erstellen
                alleProdukteFlach = [];
                produktKategorien.forEach(kategorie => {
                    alleProdukteFlach = alleProdukteFlach.concat(kategorie.produkte);
                });
            }
            if (gespeicherteEinkaufsliste) {
                einkaufsliste = JSON.parse(gespeicherteEinkaufsliste);
            }
            
            console.log('✅ Daten wurden geladen!');
        }

        /* ========================================
           NAVIGATION
           
           Diese Funktionen steuern, welche Seite
           gerade angezeigt wird.
           ======================================== */
        
        function alleBereicheVerstecken() {
            // Verstecke alle Bereiche
            document.getElementById('startseite').classList.add('hidden');
            document.getElementById('benutzer-auswahl').classList.add('hidden');
            document.getElementById('bestell-bereich').classList.add('hidden');
            document.getElementById('koch-bereich').classList.add('hidden');
            document.getElementById('guthaben-login').classList.add('hidden');
            document.getElementById('guthaben-kategorie').classList.add('hidden');
            document.getElementById('guthaben-personen').classList.add('hidden');
            document.getElementById('preisverwaltung').classList.add('hidden');
        }

        function zurückZurStartseite() {
            // Gehe zurück zur Startseite und setze alles zurück
            alleBereicheVerstecken();
            document.getElementById('startseite').classList.remove('hidden');
            
            // Zustand zurücksetzen
            aktuelleKategorie = null;
            aktuellerBenutzer = null;
            aktuellerGastIndex = null;
            warenkorb = [];
        }

        function zurückZuBenutzerauswahl() {
            // Gehe zurück zur Benutzer-Liste
            alleBereicheVerstecken();
            document.getElementById('benutzer-auswahl').classList.remove('hidden');
            
            // Benutzer abmelden, aber Kategorie behalten
            aktuellerBenutzer = null;
            warenkorb = [];
        }

        /* ========================================
           SORTIERUNG NACH NACHNAMEN
           
           Diese Funktion sortiert Personen
           alphabetisch nach ihrem Nachnamen.
           ======================================== */
        
        function nachNamenSortieren(personen) {
            // Erstelle eine Kopie der Liste
            return [...personen].sort((a, b) => {
                // Platzhalter (leere Gäste) immer ans Ende
                if (a.istPlatzhalter && !b.istPlatzhalter) return 1;
                if (!a.istPlatzhalter && b.istPlatzhalter) return -1;
                if (a.istPlatzhalter && b.istPlatzhalter) return 0;
                
                // Extrahiere Nachname (letztes Wort im Namen)
                const nameA = a.name.split(' ').pop().toLowerCase();
                const nameB = b.name.split(' ').pop().toLowerCase();
                
                // Vergleiche alphabetisch
                return nameA.localeCompare(nameB);
            });
        }

        /* ========================================
           KATEGORIE AUSWÄHLEN (Startseite)
           
           Wird aufgerufen, wenn jemand auf
           "Wachabteilung", "B-Dienst" oder "Gäste"
           klickt.
           ======================================== */
        
        function kategorieAuswaehlen(kategorie) {
            // Merke dir welche Kategorie gewählt wurde
            aktuelleKategorie = kategorie;
            
            // Zeige Benutzer-Auswahl
            alleBereicheVerstecken();
            document.getElementById('benutzer-auswahl').classList.remove('hidden');
            
            // Setze passenden Titel
            const titel = {
                'wachabteilung': 'Wachabteilung',
                'bdienst': 'B-Dienst',
                'gaeste': 'Gäste'
            };
            document.getElementById('kategorie-titel').textContent = titel[kategorie];
            
            // Schulden-Warnung nur bei Wachabteilung anzeigen
            if (kategorie === 'wachabteilung') {
                schuldenWarnungAnzeigen();
            } else {
                document.getElementById('schulden-warnung-box').classList.add('hidden');
            }
            
            // Gast-Eingabe nur bei Gästen anzeigen
            if (kategorie === 'gaeste') {
                document.getElementById('gast-bereich').classList.remove('hidden');
            } else {
                document.getElementById('gast-bereich').classList.add('hidden');
            }
            
            // Zeige die Benutzer-Liste (automatisch sortiert)
            benutzerListeAnzeigen();
        }

        /* ========================================
           SCHULDEN-WARNUNG
           
           Findet die Person mit den höchsten
           Schulden in der Wachabteilung und
           zeigt eine Warnung an.
           ======================================== */
        
        function schuldenWarnungAnzeigen() {
            const warnung = document.getElementById('schulden-warnung-box');
            
            // Finde Person mit niedrigstem Guthaben (= höchste Schulden)
            let maxSchulden = 0;
            let personMitMaxSchulden = null;
            
            benutzer.wachabteilung.forEach(person => {
                if (person.guthaben < maxSchulden) {
                    maxSchulden = person.guthaben;
                    personMitMaxSchulden = person;
                }
            });
            
            // Wenn jemand Schulden hat, zeige Warnung
            if (personMitMaxSchulden) {
                warnung.classList.remove('hidden');
                warnung.innerHTML = `
                    <strong>⚠️ Höchste Schulden:</strong> ${personMitMaxSchulden.name} 
                    (${maxSchulden.toFixed(2)} €)
                `;
            } else {
                warnung.classList.add('hidden');
            }
        }

        /* ========================================
           BENUTZER-LISTE ANZEIGEN
           
           Zeigt alle Personen der gewählten
           Kategorie an - SORTIERT NACH NACHNAMEN!
           ======================================== */
        
        function benutzerListeAnzeigen() {
            const liste = document.getElementById('benutzer-liste');
            liste.innerHTML = ''; // Leere die Liste

            // Hole Personen und sortiere sie nach Nachnamen
            let personenListe = nachNamenSortieren(benutzer[aktuelleKategorie]);

            // Erstelle für jede Person eine Karte
            personenListe.forEach((person) => {
                const karte = document.createElement('div');
                
                if (aktuelleKategorie === 'gaeste' && person.istPlatzhalter) {
                    // LEERER GAST-PLATZHALTER
                    karte.className = 'benutzer-karte platzhalter';
                    karte.innerHTML = `
                        <div class="benutzer-name">Leerer Platz</div>
                        <div class="benutzer-guthaben" style="color: #95a5a6; font-size: 14px;">
                            Unten Name eingeben
                        </div>
                    `;
                    karte.onclick = null; // Nicht klickbar
                } else {
                    // NORMALE PERSON
                    karte.className = 'benutzer-karte';
                    
                    // Finde Original-Index (wichtig fürs Speichern)
                    const originalIndex = benutzer[aktuelleKategorie].indexOf(person);
                    
                    // Klick auf Karte = Person anmelden
                    karte.onclick = () => benutzerAnmelden(person, originalIndex);
                    
                    // Farbe je nach Guthaben (positiv = grün, negativ = rot)
                    const guthabenKlasse = person.guthaben >= 0 ? 'guthaben-positiv' : 'guthaben-negativ';
                    
                    karte.innerHTML = `
                        <div class="benutzer-name">${person.name}</div>
                        <div class="benutzer-guthaben ${guthabenKlasse}">
                            ${person.guthaben.toFixed(2)} €
                        </div>
                    `;
                }
                
                // Füge Karte zur Liste hinzu
                liste.appendChild(karte);
            });
        }

        /* ========================================
           BENUTZER ANMELDEN
           
           Wird aufgerufen wenn jemand auf eine
           Person klickt. Öffnet dann die
           Bestell-Seite.
           ======================================== */
        
        function benutzerAnmelden(benutzer, index) {
            // Merke dir wer angemeldet ist
            aktuellerBenutzer = benutzer;
            if (aktuelleKategorie === 'gaeste') {
                aktuellerGastIndex = index;
            }
            warenkorb = []; // Leere den Warenkorb
            
            // Zeige Bestell-Seite
            alleBereicheVerstecken();
            document.getElementById('bestell-bereich').classList.remove('hidden');
            
            // Zeige Name und Guthaben an
            document.getElementById('aktueller-benutzer').textContent = benutzer.name;
            document.getElementById('guthaben-anzeige').textContent = benutzer.guthaben.toFixed(2) + ' €';
            
            // Zeige Produkte und Warenkorb
            produkteAnzeigen();
            warenkorbAktualisieren();
        }

        /* ========================================
           GAST NAME SETZEN
           
           Wenn ein Gastname eingegeben wird,
           wird der erste leere Platzhalter
           mit diesem Namen gefüllt.
           ======================================== */
        
        function gastNameSetzen() {
            const name = document.getElementById('gast-name-input').value.trim();
            
            // Prüfe ob Name eingegeben wurde
            if (!name) {
                meldungAnzeigen('Bitte einen Namen eingeben!', 'fehler');
                return;
            }

            // Finde ersten leeren Platzhalter
            const index = benutzer.gaeste.findIndex(g => g.istPlatzhalter);
            
            if (index === -1) {
                meldungAnzeigen('Alle 12 Gast-Plätze sind belegt!', 'fehler');
                return;
            }

            // Erstelle neuen Gast
            benutzer.gaeste[index] = {
                name: name,
                guthaben: 0.00,
                istPlatzhalter: false
            };

            datenSpeichern();
            document.getElementById('gast-name-input').value = '';
            
            // Melde Gast direkt an
            benutzerAnmelden(benutzer.gaeste[index], index);
        }

        /* ========================================
           PRODUKTE ANZEIGEN
           
           Zeigt alle Produkte nach Kategorien
           sortiert an.
           ======================================== */
        
        function produkteAnzeigen() {
            const container = document.getElementById('produkte-container');
            container.innerHTML = '';

            // Gehe durch alle Produkt-Kategorien
            produktKategorien.forEach(kategorie => {
                // Erstelle Kategorie-Container
                const katDiv = document.createElement('div');
                katDiv.className = 'produkt-kategorie';
                
                // Überschrift
                const h3 = document.createElement('h3');
                h3.textContent = kategorie.name;
                katDiv.appendChild(h3);
                
                // Produkt-Grid
                const grid = document.createElement('div');
                grid.className = 'produkt-liste';
                
                // Erstelle Karte für jedes Produkt
                kategorie.produkte.forEach(p => {
                    const karte = document.createElement('div');
                    karte.className = 'produkt-karte';
                    
                    karte.innerHTML = `
                        <div class="produkt-name">${p.name}</div>
                        <div class="produkt-preis">${p.preis.toFixed(2)} €</div>
                        <div class="menge-steuerung">
                            <button class="menge-btn" onclick="produktHinzufugen(${p.id})">+</button>
                        </div>
                    `;
                    
                    grid.appendChild(karte);
                });
                
                katDiv.appendChild(grid);
                container.appendChild(katDiv);
            });
        }

        /* ========================================
           WARENKORB-FUNKTIONEN
           
           Produkte zum Warenkorb hinzufügen,
           entfernen und anzeigen.
           ======================================== */
        
        function produktHinzufugen(produktId) {
            // Finde das Produkt in der Produktliste
            const produkt = alleProdukteFlach.find(p => p.id === produktId);
            
            // Prüfe ob Produkt schon im Warenkorb ist
            const vorhandenesItem = warenkorb.find(item => item.id === produktId);
            
            if (vorhandenesItem) {
                // Erhöhe Menge
                vorhandenesItem.menge++;
            } else {
                // Füge neues Produkt hinzu
                warenkorb.push({
                    id: produkt.id,
                    name: produkt.name,
                    preis: produkt.preis,
                    typ: produkt.typ,
                    menge: 1
                });
            }
            
            // Aktualisiere Anzeige
            warenkorbAktualisieren();
        }

        function produktEntfernen(produktId) {
            // Finde das Produkt im Warenkorb
            const item = warenkorb.find(item => item.id === produktId);
            
            if (item) {
                item.menge--;
                // Wenn Menge 0, entferne Produkt komplett
                if (item.menge <= 0) {
                    warenkorb = warenkorb.filter(item => item.id !== produktId);
                }
            }
            
            warenkorbAktualisieren();
        }

        /* ========================================
           INDIVIDUELLER BETRAG
           
           Ermöglicht das Hinzufügen eines
           benutzerdefinierten Betrags.
           ======================================== */
        
        function individuellenBetragHinzufugen() {
            const betrag = parseFloat(document.getElementById('individueller-betrag-input').value);
            const bezeichnung = document.getElementById('individueller-bezeichnung-input').value.trim();
            
            // Prüfe ob Betrag gültig ist
            if (isNaN(betrag) || betrag <= 0) {
                meldungAnzeigen('Bitte einen gültigen Betrag eingeben!', 'fehler');
                return;
            }
            
            // Nutze Bezeichnung oder Standard-Text
            const name = bezeichnung || 'Individueller Betrag';
            
            // Erstelle einzigartige ID (negativ, damit keine Konflikte)
            const neuId = -Date.now();
            
            // Füge zum Warenkorb hinzu
            warenkorb.push({
                id: neuId,
                name: name,
                preis: betrag,
                typ: 'sonstiges',
                menge: 1,
                istIndividuell: true
            });
            
            // Leere Eingabefelder
            document.getElementById('individueller-betrag-input').value = '';
            document.getElementById('individueller-bezeichnung-input').value = '';
            
            warenkorbAktualisieren();
        }

        function warenkorbAktualisieren() {
            const warenkorbDiv = document.getElementById('warenkorb');
            const summeSpan = document.getElementById('summe-anzeige');
            
            // Wenn Warenkorb leer
            if (warenkorb.length === 0) {
                warenkorbDiv.innerHTML = '<p style="color: #95a5a6; text-align: center; padding: 20px;">Warenkorb ist leer</p>';
                summeSpan.textContent = '0.00';
                return;
            }
            
            let html = '';
            let summe = 0;
            
            // Erstelle für jedes Item eine Zeile
            warenkorb.forEach(item => {
                const itemSumme = item.preis * item.menge;
                summe += itemSumme;
                
                html += `
                    <div class="warenkorb-item">
                        <div>
                            <strong>${item.name}</strong><br>
                            ${item.preis.toFixed(2)} € × ${item.menge} = ${itemSumme.toFixed(2)} €
                        </div>
                        <div class="menge-steuerung">
                            <button class="menge-btn" onclick="produktEntfernen(${item.id})">−</button>
                            <span class="menge-anzeige">${item.menge}</span>
                            <button class="menge-btn" onclick="produktHinzufugen(${item.id})">+</button>
                        </div>
                    </div>
                `;
            });
            
            warenkorbDiv.innerHTML = html;
            summeSpan.textContent = summe.toFixed(2);
        }

        /* ========================================
           BESTELLUNG ABSCHLIESSEN
           
           Zieht Guthaben ab und aktualisiert
           die Einkaufsliste.
           ======================================== */
        
        function bestellungAbschliessen() {
            // Prüfe ob Warenkorb leer
            if (warenkorb.length === 0) {
                meldungAnzeigen('Warenkorb ist leer!', 'fehler');
                return;
            }

            // Berechne Gesamtsumme
            const summe = warenkorb.reduce((total, item) => total + (item.preis * item.menge), 0);

            // Ziehe Guthaben ab
            aktuellerBenutzer.guthaben -= summe;

            // Aktualisiere Einkaufsliste (nur für gezählte Produkte)
            warenkorb.forEach(item => {
                if (einkaufsliste.hasOwnProperty(item.typ)) {
                    einkaufsliste[item.typ] += item.menge;
                }
            });

            // Speichere alle Änderungen
            datenSpeichern();

            // Zeige Erfolg-Meldung
            meldungAnzeigen(
                `Bestellung erfolgreich! Summe: ${summe.toFixed(2)} €<br>Neues Guthaben: ${aktuellerBenutzer.guthaben.toFixed(2)} €`,
                'erfolg'
            );

            // Leere Warenkorb
            warenkorb = [];
            warenkorbAktualisieren();
            
            // Aktualisiere Guthaben-Anzeige
            document.getElementById('guthaben-anzeige').textContent = aktuellerBenutzer.guthaben.toFixed(2) + ' €';
        }

        /* ========================================
           KOCH-BEREICH
           
           Zeigt Schulden und Einkaufsliste an.
           KEIN PASSWORT ERFORDERLICH!
           ======================================== */
        
        function kochBereichOeffnen() {
            alleBereicheVerstecken();
            document.getElementById('koch-bereich').classList.remove('hidden');
            
            schuldenBerechnen();
            einkaufslisteAnzeigen();
        }

        function schuldenBerechnen() {
            let gesamt = 0;

            // Summiere alle negativen Guthaben
            for (const [kategorie, personen] of Object.entries(benutzer)) {
                personen.forEach(person => {
                    if (!person.istPlatzhalter && person.guthaben < 0) {
                        gesamt += Math.abs(person.guthaben);
                    }
                });
            }

            document.getElementById('schulden-betrag').textContent = gesamt.toFixed(2) + ' €';
        }

        function einkaufslisteAnzeigen() {
            const anzeige = document.getElementById('einkaufsliste-anzeige');
            
            // Namen für Anzeige
            const namen = {
                'brötchen_normal': 'Brötchen (Normal)',
                'brötchen_mehrkorn': 'Brötchen (Mehrkorn)',
                'brötchen_sunny': 'Brötchen (Sunny)',
                'brötchen_roggen': 'Brötchen (Roggen)',
                'ei': 'Eier',
                'abendessen_normal': 'Abendessen (Normal)',
                'abendessen_vegetarisch': 'Abendessen (Vegetarisch)'
            };

            let html = '';
            let gesamt = 0;

            // Erstelle Zeile für jedes Produkt
            for (const [key, menge] of Object.entries(einkaufsliste)) {
                if (menge > 0) {
                    html += `
                        <div class="einkaufsitem">
                            <span class="einkaufsitem-name">${namen[key]}</span>
                            <span class="einkaufsitem-menge">${menge} Stück</span>
                        </div>
                    `;
                    gesamt += menge;
                }
            }

            // Wenn nichts bestellt wurde
            if (gesamt === 0) {
                html = '<p style="text-align: center; color: #95a5a6;">Noch keine Bestellungen</p>';
            }

            anzeige.innerHTML = html;
        }

        /* ========================================
           TAGESABSCHLUSS
           
           Setzt Einkaufsliste auf 0.
           
           ======================================== */
        
        function tagesabschluss() {
            if (!confirm('Wirklich Tagesabschluss durchführen?\n\n- Einkaufsliste wird auf 0 gesetzt\n- Backup wird heruntergeladen')) {
                return;
            }

            // Erstelle Backup-Objekt
            const backup = {
                datum: new Date().toLocaleString('de-DE'),
                benutzer: benutzer,
                einkaufsliste: {...einkaufsliste}
            };

            // Wandle in Text um
            const jsonString = JSON.stringify(backup, null, 2);
            
            // Erstelle Download für iOS/Edge kompatibel
            const blob = new Blob([jsonString], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            
            const dateiname = 'tagesabschluss-' + new Date().toISOString().split('T')[0] + '.json';
            
            // Versuche Download mit mehreren Methoden (für iOS/Edge)
            const a = document.createElement('a');
            a.href = url;
            a.download = dateiname;
            a.style.display = 'none';
            document.body.appendChild(a);
            
            // iOS Safari braucht einen Klick-Event
            try {
                a.click();
                
                // Aufräumen nach kurzer Verzögerung
                setTimeout(() => {
                    document.body.removeChild(a);
                    URL.revokeObjectURL(url);
                }, 100);
            } catch (error) {
                // Fallback: Zeige den JSON-Text zum Kopieren
                alert('Download fehlgeschlagen. Kopiere den folgenden Text und speichere ihn manuell:\n\n' + jsonString.substring(0, 200) + '...');
                console.log('Backup-Daten:', jsonString);
            }

            // Setze Einkaufsliste zurück
            einkaufsliste = {
                brötchen_normal: 0,
                brötchen_mehrkorn: 0,
                brötchen_sunny: 0,
                brötchen_roggen: 0,
                ei: 0,
                abendessen_normal: 0,
                abendessen_vegetarisch: 0
            };

            datenSpeichern();
            einkaufslisteAnzeigen();

            meldungAnzeigen('Tagesabschluss durchgeführt! Einkaufsliste auf 0 gesetzt. Backup-Datei sollte heruntergeladen worden sein.', 'erfolg');
        }

        /* ========================================
           GUTHABEN-VERWALTUNG
           
           MIT PASSWORT GESCHÜTZT!
           Hier können Guthaben aufgeladen werden.
           ======================================== */
        
        function guthabenVerwaltungLoginOeffnen() {
            alleBereicheVerstecken();
            document.getElementById('guthaben-login').classList.remove('hidden');
        }

        function guthabenVerwaltungLogin() {
            const passwort = document.getElementById('admin-passwort').value;
            
            // Prüfe Passwort
            if (passwort === ADMIN_PASSWORT) {
                alleBereicheVerstecken();
                document.getElementById('guthaben-kategorie').classList.remove('hidden');
                
                meldungAnzeigen('Erfolgreich angemeldet', 'erfolg');
            } else {
                meldungAnzeigen('Falsches Passwort!', 'fehler');
            }
            
            document.getElementById('admin-passwort').value = '';
        }

        function guthabenVerwaltungAbmelden() {
            zurückZurStartseite();
        }

        function guthabenKategorieAuswaehlen(kategorie) {
            guthabenVerwaltungKategorie = kategorie;
            alleBereicheVerstecken();
            document.getElementById('guthaben-personen').classList.remove('hidden');
            
            const titel = {
                'wachabteilung': 'Wachabteilung - Guthaben verwalten',
                'bdienst': 'B-Dienst - Guthaben verwalten',
                'gaeste': 'Gäste - Guthaben verwalten'
            };
            document.getElementById('guthaben-kategorie-titel').textContent = titel[kategorie];
            
            guthabenPersonenAnzeigen();
        }

        function zurückZuGuthabenKategorie() {
            alleBereicheVerstecken();
            document.getElementById('guthaben-kategorie').classList.remove('hidden');
        }

        function guthabenPersonenAnzeigen() {
            const liste = document.getElementById('guthaben-personen-liste');
            liste.innerHTML = '';

            // Sortiere nach Namen
            const sortiertePersonen = nachNamenSortieren(benutzer[guthabenVerwaltungKategorie]);

            sortiertePersonen.forEach((person) => {
                // Finde Original-Index
                const index = benutzer[guthabenVerwaltungKategorie].indexOf(person);
                
                if (person.istPlatzhalter) {
                    // Leerer Platzhalter
                    const karte = document.createElement('div');
                    karte.className = 'guthaben-verwaltung-karte';
                    karte.style.opacity = '0.5';
                    karte.innerHTML = `
                        <h3>Leerer Gast-Platz</h3>
                        <p style="color: #95a5a6; font-size: 14px;">Kein Gast hinterlegt</p>
                    `;
                    liste.appendChild(karte);
                } else {
                    // Person mit Guthaben-Verwaltung
                    const karte = document.createElement('div');
                    karte.className = 'guthaben-verwaltung-karte';
                    
                    const guthabenKlasse = person.guthaben >= 0 ? 'guthaben-positiv' : 'guthaben-negativ';
                    
                    let html = `
                        <h3>${person.name}</h3>
                        <div style="font-size: 20px; margin: 10px 0;" class="${guthabenKlasse}">
                            Aktuell: ${person.guthaben.toFixed(2)} €
                        </div>
                        <div class="guthaben-eingabe">
                            <input type="number" id="betrag-${index}" placeholder="Betrag (z.B. 20.00)" step="0.01">
                            <button class="success" onclick="guthabenErhoehen('${guthabenVerwaltungKategorie}', ${index})">
                                Aufladen
                            </button>
                        </div>
                    `;
                    
                    // Bei Gästen: Löschen-Button
                    if (guthabenVerwaltungKategorie === 'gaeste') {
                        html += `
                            <button class="danger" onclick="gastLoeschen(${index})" style="width: 100%; margin-top: 10px; padding: 10px; font-size: 14px;">
                                Gast löschen
                            </button>
                        `;
                    }
                    
                    karte.innerHTML = html;
                    liste.appendChild(karte);
                }
            });
        }

        function guthabenErhoehen(kategorie, index) {
            const betragInput = document.getElementById('betrag-' + index);
            const betrag = parseFloat(betragInput.value);

            if (isNaN(betrag) || betrag <= 0) {
                meldungAnzeigen('Bitte einen gültigen positiven Betrag eingeben!', 'fehler');
                return;
            }

            // Erhöhe Guthaben
            benutzer[kategorie][index].guthaben += betrag;
            datenSpeichern();
            
            betragInput.value = '';
            guthabenPersonenAnzeigen();
            
            meldungAnzeigen(`${betrag.toFixed(2)} € wurden aufgeladen!`, 'erfolg');
        }

        function gastLoeschen(index) {
            const gast = benutzer.gaeste[index];
            
            if (confirm(`Wirklich Gast "${gast.name}" löschen?\n\nWird zu leerem Platzhalter.`)) {
                // Mache Platz wieder leer
                benutzer.gaeste[index] = {
                    name: "",
                    guthaben: 0.00,
                    istPlatzhalter: true
                };
                
                datenSpeichern();
                guthabenPersonenAnzeigen();
                
                meldungAnzeigen('Gast wurde gelöscht!', 'erfolg');
            }
        }

        /* ========================================
           PREISVERWALTUNG
           
           Zeigt alle Produkte nach Kategorien
           und ermöglicht Preis-Änderungen.
           ======================================== */
        
        function preisverwaltungOeffnen() {
            // Öffne Preisverwaltungs-Seite
            alleBereicheVerstecken();
            document.getElementById('preisverwaltung').classList.remove('hidden');
            
            // Zeige alle Preise an
            preiseAnzeigen();
        }
        
        function preiseAnzeigen() {
            const liste = document.getElementById('preisverwaltung-liste');
            liste.innerHTML = '';

            // Gehe durch alle Produkt-Kategorien
            produktKategorien.forEach(kategorie => {
                // Erstelle Kategorie-Container
                const katDiv = document.createElement('div');
                katDiv.className = 'preis-kategorie';
                
                // Überschrift
                const h3 = document.createElement('h3');
                h3.textContent = kategorie.name;
                katDiv.appendChild(h3);
                
                // Produkt-Grid
                const grid = document.createElement('div');
                grid.className = 'preis-grid';
                
                // Erstelle Karte für jedes Produkt
                kategorie.produkte.forEach(produkt => {
                    const item = document.createElement('div');
                    item.className = 'preis-item';
                    
                    item.innerHTML = `
                        <div class="preis-item-name">${produkt.name}</div>
                        <div class="preis-item-aktuell">
                            Aktuell: <strong>${produkt.preis.toFixed(2)} €</strong>
                        </div>
                        <div class="preis-eingabe">
                            <input 
                                type="number" 
                                id="preis-${produkt.id}" 
                                placeholder="Neuer Preis" 
                                step="0.01"
                                value="${produkt.preis.toFixed(2)}"
                            >
                            <button onclick="preisAendern(${produkt.id})">
                                ✓
                            </button>
                        </div>
                    `;
                    
                    grid.appendChild(item);
                });
                
                katDiv.appendChild(grid);
                liste.appendChild(katDiv);
            });
        }

        function preisAendern(produktId) {
            // Hole neuen Preis aus Eingabefeld
            const neuerPreis = parseFloat(document.getElementById('preis-' + produktId).value);
            
            // Validierung
            if (isNaN(neuerPreis) || neuerPreis < 0) {
                meldungAnzeigen('Bitte einen gültigen Preis eingeben!', 'fehler');
                return;
            }

            // Finde Produkt in allen Kategorien
            let gefunden = false;
            produktKategorien.forEach(kategorie => {
                const produkt = kategorie.produkte.find(p => p.id === produktId);
                if (produkt) {
                    const alterPreis = produkt.preis;
                    produkt.preis = neuerPreis;
                    gefunden = true;
                    
                    // Erfolg-Meldung
                    meldungAnzeigen(
                        `Preis für "${produkt.name}" wurde von ${alterPreis.toFixed(2)} € auf ${neuerPreis.toFixed(2)} € geändert!`,
                        'erfolg'
                    );
                }
            });

            if (gefunden) {
                // Aktualisiere flache Produktliste
                alleProdukteFlach = [];
                produktKategorien.forEach(kategorie => {
                    alleProdukteFlach = alleProdukteFlach.concat(kategorie.produkte);
                });
                
                // Speichere Änderungen
                datenSpeichern();
                
                // Aktualisiere Anzeige
                preiseAnzeigen();
            }
        }

        /* ========================================
           MELDUNGEN ANZEIGEN
           
           Zeigt Erfolgs- oder Fehler-Meldungen
           für 5 Sekunden an.
           ======================================== */
        
        function meldungAnzeigen(text, typ) {
            const meldungDiv = document.getElementById('meldung');
            meldungDiv.className = 'meldung ' + typ;
            meldungDiv.innerHTML = text;
            meldungDiv.style.display = 'block';
            
            // Verstecke nach 5 Sekunden
            setTimeout(() => {
                meldungDiv.style.display = 'none';
            }, 5000);
        }

        /* ========================================
           APP START
           
           Wird aufgerufen wenn die Seite geladen
           wird. Lädt gespeicherte Daten.
           ======================================== */
        
        window.onload = function() {
            datenLaden();
            console.log('🍽️ Kantinen-App gestartet!');
            console.log('📝 Tipp: Öffne die Browser-Konsole (F12) um Code-Hinweise zu sehen');
        };
    </script>
    

</body>
</html>
