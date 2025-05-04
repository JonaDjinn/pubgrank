<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PUBG Match Summary & Leaderboard</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gradient-to-r from-blue-500 to-purple-600 text-white">

  <header class="text-center py-6">
    <h1 class="text-4xl font-bold">PUBG Tournament</h1>
    <p class="text-lg mt-2">Match Summary and Points Leaderboard</p>
  </header>

  <div class="max-w-4xl mx-auto p-6 bg-white rounded-lg shadow-lg mt-10">
    
    <!-- Match ID Section -->
    <div class="mb-6">
      <label class="block font-semibold text-gray-700 mb-2">Enter Match ID:</label>
      <input id="matchId" type="text" placeholder="Paste Match ID here"
             class="w-full p-3 border-2 border-gray-300 rounded-lg bg-gray-50 focus:outline-none focus:ring-2 focus:ring-blue-600">
      <button onclick="displayMatchId()" class="mt-3 px-6 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 focus:outline-none">
        Show Match ID
      </button>
      <p id="matchIdDisplay" class="mt-3 text-gray-600"></p>
    </div>

    <!-- Points Table -->
    <div class="mb-8">
      <h2 class="text-2xl font-semibold mb-4 text-center">Points Table</h2>
      <table class="min-w-full border-collapse table-auto">
        <thead class="bg-blue-100">
          <tr>
            <th class="border px-4 py-2">#</th>
            <th class="border px-4 py-2">Team Name</th>
            <th class="border px-4 py-2">Kills</th>
            <th class="border px-4 py-2">Placement Points</th>
            <th class="border px-4 py-2">Total Points</th>
          </tr>
        </thead>
        <tbody id="pointsBody">
          <tr class="bg-gray-50">
            <td class="border px-4 py-2">1</td>
            <td class="border px-4 py-2"><input type="text" placeholder="Team Name" class="w-full p-2 border-2 rounded-lg"></td>
            <td class="border px-4 py-2"><input type="number" placeholder="Kills" class="w-full p-2 border-2 rounded-lg"></td>
            <td class="border px-4 py-2"><input type="number" placeholder="Placement" class="w-full p-2 border-2 rounded-lg"></td>
            <td class="border px-4 py-2" id="totalPoints">0</td>
          </tr>
        </tbody>
      </table>
      <button onclick="calculatePoints()" class="mt-4 px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 focus:outline-none">Calculate Total Points</button>
    </div>

    <!-- Kill Leaders -->
    <div>
      <h2 class="text-2xl font-semibold mb-4 text-center">Kill Leaders</h2>
      <ul id="killLeaders" class="bg-white border rounded p-6 space-y-2">
        <li>1. PlayerX - 7 kills</li>
        <li>2. PlayerY - 5 kills</li>
        <li>3. PlayerZ - 5 kills</li>
        <li>4. PlayerW - 4 kills</li>
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
