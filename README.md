
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  
  <meta name="description" content="AI-powered ATS resume screening bot using Telegram, n8n, and Google Gemini. Processes PDF/ZIP resumes, generates ATS scores, extracts details, and auto-logs results into Google Sheets."/>
 
</head>
<body>
  <main class="wrap" role="main">
    <header>
 <div>
      <div>
        <h1>AI-Powered ATS Resume Screening Bot (Telegram + n8n + Gemini)📋</h1>
        <p class="lead">AI-powered ATS resume screening system built with Telegram, n8n Agentic AI, and Google Gemini. Automatically processes PDF/ZIP resumes, extracts candidate details, generates ATS scores with LLM evaluation, and logs eligible profiles into Google Sheets for seamless HR and placement workflows.</p>
        
      
 <div>
    <div class="grid">
      <section class="card">
        <h2>Quick overview</h2>
        <p>This project automates early-stage hiring by evaluating resumes with an LLM-driven ATS evaluator. Candidates upload a single PDF or a ZIP of resumes via Telegram; n8n handles file extraction, agentic prompt construction, and Google Gemini evaluation. Results (Name, Email, Mobile, ATS_Score) are written to Google Sheets and candidates are auto-classified (Accepted if score &gt; 70), and also check ATS score of you resume</p>
 <div>
        <h2>Features</h2>
        <ul>
          <li>Accepts PDF or ZIP uploads via Telegram</li>
          <li>Extracts text from PDFs (single or bulk)</li>
          <li>Agentic AI prompts (n8n LangChain node) → Google Gemini LLM</li>
          <li>Returns structured JSON: <code>{ "Name", "Email", "Mobile No", "ATS_Score" }</code></li>
          <li>Auto-classifies &amp; appends to Google Sheets (Accepted / Rejected)</li>
        </ul>
 <div>
        <h2>System flow (condensed)</h2>
        <pre><code>Telegram Trigger
  └─ Switch -> PDF or ZIP
     ├─ PDF: Extract -> AI Agent -> Clean JSON -> IF (Score>70) -> Google Sheets
     └─ ZIP: Unzip -> Loop -> Extract -> AI Agent -> Clean JSON -> IF -> Google Sheets
</code></pre>

  <h2>ATS Resume Screening Bot</h2> 


https://github.com/user-attachments/assets/50545100-41c5-4822-928b-b139f3be3b7e





   <h2>ATS Resume ATS Score Checker Bot</h2> 
   



https://github.com/user-attachments/assets/5f3db74a-e81e-401c-b440-c0df15cdcb0d



 <div>
        <h2>Quick usage</h2>
        <ol>
          <li>Import <code>workflow.json</code> into n8n.</li>
          <li>Add Telegram Bot credentials and link to the Telegram Trigger node.</li>
          <li>Configure Google Sheets OAuth and set Accepted/Rejected sheet IDs.</li>
          <li>Provide Google Gemini (PaLM) API credential to the LangChain node.</li>
          <li>Activate the workflow and test by uploading a PDF or ZIP in Telegram.</li>
        </ol>
 <div>
        <h2>Example output</h2>
        <pre><code>{
  "Name": "Jane Doe",
  "Email": "jane.doe@example.com",
  "Mobile No": "9123456789",
  "ATS_Score": 82
}</code></pre>
 <div>
        <h2>Environment variables & config</h2>
        <ul>
          <li><code>TELEGRAM_BOT_TOKEN</code> — Telegram Bot API token</li>
          <li><code>GOOGLE_SHEETS_ID</code> — Spreadsheet ID (Accepted/Rejected sheets)</li>
          <li><code>GOOGLE_PALM_API_KEY</code> — Google Gemini / PaLM credential</li>
          <li>n8n nodes: set proper credentials for Telegram, Google Sheets, and Google Palm in n8n UI</li>
        </ul>
 <div>
        <h2>Extensibility ideas</h2>
        <ul>
          <li>Dashboard for analytics (accepted / rejected counts, top failing reasons)</li>
          <li>Job-role-specific keyword matching & scoring</li>
          <li>Auto-email feedback to candidates</li>
          <li>Integrate resume rewrite suggestions (LLM-driven fixes)</li>
        </ul>
      </section>
 <div>
      <aside class="card">
        <h2>Files included</h2>
        <ul>
          <li><code>Advance ATS Bot.json</code> — n8n workflow export (import into n8n)</li>
          <li><code>README.html</code> — this file</li>
          <li><code>.env.example</code> — sample env config (optional)</li>
        </ul>
 <div>
        <h2>How to import workflow</h2>
        <ol>
          <li>Open n8n → Workflows → Import</li>
          <li>Upload <code>Advance ATS Bot.json</code></li>
          <li>Set node credentials (Telegram, Google Sheets, Google Palm)</li>
          <li>Activate workflow</li>
        </ol>
 <div>
        <h2>Google Sheets</h2>
        <p>Create a spreadsheet with two sheets (tabs):</p>
        <ul>
          <li><strong>Accepted</strong> — headers: Name, Email, Mobile No, ATS_Score</li>
          <li><strong>Rejected</strong> — same headers for tracking</li>
        </ul>
 <div>
     
 <div>
      
  

  
 <div>
    <footer>
      <div>Made with ❤️ · Advance ATS Bot — Telegram + n8n + Google Gemini</div>
    </footer>
  </main>
</body>
</html>
