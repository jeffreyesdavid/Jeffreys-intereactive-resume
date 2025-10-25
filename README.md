# Jeffreys-intereactive-resume
an interactive web resume 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jeffreys interactive resume</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Chosen Palette: Professional Indigo (Light Gray, Indigo, White) -->
    <!-- Application Structure Plan: The SPA is structured as a tabbed interface, a common and intuitive UI pattern. The main navigation [Overview, Experience, Skills, Education] allows users to explore different facets of the resume in a non-linear way. The 'Overview' tab visually introduces the core 'seed-to-sale' theme. The 'Experience' tab uses a secondary, vertical tab system to cleanly segment each job, preventing a long, overwhelming scroll and focusing user attention. The 'Skills' tab visually separates qualitative 'Competencies' (as pills) from quantitative 'Achievements' (as a bar chart) for maximum impact. This structure is chosen to make the resume's content highly digestible, interactive, and to guide the user (a hiring manager) directly to the most relevant information. -->
    <!-- Visualization & Content Choices: 1. "Seed-to-Sale" Flow: (Report Info) Career path -> (Goal) Organize/Inform -> (Viz) HTML/Tailwind Diagram -> (Interaction) Static visual flow -> (Justification) Visually explains the core "seed-to-sale" value proposition without SVG -> (Method) HTML/Tailwind. 2. Key Achievements: (Report Info) Quantifiable metrics (6 team, 16->26 drivers, 100+ brands) -> (Goal) Compare/Inform -> (Viz) Bar Chart -> (Interaction) Chart.js tooltips on hover -> (Justification) Transforms text-based bullets into a more impactful, memorable data visualization -> (Method) Chart.js with Canvas. 3. Core Competencies: (Report Info) Table of skills -> (Goal) Organize -> (Viz) HTML/Tailwind "Pills" -> (Interaction) Static list -> (Justification) More modern, scannable, and mobile-friendly presentation than a rigid table -> (Method) HTML/Tailwind. 4. Job History: (Report Info) List of 4 roles -> (Goal) Inform/Organize -> (Viz) Tabbed content blocks -> (Interaction) JS-driven show/hide on click -> (Justification) Improves clarity and focus by displaying one job at a time -> (Method) Vanilla JS. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8f9fa;
            color: #111827;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto; 
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .nav-link {
            transition: all 0.2s ease-in-out;
            border-bottom: 3px solid transparent;
        }
        .nav-link.active, .nav-link:hover {
            border-bottom-color: #4f46e5;
            color: #4f46e5;
        }
        .exp-link {
            transition: all 0.2s ease-in-out;
            border-left: 3px solid transparent;
        }
        .exp-link.active, .exp-link:hover {
            border-left-color: #4f46e5;
            background-color: #eef2ff;
            color: #4f46e5;
        }
        .content-panel {
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="antialiased">

    <div class="container mx-auto max-w-6xl p-4 sm:p-8">
        
        <header class="flex flex-col sm:flex-row justify-between sm:items-center gap-4">
            <div>
                <h1 class="text-4xl sm:text-5xl font-bold text-gray-900">Jeffrey David</h1>
                <p class="text-xl sm:text-2xl text-indigo-600 font-medium mt-1">Cannabis Operations & Sales Leader</p>
            </div>
            <div class="flex flex-col sm:items-end gap-1 text-gray-700 text-sm sm:text-right">
                <span class="flex items-center gap-2">
                    <span class="text-indigo-600">&#9742;</span>
                    (760) 780-9992
                </span>
                <span class="flex items-center gap-2">
                    <span class="text-indigo-600">&#9993;</span>
                    jeffreyisdavid@gmail.com
                </span>
                <span class="flex items-center gap-2">
                    <span class="text-indigo-600">&#128205;</span>
                    Los Angeles, CA
                </span>
            </div>
        </header>

        <nav class="mt-8 sm:mt-12 mb-8">
            <div class="flex flex-wrap space-x-2 sm:space-x-6 border-b border-gray-300">
                <button id="nav-overview" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Overview</button>
                <button id="nav-experience" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Experience</button>
                <button id="nav-skills" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Skills & Achievements</button>
                <button id="nav-education" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Education</button>
                <button id="nav-why" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Why Me?</button>
                <button id="nav-letter" class="nav-link text-sm sm:text-base font-medium px-2 py-3 text-gray-600">Cover Letter</button>
            </div>
        </nav>

        <main id="content-area">

            <section id="content-overview" class="content-panel">
                <p class="text-base text-gray-600 mb-6">This overview provides a high-level summary of my professional background and visually illustrates my unique 'seed-to-sale' expertise. This comprehensive experience allows me to understand and optimize the entire cannabis lifecycle, from initial cultivation to final sale and brand strategy.</p>
                
                <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                    <h2 class="text-2xl font-bold text-gray-900 mb-3">Professional Summary</h2>
                    <p class="text-lg text-gray-700 leading-relaxed">
                        Cannabis Operations & Sales leader with 4+ years of comprehensive **'seed-to-sale' lifecycle** experience, from hands-on cultivation to supporting C-level executive strategy. Proven ability to manage logistics, build brands, and lead teams in fast-paced, compliant environments. Seeking to leverage deep industry knowledge to drive operational excellence and sales growth as an Assistant Operations & Sales Manager.
                    </p>
                </div>

                <div class="mt-8">
                    <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">My 'Seed-to-Sale' Expertise</h2>
                    <div class="flex flex-col md:flex-row justify-between items-center gap-4 md:gap-2">
                        
                        <div class="bg-white p-6 rounded-lg shadow-lg w-full md:w-1/3 text-center">
                            <span class="text-3xl" role="img" aria-label="seedling">🌱</span>
                            <h3 class="text-xl font-bold text-indigo-700 mt-2">1. CULTIVATION</h3>
                            <p class="text-gray-600 mt-2 text-sm">Hands-on experience in cloning, vegetation, harvest, and IPM. (Yellow Dream Farm)</p>
                        </div>

                        <span class="font-bold text-4xl text-indigo-400 rotate-90 md:rotate-0">&rarr;</span>

                        <div class="bg-white p-6 rounded-lg shadow-lg w-full md:w-1/3 text-center">
                            <span class="text-3xl" role="img" aria-label="box">📦</span>
                            <h3 class="text-xl font-bold text-indigo-700 mt-2">2. OPERATIONS</h3>
                            <p class="text-gray-600 mt-2 text-sm">Managing packaging, logistics, driver teams, compliance, and 100+ vendor relations. (SoCal Green Meds)</p>
                        </div>
                        
                        <span class="font-bold text-4xl text-indigo-400 rotate-90 md:rotate-0">&rarr;</span>

                        <div class="bg-white p-6 rounded-lg shadow-lg w-full md:w-1/3 text-center">
                            <span class="text-3xl" role="img" aria-label="chart">📈</span>
                            <h3 class="text-xl font-bold text-indigo-700 mt-2">3. SALES & BRAND</h3>
                            <p class="text-gray-600 mt-2 text-sm">Building brands from scratch, social media strategy, and executive-level sales planning. (White Ray)</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="content-experience" class="content-panel hidden">
                <p class="text-base text-gray-600 mb-6">My professional experience is detailed below, from high-level management to hands-on cultivation. Click each role on the left to explore my specific responsibilities and achievements at each company. The most recent and relevant role is selected by default.</p>
                
                <div class="flex flex-col md:flex-row gap-8">
                    <aside class="w-full md:w-1/4">
                        <nav class="flex flex-col space-y-1">
                            <button id="exp-white-ray" class="exp-link text-left w-full p-3 rounded font-medium text-gray-700">White Ray</button>
                            <button id="exp-ydf" class="exp-link text-left w-full p-3 rounded font-medium text-gray-700">Yellow Dream Farm</button>
                            <button id="exp-socal" class="exp-link text-left w-full p-3 rounded font-medium text-gray-700">SoCal Green Meds</button>
                            <button id="exp-nostalgia" class="exp-link text-left w-full p-3 rounded font-medium text-gray-700">Nostalgia Vault LA</button>
                        </nav>
                    </aside>
                    
                    <div class="w-full md:w-3/4">
                        <article id="exp-content-white-ray" class="exp-panel bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                            <h2 class="text-2xl font-bold text-gray-900">Packaging Dept. Manager / Social Media & Brand Supervisor</h2>
                            <p class="text-lg font-medium text-indigo-600 mt-1">White Ray | Adelanto, CA (2023 – 2024)</p>
                            <ul class="list-disc list-outside pl-5 mt-4 space-y-2 text-gray-700">
                                <li>Provided direct operational support to the CEO, CFO, and Director of Cultivation, assisting with strategic planning, financial oversight, and cultivation management.</li>
                                <li>Managed the packaging department, <strong>hiring and leading a team of 6</strong> to ensure all products were compliant, packaged, and labeled according to state regulations.</li>
                                <li><strong>Built the company's brand identity and social media presence from the ground up</strong>, preparing for a future direct-to-consumer delivery launch.</li>
                                <li>Served as a key liaison between the executive team and department managers to streamline operational workflows.</li>
                            </ul>
                        </article>
                        
                        <article id="exp-content-ydf" class="exp-panel hidden bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                            <h2 class="text-2xl font-bold text-gray-900">Cultivator</h2>
                            <p class="text-lg font-medium text-indigo-600 mt-1">Yellow Dream Farm | Adelanto, CA (2021 – 2023)</p>
                            <ul class="list-disc list-outside pl-5 mt-4 space-y-2 text-gray-700">
                                <li>Gained hands-on experience in all stages of commercial cannabis cultivation, from cloning and propagation to vegetation, flowering, and harvest.</li>
                                <li>Responsible for daily plant maintenance, integrated pest management (IPM), and monitoring environmental controls <strong>across a multi-room weekly harvest rotation.</strong></li>
                                <li>Mastered cultivation techniques that provide a foundational 'seed-to-sale' understanding of the full cannabis supply chain.</li>
                            </ul>
                        </article>

                        <article id="exp-content-socal" class="exp-panel hidden bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                            <h2 class="text-2xl font-bold text-gray-900">Operations & Dispatch Manager</h2>
                            <p class="text-lg font-medium text-indigo-600 mt-1">SoCal Green Meds | Hesperia, CA (2020 – 2021)</p>
                            <ul class="list-disc list-outside pl-5 mt-4 space-y-2 text-gray-700">
                                <li>Promoted from Dispatcher to manage all delivery and dispatch logistics for a high-volume operation.</li>
                                <li><strong>Scaled the active driver team from 16 to 26</strong> to meet increasing demand while optimizing routes and performance.</li>
                                <li>Managed all vendor relations, ensuring compliance for <strong>over 100+ brands</strong> by verifying licenses, COAs, and all required paperwork.</li>
                                <li>Oversaw daily inventory management, curating a menu known for having the newest products and <strong>securing exclusive brand partnerships.</strong></li>
                                <li>Contributed to operational excellence that resulted in the company winning the <strong>"Best of the Desert" Award in 2021</strong>.</li>
                            </ul>
                        </article>

                        <article id="exp-content-nostalgia" class="exp-panel hidden bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                            <h2 class="text-2xl font-bold text-gray-900">Owner / Vendor</h2>
                            <p class="text-lg font-medium text-indigo-600 mt-1">Nostalgia Vault LA | Los Angeles, CA (2024 – Present)</p>
                            <ul class="list-disc list-outside pl-5 mt-4 space-y-2 text-gray-700">
                                <li>Manage all aspects of a personal business, including sourcing vintage apparel, inventory management, and pricing strategy.</li>
                                <li>Act as the primary salesperson at pop-up markets and events, building direct customer relationships and processing sales.</li>
                            </ul>
                        </article>
                    </div>
                </div>
            </section>
            
            <section id="content-skills" class="content-panel hidden">
                <p class="text-base text-gray-600 mb-8">This section highlights my core competencies and provides a visual representation of my key quantitative achievements in management and operations. These skills cover the full spectrum of the cannabis industry, from technical cultivation to executive-level support and brand strategy.</p>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                        <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">Key Achievements (Visualized)</h2>
                        <div class="chart-container">
                            <canvas id="achievementsChart"></canvas>
                        </div>
                    </div>

                    <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                        <h2 class="text-2xl font-bold text-gray-900 mb-6">Core Competencies</h2>
                        <div id="skills-container" class="flex flex-wrap gap-2 sm:gap-3">
                        </div>
                    </div>
                </div>
            </section>

            <section id="content-education" class="content-panel hidden">
                <p class="text-base text-gray-600 mb-6">This section details my formal education and foundational training, which complements my hands-on industry experience.</p>
                <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                    <h2 class="text-2xl font-bold text-gray-900">Education</h2>
                    <div class="mt-4">
                        <h3 class="text-lg font-semibold text-indigo-600">Music Production Program</h3>
                        <p class="text-gray-700">Los Angeles Film School, Los Angeles, CA</p>
                    </div>
                </div>
            </section>

            <section id="content-why" class="content-panel hidden">
                <p class="text-base text-gray-600 mb-6">This section explains my personal philosophy and what makes me a unique candidate for an operations and sales leadership role. It's about the 'why' behind the 'what' on my resume.</p>
                <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm mb-8">
                    <h2 class="text-2xl font-bold text-gray-900 mb-4">What Makes Me a Great Fit?</h2>
                    
                    <div class="space-y-4 text-gray-700">
                        <p>Beyond the specific skills and experience, my value comes from my perspective. Here’s what I bring to the table that many others don't:</p>

                        <ul class="list-disc list-outside pl-5 space-y-3">
                            <li>
                                <strong>True 360-Degree View:</strong> Most candidates are either cultivation experts, logistics managers, or brand strategists. I've been all three. I've cultivated the plant, managed the logistics of getting it to customers (scaling a 26-driver team), and supported the C-suite with brand and operational strategy. I don't just see one part of the business; I see the entire 'seed-to-sale' ecosystem.
                            </li>
                            <li>
                                <strong>A "Builder" Not Just a "Maintainer":</strong> I thrive in environments where I get to build. At White Ray, I built the brand and social media presence from scratch. At SoCal Green Meds, I secured exclusive partnerships and scaled the driver team by over 60%. I have a proven track record of taking initiative and creating value, not just managing what's already there.
                            </li>
                            <li>
                                <strong>Executive-Level Poise:</strong> My experience as a direct assistant to the CEO, CFO, and Director of Cultivation at White Ray means I know how to communicate effectively, understand high-level business goals, and operate with professionalism and discretion.
                            </li>
                            <li>
                                <strong>Personal Drive (The Capricorn Factor):</strong> You mentioned you're a Capricorn, and it's true. I am inherently driven, practical, and have a relentless work ethic. When I'm part of a mission, I am 100% committed to seeing it through with precision and integrity.
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                    <h2 class="text-2xl font-bold text-gray-900 mb-4">✨ AI-Powered Interview Prep</h2>
                    <p class="text-gray-700 mb-6">Click a question to see how I'd approach it, based on my experience. (Answers are generated in real-time by the Gemini AI using my resume as context).</p>
                    
                    <div class="flex flex-col sm:flex-row gap-2 sm:gap-4 mb-6">
                        <button id="q1-button" class="w-full sm:w-1/3 text-sm text-left bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-medium p-3 rounded-lg transition">"Tell me about a time you had to build a process from scratch."</button>
                        <button id="q2-button" class="w-full sm:w-1/3 text-sm text-left bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-medium p-3 rounded-lg transition">"What's your 30-day plan for an Operations & Sales role?"</button>
                        <button id="q3-button" class="w-full sm:w-1/3 text-sm text-left bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-medium p-3 rounded-lg transition">"How would you handle a conflict between cultivation and sales?"</button>
                    </div>

                    <div id="ai-response-box" class="p-6 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] text-gray-600 italic">Select a question above to see a sample answer here...</div>
                </div>
            </section>

            <section id="content-letter" class="content-panel hidden">
                <p class="text-base text-gray-600 mb-6">This is a tailored cover letter for the "Assistant Operations & Sales Manager – Cannabis Industry" position, demonstrating my direct fit for the role by connecting my experience to its key requirements.</p>
                <div class="bg-white p-6 sm:p-8 rounded-lg shadow-sm">
                    <h2 class="text-2xl font-bold text-gray-900 mb-6">Cover Letter</h2>
                    
                    <div class="prose prose-lg max-w-none text-gray-700">
                        <p class="font-medium">Dear Hiring Manager,</p>

                        <p>I am writing with immense enthusiasm to apply for the Assistant Operations & Sales Manager position I found advertised on Craigslist. With over four years of comprehensive, hands-on experience in the California cannabis industry—spanning from cultivation to executive-level operations—I am confident I possess the 'seed-to-sale' expertise and leadership skills necessary to excel in this role.</p>

                        <p>Your requirement for a manager who understands both operations and sales is a perfect match for my background. My experience is not limited to one silo; I have built and managed the full lifecycle:</p>
                        
                        <ul class="list-disc list-outside pl-5 space-y-2">
                            <li><strong>Operations & Logistics:</strong> As the Operations & Dispatch Manager for SoCal Green Meds, I managed all logistics for a high-volume delivery service. I scaled our driver team from 16 to 26, managed vendor relations and compliance for over 100 brands, and secured exclusive product partnerships, contributing directly to our "Best of the Desert" award.</li>
                            <li><strong>Brand & Sales Strategy:</strong> At White Ray, I was hired to build the company's brand and social media presence from the ground up. This role required me to develop a cohesive brand identity and sales strategy in preparation for a D2C launch.</li>
                            <li><strong>Executive-Level Poise:</strong> My role at White Ray also involved providing direct operational support to the CEO, CFO, and Director of Cultivation. I have a proven ability to communicate effectively at an executive level and understand high-level business goals.</li>
                            <li><strong>Cultivation Foundation:</strong> My time as a Cultivator at Yellow Dream Farm gave me the foundational knowledge of the product itself, from cloning and IPM to harvest rotations.</li>
                        </ul>

                        <p>I am not just a candidate who can maintain existing systems; I am a "builder" who thrives on creating value. I am a driven, practical, and relentlessly hard-working professional (a true Capricorn) who is ready to dedicate my full energy to your team's success.</p>

                        <p>I am available for an interview at your earliest convenience and can be reached at (760) 780-9992 or jeffreyisdavid@gmail.com. Thank you for your time and consideration.</p>

                        <p class="font-medium">Sincerely,<br>Jeffrey David</p>
                    </div>
                </div>
            </section>

        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            const skillsData = [
                'Seed-to-Sale Operations', 'C-Level Executive Support', 'Logistics & Dispatch Mgmt',
                'Team Leadership & Scaling', 'Brand Development', 'Social Media Strategy',
                'State/Local Compliance (METRC)', 'Vendor & COA Management', 'Inventory & Quality Control',
                'Cultivation & Plant Health', 'Packaging & Workflow', 'Direct-to-Consumer Sales',
                'Bilingual (English/Spanish)', 'POS & Inventory Systems', 'Customer Relationship Mgmt'
            ];

            const achievementsData = {
                labels: ['Brands Managed (SoCal)', 'Driver Team Scaled (SoCal)', 'Packaging Team (White Ray)'],
                values: [100, 26, 6]
            };

            const contentPanels = document.querySelectorAll('.content-panel');
            const navLinks = document.querySelectorAll('.nav-link');
            const expPanels = document.querySelectorAll('.exp-panel');
            const expLinks = document.querySelectorAll('.exp-link');
            const skillsContainer = document.getElementById('skills-container');
            const aiResponseBox = document.getElementById('ai-response-box');
            const q1Button = document.getElementById('q1-button');
            const q2Button = document.getElementById('q2-button');
            const q3Button = document.getElementById('q3-button');

            let achievementsChart;
            let chartInitialized = false;
            let isAiResponding = false;

            const resumeContext = "Summary: 4+ years in 'seed-to-sale' cannabis. Experience: 1. Packaging Dept. Manager / Social Media & Brand Supervisor at White Ray (2023-2024): Supported CEO/CFO, led a team of 6, built brand from scratch. 2. Cultivator at Yellow Dream Farm (2021-2023): Hands-on cultivation, harvest rotation. 3. Operations & Dispatch Manager at SoCal Green Meds (2020-2021): Scaled driver team from 16 to 26, managed 100+ vendor relations, won 'Best of the Desert' award. 4. Owner of Nostalgia Vault LA (2024-Present): Sales and inventory.";
            
            const systemPrompt = `You are Jeffrey David, a professional and results-driven cannabis operations and sales leader. Your tone is confident, professional, and practical (like a Capricorn: driven and precise). Use your resume as context: ${resumeContext}. You will be asked common interview questions. Answer in the first person ('I') using the STAR method (Situation, Task, Action, Result) when possible, and directly reference experiences from your resume to support your answer. Keep answers concise, in 2-3 paragraphs. Format your response with paragraphs separated by newlines (\n).`;

            async function fetchWithBackoff(apiUrl, payload, retries = 5, delay = 1000) {
                for (let i = 0; i < retries; i++) {
                    try {
                        const response = await fetch(apiUrl, {
                            method: 'POST',
                            headers: { 'Content-Type': 'application/json' },
                            body: JSON.stringify(payload)
                        });

                        if (response.ok) {
                            return await response.json();
                        } else if (response.status === 429 || response.status >= 500) {
                            await new Promise(resolve => setTimeout(resolve, delay));
                            delay *= 2;
                        } else {
                            return { error: `HTTP error! status: ${response.status}` };
                        }
                    } catch (error) {
                        if (i === retries - 1) {
                            return { error: error.message };
                        }
                        await new Promise(resolve => setTimeout(resolve, delay));
                        delay *= 2;
                    }
                }
                return { error: 'Max retries reached' };
            }

            async function handleInterviewQuestion(event) {
                if (isAiResponding) return;
                isAiResponding = true;
                aiResponseBox.classList.add('italic');
                aiResponseBox.classList.remove('text-gray-800');
                aiResponseBox.classList.add('text-gray-600');
                aiResponseBox.innerHTML = '✨ Thinking...';

                const question = event.target.textContent;
                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;

                const payload = {
                    contents: [{ parts: [{ text: question }] }],
                    systemInstruction: {
                        parts: [{ text: systemPrompt }]
                    },
                };

                const result = await fetchWithBackoff(apiUrl, payload);
                
                aiResponseBox.classList.remove('italic');
                aiResponseBox.classList.remove('text-gray-600');
                aiResponseBox.classList.add('text-gray-800');

                if (result && result.candidates?.[0]?.content?.parts?.[0]?.text) {
                    const rawText = result.candidates[0].content.parts[0].text;
                    const formattedText = rawText.split('\n').map(p => `<p>${p}</p>`).join('');
                    aiResponseBox.innerHTML = formattedText;
                } else {
                    aiResponseBox.innerHTML = 'Sorry, I encountered an error trying to generate a response. Please try again in a moment.';
                }
                
                isAiResponding = false;
            }

            function showTab(tabId) {
                contentPanels.forEach(panel => {
                    panel.classList.add('hidden');
                });
                document.getElementById(`content-${tabId}`).classList.remove('hidden');

                navLinks.forEach(link => {
                    link.classList.remove('active');
                });
                document.getElementById(`nav-${tabId}`).classList.add('active');

                if (tabId === 'skills' && !chartInitialized) {
                    createAchievementsChart();
                    populateSkills();
                    chartInitialized = true;
                }
            }

            function showExperience(expId) {
                expPanels.forEach(panel => {
                    panel.classList.add('hidden');
                });
                document.getElementById(`exp-content-${expId}`).classList.remove('hidden');

                expLinks.forEach(link => {
                    link.classList.remove('active');
                });
                document.getElementById(`exp-${expId}`).classList.add('active');
            }
            
            function populateSkills() {
                skillsData.forEach(skill => {
                    const skillElement = document.createElement('span');
                    skillElement.className = 'bg-indigo-100 text-indigo-800 text-sm font-medium px-3 py-1.5 rounded-full';
                    skillElement.textContent = skill;
                    skillsContainer.appendChild(skillElement);
                });
            }

            function createAchievementsChart() {
                const ctx = document.getElementById('achievementsChart').getContext('2d');
                achievementsChart = new Chart(ctx, {
                    type: 'bar',
                    data: {
                        labels: achievementsData.labels,
                        datasets: [{
                            label: 'Key Achievements',
                            data: achievementsData.values,
                            backgroundColor: [
                                'rgba(79, 70, 229, 0.7)',
                                'rgba(99, 102, 241, 0.7)',
                                'rgba(129, 140, 248, 0.7)'
                            ],
                            borderColor: [
                                'rgba(79, 70, 229, 1)',
                                'rgba(99, 102, 241, 1)',
                                'rgba(129, 140, 248, 1)'
                            ],
                            borderWidth: 1
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: {
                                display: false
                            },
                            tooltip: {
                                enabled: true,
                                backgroundColor: '#111827',
                                titleFont: { size: 14, weight: 'bold' },
                                bodyFont: { size: 12 },
                                displayColors: false,
                                callbacks: {
                                    label: function(context) {
                                        let label = context.dataset.label || '';
                                        if (label) {
                                            label += ': ';
                                        }
                                        if (context.parsed.y !== null) {
                                            if (context.label.includes('Brands')) {
                                                label += `${context.parsed.y}+ Brands`;
                                            } else if (context.label.includes('Driver')) {
                                                label += `${context.parsed.y} Drivers`;
                                            } else if (context.label.includes('Packaging')) {
                                                label += `${context.parsed.y} Team Members`;
                                            } else {
                                                label += context.parsed.y;
                                            }
                                        }
                                        return label;
                                    }
                                }
                            }
                        },
                        scales: {
                            y: {
                                beginAtZero: true,
                                grid: {
                                    color: '#e5e7eb'
                                },
                                ticks: {
                                    color: '#4b5563'
                                }
                            },
                            x: {
                                grid: {
                                    display: false
                                },
                                ticks: {
                                    color: '#4b5563',
                                    autoSkip: false,
                                    maxRotation: 0,
                                    minRotation: 0,
                                    callback: function(value) {
                                        const label = this.getLabelForValue(value);
                                        if (label.length > 15) {
                                            return label.split(' ').slice(0, 2).join(' ') + '...';
                                        }
         
                                        return label;
                                    }
                                }
                            }
                        }
                    }
                });
            }

            navLinks.forEach(link => {
                link.addEventListener('click', () => {
                    const tabId = link.id.split('-')[1];
                    showTab(tabId);
                });
            });

            expLinks.forEach(link => {
                link.addEventListener('click', () => {
                    const expId = link.id.split('-')[1];
                    showExperience(expId);
                });
            });

            showTab('overview');
            showExperience('white-ray');
            
            q1Button.addEventListener('click', handleInterviewQuestion);
            q2Button.addEventListener('click', handleInterviewQuestion);
            q3Button.addEventListener('click', handleInterviewQuestion);
        });
    </script>
</body>
</html>
