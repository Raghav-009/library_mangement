# username- admin , password- password
# library_mangement
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Management System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        header {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 1em 0;
        }
        nav {
            background-color: #555;
            color: white;
            display: flex;
            justify-content: space-around;
            padding: 0.5em;
            display: none; /* Initially hidden */
        }
        nav a {
            color: white;
            text-decoration: none;
        }
        .container {
            padding: 20px;
            margin: auto;
            max-width: 800px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        form {
            display: flex;
            flex-direction: column;
        }
        form label, form input, form select, form button {
            margin: 10px 0;
        }
        input[type="text"], input[type="date"], input[type="password"], select {
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 10px;
            background-color: #333;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #555;
        }
        .error {
            color: red;
            font-size: 0.9em;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 10px;
            text-align: left;
        }
        th {
            background-color: #333;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <h1>Library Management System</h1>
    </header>
    <nav id="mainNav">
        <a href="#book-issue">Book Issue</a>
        <a href="#return-book">Return Book</a>
        <a href="#fine-pay">Fine Pay</a>
        <a href="#membership">Membership</a>
        <a href="#maintenance">Maintenance</a>
        <a href="#book-details">Book Details</a>
    </nav>

    <!-- Login Page -->
    <div class="container" id="login">
        <h2>Login</h2>
        <form id="loginForm">
            <label for="username">Username:</label>
            <input type="text" id="username" required>

            <label for="password">Password:</label>
            <input type="password" id="password" required>

            <button type="submit">Login</button>
            <p class="error" id="loginError"></p>
        </form>
    </div>

    <!-- Book Details -->
    <div class="container" id="book-details" style="display:none;">
        <h2>Book Details</h2>
        <table>
            <tr>
                <th>Book ID</th>
                <th>Book Name</th>
                <th>Author</th>
                <th>Availability</th>
            </tr>
            <tr>
                <td>101</td>
                <td>Library Science</td>
                <td>John Doe</td>
                <td>Available</td>
            </tr>
            <tr>
                <td>102</td>
                <td>Web Development Basics</td>
                <td>Jane Smith</td>
                <td>Issued</td>
            </tr>
        </table>
    </div>

    <!-- Existing Features -->
    <div class="container" id="book-issue" style="display:none;">
        <h2>Book Issue</h2>
        <form id="bookIssueForm">
            <label for="bookName">Name of Book:</label>
            <input type="text" id="bookName" required>

            <label for="authorName">Author Name:</label>
            <input type="text" id="authorName" readonly>

            <label for="issueDate">Issue Date:</label>
            <input type="date" id="issueDate" min="">

            <label for="returnDate">Return Date (Max 15 days):</label>
            <input type="date" id="returnDate">

            <label for="remarks">Remarks:</label>
            <input type="text" id="remarks">

            <button type="submit">Submit</button>
            <p class="error" id="bookIssueError"></p>
        </form>
    </div>

    <script>
        const mainNav = document.getElementById('mainNav');
        document.getElementById('loginForm').addEventListener('submit', function (e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username === "admin" && password === "password") {
                alert("Login Successful!");
                document.getElementById('login').style.display = 'none';
                mainNav.style.display = 'flex';
                document.getElementById('book-details').style.display = 'block';
            } else {
                document.getElementById('loginError').innerText = "Invalid credentials.";
            }
        });

        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                document.querySelectorAll('.container').forEach(section => {
                    section.style.display = 'none';
                });
                document.getElementById(targetId).style.display = 'block';
            });
        });
    </script>
</body>
</html>
