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

4. DeferredEquityPlan: Models stock plans and manages annual distributions of shares for an employee of the company.
