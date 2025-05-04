<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PUBG Tournament</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 text-gray-800">
  <header class="bg-blue-600 text-white p-4 text-center text-2xl font-bold">
    PUBG PC Tournament
  </header>

  <main class="p-6 space-y-4">
    <p class="text-lg">Welcome to the official PUBG tournament hub. Navigate below:</p>
    <ul class="space-y-2">
      <li><a href="points.html" class="text-blue-600 underline">View Points Table</a></li>
      <li><a href="matches.html" class="text-blue-600 underline">View & Download Match IDs</a></li>
      <li><a href="register.html" class="text-blue-600 underline">Register Your Team</a></li>
    </ul>
  </main>
</body>
</html>

<!-- points.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Points Table</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-50">
  <div class="p-6">
    <h1 class="text-2xl font-bold mb-4">Points Table</h1>
    <table class="min-w-full border border-gray-300">
      <thead class="bg-gray-200">
        <tr>
          <th class="border px-4 py-2">Team</th>
          <th class="border px-4 py-2">Kills</th>
          <th class="border px-4 py-2">Placement</th>
          <th class="border px-4 py-2">Total Points</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="border px-4 py-2">Team Alpha</td>
          <td class="border px-4 py-2">12</td>
          <td class="border px-4 py-2">2</td>
          <td class="border px-4 py-2">24</td>
        </tr>
        <tr>
          <td class="border px-4 py-2">Team Bravo</td>
          <td class="border px-4 py-2">8</td>
          <td class="border px-4 py-2">3</td>
          <td class="border px-4 py-2">18</td>
        </tr>
      </tbody>
    </table>
  </div>
</body>
</html>

<!-- matches.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Match IDs</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-white p-6">
  <h1 class="text-2xl font-bold mb-4">Match IDs</h1>
  <ul id="match-list" class="mb-4 list-disc list-inside">
    <li>Match 1 - ID: 12345678</li>
    <li>Match 2 - ID: 23456789</li>
    <li>Match 3 - ID: 34567890</li>
  </ul>
  <button onclick="downloadMatchIDs()" class="bg-blue-600 text-white px-4 py-2 rounded">Download Match IDs</button>

  <script>
    function downloadMatchIDs() {
      const data = [
        "Match 1 - ID: 12345678",
        "Match 2 - ID: 23456789",
        "Match 3 - ID: 34567890"
      ].join("\n");

      const blob = new Blob([data], { type: "text/plain" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "match_ids.txt";
      a.click();
      URL.revokeObjectURL(url);
    }
  </script>
</body>
</html>

<!-- register.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Register Team</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-6">
  <h1 class="text-2xl font-bold mb-4">Team Registration</h1>
  <form action="https://formspree.io/f/xqaqpoqb" method="POST" class="space-y-4 bg-white p-6 rounded shadow">
    <div>
      <label class="block font-medium">Team Name</label>
      <input type="text" name="teamName" class="w-full border p-2 rounded" required>
    </div>
    <div>
      <label class="block font-medium">Player 1 Name & PUBG ID</label>
      <input type="text" name="player1" class="w-full border p-2 rounded" required>
    </div>
    <div>
      <label class="block font-medium">Player 2 Name & PUBG ID</label>
      <input type="text" name="player2" class="w-full border p-2 rounded">
    </div>
    <div>
      <label class="block font-medium">Player 3 Name & PUBG ID</label>
      <input type="text" name="player3" class="w-full border p-2 rounded">
    </div>
    <div>
      <label class="block font-medium">Player 4 Name & PUBG ID</label>
      <input type="text" name="player4" class="w-full border p-2 rounded">
    </div>
    <button type="submit" class="bg-green-600 text-white px-4 py-2 rounded">Submit Registration</button>
  </form>
</body>
</html>
