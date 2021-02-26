# Homework #20

Homework 20 requires Ganache and MetaMask pointed to localhost:8545
Custom (5777) Network

testnet addresses:
1. 0x882FB0E63Ce059787243482eF9107564715Fd7F6

2. 0xE49E3220EdD764a3187D6698CBCeE8AFEBfD63Ac

3. 0x55D8A1Dbc5b3a4Ad9eAAD0d49466491d6D234cf2


Contracts functions:
1. AssociateProfitSplitter: Takes ether into contract then divides it evenly to pay employees at associate level quickly.
2. 
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

3. TieredProfitSplitter: Distributes percentages of ethere taken into contract among different level tiered employees.
4. DeferredEquityPlan: Models stock plans and manages annual distributions of shares for an employee of the company.
