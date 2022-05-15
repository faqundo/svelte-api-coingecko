<script>
  let titles = ["#", "Coin", "Price", "Price Change", "24h Volume"];
  let coins = [];

  const loadCoins = async () => {
    const res = await fetch(
      "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false"
    );
    const data = await res.json();
    console.log(data);
    coins = data;
  };
  loadCoins();
</script>

<main>
  <div class="container">
    <div class="row">
      <h1>Hello World</h1>
      <table class="table table-dark ">
        <thead>
          <tr>
            {#each titles as title}
              <th>{title}</th>
            {/each}
          </tr>
        </thead>
        <tbody>
          {#each coins as coin, index}
            <tr>
              <td>{index + 1}</td>
              <td>
				  <img class="img-fluid me-2" src={coin.image} alt={coin.name} style="width: 2rem ">
                <span>
					{coin.name}
				</span>
				<span>
					{coin.symbol}
				</span>
              </td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </div>
</main>

<style>
</style>
