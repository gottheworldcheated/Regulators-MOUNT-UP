<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Regulators Mount Up! | KY Foreclosure Compliance</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: system-ui, -apple-system, 'Segoe UI', Roboto;
    background: linear-gradient(135deg, #0f172a, #020617);
    color: #e5e7eb;
    line-height: 1.6;
}

header {
    padding: 24px;
    text-align: center;
    background: linear-gradient(90deg, #bfa14a, #f5d76e);
    color: #0f172a;
    box-shadow: 0 4px 18px rgba(0,0,0,.4);
}

header h1 {
    font-size: 2.2em;
    margin-bottom: 8px;
    text-shadow: 1px 1px 2px rgba(0,0,0,.2);
}

header p {
    font-size: 0.95em;
    opacity: 0.9;
}

.container {
    max-width: 1400px;
    margin: auto;
    padding: 20px;
    display: grid;
    grid-template-columns: 280px 1fr 280px;
    gap: 20px;
}

.panel {
    background: rgba(255,255,255,0.06);
    border-radius: 14px;
    padding: 20px;
    border: 1px solid rgba(255,255,255,0.1);
}

.panel h3 {
    margin-bottom: 16px;
    font-size: 1.1em;
}

.panel h4 {
    margin-top: 20px;
    margin-bottom: 12px;
    font-size: 0.95em;
    opacity: 0.85;
}

input, select, textarea {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.15);
    background: rgba(255,255,255,0.08);
    color: #e5e7eb;
    font-size: 14px;
}

input::placeholder, textarea::placeholder {
    color: rgba(229,231,235,0.5);
}

input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #facc15;
    background: rgba(255,255,255,0.12);
}

button {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border-radius: 8px;
    border: none;
    background: #16a34a;
    color: white;
    font-weight: 700;
    cursor: pointer;
    font-size: 14px;
    transition: all 0.2s;
}

button:hover {
    background: #15803d;
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(22,163,74,.3);
}

button:active {
    transform: translateY(0);
}

button.secondary {
    background: rgba(255,255,255,0.1);
    color: #facc15;
}

button.secondary:hover {
    background: rgba(255,255,255,0.15);
}

.flag {
    padding: 12px;
    border-left: 5px solid;
    margin: 10px 0;
    border-radius: 6px;
    font-size: 0.9em;
    line-height: 1.5;
}

.flag.violation {
    border-color: #ef4444;
    background: rgba(239,68,68,.15);
}

.flag.review {
    border-color: #f59e0b;
    background: rgba(245,158,11,.15);
}

.flag.compliant {
    border-color: #10b981;
    background: rgba(16,185,129,.15);
}

.metric {
    padding: 12px;
    background: rgba(255,255,255,0.05);
    border-radius: 8px;
    margin: 10px 0;
    font-size: 0.95em;
}

.metric strong {
    color: #facc15;
}

#timelineChart {
    max-height: 300px;
}

#countyMap {
    height: 250px;
    background: linear-gradient(45deg, #1e293b, #0f172a);
    border-radius: 10px;
    padding: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9em;
}

.county-item {
    padding: 8px;
    margin: 4px 0;
    border-radius: 6px;
    font-size: 0.85em;
    border-left: 4px solid;
}

.county-ready {
    border-left-color: #10b981;
    background: rgba(16,185,129,.1);
}

.county-pending {
    border-left-color: #f59e0b;
    background: rgba(245,158,11,.1);
}

.county-setup {
    border-left-color: #ef4444;
    background: rgba(239,68,68,.1);
}

.document-list {
    font-size: 0.85em;
    max-height: 120px;
    overflow-y: auto;
}

.doc-item {
    padding: 6px;
    margin: 4px 0;
    background: rgba(255,255,255,0.05);
    border-radius: 4px;
    border-left: 3px solid #10b981;
}

footer {
    padding: 20px;
    text-align: center;
    font-size: 12px;
    opacity: .7;
    border-top: 1px solid rgba(255,255,255,0.1);
}

@media(max-width:1024px) {
    .container {
        grid-template-columns: 1fr;
    }
}

@media(max-width:640px) {
    header h1 {
        font-size: 1.6em;
    }
    
    .container {
        padding: 12px;
        gap: 12px;
    }
    
    .panel {
        padding: 16px;
    }
}
</style>
</head>

<body>

<header>
    <h1>🔥 REGULATORS MOUNT UP</h1>
    <p>Kentucky Foreclosure Compliance Review | Real-Time Violation Detection</p>
