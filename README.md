<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UAEMéx - Actividad de Dilemas: Trabajo Colaborativo</title>
    <!-- CDN Estable de Tailwind CSS -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <!-- Iconos para la estética de juego -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@500;700&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            background-color: #0b1411;
        }
        /* Colores de identidad UAEMéx */
        .bg-uaemex-verde {
            background-color: #004a2f;
        }
        .border-uaemex-oro {
            border-color: #d4a373;
        }
        .text-uaemex-oro {
            color: #d4a373;
        }
        .game-card {
            border: 3px solid #d4a373;
            box-shadow: 0px 6px 0px rgba(0,0,0,0.5);
        }
        /* Fondo Galaxy para la Portada */
        .bg-mario-galaxy-cover {
            background-image: url('https://images.unsplash.com/photo-1506318137071-a8e063b4bec0?auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
        }
        .bg-galaxy {
            background: linear-gradient(135deg, #003622 0%, #051410 100%);
        }
    </style>
</head>
<body class="min-h-screen text-gray-100 flex flex-col justify-between">

    <!-- HUD SUPERIOR INSTITUCIONAL -->
    <header class="bg-black p-4 border-b-4 border-gray-900">
        <div class="max-w-4xl mx-auto flex justify-between items-center text-xs font-bold tracking-wider">
            <div class="flex items-center space-x-2 text-uaemex-oro">
                <i class="fa-solid fa-university animate-pulse"></i>
                <span>UAEMéx • ORIENTACIÓN EDUCATIVA</span>
            </div>
            <div class="text-gray-400 uppercase hidden sm:block">Tema 2.1: Desafíos Colaborativos</div>
            <div class="text-green-400 text-[11px]" id="hud-account">1ER SEMESTRE</div>
        </div>
    </header>

    <!-- NÚCLEO DEL SIMULADOR -->
    <main class="flex-grow p-4 md:p-6 max-w-3xl w-full mx-auto flex flex-col justify-center items-center">

        <!-- PANTALLA 1: PORTADA Y REGISTRO -->
        <div id="screen-start" class="w-full max-w-md bg-mario-galaxy-cover p-6 rounded-2xl game-card text-center space-y-5 relative overflow-hidden">
            <div class="absolute inset-0 bg-black bg-opacity-50 z-0"></div>

            <div class="space-y-2 relative z-10">
                <span class="bg-uaemex-verde text-white text-[10px] font-bold px-3 py-0.5 rounded-full uppercase tracking-widest border border-yellow-500 shadow-md">UAEMéx</span>
                <h2 class="text-lg md:text-xl font-extrabold text-uaemex-oro uppercase leading-tight filter drop-shadow-md">
                    Desafíos en el Trabajo Colaborativo
                </h2>
                <p class="text-xs text-gray-100 px-2 font-medium">Análisis Crítico de Dilemas Éticos en el Aula</p>
            </div>

            <div class="bg-black bg-opacity-80 p-4 rounded-xl border border-uaemex-oro border-opacity-40 text-left space-y-3.5 relative z-10 shadow-xl backdrop-blur-sm">
                <div class="space-y-1">
                    <label class="text-xs font-bold text-gray-200 uppercase block"><i class="fa-solid fa-user text-uaemex-oro mr-1.5"></i> Nombre Completo:</label>
                    <input type="text" id="ins-name" placeholder="Ej. Sofía Almeida Pozos" class="w-full px-3 py-2 rounded-lg bg-gray-900 border border-gray-700 text-white text-sm focus:ring-2 focus:ring-yellow-500 focus:outline-none">
                </div>
                <div class="space-y-1">
                    <label class="text-xs font-bold text-gray-200 uppercase block"><i class="fa-solid fa-id-card text-uaemex-oro mr-1.5"></i> Número de Cuenta:</label>
                    <input type="number" id="ins-account" placeholder="Ej. 2410943" class="w-full px-3 py-2 rounded-lg bg-gray-900 border border-gray-700 text-white text-sm focus:ring-2 focus:ring-yellow-500 focus:outline-none">
                </div>
                <p id="err-start" class="text-xs text-red-400 font-bold hidden"><i class="fa-solid fa-circle-exclamation mr-1"></i> Completa ambos campos institucionales antes de iniciar.</p>
            </div>

            <button onclick="actionToDilemmas()" class="w-full py-3 rounded-xl bg-gradient-to-r from-yellow-500 to-yellow-600 hover:from-yellow-400 hover:to-yellow-500 text-black font-bold text-xs uppercase tracking-wider shadow-md transform active:scale-95 transition-transform relative z-10 border-b-4 border-yellow-700">
                Iniciar Misión Académica <i class="fa-solid fa-rocket ml-1.5"></i>
            </button>
        </div>


        <!-- PANTALLA 2: BANCO DE 5 DILEMAS (200 CARACTERES MÁX) -->
        <div id="screen-dilemmas" class="w-full max-w-xl hidden bg-galaxy p-5 rounded-2xl game-card space-y-4">
            
            <div class="bg-black bg-opacity-40 border border-uaemex-oro border-opacity-30 p-3 rounded-lg text-xs text-gray-300 leading-relaxed">
                <span class="text-uaemex-oro font-bold uppercase block mb-1"><i class="fa-solid fa-star mr-1"></i> Instrucciones de Coherencia Crítica:</span>
                Analiza cada escenario. Redacta soluciones lógicas y empáticas que promuevan la colaboración sana. Cuentas con un límite estricto de **200 caracteres** por respuesta.
            </div>

            <div class="space-y-4 text-xs max-h-[440px] overflow-y-auto pr-1">
                <!-- D1 -->
                <div class="bg-black bg-opacity-30 p-3.5 rounded-xl border border-gray-800 space-y-2">
                    <p class="font-bold text-uaemex-oro">Dilema 1. El compañero que no participa</p>
                    <p class="text-gray-300 italic">"Un integrante no responde mensajes ni asiste a las reuniones de tu equipo, pero el día de la entrega pide que lo incluyan para no reprobar la materia."</p>
                    <textarea id="txt-d1" maxlength="200" oninput="trackChars('txt-d1','c1')" rows="2" placeholder="Escribe tu postura aquí..." class="w-full p-2.5 rounded bg-gray-950 border border-gray-700 text-white focus:ring-1 focus:ring-yellow-500 focus:outline-none resize-none"></textarea>
                    <div class="text-right text-[10px] text-gray-400"><span id="c1">0</span> / 200 caracteres</div>
                </div>

                <!-- D2 -->
                <div class="bg-black bg-opacity-30 p-3.5 rounded-xl border border-gray-800 space-y-2">
                    <p class="font-bold text-uaemex-oro">Dilema 2. El líder que controla todo</p>
                    <p class="text-gray-300 italic">"Una compañera organiza el trabajo de forma autocrática: distribuye tareas y toma todas las decisiones importantes sin consultar ni escuchar al resto del grupo."</p>
                    <textarea id="txt-d2" maxlength="200" oninput="trackChars('txt-d2','c2')" rows="2" placeholder="¿Cómo solucionarías este problema de liderazgo?..." class="w-full p-2.5 rounded bg-gray-950 border border-gray-700 text-white focus:ring-1 focus:ring-yellow-500 focus:outline-none resize-none"></textarea>
                    <div class="text-right text-[10px] text-gray-400"><span id="c2">0</span> / 200 caracteres</div>
                </div>

                <!-- D3 -->
                <div class="bg-black bg-opacity-30 p-3.5 rounded-xl border border-gray-800 space-y-2">
                    <p class="font-bold text-uaemex-oro">Dilema 3. Calidad o amistad</p>
                    <p class="text-gray-300 italic">"Dos integrantes entregan partes deficientes que dañan la calificación del proyecto. Son tus amigos y sabes que atraviesan por problemas familiares severos."</p>
                    <textarea id="txt-d3" maxlength="200" oninput="trackChars('txt-d3','c3')" rows="2" placeholder="¿Cómo equilibras la empatía con la calidad académica?..." class="w-full p-2.5 rounded bg-gray-950 border border-gray-700 text-white focus:ring-1 focus:ring-yellow-500 focus:outline-none resize-none"></textarea>
                    <div class="text-right text-[10px] text-gray-400"><span id="c3">0</span> / 200 caracteres</div>
                </div>

                <!-- D4 -->
                <div class="bg-black bg-opacity-30 p-3.5 rounded-xl border border-gray-800 space-y-2">
                    <p class="font-bold text-uaemex-oro">Dilema 4. El reparto inequitativo de cargas</p>
                    <p class="text-gray-300 italic">"Al dividir el proyecto, un integrante elige la parte más fácil y corta de la exposición, dejando las secciones complejas e investigativas al resto del equipo."</p>
                    <textarea id="txt-d4" maxlength="200" oninput="trackChars('txt-d4','c4')" rows="2" placeholder="¿Cómo negociarías una redistribución justa y equitativa?..." class="w-full p-2.5 rounded bg-gray-950 border border-gray-700 text-white focus:ring-1 focus:ring-yellow-500 focus:outline-none resize-none"></textarea>
                    <div class="text-right text-[10px] text-gray-400"><span id="c4">0</span> / 200 caracteres</div>
                </div>

                <!-- D5 -->
                <div class="bg-black bg-opacity-30 p-3.5 rounded-xl border border-gray-800 space-y-2">
                    <p class="font-bold text-uaemex-oro">Dilema 5. El plagio detectado al final</p>
                    <p class="text-gray-300 italic">"Faltan pocas horas para enviar la evidencia final del equipo y descubres que un compañero copió y pegó directamente de internet toda su sección asignada."</p>
                    <textarea id="txt-d5" maxlength="200" oninput="trackChars('txt-d5','c5')" rows="2" placeholder="¿Cuál es tu postura ética y plan de acción inmediato?..." class="w-full p-2.5 rounded bg-gray-950 border border-gray-700 text-white focus:ring-1 focus:ring-yellow-500 focus:outline-none resize-none"></textarea>
                    <div class="text-right text-[10px] text-gray-400"><span id="c5">0</span> / 200 caracteres</div>
                </div>
            </div>

            <div class="flex justify-between items-center pt-2 border-t border-gray-800">
                <p id="err-dilemmas" class="text-xs text-red-400 font-bold hidden">Responde los 5 dilemas para registrar tu avance institucional.</p>
                <button onclick="actionCompileReport()" class="ml-auto px-5 py-2.5 rounded-xl bg-uaemex-verde hover:bg-opacity-90 text-white font-bold text-xs uppercase tracking-wider border border-uaemex-oro">
                    Concluir y Mostrar Resultados <i class="fa-solid fa-flag-checkered ml-1.5"></i>
                </button>
            </div>
        </div>


        <!-- PANTALLA 3: TABLERO DIGITAL DE RESULTADOS DE LA UAEMéx -->
        <div id="section-report" class="w-full max-w-xl hidden bg-galaxy p-5 rounded-2xl game-card space-y-4 border-uaemex-oro">
            
            <div class="text-center border-b pb-3 border-gray-800">
                <div class="text-uaemex-oro text-2xl mb-1"><i class="fa-solid fa-award"></i></div>
                <h2 class="text-base font-bold text-white uppercase tracking-wide">Desempeño Formativo UAEMéx</h2>
                <p class="text-[11px] text-gray-400">Evidencia de Reflexión Crítica Procesada Exitosamente</p>
            </div>

            <!-- Ficha Alumno -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 p-3 rounded-xl bg-black bg-opacity-40 border border-gray-800 text-xs">
                <div>
                    <span class="text-[10px] font-bold uppercase tracking-wider text-gray-500 block">Estudiante Alumno(a):</span>
                    <span id="rep-lbl-name" class="font-bold text-uaemex-oro">--</span>
                </div>
                <div>
                    <span class="text-[10px] font-bold uppercase tracking-wider text-gray-500 block">Número de Cuenta Universitaria:</span>
                    <span id="rep-lbl-account" class="font-bold text-uaemex-oro">--</span>
                </div>
            </div>

            <!-- Respuestas en Pantalla -->
            <div class="space-y-3 text-xs max-h-[320px] overflow-y-auto pr-1">
                <div class="p-3 bg-black bg-opacity-30 rounded-xl border border-gray-800 space-y-1">
                    <p class="font-bold text-gray-400">Postura - Dilema 1 (Falta de participación):</p>
                    <p id="rep-txt-d1" class="text-gray-200 bg-gray-900 bg-opacity-50 p-2 rounded border border-dashed border-gray-700 italic">--</p>
                </div>
                <div class="p-3 bg-black bg-opacity-30 rounded-xl border border-gray-800 space-y-1">
                    <p class="font-bold text-gray-400">Postura - Dilema 2 (Liderazgo autocrático):</p>
                    <p id="rep-txt-d2" class="text-gray-200 bg-gray-900 bg-opacity-50 p-2 rounded border border-dashed border-gray-700 italic">--</p>
                </div>
                <div class="p-3 bg-black bg-opacity-30 rounded-xl border border-gray-800 space-y-1">
                    <p class="font-bold text-gray-400">Postura - Dilema 3 (Empatía vs Calidad):</p>
                    <p id="rep-txt-d3" class="text-gray-200 bg-gray-900 bg-opacity-50 p-2 rounded border border-dashed border-gray-700 italic">--</p>
                </div>
                <div class="p-3 bg-black bg-opacity-30 rounded-xl border border-gray-800 space-y-1">
                    <p class="font-bold text-gray-400">Postura - Dilema 4 (Reparto inequitativo):</p>
                    <p id="rep-txt-d4" class="text-gray-200 bg-gray-900 bg-opacity-50 p-2 rounded border border-dashed border-gray-700 italic">--</p>
                </div>
                <div class="p-3 bg-black bg-opacity-30 rounded-xl border border-gray-800 space-y-1">
                    <p class="font-bold text-gray-400">Postura - Dilema 5 (Plagio al cierre):</p>
                    <p id="rep-txt-d5" class="text-gray-200 bg-gray-900 bg-opacity-50 p-2 rounded border border-dashed border-gray-700 italic">--</p>
                </div>
            </div>

            <div class="bg-green-950 bg-opacity-30 border border-green-800 p-2.5 rounded-lg text-center text-[11px] text-green-400">
                <i class="fa-solid fa-circle-check mr-1"></i> Misión completada. Muestra esta pantalla final a tu orientador(a) para el registro de tu participación.
            </div>
        </div>

    </main>

    <!-- FOOTER -->
    <footer class="bg-black border-t border-gray-900 py-2.5 text-center text-[10px] text-gray-500">
        UAEMéx • Dirección de Orientación Educativa • Recursos Didácticos Digitales
    </footer>

    <!-- LOGIC SCRIPT -->
    <script>
        let currentName = "";
        let currentAccount = "";

        function trackChars(textId, counterId) {
            const element = document.getElementById(textId);
            document.getElementById(counterId).innerText = element.value.length;
        }

        function actionToDilemmas() {
            const nameVal = document.getElementById('ins-name').value.trim();
            const accVal = document.getElementById('ins-account').value.trim();
            
            if (nameVal === "" || accVal === "") {
                document.getElementById('err-start').classList.remove('hidden');
                return;
            }
            currentName = nameVal;
            currentAccount = accVal;
            
            document.getElementById('hud-account').innerText = `CTA: ${currentAccount}`;
            
            document.getElementById('screen-start').classList.add('hidden');
            document.getElementById('screen-dilemmas').classList.remove('hidden');
        }

        function actionCompileReport() {
            const d1Text = document.getElementById('txt-d1').value.trim();
            const d2Text = document.getElementById('txt-d2').value.trim();
            const d3Text = document.getElementById('txt-d3').value.trim();
            const d4Text = document.getElementById('txt-d4').value.trim();
            const d5Text = document.getElementById('txt-d5').value.trim();
            
            if (d1Text === "" || d2Text === "" || d3Text === "" || d4Text === "" || d5Text === "") {
                document.getElementById('err-dilemmas').classList.remove('hidden');
                return;
            }
            document.getElementById('err-dilemmas').classList.add('hidden');

            // Volcado de información
            document.getElementById('rep-lbl-name').innerText = currentName;
            document.getElementById('rep-lbl-account').innerText = currentAccount;
            
            document.getElementById('rep-txt-d1').innerText = `"${d1Text}"`;
            document.getElementById('rep-txt-d2').innerText = `"${d2Text}"`;
            document.getElementById('rep-txt-d3').innerText = `"${d3Text}"`;
            document.getElementById('rep-txt-d4').innerText = `"${d4Text}"`;
            document.getElementById('rep-txt-d5').innerText = `"${d5Text}"`;

            // Transición de pantallas
            document.getElementById('screen-dilemmas').classList.add('hidden');
            document.getElementById('section-report').classList.remove('hidden');
        }
    </script>
</body>
</html>
