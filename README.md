# simulacro1buhos.github.io
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resultados Académicos · Comunidad Búho</title>
    <link href="https://fonts.googleapis.com/css2?family=Acme&family=Arial:wght@400;700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Acme&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
    <style>
        :root {
            --verde: #00a03c;
            --verde-d: #007a2e;
            --verde-l: #e6f7ed;
            --purp: #460256;
            --purp-l: #f3e8f7;
            --gray1: #f5f6fa;
            --gray2: #e8eaef;
            --gray3: #9aa0b0;
            --text: #1a1d2e;
            --text-s: #4a5068;
            --white: #ffffff;
            --shadow: 0 4px 24px rgba(70, 2, 86, 0.10);
            --shadow-l: 0 2px 10px rgba(70, 2, 86, 0.07);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: var(--gray1);
            color: var(--text);
            min-height: 100vh;
        }


        /* ── HEADER ── */
        .site-header {
            background: var(--white);
            border-bottom: 2px solid var(--gray2);
            padding: 1.1rem 2rem;
            display: flex;
            align-items: center;
            gap: 1.1rem;
            box-shadow: var(--shadow-l);
        }

        .site-header img {
            width: 70px;
            height: 70px;
            object-fit: contain;
        }

        .header-text {}

        .header-text .inst-name {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 1.6rem;
            color: var(--verde-d);
            letter-spacing: 0.01em;
            line-height: 1.1;
        }

        .header-text .inst-sub {
            font-size: 0.78rem;
            color: var(--gray3);
            margin-top: 0.15rem;
            letter-spacing: 0.03em;
            text-transform: uppercase;
        }

        /* ── PAGE WRAPPER ── */
        .page {
            max-width: 860px;
            margin: 0 auto;
            padding: 2.5rem 1.2rem 3rem;
        }

        /* ── LOGIN CARD ── */
        .login-wrap {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding-top: 1rem;
        }

        .login-hero {
            text-align: center;
            margin-bottom: 2rem;
        }

        .login-hero .logo-big {
            width: 170px;
            height: 170px;
            object-fit: contain;
            margin-bottom: 1rem;
            filter: drop-shadow(0 4px 12px rgba(70, 2, 86, 0.18));
        }

        .login-hero h1 {
            font-family: 'Acme', Arial, sans-serif;
            font-size: clamp(1.6rem, 4vw, 2.2rem);
            color: var(--verde);
            line-height: 1.15;
        }

        .login-hero p {
            margin-top: 0.5rem;
            color: var(--text-s);
            font-size: 0.93rem;
        }

        .login-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 16px;
            padding: 2.2rem 2rem;
            width: 100%;
            max-width: 440px;
            box-shadow: var(--shadow);
        }

        .field-label {
            display: block;
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.82rem;
            letter-spacing: 0.08em;
            text-transform: uppercase;
            color: var(--purp);
            margin-bottom: 0.6rem;
        }

        .input-row {
            display: flex;
            gap: 0.7rem;
        }

        .input-row input {
            flex: 1;
            border: 1.5px solid var(--gray2);
            border-radius: 10px;
            padding: 0.85rem 1rem;
            font-size: 1rem;
            font-family: Arial, sans-serif;
            color: var(--text);
            background: var(--gray1);
            outline: none;
            transition: border-color 0.2s, box-shadow 0.2s;
            -moz-appearance: textfield;
        }

        .input-row input::-webkit-outer-spin-button,
        .input-row input::-webkit-inner-spin-button {
            -webkit-appearance: none;
        }

        .input-row input::placeholder {
            color: var(--gray3);
        }

        .input-row input:focus {
            border-color: var(--verde);
            box-shadow: 0 0 0 3px rgba(0, 160, 60, 0.12);
            background: var(--white);
        }

        .btn-consultar {
            background: var(--verde);
            color: white;
            border: none;
            border-radius: 10px;
            padding: 0 1.4rem;
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.95rem;
            letter-spacing: 0.04em;
            cursor: pointer;
            transition: background 0.2s, transform 0.15s, box-shadow 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.4rem;
            min-width: 110px;
            box-shadow: 0 3px 12px rgba(0, 160, 60, 0.25);
            white-space: nowrap;
        }

        .btn-consultar:hover {
            background: var(--verde-d);
            transform: translateY(-1px);
            box-shadow: 0 5px 18px rgba(0, 160, 60, 0.3);
        }

        .btn-consultar:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        .spinner {
            width: 15px;
            height: 15px;
            border: 2px solid rgba(255, 255, 255, 0.35);
            border-top-color: white;
            border-radius: 50%;
            animation: spin 0.7s linear infinite;
            display: none;
        }

        .error-box {
            margin-top: 1rem;
            background: #fff0f0;
            border: 1px solid #ffc8c8;
            color: #c0392b;
            border-radius: 8px;
            padding: 0.7rem 1rem;
            font-size: 0.87rem;
            display: none;
        }

        /* ── DIVIDER ── */

        /* ── RESULTS ── */
        .results-panel {
            display: none;
        }

        .back-btn {
            display: inline-flex;
            align-items: center;
            gap: 0.45rem;
            color: var(--gray3);
            font-size: 0.83rem;
            cursor: pointer;
            border: none;
            background: none;
            padding: 0;
            margin-bottom: 1.8rem;
            transition: color 0.2s;
            font-family: Arial, sans-serif;
        }

        .back-btn:hover {
            color: var(--purp);
        }

        /* Student hero card */
        .hero-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 16px;
            padding: 0;
            margin-bottom: 1.2rem;
            box-shadow: var(--shadow);
            overflow: hidden;
        }

        .hero-top {
            background: linear-gradient(120deg, var(--purp) 0%, #6d0f88 100%);
            padding: 1.6rem 2rem;
            display: flex;
            align-items: center;
            gap: 1.2rem;
        }

        .hero-top img {
            width: 48px;
            height: 48px;
            object-fit: contain;
            opacity: 0.92;
        }

        .hero-name {
            font-family: 'Acme', Arial, sans-serif;
            font-size: clamp(1.3rem, 3vw, 1.8rem);
            color: white;
            line-height: 1.15;
        }

        .hero-doc {
            font-size: 0.8rem;
            color: rgba(255, 255, 255, 0.65);
            margin-top: 0.25rem;
        }



        .puntaje-block {
            text-align: center;
            background: rgba(255, 255, 255, 0.15);
            border: 1.5px solid rgba(255, 255, 255, 0.3);
            border-radius: 12px;
            padding: 0.9rem 1.3rem;
            min-width: 130px;
            backdrop-filter: blur(4px);
        }

        .puntaje-block .lbl {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.65rem;
            letter-spacing: 0.12em;
            text-transform: uppercase;
            color: rgba(255, 255, 255, 0.75);
            margin-bottom: 0.3rem;
        }

        .puntaje-block .num {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 2.2rem;
            color: white;
            line-height: 1;
        }

        .puntaje-block .sub {
            font-size: 0.7rem;
            color: rgba(255, 255, 255, 0.6);
            margin-top: 0.2rem;
        }

        /* Areas */
        .section-title {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.78rem;
            letter-spacing: 0.12em;
            text-transform: uppercase;
            color: var(--gray3);
            margin: 1.5rem 0 0.8rem;
        }

        .areas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(148px, 1fr));
            gap: 0.9rem;
            margin-bottom: 0.5rem;
        }

        .area-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 13px;
            padding: 1.1rem 1rem;
            position: relative;
            overflow: hidden;
            transition: box-shadow 0.2s, transform 0.2s;
        }

        .area-card:hover {
            box-shadow: var(--shadow);
            transform: translateY(-2px);
        }

        .area-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            border-radius: 13px 13px 0 0;
        }

        .area-card:nth-child(1)::before {
            background: linear-gradient(90deg, #f59e0b, #fcd34d);
        }

        .area-card:nth-child(2)::before {
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
        }

        .area-card:nth-child(3)::before {
            background: linear-gradient(90deg, #16a34a, #34d399);
        }

        .area-card:nth-child(4)::before {
            background: linear-gradient(90deg, #7c3aed, #a78bfa);
        }

        .area-card:nth-child(5)::before {
            background: linear-gradient(90deg, #dc2626, #f87171);
        }

        .area-name {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.82rem;
            letter-spacing: 0.06em;
            text-transform: uppercase;
            color: var(--gray3);
            margin-bottom: 0.6rem;
            line-height: 1.3;
        }

        .area-score {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 2.1rem;
            color: var(--text);
            line-height: 1;
        }

        .area-score span {
            font-family: Arial, sans-serif;
            font-size: 0.78rem;
            color: var(--gray3);
            font-weight: 400;
        }

        .area-progress {
            margin-top: 0.65rem;
            height: 6px;
            background: var(--gray2);
            border-radius: 100px;
            overflow: visible;
            position: relative;
        }

        /* línea central de referencia */
        .area-progress::before {
            content: '';
            position: absolute;
            left: 50%;
            top: -2px;
            width: 2px;
            height: 10px;
            background: var(--gray3);
            border-radius: 2px;
            z-index: 2;
        }

        .area-progress-fill {
            height: 100%;
            border-radius: 100px;
            position: absolute;
            transition: left 1s ease 0.3s, width 1s ease 0.3s;
        }

        .area-card:nth-child(1) .area-progress-fill {
            background: linear-gradient(90deg, #f59e0b, #fcd34d);
        }

        .area-card:nth-child(2) .area-progress-fill {
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
        }

        .area-card:nth-child(3) .area-progress-fill {
            background: linear-gradient(90deg, #16a34a, #34d399);
        }

        .area-card:nth-child(4) .area-progress-fill {
            background: linear-gradient(90deg, #7c3aed, #a78bfa);
        }

        .area-card:nth-child(5) .area-progress-fill {
            background: linear-gradient(90deg, #dc2626, #f87171);
        }

        /* Chart */
        .chart-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 16px;
            padding: 1.8rem;
            box-shadow: var(--shadow-l);
            margin-top: 0.9rem;
        }

        .chart-head {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.78rem;
            letter-spacing: 0.12em;
            text-transform: uppercase;
            color: var(--gray3);
            margin-bottom: 1.2rem;
        }

        .chart-container {
            position: relative;
            height: 500px;
            overflow: visible;
        }

        /* Footer */
        .site-footer {
            text-align: center;
            margin-top: 2.5rem;
            padding-top: 1.5rem;
            border-top: 1.5px solid var(--gray2);
            font-size: 0.76rem;
            color: var(--gray3);
            line-height: 1.7;
        }

        .site-footer strong {
            font-family: 'Acme', Arial, sans-serif;
            color: var(--purp);
        }

        /* Animations */
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(20px)
            }

            to {
                opacity: 1;
                transform: translateY(0)
            }
        }

        @keyframes fadeDown {
            from {
                opacity: 0;
                transform: translateY(-16px)
            }

            to {
                opacity: 1;
                transform: translateY(0)
            }
        }

        @keyframes spin {
            to {
                transform: rotate(360deg)
            }
        }

        .anim-up {
            animation: fadeUp 0.55s ease both;
        }

        .anim-down {
            animation: fadeDown 0.55s ease both;
        }

        @media(max-width:580px) {

            /* Hero: logo + nombre arriba, puntaje abajo full width */
            .hero-card {
                border-radius: 14px !important;
                overflow: hidden;
            }

            .puntaje-block {
                border-radius: 0 0 14px 14px !important;
                margin: 0;
            }

            .hero-top {
                flex-wrap: wrap;
                padding: 1.2rem 1.2rem 1rem;
                gap: 0.8rem;
                align-items: center;
            }

            .hero-top img {
                width: 38px;
                height: 38px;
            }

            .hero-top>div[style] {
                flex: 1;
                min-width: 0;
            }

            .hero-name {
                font-size: 1.1rem;
            }

            .puntaje-block {
                width: 100%;
                display: flex;
                flex-direction: row;
                align-items: center;
                justify-content: space-between;
                border-radius: 10px;
                border: 1.5px solid rgba(255, 255, 255, 0.25);
                padding: 0.7rem 1.1rem;
                min-width: unset;
                background: rgba(255, 255, 255, 0.12);
                margin-top: 0.2rem;
            }

            .puntaje-block .lbl {
                margin-bottom: 0;
                font-size: 0.68rem;
            }

            .puntaje-block .num {
                font-size: 2rem;
            }

            .puntaje-block .sub {
                font-size: 0.65rem;
                margin-top: 0;
            }

            /* Login */
            .login-card {
                padding: 1.5rem 1.1rem;
            }

            .input-row {
                flex-direction: column;
                gap: 0.6rem;
            }

            .btn-consultar {
                width: 100%;
                padding: 0.85rem;
            }

            .site-header {
                padding: 0.9rem 1rem;
            }

            .site-header img {
                width: 48px;
                height: 48px;
            }

            /* Tacómetros 2 columnas, quinto centrado */
            .tach-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .tach-grid .tach-card:nth-child(5) {
                grid-column: 1 / -1;
                max-width: 50%;
                margin: 0 auto;
                width: 100%;
            }

            .tach-card.total-card {
                grid-column: 1 / -1;
            }

            /* Áreas 2 columnas, último centrado */
            .areas-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .areas-grid .area-card:last-child {
                grid-column: 1 / -1;
                max-width: 50%;
                margin: 0 auto;
                width: 100%;
            }

            /* Radar chart más alto para que labels no se corten */
            .chart-container {
                height: auto;
                aspect-ratio: 4 / 3;
            }

            .chart-card {
                padding: 0;
                border-radius: 10px;
                overflow: hidden;
            }

            .chart-head {
                padding: 0.6rem 0.8rem 0;
            }
        }

        /* ── TACÓMETROS ── */
        .tach-section {
            margin-top: 1.2rem;
        }

        .tach-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(148px, 1fr));
            gap: 0.9rem;
            margin-bottom: 0.9rem;
        }

        .tach-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 13px;
            padding: 1.1rem 1rem 1rem;
            text-align: center;
            transition: box-shadow 0.2s, transform 0.2s;
        }

        .tach-card:hover {
            box-shadow: var(--shadow);
            transform: translateY(-2px);
        }

        .tach-card.total-card {
            grid-column: 1 / -1;
            background: linear-gradient(135deg, var(--purp-l), #f0e8f8);
            border-color: rgba(70, 2, 86, 0.15);
        }

        .tach-name {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.75rem;
            letter-spacing: 0.06em;
            text-transform: uppercase;
            color: var(--text-s);
            margin-bottom: 0.7rem;
        }

        .tach-wrap {
            position: relative;
            width: 110px;
            height: 60px;
            margin: 0 auto 0.5rem;
        }

        .tach-wrap.big {
            width: 140px;
            height: 75px;
        }

        .tach-svg {
            width: 100%;
            height: 100%;
            overflow: visible;
        }

        .tach-track {
            fill: none;
            stroke: var(--gray2);
            stroke-width: 10;
            stroke-linecap: round;
        }

        .tach-fill {
            fill: none;
            stroke-width: 10;
            stroke-linecap: round;
            transition: stroke-dashoffset 1.2s ease 0.4s;
        }

        .tach-nums {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 1.4rem;
            color: var(--text);
            line-height: 1;
        }

        .tach-card.total-card .tach-nums {
            font-size: 1.8rem;
            color: var(--purp);
        }

        .tach-pct {
            font-size: 0.72rem;
            color: var(--gray3);
            margin-top: 0.15rem;
        }

        .tach-card.total-card .tach-pct {
            font-size: 0.82rem;
        }

        /* ── RÚBRICA ── */
        .rubrica-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 13px;
            padding: 1.2rem 1.4rem;
            margin-top: 0.9rem;
            box-shadow: var(--shadow-l);
        }

        .rubrica-title {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.78rem;
            letter-spacing: 0.1em;
            text-transform: uppercase;
            color: var(--gray3);
            margin-bottom: 0.9rem;
        }

        .rubrica-items {
            display: flex;
            flex-direction: column;
            gap: 0.65rem;
        }

        .rubrica-item {
            display: flex;
            align-items: flex-start;
            gap: 0.75rem;
        }

        .rubrica-barra {
            width: 4px;
            height: 36px;
            border-radius: 4px;
            flex-shrink: 0;
        }

        .rubrica-label {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.85rem;
            color: var(--text);
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        .rubrica-desc {
            font-size: 0.78rem;
            color: var(--gray3);
            margin-top: 0.1rem;
        }

        /* ── RADAR HTML LABELS ── */
        .radar-labels {
            position: absolute;
            inset: 0;
            pointer-events: none;
            z-index: 10;
        }

        .radar-label {
            position: absolute;
            font-family: Arial, sans-serif;
            font-weight: bold;
            font-size: 11px;
            color: #1a1d2e;
            text-align: center;
            line-height: 1.3;
            transform: translate(-50%, -50%);
            background: none;
            padding: 2px 4px;
            white-space: nowrap;
        }

        /* ── TARJETAS DESPLEGABLES ── */
        .mat-card {
            background: var(--white);
            border: 1.5px solid var(--gray2);
            border-radius: 14px;
            margin-bottom: 0.75rem;
            overflow: hidden;
            box-shadow: var(--shadow-l);
            transition: box-shadow 0.2s;
        }

        .mat-card:hover {
            box-shadow: var(--shadow);
        }

        .mat-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 1rem 1.1rem;
            cursor: pointer;
            user-select: none;
            transition: background 0.2s;
            gap: 0.8rem;
        }

        .mat-header:hover {
            background: #faf9ff;
        }

        .mat-header-left {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            flex: 1;
            min-width: 0;
        }

        .mat-barra-vert {
            width: 4px;
            height: 40px;
            border-radius: 4px;
            flex-shrink: 0;
        }

        .mat-titulo {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.95rem;
            color: var(--text);
        }

        .mat-sub {
            font-size: 0.77rem;
            color: var(--gray3);
            margin-top: 0.15rem;
        }

        .mat-right {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            flex-shrink: 0;
        }

        .mat-score {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 1.4rem;
            color: var(--purp);
            line-height: 1;
        }

        .pct-badge {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.78rem;
            padding: 0.2rem 0.55rem;
            border-radius: 100px;
        }

        .badge-g {
            background: #dcfce7;
            color: #15803d;
        }

        .badge-a {
            background: #fef3c7;
            color: #b45309;
        }

        .badge-r {
            background: #fee2e2;
            color: #b91c1c;
        }

        .mat-chevron {
            color: var(--gray3);
            font-size: 0.75rem;
            transition: transform 0.3s;
            flex-shrink: 0;
        }

        .mat-chevron.open {
            transform: rotate(180deg);
        }

        .mat-detalle {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.38s ease;
        }

        .mat-detalle.open {
            max-height: 500px;
        }

        .mat-detalle-inner {
            padding: 0.85rem 1.1rem 1rem;
            border-top: 1.5px solid var(--gray2);
            background: #faf8ff;
        }

        .mat-detalle-titulo {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.7rem;
            letter-spacing: 0.1em;
            text-transform: uppercase;
            color: var(--gray3);
            margin-bottom: 0.75rem;
        }

        .asig-row {
            display: grid;
            grid-template-columns: 90px 1fr 72px;
            align-items: center;
            gap: 0.7rem;
            margin-bottom: 0.6rem;
        }

        .asig-row:last-child {
            margin-bottom: 0;
        }

        .asig-nombre {
            font-size: 0.82rem;
            color: var(--text-s);
        }

        .asig-barra-wrap {
            height: 8px;
            background: var(--gray2);
            border-radius: 100px;
            overflow: hidden;
        }

        .asig-barra-fill {
            height: 100%;
            border-radius: 100px;
            transition: width 0.9s ease 0.2s;
        }

        .asig-nums {
            font-family: 'Acme', Arial, sans-serif;
            font-size: 0.78rem;
            color: var(--text);
            text-align: right;
            white-space: nowrap;
        }

        @media(max-width:580px) {
            .asig-row {
                grid-template-columns: 72px 1fr 62px;
                gap: 0.5rem;
            }

            .asig-nombre {
                font-size: 0.76rem;
            }

            .asig-nums {
                font-size: 0.72rem;
            }

            .mat-titulo {
                font-size: 0.88rem;
            }

            .mat-score {
                font-size: 1.2rem;
            }
        }
    </style>
</head>

<body>


    <header class="site-header">
        <img src="logo.png" alt="Comunidad Búho">
        <div class="header-text">
            <div class="inst-name">Comunidad Búho</div>

        </div>
    </header>

    <div class="page">

        <!-- ── LOGIN ── -->
        <div id="loginView" class="login-wrap anim-up">
            <div class="login-hero">
                <img class="logo-big" src="logo.png" alt="Logo Comunidad Búho">
                <h1>Consulta tus Resultados</h1>
                <p>Ingresa tu número de documento para ver tu desempeño</p>
            </div>

            <div class="login-card">
                <label class="field-label" for="docInput">Número de documento</label>
                <div class="input-row">
                    <input type="text" id="docInput" placeholder="Ej. 0123456789" autocomplete="off"
                        inputmode="numeric">
                    <button class="btn-consultar" id="btnSearch" onclick="buscar()">
                        <div class="spinner" id="spinner"></div>
                        <span id="btnText">Consultar</span>
                    </button>
                </div>
                <div class="error-box" id="errorMsg"></div>
            </div>

        </div>

        <!-- ── RESULTS ── -->
        <div class="results-panel" id="resultsView" style="display:none">

            <button class="back-btn" onclick="volverAtras()">
                <svg width="15" height="15" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
                </svg>
                Nueva consulta
            </button>

            <div class="hero-card">
                <div class="hero-top">
                    <img src="logo.png" alt="Logo">
                    <div style="flex:1">
                        <div class="hero-name" id="resNombre"></div>
                        <div class="hero-doc" id="resDoc"></div>
                    </div>
                    <div class="puntaje-block">
                        <div class="lbl">Puntaje UNAL</div>
                        <div class="num" id="resPuntaje"></div>
                        <div class="sub">puntos totales</div>
                    </div>
                </div>

            </div>

            <div class="section-title">Puntaje por áreas</div>
            <div class="areas-grid" id="areasGrid"></div>

            <div class="chart-card">
                <div class="chart-head">Perfil por áreas</div>
                <div class="chart-container"><canvas id="radarChart"></canvas></div>
            </div>

            <div class="tach-section">
                <div class="section-title">Aciertos por área</div>
                <div class="tach-grid" id="tachGrid"></div>
            </div>

            <div class="section-title" style="margin-top:1.5rem">Puntaje y aciertos por materia</div>
            <div id="materiasGrid"></div>
            <div class="rubrica-card">
                <div class="rubrica-title">¿Qué significa cada color?</div>
                <div class="rubrica-items">
                    <div class="rubrica-item">
                        <div class="rubrica-barra" style="background:#00a03c"></div>
                        <div>
                            <div class="rubrica-label">Verde <span style="font-family:Arial">≥</span> 70%</div>
                            <div class="rubrica-desc">Desempeño alto — excelente dominio del área</div>
                        </div>
                    </div>
                    <div class="rubrica-item">
                        <div class="rubrica-barra" style="background:#f59e0b"></div>
                        <div>
                            <div class="rubrica-label">Amarillo <span style="font-family:'Acme',Arial">50%–69%</span>
                            </div>
                            <div class="rubrica-desc">Desempeño medio — hay aspectos por reforzar</div>
                        </div>
                    </div>
                    <div class="rubrica-item">
                        <div class="rubrica-barra" style="background:#f87171"></div>
                        <div>
                            <div class="rubrica-label">Rojo <span style="font-family:Arial">&lt;</span> 50%</div>
                            <div class="rubrica-desc">Desempeño bajo — se recomienda refuerzo prioritario</div>
                        </div>
                    </div>
                </div>
            </div>

        </div>

        <footer class="site-footer">
            <strong>Comunidad Búho</strong><br>
            Consulta individual · Los datos son confidenciales · Solo tú puedes ver tus resultados
        </footer>

    </div><!-- /page -->

    <script>
        const API_URL = "https://script.google.com/macros/s/AKfycbx1Tfgh1XEaU6gtvQTEGfIy_3OmJuyoKpZToj5mQ6q98AkHp_R1OrMi8GG9MqnXM1LV/exec";

        const AREAS = [
            { key: 'analisis_imagen', label: 'Análisis de Imagen' },
            { key: 'analisis_textual', label: 'Análisis Textual' },
            { key: 'ciencias_naturales', label: 'Ciencias Naturales' },
            { key: 'ciencias_sociales', label: 'Ciencias Sociales' },
            { key: 'matematicas', label: 'Matemáticas' },
        ];

        let chartInstance = null;

        function jsonp(url) {
            return new Promise((resolve, reject) => {
                const cb = 'cb_' + Math.random().toString(36).slice(2);
                const script = document.createElement('script');
                window[cb] = (data) => {
                    delete window[cb];
                    document.body.removeChild(script);
                    resolve(data);
                };
                script.onerror = () => {
                    delete window[cb];
                    document.body.removeChild(script);
                    reject(new Error('JSONP failed'));
                };
                script.src = url + '&callback=' + cb;
                document.body.appendChild(script);
            });
        }

        function setLoading(on) {
            const btn = document.getElementById('btnSearch');
            document.getElementById('spinner').style.display = on ? 'block' : 'none';
            document.getElementById('btnText').style.display = on ? 'none' : 'inline';
            btn.disabled = on;
        }

        // ── DATOS DE PRUEBA (documento "0000") ─────────────────────────────────
        const DEMO = {
            documento: "0000",
            nombre: "Estudiante de Prueba",
            analisis_imagen: 11.50,
            analisis_textual: 10.75,
            ciencias_naturales: 9.80,
            ciencias_sociales: 11.20,
            matematicas: 10.40,
            puntaje_unal: 580.00,
            rank: 1,
            total: 35,
            aciertos: { ai: 12, at: 24, cn: 5, cs: 17, mat: 9, suma: 67 },
            totales: { ai: 19, at: 31, cn: 21, cs: 23, mat: 26, suma: 120 },
            materias: { ai: 12, at: 15, log: 9, bio: 3, fis: 1, qui: 1, geo: 9, his: 8, mat: 6, geom: 3, suma: 67 },
            totalesMat: { ai: 19, at: 18, log: 13, bio: 8, fis: 7, qui: 6, geo: 12, his: 11, mat: 16, geom: 10, suma: 120 }
        };
        // ────────────────────────────────────────────────────────────────────────

        async function buscar() {
            const val = document.getElementById('docInput').value.trim();
            const err = document.getElementById('errorMsg');
            err.style.display = 'none';

            if (!val) {
                err.textContent = '⚠️ Por favor ingresa tu número de documento.';
                err.style.display = 'block';
                return;
            }

            // Modo demo: documento "0000" carga datos de prueba sin llamar al servidor
            if (val === '0000' || val === '0') {
                mostrarResultados(DEMO);
                return;
            }

            setLoading(true);

            try {
                const json = await jsonp(`${API_URL}?doc=${encodeURIComponent(val)}`);

                if (!json.ok) {
                    err.textContent = '⚠️ No se encontró ningún estudiante con ese documento. Verifica el número e intenta de nuevo.';
                    err.style.display = 'block';
                    setLoading(false);
                    return;
                }

                mostrarResultados(json.data);

            } catch (e) {
                err.textContent = '⚠️ Error al conectar con el servidor. Intenta de nuevo en unos segundos.';
                err.style.display = 'block';
                setLoading(false);
            }
        }

        function mostrarResultados(s) {
            document.getElementById('resNombre').textContent = s.nombre;
            document.getElementById('resDoc').textContent = 'C.C. ' + s.documento;
            document.getElementById('resPuntaje').textContent = parseFloat(s.puntaje_unal).toFixed(1);
            document.getElementById("areasGrid").innerHTML = "";
            document.getElementById("tachGrid").innerHTML = "";
            buildAreas(s);
            buildChart(s);
            buildTach(s);
            buildMaterias(s);
            setTimeout(animateTach, 200);

            document.getElementById('loginView').style.display = 'none';
            const rv = document.getElementById('resultsView');
            rv.style.display = 'block';
            rv.classList.remove('anim-up');
            void rv.offsetWidth;
            rv.classList.add('anim-up');
            setLoading(false);
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function buildAreas(s) {
            const grid = document.getElementById('areasGrid');
            grid.innerHTML = '';
            // Rango de referencia: media=10, rango visual 7-13
            const REF_MIN = 7, REF_MAX = 13, REF_MID = 10;
            const RANGE = REF_MAX - REF_MIN; // 6

            AREAS.forEach(area => {
                const score = parseFloat(s[area.key]);
                // Posición relativa: 0% = izquierda (7), 50% = centro (10), 100% = derecha (13)
                const pos = Math.min(Math.max((score - REF_MIN) / RANGE, 0), 1); // 0..1
                const center = 0.5;
                // La barra va desde el centro hacia la posición del score
                const barLeft = Math.min(pos, center) * 100;   // % desde izquierda
                const barWidth = Math.abs(pos - center) * 100;  // % de ancho
                const isAbove = pos >= center;

                const card = document.createElement('div');
                card.className = 'area-card';
                card.innerHTML = `
      <div class="area-name">${area.label}</div>
      <div class="area-score">${score.toFixed(2)}</div>
      <div class="area-progress" style="margin-top:0.65rem">
        <div class="area-progress-fill"
          style="left:${barLeft}%;width:0%"
          data-left="${barLeft}%"
          data-width="${barWidth}%"
          data-above="${isAbove}">
        </div>
      </div>`;
                grid.appendChild(card);
            });

            requestAnimationFrame(() => {
                document.querySelectorAll('.area-progress-fill').forEach((el, i) => {
                    el.style.left = el.dataset.left;
                    el.style.width = el.dataset.width;
                });
            });
        }



        // Definición de áreas con sus asignaturas
        const AREAS_DEF = [
            {
                key: 'imagen', label: '🖼️ Análisis de Imagen', color: 'linear-gradient(#f59e0b,#fcd34d)',
                scoreKey: 'analisis_imagen',
                subs: [
                    { label: 'Análisis de imagen', ac: 'ai', tot: 'ai' }
                ]
            },
            {
                key: 'textual', label: '📝 Análisis Textual', color: 'linear-gradient(#3b82f6,#60a5fa)',
                scoreKey: 'analisis_textual',
                subs: [
                    { label: 'Análisis textual', ac: 'at', tot: 'at' },
                    { label: 'Lógica', ac: 'log', tot: 'log' }
                ]
            },
            {
                key: 'naturales', label: '🔬 Ciencias Naturales', color: 'linear-gradient(#16a34a,#34d399)',
                scoreKey: 'ciencias_naturales',
                subs: [
                    { label: 'Biología', ac: 'bio', tot: 'bio' },
                    { label: 'Física', ac: 'fis', tot: 'fis' },
                    { label: 'Química', ac: 'qui', tot: 'qui' }
                ]
            },
            {
                key: 'sociales', label: '🌍 Ciencias Sociales', color: 'linear-gradient(#7c3aed,#a78bfa)',
                scoreKey: 'ciencias_sociales',
                subs: [
                    { label: 'Geografía', ac: 'geo', tot: 'geo' },
                    { label: 'Historia', ac: 'his', tot: 'his' }
                ]
            },
            {
                key: 'matematicas', label: '📐 Matemáticas', color: 'linear-gradient(#dc2626,#f87171)',
                scoreKey: 'matematicas',
                subs: [
                    { label: 'Matemáticas', ac: 'mat', tot: 'mat' },
                    { label: 'Geometría', ac: 'geom', tot: 'geom' }
                ]
            }
        ];

        function badgeClass(pct) {
            return pct >= 70 ? 'badge-g' : pct >= 50 ? 'badge-a' : 'badge-r';
        }

        function barColor(pct) {
            return pct >= 70 ? '#16a34a' : pct >= 50 ? '#f59e0b' : '#f87171';
        }

        function buildMaterias(s) {
            const grid = document.getElementById('materiasGrid');
            if (!grid) return;
            grid.innerHTML = '';

            const m = s.materias;
            const tm = s.totalesMat;
            if (!m || !tm) return;

            AREAS_DEF.forEach(area => {
                // Calcular aciertos y total del área sumando sus subs
                const acArea = area.subs.reduce((sum, sub) => sum + (m[sub.ac] || 0), 0);
                const totArea = area.subs.reduce((sum, sub) => sum + (tm[sub.tot] || 0), 0);
                const pctArea = totArea > 0 ? Math.round(acArea / totArea * 100) : 0;
                const score = parseFloat(s[area.scoreKey]).toFixed(2);

                const card = document.createElement('div');
                card.className = 'mat-card';

                const subsHTML = area.subs.map(sub => {
                    const ac = m[sub.ac] || 0;
                    const tot = tm[sub.tot] || 0;
                    const pct = tot > 0 ? Math.round(ac / tot * 100) : 0;
                    return `
        <div class="asig-row">
          <div class="asig-nombre">${sub.label}</div>
          <div class="asig-barra-wrap">
            <div class="asig-barra-fill" style="width:0%;background:${barColor(pct)}" data-width="${pct}%"></div>
          </div>
          <div class="asig-nums">${ac}/${tot} · ${pct}%</div>
        </div>`;
                }).join('');

                card.innerHTML = `
      <div class="mat-header" onclick="toggleMat(this)">
        <div class="mat-header-left">
          <div class="mat-barra-vert" style="background:${area.color}"></div>
          <div>
            <div class="mat-titulo">${area.label}</div>
            <div class="mat-sub">${acArea} / ${totArea} aciertos</div>
          </div>
        </div>
        <div class="mat-right">
          <div class="mat-score">${score}</div>
          <div class="pct-badge ${badgeClass(pctArea)}">${pctArea}%</div>
          <div class="mat-chevron">▼</div>
        </div>
      </div>
      <div class="mat-detalle">
        <div class="mat-detalle-inner">
          <div class="mat-detalle-titulo">Detalle por asignatura</div>
          ${subsHTML}
        </div>
      </div>`;

                grid.appendChild(card);
            });

            // Animar barras
            requestAnimationFrame(() => {
                document.querySelectorAll('.asig-barra-fill').forEach(el => {
                    el.style.width = el.dataset.width;
                });
            });
        }

        function toggleMat(header) {
            const detalle = header.nextElementSibling;
            const chevron = header.querySelector('.mat-chevron');
            const isOpen = detalle.classList.contains('open');
            document.querySelectorAll('.mat-detalle').forEach(d => d.classList.remove('open'));
            document.querySelectorAll('.mat-chevron').forEach(c => c.classList.remove('open'));
            if (!isOpen) {
                detalle.classList.add('open');
                chevron.classList.add('open');
            }
        }

        const TACH_AREAS = [
            { key: 'ai', label: '🖼️ Imagen', color: '#f59e0b' },
            { key: 'at', label: '📝 Textual', color: '#3b82f6' },
            { key: 'cn', label: '🔬 C. Naturales', color: '#16a34a' },
            { key: 'cs', label: '🌍 Sociales', color: '#7c3aed' },
            { key: 'mat', label: '📐 Matemáticas', color: '#dc2626' },
        ];

        function buildTach(s) {
            const grid = document.getElementById('tachGrid');
            if (!grid) return;
            grid.innerHTML = '';

            const ac = s.aciertos;
            const tot = s.totales;
            if (!ac || !tot) return;

            // Áreas individuales
            TACH_AREAS.forEach(area => {
                const acierto = ac[area.key];
                const total = tot[area.key];
                const pct = total > 0 ? (acierto / total) * 100 : 0;
                grid.appendChild(makeTachCard(area.label, acierto, total, pct, area.color, false));
            });

            // Total
            const pctTotal = tot.suma > 0 ? (ac.suma / tot.suma) * 100 : 0;
            grid.appendChild(makeTachCard('🎯 Total General', ac.suma, tot.suma, pctTotal, '#460256', true));
        }

        function makeTachCard(label, acierto, total, pct, color, isBig) {
            const card = document.createElement('div');
            card.className = 'tach-card' + (isBig ? ' total-card' : '');

            // Semi-circle SVG gauge
            // Arc: center=(60,60), r=45, from 180° to 0° (left to right)
            const cx = isBig ? 70 : 55;
            const cy = isBig ? 70 : 55;
            const r = isBig ? 52 : 40;
            const vw = cx * 2;
            const vh = cy + 5;

            const circumference = Math.PI * r; // half circle
            const dashTotal = circumference;
            const dashFill = (pct / 100) * circumference;
            const dashOffset = dashTotal - dashFill;

            // Color based on pct
            const fillColor = pct >= 70 ? '#00a03c' : pct >= 50 ? '#f59e0b' : '#f87171';

            card.innerHTML = `
    <div class="tach-name">${label}</div>
    <div class="tach-wrap${isBig ? ' big' : ''}">
      <svg class="tach-svg" viewBox="0 0 ${vw} ${vh}">
        <path class="tach-track"
          d="M ${cx - r} ${cy} A ${r} ${r} 0 0 1 ${cx + r} ${cy}"
          style="stroke:var(--gray2)"/>
        <path class="tach-fill"
          d="M ${cx - r} ${cy} A ${r} ${r} 0 0 1 ${cx + r} ${cy}"
          style="stroke:${fillColor};stroke-dasharray:${dashTotal};stroke-dashoffset:${dashTotal}"
          data-offset="${dashOffset}"/>
      </svg>
      <div style="position:absolute;bottom:0;width:100%;text-align:center">
        <div class="tach-nums">${acierto}<span style="font-size:0.6em;color:var(--gray3)">/${total}</span></div>
        <div class="tach-pct">${pct.toFixed(1)}%</div>
      </div>
    </div>`;

            return card;
        }

        function animateTach() {
            document.querySelectorAll('.tach-fill').forEach(el => {
                el.style.strokeDashoffset = el.dataset.offset;
            });
        }

        const radarLabelPlugin = {
            id: 'customLabels',
            afterDatasetsDraw(chart) {
                const ctx = chart.ctx;
                const meta = chart.getDatasetMeta(0);
                if (!meta || !meta.data) return;
                const labels = ['🖼️ Imagen', '📝 Textual', '🔬 C. Naturales', '🌍 Sociales', '📐 Matemáticas'];
                const w = chart.width;
                const fontSize = w < 380 ? 9 : 11;

                ctx.save();
                ctx.font = `bold ${fontSize}px Arial`;
                ctx.textAlign = 'center';
                ctx.textBaseline = 'middle';

                meta.data.forEach((point, i) => {
                    const x = point.x;
                    const y = point.y;
                    const words = labels[i].split(' ');

                    // Fondo semitransparente pequeño para legibilidad
                    const lineH = fontSize * 1.4;
                    const maxW = words.reduce((m, w) => Math.max(m, ctx.measureText(w).width), 0);
                    ctx.fillStyle = 'rgba(255,255,255,0.75)';
                    ctx.beginPath();
                    ctx.roundRect(x - maxW / 2 - 3, y - (words.length * lineH) / 2 - 2, maxW + 6, words.length * lineH + 4, 3);
                    ctx.fill();

                    ctx.fillStyle = '#460256';
                    words.forEach((word, j) => {
                        const offsetY = (j - (words.length - 1) / 2) * lineH;
                        ctx.fillText(word, x, y + offsetY);
                    });
                });
                ctx.restore();
            }
        };

        function buildChart(s) {
            const ctx = document.getElementById('radarChart').getContext('2d');
            if (chartInstance) chartInstance.destroy();
            Chart.register(radarLabelPlugin);
            chartInstance = new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['Análisis de Imagen', 'Análisis Textual', 'Ciencias Naturales', 'Ciencias Sociales', 'Matemáticas'],
                    datasets: [{
                        data: AREAS.map(a => parseFloat(s[a.key])),
                        backgroundColor: 'rgba(70,2,86,0.08)',
                        borderColor: 'rgba(70,2,86,0.7)',
                        borderWidth: 2,
                        pointBackgroundColor: '#460256',
                        pointBorderColor: '#fff',
                        pointBorderWidth: 2,
                        pointRadius: 5,
                        pointHoverRadius: 7,
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    layout: {
                        padding: 12
                    },
                    scales: {
                        r: {
                            min: 6, max: 14,
                            ticks: { stepSize: 2, color: '#9aa0b0', font: { size: 10, family: 'Arial' }, backdropColor: 'transparent' },
                            grid: { color: 'rgba(0,0,0,0.07)' },
                            angleLines: { color: 'rgba(0,0,0,0.07)' },
                            pointLabels: { display: false }
                        }
                    },
                    plugins: {
                        legend: { display: false },
                        tooltip: {
                            backgroundColor: '#460256',
                            titleColor: 'white',
                            bodyColor: 'white',
                            padding: 12,
                            borderColor: 'rgba(255,255,255,0.15)',
                            borderWidth: 1,
                            displayColors: false,
                            callbacks: {
                                label: ctx => {
                                    const emojis = ['🖼️', '📝', '🔬', '🌍', '📐'];
                                    const areaLabels = ['Análisis de Imagen', 'Análisis Textual', 'Ciencias Naturales', 'Ciencias Sociales', 'Matemáticas'];
                                    const idx = ctx.dataIndex;
                                    return `${emojis[idx]} ${areaLabels[idx]}: ${ctx.parsed.r.toFixed(2)} pts`;
                                },
                                title: () => ''
                            }
                        }
                    },
                    animation: { duration: 900, easing: 'easeOutQuart' }
                }
            });
        }

        function volverAtras() {
            document.getElementById('resultsView').style.display = 'none';
            document.getElementById('loginView').style.display = 'flex';
            document.getElementById('docInput').value = '';
            document.getElementById('errorMsg').style.display = 'none';
            document.getElementById('areasGrid').innerHTML = '';
            document.getElementById('tachGrid').innerHTML = '';
            if (document.getElementById('materiasGrid')) document.getElementById('materiasGrid').innerHTML = '';
            if (chartInstance) { chartInstance.destroy(); chartInstance = null; }
        }

        document.getElementById('docInput').addEventListener('keydown', e => {
            if (e.key === 'Enter') buscar();
        });
    </script>
</body>

</html>
