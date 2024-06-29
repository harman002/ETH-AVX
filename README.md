# Project Title
Functions and Errors:ETH+AVX

Smart Contract Project

# Description

Project of Creating a smartContract in Functions and Errors:ETH+AVAX Course.This Project implements the require(), assert() and revert() statements.

# Functionality

Firstly I created a contract named smartContract and declare public variables named owner value inside it of type address and unit respectively.Then I use modifier named onlyOwner. A modifier is a special type of function that contains certain user-defined conditions.modifier always ends with  '_;' before the closing parenthesis all the conditions inside the modifier are checked, and if all the conditions are satisfied or are equal to true, only then does the function execution move forward.
The contract is designed to store a value and allow only the owner to set, decrement, and reset the value.Then I create Function name setValue  with parameter value and inside of it i create require() statement  which is used for input validation and access control.
Then i created function named decrementValuewiith parameter named amount and inside of it i created assert() statement  which is used to check for conditions that should never be false.
At last I created a function named resetValue and inside of this functioni declare revert() statement which is used to handle complex conditional reverts, ensuring that state changes can be undone if necessary conditions are not met.

# Code
 // SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract smartContract {
    address public owner;
    uint public value;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the contract owner");
        _;
    }

    function setValue(uint _value) public onlyOwner {
        require(_value > 0, "Value is greater than zero");
        value = _value;
    }

    function decrementValue(uint _amount) public onlyOwner {
        require(_amount > 0, "Amount is greater than zero");
        assert(value >= _amount);
        value -= _amount;
    }

    function resetValue() public onlyOwner {
        value = 0;
        if (value != 0) {
            revert("Value reset failed");
        }
    }
}
# Author

Harmandeep Singh

mail:harmandeep7448@icloud.com
