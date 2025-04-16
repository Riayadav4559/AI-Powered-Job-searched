# AI-Powered-Job-searched
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AI Job Search Platform</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 600px;
      margin: 50px auto;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      text-align: center;
    }

    input {
      padding: 10px;
      width: 80%;
      margin-bottom: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
    padding: 10px 20px;
    background: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
      cursor: pointer;
    }

    .results {
      margin-top: 20px;
      text-align: left;
    }

    .job-card {
      background: #e8f0fe;
      padding: 10px;
      margin: 10px 0;
      border-left: 4px solid #007bff;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>AI Job Search</h1>
    <input type="text" id="skillInput" placeholder="Enter your skills (comma-separated)" />
    <button onclick="matchJobs()">Find Jobs</button>

    <div id="jobResults" class="results"></div>
  </div>

  <script>
    const jobs = [
      { title: "Frontend Developer", skills: ["HTML", "CSS", "JavaScript"] },
      { title: "Data Analyst", skills: ["Python", "SQL", "Excel"] },
      { title: "Backend Developer", skills: ["Node.js", "MongoDB", "JavaScript"] },
      { title: "ML Engineer", skills: ["Python", "Pandas", "Scikit-learn"] },
      { title: "Android Developer", skills: ["Java", "Kotlin", "Android Studio"] },
    ];

    function matchJobs() {
      const input = document.getElementById("skillInput").value.toLowerCase().split(",");
      const cleanedSkills = input.map(skill => skill.trim());

      const matchedJobs = jobs.filter(job => {
        return job.skills.some(skill => cleanedSkills.includes(skill.toLowerCase()));
      });

      const resultDiv = document.getElementById("jobResults");
      resultDiv.innerHTML = "";

      if (matchedJobs.length === 0) {
        resultDiv.innerHTML = "<p>No matching jobs found.</p>";
        return;
      }

      matchedJobs.forEach(job => {
        const div = document.createElement("div");
        div.className = "job-card";
        div.innerHTML = `<h3>${job.title}</h3><p>Required Skills: ${job.skills.join(", ")}</p>`;
        resultDiv.appendChild(div);
      });
    }
  </script>
</body>
</html>
