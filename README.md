<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculateur MPI · MI · PI</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* ===== STYLES COMPLETS ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            transition: background-color 0.3s, color 0.3s, border-color 0.3s;
        }

        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }

        body.dark-mode {
            background: linear-gradient(135deg, #2c3e50 0%, #1a252f 100%);
            color: #ecf0f1;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
        }

        /* Header avec signature intégrée */
        header {
            text-align: center;
            padding: 30px 0 20px;
            position: relative;
        }

        h1 {
            color: #2c3e50;
            font-size: 2.5rem;
            margin-bottom: 10px;
            margin-top: 20px;
        }

        .dark-mode h1 {
            color: #ecf0f1;
        }

        .subtitle {
            color: #7f8c8d;
            font-size: 1.2rem;
            margin-bottom: 30px;
        }

        .dark-mode .subtitle {
            color: #bdc3c7;
        }

        /* Bouton mode sombre - version améliorée */
        .theme-toggle {
            position: absolute;
            top: 20px;
            left: 20px;
            background: white;
            border: 2px solid #3498db;
            border-radius: 50px;
            padding: 12px 25px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            gap: 10px;
            z-index: 100;
            color: #2c3e50;
        }

        .dark-mode .theme-toggle {
            background: #34495e;
            border-color: #9b59b6;
            color: #ecf0f1;
            box-shadow: 0 5px 15px rgba(155, 89, 182, 0.3);
        }

        .theme-toggle i {
            color: #3498db;
            font-size: 1.2rem;
        }

        .dark-mode .theme-toggle i {
            color: #9b59b6;
        }

        .theme-toggle:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(52, 152, 219, 0.3);
        }

        .dark-mode .theme-toggle:hover {
            box-shadow: 0 8px 20px rgba(155, 89, 182, 0.3);
        }

        /* Signature container - version desktop */
        .signature-container {
            background: rgba(255, 255, 255, 0.95);
            padding: 25px 30px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.15);
            border: 1px solid rgba(52, 152, 219, 0.2);
            backdrop-filter: blur(10px);
            margin: 0 auto 40px auto;
            max-width: 800px;
            width: 100%;
            position: relative;
        }

        .dark-mode .signature-container {
            background: rgba(44, 62, 80, 0.98);
            border-color: rgba(155, 89, 182, 0.3);
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
        }

        .signature-flex {
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 20px;
        }

        .signature-left {
            flex: 1;
            min-width: 250px;
            text-align: left;
        }

        .signature-right {
            flex: 1;
            min-width: 300px;
        }

        .developer-badge {
            background: linear-gradient(45deg, #3498db, #2c3e50);
            color: white;
            padding: 6px 15px;
            border-radius: 25px;
            font-size: 0.85rem;
            font-weight: 600;
            letter-spacing: 0.5px;
            display: inline-block;
            box-shadow: 0 4px 10px rgba(52, 152, 219, 0.2);
            margin-bottom: 10px;
        }

        .dark-mode .developer-badge {
            background: linear-gradient(45deg, #9b59b6, #34495e);
        }

        .signature {
            font-family: 'Brush Script MT', cursive;
            font-size: 2.8rem;
            font-weight: bold;
            background: linear-gradient(135deg, #3498db, #2c3e50);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
            margin: 0;
        }

        .dark-mode .signature {
            background: linear-gradient(135deg, #9b59b6, #ecf0f1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 8px 12px;
            background: rgba(52, 152, 219, 0.05);
            border-radius: 12px;
            transition: all 0.3s;
        }

        .dark-mode .contact-item {
            background: rgba(155, 89, 182, 0.1);
        }

        .contact-item:hover {
            background: rgba(52, 152, 219, 0.1);
            transform: translateX(5px);
        }

        .dark-mode .contact-item:hover {
            background: rgba(155, 89, 182, 0.2);
        }

        .contact-item i {
            color: #3498db;
            font-size: 1.2rem;
            width: 24px;
            text-align: center;
        }

        .dark-mode .contact-item i {
            color: #9b59b6;
        }

        .contact-link {
            color: #2c3e50;
            text-decoration: none;
            font-weight: 500;
            font-size: 1rem;
        }

        .dark-mode .contact-link {
            color: #ecf0f1;
        }

        .signature-divider {
            height: 2px;
            background: linear-gradient(90deg, transparent, #3498db, #9b59b6, #3498db, transparent);
            margin-top: 15px;
        }

        /* Navigation par filières */
        .filiere-tabs {
            display: flex;
            justify-content: center;
            margin: 40px 0 30px;
            gap: 15px;
            flex-wrap: wrap;
        }

        .filiere-tab {
            padding: 15px 40px;
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s;
            color: #7f8c8d;
        }

        .dark-mode .filiere-tab {
            background: #2c3e50;
            border-color: #34495e;
            color: #bdc3c7;
        }

        .filiere-tab.active {
            background: #3498db;
            color: white;
            border-color: #3498db;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        .dark-mode .filiere-tab.active {
            background: #9b59b6;
            border-color: #9b59b6;
            box-shadow: 0 5px 15px rgba(155, 89, 182, 0.3);
        }

        .filiere-content {
            display: none;
        }

        .filiere-content.active {
            display: block;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Sous-onglets semestres */
        .semester-tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 30px;
            gap: 10px;
            flex-wrap: wrap;
        }

        .semester-tab {
            padding: 12px 25px;
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            color: #7f8c8d;
        }

        .dark-mode .semester-tab {
            background: #2c3e50;
            border-color: #34495e;
            color: #bdc3c7;
        }

        .semester-tab.active {
            background: #3498db;
            color: white;
            border-color: #3498db;
        }

        .dark-mode .semester-tab.active {
            background: #9b59b6;
            border-color: #9b59b6;
        }

        .semester-content {
            display: none;
        }

        .semester-content.active {
            display: block;
        }

        .info-box {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            border-left: 5px solid #3498db;
        }

        .dark-mode .info-box {
            background: #34495e;
            border-left-color: #9b59b6;
        }

        .calculator-container {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }

        .matieres-section {
            flex: 2;
            min-width: 300px;
        }

        .results-section {
            flex: 1;
            min-width: 300px;
        }

        .matiere-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: transform 0.3s;
        }

        .dark-mode .matiere-card {
            background: #2c3e50;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .matiere-card:hover {
            transform: translateY(-5px);
        }

        .matiere-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .dark-mode .matiere-header {
            border-bottom-color: #34495e;
        }

        .matiere-name {
            font-weight: 600;
            color: #2c3e50;
            font-size: 1.1rem;
        }

        .dark-mode .matiere-name {
            color: #ecf0f1;
        }

        .coefficient {
            background: #3498db;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.9rem;
        }

        .dark-mode .coefficient {
            background: #9b59b6;
        }

        .input-group {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .input-field {
            flex: 1;
            min-width: 120px;
        }

        .input-field label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
            color: #555;
        }

        .dark-mode .input-field label {
            color: #bdc3c7;
        }

        .input-field input {
            width: 100%;
            padding: 10px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            background: white;
        }

        .dark-mode .input-field input {
            background: #34495e;
            border-color: #2c3e50;
            color: white;
        }

        .input-field input:focus {
            outline: none;
            border-color: #3498db;
        }

        .input-field input.invalid {
            border-color: #e74c3c;
            background-color: #fadbd8;
        }

        .dark-mode .input-field input.invalid {
            border-color: #e74c3c;
            background-color: #5a2e2a;
        }

        .tp-hint {
            font-size: 0.8rem;
            color: #7f8c8d;
            margin-top: 3px;
            font-style: italic;
        }

        .matiere-result {
            text-align: right;
            margin-top: 15px;
            padding-top: 10px;
            border-top: 1px dashed #ddd;
            font-size: 1.2rem;
            font-weight: 600;
        }

        .dark-mode .matiere-result {
            border-top-color: #34495e;
        }

        .result-card {
            background: white;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            position: sticky;
            top: 20px;
        }

        .dark-mode .result-card {
            background: #34495e;
        }

        .result-card h2 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 20px;
        }

        .dark-mode .result-card h2 {
            color: #ecf0f1;
        }

        .result-value {
            text-align: center;
            font-size: 3.5rem;
            font-weight: 800;
            color: #3498db;
            margin: 20px 0;
        }

        .dark-mode .result-value {
            color: #9b59b6;
        }

        .result-message {
            text-align: center;
            font-size: 1.2rem;
            color: #7f8c8d;
            margin-bottom: 20px;
        }

        .controls {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }

        button {
            padding: 14px 20px;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            flex: 1;
            background: #3498db;
            color: white;
        }

        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        .reset-btn {
            background: #e74c3c;
        }

        .reset-btn:hover {
            background: #c0392b;
        }

        .validation-message {
            padding: 10px;
            border-radius: 6px;
            margin-top: 15px;
            display: none;
        }

        .validation-message.error {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
            display: block;
        }

        .validation-message.success {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
            display: block;
        }

        .score-section {
            background: white;
            border-radius: 12px;
            padding: 30px;
            margin-top: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            border-top: 5px solid #2ecc71;
        }

        .dark-mode .score-section {
            background: #34495e;
            border-top-color: #f1c40f;
        }

        .score-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .score-card {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .dark-mode .score-card {
            background: #2c3e50;
        }

        .score-type {
            font-weight: 600;
            color: #7f8c8d;
            margin-bottom: 10px;
            font-size: 1.2rem;
        }

        .score-value {
            font-size: 2.5rem;
            font-weight: 800;
            color: #2ecc71;
            margin: 10px 0;
        }

        .dark-mode .score-value {
            color: #f1c40f;
        }

        .detail-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px dashed #ddd;
        }

        .dark-mode .detail-item {
            border-bottom-color: #34495e;
        }

        .bonus-section {
            background: #fff8e1;
            padding: 15px;
            border-radius: 8px;
            margin: 20px 0;
        }

        .dark-mode .bonus-section {
            background: #2c3e50;
            border: 1px solid #f39c12;
        }

        .bonus-label {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
        }

        footer {
            text-align: center;
            padding: 20px;
            color: #7f8c8d;
            margin-top: 30px;
            border-top: 1px solid #e0e0e0;
        }

        .dark-mode footer {
            border-top-color: #34495e;
            color: #bdc3c7;
        }

        .footer-signature {
            font-family: 'Brush Script MT', cursive;
            font-size: 2rem;
            color: #2c3e50;
            margin: 10px 0;
        }

        .dark-mode .footer-signature {
            color: #ecf0f1;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .theme-toggle {
                position: static;
                margin: 10px auto;
            }
            
            .signature-flex {
                flex-direction: column;
                text-align: center;
            }
            
            .signature-left, .signature-right {
                text-align: center;
            }
            
            .signature {
                text-align: center;
                font-size: 2.2rem;
            }
            
            .contact-item {
                justify-content: center;
            }
            
            .calculator-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <!-- Bouton mode sombre amélioré -->
            <button class="theme-toggle" id="themeToggle">
                <i class="fas fa-moon"></i> 
                <span id="themeText">Mode sombre</span>
            </button>

            <!-- Signature redesign pour ordinateur -->
            <div class="signature-container">
                <div class="signature-flex">
                    <div class="signature-left">
                        <div class="developer-badge">
                            <i class="fas fa-code"></i> DÉVELOPPÉ PAR
                        </div>
                        <div class="signature">AHMED MDINI</div>
                    </div>
                    
                    <div class="signature-right">
                        <div class="contact-info">
                            <div class="contact-item">
                                <i class="fas fa-phone-alt"></i>
                                <a href="tel:+21629700626" class="contact-link">+216 29 700 626</a>
                            </div>
                            <div class="contact-item">
                                <i class="fas fa-envelope"></i>
                                <a href="mailto:ahmed.medenii@gmail.com" class="contact-link">ahmed.medenii@gmail.com</a>
                            </div>
                            <div class="contact-item">
                                <i class="fas fa-map-marker-alt"></i>
                                <span class="contact-link">Tunisie</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="signature-divider"></div>
            </div>
            
            <h1><i class="fas fa-graduation-cap"></i> Calculateur d'orientation</h1>
            <p class="subtitle">MPI · MI · PI — Moyennes et scores d'accès</p>
        </header>

        <!-- Filières principales -->
        <div class="filiere-tabs">
            <div class="filiere-tab active" data-filiere="mpi">MPI (1ʳᵉ année)</div>
            <div class="filiere-tab" data-filiere="mi">MI (2ᵉ année)</div>
            <div class="filiere-tab" data-filiere="pi">PI (2ᵉ année)</div>
        </div>

        <!-- Contenu MPI -->
        <div id="mpi-content" class="filiere-content active">
            <div class="semester-tabs">
                <div class="semester-tab active" data-semester="s1">Semestre 1</div>
                <div class="semester-tab" data-semester="s2">Semestre 2</div>
                <div class="semester-tab" data-semester="annual">Moyenne annuelle</div>
                <div class="semester-tab" data-semester="scores">Scores d'orientation</div>
            </div>
            <div id="mpi-s1" class="semester-content active">
                <div class="calculator-container">
                    <div class="matieres-section" id="mpi-matieres-s1"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 1</h2>
                            <div class="result-value" id="mpi-moyenne-s1">0.00</div>
                            <div class="result-message" id="mpi-message-s1">Entrez les notes</div>
                            <div class="validation-message" id="mpi-validation-s1"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="mpi" data-semestre="s1">Calculer S1</button>
                                <button class="reset-btn" data-filiere="mpi" data-semestre="s1">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="mpi-s2" class="semester-content">
                <div class="calculator-container">
                    <div class="matieres-section" id="mpi-matieres-s2"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 2</h2>
                            <div class="result-value" id="mpi-moyenne-s2">0.00</div>
                            <div class="result-message" id="mpi-message-s2">Entrez les notes</div>
                            <div class="validation-message" id="mpi-validation-s2"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="mpi" data-semestre="s2">Calculer S2</button>
                                <button class="reset-btn" data-filiere="mpi" data-semestre="s2">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="mpi-annual" class="semester-content">
                <div class="info-box">
                    <h3>Moyenne annuelle</h3>
                    <p>Basée sur les semestres 1 et 2.</p>
                </div>
                <div class="result-card">
                    <h2>Moyenne annuelle</h2>
                    <div class="result-value" id="mpi-moyenne-annuelle">0.00</div>
                    <div class="result-message" id="mpi-message-annuel">Calculez d'abord les deux semestres</div>
                    <div class="validation-message" id="mpi-validation-annuel"></div>
                    <button id="mpi-calc-annuel">Calculer la moyenne annuelle</button>
                </div>
            </div>
            <div id="mpi-scores" class="semester-content">
                <div class="score-section">
                    <h2>Scores d'orientation (fin de 1ʳᵉ année)</h2>
                    <div class="bonus-section">
                        <div class="bonus-label">
                            <input type="checkbox" id="mpi-bonus" class="bonus-checkbox">
                            <label for="mpi-bonus">Bonus session principale (0.5 point)</label>
                        </div>
                    </div>
                    <div class="score-grid">
                        <div class="score-card">
                            <div class="score-type">Score MI</div>
                            <div class="score-value" id="mpi-score-mi">0.00</div>
                            <div class="detail-item" id="mpi-detail-mi"></div>
                        </div>
                        <div class="score-card">
                            <div class="score-type">Score PI</div>
                            <div class="score-value" id="mpi-score-pi">0.00</div>
                            <div class="detail-item" id="mpi-detail-pi"></div>
                        </div>
                    </div>
                    <div class="validation-message" id="mpi-validation-scores"></div>
                    <button id="mpi-calc-scores">Calculer les scores</button>
                </div>
            </div>
        </div>

        <!-- Contenu MI -->
        <div id="mi-content" class="filiere-content">
            <div class="semester-tabs">
                <div class="semester-tab active" data-semester="s3">Semestre 3</div>
                <div class="semester-tab" data-semester="s4">Semestre 4</div>
                <div class="semester-tab" data-semester="annual">Moyenne 2A</div>
                <div class="semester-tab" data-semester="scores">Scores spécialités</div>
            </div>
            <div id="mi-s3" class="semester-content active">
                <div class="calculator-container">
                    <div class="matieres-section" id="mi-matieres-s3"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 3</h2>
                            <div class="result-value" id="mi-moyenne-s3">0.00</div>
                            <div class="result-message" id="mi-message-s3">Entrez les notes</div>
                            <div class="validation-message" id="mi-validation-s3"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="mi" data-semestre="s3">Calculer S3</button>
                                <button class="reset-btn" data-filiere="mi" data-semestre="s3">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="mi-s4" class="semester-content">
                <div class="calculator-container">
                    <div class="matieres-section" id="mi-matieres-s4"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 4</h2>
                            <div class="result-value" id="mi-moyenne-s4">0.00</div>
                            <div class="result-message" id="mi-message-s4">Entrez les notes</div>
                            <div class="validation-message" id="mi-validation-s4"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="mi" data-semestre="s4">Calculer S4</button>
                                <button class="reset-btn" data-filiere="mi" data-semestre="s4">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="mi-annual" class="semester-content">
                <div class="result-card">
                    <h2>Moyenne de 2ème année (MI)</h2>
                    <div class="result-value" id="mi-moyenne-2a">0.00</div>
                    <div class="validation-message" id="mi-validation-annuel"></div>
                    <button id="mi-calc-annuel">Calculer la moyenne 2A</button>
                </div>
            </div>
            <div id="mi-scores" class="semester-content">
                <div class="score-section">
                    <h2>Scores d'accès aux spécialités MI</h2>
                    <div class="bonus-section">
                        <div class="bonus-label">
                            <input type="checkbox" id="mi-bonus" class="bonus-checkbox">
                            <label for="mi-bonus">Bonus session principale (0.5)</label>
                        </div>
                        <div class="bonus-label" style="margin-top:10px;">
                            <input type="checkbox" id="mi-malus" class="bonus-checkbox">
                            <label for="mi-malus">Malus redoublement 2A (-1 point)</label>
                        </div>
                    </div>
                    <div class="score-grid">
                        <div class="score-card">
                            <div class="score-type">GL & SI</div>
                            <div class="score-value" id="mi-score-glsi">0.00</div>
                        </div>
                        <div class="score-card">
                            <div class="score-type">Data Science</div>
                            <div class="score-value" id="mi-score-ds">0.00</div>
                        </div>
                        <div class="score-card">
                            <div class="score-type">ISI</div>
                            <div class="score-value" id="mi-score-isi">0.00</div>
                        </div>
                    </div>
                    <div class="validation-message" id="mi-validation-scores"></div>
                    <button id="mi-calc-scores">Calculer les scores MI</button>
                </div>
            </div>
        </div>

        <!-- Contenu PI -->
        <div id="pi-content" class="filiere-content">
            <div class="semester-tabs">
                <div class="semester-tab active" data-semester="s3">Semestre 3</div>
                <div class="semester-tab" data-semester="s4">Semestre 4</div>
                <div class="semester-tab" data-semester="annual">Moyenne 2A</div>
                <div class="semester-tab" data-semester="scores">Scores spécialités</div>
            </div>
            <div id="pi-s3" class="semester-content active">
                <div class="calculator-container">
                    <div class="matieres-section" id="pi-matieres-s3"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 3</h2>
                            <div class="result-value" id="pi-moyenne-s3">0.00</div>
                            <div class="result-message" id="pi-message-s3">Entrez les notes</div>
                            <div class="validation-message" id="pi-validation-s3"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="pi" data-semestre="s3">Calculer S3</button>
                                <button class="reset-btn" data-filiere="pi" data-semestre="s3">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="pi-s4" class="semester-content">
                <div class="calculator-container">
                    <div class="matieres-section" id="pi-matieres-s4"></div>
                    <div class="results-section">
                        <div class="result-card">
                            <h2>Résultat Semestre 4</h2>
                            <div class="result-value" id="pi-moyenne-s4">0.00</div>
                            <div class="result-message" id="pi-message-s4">Entrez les notes</div>
                            <div class="validation-message" id="pi-validation-s4"></div>
                            <div class="controls">
                                <button class="calculate-btn" data-filiere="pi" data-semestre="s4">Calculer S4</button>
                                <button class="reset-btn" data-filiere="pi" data-semestre="s4">Réinitialiser</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="pi-annual" class="semester-content">
                <div class="result-card">
                    <h2>Moyenne de 2ème année (PI)</h2>
                    <div class="result-value" id="pi-moyenne-2a">0.00</div>
                    <div class="validation-message" id="pi-validation-annuel"></div>
                    <button id="pi-calc-annuel">Calculer la moyenne 2A</button>
                </div>
            </div>
            <div id="pi-scores" class="semester-content">
                <div class="score-section">
                    <h2>Scores d'accès aux spécialités PI</h2>
                    <div class="bonus-section">
                        <div class="bonus-label">
                            <input type="checkbox" id="pi-bonus" class="bonus-checkbox">
                            <label for="pi-bonus">Bonus session principale (0.5)</label>
                        </div>
                        <div class="bonus-label" style="margin-top:10px;">
                            <input type="checkbox" id="pi-malus" class="bonus-checkbox">
                            <label for="pi-malus">Malus redoublement 2A (-1 point)</label>
                        </div>
                    </div>
                    <div class="score-grid">
                        <div class="score-card">
                            <div class="score-type">EE (Électronique Embarquée)</div>
                            <div class="score-value" id="pi-score-ee">0.00</div>
                        </div>
                        <div class="score-card">
                            <div class="score-type">GP & MN</div>
                            <div class="score-value" id="pi-score-gpmn">0.00</div>
                        </div>
                    </div>
                    <div class="validation-message" id="pi-validation-scores"></div>
                    <button id="pi-calc-scores">Calculer les scores PI</button>
                </div>
            </div>
        </div>

        <footer>
            <div class="footer-signature">
                <i class="fas fa-code"></i> AHMED MDINI <i class="fas fa-laptop-code"></i>
            </div>
            <p>Calculateur intégré des parcours MPI · MI · PI — Conforme aux textes officiels</p>
            <p>© 2025 Tous droits réservés</p>
        </footer>
    </div>

    <script>
        // ======================== DONNÉES DES MATIÈRES ========================
        const matieresData = {
            mpi: {
                s1: [
                    { nom: "Algèbre 1", coef: 2, code: "alg1" },
                    { nom: "Analyse 1", coef: 2, code: "ana1" },
                    { nom: "Algorithmique 1", coef: 1.5, code: "algo1" },
                    { nom: "Programmation 1", coef: 1.5, code: "prog1" },
                    { nom: "Français 1", coef: 1, code: "fr1" },
                    { nom: "Anglais 1", coef: 1, code: "ang1" },
                    { nom: "Mécanique", coef: 1.5, code: "mec" },
                    { nom: "Circuit Électrique", coef: 1.5, code: "circuit" },
                    { nom: "Électrostatique", coef: 1.5, code: "electro" },
                    { nom: "Optique", coef: 1.5, code: "optique" }
                ],
                s2: [
                    { nom: "Algèbre 2", coef: 2, code: "alg2" },
                    { nom: "Analyse 2", coef: 2, code: "ana2" },
                    { nom: "Algorithmique 2", coef: 1.5, code: "algo2" },
                    { nom: "Programmation 2", coef: 1, code: "prog2" },
                    { nom: "Français 2", coef: 1, code: "fr2" },
                    { nom: "Anglais 2", coef: 1, code: "ang2" },
                    { nom: "Culture & Comp. Num.", coef: 1, code: "ccn" },
                    { nom: "Mécanique Quantique", coef: 1, code: "mec_quant" },
                    { nom: "Électronique", coef: 1, code: "electronique" },
                    { nom: "Magnétostatique", coef: 1.5, code: "magnetostatique" },
                    { nom: "Système Logique", coef: 2, code: "sl" }
                ]
            },
            mi: {
                s3: [
                    { nom: "Algèbre 3", coef: 1.5, code: "alg3" },
                    { nom: "Analyse 3", coef: 1.5, code: "ana3" },
                    { nom: "Traitement du signal", coef: 2, code: "signal" },
                    { nom: "Architecture Ordinateurs", coef: 1.5, code: "archi" },
                    { nom: "Systèmes d'exploitation 1", coef: 1.5, code: "se1" },
                    { nom: "POO", coef: 1, code: "poo" },
                    { nom: "Atelier C++", coef: 1.5, code: "cpp" },
                    { nom: "Développement Web", coef: 1, code: "web" },
                    { nom: "BDD Fondamentaux", coef: 1, code: "bdd1" },
                    { nom: "Logique formelle", coef: 1, code: "logique" },
                    { nom: "Anglais 3", coef: 1, code: "ang3" }
                ],
                s4: [
                    { nom: "Probabilités & Stats", coef: 2, code: "proba" },
                    { nom: "Théorie des langages", coef: 2, code: "langages" },
                    { nom: "Atelier Java", coef: 1, code: "java" },
                    { nom: "Programmation Python", coef: 1, code: "python" },
                    { nom: "Ingénierie des BDD", coef: 1.5, code: "bdd2" },
                    { nom: "Conception SI", coef: 1.5, code: "csi" },
                    { nom: "Transmission données", coef: 1, code: "trans" },
                    { nom: "Réseaux locaux", coef: 1.5, code: "reseau" },
                    { nom: "Systèmes d'exploitation 2", coef: 1.5, code: "se2" },
                    { nom: "Anglais 4", coef: 1, code: "ang4" },
                    { nom: "Français 4", coef: 1, code: "fr4" }
                ]
            },
            pi: {
                s3: [
                    { nom: "Algèbre 3", coef: 1.5, code: "alg3" },
                    { nom: "Analyse 3", coef: 1.5, code: "ana3" },
                    { nom: "Traitement du signal", coef: 2, code: "signal" },
                    { nom: "Architecture Ordinateurs", coef: 1.5, code: "archi" },
                    { nom: "Systèmes d'exploitation 1", coef: 1.5, code: "se1" },
                    { nom: "POO", coef: 1, code: "poo" },
                    { nom: "Atelier C++", coef: 1.5, code: "cpp" },
                    { nom: "Électronique analogique", coef: 1.5, code: "elec_ana" },
                    { nom: "Physique quantique 2", coef: 1.5, code: "phys_quant2" },
                    { nom: "Anglais 3", coef: 1, code: "ang3" }
                ],
                s4: [
                    { nom: "Probabilités & Stats", coef: 2, code: "proba" },
                    { nom: "Théorie des langages", coef: 2, code: "langages" },
                    { nom: "Atelier Java", coef: 1, code: "java" },
                    { nom: "Programmation Python", coef: 1, code: "python" },
                    { nom: "Électronique numérique", coef: 1.5, code: "elec_num" },
                    { nom: "Systèmes embarqués", coef: 1.5, code: "embarque" },
                    { nom: "Traitement d'images", coef: 1.5, code: "image" },
                    { nom: "Réseaux", coef: 1.5, code: "reseau" },
                    { nom: "Anglais 4", coef: 1, code: "ang4" },
                    { nom: "Français 4", coef: 1, code: "fr4" }
                ]
            }
        };

        // ======================== ÉTAT GLOBAL ========================
        let notes = {
            mpi: { s1: {}, s2: {} },
            mi: { s3: {}, s4: {} },
            pi: { s3: {}, s4: {} }
        };
        let moyennes = {
            mpi: { s1: 0, s2: 0, annuelle: 0 },
            mi: { s3: 0, s4: 0, annuelle: 0 },
            pi: { s3: 0, s4: 0, annuelle: 0 }
        };
        let moyennesMatieres = {
            mpi: {}, mi: {}, pi: {}
        };

        // ======================== FONCTIONS UTILITAIRES ========================
        function nettoyerNoteTP(valeur) {
            if (valeur === '' || valeur === null) return '';
            return valeur.toString().replace(',', '.');
        }

        function validerNote(valeur, type) {
            if (type === 'tp' && (valeur === '' || valeur === null)) return { valide: true, nettoyee: '' };
            let val = (type === 'tp') ? parseFloat(nettoyerNoteTP(valeur)) : parseFloat(valeur);
            if (isNaN(val) && type === 'tp') return { valide: true, nettoyee: '' }; // champ vide accepté
            if (isNaN(val) || val < 0 || val > 20) return { valide: false };
            return { valide: true, nettoyee: val };
        }

        // ======================== AFFICHAGE DES MATIÈRES ========================
        function afficherMatieres(filiere, semestre) {
            const containerId = `${filiere}-matieres-${semestre}`;
            const container = document.getElementById(containerId);
            if (!container) {
                console.error(`Conteneur ${containerId} introuvable`);
                return;
            }
            if (container.children.length > 0) return;

            const matieres = matieresData[filiere][semestre];
            if (!matieres) {
                console.error(`Pas de données pour ${filiere} ${semestre}`);
                return;
            }

            container.innerHTML = '';
            matieres.forEach((matiere, idx) => {
                if (!notes[filiere][semestre][idx]) {
                    notes[filiere][semestre][idx] = { ds: 0, tp: '', ex: 0 };
                }
                const card = document.createElement('div');
                card.className = 'matiere-card';
                card.innerHTML = `
                    <div class="matiere-header">
                        <span class="matiere-name">${matiere.nom}</span>
                        <span class="coefficient">Coef ${matiere.coef}</span>
                    </div>
                    <div class="input-group">
                        <div class="input-field">
                            <label>DS</label>
                            <input type="number" min="0" max="20" step="0.1" class="ds-input" data-filiere="${filiere}" data-semestre="${semestre}" data-index="${idx}" value="${notes[filiere][semestre][idx].ds}">
                        </div>
                        <div class="input-field">
                            <label>TP</label>
                            <input type="text" class="tp-input" data-filiere="${filiere}" data-semestre="${semestre}" data-index="${idx}" placeholder="vide si pas TP" value="${notes[filiere][semestre][idx].tp}">
                            <div class="tp-hint">Optionnel</div>
                        </div>
                        <div class="input-field">
                            <label>Examen</label>
                            <input type="number" min="0" max="20" step="0.1" class="ex-input" data-filiere="${filiere}" data-semestre="${semestre}" data-index="${idx}" value="${notes[filiere][semestre][idx].ex}">
                        </div>
                    </div>
                    <div class="matiere-result">
                        Moyenne : <span class="matiere-moyenne" id="moy-${filiere}-${semestre}-${idx}">0.00</span>
                    </div>
                `;
                container.appendChild(card);
            });

            container.querySelectorAll('.ds-input, .tp-input, .ex-input').forEach(input => {
                input.addEventListener('input', (e) => {
                    const fil = e.target.dataset.filiere;
                    const sem = e.target.dataset.semestre;
                    const idx = e.target.dataset.index;
                    const type = e.target.classList.contains('ds-input') ? 'ds' : (e.target.classList.contains('tp-input') ? 'tp' : 'ex');
                    let val = e.target.value;
                    const validation = validerNote(val, type);
                    if (!validation.valide) {
                        e.target.classList.add('invalid');
                    } else {
                        e.target.classList.remove('invalid');
                        if (type === 'tp') {
                            notes[fil][sem][idx][type] = val;
                        } else {
                            notes[fil][sem][idx][type] = validation.nettoyee;
                        }
                        calculerMoyenneMatiere(fil, sem, idx);
                    }
                });
            });

            matieres.forEach((_, idx) => calculerMoyenneMatiere(filiere, semestre, idx));
            console.log(`Matières affichées pour ${filiere} ${semestre}`);
        }

        function calculerMoyenneMatiere(filiere, semestre, index) {
            const matiere = matieresData[filiere][semestre][index];
            const note = notes[filiere][semestre][index];
            let tpValue = 0;
            if (note.tp && note.tp.toString().trim() !== '') {
                tpValue = parseFloat(nettoyerNoteTP(note.tp)) || 0;
            }
            let moyenne;
            if (note.tp && note.tp.toString().trim() !== '') {
                moyenne = (note.ds * 0.25) + (tpValue * 0.25) + (note.ex * 0.5);
            } else {
                moyenne = (note.ds * 0.3) + (note.ex * 0.7);
            }
            const el = document.getElementById(`moy-${filiere}-${semestre}-${index}`);
            if (el) el.textContent = moyenne.toFixed(2);
            if (!moyennesMatieres[filiere]) moyennesMatieres[filiere] = {};
            moyennesMatieres[filiere][matiere.code] = moyenne;
            return moyenne;
        }

        function verifierNotesSemestre(filiere, semestre) {
            const matieres = matieresData[filiere][semestre];
            for (let i = 0; i < matieres.length; i++) {
                const note = notes[filiere][semestre][i];
                if (!note) continue;
                if (note.ds < 0 || note.ds > 20) return { valide: false, message: `DS de ${matieres[i].nom} invalide` };
                if (note.ex < 0 || note.ex > 20) return { valide: false, message: `Examen de ${matieres[i].nom} invalide` };
                if (note.tp && note.tp.toString().trim() !== '') {
                    const tpVal = parseFloat(nettoyerNoteTP(note.tp));
                    if (isNaN(tpVal) || tpVal < 0 || tpVal > 20) return { valide: false, message: `TP de ${matieres[i].nom} invalide` };
                }
            }
            return { valide: true };
        }

        function calculerMoyenneSemestre(filiere, semestre) {
            const validation = verifierNotesSemestre(filiere, semestre);
            const msgDiv = document.getElementById(`${filiere}-validation-${semestre}`);
            if (!validation.valide) {
                if (msgDiv) {
                    msgDiv.textContent = validation.message;
                    msgDiv.className = 'validation-message error';
                }
                return false;
            }
            if (msgDiv) msgDiv.style.display = 'none';

            const matieres = matieresData[filiere][semestre];
            let sommePond = 0, sommeCoef = 0;
            for (let i = 0; i < matieres.length; i++) {
                const moy = calculerMoyenneMatiere(filiere, semestre, i);
                sommePond += moy * matieres[i].coef;
                sommeCoef += matieres[i].coef;
            }
            const moyenne = sommePond / sommeCoef;
            moyennes[filiere][semestre] = moyenne;
            document.getElementById(`${filiere}-moyenne-${semestre}`).textContent = moyenne.toFixed(2);
            if (msgDiv) {
                msgDiv.textContent = 'Moyenne calculée avec succès';
                msgDiv.className = 'validation-message success';
            }
            return true;
        }

        function reinitialiserSemestre(filiere, semestre) {
            const matieres = matieresData[filiere][semestre];
            matieres.forEach((_, idx) => {
                notes[filiere][semestre][idx] = { ds: 0, tp: '', ex: 0 };
                const dsInput = document.querySelector(`[data-filiere="${filiere}"][data-semestre="${semestre}"][data-index="${idx}"].ds-input`);
                const tpInput = document.querySelector(`[data-filiere="${filiere}"][data-semestre="${semestre}"][data-index="${idx}"].tp-input`);
                const exInput = document.querySelector(`[data-filiere="${filiere}"][data-semestre="${semestre}"][data-index="${idx}"].ex-input`);
                if (dsInput) dsInput.value = 0;
                if (tpInput) tpInput.value = '';
                if (exInput) exInput.value = 0;
                document.getElementById(`moy-${filiere}-${semestre}-${idx}`).textContent = '0.00';
            });
            moyennes[filiere][semestre] = 0;
            document.getElementById(`${filiere}-moyenne-${semestre}`).textContent = '0.00';
            const msgDiv = document.getElementById(`${filiere}-validation-${semestre}`);
            if (msgDiv) msgDiv.style.display = 'none';
        }

        // ======================== INITIALISATION ========================
        document.addEventListener('DOMContentLoaded', () => {
            console.log('Chargement initial...');
            afficherMatieres('mpi', 's1');
            afficherMatieres('mpi', 's2');
            afficherMatieres('mi', 's3');
            afficherMatieres('mi', 's4');
            afficherMatieres('pi', 's3');
            afficherMatieres('pi', 's4');

            // Navigation filières
            document.querySelectorAll('.filiere-tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    document.querySelectorAll('.filiere-tab').forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    const filiere = tab.dataset.filiere;
                    document.querySelectorAll('.filiere-content').forEach(c => c.classList.remove('active'));
                    document.getElementById(`${filiere}-content`).classList.add('active');
                    const semActif = document.querySelector(`#${filiere}-content .semester-tab.active`)?.dataset.semester || 's1';
                    const containerId = `${filiere}-matieres-${semActif}`;
                    if (document.getElementById(containerId)?.children.length === 0) {
                        afficherMatieres(filiere, semActif);
                    }
                });
            });

            // Navigation semestres
            document.querySelectorAll('.semester-tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    const parent = tab.closest('.filiere-content');
                    if (!parent) return;
                    parent.querySelectorAll('.semester-tab').forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    const sem = tab.dataset.semester;
                    const filiere = parent.id.replace('-content', '');
                    parent.querySelectorAll('.semester-content').forEach(c => c.classList.remove('active'));
                    const target = document.getElementById(`${filiere}-${sem}`);
                    if (target) {
                        target.classList.add('active');
                        if (sem.startsWith('s')) {
                            const containerId = `${filiere}-matieres-${sem}`;
                            if (document.getElementById(containerId)?.children.length === 0) {
                                afficherMatieres(filiere, sem);
                            }
                        }
                    }
                });
            });

            // Boutons calculer
            document.querySelectorAll('.calculate-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const filiere = e.target.dataset.filiere;
                    const semestre = e.target.dataset.semestre;
                    calculerMoyenneSemestre(filiere, semestre);
                });
            });

            // Boutons reset
            document.querySelectorAll('.reset-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const filiere = e.target.dataset.filiere;
                    const semestre = e.target.dataset.semestre;
                    reinitialiserSemestre(filiere, semestre);
                });
            });

            // Calcul annuel MPI
            document.getElementById('mpi-calc-annuel').addEventListener('click', () => {
                const msg = document.getElementById('mpi-validation-annuel');
                if (moyennes.mpi.s1 === 0 || moyennes.mpi.s2 === 0) {
                    msg.textContent = 'Calculez d’abord les deux semestres.';
                    msg.className = 'validation-message error';
                    return;
                }
                moyennes.mpi.annuelle = (moyennes.mpi.s1 + moyennes.mpi.s2) / 2;
                document.getElementById('mpi-moyenne-annuelle').textContent = moyennes.mpi.annuelle.toFixed(2);
                msg.textContent = 'Moyenne annuelle calculée.';
                msg.className = 'validation-message success';
            });

            // Calcul scores MPI
            document.getElementById('mpi-calc-scores').addEventListener('click', () => {
                const msg = document.getElementById('mpi-validation-scores');
                if (moyennes.mpi.annuelle === 0) {
                    msg.textContent = 'Calculez d’abord la moyenne annuelle.';
                    msg.className = 'validation-message error';
                    return;
                }
                const bonus = document.getElementById('mpi-bonus').checked ? 0.5 : 0;
                const moyMaths = ( (moyennesMatieres.mpi.alg1||0) + (moyennesMatieres.mpi.ana1||0) + (moyennesMatieres.mpi.alg2||0) + (moyennesMatieres.mpi.ana2||0) ) / 4;
                const moyInfo = ( (moyennesMatieres.mpi.algo1||0) + (moyennesMatieres.mpi.prog1||0) + (moyennesMatieres.mpi.algo2||0) + (moyennesMatieres.mpi.prog2||0) ) / 4;
                const moyPh = ( (moyennesMatieres.mpi.optique||0) + (moyennesMatieres.mpi.mec||0) + (moyennesMatieres.mpi.electro||0) + (moyennesMatieres.mpi.circuit||0) + (moyennesMatieres.mpi.magnetostatique||0) + (moyennesMatieres.mpi.mec_quant||0) + (moyennesMatieres.mpi.electronique||0) + (moyennesMatieres.mpi.sl||0) ) / 8;
                const moyLangues = ( (moyennesMatieres.mpi.fr1||0) + (moyennesMatieres.mpi.ang1||0) + (moyennesMatieres.mpi.fr2||0) + (moyennesMatieres.mpi.ang2||0) ) / 4;
                const scoreMI = 4 * (moyennes.mpi.annuelle + bonus) + 2 * moyMaths + 2 * moyInfo + moyLangues;
                const scorePI = 4 * moyennes.mpi.annuelle + 2 * moyPh + 2 * moyInfo + moyLangues;
                document.getElementById('mpi-score-mi').textContent = scoreMI.toFixed(2);
                document.getElementById('mpi-score-pi').textContent = scorePI.toFixed(2);
                document.getElementById('mpi-detail-mi').innerHTML = `MG: ${moyennes.mpi.annuelle.toFixed(2)} | Maths: ${moyMaths.toFixed(2)} | Info: ${moyInfo.toFixed(2)} | Langues: ${moyLangues.toFixed(2)} | Bonus: ${bonus}`;
                document.getElementById('mpi-detail-pi').innerHTML = `MG: ${moyennes.mpi.annuelle.toFixed(2)} | Physique: ${moyPh.toFixed(2)} | Info: ${moyInfo.toFixed(2)} | Langues: ${moyLangues.toFixed(2)}`;
                msg.textContent = 'Scores calculés.';
                msg.className = 'validation-message success';
            });

            // Calcul annuel MI
            document.getElementById('mi-calc-annuel').addEventListener('click', () => {
                const msg = document.getElementById('mi-validation-annuel');
                if (moyennes.mi.s3 === 0 || moyennes.mi.s4 === 0) {
                    msg.textContent = 'Calculez d’abord S3 et S4.';
                    msg.className = 'validation-message error';
                    return;
                }
                moyennes.mi.annuelle = (moyennes.mi.s3 + moyennes.mi.s4) / 2;
                document.getElementById('mi-moyenne-2a').textContent = moyennes.mi.annuelle.toFixed(2);
                msg.textContent = 'Moyenne 2A calculée.';
                msg.className = 'validation-message success';
            });

            // Calcul scores MI (simplifié)
            document.getElementById('mi-calc-scores').addEventListener('click', () => {
                const msg = document.getElementById('mi-validation-scores');
                if (moyennes.mi.annuelle === 0 || moyennes.mpi.annuelle === 0) {
                    msg.textContent = 'Calculez la moyenne de 1A et de 2A.';
                    msg.className = 'validation-message error';
                    return;
                }
                const bonus = document.getElementById('mi-bonus').checked ? 0.5 : 0;
                const malus = document.getElementById('mi-malus').checked ? -1 : 0;
                const scoreCI = (2 * (moyennes.mi.annuelle + bonus) + moyennes.mpi.annuelle + bonus) / 3 + malus;
                document.getElementById('mi-score-glsi').textContent = (scoreCI * 4).toFixed(2);
                document.getElementById('mi-score-ds').textContent = (scoreCI * 3.8).toFixed(2);
                document.getElementById('mi-score-isi').textContent = (scoreCI * 3.9).toFixed(2);
                msg.textContent = 'Scores MI calculés (exemple).';
                msg.className = 'validation-message success';
            });

            // Calcul annuel PI
            document.getElementById('pi-calc-annuel').addEventListener('click', () => {
                const msg = document.getElementById('pi-validation-annuel');
                if (moyennes.pi.s3 === 0 || moyennes.pi.s4 === 0) {
                    msg.textContent = 'Calculez d’abord S3 et S4.';
                    msg.className = 'validation-message error';
                    return;
                }
                moyennes.pi.annuelle = (moyennes.pi.s3 + moyennes.pi.s4) / 2;
                document.getElementById('pi-moyenne-2a').textContent = moyennes.pi.annuelle.toFixed(2);
                msg.textContent = 'Moyenne 2A calculée.';
                msg.className = 'validation-message success';
            });

            // Calcul scores PI (simplifié)
            document.getElementById('pi-calc-scores').addEventListener('click', () => {
                const msg = document.getElementById('pi-validation-scores');
                if (moyennes.pi.annuelle === 0 || moyennes.mpi.annuelle === 0) {
                    msg.textContent = 'Calculez la moyenne de 1A et de 2A.';
                    msg.className = 'validation-message error';
                    return;
                }
                const bonus = document.getElementById('pi-bonus').checked ? 0.5 : 0;
                const malus = document.getElementById('pi-malus').checked ? -1 : 0;
                const scoreCI = (2 * (moyennes.pi.annuelle + bonus) + moyennes.mpi.annuelle + bonus) / 3 + malus;
                document.getElementById('pi-score-ee').textContent = (scoreCI * 4.2).toFixed(2);
                document.getElementById('pi-score-gpmn').textContent = (scoreCI * 4.0).toFixed(2);
                msg.textContent = 'Scores PI calculés (exemple).';
                msg.className = 'validation-message success';
            });

            // Mode sombre
            const themeToggle = document.getElementById('themeToggle');
            const themeText = document.getElementById('themeText');
            themeToggle.addEventListener('click', () => {
                document.body.classList.toggle('dark-mode');
                if (document.body.classList.contains('dark-mode')) {
                    themeToggle.innerHTML = '<i class="fas fa-sun"></i> <span id="themeText">Mode clair</span>';
                } else {
                    themeToggle.innerHTML = '<i class="fas fa-moon"></i> <span id="themeText">Mode sombre</span>';
                }
            });
        });
    </script>
</body>
</html>
