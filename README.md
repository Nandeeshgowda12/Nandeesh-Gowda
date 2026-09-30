<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Anime Login</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;

            background:
                radial-gradient(circle at 20% 20%, #6a00ff55, transparent 30%),
                radial-gradient(circle at 80% 80%, #00eaff44, transparent 30%),
                linear-gradient(135deg, #050014, #09001f, #00182b);

            color: white;
        }

        /* Animated background */
        .background {
            position: fixed;
            inset: 0;
            overflow: hidden;
            z-index: -1;
        }

        .circle {
            position: absolute;
            border-radius: 50%;
            filter: blur(2px);
            animation: float 8s infinite ease-in-out;
        }

        .circle:nth-child(1) {
            width: 180px;
            height: 180px;
            background: #8a2be2;
            left: 10%;
            top: 10%;
        }

        .circle:nth-child(2) {
            width: 250px;
            height: 250px;
            background: #00d9ff;
            right: 5%;
            bottom: 5%;
            animation-delay: 2s;
        }

        .circle:nth-child(3) {
            width: 100px;
            height: 100px;
            background: #ff00cc;
            right: 30%;
            top: 15%;
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) scale(1);
            }

            50% {
                transform: translateY(-40px) scale(1.15);
            }
        }

        /* Login box */
        .login-box {
            width: 380px;
            padding: 45px 35px;

            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 25px;

            backdrop-filter: blur(20px);

            box-shadow:
                0 0 30px #7b2cff55,
                inset 0 0 20px #ffffff08;

            text-align: center;

            animation: appear 1.2s ease;
        }

        @keyframes appear {
            from {
                opacity: 0;
                transform: translateY(50px) scale(0.9);
            }

            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        /* Anime symbol */
        .anime-symbol {
            font-size: 60px;
            margin-bottom: 10px;

            text-shadow:
                0 0 10px #00eaff,
                0 0 30px #8a2be2;

            animation: glow 2s infinite alternate;
        }

        @keyframes glow {
            from {
                transform: scale(1);
                text-shadow:
                    0 0 10px #00eaff;
            }

            to {
                transform: scale(1.1);
                text-shadow:
                    0 0 20px #ff00cc,
                    0 0 40px #00eaff;
            }
        }

        h1 {
            font-size: 32px;
            margin-bottom: 8px;

            background: linear-gradient(
                90deg,
                #00eaff,
                #ffffff,
                #ff00cc
            );

            -webkit-background-clip: text;
            color: transparent;
        }

        .subtitle {
            color: #bbb;
            font-size: 14px;
            margin-bottom: 30px;
        }

        /* Input */
        .input-box {
            position: relative;
            margin: 22px 0;
        }

        .input-box span {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 20px;
        }

        .input-box input {
            width: 100%;
            padding: 15px 45px;

            border: 1px solid #ffffff22;
            border-radius: 12px;

            outline: none;

            background: rgba(0, 0, 0, 0.25);
            color: white;

            font-size: 15px;

            transition: 0.3s;
        }

        .input-box input:focus {
            border-color: #00eaff;

            box-shadow:
                0 0 10px #00eaff88,
                0 0 25px #8a2be255;
        }

        .input-box input::placeholder {
            color: #aaa;
        }

        /* Password eye */
        .eye {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);

            cursor: pointer;
            font-size: 18px;
        }

        /* Options */
        .options {
            display: flex;
            justify-content: space-between;
            align-items: center;

            font-size: 13px;
            margin: 15px 0 25px;
        }

        .options label {
            color: #bbb;
        }

        .options a {
            color: #00eaff;
            text-decoration: none;
        }

        /* Button */
        button {
            width: 100%;
            padding: 15px;

            border: none;
            border-radius: 12px;

            cursor: pointer;

            color: white;
            font-size: 16px;
            font-weight: bold;

            background: linear-gradient(
                90deg,
                #6a00ff,
                #00c6ff,
                #ff00cc
            );

            background-size: 200%;

            box-shadow:
                0 0 15px #7b2cff88;

            transition: 0.4s;
        }

        button:hover {
            background-position: right;

            transform: translateY(-3px);

            box-shadow:
                0 0 20px #00eaff,
                0 0 40px #ff00cc55;
        }

        button:active {
            transform: scale(0.97);
        }

        /* Register */
        .register {
            margin-top: 25px;
            color: #aaa;
            font-size: 14px;
        }

        .register a {
            color: #00eaff;
            text-decoration: none;
            font-weight: bold;
        }

        /* Floating symbols */
        .symbol {
            position: absolute;
            color: #ffffff55;
            font-size: 25px;
            animation: symbolFloat 6s infinite ease-in-out;
        }

        .s1 {
            left: 10%;
            top: 20%;
        }

        .s2 {
            right: 15%;
            top: 25%;
            animation-delay: 1s;
        }

        .s3 {
            left: 20%;
            bottom: 15%;
            animation-delay: 2s;
        }

        .s4 {
            right: 25%;
            bottom: 20%;
            animation-delay: 3s;
        }

        @keyframes symbolFloat {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
                opacity: 0.3;
            }

            50% {
                transform: translateY(-30px) rotate(180deg);
                opacity: 1;
            }
        }

        /* Mobile */
        @media (max-width: 500px) {
            .login-box {
                width: 90%;
                padding: 35px 25px;
            }

            h1 {
                font-size: 27px;
            }
        }
    </style>
</head>

<body>

    <!-- Background -->
    <div class="background">
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
    </div>

    <!-- Floating anime symbols -->
    <div class="symbol s1">✦</div>
    <div class="symbol s2">✧</div>
    <div class="symbol s3">◇</div>
    <div class="symbol s4">✦</div>

    <!-- Login -->
    <div class="login-box">

        <div class="anime-symbol">⚔️</div>

        <h1>ANIME LOGIN</h1>

        <p class="subtitle">
            Enter the world of warriors
        </p>

        <form id="loginForm">

            <div class="input-box">
                <span>👤</span>

                <input
                    type="text"
                    id="username"
                    placeholder="Username"
                    required
                >
            </div>

            <div class="input-box">
                <span>🔒</span>

                <input
                    type="password"
                    id="password"
                    placeholder="Password"
                    required
                >

                <span
                    class="eye"
                    onclick="togglePassword()"
                >
                    👁️
                </span>
            </div>

            <div class="options">

                <label>
                    <input type="checkbox">
                    Remember me
                </label>

                <a href="#">
                    Forgot password?
                </a>

            </div>

            <button type="submit">
                ENTER THE WORLD ⚡
            </button>

        </form>

        <p class="register">
            New warrior?
            <a href="#">Create Account</a>
        </p>

    </div>

    <script>

        /* Show / Hide password */

        function togglePassword() {

            const password =
                document.getElementById("password");

            if (password.type === "password") {
                password.type = "text";
            } else {
                password.type = "password";
            }
        }


        /* Login button */

        document
            .getElementById("loginForm")
            .addEventListener("submit", function(event) {

                event.preventDefault();

                const username =
                    document.getElementById("username").value;

                const password =
                    document.getElementById("password").value;

                if (username && password) {

                    alert(
                        "Welcome, " +
                        username +
                        " ⚡"
                    );

                }

            });

    </script>

</body>
</html>
