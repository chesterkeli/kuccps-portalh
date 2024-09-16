# kuccps-portalh
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KUCCPS Portal - Check Cutoff Points</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/css/bootstrap.min.css">
    <style>
        body {
            background-color: #f5f5f5;
        }
        .container {
            margin-top: 50px;
        }
        .card {
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        .btn-check {
            background-color: #28a745;
            color: white;
            border: none;
        }
        .btn-check:hover {
            background-color: #218838;
        }
        .result-box {
            display: none;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="card">
            <h2 class="text-center">KUCCPS Cutoff Points Checker</h2>
            <p class="text-center">Enter your KCSE score to find out the courses you're eligible for.</p>
            <form id="cutoffForm">
                <div class="mb-3">
                    <label for="kcseScore" class="form-label">KCSE Score</label>
                    <input type="number" class="form-control" id="kcseScore" placeholder="Enter your KCSE score" required>
                </div>
                <button type="submit" class="btn btn-check w-100">Check Cutoff Points</button>
            </form>

            <div class="result-box mt-4">
                <h4>Eligible Courses</h4>
                <ul id="coursesList" class="list-group"></ul>
            </div>
        </div>
    </div>

    <script>
        document.getElementById('cutoffForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const kcseScore = document.getElementById('kcseScore').value;

            // Dummy data to simulate a course check
            const courses = {
                80: ['Medicine', 'Engineering', 'Law'],
                70: ['Business Administration', 'Information Technology', 'Nursing'],
                60: ['Education', 'Hospitality Management', 'Journalism']
            };

            const resultBox = document.querySelector('.result-box');
            const coursesList = document.getElementById('coursesList');
            coursesList.innerHTML = '';

            let eligibleCourses = [];
            if (kcseScore >= 80) {
                eligibleCourses = courses[80];
            } else if (kcseScore >= 70) {
                eligibleCourses = courses[70];
            } else if (kcseScore >= 60) {
                eligibleCourses = courses[60];
            } else {
                eligibleCourses = ['No courses available for your score'];
            }

            eligibleCourses.forEach(course => {
                const listItem = document.createElement('li');
                listItem.textContent = course;
                listItem.className = 'list-group-item';
                coursesList.appendChild(listItem);
            });

            resultBox.style.display = 'block';
        });
    </script>
</body>
</html>
