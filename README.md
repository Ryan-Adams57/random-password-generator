<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Password Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f9;
        }
        .container {
            background-color: white;
            border-radius: 8px;
            padding: 30px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
        }
        h1 {
            text-align: center;
            font-size: 24px;
            margin-bottom: 20px;
        }
        label {
            font-size: 16px;
        }
        select, input[type="number"], button {
            padding: 10px;
            font-size: 16px;
            margin-top: 10px;
            width: 100%;
            max-width: 300px;
            display: block;
            margin-bottom: 15px;
        }
        #generatedPassword {
            font-size: 18px;
            font-weight: bold;
            margin-top: 20px;
            word-wrap: break-word;
            text-align: center;
            padding: 15px;
            background-color: #f2f2f2;
            border: 1px solid #ddd;
        }
        .footer {
            text-align: center;
            margin-top: 30px;
            font-size: 12px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Random Password Generator</h1>
    <p>Type in the desired password length and select the type of password.</p>

    <label for="length">Password Length (8-20 characters):</label>
    <input type="number" id="length" value="12" min="8" max="20">

    <label for="passwordType">Password Type:</label>
    <select id="passwordType">
        <option value="alphanumeric">Alphanumeric (letters + numbers)</option>
        <option value="numeric">Numeric (only numbers)</option>
    </select>

    <button id="generateBtn">Generate Password</button>

    <div id="generatedPassword">Your generated password will appear here.</div>

    <div class="footer">
        <p>All passwords are generated on your browser so nothing is stored online. You're the only one who has knowledge of the generated password.</p>
    </div>
</div>

<script>
    document.getElementById("generateBtn").addEventListener("click", function() {
        const length = document.getElementById("length").value;
        const passwordType = document.getElementById("passwordType").value;
        const password = generatePassword(length, passwordType);
        document.getElementById("generatedPassword").textContent = "Generated Password: " + password;
    });

    function generatePassword(length, type) {
        const alphabets = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
        const numbers = "0123456789";
        const specialChars = "!@#$%^&*()_+[]{}|;:,.<>?";

        let characters = "";
        if (type === "alphanumeric") {
            characters = alphabets + numbers + specialChars;
        } else if (type === "numeric") {
            characters = numbers;
        }

        let password = "";
        for (let i = 0; i < length; i++) {
            password += characters.charAt(Math.floor(Math.random() * characters.length));
        }

        return password;
    }
</script>

</body>
</html>
