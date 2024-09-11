<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Stats</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            max-width: 600px;
            width: 100%;
            box-sizing: border-box;
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #333;
            text-align: center;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 0 auto;
        }

        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        th {
            background-color: #f4f4f4;
            color: #333;
        }

        tr:hover {
            background-color: #f1f1f1;
        }

        caption {
            font-weight: bold;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>GitHub Stats</h1>
        <table>
            <caption>GitHub User Information</caption>
            <tr>
                <th>Stat</th>
                <th>Value</th>
            </tr>
            <tr>
                <td>Username</td>
                <td id="username">[Your GitHub Username]</td>
            </tr>
            <tr>
                <td>Public Repositories</td>
                <td id="public-repos">[Number]</td>
            </tr>
            <tr>
                <td>Public Gists</td>
                <td id="public-gists">[Number]</td>
            </tr>
            <tr>
                <td>Followers</td>
                <td id="followers">[Number]</td>
            </tr>
            <tr>
                <td>Following</td>
                <td id="following">[Number]</td>
            </tr>
        </table>
    </div>

    <script>
        // Replace placeholders with actual data
        document.getElementById('username').textContent = 'Momwhyareyouhere'; // Replace with actual username
        document.getElementById('public-repos').textContent = '42'; // Replace with actual number
        document.getElementById('public-gists').textContent = '7'; // Replace with actual number
        document.getElementById('followers').textContent = '15'; // Replace with actual number
        document.getElementById('following').textContent = '10'; // Replace with actual number
    </script>
</body>
</html>
