<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Student Registration Form</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 30px;
        }

        .container {
            width: 400px;
            max-width: 90%;
            margin: auto;
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 10px #aaa;
        }

        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 25px;
        }

        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }

        input,
        select {
            width: 100%;
            padding: 10px;
            margin-top: 6px;
            box-sizing: border-box;
            border: 1px solid #aaa;
            border-radius: 5px;
        }

        button {
            width: 100%;
            padding: 12px;
            margin-top: 25px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        .error {
            color: red;
            font-size: 14px;
            margin-top: 5px;
        }

        #success {
            color: green;
            text-align: center;
            font-weight: bold;
            margin-top: 15px;
        }
    </style>
</head>

<body>

    <div class="container">

        <h1>Student Registration</h1>

        <form id="registrationForm">

            <!-- Name -->
            <label for="name">Full Name</label>
            <input type="text" id="name" placeholder="Enter your name">
            <div id="nameError" class="error"></div>

            <!-- Email -->
            <label for="email">Email</label>
            <input type="text" id="email" placeholder="Enter your email">
            <div id="emailError" class="error"></div>

            <!-- Mobile -->
            <label for="mobile">Mobile Number</label>
            <input type="text" id="mobile" placeholder="Enter 10-digit mobile number">
            <div id="mobileError" class="error"></div>

            <!-- Password -->
            <label for="password">Password</label>
            <input type="password" id="password" placeholder="Enter password">
            <div id="passwordError" class="error"></div>

            <!-- Course -->
            <label for="course">Select Course</label>
            <select id="course">
                <option value="">-- Select Course --</option>
                <option value="ETC">ETC</option>
                <option value="CSE">CSE</option>
                <option value="IT">IT</option>
                <option value="Mechanical">Mechanical</option>
                <option value="Civil">Civil</option>
            </select>
            <div id="courseError" class="error"></div>

            <!-- Submit -->
            <button type="submit">Register</button>

            <div id="success"></div>

        </form>

    </div>


    <script>

        // Get form
        const form = document.getElementById("registrationForm");

        // Add submit event listener
        form.addEventListener("submit", function(event) {

            // Stop form from submitting immediately
            event.preventDefault();

            // Get values
            const name = document.getElementById("name").value.trim();
            const email = document.getElementById("email").value.trim();
            const mobile = document.getElementById("mobile").value.trim();
            const password = document.getElementById("password").value;
            const course = document.getElementById("course").value;

            // Error elements
            const nameError = document.getElementById("nameError");
            const emailError = document.getElementById("emailError");
            const mobileError = document.getElementById("mobileError");
            const passwordError = document.getElementById("passwordError");
            const courseError = document.getElementById("courseError");
            const success = document.getElementById("success");

            // Clear previous messages
            nameError.textContent = "";
            emailError.textContent = "";
            mobileError.textContent = "";
            passwordError.textContent = "";
            courseError.textContent = "";
            success.textContent = "";

            let valid = true;


            // Name validation
            if (name === "") {
                nameError.textContent = "Name is required.";
                valid = false;
            }


            // Email validation
            const emailPattern =
                /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

            if (email === "") {
                emailError.textContent = "Email is required.";
                valid = false;
            }
            else if (!emailPattern.test(email)) {
                emailError.textContent = "Enter a valid email address.";
                valid = false;
            }


            // Mobile validation
            const mobilePattern = /^[0-9]{10}$/;

            if (mobile === "") {
                mobileError.textContent = "Mobile number is required.";
                valid = false;
            }
            else if (!mobilePattern.test(mobile)) {
                mobileError.textContent =
                    "Mobile number must contain exactly 10 digits.";
                valid = false;
            }


            // Password validation
            if (password === "") {
                passwordError.textContent = "Password is required.";
                valid = false;
            }
            else if (password.length < 6) {
                passwordError.textContent =
                    "Password must be at least 6 characters.";
                valid = false;
            }


            // Course validation
            if (course === "") {
                courseError.textContent = "Please select a course.";
                valid = false;
            }


            // Final result
            if (valid) {

                success.textContent =
                    "Registration successful!";

                // Clear form
                form.reset();
            }

        });

    </script>

</body>
</html>
