<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Blood Donation Eligibility Quiz 🩸</title>
<style>
  body {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 40px auto;
    background: #fff6f6;
    color: #800000;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 15px #f2a1a1;
  }
  h1 {
    text-align: center;
    margin-bottom: 30px;
  }
  .question {
    margin-bottom: 20px;
  }
  .emoji {
    font-size: 1.4em;
    margin-right: 8px;
  }
  label {
    display: block;
    margin: 6px 0;
    cursor: pointer;
  }
  input[type="radio"] {
    margin-right: 8px;
    cursor: pointer;
  }
  button {
    background-color: #800000;
    color: white;
    border: none;
    padding: 12px 25px;
    border-radius: 6px;
    font-size: 1.1em;
    cursor: pointer;
    display: block;
    margin: 30px auto 10px;
  }
  button:hover {
    background-color: #a00000;
  }
  #result {
    margin-top: 30px;
    background: #ffdddd;
    border: 2px solid #cc0000;
    padding: 20px;
    border-radius: 8px;
    font-size: 1.3em;
    text-align: center;
  }
  #result.eligible {
    background: #ddffdd;
    border-color: #009900;
    color: #006600;
  }
</style>
</head>
<body>

<h1>🩸 Blood Donation Eligibility Quiz 🩸</h1>

<form id="quizForm">
  
  <div class="question">
    <span class="emoji">🩸</span><strong>1. Are you feeling healthy and well today?</strong>
    <label><input type="radio" name="q1" value="yes" required> Yes</label>
    <label><input type="radio" name="q1" value="no"> No</label>
  </div>

  <div class="question">
    <span class="emoji">💉</span><strong>2. Are you between 17 and 65 years old?</strong>
    <label><input type="radio" name="q2" value="yes" required> Yes</label>
    <label><input type="radio" name="q2" value="no"> No</label>
  </div>

  <div class="question">
    <span class="emoji">⚕️</span><strong>3. Do you weigh at least 110 lbs (50 kg)?</strong>
    <label><input type="radio" name="q3" value="yes" required> Yes</label>
    <label><input type="radio" name="q3" value="no"> No</label>
  </div>

  <div class="question">
    <span class="emoji">🌡️</span><strong>4. Have you had a cold, flu, or infection in the last 7 days?</strong>
    <label><input type="radio" name="q4" value="no" required> No</label>
    <label><input type="radio" name="q4" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">🩹</span><strong>5. Have you donated blood in the last 56 days?</strong>
    <label><input type="radio" name="q5" value="no" required> No</label>
    <label><input type="radio" name="q5" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">💊</span><strong>6. Are you currently taking any medication that your doctor said would disqualify you?</strong>
    <label><input type="radio" name="q6" value="no" required> No</label>
    <label><input type="radio" name="q6" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">🤒</span><strong>7. Have you ever had hepatitis, HIV/AIDS, or other blood-borne infections?</strong>
    <label><input type="radio" name="q7" value="no" required> No</label>
    <label><input type="radio" name="q7" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">🩺</span><strong>8. Have you had any major surgery or tattoo in the past 12 months?</strong>
    <label><input type="radio" name="q8" value="no" required> No</label>
    <label><input type="radio" name="q8" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">🤰</span><strong>9. Are you currently pregnant or breastfeeding?</strong>
    <label><input type="radio" name="q9" value="no" required> No</label>
    <label><input type="radio" name="q9" value="yes"> Yes</label>
  </div>

  <div class="question">
    <span class="emoji">💔</span><strong>10. Do you have any heart problems or chronic diseases your doctor has warned about?</strong>
    <label><input type="radio" name="q10" value="no" required> No</label>
    <label><input type="radio" name="q10" value="yes"> Yes</label>
  </div>

  <button type="submit">See My Result</button>
</form>

<div id="result"></div>

<script>
  const form = document.getElementById('quizForm');
  const resultDiv = document.getElementById('result');

  form.addEventListener('submit', function(event) {
    event.preventDefault();

    // Get all answers
    const answers = new FormData(form);

    // Check eligibility rules:
    // If any "no" where "yes" required, or any "yes" where "no" required, disqualify

    // Questions where answer must be "yes" to be eligible: 1, 2, 3
    if (answers.get('q1') !== 'yes') {
      showResult(false, "You need to be feeling healthy to donate blood.");
      return;
    }
    if (answers.get('q2') !== 'yes') {
      showResult(false, "You must be between 17 and 65 years old to donate.");
      return;
    }
    if (answers.get('q3') !== 'yes') {
      showResult(false, "You must weigh at least 110 lbs (50 kg) to donate.");
      return;
    }

    // Questions where answer must be "no" to be eligible: 4,5,6,7,8,9,10
    const disqualifyingQuestions = ['q4','q5','q6','q7','q8','q9','q10'];
    for (const q of disqualifyingQuestions) {
      if (answers.get(q) === 'yes') {
        const reasons = {
          q4: "You can't donate if you’ve had a cold, flu, or infection in the last 7 days.",
          q5: "You need to wait at least 56 days between donations.",
          q6: "Certain medications may disqualify you from donating.",
          q7: "History of hepatitis, HIV/AIDS, or blood infections disqualifies you.",
          q8: "Recent surgery or tattoos (within 12 months) can disqualify you.",
          q9: "Pregnant or breastfeeding women cannot donate at this time.",
          q10: "Certain heart or chronic conditions may prevent donation."
        };
        showResult(false, reasons[q]);
        return;
      }
    }

    // If passed all checks:
    showResult(true, "Congratulations! You are likely eligible to donate blood. Please visit your local blood donation center to confirm.");
  });

  function showResult(isEligible, message) {
    if (isEligible) {
      resultDiv.className = "eligible";
      resultDiv.innerHTML = "✅ <strong>Eligible to Donate:</strong><br>" + message;
    } else {
      resultDiv.className = "";
      resultDiv.innerHTML = "❌ <strong>Not Eligible:</strong><br>" + message;
    }
  }
</script>

</body>
</html>
