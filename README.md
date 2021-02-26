# Homework #20

Homework 20 requires Ganache and MetaMask pointed to localhost:8545
Custom (5777) Network

testnet addresses:
1. 0x882FB0E63Ce059787243482eF9107564715Fd7F6

2. 0xE49E3220EdD764a3187D6698CBCeE8AFEBfD63Ac

3. 0x55D8A1Dbc5b3a4Ad9eAAD0d49466491d6D234cf2


Contracts functions:
1. AssociateProfitSplitter: Takes ether into contract then divides it evenly to pay employees at associate level quickly.
 
### Smart contract code for AssociateProfitSplitter.sol.
![AssociateProfitSplitter sol](https://user-images.githubusercontent.com/70610967/109243692-3b5fd980-7792-11eb-8200-366dee37fc99.png)

### The amount in addresses that represent `employee_one`, `employee_two`, and `employee_three` before deployment of transaction.
![preTrans](https://user-images.githubusercontent.com/70610967/109243750-56cae480-7792-11eb-8652-f3d9c356619e.png)

### The smart contract AssociateProfitSplitter.sol is compiled. 
![AssociateProfitSplitter sol_compiled](https://user-images.githubusercontent.com/70610967/109243900-9c87ad00-7792-11eb-94cc-17cdcccf1975.png)

![AssociateProfitSplitter sol_compiled(1)](https://user-images.githubusercontent.com/70610967/109243816-72ce8600-7792-11eb-9ba7-7a0dd64d7f68.png)

### The smart contract is deployed.
![deployedContract](https://user-images.githubusercontent.com/70610967/109243937-ac06f600-7792-11eb-8468-2233fae44e02.png)

![deposit](https://user-images.githubusercontent.com/70610967/109243973-bb863f00-7792-11eb-9f8b-1797cbf26eb0.png)

### The Transaction is reflected in MetaMask.
![transaction](https://user-images.githubusercontent.com/70610967/109244016-ce007880-7792-11eb-9a65-84854c485c47.png)
![Deposit Trasaction](Images/transaction(1).png)

### The transaction amounts are reflected in the ledger.
![transaction(1)](https://user-images.githubusercontent.com/70610967/109244051-db1d6780-7792-11eb-83f1-3e9ebcc1f652.png)

2. TieredProfitSplitter: Distributes percentages of ethere taken into contract among different level tiered employees.

### The amount of ETH in addresses that represent `employee_one`, `employee_two`, and `employee_three` before deployment of transaction.
![TieredProfitSplitter(1)](https://user-images.githubusercontent.com/70610967/109244573-c8576280-7793-11eb-9c31-7ac7da1ce8a0.png)![TieredProfitSplitter(1)](https://user-images.githubusercontent.com/70610967/109244573-c8576280-7793-11eb-9c31-7ac7da1ce8a0.png)

### TieredProfitSplitter.sol compiled.
![TieredProfitSplitter(2)](https://user-images.githubusercontent.com/70610967/109244608-d6a57e80-7793-11eb-9e32-25f1a85a0056.png)

### TieredProfitSplitter.sol deployed.
![TieredProfitSplitter(3)](https://user-images.githubusercontent.com/70610967/109244624-de652300-7793-11eb-8538-4e035fc7fb92.png)

![TieredProfitSplitter(4)](https://user-images.githubusercontent.com/70610967/109244636-e2914080-7793-11eb-8f64-ca0a653ad8f6.png)

### Deposit reflected in MetaMask.
![TieredProfitSplitter(5)](https://user-images.githubusercontent.com/70610967/109244644-e58c3100-7793-11eb-8aa6-43e22ff84eec.png)

### The smart contract has confirmed the deposit to the employee accounts.
![TieredProfitSplitter(6)](https://user-images.githubusercontent.com/70610967/109244650-e8872180-7793-11eb-876f-efbbb4065353.png)

### Deposit reflected in addresses of `employee_one`, `employee_two`,  and `employee_three`.
![TieredProfitSplitter(7)](https://user-images.githubusercontent.com/70610967/109244660-ec1aa880-7793-11eb-97c7-883988855e36.png)

3. DeferredEquityPlan: Models stock plans and manages annual distributions of shares for an employee of the company.

<details>
    <summary>Level Three: The `DeferredEquityPlan` Contract</summary>

In this contract, manage an employee's "deferred equity incentive plan" in which 1000 shares will be distributed over 4 years to the employee. No need to work with Ether in this contract, but there will storing and setting amounts that represent the number of distributed shares the employee owns and enforcing the vetting periods automatically.

* **A two-minute primer on deferred equity incentive plans:** In this set-up, employees receive shares for joining and staying with the firm. They may receive, for example, an award of 1,000 shares when joining, but with a 4 year vesting period for these shares. This means that these shares would stay with the company, with only 250 shares (1,000/4) actually distributed to and owned by the employee each year. If the employee leaves within the first 4 years, he or she would forfeit ownership of any remaining (“unvested”) shares.

  * If, for example, the employee only sticks around for the first two years before moving on, the employee’s account will end up with 500 shares (250 shares * 2 years), with the remaining 500 shares staying with the company. In this above example, only half of the shares (and any distributions of company profit associated with them) actually “vested”, or became fully owned by the employee. The remaining half, which were still “deferred” or “unvested”, ended up fully owned by the company since the employee left midway through the incentive/vesting period.

  * Specific vesting periods, the dollar/crypto value of shares awarded, and the percentage equity stake (the percentage ownership of the company) all tend to vary according to the company, the specialized skills, or seniority of the employee, and the negotiating positions of the employee/company. If you receive an offer from a company offering equity (which is great!), just make sure you can clarify the current dollar value of those shares being offered (based on, perhaps, valuation implied by the most recent outside funding round). In other words, don’t be content with just receiving “X” number of shares without having a credible sense of what amount of dollars that “X” number represents. Be sure to understand your vesting schedule as well, particularly if you think you may not stick around for an extended period of time.

Using the starter code, perform the following:

* Human Resources will be set in the constructor as the `msg.sender`, since HR will be deploying the contract.

* Below the `employee` initialization variables at the top (after `bool active = true;`), set the total shares and annual distribution:

  * Create a `uint` called `total_shares` and set this to `1000`.

  * Create another `uint` called `annual_distribution` and set this to `250`. This equates to a 4 year vesting period for the `total_shares`, as `250` will be distributed per year. Since it is expensive to calculate this in Solidity, we can simply set these values manually. You can tweak them as you see fit, as long as you can divide `total_shares` by `annual_distribution` evenly.

* The `uint start_time = now;` line permanently stores the contract's start date. We'll use this to calculate the vested shares later. Below this variable, set the `unlock_time` to equal `now` plus `365 days`. We will increment each distribution period.

* The `uint public distributed_shares` will track how many vested shares the employee has claimed and was distributed. By default, this is `0`.

* In the `distribute` function:

  * Add the following `require` statements:

    * Require that `unlock_time` is less than or equal to `now`.

    * Require that `distributed_shares` is less than the `total_shares` the employee was set for.

    * Ensure to provide error messages in your `require` statements.

  * After the `require` statements, add `365 days` to the `unlock_time`. This will calculate next year's unlock time before distributing this year's shares. We want to perform all of our calculations like this before distributing the shares.

  * Next, set the new value for `distributed_shares` by calculating how many years have passed since `start_time` multiplied by `annual_distributions`. For example:

    * The `distributed_shares` is equal to `(now - start_time)` divided by `365 days`, multiplied by the annual distribution. If `now - start_time` is less than `365 days`, the output will be `0` since the remainder will be discarded. If it is something like `400` days, the output will equal `1`, meaning `distributed_shares` would equal `250`.

    * Make sure to include the parenthesis around `now - start_time` in your calculation to ensure that the order of operations is followed properly.

  * The final `if` statement provided checks that in case the employee does not cash out until 5+ years after the contract start, the contract does not reward more than the `total_shares` agreed upon in the contract.

* Deploy and test your contract locally.

  * For this contract, test the timelock functionality by adding a new variable called `uint fakenow = now;` as the first line of the contract, then replace every other instance of `now` with `fakenow`. Utilize the following `fastforward` function to manipulate `fakenow` during testing.

  * Add this function to "fast forward" time by 100 days when the contract is deployed (requires setting up `fakenow`):

    ```solidity
    function fastforward() public {
        fakenow += 100 days;
    }
    ```

  * Once satisfied with the contract's logic, revert the `fakenow` testing logic.

![deferred_equity_plan](https://user-images.githubusercontent.com/70610967/109245223-f1c4be00-7794-11eb-8d06-0beba3041ae0.png)
    
</details>

<details>
    <summary>Transactions History</summary>

'Etherscan' Blockchain Transaction Ledger

![etherscan](https://user-images.githubusercontent.com/70610967/109245274-02753400-7795-11eb-85b7-544948b78a76.png)

</details>
