
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PREDICTION OF MEDICINE BY SYMPTOMS</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 110vh;   
      background: url('http://www.philipgordts.com/wp-content/uploads/2018/03/medical-website-background-images-7.jpg') no-repeat center center fixed;
      background-size: cover;
      color: #111010;
      margin: 0;
      padding: 0;
    }

    #container {
      background-color: rgba(255, 255, 255, 0.8);
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      width: 400px;
      text-align: center;
    }

    label {
      display: block;
      margin-bottom: 8px;
      color: #0e0c0c;
    }

    input, select, textarea {
      width: 100%;
      padding: 8px;
      margin-bottom: 16px;
      box-sizing: border-box;
    }

    button {
      background-color: #4caf50;
      color: #fff;
      padding: 10px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }

    #medicalHistorySection {
      display: none;
    }

    #results {
      margin-top: 20px;   
    }
    /* Add some space between the checkbox and the button */
    #termsCheckbox {
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div id="container">
    <h2>PREDICTION OF MEDICINE SYMPTOMS</h2>
    <label for="symptoms">Symptoms:</label>
    <input type="text" id="symptoms" placeholder="Enter symptoms" required>

    <label for="medicalHistory">Do you have a medical history?</label>
    <select id="medicalHistory" onchange="toggleMedicalHistory()">
      <option value="no">No</option>
      <option value="yes">Yes</option>
    </select>

    <div id="medicalHistorySection">
      <label for="historyDetails">Medical History Details:</label>
      <textarea id="historyDetails" placeholder="Enter medical history details:" rows="4"></textarea>
    </div>

    <label for="age">Age:</label>
    <input type="number" id="age" placeholder="Enter your age" required>

    <!-- Add the checkbox for terms and conditions -->
    <input type="checkbox" id="termsCheckbox" required>
    <label for="termsCheckbox">I take complete responsibility for prescription</label>
    <input type="checkbox" id="termsCheckbox" required>
    <label for="termsCheckbox">I agree to the terms and conditions</label>
    <button onclick="recommendMedicine()">Get Recommendation</button>

    <div id="results"></div>
  </div>

  <script>
    function toggleMedicalHistory() {
      const medicalHistorySection = document.getElementById("medicalHistorySection");
      const medicalHistoryValue = document.getElementById("medicalHistory").value;

      medicalHistorySection.style.display = medicalHistoryValue === "yes" ? "block" : "none";
    }

    function recommendMedicine() {
      // Check if the checkbox for terms and conditions is checked
      const termsCheckbox = document.getElementById("termsCheckbox");
      if (!termsCheckbox.checked) {
        alert("Please agree to the terms and conditions before getting a recommendation.");
        return;
      }

      const symptoms = document.getElementById("symptoms").value;
      const medicalHistory = document.getElementById("medicalHistory").value;
      const historyDetails = document.getElementById("historyDetails").value;
      const age = document.getElementById("age").value;

      // You would typically make an API call to a back-end server to retrieve medicine recommendations
      // For this example, let's simulate results
      const medicinea = "medicineA";
      const compositiona = "compositionA";
      const medicineb = "medicineB";
      const compositionb = "compositionB";
      const dosage = determineDosage(age);
      const ageGroup = determineAgeGroup(age);

      // Display results
      const resultsDiv = document.getElementById("results");
      resultsDiv.innerHTML = <p><strong>Recommended Medicine 1:</strong> ${medicinea}</p>;
      resultsDiv.innerHTML += <p><strong>Composition 1:</strong> ${compositiona}</p>;
      resultsDiv.innerHTML += <p><strong>Recommended Medicine 2:</strong> ${medicineb}</p>;
      resultsDiv.innerHTML += <p><strong>Composition 2:</strong> ${compositionb}</p>;
      resultsDiv.innerHTML += <p><strong>Dosage:</strong> ${dosage}</p>;
      resultsDiv.innerHTML += <p><strong>Age Group:</strong> ${ageGroup}</p>;
    }

    function determineDosage(age) {
      if (age < 12) {
        return "take half after food";
      } else if (age >= 12 && age < 18) {
        return "take two 1-morning & 2-afternoon after food";
      } else {
        return "take three 1-morning & 2-afternoon & 3-evening after food";
      }
    }

    function determineAgeGroup(age) {
      if (age < 12) {
        return "Child";
      } else if (age >= 12 && age < 18) {
        return "Teenager";
      } else {
        return "Adult";
      }
    }
  </script>
</body>
</html>
