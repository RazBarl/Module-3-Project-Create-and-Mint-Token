# Project Title

Module-3-Project-Create-and-Mint-Token

## Description

For this project, you will write a smart contract to create your own ERC20 token and deploy it using Remix. The contract owner should be able to mint tokens to a provided address and any user should be able to burn and transfer tokens.

### Executing program

// SPDX-License-Identifier: MIT

pragma solidity >=0.6.12 <0.9.0;

// Project: Create and Mint Token, 

// 1. Write a smart contract to create your own ERC20 token.

// 2. The contract owner should be able to mint tokens to a provided address and any user should be able to burn and transfer tokens.

// By importing ERC20.sol, your contract inherits all the functionality and features defined in the ERC20 standard.

// This includes functions like transfer, transferFrom, approve, balanceOf, totalSupply, and more, which are essential for interacting with ERC20 tokens.

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

// By importing Ownable.sol into your contract, you gain access to this functionality,

// allowing you to easily implement ownership-based access control in your smart contracts.

// This is particularly useful for scenarios where certain operations, such as administrative tasks or sensitive operations, should only be performed by the contract owner.

import "@openzeppelin/contracts/access/Ownable.sol";

// The contract TokenArlos inherits from both ERC20 and Ownable, which means it will have access to the functionalities of both contracts.

contract TokenArlos is ERC20, Ownable {

  // Constructor: The constructor function initializes the contract. It takes an initialOwner address as an argument,
  
  // which will be passed to the constructor of the Ownable contract. The Ownable constructor sets the initial owner of the contract.
  
  // Additionally, the constructor of the ERC20 contract is called with the token name "TokenArlos" and symbol "ARL".
  
    constructor(address initialOwner) Ownable(initialOwner) ERC20("TokenArlos", "ARL") {

      // Token Minting: Inside the constructor, _mint function from the ERC20 contract is called to mint an initial supply of 30,000 tokens to the initialOwner.
        _mint(initialOwner, 30000);
    }

    // This function allows the contract owner to mint new tokens and assign them to any address. 
    // This is a common feature in ERC20 tokens, as it allows for the controlled expansion of the token supply when needed.
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // This function allows any user to burn their own tokens, reducing the total supply of the token. 
    // Burning tokens can be useful for various purposes, such as reducing supply to increase token value or removing tokens from circulation.
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    // This function allows any user to transfer tokens from their own address to another address. 
    // It's a fundamental function in ERC20 tokens that enables token holders to send tokens to each other.
    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, to, amount);
        return true;
    }
}   

## Authors

National Teachers College

Razelle Brian L. Arlos

8214515@ntc.edu.ph

