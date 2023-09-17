<!DOCTYPE html>
<html>
<head>
    <title>Lux Aurum</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
    <h1>Lux Aurum</h1>
    
    <h2>Dropdown Example</h2>
    <div class="dropdown">
        <button onclick="toggleDropdown()" class="dropbtn">Click me</button>
        <div id="myDropdown" class="dropdown-content">
            <a href="#">Option 1</a>
            <a href="#">Option 2</a>
            <a href="#">Option 3</a>
        </div>
    </div>
    
    <h2>Information Display</h2>
    <button onclick="toggleInfo()">Show/Hide Information</button>
    <div id="info" style="display: none;">
        <p>This is some hidden information that can be displayed or hidden using JavaScript.</p>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
