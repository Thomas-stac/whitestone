<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard Entreprises</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      display: flex;
      background-color: #f4f4f4;
    }
    .sidebar {
      width: 200px;
      background-color: #004b93;
      color: white;
      padding: 1rem;
    }
    .sidebar h2 {
      font-size: 20px;
      margin-bottom: 20px;
    }
    .sidebar ul {
      list-style: none;
      padding: 0;
    }
    .sidebar ul li {
      margin: 15px 0;
      cursor: pointer;
    }
    .sidebar ul li.active {
      background-color: #0e75d8;
      padding: 5px;
    }
    .main-content {
      flex-grow: 1;
      padding: 20px;
    }
    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: #7eab88;
      padding: 10px 20px;
      color: white;
    }
    .charts {
      display: flex;
      flex-direction: column;
      gap: 20px;
      margin-top: 20px;
    }
    .chart {
      background-color: white;
      padding: 10px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    .info-panel {
      margin-top: 20px;
      background-color: #e5e5e5;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 10px;
      max-width: 250px;
    }
    .info-panel strong {
      font-size: 1.2em;
    }
    .notes {
      margin-top: 10px;
    }
    canvas {
      width: 100% !important;
      max-height: 200px;
    }
  </style>
</head>
<body>
  <div class="sidebar">
    <h2>WATCHLIST</h2>
    <ul>
      <li class="active">Entreprise 1</li>
      <li>Entreprise 2</li>
      <li>Entreprise 3</li>
      <li>Entreprise 4</li>
      <li>Entreprise 5</li>
    </ul>
  </div>
  <div class="main-content">
    <div class="top-bar">
      <div>Entreprise 1</div>
      <div>Score global : <strong>95</strong></div>
    </div>

    <div class="charts">
      <div class="chart">
        <canvas id="caChart"></canvas>
      </div>
      <div class="chart">
        <canvas id="ebitdaChart"></canvas>
      </div>
    </div>

    <div class="info-panel">
      <div><strong>Valeur estimée</strong><br><span style="font-size: 1.5em; color: #2e6d9c;">€2.8M</span></div>
      <div><strong>Âge du propriétaire</strong><br><span style="font-size: 1.5em; color: #2e6d9c;">63 ans</span></div>
      <div><strong>Positionnement ESG</strong><br>News</div>
      <div class="notes">
        <ul>
          <li>“Clients” croissant</li>
          <li>Croissance du C.A. à 6% sur les 3 dernières années</li>
          <li>BFR stable</li>
        </ul>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    const caCtx = document.getElementById('caChart').getContext('2d');
    const ebitdaCtx = document.getElementById('ebitdaChart').getContext('2d');

    new Chart(caCtx, {
      type: 'line',
      data: {
        labels: ['2019', '2020', '2021', '2022', '2023'],
        datasets: [{
          label: 'Chiffre d\'affaires',
          data: [18, 30, 26, 40, 43],
          borderColor: '#0072c6',
          backgroundColor: 'transparent',
          tension: 0.3
        }]
      },
      options: {
        responsive: true,
        plugins: { legend: { display: true } },
        scales: { y: { beginAtZero: true } }
      }
    });

    new Chart(ebitdaCtx, {
      type: 'line',
      data: {
        labels: ['2019', '2020', '2021', '2022', '2023'],
        datasets: [{
          label: 'EBITDA',
          data: [23, 30, 35, 19, 40],
          borderColor: '#fca311',
          backgroundColor: 'transparent',
          tension: 0.3
        }]
      },
      options: {
        responsive: true,
        plugins: { legend: { display: true } },
        scales: { y: { beginAtZero: true } }
      }
    });
  </script>
</body>
</html>
