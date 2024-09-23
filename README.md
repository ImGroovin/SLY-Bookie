# SLY-Bookie
SLY Bookie is a system to help teams keep track of contributions towards a crafting project. A Crafter selects the desired end product, contributors contribute to the project, and revenue is calculated and distributed based on contributions.

## How It Works
**Step 1:** The Crafter selects the desired end product and enters the desired amount.
* *Collect data*:
  * On-chain SAGE data is queried to determine the necessary ingredients to complete the project.
  * Star Atlas Marketplace data is queried to determine the current “sell now” price for each ingredient. This is used as the cost bases of contributions.
* *Create orders*:
  * For each ingredient, a 0.00000001 ATLAS buy order is opened on the Star Atlas Marketplace. This is used as an on-chain mechanism to track contributions towards a project.
* *Create the project*:
  * The project data (desired output, ingredient data, ingredient buy orders) is locally stored in persistent Tampermonkey storage.

**Step 2:** Any number of Contributors searches for the buy order to which they want to contribute. The desired amount is entered and the buy order is filled.

**Step 3:** The Crafter bears the responsibility to use the contributed ingredients to craft the desired output.

**Step 4:** When crafting is complete, the Crafter selects the project, enters the per-unit price, and clicks “Sell”. This sell price is added to the stored project data.

**Step 5:** When the sale is complete, the Crafter selects the project and clicks “Distribute”.
* On-chain transactions for each buy order correlated to the project are queried to determine all contributions.
* Contributions are calculated based on the items contributed and the initial cost basis of each ingredient.
* Revenue is distributed to each contributor in proportion to their contributions.

## Future Work
Buy orders related to a project are tracked within persistent local storage. A more robust storage solution would be ideal – preferably one which can be freely queried by potential contributors.

The actual crafting action is not handled by SLY Bookie. Future iterations can leverage SLY Assistant logic to automate this process.

Contributors bear all of the risk and must trust the Crafter to follow through with distribution. An escrow service would alleviate a great deal of that risk.
