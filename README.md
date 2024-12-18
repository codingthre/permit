<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parking Permit</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
            background-color: #f4f4f4;
            position: relative;
        }

        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #218838;
        }

        /* Admin Button */
        .admin-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            padding: 10px 15px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        .admin-btn:hover {
            background-color: #0056b3;
        }

        /* Popup Style */
        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: #28a745;
            color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            text-align: center;
        }

        .popup button {
            background-color: #c82333;
            border: none;
            color: white;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
        }

        .popup button:hover {
            background-color: #bd2130;
        }

        /* Overlay */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: none;
            z-index: 999;
        }

        /* Admin PIN Modal */
        .admin-modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: #ffffff;
            color: black;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            width: 300px;
            text-align: center;
        }

        .admin-modal input[type="text"] {
            padding: 10px;
            width: 80%;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .admin-modal button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        .admin-modal button:hover {
            background-color: #0056b3;
        }

        .admin-modal .cancel-btn {
            background-color: #c82333;
            margin-top: 10px;
        }

        .admin-modal .cancel-btn:hover {
            background-color: #bd2130;
        }
    </style>
</head>
<body>

    <!-- Admin Button -->
    <button class="admin-btn" onclick="openAdminModal()">Admin</button>

    <div class="container">
        <h2>Parking Permit</h2>
        <label for="regPlate">Enter your Registration Plate Number:</label>
        <input type="text" id="regPlate" placeholder="Enter registration number">
        <button onclick="submitPermit()">Submit</button>
    </div>

    <!-- Popup and Overlay -->
    <div class="overlay" id="overlay"></div>
    <div class="popup" id="popup">
        <p>Permit Approved!</p>
        <button onclick="closePopup()">Close</button>
    </div>

    <!-- Admin PIN Modal -->
    <div class="admin-modal" id="adminModal">
        <h3>Enter Admin PIN</h3>
        <input type="text" id="adminPin" placeholder="Enter PIN">
        <button onclick="checkAdminPin()">Submit</button>
        <button class="cancel-btn" onclick="closeAdminModal()">Cancel</button>
    </div>

    <!-- Access Denied Popup -->
    <div class="popup" id="accessDeniedPopup" style="background-color: #dc3545;">
        <p>Access Denied!</p>
        <button onclick="closeAccessDeniedPopup()">Close</button>
    </div>

    <script>
        // Function to submit the permit and show popup for 2 seconds before redirecting
        function submitPermit() {
            var regPlate = document.getElementById('regPlate').value;
            if (regPlate) {
                // Show the confirmation popup
                document.getElementById('popup').style.display = 'block';
                document.getElementById('overlay').style.display = 'block';

                // Wait for 2 seconds before redirecting
                setTimeout(function() {
                    window.location.href = "https://www.youtube.com"; // Redirect to YouTube
                }, 2000);
            } else {
                alert('Please enter a valid registration plate number.');
            }
        }

        // Function to close the permit approval popup
        function closePopup() {
            document.getElementById('popup').style.display = 'none';
            document.getElementById('overlay').style.display = 'none';
        }

        // Function to open the admin modal
        function openAdminModal() {
            document.getElementById('adminModal').style.display = 'block';
            document.getElementById('overlay').style.display = 'block';
        }

        // Function to check the admin PIN
        function checkAdminPin() {
            var pin = document.getElementById('adminPin').value;
            if (pin === '8737') {
                alert('Access granted!');
                closeAdminModal();
                // Here you could add functionality to open the admin panel
            } else {
                // Show access denied popup
                document.getElementById('accessDeniedPopup').style.display = 'block';
                document.getElementById('overlay').style.display = 'block';

                // Wait for 2 seconds before redirecting
                setTimeout(function() {
                    window.location.href = "https://youtu.be/dQw4w9WgXcQ?si=J_D_djJNRSEE9VQm"; // Redirect to the RickRoll
                }, 2000);
            }
        }

        // Function to close the admin modal
        function closeAdminModal() {
            document.getElementById('adminModal').style.display = 'none';
            document.getElementById('overlay').style.display = 'none';
        }

        // Function to close the access denied popup
        function closeAccessDeniedPopup() {
            document.getElementById('accessDeniedPopup').style.display = 'none';
            document.getElementById('overlay').style.display = 'none';
        }
    </script>

</body>
</html>
