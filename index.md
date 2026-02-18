<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Atul Sharma | Data Science</title>

  <style>
    /* Layout */
    .wrap { max-width: 920px; margin: 0 auto; padding: 48px 20px; }
    .kicker { font-size: 14px; letter-spacing: 0.08em; text-transform: uppercase; opacity: 0.8; }
    .headline { margin: 10px 0 8px; font-size: 42px; line-height: 1.1; }
    .subhead { font-size: 18px; opacity: 0.85; max-width: 70ch; }

    /* Image motion */
    .image-wrap {
      margin: 26px 0 10px;
      display: flex;
      justify-content: center;
    }
    .motion-image {
      width: 100%;
      max-width: 820px;
      border-radius: 18px;
      box-shadow: 0 18px 40px rgba(0,0,0,0.25);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
      will-change: transform;
      cursor: pointer;
    }
    .motion-image:hover {
      box-shadow: 0 28px 70px rgba(0,100,255,0.35);
    }

    /* Cards */
    .grid { display: grid; grid-template-columns: 1fr; gap: 14px; margin-top: 22px; }
    @media (min-width: 760px) { .grid { grid-template-columns: 1fr 1fr; } }

    .card {
      border: 1px solid rgba(0,0,0,0.08);
      border-radius: 14px;
      padding: 16px;
      background: rgba(255,255,255,0.95);
      box-shadow: 0 6px 18px rgba(0,0,0,0.06);
      transition: transform 160ms ease, box-shadow 160ms ease;
    }
    .card:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 28px rgba(0,0,0,0.08);
    }
    .card h3 { margin: 0 0 6px; font-size: 18px; }
    .muted { opacity: 0.8; }

    /* Flow animation */
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
      background: rgba(255,255,255,0.9);
      font-weight: 600;
      opacity: 0;
      transform: translateY(10px);
      transition: opacity 600ms ease, transform 600ms ease;
    }
    .step.show {
      opacity: 1;
      transform: translateY(0);
    }

    .section { margin-top: 34px; }
    a { text-decoration: none; }
    a:hover { text-decoration: underline; }
    .links a { margin-right: 14px; }
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

    <!-- Motion Image -->
    <div class="image-wrap">
      <img
        src="assets/images/data-driven-decisions.jpg"
        alt="Data-driven decision making"
        class="motion-image"
        id="motionImage"
      />
    </div>

    <!-- Animated Flow -->
    <div class="flow" id="decisionFlow">
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
            ROC-AUC ≈ 0.70 with feature importance and explainability.
          </div>
          <p class="links" style="margin-top: 12px;">
            <a href="https://github.com/atulsharma3858/credit-risk-ml-project" target="_blank">GitHub →</a>
            <a href="https://github.com/atulsharma3858/credit-risk-ml-project/tree/main/paper" target="_blank">Paper →</a>
          </p>
        </div>

        <div class="card">
          <h3>About</h3>
          <div class="muted">
            Graduate student in Big Data Science (Washington, D.C.).
            Interested in applied ML, analytics engineering, and decision science.
          </div>
          <p class="links" style="margin-top: 12px;">
            <a href="https://www.linkedin.com/in/atul-sharma-3858" target="_blank">LinkedIn →</a>
            <a href="https://github.com/atulsharma3858" target="_blank">GitHub →</a>
          </p>
        </div>
      </div>
    </div>
  </div>

  <!-- Scripts -->
  <script>
    // Image tilt motion
    const img = document.getElementById("motionImage");
    if (img) {
      img.addEventListener("mousemove", (e) => {
        const r = img.getBoundingClientRect();
        const x = e.clientX - r.left;
        const y = e.clientY - r.top;
        const rx = ((y / r.height) - 0.5) * -10;
        const ry = ((x / r.width) - 0.5) * 10;
        img.style.transform =
          `perspective(1000px) rotateX(${rx}deg) rotateY(${ry}deg) scale(1.04)`;
      });
      img.addEventListener("mouseleave", () => {
        img.style.transform =
          "perspective(1000px) rotateX(0deg) rotateY(0deg) scale(1)";
      });
    }

    // Flow reveal animation
    const steps = document.querySelectorAll("#decisionFlow .step");
    const reveal = () => {
      const top = document.getElementById("decisionFlow").getBoundingClientRect().top;
      if (top < window.innerHeight * 0.85) {
        steps.forEach((el, i) =>
          setTimeout(() => el.classList.add("show"), i * 120)
        );
        window.removeEventListener("scroll", reveal);
      }
    };
    window.addEventListener("scroll", reveal);
    reveal();
  </script>
</body>
</html>
