MyToken Contract
This README document provides an explanation of the code for the MyToken contract. The contract is implemented in Solidity, a programming language used for writing smart contracts on the Ethereum blockchain.
Requirements
The MyToken contract is designed to fulfill the following requirements:
1.	The contract should have public variables to store the details about the coin, including the token name, token abbreviation, and total supply.
2.	The contract should include a mapping that associates addresses with token balances.
3.	The contract should have a mint function that increases the total supply of tokens and adds the specified amount to the balance of the "sender" address.
4.	The contract should have a burn function that decreases the total supply of tokens and deducts the specified amount from the balance of the "sender" address.
5.	The burn function should include conditionals to ensure that the balance of the "sender" is greater than or equal to the amount to be burned.

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;
contract MyToken {

    // public variables here
    string public tokenName = "Carmina";
    string public tokenAbbrv = "Mina";
    uint public totalSupply = 0;

    // mapping variable here
    mapping (address => uint) public balances;
    // mint function
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances [_address] += _value;    
    }
    // burn function
    function burn (address _address, uint _value) public {
        if (balances[_address] >= _value){
        totalSupply -= _value;
        balances [_address] -= _value;  
        }   
    }
}

Usage
The contract provides the following public variables:
•	tokenName: A string representing the name of the token ("Carmina").
•	tokenAbbrv: A string representing the abbreviation of the token ("Mina").
•	totalSupply: An unsigned integer representing the total supply of tokens.
The contract also includes the following mapping variable:
•	balances: A mapping that associates Ethereum addresses with their corresponding token balances. Each address is mapped to an unsigned integer representing the balance.
The contract provides two functions to interact with the token:
Mint Function
The mint function allows new tokens to be created and added to the balance of a specified address. It takes two parameters:
•	_address: The Ethereum address to which the new tokens will be minted.
•	_value: The amount of tokens to be minted and added to the balance.
When the mint function is called, it increases the totalSupply by the specified _value and adds the same amount to the balance of the _address.
Burn Function
The burn function allows tokens to be destroyed and deducted from the balance of a specified address. It takes two parameters:
•	_address: The Ethereum address from which the tokens will be burned.
•	_value: The amount of tokens to be burned and deducted from the balance.
Before deducting the tokens, the burn function checks if the balance of the _address is greater than or equal to the _value. If the condition is met, the function decreases the totalSupply by the specified _value and deducts the same amount from the balance of the _address.
It's important to note that the mint and burn functions are public, meaning they can be called by anyone with access to the contract.
License
The code in this contract is licensed under the MIT license. The SPDX-License-Identifier at the top of the code file indicates that the code is licensed under the MIT license.
