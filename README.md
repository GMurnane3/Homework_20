# Homework #20

Homework 20 requires Ganache and MetaMask pointed to localhost:8545
Custom (5777) Network

testnet addresses:
1. 0xE49E3220EdD764a3187D6698CBCeE8AFEBfD63Ac

2. 0x55D8A1Dbc5b3a4Ad9eAAD0d49466491d6D234cf2

3. 0x14CCA802c2a73062Ea4F53cf6076137fC2914B08


Contracts functions:
1. AssociateProfitSplitter: Takes ether into contract then divides it evenly to pay employees at associate level quickly.
 
### Smart contract code for AssociateProfitSplitter.sol.
![1 AssociateProfitSplitter Code](https://user-images.githubusercontent.com/70610967/109328253-1a3cce80-780e-11eb-93d6-41a97a86cb9f.PNG)

### The amount in addresses that represent `employee_one`, `employee_two`, and `employee_three` before deployment of transaction.
![2 Ganache](https://user-images.githubusercontent.com/70610967/109328317-304a8f00-780e-11eb-9536-020cd512c193.PNG)

### The smart contract AssociateProfitSplitter.sol is compiled. 
![3 AssociateProfitSplitter Compiled](https://user-images.githubusercontent.com/70610967/109328871-c979a580-780e-11eb-8d4f-dcda329538f1.PNG)

![4 AssociateProfitSplitter Compiled](https://user-images.githubusercontent.com/70610967/109328887-ced6f000-780e-11eb-8d10-88c4b5303c0b.PNG)

### The smart contract is deployed.
![6 AssociateProfitSplitter Deployed](https://user-images.githubusercontent.com/70610967/109329199-25dcc500-780f-11eb-84f2-62a6d95c8387.PNG)

### The Transaction is reflected in MetaMask.
![7 MetaMask](https://user-images.githubusercontent.com/70610967/109329367-53c20980-780f-11eb-803a-576de32617cd.PNG)

### The transaction amounts are reflected in the ledger.
![8 MetaMask](https://user-images.githubusercontent.com/70610967/109329446-6ccaba80-780f-11eb-8bf9-8f554978be39.PNG))

2. TieredProfitSplitter: Distributes percentages of ethere taken into contract among different level tiered employees.

### The amount of ETH in addresses that represent `employee_one`, `employee_two`, and `employee_three` before deployment of transaction.
![9 Ganache](https://user-images.githubusercontent.com/70610967/109329502-7f44f400-780f-11eb-8977-4743e91f42f1.PNG)

### TieredProfitSplitter.sol compiled.
![10 TieredProfitSplitter Compiled](https://user-images.githubusercontent.com/70610967/109329572-98e63b80-780f-11eb-8ecb-42a16920a373.PNG)

### TieredProfitSplitter.sol deployed.
![11 TieredProfitSplitter Deployed](https://user-images.githubusercontent.com/70610967/109329631-aef3fc00-780f-11eb-9134-d2fa7ea0a07c.PNG)

### Deposit reflected in MetaMask.
![12 TieredProfitSplitter Depositied](https://user-images.githubusercontent.com/70610967/109329710-c3d08f80-780f-11eb-8b9b-a706ec3dec01.PNG)

### The smart contract has confirmed the deposit to the employee accounts and is reflected in addresses of `employee_one`, `employee_two`,  and `employee_three` (reflects 2 deposits of 10 ETH each).
![13 Ganache](https://user-images.githubusercontent.com/70610967/109329946-04c8a400-7810-11eb-991e-4dd2c0f8f0a6.PNG)

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
