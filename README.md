<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formatador RPA Sisprime</title>
  <link rel="icon" href="favicon.ico" type="image/x-icon">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --primary: #2563eb;
      --primary-dark: #1e40af;
      --primary-light: #3b82f6;
      --secondary: #64748b;
      --success: #10b981;
      --warning: #f59e0b;
      --danger: #ef4444;
      --background: #f8fafc;
      --surface: #ffffff;
      --text-primary: #1e293b;
      --text-secondary: #64748b;
      --border: #e2e8f0;
      --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
      --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
      --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1);
      --radius: 12px;
      --transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', sans-serif;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
      color: var(--text-primary);
      line-height: 1.6;
      padding: 20px;
    }

    .app-wrapper {
      max-width: 1200px;
      margin: 0 auto;
    }

    .header {
      text-align: center;
      margin-bottom: 32px;
      animation: fadeInDown 0.6s ease-out;
    }

    .header h1 {
      color: white;
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 8px;
      text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .header p {
      color: rgba(255, 255, 255, 0.9);
      font-size: 1.1rem;
    }

    .tabs {
      background: var(--surface);
      border-radius: var(--radius);
      padding: 8px;
      display: flex;
      gap: 8px;
      margin-bottom: 24px;
      box-shadow: var(--shadow-lg);
      animation: fadeInUp 0.6s ease-out 0.1s both;
    }

    .tab-button {
      flex: 1;
      padding: 16px 24px;
      border: none;
      background: transparent;
      color: var(--text-secondary);
      font-size: 15px;
      font-weight: 600;
      border-radius: 8px;
      cursor: pointer;
      transition: var(--transition);
      position: relative;
      overflow: hidden;
    }

    .tab-button::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: var(--primary);
      opacity: 0;
      transition: var(--transition);
      border-radius: 8px;
    }

    .tab-button:hover {
      color: var(--primary);
      transform: translateY(-2px);
    }

    .tab-button.active {
      color: white;
    }

    .tab-button.active::before {
      opacity: 1;
    }

    .tab-button span {
      position: relative;
      z-index: 1;
    }

    .container {
      background: var(--surface);
      border-radius: var(--radius);
      padding: 32px;
      box-shadow: var(--shadow-lg);
      animation: fadeInUp 0.6s ease-out 0.2s both;
    }

    .section-header {
      margin-bottom: 24px;
      padding-bottom: 16px;
      border-bottom: 2px solid var(--border);
    }

    .section-header h2 {
      color: var(--text-primary);
      font-size: 1.75rem;
      font-weight: 700;
      margin-bottom: 8px;
    }

    .section-header p {
      color: var(--text-secondary);
      font-size: 0.95rem;
    }

    .form-group {
      margin-bottom: 24px;
    }

    .form-label {
      display: block;
      font-weight: 600;
      color: var(--text-primary);
      margin-bottom: 8px;
      font-size: 0.95rem;
    }

    .textarea-wrapper {
      position: relative;
    }

    textarea {
      width: 100%;
      min-height: 180px;
      padding: 16px;
      border: 2px solid var(--border);
      border-radius: var(--radius);
      font-size: 14px;
      font-family: 'Courier New', monospace;
      resize: vertical;
      transition: var(--transition);
      background: var(--background);
      color: var(--text-primary);
    }

    textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    }

    textarea:disabled {
      background: #f1f5f9;
      cursor: not-allowed;
    }

    .char-count {
      position: absolute;
      bottom: 12px;
      right: 16px;
      font-size: 0.75rem;
      color: var(--text-secondary);
      background: white;
      padding: 4px 8px;
      border-radius: 4px;
      pointer-events: none;
    }

    .button-group {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    button {
      padding: 12px 24px;
      border: none;
      border-radius: 8px;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      display: inline-flex;
      align-items: center;
      gap: 8px;
      box-shadow: var(--shadow-sm);
    }

    button:active {
      transform: scale(0.98);
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }

    .btn-primary:hover {
      background: var(--primary-dark);
      box-shadow: var(--shadow-md);
      transform: translateY(-2px);
    }

    .btn-secondary {
      background: var(--secondary);
      color: white;
    }

    .btn-secondary:hover {
      background: #475569;
      box-shadow: var(--shadow-md);
    }

    .btn-success {
      background: var(--success);
      color: white;
    }

    .btn-success:hover {
      background: #059669;
      box-shadow: var(--shadow-md);
    }

    .btn-outline {
      background: transparent;
      border: 2px solid var(--border);
      color: var(--text-primary);
    }

    .btn-outline:hover {
      border-color: var(--primary);
      color: var(--primary);
      background: rgba(37, 99, 235, 0.05);
    }

    .output-section {
      margin-top: 32px;
      padding-top: 32px;
      border-top: 2px solid var(--border);
    }

    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 24px;
      margin-bottom: 24px;
    }

    .card {
      background: var(--background);
      border: 2px solid var(--border);
      border-radius: var(--radius);
      padding: 24px;
      transition: var(--transition);
    }

    .card:hover {
      border-color: var(--primary-light);
      box-shadow: var(--shadow-md);
    }

    .card h3 {
      color: var(--text-primary);
      font-size: 1.25rem;
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      padding: 4px 12px;
      border-radius: 12px;
      font-size: 0.75rem;
      font-weight: 600;
      background: var(--primary);
      color: white;
      margin-left: auto;
    }

    .badge-success {
      background: var(--success);
    }

    .badge-warning {
      background: var(--warning);
    }

    .stats {
      display: flex;
      gap: 16px;
      margin-top: 12px;
      padding-top: 12px;
      border-top: 1px solid var(--border);
    }

    .stat-item {
      flex: 1;
      text-align: center;
    }

    .stat-value {
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--primary);
    }

    .stat-label {
      font-size: 0.75rem;
      color: var(--text-secondary);
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .hidden {
      display: none !important;
    }

    .toast {
      position: fixed;
      bottom: 24px;
      right: 24px;
      background: var(--surface);
      color: var(--text-primary);
      padding: 16px 24px;
      border-radius: var(--radius);
      box-shadow: var(--shadow-lg);
      display: flex;
      align-items: center;
      gap: 12px;
      animation: slideInRight 0.3s ease-out;
      z-index: 1000;
      border-left: 4px solid var(--success);
    }

    .toast.error {
      border-left-color: var(--danger);
    }

    .toast-icon {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--success);
      color: white;
      font-weight: bold;
    }

    .toast.error .toast-icon {
      background: var(--danger);
    }

    .loading {
      display: inline-block;
      width: 16px;
      height: 16px;
      border: 2px solid rgba(255, 255, 255, 0.3);
      border-top-color: white;
      border-radius: 50%;
      animation: spin 0.6s linear infinite;
    }

    @keyframes fadeInDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes slideInRight {
      from {
        opacity: 0;
        transform: translateX(100px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }

    @keyframes spin {
      to { transform: rotate(360deg); }
    }

    @media (max-width: 768px) {
      body {
        padding: 12px;
      }

      .header h1 {
        font-size: 1.75rem;
      }

      .container {
        padding: 20px;
      }

      .tabs {
        flex-direction: column;
      }

      .button-group {
        flex-direction: column;
      }

      button {
        width: 100%;
        justify-content: center;
      }

      .grid-2 {
        grid-template-columns: 1fr;
      }
    }

    .empty-state {
      text-align: center;
      padding: 48px 24px;
      color: var(--text-secondary);
    }

    .empty-state-icon {
      font-size: 3rem;
      margin-bottom: 16px;
      opacity: 0.5;
    }

    .icon {
      display: inline-block;
      width: 20px;
      height: 20px;
    }
  </style>
</head>
<body>
  <div class="app-wrapper">
    <div class="header">
      <h1>🤖 Formatador RPA Sisprime</h1>
      <p>Ferramentas profissionais para otimização de processos</p>
    </div>

    <div class="tabs">
      <button class="tab-button active" onclick="showSection('envelopes')" data-section="envelopes">
        <span>📧 ID Envelopes</span>
      </button>
      <button class="tab-button" onclick="showSection('numeros')" data-section="numeros">
        <span>🔢 Números SQL</span>
      </button>
      <button class="tab-button" onclick="showSection('comparador')" data-section="comparador">
        <span>⚖️ Comparador</span>
      </button>
    </div>

    <!-- Seção Envelopes -->
    <div id="envelopes" class="container">
      <div class="section-header">
        <h2>Formatador de ID Envelopes</h2>
        <p>Transforme IDs em formato compatível com consultas RPA</p>
      </div>

      <div class="form-group">
        <label class="form-label">IDs de Entrada</label>
        <div class="textarea-wrapper">
          <textarea id="keysInput" placeholder="Cole os IDs aqui (um por linha ou em sequência)"></textarea>
          <span class="char-count" id="keysInputCount">0 caracteres</span>
        </div>
      </div>

      <div class="button-group">
        <button class="btn-primary" onclick="formatKeys()">
          <span>✨</span> Formatar Chaves
        </button>
        <button class="btn-outline" onclick="clearSection('envelopes')">
          <span>🗑️</span> Limpar Tudo
        </button>
      </div>

      <div class="output-section hidden" id="envelopesOutput">
        <div class="form-group">
          <label class="form-label">IDs Formatados</label>
          <div class="textarea-wrapper">
            <textarea id="formattedKeys" readonly></textarea>
            <span class="char-count" id="formattedKeysCount">0 caracteres</span>
          </div>
        </div>
        <button class="btn-success" onclick="copyToClipboard('formattedKeys')">
          <span>📋</span> Copiar para Área de Transferência
        </button>
      </div>
    </div>

    <!-- Seção Números -->
    <div id="numeros" class="container hidden">
      <div class="section-header">
        <h2>Formatador de Números SQL</h2>
        <p>Organize números para consultas SQL otimizadas</p>
      </div>

      <div class="form-group">
        <label class="form-label">Números de Entrada</label>
        <div class="textarea-wrapper">
          <textarea id="numbersInput" placeholder="Cole os números aqui (um por linha)"></textarea>
          <span class="char-count" id="numbersInputCount">0 números</span>
        </div>
      </div>

      <div class="button-group">
        <button class="btn-primary" onclick="formatNumbers()">
          <span>✨</span> Formatar Números
        </button>
        <button class="btn-outline" onclick="clearSection('numeros')">
          <span>🗑️</span> Limpar Tudo
        </button>
      </div>

      <div class="output-section hidden" id="numerosOutput">
        <div class="form-group">
          <label class="form-label">Números Formatados</label>
          <div class="textarea-wrapper">
            <textarea id="formattedNumbers" readonly></textarea>
          </div>
        </div>
        <button class="btn-success" onclick="copyToClipboard('formattedNumbers')">
          <span>📋</span> Copiar para Área de Transferência
        </button>
      </div>
    </div>

    <!-- Seção Comparador -->
    <div id="comparador" class="container hidden">
      <div class="section-header">
        <h2>Comparador de IDs</h2>
        <p>Identifique IDs processados e pendentes</p>
      </div>

      <div class="grid-2">
        <div class="card">
          <h3>📥 IDs a Processar</h3>
          <textarea id="idsToProcess" placeholder="Cole os IDs a processar aqui..."></textarea>
          <div class="stats">
            <div class="stat-item">
              <div class="stat-value" id="countToProcess">0</div>
              <div class="stat-label">Total</div>
            </div>
          </div>
        </div>

        <div class="card">
          <h3>✅ IDs Já Processados</h3>
          <textarea id="idsProcessed" placeholder="Cole os IDs já processados aqui..."></textarea>
          <div class="stats">
            <div class="stat-item">
              <div class="stat-value" id="countProcessed">0</div>
              <div class="stat-label">Total</div>
            </div>
          </div>
        </div>
      </div>

      <div class="button-group">
        <button class="btn-primary" onclick="compareIDs()">
          <span>⚖️</span> Comparar IDs
        </button>
        <button class="btn-outline" onclick="clearSection('comparador')">
          <span>🗑️</span> Limpar Tudo
        </button>
      </div>

      <div class="output-section hidden" id="comparadorOutput">
        <div class="grid-2">
          <div class="card">
            <h3>
              ✅ IDs Iguais
              <span class="badge badge-success" id="commonCount">0</span>
            </h3>
            <textarea id="commonIDs" readonly></textarea>
            <button class="btn-success" onclick="copyToClipboard('commonIDs')" style="margin-top: 12px; width: 100%;">
              <span>📋</span> Copiar IDs Iguais
            </button>
          </div>

          <div class="card">
            <h3>
              ⚠️ IDs Diferentes
              <span class="badge badge-warning" id="differentCount">0</span>
            </h3>
            <textarea id="differentIDs" readonly></textarea>
            <button class="btn-success" onclick="copyToClipboard('differentIDs')" style="margin-top: 12px; width: 100%;">
              <span>📋</span> Copiar IDs Diferentes
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Sistema de Notificações Toast
    function showToast(message, isError = false) {
      const existingToast = document.querySelector('.toast');
      if (existingToast) {
        existingToast.remove();
      }

      const toast = document.createElement('div');
      toast.className = `toast ${isError ? 'error' : ''}`;
      toast.innerHTML = `
        <div class="toast-icon">${isError ? '✕' : '✓'}</div>
        <span>${message}</span>
      `;
      document.body.appendChild(toast);

      setTimeout(() => {
        toast.style.animation = 'slideInRight 0.3s ease-out reverse';
        setTimeout(() => toast.remove(), 300);
      }, 3000);
    }

    // Gerenciamento de Seções/Tabs
    function showSection(sectionId) {
      document.querySelectorAll('.container').forEach(el => el.classList.add('hidden'));
      document.getElementById(sectionId).classList.remove('hidden');

      document.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active'));
      document.querySelector(`[data-section="${sectionId}"]`).classList.add('active');
    }

    // Contador de Caracteres
    function setupCharCounter(inputId, counterId, isNumber = false) {
      const input = document.getElementById(inputId);
      const counter = document.getElementById(counterId);
      
      input.addEventListener('input', () => {
        if (isNumber) {
          const lines = input.value.split('\n').filter(line => line.trim());
          counter.textContent = `${lines.length} número${lines.length !== 1 ? 's' : ''}`;
        } else {
          counter.textContent = `${input.value.length} caractere${input.value.length !== 1 ? 's' : ''}`;
        }
      });
    }

    // Formatador de Chaves
    function formatKeys() {
      const keysInput = document.getElementById('keysInput').value.trim();
      
      if (!keysInput) {
        showToast('Por favor, insira os IDs no campo de entrada', true);
        return;
      }

      let formattedKeys = '';
      if (keysInput.includes('\n')) {
        formattedKeys = keysInput.replace(/\n/g, ' ').replace(/ +/g, ' OR ');
      } else {
        for (let i = 0; i < keysInput.length; i += 36) {
          if (i > 0) formattedKeys += ' OR ';
          formattedKeys += keysInput.substring(i, i + 36);
        }
      }

      document.getElementById('formattedKeys').value = formattedKeys;
      document.getElementById('envelopesOutput').classList.remove('hidden');
      
      const count = formattedKeys.split(' OR ').length;
      showToast(`${count} ID${count !== 1 ? 's' : ''} formatado${count !== 1 ? 's' : ''} com sucesso!`);
    }

    // Formatador de Números
    function formatNumbers() {
      const numbersInput = document.getElementById('numbersInput').value.trim();
      
      if (!numbersInput) {
        showToast('Por favor, insira os números no campo de entrada', true);
        return;
      }

      const numbersArray = numbersInput.split('\n').map(num => num.trim()).filter(num => num);
      const formattedNumbers = numbersArray.map((num, index) => 
        (index + 1) % 8 === 0 && index !== numbersArray.length - 1 ? `${num},\n` : `${num}, `
      ).join('').slice(0, -2);

      document.getElementById('formattedNumbers').value = formattedNumbers;
      document.getElementById('numerosOutput').classList.remove('hidden');
      
      showToast(`${numbersArray.length} número${numbersArray.length !== 1 ? 's' : ''} formatado${numbersArray.length !== 1 ? 's' : ''} com sucesso!`);
    }

    // Comparador de IDs
    function extractKey(path) {
      const match = path.match(/\\([^\\]+)"?$/);
      return match ? match[1].replace(/"$/, '') : path;
    }

    function updateProcessCount() {
      const textarea = document.getElementById('idsToProcess');
      const ids = textarea.value.split('\n').map(id => id.trim()).filter(id => id);
      document.getElementById('countToProcess').textContent = ids.length;
    }

    function updateProcessedCount() {
      const textarea = document.getElementById('idsProcessed');
      const ids = textarea.value.split('\n').map(id => id.trim()).filter(id => id);
      document.getElementById('countProcessed').textContent = ids.length;
    }

    function compareIDs() {
      const idsToProcess = document.getElementById('idsToProcess').value
        .split('\n').map(id => extractKey(id.trim())).filter(id => id);
      const idsProcessed = document.getElementById('idsProcessed').value
        .split('\n').map(id => extractKey(id.trim())).filter(id => id);

      if (idsToProcess.length === 0 || idsProcessed.length === 0) {
        showToast('Por favor, preencha ambos os campos antes de comparar', true);
        return;
      }

      const setToProcess = new Set(idsToProcess);
      const setProcessed = new Set(idsProcessed);

      const commonIDs = [...setToProcess].filter(id => setProcessed.has(id));
      const differentIDs = [...setToProcess].filter(id => !setProcessed.has(id));

      document.getElementById('commonIDs').value = commonIDs.length > 0 
        ? commonIDs.join('\n') 
        : 'Nenhum ID em comum encontrado.';
      
      document.getElementById('differentIDs').value = differentIDs.length > 0 
        ? differentIDs.join('\n') 
        : 'Nenhum ID diferente encontrado.';

      document.getElementById('commonCount').textContent = commonIDs.length;
      document.getElementById('differentCount').textContent = differentIDs.length;
      
      document.getElementById('comparadorOutput').classList.remove('hidden');
      
      showToast(`Comparação concluída: ${commonIDs.length} iguais, ${differentIDs.length} diferentes`);
    }

    // Copiar para Clipboard
    async function copyToClipboard(elementId) {
      const copyText = document.getElementById(elementId);
      
      if (!copyText.value || copyText.value.includes('Nenhum')) {
        showToast('Nenhum conteúdo para copiar', true);
        return;
      }

      try {
        await navigator.clipboard.writeText(copyText.value);
        showToast('Texto copiado para a área de transferência!');
      } catch (err) {
        showToast('Falha ao copiar o texto', true);
      }
    }

    // Limpar Seções
    function clearSection(section) {
      if (section === 'envelopes') {
        document.getElementById('keysInput').value = '';
        document.getElementById('formattedKeys').value = '';
        document.getElementById('envelopesOutput').classList.add('hidden');
      } else if (section === 'numeros') {
        document.getElementById('numbersInput').value = '';
        document.getElementById('formattedNumbers').value = '';
        document.getElementById('numerosOutput').classList.add('hidden');
      } else if (section === 'comparador') {
        document.getElementById('idsToProcess').value = '';
        document.getElementById('idsProcessed').value = '';
        document.getElementById('commonIDs').value = '';
        document.getElementById('differentIDs').value = '';
        document.getElementById('comparadorOutput').classList.add('hidden');
        updateProcessCount();
        updateProcessedCount();
      }
      
      showToast('Campos limpos com sucesso');
    }

    // Inicialização
    document.addEventListener('DOMContentLoaded', () => {
      setupCharCounter('keysInput', 'keysInputCount');
      setupCharCounter('formattedKeys', 'formattedKeysCount');
      setupCharCounter('numbersInput', 'numbersInputCount', true);
      
      document.getElementById('idsToProcess').addEventListener('input', updateProcessCount);
      document.getElementById('idsProcessed').addEventListener('input', updateProcessedCount);
      
      showSection('envelopes');
    });
  </script>
</body>
</html>
