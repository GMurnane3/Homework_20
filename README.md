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

Using the starter code, performed the following:

* Human Resources was set in the constructor as the `msg.sender`, since HR will be deploying the contract.

* Below the `employee` initialization variables at the top (after `bool active = true;`), set the total shares and annual distribution:

  * Created a `uint` called `total_shares` and set this to `1000`.

  * Created another `uint` called `annual_distribution` and set this to `250`. This equates to a 4 year vesting period for the `total_shares`, as `250` will be distributed per year totalling `1000`. Since it is expensive to calculate this in Solidity, we set these values manually.

* The `uint start_time = now;` line permanently stores the contract's start date and will be later used to calculate the vested shares. Below this variable, we set the `unlock_time` to equal `now` plus `365 days`. We will increment each distribution period.

![14 DeferredEquity Plan](https://user-images.githubusercontent.com/70610967/109331782-2165db80-7812-11eb-8bb4-454c1ca26662.PNG)

* The `uint public distributed_shares` will track how many vested shares the employee has claimed and was distributed. By default, this is `0`.

* In the `distribute` function:

  * The following `require` statements were added:

    * Require that `unlock_time` is less than or equal to `now`.

    * Require that `distributed_shares` is less than the `total_shares` the employee was set for.

    * Ensure to provide error messages in your `require` statements.

  * After the `require` statements, added `365 days` to the `unlock_time`. This will calculate next year's unlock time before distributing this year's shares. We want to perform all of our calculations like this before distributing the shares.

  * Next, set the new value for `distributed_shares` by calculating how many years have passed since `start_time` multiplied by `annual_distributions`.

  * The final `if` statement provided checks that in case the employee does not cash out until 5+ years after the contract start, the contract does not reward more than the `total_shares` agreed upon in the contract.

![15 DeferredEquity Plan](https://user-images.githubusercontent.com/70610967/109332367-da2c1a80-7812-11eb-951b-c2e8aa2ea7d0.PNG)

* Deployed and tested my contract locally.

![16 DeferredEquity Plan](https://user-images.githubusercontent.com/70610967/109332681-4ad33700-7813-11eb-934b-2bc726c5ac75.PNG)

