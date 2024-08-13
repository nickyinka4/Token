# MyToken Smart Contract

This Solidity program defines a custom ERC20 token called "nickyinka" (NKYKA). The contract leverages OpenZeppelin libraries to include standard ERC20 functionality, as well as additional features like minting, burning, and pausing the token. The purpose of this contract is to serve as a foundational token for blockchain-based projects, with enhanced controls for the token owner.

## Description

The `MyToken` smart contract is a customizable ERC20 token implemented in Solidity. It uses OpenZeppelin's ERC20, ERC20Burnable, ERC20Pausable, and Ownable extensions to provide a secure and flexible token contract. Key features include:

- **Minting:** The contract owner can mint new tokens to any address.
- **Burning:** The contract owner can burn tokens from any address.
- **Pausing:** The contract owner can pause and unpause all token transfers.
- **Ownership:** Only the owner of the contract has permission to mint, burn, and manage the pausing of token transfers.

The contract is designed for deployment on the Ethereum blockchain and can be used as a foundation for various decentralized applications (DApps).

## Getting Started
- npm start

### Prerequisites

- Solidity compiler version ^0.8.19
- Node.js and npm (for deploying via scripts)
- Truffle or Hardhat (for testing and deployment)
- MetaMask or any other Ethereum-compatible wallet

### Installing

1. Clone the repository:

   ```bash
   git clone https://github.com/your-repo/mytoken.git
   cd mytoken

 ## Contract Code

 ### Executing program

```javascript
pragma solidity ^0.8.19;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, ERC20Burnable, ERC20Pausable, Ownable {
    constructor(address initialOwner)
        ERC20("nickyinka", "NKYKA")
        Ownable(initialOwner)
    {}

    function pause() public onlyOwner {
        _pause();
    }

    function unpause() public onlyOwner {
        _unpause();
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(address account, uint256 amount) public onlyOwner {
        _burn(account, amount);
    }

    function transfer(address recipient, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }

    function _update(address from, address to, uint256 value)
        internal
        override(ERC20, ERC20Pausable)
    {
        super._update(from, to, value);
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.19" (or another compatible version), and then click on the "Compile HelloWorld.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "HelloWorld" contract in the left-hand sidebar, and then click on the "sayHello" function. Finally, click on the "transact" button to execute the function and retrieve the "Hello World!" message.


This file provides a comprehensive overview of your smart contract, including the code, usage instructions, and additional details.
