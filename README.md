# TypesOfFunctions
  Types of Functions - Minting, Burning and Transferring Tokens

## Description
    Hello everyone, my name is Carl, and I will discuss with you the ERC20 token with functionalities 
    for minting, burning, and transferring tokens.
    
## Getting Started
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract AdrlsTkn is ERC20 {
    address public ID;

    constructor(string memory OwnerName, string memory Acronym, uint256 Value) ERC20(OwnerName, Acronym) {
        _mint(msg.sender, Value);
        ID = msg.sender;
    }

    function mint(address to, uint256 amount) public {
        require(msg.sender == ID, "Only the owner can mint.");
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
        require(amount <= balanceOf(msg.sender), "Your account has zero balance.");
        _transfer(msg.sender, recipient, amount);
        return true;
    }
}
```
## Executing Program 
    To run this program, you can use Remix, an online Solidity IDE. To get started, go to the 
    Remix website at https://remix.ethereum.org/. Once you are on the Remix website, create a 
    new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension 
    (e.g., HelloWorld.sol). Then copy the code given in the assessment.

## Author 
    Carl Jasper M. Adrales
    8214773@ntc.edu.ph

## License
     This project is licensed under the MIT License - see the LICENSE file for details

