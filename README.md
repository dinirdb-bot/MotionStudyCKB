# MotionStudyCKB
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Motion Study Calculator Pro - CKB</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            min-height: 100vh;
            color: #1e293b;
            line-height: 1.6;
            line-height: 1.6;
   
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .header {
          background: linear-gradient(135deg, #025c5b 0%, #0f4c4b 100%);
            color: white;
            padding: 48px 40px;
            border-radius: 20px;
            margin-bottom: 32px;
            box-shadow: 0 25px 50px -12px rgba(2, 92, 91, 0.25);
            position: relative;
            overflow: hidden;
            
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .content {
            padding: 30px;
        }

        .section {
            margin-bottom: 40px;
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            border: 2px solid #e3f2fd;
        }

        .section-title {
            font-size: 1.875rem;
            font-weight: 700;
            color: #025c5b;
            margin-bottom: 32px;
            padding-bottom: 16px;
            border-bottom: 3px solid #025c5b;
            display: flex;
            align-items: center;
            gap: 16px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        th {
            background: linear-gradient(135deg, #025c5b 0%, #0f4c4b 100%);
            color: white;
            padding: 24px 20px;
            text-align: center;
            font-weight: 600;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            border-bottom: 2px solid #014948;
            position: relative;
        }

        td {
            padding: 12px;
            text-align: center;
            border-bottom: 1px solid #ecf0f1;
        }

        tr:nth-child(even) {
            background-color: #f8f9fa;
        }

        tr:hover {
            background-color: #e3f2fd;
            transition: background-color 0.3s ease;
        }

        input, select {
            width: 100%;
            padding: 8px;
            border: 2px solid #bdc3c7;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s ease;
        }

        input:disabled, select:disabled {
            background: linear-gradient(135deg, #f1f5f9 0%, #e2e8f0 100%);
            color: #64748b;
            cursor: not-allowed;
            opacity: 0.7;
            border-color: #cbd5e1;
        }

        .storage-select.enabled {
            background: white;
            color: #1e293b;
            cursor: pointer;
            opacity: 1;
            border-color: #e5e7eb;
        }

        .btn {
            background: linear-gradient(135deg, #025c5b 0%, #0f4c4b 100%);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 12px;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: 600;
            transition: all 0.3s ease;
            margin: 8px 6px;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            box-shadow: 0 4px 6px -1px rgba(2, 92, 91, 0.3);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 20px 25px -5px rgba(2, 92, 91, 0.4), 0 10px 10px -5px rgba(2, 92, 91, 0.2);
            background: linear-gradient(135deg, #037f7e 0%, #125a59 100%);
        }

        .result-box {
            background: linear-gradient(135deg, #025c5b 0%, #0f4c4b 100%);
            color: white;
            padding: 32px;
            border-radius: 16px;
            text-align: center;
            font-size: 1.25rem;
            font-weight: 600;
            margin-top: 32px;
            box-shadow: 0 25px 50px -12px rgba(2, 92, 91, 0.25);
            position: relative;
            overflow: hidden;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .stat-card {
            background: white;
            padding: 32px 24px;
            border-radius: 20px;
            text-align: center;
            border: 1px solid #e5e7eb;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-number {
            font-size: 2em;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .storage-percentage {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .storage-item {
            background: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            border: 2px solid #34dba6;
        }

        .storage-item h4 {
            color: #2c3e50;
            margin-bottom: 10px;
        }

        .percentage-display {
            font-size: 1.5em;
            font-weight: bold;
            color: #e74c3c;
        }

        .logo-kanan {
            position: absolute;
            top: 45px;
            right: 65px;
            height: 95px;
            z-index: 15;
        }
    </style>
    <body>
        <div class="header">
            <img src="ckb.png" alt="Logo CKB" class="logo-kanan">
            <h1>Motion Study Calculator</h1>
            <p>Sistem Perhitungan Otomatis Kebutuhan Pekerja</p>
        </div>
    </body>
    <div class="container">
        <div class="header">
            <h1>Motion Study Calculator</h1>
            <p>Sistem Perhitungan Otomatis Kebutuhan Pekerja</p>
        </div>

        <div class="content">
            <!-- Motion Study Table -->
            <div class="section">
                <div class="section-title">Tabel Motion Study</div>
                <table id="motionTable">
                    <thead>
                        <tr>
                            <th>Proses/Aktivitas</th>
                            <th>Storage Type</th>
                            <th>Posisi Manpower</th>
                            <th>Durasi (detik) per Line Item</th>
                            <th>Line Item 24 Jam ke-1</th>
                            <th>Line Item 24 Jam ke-2</th>
                            <th>Line Item 24 Jam ke-3</th>
                            <th>Total Waktu 24 Jam ke-1 (detik)</th>
                            <th>Total Waktu 24 Jam ke-2 (detik)</th>
                            <th>Total Waktu 24 Jam ke-3 (detik)</th>
                            <th>Total Durasi (jam)</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="motionTableBody">
                        <tr>
                            <td><input type="text" placeholder="Picking" onchange="updateStorageTypeStatus(this)" /></td>
                            <td>
                                <select class="storage-select" disabled>
                                    <option value="">- Tidak Tersedia -</option>
                                    <option value="kabinet">Kabinet</option>
                                    <option value="raking">Raking</option>
                                    <option value="selving">Selving</option>
                                    <option value="floor">Floor</option>
                                </select>
                            </td>
                            <td><input type="text" placeholder="Picker" /></td>
                            <td><input type="number" placeholder="30" /></td>
                            <td><input type="number" placeholder="100" /></td>
                            <td><input type="number" placeholder="120" /></td>
                            <td><input type="number" placeholder="110" /></td>
                            <td class="total-time-day1">0</td>
                            <td class="total-time-day2">0</td>
                            <td class="total-time-day3">0</td>
                            <td class="total-duration">0</td>
                            <td><button class="btn" onclick="deleteRow(this)">Hapus</button></td>
                        </tr>
                    </tbody>
                </table>
                <button class="btn" onclick="addMotionRow()">+ Tambah Baris</button>
                <button class="btn" onclick="calculateAll()">Hitung Semua</button>
            </div>

            <!-- Line Item Average -->
            <div class="section">
                <div class="section-title">Rata-rata Line Item Per Hari</div>
                <table>
                    <thead>
                        <tr>
                            <th>Rata-rata Line Item Per Hari</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><input type="number" id="averageLineItems" placeholder="110" onchange="calculateAverages()" /></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <!-- Existing Manpower -->
            <div class="section">
                <div class="section-title">Existing Manpower</div>
                <table id="manpowerTable">
                    <thead>
                        <tr>
                            <th>Posisi</th>
                            <th>Jumlah Pekerja</th>
                            <th>Jam Kerja/Hari</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="manpowerTableBody">
                        <tr>
                            <td><input type="text" placeholder="Picker" /></td>
                            <td><input type="number" placeholder="5" /></td>
                            <td><input type="number" placeholder="8" /></td>
                            <td><button class="btn" onclick="deleteRow(this)">Hapus</button></td>
                        </tr>
                    </tbody>
                </table>
                <button class="btn" onclick="addManpowerRow()">+ Tambah Pekerja</button>
            </div>

            <!-- Results -->
            <div class="section">
                <div class="section-title">Hasil Perhitungan Kebutuhan Pekerja</div>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-number" id="totalWorkHours">0</div>
                        <div>Total Jam Kerja Dibutuhkan</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="currentCapacity">0</div>
                        <div>Kapasitas Saat Ini (jam)</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="adminRequired">0</div>
                        <div>Admin Dibutuhkan</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="checkerRequired">0</div>
                        <div>Checker Dibutuhkan</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="binnerRequired">0</div>
                        <div>Binner Dibutuhkan</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="utilizationRate">0%</div>
                        <div>Tingkat Utilisasi</div>
                    </div>
                </div>

                <!-- Worker Position Breakdown -->
                <div class="section-title" style="margin-top: 30px;">Kebutuhan Pekerja per Posisi</div>
                <table>
                    <thead>
                        <tr>
                            <th>Posisi</th>
                            <th>Jam Kerja Dibutuhkan</th>
                            <th>Jumlah Pekerja Existing</th>
                            <th>Jumlah Pekerja Dibutuhkan</th>
                            <th>Selisih (+/-)</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><strong>Admin</strong></td>
                            <td id="adminHours">0</td>
                            <td id="adminExisting">0</td>
                            <td id="adminRequired">0</td>
                            <td id="adminDiff">0</td>
                            <td id="adminStatus">-</td>
                        </tr>
                        <tr>
                            <td><strong>Checker</strong></td>
                            <td id="checkerHours">0</td>
                            <td id="checkerExisting">0</td>
                            <td id="checkerRequired">0</td>
                            <td id="checkerDiff">0</td>
                            <td id="checkerStatus">-</td>
                        </tr>
                        <tr>
                            <td><strong>Binner</strong></td>
                            <td id="binnerHours">0</td>
                            <td id="binnerExisting">0</td>
                            <td id="binnerRequired">0</td>
                            <td id="binnerDiff">0</td>
                            <td id="binnerStatus">-</td>
                        </tr>
                    </tbody>
                </table>

                <div class="result-box" id="recommendation">
                    Masukkan data untuk mendapatkan rekomendasi kebutuhan pekerja
                </div>
            </div>
        </div>
    </div>

    <script>
        function addMotionRow() {
            const tableBody = document.getElementById('motionTableBody');
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
                <td><input type="text" placeholder="Aktivitas Baru" onchange="updateStorageTypeStatus(this)" /></td>
                <td>
                    <select class="storage-select" disabled>
                        <option value="">- Tidak Tersedia -</option>
                        <option value="kabinet">Kabinet</option>
                        <option value="raking">Raking</option>
                        <option value="selving">Selving</option>
                        <option value="floor">Floor</option>
                    </select>
                </td>
                <td><input type="text" placeholder="Posisi" /></td>
                <td><input type="number" placeholder="30" /></td>
                <td><input type="number" placeholder="0" /></td>
                <td><input type="number" placeholder="0" /></td>
                <td><input type="number" placeholder="0" /></td>
                <td class="total-time-day1">0</td>
                <td class="total-time-day2">0</td>
                <td class="total-time-day3">0</td>
                <td class="total-duration">0</td>
                <td><button class="btn" onclick="deleteRow(this)">Hapus</button></td>
            `;
            tableBody.appendChild(newRow);
        }

        function addManpowerRow() {
            const tableBody = document.getElementById('manpowerTableBody');
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
                <td><input type="text" placeholder="Posisi Baru" /></td>
                <td><input type="number" placeholder="1" /></td>
                <td><input type="number" placeholder="8" /></td>
                <td><button class="btn" onclick="deleteRow(this)">Hapus</button></td>
            `;
            tableBody.appendChild(newRow);
        }

        function updateStorageTypeStatus(input) {
            const row = input.closest('tr');
            const storageSelect = row.querySelector('.storage-select');
            const activityValue = input.value.toLowerCase().trim();
            
            if (activityValue.includes('binning') || activityValue.includes('bin')) {
                // Enable storage type selection for binning activities
                storageSelect.disabled = false;
                storageSelect.classList.add('enabled');
                storageSelect.querySelector('option[value=""]').textContent = '- Pilih Storage Type -';
                if (storageSelect.value === '') {
                    storageSelect.value = 'kabinet'; // Default selection
                }
            } else {
                // Disable storage type selection for non-binning activities
                storageSelect.disabled = true;
                storageSelect.classList.remove('enabled');
                storageSelect.value = '';
                storageSelect.querySelector('option[value=""]').textContent = '- Tidak Tersedia -';
            }
        }

        function deleteRow(button) {
            button.closest('tr').remove();
            calculateAll();
        }

        function calculateAverages() {
            const averageItems = parseInt(document.getElementById('averageLineItems').value) || 0;
            // This function now just handles the single average input
            // The value will be used in other calculations as needed
        }

        function calculateAll() {
            // Calculate motion study totals
            const motionRows = document.querySelectorAll('#motionTableBody tr');
            let totalWorkHours = 0;
            let positionHours = { admin: 0, checker: 0, binner: 0 };
            
            motionRows.forEach(row => {
                const cells = row.querySelectorAll('input, select');
                if (cells.length >= 7) {
                    const position = cells[2].value.toLowerCase().trim();
                    const duration = parseFloat(cells[3].value) || 0;
                    const day1 = parseFloat(cells[4].value) || 0;
                    const day2 = parseFloat(cells[5].value) || 0;
                    const day3 = parseFloat(cells[6].value) || 0;
                    
                    const totalSecondsDay1 = duration * day1;
                    const totalSecondsDay2 = duration * day2;
                    const totalSecondsDay3 = duration * day3;
                    
                    const totalHoursDay1 = totalSecondsDay1 / 3600;
                    const totalHoursDay2 = totalSecondsDay2 / 3600;
                    const totalHoursDay3 = totalSecondsDay3 / 3600;
                    const totalHours = totalHoursDay1 + totalHoursDay2 + totalHoursDay3;
                    
                    row.querySelector('.total-time-day1').textContent = totalSecondsDay1.toFixed(0);
                    row.querySelector('.total-time-day2').textContent = totalSecondsDay2.toFixed(0);
                    row.querySelector('.total-time-day3').textContent = totalSecondsDay3.toFixed(0);
                    row.querySelector('.total-duration').textContent = totalHours.toFixed(2);
                    totalWorkHours += totalHours;
                    
                    // Categorize hours by position
                    if (position.includes('admin')) {
                        positionHours.admin += totalHours;
                    } else if (position.includes('checker') || position.includes('check')) {
                        positionHours.checker += totalHours;
                    } else if (position.includes('binner') || position.includes('bin')) {
                        positionHours.binner += totalHours;
                    }
                }
            });

            // Calculate manpower capacity by position
            const manpowerRows = document.querySelectorAll('#manpowerTableBody tr');
            let totalCapacity = 0;
            let existingWorkers = { admin: 0, checker: 0, binner: 0 };
            
            manpowerRows.forEach(row => {
                const cells = row.querySelectorAll('input');
                if (cells.length >= 3) {
                    const position = cells[0].value.toLowerCase().trim();
                    const workers = parseFloat(cells[1].value) || 0;
                    const hoursPerDay = parseFloat(cells[2].value) || 0;
                    
                    // Using standard 85% effectiveness
                    const effectiveCapacity = workers * hoursPerDay * 0.85;
                    totalCapacity += effectiveCapacity;
                    
                    // Count existing workers by position
                    if (position.includes('admin')) {
                        existingWorkers.admin += workers;
                    } else if (position.includes('checker') || position.includes('check')) {
                        existingWorkers.checker += workers;
                    } else if (position.includes('binner') || position.includes('bin')) {
                        existingWorkers.binner += workers;
                    }
                }
            });

            // Calculate requirements per position (assuming 8 hours per day, 85% efficiency)
            const standardHours = 8 * 0.85; // 6.8 effective hours per worker per day
            const requiredWorkers = {
                admin: Math.ceil(positionHours.admin / standardHours),
                checker: Math.ceil(positionHours.checker / standardHours),
                binner: Math.ceil(positionHours.binner / standardHours)
            };

            const totalRequired = requiredWorkers.admin + requiredWorkers.checker + requiredWorkers.binner;
            const utilizationRate = totalCapacity > 0 ? Math.min((totalWorkHours / totalCapacity) * 100, 100) : 0;

            // Update main stats
            document.getElementById('totalWorkHours').textContent = totalWorkHours.toFixed(2);
            document.getElementById('currentCapacity').textContent = totalCapacity.toFixed(2);
            document.getElementById('adminRequired').textContent = requiredWorkers.admin;
            document.getElementById('checkerRequired').textContent = requiredWorkers.checker;
            document.getElementById('binnerRequired').textContent = requiredWorkers.binner;
            document.getElementById('utilizationRate').textContent = utilizationRate.toFixed(1) + '%';

            // Update position breakdown
            updatePositionBreakdown('admin', positionHours.admin, existingWorkers.admin, requiredWorkers.admin);
            updatePositionBreakdown('checker', positionHours.checker, existingWorkers.checker, requiredWorkers.checker);
            updatePositionBreakdown('binner', positionHours.binner, existingWorkers.binner, requiredWorkers.binner);

            // Generate recommendation
            let recommendation = '';
            const totalDeficit = Math.max(0, totalRequired - (existingWorkers.admin + existingWorkers.checker + existingWorkers.binner));
            
            if (totalDeficit > 0) {
                recommendation = `⚠️ KEKURANGAN PEKERJA: Dibutuhkan tambahan ${totalDeficit} pekerja total!`;
                
                const details = [];
                if (requiredWorkers.admin > existingWorkers.admin) {
                    details.push(`Admin: +${requiredWorkers.admin - existingWorkers.admin}`);
                }
                if (requiredWorkers.checker > existingWorkers.checker) {
                    details.push(`Checker: +${requiredWorkers.checker - existingWorkers.checker}`);
                }
                if (requiredWorkers.binner > existingWorkers.binner) {
                    details.push(`Binner: +${requiredWorkers.binner - existingWorkers.binner}`);
                }
                
                if (details.length > 0) {
                    recommendation += ` Detail: ${details.join(', ')}`;
                }
            } else if (utilizationRate < 70) {
                recommendation = `✅ KAPASITAS BERLEBIH: Utilisasi rendah (${utilizationRate.toFixed(1)}%), pertimbangkan optimasi atau redistribusi pekerja.`;
            } else {
                recommendation = `✅ KAPASITAS OPTIMAL: Jumlah pekerja saat ini mencukupi dengan utilisasi ${utilizationRate.toFixed(1)}%.`;
            }
            
            document.getElementById('recommendation').textContent = recommendation;
            
            // Update other calculations
            calculateAverages();
        }

        function updatePositionBreakdown(position, hours, existing, required) {
            document.getElementById(position + 'Hours').textContent = hours.toFixed(2);
            document.getElementById(position + 'Existing').textContent = existing;
            document.getElementById(position + 'Required').textContent = required;
            
            const diff = required - existing;
            const diffElement = document.getElementById(position + 'Diff');
            const statusElement = document.getElementById(position + 'Status');
            
            diffElement.textContent = diff > 0 ? '+' + diff : diff.toString();
            
            if (diff > 0) {
                diffElement.style.color = '#e74c3c';
                statusElement.textContent = 'KURANG';
                statusElement.style.color = '#e74c3c';
                statusElement.style.fontWeight = 'bold';
            } else if (diff < 0) {
                diffElement.style.color = '#f39c12';
                statusElement.textContent = 'BERLEBIH';
                statusElement.style.color = '#f39c12';
                statusElement.style.fontWeight = 'bold';
            } else {
                diffElement.style.color = '#27ae60';
                statusElement.textContent = 'SESUAI';
                statusElement.style.color = '#27ae60';
                statusElement.style.fontWeight = 'bold';
            }
        }

        function getTotalManpower() {
            const manpowerRows = document.querySelectorAll('#manpowerTableBody tr');
            let total = 0;
            manpowerRows.forEach(row => {
                const workerInput = row.querySelectorAll('input')[1];
                total += parseFloat(workerInput.value) || 0;
            });
            return total || 1;
        }

        // Initialize calculations
        window.onload = function() {
            calculateAll();
            // Initialize storage type status for existing rows
            document.querySelectorAll('#motionTableBody input[type="text"]').forEach(input => {
                if (input.placeholder === 'Picking') {
                    updateStorageTypeStatus(input);
                }
            });
        };

        // Add event listeners for real-time calculation
        document.addEventListener('input', function(e) {
            if (e.target.tagName === 'INPUT' || e.target.tagName === 'SELECT') {
                setTimeout(calculateAll, 100);
            }
        });
    </script>
</body>
</html>
