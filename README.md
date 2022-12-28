<html>
<body>

<h1>Fortnite Stats</h1>

<label for="accountIdInput">Enter account ID:</label><br>
<input type="text" id="accountIdInput"><br>
<button type="button" onclick="getStats()">Get Stats</button>

<div id="stats"></div>

<script>
  function getStats() {
    const accountId = document.getElementById('accountIdInput').value;
    const apiUrl = `https://fortnite-api.com/v2/stats/br/v2/${accountId}`;

    fetch(apiUrl)
      .then(response => response.json())
      .then(data => {
        const stats = data.stats;
        let statsHtml = '';
        for (const stat of stats) {
          if (stat.name === 'Kills' || stat.name === 'Wins') {
            statsHtml += `<p>${stat.name}: ${stat.displayValue}</p>`;
          }
        }
        document.getElementById('stats').innerHTML = statsHtml;
      });
  }
</script>

</body>
</html>
