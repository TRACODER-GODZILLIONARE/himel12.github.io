# himel12.github.io
An HTML-based learning module with embedded visuals and interactive content.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GATE Examination - Network Circuit Analysis</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 10px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .header h1 {
            font-size: 24px;
        }
        
        .timer {
            font-size: 28px;
            font-weight: bold;
            background: rgba(255,255,255,0.2);
            padding: 10px 20px;
            border-radius: 5px;
        }
        
        .welcome-screen {
            padding: 60px;
            text-align: center;
        }
        
        .welcome-screen h2 {
            color: #1e3c72;
            font-size: 32px;
            margin-bottom: 30px;
        }
        
        .exam-info {
            background: #f8f9fa;
            padding: 30px;
            border-radius: 10px;
            margin: 30px 0;
            text-align: left;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .exam-info h3 {
            color: #2a5298;
            margin-bottom: 15px;
        }
        
        .exam-info ul {
            list-style: none;
            padding-left: 0;
        }
        
        .exam-info li {
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
        }
        
        .exam-info li:last-child {
            border-bottom: none;
        }
        
        .start-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 15px 50px;
            font-size: 20px;
            border-radius: 50px;
            cursor: pointer;
            margin-top: 30px;
            transition: transform 0.3s;
        }
        
        .start-btn:hover {
            transform: scale(1.05);
        }
        
        .main-content {
            display: none;
            padding: 30px;
        }
        
        .content-wrapper {
            display: flex;
            gap: 20px;
        }
        
        .question-area {
            flex: 1;
            background: #f8f9fa;
            padding: 30px;
            border-radius: 10px;
            min-height: 500px;
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #ddd;
        }
        
        .question-number {
            font-size: 18px;
            font-weight: bold;
            color: #2a5298;
        }
        
        .question-marks {
            background: #ffc107;
            color: #333;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: bold;
        }
        
        .question-text {
            font-size: 16px;
            line-height: 1.8;
            margin-bottom: 25px;
            color: #333;
        }
        
        .question-image {
            max-width: 100%;
            margin: 20px 0;
            border: 2px solid #ddd;
            border-radius: 5px;
        }
        
        .options {
            margin: 20px 0;
        }
        
        .option {
            background: white;
            padding: 15px;
            margin: 10px 0;
            border: 2px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .option:hover {
            border-color: #667eea;
            transform: translateX(5px);
        }
        
        .option.selected {
            background: #667eea;
            color: white;
            border-color: #667eea;
        }
        
        .option input[type="radio"] {
            margin-right: 10px;
        }
        
        .numerical-input {
            width: 200px;
            padding: 12px;
            font-size: 16px;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin: 20px 0;
        }
        
        .navigation-buttons {
            display: flex;
            gap: 15px;
            margin-top: 30px;
        }
        
        .nav-btn {
            padding: 12px 30px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .save-next-btn {
            background: #28a745;
            color: white;
        }
        
        .save-next-btn:hover {
            background: #218838;
        }
        
        .prev-btn {
            background: #6c757d;
            color: white;
        }
        
        .prev-btn:hover {
            background: #5a6268;
        }
        
        .sidebar {
            width: 300px;
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            position: sticky;
            top: 20px;
            height: fit-content;
            max-height: calc(100vh - 200px);
            overflow-y: auto;
        }
        
        .calculator-btn {
            width: 100%;
            padding: 12px;
            background: #17a2b8;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            margin-bottom: 20px;
            transition: all 0.3s;
        }
        
        .calculator-btn:hover {
            background: #138496;
        }
        
        .question-palette {
            margin-top: 20px;
        }
        
        .question-palette h3 {
            color: #2a5298;
            margin-bottom: 15px;
            font-size: 16px;
        }
        
        .palette-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 8px;
        }
        
        .palette-btn {
            padding: 10px;
            border: 2px solid #ddd;
            background: white;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .palette-btn:hover {
            transform: scale(1.1);
        }
        
        .palette-btn.attempted {
            background: #28a745;
            color: white;
            border-color: #28a745;
        }
        
        .palette-btn.unattempted {
            background: white;
            color: #333;
            border-color: #ddd;
        }
        
        .palette-btn.current {
            background: #ffc107;
            color: #333;
            border-color: #ffc107;
        }
        
        .legend {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #ddd;
        }
        
        .legend-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 12px;
        }
        
        .legend-box {
            width: 20px;
            height: 20px;
            border-radius: 3px;
        }
        
        .submit-btn {
            width: 100%;
            padding: 15px;
            background: #dc3545;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            margin-top: 20px;
            transition: all 0.3s;
        }
        
        .submit-btn:hover {
            background: #c82333;
        }
        
        .reset-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            padding: 8px 16px;
            background: #6c757d;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s;
        }
        
        .reset-btn:hover {
            background: #5a6268;
        }
        
        .print-btn {
            position: fixed;
            bottom: 20px;
            right: 100px;
            padding: 8px 16px;
            background: #17a2b8;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s;
            display: none;
        }
        
        .print-btn:hover {
            background: #138496;
        }
        
        @media print {
            .header, .reset-btn, .print-btn, .sidebar {
                display: none !important;
            }
            .content-wrapper {
                display: block !important;
            }
            .question-area {
                width: 100% !important;
                max-width: 100% !important;
            }
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: white;
            padding: 40px;
            border-radius: 10px;
            text-align: center;
            max-width: 400px;
        }
        
        .modal-content h3 {
            color: #2a5298;
            margin-bottom: 20px;
        }
        
        .modal-content input {
            width: 100%;
            padding: 12px;
            margin: 20px 0;
            border: 2px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        
        .modal-content button {
            padding: 12px 30px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        
        .calculator {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
            z-index: 999;
        }
        
        .calc-display {
            width: 100%;
            padding: 15px;
            font-size: 24px;
            text-align: right;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin-bottom: 15px;
            background: #f8f9fa;
        }
        
        .calc-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        
        .calc-btn {
            padding: 15px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background: #e9ecef;
            transition: all 0.3s;
        }
        
        .calc-btn:hover {
            background: #667eea;
            color: white;
        }
        
        .calc-btn.operator {
            background: #ffc107;
        }
        
        .calc-btn.equals {
            background: #28a745;
            color: white;
            grid-column: span 2;
        }
        
        .calc-close {
            width: 100%;
            padding: 10px;
            background: #dc3545;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Graduate Aptitude Test in Engineering (GATE)</h1>
            <div class="timer" id="timer">00:00:00</div>
        </div>
        
        <div class="welcome-screen" id="welcomeScreen">
            <h2>Network Circuit Analysis</h2>
            <div class="exam-info">
                <h3>Examination Details</h3>
                <ul>
                    <li><strong>Total Duration:</strong> 90 Minutes</li>
                    <li><strong>Total Questions:</strong> 30</li>
                    <li><strong>Total Marks:</strong> 50</li>
                    <li><strong>Questions 1-10:</strong> 1 Mark each</li>
                    <li><strong>Questions 11-30:</strong> 2 Marks each</li>
                </ul>
                <h3 style="margin-top: 25px;">Marking Scheme</h3>
                <ul>
                    <li><strong>1 Mark Questions:</strong> -1/3 mark for wrong answer</li>
                    <li><strong>2 Mark Questions:</strong> -2/3 mark for wrong answer</li>
                    <li><strong>No negative marking</strong> for numerical answer type questions</li>
                </ul>
            </div>
            <button class="start-btn" onclick="startExam()">START EXAMINATION</button>
        </div>
        
        <div class="main-content" id="mainContent">
            <div class="content-wrapper">
                <div class="question-area" id="questionArea"></div>
                
                <div class="sidebar">
                    <button class="calculator-btn" onclick="toggleCalculator()">
                        🧮 Scientific Calculator
                    </button>
                    
                    <div class="question-palette">
                        <h3>Question Palette</h3>
                        <div class="palette-grid" id="paletteGrid"></div>
                    </div>
                    
                    <div class="legend">
                        <div class="legend-item">
                            <div class="legend-box" style="background: #28a745;"></div>
                            <span>Attempted</span>
                        </div>
                        <div class="legend-item">
                            <div class="legend-box" style="background: white; border: 2px solid #ddd;"></div>
                            <span>Unattempted</span>
                        </div>
                        <div class="legend-item">
                            <div class="legend-box" style="background: #ffc107;"></div>
                            <span>Current</span>
                        </div>
                    </div>
                    
                    <button class="submit-btn" onclick="submitExam()">SUBMIT EXAM</button>
                </div>
            </div>
        </div>
    </div>
    
    <button class="reset-btn" onclick="resetExam()">RESET</button>
    <button class="print-btn" id="printBtn" onclick="printResponses()">PRINT RESPONSES</button>
    
    <div class="modal" id="passwordModal">
        <div class="modal-content">
            <h3>Exam Completed</h3>
            <p>Enter password to view your responses</p>
            <input type="password" id="passwordInput" placeholder="Enter password">
            <button onclick="checkPassword()">Submit</button>
        </div>
    </div>
    
    <div class="modal" id="resetPasswordModal">
        <div class="modal-content">
            <h3>Reset Confirmation</h3>
            <p>Enter password to reset exam</p>
            <input type="password" id="resetPasswordInput" placeholder="Enter reset password">
            <div style="display: flex; gap: 10px; margin-top: 20px;">
                <button onclick="confirmReset()" style="background: #dc3545;">Confirm Reset</button>
                <button onclick="closeResetModal()">Cancel</button>
            </div>
        </div>
    </div>
    
    <div class="calculator" id="calculator">
        <input type="text" class="calc-display" id="calcDisplay" readonly>
        <div class="calc-buttons">
            <button class="calc-btn" onclick="calcAppend('7')">7</button>
            <button class="calc-btn" onclick="calcAppend('8')">8</button>
            <button class="calc-btn" onclick="calcAppend('9')">9</button>
            <button class="calc-btn operator" onclick="calcAppend('/')">/</button>
            <button class="calc-btn" onclick="calcAppend('4')">4</button>
            <button class="calc-btn" onclick="calcAppend('5')">5</button>
            <button class="calc-btn" onclick="calcAppend('6')">6</button>
            <button class="calc-btn operator" onclick="calcAppend('*')">*</button>
            <button class="calc-btn" onclick="calcAppend('1')">1</button>
            <button class="calc-btn" onclick="calcAppend('2')">2</button>
            <button class="calc-btn" onclick="calcAppend('3')">3</button>
            <button class="calc-btn operator" onclick="calcAppend('-')">-</button>
            <button class="calc-btn" onclick="calcAppend('0')">0</button>
            <button class="calc-btn" onclick="calcAppend('.')">.</button>
            <button class="calc-btn equals" onclick="calcEqual()">=</button>
            <button class="calc-btn operator" onclick="calcAppend('+')">+</button>
            <button class="calc-btn" onclick="calcClear()">C</button>
            <button class="calc-btn" onclick="calcAppend('Math.sqrt(')">√</button>
            <button class="calc-btn" onclick="calcAppend('Math.pow(')">^</button>
            <button class="calc-btn" onclick="calcAppend('Math.sin(')">sin</button>
            <button class="calc-btn" onclick="calcAppend('Math.cos(')">cos</button>
            <button class="calc-btn" onclick="calcAppend('Math.tan(')">tan</button>
            <button class="calc-btn" onclick="calcAppend('Math.log(')">log</button>
            <button class="calc-btn" onclick="calcAppend('(')}">(</button>
            <button class="calc-btn" onclick="calcAppend(')')">)</button>
            <button class="calc-btn" onclick="calcAppend('Math.PI')">π</button>
            <button class="calc-btn" onclick="calcAppend('Math.E')">e</button>
        </div>
        <button class="calc-close" onclick="toggleCalculator()">Close</button>
    </div>

    <script>
        const questions = [
            {
                id: 1,
                marks: 1,
                text: "A circuit has Thevenin equivalent Vth = 20∠45° V and Zth = 5 + j5 Ω. Calculate the maximum power delivered to a load in watt",
                type: "numerical"
            },
            {
                id: 2,
                marks: 1,
                text: "In a reciprocal network, when a 10V source is connected between terminals A-B, the current through a branch between terminals C-D is 0.5A. If the same 10V source is now connected between terminals C-D, what will be the current through the branch between terminals A-B?",
                type: "mcq",
                options: ["0.25 A", "0.5 A", "1 A", "2 A"]
            },
            {
                id: 3,
                marks: 1,
                text: "A load draws 100W at 0.8 power factor lagging. The reactive power consumed is",
                type: "mcq",
                options: ["60 VAR", "75 VAR", "80 VAR", "125 VAR"]
            },
            {
                id: 4,
                marks: 1,
                text: "For a series RLC circuit with R = 2Ω, L = 1H, C = 0.5F, the characteristic equation in s-domain is s² + as + b = 0. The value of 'a' is:",
                type: "numerical"
            },
            {
                id: 5,
                marks: 1,
                text: "In a circuit with 'n' nodes and 'b' branches, if there are 'v' independent voltage sources, the number of independent node equations that can be written using nodal analysis is:",
                type: "mcq",
                options: ["n - 1 - v", "n - v", "b - n + 1", "n - 1"]
            },
            {
                id: 6,
                marks: 1,
                text: "In an AC circuit, if the complex power S = 300 + j400 VA, the power factor is:",
                type: "mcq",
                options: ["0.6 lagging", "0.8 lagging", "0.6 leading", "0.8 leading"]
            },
            {
                id: 7,
                marks: 1,
                text: "In a series RLC circuit, the condition for critical damping is:",
                type: "mcq",
                options: ["R = 2√(L/C)", "R = √(L/C)", "R = √(4L/C)", "R = 2√(L·C)"]
            },
            {
                id: 8,
                marks: 1,
                text: "In wye-delta transformation, if the wye resistances are Ra, Rb, Rc, the delta resistance RAB is given by:",
                type: "mcq",
                options: ["Ra + Rb + RaRb/Rc", "(RaRb + RbRc + RcRa)/Rc", "Ra + Rb", "RaRb/(Ra + Rb + Rc)"]
            },
            {
                id: 9,
                marks: 1,
                text: "For the Thevenin equivalent circuit, if the open-circuit voltage is 20V and the short-circuit current is 4A, the Thevenin resistance in OHM is:",
                type: "numerical"
            },
            {
                id: 10,
                marks: 1,
                text: "A source with internal impedance Zₛ = (3 + j4) Ω delivers maximum power to a load. The load impedance ZL should be:",
                type: "mcq",
                options: ["(3 + j4) Ω", "(3 - j4) Ω", "(-3 - j4) Ω", "(4 + j3) Ω"]
            },
            {
                id: 11,
                marks: 2,
                text: "In the circuit shown below, find the voltage V₁ at node 1",
                type: "numerical",
                image: "11.png"
            },
            {
                id: 12,
                marks: 2,
                text: "Two coupled coils with L₁ = 2H, L₂ = 3H, and M = 1H carry currents i₁ = 2sin(ωt) A and i₂ = 3sin(ωt) A. The magnitude of total energy stored at ω = 1 rad/s when sin(ωt) = 1 is:",
                type: "mcq",
                options: ["3.5 J", "8.5 J", "11.5 J", "23.5 J"],
                image: "12.png"
            },
            {
                id: 13,
                marks: 2,
                text: "In the circuit below, find the current through the 3Ω resistor:",
                type: "numerical",
                image: "13.png"
            },
            {
                id: 14,
                marks: 2,
                text: "A transmission line segment has ABCD parameters: A = D = cosh(γl), B = Z₀sinh(γl), C = sinh(γl)/Z₀. For a lossless line with γl = jπ/2, the value of A is:",
                type: "mcq",
                options: ["0", "1", "j", "-j"]
            },
            {
                id: 15,
                marks: 2,
                text: "A circuit's impedance is Z(s) = (s² + 3s + 2)/(s + 1). The initial value of the impulse response z(0⁺) is:",
                type: "mcq",
                options: ["0", "1", "2", "∞"]
            },
            {
                id: 16,
                marks: 2,
                text: "A 230V, 50Hz supply feeds a load of 10kW at 0.7 lagging power factor. To improve the power factor to 0.95 lagging, the required capacitor value is:",
                type: "numerical"
            },
            {
                id: 17,
                marks: 2,
                text: "An RL circuit with R = 100Ω and L = 0.1H is connected to a 10V step input at t = 0. The current at t = 1ms is:",
                type: "mcq",
                options: ["0.0063", "0.063", "0.63", "6.3"]
            },
            {
                id: 18,
                marks: 2,
                text: "A series RLC circuit has R = 10Ω, L = 1mH, C = 10nF. The bandwidth in rad/s is",
                type: "mcq",
                options: ["10⁴", "10⁵", "10⁶", "10⁷"]
            },
            {
                id: 19,
                marks: 2,
                text: "A circuit has two sources: V₁ = 20∠0° V at ω₁ = 100 rad/s and V₂ = 30∠90° V at ω₂ = 200 rad/s. Through a 2Ω resistor, V₁ alone produces 4A and V₂ alone produces 3A. The total power dissipated in the resistor in Watt is:",
                type: "numerical"
            },
            {
                id: 20,
                marks: 2,
                text: "A T-network has series impedances Z₁ = 10Ω and Z₃ = 20Ω, and shunt impedance Z₂ = 30Ω. Find Z₂₁ in Ω:",
                type: "numerical",
                image: "20.png"
            },
            {
                id: 21,
                marks: 2,
                text: "A system has transfer function H(s) = 10(s + 2)/[s(s + 5)]. For a unit step input, the steady-state output is:",
                type: "mcq",
                options: ["2", "3", "4", "5"]
            },
            {
                id: 22,
                marks: 2,
                text: "A network contains only resistors and one CCCS with α = 0.5. When I₁ = 2A at port 1 produces V₂ = 8V at port 2, what voltage at port 2 will produce I₁ = 2A at port 1?",
                type: "mcq",
                options: ["4V", "8V", "16V", "Cannot be determined"]
            },
            {
                id: 23,
                marks: 2,
                text: "A balanced three-phase Y-connected load draws 10 kW at 0.8 pf lagging from a 400V (line-to-line) supply. The magnitude of line current is:",
                type: "mcq",
                options: ["18.04 A", "20.41 A", "25.53 A", "31.25 A"]
            },
            {
                id: 24,
                marks: 2,
                text: "Consider the op-amp based 2-port network shown in the circuit diagram below. The op-amp is ideal with infinite input impedance, zero output impedance, and infinite open-loop gain. Given R₁ = 10 kΩ, R₂ = 20 kΩ, R₃ = 5 kΩ, and R₄ = 15 kΩ. Find the Z₁₁ parameter of this 2-port network in kΩ.",
                type: "mcq",
                options: ["10", "15", "30", "50"],
                image: "24.png"
            },
            {
                id: 25,
                marks: 2,
                text: "The following op-amp based circuit operates as an active filter. The op-amp is ideal. Given R = 1 kΩ, C = 1 μF, and L = 1 mH. A sinusoidal input voltage v_in(t) = 10cos(1000t) V is applied. Calculate the magnitude of the output voltage |V_out| at the given frequency.",
                type: "mcq",
                options: ["5.77 V", "7.07 V", "10 V", "14.14 V"],
                image: "25.png"
            },
            {
                id: 26,
                marks: 2,
                text: "An RLC circuit with R = 4Ω, L = 1H, C = 0.25F is initially at rest. For a unit impulse input, the nature of response and time to first peak are:",
                type: "mcq",
                options: ["Underdamped, π/2 seconds", "Underdamped, π seconds", "Critically damped, no peak", "Overdamped, no peak"]
            },
            {
                id: 27,
                marks: 2,
                text: "For the op-amp integrator circuit shown (assume ideal op-amp), find the Norton equivalent current (In in mA) as seen from terminals A-B at t = 2ms, given that the capacitor is initially uncharged and a step input of 5V is applied at t = 0.",
                type: "mcq",
                options: ["25", "2.5", "-25", "-2.5"],
                image: "27.png"
            },
            {
                id: 28,
                marks: 2,
                text: "For the same diagram and values as question no 27, Norton equivalent resistance (Rn in Ω) as seen from terminals A-B at t = 2ms",
                type: "mcq",
                options: ["∞", "0", "2K", "1/2K"]
            },
            {
                id: 29,
                marks: 2,
                text: "For the op-amp differential amplifier circuit shown, verify the reciprocity theorem by calculating the transfer impedance Z21 when a 1V source is applied at terminal C and current is measured at terminal A, and Z12 when a 1V source is applied at terminal A and current is measured at terminal C. Given that terminal B is grounded for both measurements.",
                type: "mcq",
                options: ["Z21 = Z12 = 2kΩ, reciprocity verified", "Z21 = Z12 = -3kΩ, reciprocity verified", "Z21 ≠ Z12, reciprocity not applicable", "Z21 = Z12 = 4kΩ, reciprocity verified"],
                image: "29.png"
            },
            {
                id: 30,
                marks: 2,
                text: "An op-amp based integrator circuit is shown below with R = 2 kΩ and C = 0.5 μF. The op-amp is ideal. A sinusoidal input v_in(t) = 8sin(2000t + 30°) V is applied. Find the phase angle of the output voltage with respect to the input voltage.",
                type: "mcq",
                options: ["-60°", "+120°", "+60°", "-120°"],
                image: "30.png"
            }
        ];

        let currentQuestion = 0;
        let answers = {};
        let timerInterval;
        let timeLeft = 5400; // 90 minutes in seconds
        let examStarted = false;
        let examEnded = false;
        const PASSWORD = "gate2025";
        const RESET_PASSWORD = "R15himel";

        // Load saved data
        function loadSavedData() {
            const saved = localStorage.getItem('gateExamData');
            if (saved) {
                const data = JSON.parse(saved);
                answers = data.answers || {};
                timeLeft = data.timeLeft || 5400;
                examStarted = data.examStarted || false;
                examEnded = data.examEnded || false;
                currentQuestion = data.currentQuestion || 0;
            }
        }

        // Save data
        function saveData() {
            const data = {
                answers,
                timeLeft,
                examStarted,
                examEnded,
                currentQuestion
            };
            localStorage.setItem('gateExamData', JSON.stringify(data));
        }

        function startExam() {
            examStarted = true;
            document.getElementById('welcomeScreen').style.display = 'none';
            document.getElementById('mainContent').style.display = 'block';
            startTimer();
            renderPalette();
            displayQuestion(currentQuestion);
            saveData();
        }

        function startTimer() {
            updateTimerDisplay();
            timerInterval = setInterval(() => {
                timeLeft--;
                updateTimerDisplay();
                saveData();
                
                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    endExam();
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const hours = Math.floor(timeLeft / 3600);
            const minutes = Math.floor((timeLeft % 3600) / 60);
            const seconds = timeLeft % 60;
            document.getElementById('timer').textContent = 
                `${String(hours).padStart(2, '0')}:${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
        }

        function displayQuestion(index) {
            currentQuestion = index;
            const question = questions[index];
            const questionArea = document.getElementById('questionArea');
            
            let html = `
                <div class="question-header">
                    <div class="question-number">Question ${question.id} of 30</div>
                    <div class="question-marks">${question.marks} Mark${question.marks > 1 ? 's' : ''}</div>
                </div>
                <div class="question-text">${question.text}</div>
            `;
            
            if (question.image) {
                html += `<img src="${question.image}" class="question-image" alt="Circuit Diagram ${question.id}">`;
            }
            
            if (question.type === 'mcq') {
                html += '<div class="options">';
                question.options.forEach((option, i) => {
                    const checked = answers[question.id] === option ? 'selected' : '';
                    html += `
                        <div class="option ${checked}" onclick="selectOption(${question.id}, '${option.replace(/'/g, "\\'")}')">
                            <input type="radio" name="q${question.id}" value="${option}" ${answers[question.id] === option ? 'checked' : ''}>
                            ${option}
                        </div>
                    `;
                });
                html += '</div>';
            } else {
                html += `
                    <input type="number" 
                           class="numerical-input" 
                           id="numerical${question.id}" 
                           placeholder="Enter your answer (up to 1 decimal)" 
                           step="0.1"
                           value="${answers[question.id] || ''}"
                           onchange="saveNumerical(${question.id})">
                `;
            }
            
            html += `
                <div class="navigation-buttons">
                    ${index > 0 ? '<button class="nav-btn prev-btn" onclick="previousQuestion()">Previous</button>' : ''}
                    <button class="nav-btn save-next-btn" onclick="saveAndNext()">Save & Next</button>
                </div>
            `;
            
            questionArea.innerHTML = html;
            updatePalette();
            saveData();
        }

        function selectOption(questionId, option) {
            answers[questionId] = option;
            const options = document.querySelectorAll('.option');
            options.forEach(opt => opt.classList.remove('selected'));
            event.target.closest('.option').classList.add('selected');
            saveData();
        }

        function saveNumerical(questionId) {
            const input = document.getElementById(`numerical${questionId}`);
            let value = parseFloat(input.value);
            if (!isNaN(value)) {
                value = Math.round(value * 10) / 10; // Round to 1 decimal
                answers[questionId] = value;
                input.value = value;
            } else {
                delete answers[questionId];
            }
            saveData();
        }

        function saveAndNext() {
            if (currentQuestion < questions.length - 1) {
                displayQuestion(currentQuestion + 1);
            }
        }

        function previousQuestion() {
            if (currentQuestion > 0) {
                displayQuestion(currentQuestion - 1);
            }
        }

        function renderPalette() {
            const paletteGrid = document.getElementById('paletteGrid');
            paletteGrid.innerHTML = '';
            
            questions.forEach((q, index) => {
                const btn = document.createElement('button');
                btn.className = 'palette-btn';
                btn.textContent = q.id;
                btn.onclick = () => displayQuestion(index);
                paletteGrid.appendChild(btn);
            });
        }

        function updatePalette() {
            const buttons = document.querySelectorAll('.palette-btn');
            buttons.forEach((btn, index) => {
                btn.classList.remove('attempted', 'unattempted', 'current');
                
                if (index === currentQuestion) {
                    btn.classList.add('current');
                } else if (answers[questions[index].id] !== undefined) {
                    btn.classList.add('attempted');
                } else {
                    btn.classList.add('unattempted');
                }
            });
        }

        function submitExam() {
            if (confirm('Are you sure you want to submit the exam?')) {
                endExam();
            }
        }

        function endExam() {
            examEnded = true;
            clearInterval(timerInterval);
            saveData();
            document.getElementById('passwordModal').style.display = 'flex';
        }

        function checkPassword() {
            const input = document.getElementById('passwordInput').value;
            if (input === PASSWORD) {
                document.getElementById('passwordModal').style.display = 'none';
                document.getElementById('printBtn').style.display = 'block';
                displayResults();
            } else {
                alert('Incorrect password!');
            }
        }

        function displayResults() {
            const questionArea = document.getElementById('questionArea');
            let html = '<div style="padding: 20px;"><h2 style="color: #2a5298; margin-bottom: 30px;">Your Exam Responses</h2>';
            
            let attemptedCount = 0;
            questions.forEach(q => {
                if (answers[q.id] !== undefined) attemptedCount++;
                
                html += `
                    <div style="margin: 20px 0; padding: 20px; background: white; border-radius: 5px; border-left: 4px solid ${answers[q.id] !== undefined ? '#28a745' : '#dc3545'};">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
                            <strong style="color: #2a5298; font-size: 18px;">Question ${q.id}</strong>
                            <span style="background: #ffc107; padding: 5px 15px; border-radius: 20px; font-weight: bold;">${q.marks} Mark${q.marks > 1 ? 's' : ''}</span>
                        </div>
                        <div style="margin: 10px 0; color: #333;">${q.text}</div>
                        ${q.image ? `<img src="${q.image}" style="max-width: 400px; margin: 10px 0; border: 2px solid #ddd; border-radius: 5px;">` : ''}
                        <div style="margin-top: 15px; padding: 15px; background: #f8f9fa; border-radius: 5px;">
                            <strong style="color: ${answers[q.id] !== undefined ? '#28a745' : '#dc3545'};">Your Answer:</strong> 
                            <span style="font-size: 16px; margin-left: 10px;">${answers[q.id] !== undefined ? answers[q.id] : 'Not Attempted'}</span>
                        </div>
                    </div>
                `;
            });
            
            html += `
                <div style="margin: 30px 0; padding: 20px; background: #e3f2fd; border-radius: 10px; text-align: center;">
                    <h3 style="color: #1976d2; margin-bottom: 15px;">Exam Summary</h3>
                    <p style="font-size: 18px;"><strong>Total Questions:</strong> ${questions.length}</p>
                    <p style="font-size: 18px;"><strong>Attempted:</strong> <span style="color: #28a745;">${attemptedCount}</span></p>
                    <p style="font-size: 18px;"><strong>Not Attempted:</strong> <span style="color: #dc3545;">${questions.length - attemptedCount}</span></p>
                </div>
            </div>`;
            
            questionArea.innerHTML = html;
        }

        function printResponses() {
            window.print();
        }

        function resetExam() {
            document.getElementById('resetPasswordModal').style.display = 'flex';
        }

        function confirmReset() {
            const input = document.getElementById('resetPasswordInput').value;
            if (input === RESET_PASSWORD) {
                localStorage.removeItem('gateExamData');
                location.reload();
            } else {
                alert('Incorrect password!');
                document.getElementById('resetPasswordInput').value = '';
            }
        }

        function closeResetModal() {
            document.getElementById('resetPasswordModal').style.display = 'none';
            document.getElementById('resetPasswordInput').value = '';
        }

        function toggleCalculator() {
            const calc = document.getElementById('calculator');
            calc.style.display = calc.style.display === 'none' || calc.style.display === '' ? 'block' : 'none';
        }

        function calcAppend(value) {
            document.getElementById('calcDisplay').value += value;
        }

        function calcClear() {
            document.getElementById('calcDisplay').value = '';
        }

        function calcEqual() {
            try {
                const result = eval(document.getElementById('calcDisplay').value);
                document.getElementById('calcDisplay').value = result;
            } catch (e) {
                document.getElementById('calcDisplay').value = 'Error';
            }
        }

        // Initialize on load
        window.onload = function() {
            loadSavedData();
            
            if (examEnded) {
                document.getElementById('welcomeScreen').style.display = 'none';
                document.getElementById('mainContent').style.display = 'block';
                document.getElementById('passwordModal').style.display = 'flex';
            } else if (examStarted) {
                document.getElementById('welcomeScreen').style.display = 'none';
                document.getElementById('mainContent').style.display = 'block';
                startTimer();
                renderPalette();
                displayQuestion(currentQuestion);
            }
        };
    </script>
</body>
</html>
