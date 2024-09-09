<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Strength   
 Checker</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f5f5f5;
            text-align: center;
        }

        .container {
            margin: 20px auto;
            padding: 40px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 400px;
        }

        h1 {
            font-size: 28px;
            margin-bottom: 20px;
        }

        .password-input-container {
            position: relative;
        }

        #password {
            width: 100%;
            padding: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin-bottom: 20px;
        }

        .show-password-button {
            position: absolute;
            top: 50%;
            right: 10px;
            transform: translateY(-50%);
            cursor: pointer;
            transition: color 0.3s ease-in-out;
        }

        .show-password-button:hover {
            color: blue;
        }

        #strength-meter {
            width: 100%;
            height: 30px;
            background-color: #ccc;
            border-radius: 5px;
            overflow: hidden;
        }

        #meter-bar {
            height: 100%;
            background-color: red;
            transition: width 0.3s ease-in-out;
        }

        #strength-text {
            font-size: 18px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Password Strength Checker</h1>
        <div class="password-input-container">
            <input type="password" id="password"   
 placeholder="Enter Your Password">
            <span class="show-password-button">👁️</span>
        </div>
        <div id="strength-meter">
            <div id="meter-bar"></div>
        </div>
        <p id="strength-text"></p>
    </div>
    <script>
        const passwordInput = document.getElementById('password');
        const meterBar = document.getElementById('meter-bar');
        const strengthText = document.getElementById('strength-text');
        const showPasswordButton = document.querySelector('.show-password-button');

        
        meterBar.style.width = '0%';
        meterBar.style.backgroundColor = 'red';
        strengthText.textContent = 'Empty 🙁';

        passwordInput.addEventListener('input', () => {
            const password = passwordInput.value;

            
            let strength = 0;
            if (password.length >= 8) strength++;
            if (password.match(/[A-Z]/)) strength++;
            if (password.match(/[a-z]/)) strength++;
            if (password.match(/[0-9]/)) strength++;
            if (password.match(/[!@#$%^&*()]/))   
 strength++;   


            
            const meterWidth = (strength / 5) * 100;
            meterBar.style.width = meterWidth + '%';
            if (strength === 0) {
                meterBar.style.backgroundColor = 'red';
                strengthText.textContent = 'Empty 😶';
            } else if (strength === 1 || strength === 2) {
                meterBar.style.backgroundColor = 'red';
                strengthText.textContent = 'Weak 🙁';
            } else if (strength === 3 || strength === 4) {
                meterBar.style.backgroundColor = 'orange';
                strengthText.textContent = 'Medium 🙂';
            } else {
                meterBar.style.backgroundColor = 'green';
                strengthText.textContent = 'Strong 😀';
            }
        });

        showPasswordButton.addEventListener('click', () => {
            if (passwordInput.type === 'password') {
                passwordInput.type = 'text';
            } else {
                passwordInput.type = 'password';
            }
        });
    </script>
</body>   

</html>
