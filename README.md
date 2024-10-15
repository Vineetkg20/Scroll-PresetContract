This repository contains the Solidity smart contract for VOSC (VineetonScroll), a custom ERC-20 token deployed on the Ethereum blockchain. The VOSC token follows standard ERC-20 functionality, with features for minting, burning, and transferring tokens.

Token Details
Token Name: VineetonScroll
Symbol: VOSC
Decimals: 18
Total Supply: 10,000,000 VOSC (10 million)
Features
The VOSC token provides standard ERC-20 functionality with some added capabilities:

Minting: The contract owner can mint additional tokens, increasing the total supply (within limits).
Burning: Any holder of VOSC tokens can burn their tokens, reducing the total supply.
Transfer: VOSC tokens can be transferred between Ethereum addresses.
Allowance and Approval: Users can approve others to spend tokens on their behalf using the approve and transferFrom functions.
Getting Started
Prerequisites
To work with the VOSC contract, you will need the following:

Solidity Compiler: You can use online tools like Remix or install a framework such as Hardhat or Truffle for local development.
Node.js & npm: If you're using Hardhat or Truffle, ensure you have Node.js and npm installed.
Metamask: For deploying and interacting with the contract, you'll need a web3 wallet like Metamask.
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/your-username/Scroll-PresetContract.git
cd Scroll-PresetContract
Set Up Solidity Development Environment:

You can use Remix to compile and deploy the contract, or set up Hardhat or Truffle locally by installing their dependencies:
bash
Copy code
npm install --save-dev hardhat
# Or, for Truffle users
npm install -g truffle
Compile the Contract:

If using Remix, open the VOSC.sol file in Remix and compile it there.
If using Hardhat/Truffle, compile the contract locally:
bash
Copy code
npx hardhat compile
Deployment
Using Remix:
Open Remix.
Copy the code from VOSC.sol into a new Solidity file in Remix.
Compile the contract using the Solidity compiler in Remix.
Connect to your Ethereum wallet (e.g., MetaMask) and select a network (such as a testnet like Rinkeby or Goerli).
Deploy the contract by clicking on the Deploy button in Remix.
Using Hardhat:
Set up a deployment script (e.g., deploy.js) in your Hardhat project:

javascript
Copy code
async function main() {
  const VOSC = await ethers.getContractFactory("VOSC");
  const vosc = await VOSC.deploy();
  console.log("VOSC deployed to:", vosc.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
Deploy the contract using:

bash
Copy code
npx hardhat run scripts/deploy.js --network rinkeby
Interacting with the Contract
You can interact with the VOSC smart contract using tools like Ethers.js or Web3.js in a JavaScript/Node.js environment, or via the Remix interface. The most common interactions include:

Checking balance:

solidity
Copy code
balanceOf(address account) → uint256
Transferring tokens:

solidity
Copy code
transfer(address recipient, uint256 amount) → bool
Approving someone to spend tokens on your behalf:

solidity
Copy code
approve(address spender, uint256 amount) → bool
Transferring tokens on behalf of another user:

solidity
Copy code
transferFrom(address sender, address recipient, uint256 amount) → bool
Minting new tokens (owner only):

solidity
Copy code
mint(uint256 amount) → bool
Burning tokens:

solidity
Copy code
burn(uint256 amount) → bool
Testing
If you're using a framework like Hardhat or Truffle, you can write unit tests to validate the smart contract functions. For example, you can use Mocha and Chai for testing in Hardhat.

Here’s a basic example for testing the token's minting functionality:

javascript
Copy code
const { expect } = require("chai");

describe("VOSC Token", function () {
  it("Should mint new tokens correctly", async function () {
    const [owner] = await ethers.getSigners();
    const VOSC = await ethers.getContractFactory("VOSC");
    const vosc = await VOSC.deploy();

    await vosc.mint(1000);
    expect(await vosc.totalSupply()).to.equal(10001000000000000000000000); // Check total supply after minting
  });
});
Run your tests with:

bash
Copy code
npx hardhat test
Contributing
Contributions to the Scroll-PresetContract project are welcome! If you would like to add new features or improve existing ones, feel free to submit a pull request or open an issue. Please make sure that your code adheres to the repository's coding guidelines and passes all tests.

License
This project is licensed under the MIT License. See the LICENSE file for more details.
