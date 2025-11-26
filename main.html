<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>均值与标准差计算器</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap');
        body {
            font-family: 'Noto Sans SC', sans-serif;
            background-color: #f3f4f6;
        }
        .result-card {
            transition: all 0.3s ease;
        }
        .result-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        .report-box {
            background: linear-gradient(135deg, #4f46e5 0%, #3b82f6 100%);
        }
        .error-rate-box {
            background: linear-gradient(135deg, #ef4444 0%, #f87171 100%);
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen flex flex-col items-center py-10 px-4">

    <div class="max-w-4xl w-full bg-white rounded-2xl shadow-lg overflow-hidden">
        <!-- Header -->
        <div class="bg-indigo-600 p-6 text-white text-center">
            <h1 class="text-3xl font-bold mb-2"><i class="fas fa-calculator mr-2"></i>统计学计算器</h1>
            <p class="text-indigo-100">快速计算 Mean ± SD 与 Mean ± SEM</p>
        </div>

        <div class="p-6 md:p-8">
            <!-- Input Section -->
            <div class="mb-8">
                <label for="dataInput" class="block text-sm font-medium text-gray-700 mb-2">
                    输入数据 (准确率/正确数):
                </label>
                <div class="relative">
                    <textarea id="dataInput" rows="4" 
                        class="w-full p-4 border border-gray-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 transition-colors text-gray-700 font-mono"
                        placeholder="例如: 95.5, 96.2, 95.8 (百分制) 或 0.95, 0.96 (小数)"></textarea>
                    <div class="absolute bottom-3 right-3 text-xs text-gray-400" id="inputCount">0 个数字</div>
                </div>
                
                <div class="flex flex-wrap gap-3 mt-4">
                    <button onclick="calculate()" class="flex-1 bg-indigo-600 hover:bg-indigo-700 text-white font-semibold py-2.5 px-6 rounded-lg shadow transition-colors flex items-center justify-center gap-2">
                        <i class="fas fa-play"></i> 计算
                    </button>
                    <button onclick="generateRandom()" class="bg-gray-100 hover:bg-gray-200 text-gray-700 font-medium py-2.5 px-4 rounded-lg transition-colors flex items-center gap-2">
                        <i class="fas fa-dice"></i> 随机示例
                    </button>
                    <button onclick="clearInput()" class="bg-red-50 hover:bg-red-100 text-red-600 font-medium py-2.5 px-4 rounded-lg transition-colors flex items-center gap-2">
                        <i class="fas fa-trash-alt"></i> 清空
                    </button>
                </div>
                <p id="errorMsg" class="text-red-500 text-sm mt-2 hidden"><i class="fas fa-exclamation-circle mr-1"></i> 请输入有效的数字。</p>
            </div>

            <!-- Results Section (Initially Hidden) -->
            <div id="resultsSection" class="hidden animate-fade-in">
                
                <!-- Reporting Formats Grid -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
                    
                    <!-- Accuracy / Correctness Box -->
                    <div class="report-box rounded-xl p-6 text-white shadow-md relative overflow-hidden">
                        <div class="absolute top-0 right-0 bg-white/20 px-3 py-1 rounded-bl-lg text-xs font-bold">输入数据</div>
                        <h3 class="text-lg font-semibold mb-4 border-b border-white/20 pb-2 flex items-center">
                            <i class="fas fa-check-circle mr-2"></i> 准确率 (Accuracy)
                        </h3>
                        <div class="space-y-4">
                            <div>
                                <div class="text-indigo-100 text-sm mb-1">Mean ± SD</div>
                                <div class="text-3xl font-bold font-mono tracking-tight" id="reportMeanSD">--</div>
                            </div>
                            <div>
                                <div class="text-indigo-100 text-sm mb-1">Mean ± SEM</div>
                                <div class="text-2xl font-bold font-mono tracking-tight opacity-90" id="reportMeanSEM">--</div>
                            </div>
                        </div>
                    </div>

                    <!-- Error Rate Box (New) -->
                    <div class="error-rate-box rounded-xl p-6 text-white shadow-md relative overflow-hidden">
                        <div class="absolute top-0 right-0 bg-white/20 px-3 py-1 rounded-bl-lg text-xs font-bold" id="scaleBadge">自动检测</div>
                        <h3 class="text-lg font-semibold mb-4 border-b border-white/20 pb-2 flex items-center">
                            <i class="fas fa-times-circle mr-2"></i> 错误率 (Error Rate)
                        </h3>
                        <div class="space-y-4">
                            <div>
                                <div class="text-red-100 text-sm mb-1">Mean ± SD (标准差不变)</div>
                                <div class="text-3xl font-bold font-mono tracking-tight" id="errorMeanSD">--</div>
                            </div>
                            <div class="text-xs text-red-100 mt-2 bg-white/10 p-2 rounded">
                                <i class="fas fa-info-circle mr-1"></i> 假设基准为 <span id="scaleText" class="font-bold">100</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-8">
                    <!-- Mean -->
                    <div class="result-card bg-blue-50 border border-blue-100 p-4 rounded-xl">
                        <div class="text-blue-500 text-sm font-semibold uppercase tracking-wider mb-1">平均值 (Mean)</div>
                        <div class="text-3xl font-bold text-gray-800" id="resMean">--</div>
                        <div class="text-xs text-gray-500 mt-1">符号: <span class="font-serif">x̄</span></div>
                    </div>

                    <!-- Sum -->
                    <div class="result-card bg-emerald-50 border border-emerald-100 p-4 rounded-xl">
                        <div class="text-emerald-500 text-sm font-semibold uppercase tracking-wider mb-1">总和 (Sum)</div>
                        <div class="text-3xl font-bold text-gray-800" id="resSum">--</div>
                        <div class="text-xs text-gray-500 mt-1">符号: <span class="font-serif">Σx</span></div>
                    </div>

                    <!-- Count -->
                    <div class="result-card bg-purple-50 border border-purple-100 p-4 rounded-xl">
                        <div class="text-purple-500 text-sm font-semibold uppercase tracking-wider mb-1">样本数量 (Count)</div>
                        <div class="text-3xl font-bold text-gray-800" id="resCount">--</div>
                        <div class="text-xs text-gray-500 mt-1">符号: <span class="font-serif">n</span></div>
                    </div>
                </div>

                <!-- Standard Deviation & Variance Grid -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
                    <!-- Sample Stats -->
                    <div class="border-2 border-indigo-100 rounded-xl overflow-hidden bg-white relative ring-2 ring-indigo-50">
                        <div class="absolute top-0 right-0 bg-indigo-100 text-indigo-700 text-xs px-2 py-1 font-bold rounded-bl-lg">常用</div>
                        <div class="bg-indigo-50 px-4 py-3 border-b border-indigo-100 font-semibold text-indigo-900 flex justify-between items-center">
                            <span>样本统计 (Sample)</span>
                            <span class="text-xs bg-white border border-indigo-200 px-2 py-1 rounded text-indigo-600">除以 n-1</span>
                        </div>
                        <div class="p-4 space-y-4">
                            <div>
                                <div class="text-sm text-gray-500 mb-1">样本标准差 (SD)</div>
                                <div class="text-2xl font-bold text-indigo-700" id="resSampleStd">--</div>
                                <div class="text-xs text-gray-400 font-serif">s</div>
                            </div>
                            <div class="border-t border-gray-100 pt-3">
                                <div class="text-sm text-gray-500 mb-1">样本方差 (Variance)</div>
                                <div class="text-xl font-semibold text-gray-800" id="resSampleVar">--</div>
                                <div class="text-xs text-gray-400 font-serif">s²</div>
                            </div>
                        </div>
                    </div>

                    <!-- Population Stats -->
                    <div class="border border-gray-200 rounded-xl overflow-hidden bg-gray-50 opacity-90">
                        <div class="bg-gray-100 px-4 py-3 border-b border-gray-200 font-semibold text-gray-600 flex justify-between items-center">
                            <span>总体统计 (Population)</span>
                            <span class="text-xs bg-white border border-gray-300 px-2 py-1 rounded text-gray-500">除以 n</span>
                        </div>
                        <div class="p-4 space-y-4">
                            <div>
                                <div class="text-sm text-gray-500 mb-1">总体标准差 (SD)</div>
                                <div class="text-2xl font-bold text-gray-600" id="resPopStd">--</div>
                                <div class="text-xs text-gray-400 font-serif">σ</div>
                            </div>
                            <div class="border-t border-gray-200 pt-3">
                                <div class="text-sm text-gray-500 mb-1">总体方差 (Variance)</div>
                                <div class="text-xl font-semibold text-gray-600" id="resPopVar">--</div>
                                <div class="text-xs text-gray-400 font-serif">σ²</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Calculation Steps Details -->
                <div class="bg-gray-50 rounded-xl p-5 border border-gray-200">
                    <h3 class="font-semibold text-gray-800 mb-4 flex items-center">
                        <i class="fas fa-list-ol text-indigo-500 mr-2"></i> 计算细节
                    </h3>
                    <div class="text-sm text-gray-600 space-y-2 font-mono overflow-x-auto">
                        <div class="flex justify-between border-b pb-2 mb-2 font-sans font-medium">
                            <span class="w-16">数据点</span>
                            <span class="w-32 text-right">差值 (x - x̄)</span>
                            <span class="w-32 text-right">平方 (x - x̄)²</span>
                        </div>
                        <div id="stepsContainer" class="max-h-60 overflow-y-auto pr-2 space-y-1">
                            <!-- Steps will be injected here -->
                        </div>
                        <div class="border-t pt-2 mt-2 flex justify-between font-bold text-indigo-700">
                            <span>平方和 (SS)</span>
                            <span id="resSS">--</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Empty State -->
            <div id="emptyState" class="text-center py-12 text-gray-400">
                <i class="fas fa-chart-bar text-6xl mb-4 text-gray-200"></i>
                <p>请输入数据并点击“计算”以查看结果</p>
            </div>
        </div>
    </div>

    <script>
        const input = document.getElementById('dataInput');
        const countDisplay = document.getElementById('inputCount');
        const errorMsg = document.getElementById('errorMsg');
        const resultsSection = document.getElementById('resultsSection');
        const emptyState = document.getElementById('emptyState');

        // Live count update
        input.addEventListener('input', () => {
            const val = input.value.trim();
            if (!val) {
                countDisplay.textContent = '0 个数字';
                return;
            }
            // Match numbers including decimals and negatives
            const matches = val.split(/[\s,]+/).filter(v => v !== '');
            countDisplay.textContent = `${matches.length} 个数据点`;
            errorMsg.classList.add('hidden');
        });

        function clearInput() {
            input.value = '';
            input.focus();
            countDisplay.textContent = '0 个数字';
            resultsSection.classList.add('hidden');
            emptyState.classList.remove('hidden');
            errorMsg.classList.add('hidden');
        }

        function generateRandom() {
            const count = Math.floor(Math.random() * 5) + 5; // 5-10 numbers
            const nums = [];
            // Generate percentages like 85.5, 92.1 etc
            for (let i = 0; i < count; i++) {
                nums.push((Math.random() * 15 + 80).toFixed(1));
            }
            input.value = nums.join(', ');
            // Trigger input event to update count
            input.dispatchEvent(new Event('input'));
            calculate();
        }

        function calculate() {
            const rawValue = input.value;
            const tokens = rawValue.split(/[\s,]+/).filter(v => v !== '');
            
            if (tokens.length === 0) {
                errorMsg.textContent = "请输入至少一个数字。";
                errorMsg.classList.remove('hidden');
                return;
            }

            const numbers = tokens.map(Number);
            
            if (numbers.some(isNaN)) {
                errorMsg.textContent = "输入包含非数字字符，请检查。";
                errorMsg.classList.remove('hidden');
                return;
            }

            errorMsg.classList.add('hidden');

            const n = numbers.length;
            const sum = numbers.reduce((a, b) => a + b, 0);
            const mean = sum / n;

            let sumSqDiff = 0;
            const stepsHtml = numbers.map(num => {
                const diff = num - mean;
                const sqDiff = diff * diff;
                sumSqDiff += sqDiff;
                return `
                    <div class="flex justify-between hover:bg-gray-100 p-1 rounded">
                        <span class="w-16">${num}</span>
                        <span class="w-32 text-right text-gray-500">${diff.toFixed(4)}</span>
                        <span class="w-32 text-right text-gray-800">${sqDiff.toFixed(4)}</span>
                    </div>
                `;
            }).join('');

            const popVar = sumSqDiff / n;
            const popStd = Math.sqrt(popVar);
            
            let sampleVar = 0;
            let sampleStd = 0;
            let sem = 0;
            
            if (n > 1) {
                sampleVar = sumSqDiff / (n - 1);
                sampleStd = Math.sqrt(sampleVar);
                sem = sampleStd / Math.sqrt(n);
            }

            // --- Error Rate Logic ---
            // Auto detect scale: if any value > 1, assume 0-100 scale. Else 0-1 scale.
            const isPercentage = numbers.some(x => x > 1);
            const scaleBase = isPercentage ? 100 : 1;
            const errorMean = scaleBase - mean;
            // SD and SEM remain the same for Error Rate as Accuracy

            // Update UI
            const fmtMean = formatNum(mean);
            const fmtErrorMean = formatNum(errorMean);
            const fmtSampleStd = n > 1 ? formatNum(sampleStd) : "N/A";
            const fmtSEM = n > 1 ? formatNum(sem) : "N/A";

            document.getElementById('resMean').textContent = fmtMean;
            document.getElementById('resSum').textContent = formatNum(sum);
            document.getElementById('resCount').textContent = n;
            
            document.getElementById('resPopStd').textContent = formatNum(popStd);
            document.getElementById('resPopVar').textContent = formatNum(popVar);
            
            if (n > 1) {
                document.getElementById('resSampleStd').textContent = fmtSampleStd;
                document.getElementById('resSampleVar').textContent = formatNum(sampleVar);
                
                // Report Box - Accuracy
                document.getElementById('reportMeanSD').textContent = `${fmtMean} ± ${fmtSampleStd}`;
                document.getElementById('reportMeanSEM').textContent = `${fmtMean} ± ${fmtSEM}`;

                // Report Box - Error Rate
                document.getElementById('errorMeanSD').textContent = `${fmtErrorMean} ± ${fmtSampleStd}`;
                document.getElementById('scaleBadge').textContent = isPercentage ? "百分制 (%)" : "小数 (0-1)";
                document.getElementById('scaleText').textContent = isPercentage ? "100" : "1";
            } else {
                document.getElementById('resSampleStd').textContent = "N/A";
                document.getElementById('resSampleVar').textContent = "N/A";
                document.getElementById('reportMeanSD').textContent = "n > 1";
                document.getElementById('reportMeanSEM').textContent = "n > 1";
                document.getElementById('errorMeanSD').textContent = "n > 1";
            }

            document.getElementById('stepsContainer').innerHTML = stepsHtml;
            document.getElementById('resSS').textContent = formatNum(sumSqDiff);

            emptyState.classList.add('hidden');
            resultsSection.classList.remove('hidden');
        }

        function formatNum(num) {
            if (Number.isInteger(num)) return num;
            return parseFloat(num.toFixed(4));
        }
    </script>
</body>
</html>
