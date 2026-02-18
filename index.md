<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Atul Sharma | Data Science</title>

  <!-- Cayman theme base styles (already active via _config.yml) will still apply.
       This is just minimal extra styling + animation. -->

  <style>
    /* Clean layout */
    .wrap { max-width: 920px; margin: 0 auto; padding: 48px 20px; }
    .kicker { font-size: 14px; letter-spacing: 0.08em; text-transform: uppercase; opacity: 0.8; }
    .headline { margin: 10px 0 8px; font-size: 42px; line-height: 1.1; }
    .subhead { font-size: 18px; opacity: 0.85; max-width: 70ch; }

    /* Cards */
    .grid { display: grid; grid-template-columns: 1fr; gap: 14px; margin-top: 22px; }
    @media (min-width: 760px) { .grid { grid-template-columns: 1fr 1fr; } }
    .card {
      border: 1px solid rgba(0,0,0,0.08);
      border-radius: 14px;
      padding: 16px 16px;
      background: rgba(255,255,255,0.9);
      box-shadow: 0 6px 18px rgba(0,0,0,0.06);
      transition: transform 160ms ease, box-shadow 160ms ease;
    }
    .card:hover { transform: translateY(-2px); box-shadow: 0 10px 28px rgba(0,0,0,0.08); }
    .card h3 { margin: 0 0 6px; font-size: 18px; }
    .muted { opacity: 0.8; }

    /* Animated flow */
    .flow {
      margin-top: 26px;
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
    }
    @media (min-width: 760px) {
      .flow { grid-template-columns: repeat(4, 1fr); gap: 12px; }
    }
    .step {
      border-radius: 999px;
      padding: 12px 14px;
      text-align: center;
      border: 1px solid rgba(0,0,0,0.10);
      background: rgba(255,255,255,0.85);
      font-weight: 600;

      /* animation initial state */
      opacity: 0;
      transform: translateY(10px);
      transition: opacity 600ms ease, transform 600ms ease;
    }
    .step.show {
      opacity: 1;
      transform: translateY(0);
    }

    .section { margin-top: 34px; }
    .section h2 { margin-bottom: 10px; }

    a { text-decoration: none; }
    a:hover { text-decoration: underline; }
    .links a { display: inline-block; margin-right: 14px; }
  </style>
</head>

<body>
  <div class="wrap">
    <div class="kicker">Data-driven decision making</div>
    <div class="headline">Atul Sharma</div>
    <div class="subhead">
      I build interpretable machine learning systems that turn real-world data into measurable decisions —
      with a focus on risk modeling, evaluation, and explainability.
    </div>

    <!-- Animated decision flow -->
    <div class="flow" id="decisionFlow" aria-label="Data to Decision flow">
      <div class="step">📊 Data</div>
      <div class="step">🤖 Model</div>
      <div class="step">📈 Insight</div>
      <div class="step">✅ Decision</div>
    </div>

    <div class="section">
      <h2>Featured Work</h2>

      <div class="grid">
        <div class="card">
          <h3>Interpretable Credit Risk Modeling</h3>
          <div class="muted">
            LendingClub loan default prediction using Logistic Regression, Decision Tree, and XGBoost.
            Evaluated with ROC-AUC (~0.70) and feature importance for interpretability.
          </div>
          <p class="links" style="margin: 12px 0 0;">
            <a href="https://github.com/atulsharma3858/credit-risk-ml-project" target="_blank" rel="noreferrer">GitHub Repo →</a>
            <a href="https://github.com/atulsharma3858/credit-risk-ml-project/tree/main/paper" target="_blank" rel="noreferrer">Paper PDF →</a>
          </p>
        </div>

        <div class="card">
          <h3>About</h3>
          <div class="muted">
            Graduate student in Big Data Science (Washington, D.C.). Interested in applied ML, analytics engineering,
            and decision science.
          </div>
          <p class="links" style="margin: 12px 0 0;">
            <a href="https://www.linkedin.com/in/atul-sharma-3858" target="_blank" rel="noreferrer">LinkedIn →</a>
            <a href="https://github.com/atulsharma3858" target="_blank" rel="noreferrer">GitHub →</a>
          </p>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Simple, professional scroll/fade animation (no libraries)
    const steps = Array.from(document.querySelectorAll("#decisionFlow .step"));
    const reveal = () => {
      const top = document.getElementById("decisionFlow").getBoundingClientRect().top;
      const trigger = window.innerHeight * 0.85;
      if (top < trigger) {
        steps.forEach((el, i) => setTimeout(() => el.classList.add("show"), i * 120));
        window.removeEventListener("scroll", reveal);
      }
    };
    window.addEventListener("scroll", reveal);
    reveal(); // run once on load
  </script>
</body>
</html>