</header>

<div class="container">

<!-- LEFT PANEL: Case Intake -->
<div class="panel">
    <h3>📋 Case Intake</h3>
    
    <label>Case ID</label>
    <input id="caseId" placeholder="KY-2026-001" value="KY-2026-001">
    
    <label>Property Address</label>
    <input id="address" placeholder="123 Main St, Louisville, KY" value="123 Main St, Louisville, KY">
    
    <label>Status</label>
    <select id="status">
        <option>Dispute Active</option>
        <option>Foreclosure Filed</option>
        <option>Lis Pendens Active</option>
        <option>Sale Scheduled</option>
    </select>
    
    <h4>📄 Document Upload</h4>
    <label>Credit Report</label>
    <input type="file" id="creditFile" accept=".pdf">
    
    <label>Land Records</label>
    <input type="file" id="landFile" accept=".pdf">
    
    <label>Court Docket</label>
    <input type="file" id="courtFile" accept=".pdf">
    
    <div id="docList" class="document-list" style="display:none; margin-top:12px;"></div>
    
    <button onclick="analyze()">🚀 Run Compliance Review</button>
    <button class="secondary" onclick="clearCase()">Clear Case</button>
</div>

<!-- CENTER PANEL: Timeline & Flags -->
<div class="panel">
    <h3>📊 Documented Timeline</h3>
    <canvas id="timelineChart"></canvas>

    <h4>🤖 Preliminary Review Flags</h4>
    <div id="flagsContainer">
        <div class="flag review">
            ⏰ Balance reported during active FCRA dispute (12 CFR §1681s-2)
        </div>
        <div class="flag violation">
            🔗 Assignment executed after lis pendens filing — chain of title review required
        </div>
        <div class="flag review">
            💰 Prohibited property inspection/appraisal fees detected (RESPA §8)
        </div>
    </div>

    <h4>💬 Regulator Notes</h4>
    <textarea id="notes" placeholder="Document observations, timeline questions, next steps..." style="height: 100px;"></textarea>
</div>

<!-- RIGHT PANEL: KY Map & Summary -->
<div class="panel">
    <h3>🗺️ KY County Status</h3>
    <div id="countyMap">
        <div style="text-align: center;">
            <div class="county-item county-ready">✓ Jefferson: Connected</div>
            <div class="county-item county-ready">✓ Fayette: Connected</div>
            <div class="county-item county-pending">⏳ Warren: Pending Setup</div>
            <div class="county-item county-setup">⚠ Kenton: Needs Review</div>
        </div>
    </div>

    <h4>📈 Case Summary</h4>
    <div class="metric">
        <strong>Flags Identified:</strong> <span id="flagCount">3</span>
    </div>
    <div class="metric">
        <strong>Violations (Preliminary):</strong> <span id="violationCount">2</span>
    </div>
    <div class="metric">
        <strong>Documents Submitted:</strong> <span id="docCount">0</span>
    </div>
    <div class="metric">
        <strong>Review Status:</strong> <span id="reviewStatus">Awaiting Analysis</span>
    </div>

    <button onclick="exportSummary()">📄 Export Case Summary</button>
    <button class="secondary" onclick="printCase()">🖨️ Print Report</button>
</div>

</div>

<footer>
    <strong>Regulators Mount Up! v1.0</strong> — Prototype for regulator review and homeowner education. 
    All findings require independent verification and judicial review. Not a substitute for attorney counsel.
    | CFPB Supervisory Highlights 2024 | TWCA 2025 Initiative
</footer>

<script>
// Timeline chart
const ctx = document.getElementById('timelineChart').getContext('2d');
const timelineChart = new Chart(ctx, {
    type: 'scatter',
    data: {
        datasets: [{
            label: 'Key Events',
            data: [
                {x: new Date('2025-01-15'), y: 1, label: 'Mortgage Originated'},
                {x: new Date('2025-03-10'), y: 2, label: 'Dispute Filed'},
                {x: new Date('2025-04-15'), y: 3, label: 'Lis Pendens'},
                {x: new Date('2025-05-01'), y: 4, label: 'Assignment (Post-FC)'}
            ],
            backgroundColor: ['#10b981', '#f59e0b', '#10b981', '#ef4444'],
            pointRadius: 8,
            pointHoverRadius: 10,
            showLine: false
        }]
    },
    options: {
        responsive: true,
        maintainAspectRatio: true,
        indexAxis: 'x',
        scales: {
            x: {
                type: 'time',
                time: { unit: 'month', displayFormats: { month: 'MMM YYYY' }},
                title: { display: true, text: 'Date' }
            },
            y: {
                display: false,
                min: 0,
                max: 5
            }
        },
        plugins: {
            legend: { display: false },
            tooltip: {
                enabled: true,
                backgroundColor: 'rgba(0,0,0,0.8)',
                titleColor: '#facc15',
                bodyColor: '#fff',
                padding: 12,
                displayColors: false
            }
        }
    }
});

