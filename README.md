<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PUBG Tournament Leaderboard</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white font-sans">

  <!-- Header Section -->
  <header class="text-center py-8">
    <h1 class="text-5xl font-bold text-yellow-400">PUBG Tournament</h1>
    <p class="text-lg text-gray-400 mt-2">Real-Time Match Summary & Leaderboard</p>
  </header>

  <!-- Main Content -->
  <div class="max-w-6xl mx-auto px-6 pb-12">

    <!-- Match ID Section -->
    <div class="bg-gray-800 rounded-lg p-6 mb-10 shadow-xl">
      <h2 class="text-2xl font-semibold text-yellow-300 mb-4">Enter Match ID</h2>
      <input id="matchId" type="text" placeholder="Paste Match ID here"
             class="w-full p-3 border-2 border-gray-700 bg-gray-600 text-white rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-400">
      <button onclick="displayMatchId()" class="mt-4 px-6 py-2 bg-yellow-500 text-gray-900 rounded-lg hover:bg-yellow-600 focus:outline-none">
        Show Match ID
      </button>
      <p id="matchIdDisplay" class="mt-3 text-gray-400">Match ID will appear here after pasting.</p>
    </div>

    <!-- Points Table Section -->
    <div class="bg-gray-800 rounded-lg p-6 mb-10 shadow-xl">
      <h2 class="text-2xl font-semibold text-yellow-300 mb-4 text-center">Points Table</h2>
      <table class="min-w-full table-auto border-collapse text-center">
        <thead class="bg-gray-700">
          <tr>
            <th class="border px-4 py-2 text-yellow-300">#</th>
            <th class="border px-4 py-2 text-yellow-300">Team Name</th>
            <th class="border px-4 py-2 text-yellow-300">Kills</th>
            <th class="border px-4 py-2 text-yellow-300">Placement Points</th>
            <th class="border px-4 py-2 text-yellow-300">Total Points</th>
          </tr>
        </thead>
        <tbody id="pointsBody">
          <tr class="bg-gray-700 hover:bg-gray-600">
            <td class="border px-4 py-2">1</td>
            <td class="border px-4 py-2"><input type="text" placeholder="Team Name" class="w-full p-2 bg-gray-600 text-white border-2 border-gray-700 rounded-lg"></td>
            <td class="border px-4 py-2"><input type="number" placeholder="Kills" class="w-full p-2 bg-gray-600 text-white border-2 border-gray-700 rounded-lg"></td>
            <td class="border px-4 py-2"><input type="number" placeholder="Placement" class="w-full p-2 bg-gray-600 text-white border-2 border-gray-700 rounded-lg"></td>
            <td class="border px-4 py-2" id="totalPoints">0</td>
          </tr>
        </tbody>
      </table>
      <button onclick="calculatePoints()" class="mt-6 px-6 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 focus:outline-none">
        Calculate Total Points
      </button>
    </div>

    <!-- Kill Leaders Section -->
    <div class="bg-gray-800 rounded-lg p-6 shadow-xl">
      <h2 class="text-2xl font-semibold text-yellow-300 mb-4 text-center">Kill Leaders</h2>
      <ul id="killLeaders" class="space-y-2">
        <li class="bg-gray-700 px-4 py-2 rounded-lg">1. PlayerX - 7 kills</li>
        <li class="bg-gray-700 px-4 py-2 rounded-lg">2. PlayerY - 5 kills</li>
        <li class="bg-gray-700 px-4 py-2 rounded-lg">3. PlayerZ - 5 kills</li>
        <li class="bg-gray-700 px-4 py-2 rounded-lg">4. PlayerW - 4 kills</li>
      </ul>
    </div>

  </div>

  <script>
    // Function to display Match ID after pasting
    function displayMatchId() {
      const matchId = document.getElementById('matchId').value;
      document.getElementById('matchIdDisplay').textContent = `Match ID: ${matchId}`;
    }

    // Function to calculate total points
    function calculatePoints() {
      const rows = document.querySelectorAll('#pointsBody tr');
      rows.forEach(row => {
        const kills = row.querySelector('td:nth-child(3) input').value;
        const placement = row.querySelector('td:nth-child(4) input').value;
        const totalPointsCell = row.querySelector('td:nth-child(5)');
        
        // Simple calculation (e.g., kills + placement points)
        if (kills && placement) {
          const totalPoints = parseInt(kills) + parseInt(placement);
          totalPointsCell.textContent = totalPoints;
        }
      });
    }
  </script>

</body>
</html>
