<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background-color: #fff;
            width: 100%;
            max-width: 500px;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            color: #333;
        }

        .input-group {
            margin-bottom: 20px;
        }

        label {
            font-size: 16px;
            color: #555;
            margin-bottom: 5px;
            display: block;
        }

        input[type="date"] {
            width: 100%;
            padding: 12px;
            font-size: 16px;
            border-radius: 6px;
            border: 1px solid #ddd;
            background-color: #f9f9f9;
            outline: none;
            transition: border 0.3s ease;
        }

        input[type="date"]:focus {
            border: 1px solid #4CAF50;
        }

        button {
            width: 100%;
            padding: 15px;
            font-size: 18px;
            color: white;
            background-color: #4CAF50;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #45a049;
        }

        .result {
            text-align: center;
            font-size: 20px;
            color: #333;
            font-weight: bold;
            margin-top: 20px;
        }

        .result span {
            color: #4CAF50;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Age Calculator</h2>
        
        <!-- Input for Date of Birth -->
        <div class="input-group">
            <label for="dob">Enter Your Date of Birth:</label>
            <input type="date" id="dob" name="dob">
        </div>

        <!-- Calculate Button -->
        <button onclick="calculateAge()">Calculate Age</button>

        <!-- Display Result -->
        <div class="result" id="ageResult"></div>
    </div>

    <script>
        function calculateAge() {
            // Get the selected date of birth value
            var dob = document.getElementById("dob").value;
            
            // Check if the date is not empty
            if (!dob) {
                document.getElementById("ageResult").innerText = "Please select your date of birth.";
                return;
            }

            // Parse the date of birth
            var birthDate = new Date(dob);
            var today = new Date();

            // Calculate the age
            var age = today.getFullYear() - birthDate.getFullYear();
            var monthDifference = today.getMonth() - birthDate.getMonth();

            // If the birthday hasn't occurred yet this year, subtract one from the age
            if (monthDifference < 0 || (monthDifference === 0 && today.getDate() < birthDate.getDate())) {
                age--;
            }

            // Display the result
            document.getElementById("ageResult").innerHTML = "Your Age is: <span>" + age + " years</span>";
        }
    </script>

</body>
</html>
