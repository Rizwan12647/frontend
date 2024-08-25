# Function Frontend

This Solidity program is a simple "Function Frontend" program that demonstrates the  simple contract with 2-3 functions. Then show the values of those functions in frontend of the application.
## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a single function that returns the string "Hello World!". This program serves as a simple and straightforward introduction to Solidity programming, and can be used as a stepping stone for more complex projects in the future.
 It is a  simple contract with 2-3 functions. Then show the values of those functions in frontend of the application.
 



### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```// For this project, create a simple contract with 2-3 functions. Then show the values of those functions in frontend of the application. 

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.16;

contract Frontend {
    address payable public owner;
    uint256 public balance;
    uint256 public Order;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);
    


    constructor(uint initBalance) payable {
        owner = payable(msg.sender);
        balance = initBalance;
        Order = 0;
    }

    function getBalance() public view returns(uint256){
        return balance;
    }

    function deposit(uint256 _amount) public payable {

   // Using require() to check for a valid deposit amount
        require(msg.value > 0, "Deposit amount must be greater than zero");
        

        uint _prevBalance = balance;

        require(msg.sender == owner, "only owner can access");
        balance += _amount;

        assert(balance == _prevBalance + _amount);

        emit Deposit(_amount);
    }

    // custom error message to track state of contract.
    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == owner, "You are not the owner of this account");
        uint _prevBalance = balance;
        if (balance < _withdrawAmount) {
            revert InsufficientBalance({
                balance: balance,
                withdrawAmount: _withdrawAmount
            });
        }

        balance -= _withdrawAmount;

        // assert the balance is correct
        assert(balance == (_prevBalance - _withdrawAmount));

        // emit the event
        emit Withdraw(_withdrawAmount);
    }
    

    function increment() public {
        Order++;
    }

    function decrement() public {
        Order--;
    }
    
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "CFunctionfrontend.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. nd then click on the "Deploy" button.
Once the contract is deployed, you can interact with it 
## Authors

Rizwan khan


## License

This project is licensed under the MIT License .