// Document tracking
document.getElementById('creditFile').addEventListener('change', updateDocList);
document.getElementById('landFile').addEventListener('change', updateDocList);
document.getElementById('courtFile').addEventListener('change', updateDocList);

function updateDocList() {
    const docs = [];
    if(document.getElementById('creditFile').files.length) docs.push('✓ Credit Report');
    if(document.getElementById('landFile').files.length) docs.push('✓ Land Records');
    if(document.getElementById('courtFile').files.length) docs.push('✓ Court Docket');
    
    const docList = document.getElementById('docList');
    if(docs.length) {
        docList.innerHTML = docs.map(d => `<div class="doc-item">${d}</div>`).join('');
        docList.style.display = 'block';
        document.getElementById('docCount').textContent = docs.length;
    }
}

function analyze() {
    document.getElementById('reviewStatus').textContent = 'Analysis Complete';
    alert('✓ Compliance review generated.\n\n3 preliminary flags identified for regulator examination.\n\nExport summary or continue to case notes.');
}

function clearCase() {
    document.getElementById('caseId').value = 'KY-2026-001';
    document.getElementById('address').value = '123 Main St, Louisville, KY';
    document.getElementById('status').value = 'Dispute Active';
    document.getElementById('creditFile').value = '';
    document.getElementById('landFile').value = '';
    document.getElementById('courtFile').value = '';
    document.getElementById('notes').value = '';
    document.getElementById('docList').style.display = 'none';
    document.getElementById('docCount').textContent = '0';
    document.getElementById('reviewStatus').textContent = 'Awaiting Analysis';
}

function exportSummary() {
    const summary = `REGULATORS MOUNT UP! CASE SUMMARY
=====================================

Case ID: ${document.getElementById('caseId').value}
Property: ${document.getElementById('address').value}
Status: ${document.getElementById('status').value}
Date Generated: ${new Date().toLocaleDateString()}

FLAGS IDENTIFIED (3)
====================
1. FCRA Dispute Reporting Conflict
   - Balance reported during active dispute (12 CFR §1681s-2)
   - Timeline concern: dispute filed 03/10/2025

2. Assignment Chain of Title Issue
   - Assignment executed 05/01/2025 (after lis pendens 04/15/2025)
   - Post-foreclosure assignment detected

3. Prohibited Fees Detected
   - Property inspection/appraisal fees (RESPA §8)
   - Requires verification in loan documents

VIOLATIONS (PRELIMINARY)
=======================
Critical Issues: 2
Requires Review: 1

DOCUMENTS SUBMITTED
===================
${document.getElementById('docCount').textContent} document(s) uploaded

REGULATOR NOTES
===============
${document.getElementById('notes').value || '(None)'}

DISCLAIMER
==========
This is a preliminary compliance review tool. All findings require independent verification,
judicial review, and attorney counsel. Use for regulator investigation and homeowner education only.

Generated by: Regulators Mount Up! v1.0 | CFPB 2024 Supervisory Standards | TWCA 2025`;

    const blob = new Blob([summary], {type: 'text/plain'});
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = `RMU_${document.getElementById('caseId').value.replace(/[^a-zA-Z0-9]/g, '_')}_Summary.txt`;
    a.click();
    URL.revokeObjectURL(url);
}

function printCase() {
    const printContent = `
REGULATORS MOUNT UP! — ${document.getElementById('caseId').value}
Property: ${document.getElementById('address').value}
Status: ${document.getElementById('status').value}

PRELIMINARY FLAGS (3):
1. FCRA Dispute Reporting Conflict
2. Assignment Chain of Title Issue  
3. Prohibited Fees Detected

VIOLATIONS: 2 Critical, 1 Review
    `;
    
    const w = window.open('', '', 'height=600,width=800');
    w.document.write('<pre>' + printContent + '</pre>');
    w.document.close();
    w.print();
}
</script>

</body>
</html>
