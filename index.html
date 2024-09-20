<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apuestas Diarias</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        .highlight {
            background-color: #add8e6; /* Light blue highlight */
        }
    </style>
</head>

<body>
    <div class="container">
        <h1>Cálculo de Apuestas Diarias</h1>
        <form method="POST">
            <label for="inversion">Inversión Inicial (MXN):</label>
            <input type="number" name="inversion" id="inversion" required placeholder="Introduce el valor de la inversión inicial" value="<?php echo isset($_POST['inversion']) ? $_POST['inversion'] : ''; ?>">

            <label for="porcentaje">Porcentaje de Ganancia (%):</label>
            <input type="number" step="0.01" name="porcentaje" id="porcentaje" required placeholder="Introduce el porcentaje de ganancia" value="<?php echo isset($_POST['porcentaje']) ? $_POST['porcentaje'] : ''; ?>">

            <label for="dias">Número de Días:</label>
            <input type="number" name="dias" id="dias" required placeholder="Introduce el número de días" value="<?php echo isset($_POST['dias']) ? $_POST['dias'] : ''; ?>">

            <button type="submit">Calcular</button>
        </form>

        <?php
            if ($_SERVER["REQUEST_METHOD"] == "POST") {
                $inversionInicial = $_POST['inversion'];
                $porcentaje = $_POST['porcentaje'] / 100; // Convert percentage input to decimal
                $totalDias = $_POST['dias']; // Use the input number of days
                $resultados = [];

                $dias = [];
                $gananciasDia = [];
                $saldosDia = [];

                // Set initial meta values
                $meta = $inversionInicial * 2; // First goal is double the initial investment
                $metas = [$meta]; // Array to keep track of each goal

                for ($dia = 1; $dia <= $totalDias; $dia++) {
                    if ($dia == 1) {
                        $inversion = $inversionInicial;
                    } else {
                        $inversion = $resultados[$dia - 2]['saldoDia'];
                    }

                    // Cálculos para la 1ra apuesta
                    $ganancia1 = round($inversion * $porcentaje, 2);
                    $saldo1 = round($inversion + $ganancia1, 2);

                    // Cálculos para la 2da apuesta
                    $ganancia2 = round($saldo1 * $porcentaje, 2);
                    $saldo2 = round($saldo1 + $ganancia2, 2);

                    // Cálculos para la 3ra apuesta
                    $ganancia3 = round($saldo2 * $porcentaje, 2);
                    $saldo3 = round($saldo2 + $ganancia3, 2);

                    // Cálculos del día
                    $gananciaDia = round($ganancia1 + $ganancia2 + $ganancia3, 2);
                    $saldoDia = round($saldo3, 2);

                    $resultados[] = [
                        'dia' => $dia,
                        'ganancia1' => $ganancia1,
                        'saldo1' => $saldo1,
                        'ganancia2' => $ganancia2,
                        'saldo2' => $saldo2,
                        'ganancia3' => $ganancia3,
                        'saldo3' => $saldo3,
                        'gananciaDia' => $gananciaDia,
                        'saldoDia' => $saldoDia
                    ];

                    // Save data for the graph
                    $dias[] = $dia;
                    $gananciasDia[] = $gananciaDia;
                    $saldosDia[] = $saldoDia;

                    // Check if the current saldo meets or exceeds the next goal
                    if ($saldoDia >= $metas[count($metas) - 1]) {
                        // Set new goal by doubling the previous one
                        $metas[] = end($metas) * 2;
                    }
                }

                echo "<table class='results-table'>";
                echo "<tr>
                        <th>Día</th>
                        <th>Ganancia 1ra Apuesta (MXN)</th>
                        <th>Saldo 1ra Apuesta (MXN)</th>
                        <th>Ganancia 2da Apuesta (MXN)</th>
                        <th>Saldo 2da Apuesta (MXN)</th>
                        <th>Ganancia 3ra Apuesta (MXN)</th>
                        <th>Saldo 3ra Apuesta (MXN)</th>
                        <th>Ganancia del Día (MXN)</th>
                        <th>Saldo del Día (MXN)</th>
                      </tr>";
                foreach ($resultados as $fila) {
                    // Highlight rows where Saldo del Día meets any defined goal
                    $row_class = in_array($fila['saldoDia'], $metas) ? 'highlight' : '';
                    echo "<tr class='$row_class'>
                            <td>{$fila['dia']}</td>
                            <td>$" . number_format($fila['ganancia1'], 2) . "</td>
                            <td>$" . number_format($fila['saldo1'], 2) . "</td>
                            <td>$" . number_format($fila['ganancia2'], 2) . "</td>
                            <td>$" . number_format($fila['saldo2'], 2) . "</td>
                            <td>$" . number_format($fila['ganancia3'], 2) . "</td>
                            <td>$" . number_format($fila['saldo3'], 2) . "</td>
                            <td>$" . number_format($fila['gananciaDia'], 2) . "</td>
                            <td>$" . number_format($fila['saldoDia'], 2) . "</td>
                          </tr>";
                }
                echo "</table>";
            }
        ?>

        <!-- Graph Section -->
        <canvas id="resultChart" width="400" height="200"></canvas>
        <script>
            const ctx = document.getElementById('resultChart').getContext('2d');
            const chart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: <?php echo json_encode($dias); ?>,
                    datasets: [{
                        label: 'Ganancia del Día (MXN)',
                        data: <?php echo json_encode($gananciasDia); ?>,
                        borderColor: 'rgba(75, 192, 192, 1)',
                        fill: false,
                    }, {
                        label: 'Saldo del Día (MXN)',
                        data: <?php echo json_encode($saldosDia); ?>,
                        borderColor: 'rgba(153, 102, 255, 1)',
                        fill: false,
                    }]
                },
                options: {
                    responsive: true,
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        title: {
                            display: true,
                            text: 'Resultados de Apuestas Diarias'
                        }
                    },
                    scales: {
                        x: {
                            display: true,
                            title: {
                                display: true,
                                text: 'Día'
                            }
                        },
                        y: {
                            display: true,
                            title: {
                                display: true,
                                text: 'Valores (MXN)'
                            }
                        }
                    }
                }
            });
        </script>
    </div>

<div class="container">
    <h1>Análisis del Crecimiento de la Inversión</h1>
    <table class="results-table">
        <thead>
            <tr>
                <th>Día</th>
                <th>Valor de la Inversión</th>
            </tr>
        </thead>
        <tbody>
            <tr><td>36</td><td>Duplicas tu dinero</td></tr>
            <tr><td>57</td><td>Triplicas tu dinero</td></tr>
            <tr><td>72</td><td>Cuadruplicas tu dinero</td></tr>
            <tr><td>83</td><td>Quintuplicas tu dinero</td></tr>
            <tr><td>93</td><td>Sextuplicas tu dinero</td></tr>
        </tbody>
    </table>
</div>

</body>
</html>
