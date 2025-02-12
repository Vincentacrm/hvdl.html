<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Valentine's Day</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #fff0f5;
            color: #c71585;
            padding: 0;
            margin: 0;
        }

        h1 {
            font-size: 3em;
            margin-top: 20px;
        }

        .heart {
            font-size: 100px;
            color: #ff1493;
        }

        .compliment {
            font-size: 1.5em;
            margin: 20px 0;
        }

        #message {
            font-size: 1.2em;
            margin: 20px;
            padding: 10px;
            width: 60%;
            border: 2px solid #ff1493;
            border-radius: 10px;
            outline: none;
        }

        button {
            background-color: #ff1493;
            color: white;
            padding: 10px 20px;
            font-size: 1em;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }

        button:hover {
            background-color: #ff69b4;
        }

        .footer {
            margin-top: 30px;
            font-size: 1.2em;
            color: #8b008b;
        }

    </style>
</head>
<body>

    <div>
        <h1>Happy Valentine's Day! 💖</h1>
        <div class="heart">❤️</div>
        <div id="compliment" class="compliment">Loading a compliment...</div>

        <label for="to_name">Recipient's Name:</label><br>
        <input type="text" id="to_name" placeholder="Enter recipient's name"><br><br>

        <label for="from_name">Your Name:</label><br>
        <input type="text" id="from_name" placeholder="Enter your name"><br><br>

        <label for="message">Write a sweet Valentine's message to your loved one:</label><br>
        <textarea id="message" rows="4" placeholder="Type something nice..."></textarea><br><br>
        <button onclick="sendMessage()">Send Your Message</button>
        
        <div id="outputMessage" class="footer"></div>
    </div>

    <!-- EmailJS Script -->
    <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script>
        // Compliment Generator
        const compliments = [
            "You are amazing!",
            "Your smile lights up the room!",
            "You're the reason someone smiles today.",
            "You are loved more than you know!",
            "Your kindness is contagious."
        ];

        const randomCompliment = compliments[Math.floor(Math.random() * compliments.length)];
        document.getElementById("compliment").innerText = randomCompliment;

        // Initialize EmailJS
        emailjs.init("rtkZeRh69f6xJMkaM"); // Your public key

        // Sending the User's Message
        function sendMessage() {
            const toName = document.getElementById("to_name").value;
            const fromName = document.getElementById("from_name").value;
            const userMessage = document.getElementById("message").value;

            if (toName && fromName && userMessage) {
                // Send email via EmailJS
                emailjs.send("service_7ps40yr", "template_go0gdu8", {
                    to_name: toName,
                    from_name: fromName,
                    message: userMessage
                }).then(function(response) {
                    console.log("Success!", response);
                    document.getElementById("outputMessage").innerText = "Your message has been sent! 💌";
                }, function(error) {
                    console.log("Failed...", error);
                    document.getElementById("outputMessage").innerText = "There was an error. Please try again!";
                });
            } else {
                document.getElementById("outputMessage").innerText = "Please fill in all the fields!";
            }
        }
    </script>

</body>
</html>
