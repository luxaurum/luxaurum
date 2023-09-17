<!DOCTYPE html>
<html>
<head>
    <title>Lux Aurum</title>
    <link rel="stylesheet" type="text/css" href="style.css">
    <style>
        /* Additional CSS styles */
        /* Body */
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            color: #333;
            margin: 0;
            padding: 0;
        }

        /* Header */
        h1 {
            text-align: center;
            background-color: #007BFF;
            color: #fff;
            padding: 10px 0;
            margin: 0;
        }

        /* Dropdown */
        .dropdown {
            position: relative;
            display: inline-block;
        }

        .dropbtn {
            background-color: #007BFF;
            color: #fff;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }

        .dropbtn:hover {
            background-color: #0056b3;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #fff;
            min-width: 160px;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            z-index: 1;
        }

        .dropdown-content a {
            color: #333;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }

        .dropdown-content a:hover {
            background-color: #f2f2f2;
        }

        .show {
            display: block;
        }

        /* Information Display */
        #info {
            display: none;
        }

        /* Button */
        button {
            background-color: #007BFF;
            color: #fff;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Lux Aurum</h1>
    
    <h2>Dropdown Example</h2>
    <div class="dropdown">
        <button onclick="toggleDropdown()" class="dropbtn">Click me</button>
        <div id="myDropdown" class="dropdown-content">
            <a href="page1">Sample Blockchain</a>
            <a href="#">Option 2</a>
            <a href="#">Option 3</a>
        </div>
    </div>
    
    <h2>Information Display</h2>
    <button onclick="toggleInfo()">Show/Hide Information</button>
    <div id="info" style="display: none;">
        <p>This is some hidden information that can be displayed or hidden using JavaScript.</p>
    </div>
    
    <script>
        // JavaScript code for dropdown functionality
        function toggleDropdown() {
            document.getElementById("myDropdown").classList.toggle("show");
        }
        
        // JavaScript code for showing/hiding information
        function toggleInfo() {
            var infoDiv = document.getElementById("info");
            if (infoDiv.style.display === "none") {
                infoDiv.style.display = "block";
            } else {
                infoDiv.style.display = "none";
            }
        }
    </script>
</body>
</html>
