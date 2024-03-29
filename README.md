# Unit 21: Martian Token Crowdsale

![alt=""](Images/application-image.png)

## Background

After waiting for years and passing several tests, the Martian Aerospace Agency selected to become part of the first human colony on Mars. As a prominent fintech professional, they chose to lead a project developing a monetary system for the new Mars colony. decided to base this new system on blockchain technology and to define a new cryptocurrency named **KaseiCoin**. (Kasei means Mars in Japanese.)

KaseiCoin will be a fungible token that’s ERC-20 compliant. I’ll launch a crowdsale that will allow people who are moving to Mars to convert their earthling money to KaseiCoin.

## Files

Download the following files to help get started:

[KaseiCoin.sol](./Starter_Code/KaseiCoin.sol)

[KaseiCoinCrowdsale.sol](./Starter_Code/KaseiCoinCrowdsale.com)

## Instructions

The steps for this mission are divided into the following subsections:

1. Create the KaseiCoin Token Contract

2. Create the KaseiCoin Crowdsale Contract

3. Create the KaseiCoin Deployer Contract

4. Deploy and Test the Crowdsale on a Local Blockchain


### Step 1: Create the KaseiCoin Token Contract

In this subsection, I’ll create a smart contract that defines KaseiCoin as an ERC-20 token. To do so, complete the following steps:

1. Import the provided `KaseiCoin.sol` starter file into the Remix IDE.

2. Import the following contracts from the OpenZeppelin library:

    * `ERC20`

    * `ERC20Detailed`

    * `ERC20Mintable`

3. Define a contract for the KaseiCoin token, and name it `KaseiCoin`. Have the contract inherit the three contracts that just imported from OpenZeppelin.

4. Inside my `KaseiCoin` contract, add a constructor with the following parameters: `name`, `symbol`, and `initial_supply`.

5. As part of my constructor definition, add a call to the constructor of the `ERC20Detailed` contract, passing the parameters `name`, `symbol`, and `18`. (Recall that 18 is the value for the `decimals` parameter.)

6. Compile the contract by using compiler version 0.5.0.

7. Check for any errors, and debug them as needed.

8. Take a screenshot of the successful compilation of the contract, and add it to the Evaluation Evidence section of the `README.md` file for my GitHub repository.

### Step 2: Create the KaseiCoin Crowdsale Contract

In this subsection, I’ll define the KaseiCoin crowdsale contract. To do so, complete the following steps:

1. Import the provided `KaseiCoinCrowdsale.sol` starter code into the Remix IDE.

2. Have this contract inherit the following OpenZeppelin contracts:

    * `Crowdsale`

    * `MintedCrowdsale`

3. In the `KaisenCoinCrowdsale` constructor, provide parameters for all the features of my crowdsale, such as `rate`, `wallet` (where to deposit the funds that the token raises), and `token`. Configure these parameters as want for my KaseiCoin token.

4. Compile the contract by using compiler version 0.5.0.

5. Check for any errors, and debug them as needed.

6. Take a screenshot of the successful compilation of the contract, and add it to the Evaluation Evidence section of the `README.md` file for my GitHub repository.

### Step 3: Create the KaseiCoin Deployer Contract

In this subsection, I’ll create the KaseiCoin deployer contract. Start by uncommenting the `KaseiCoinCrowdsaleDeployer` contract in the provided `KaseiCoinCrowdsale.sol` starter code.

Next, in the `KaseiCoinCrowdsaleDeployer` contract, I’ll add variables to store the addresses of the `KaseiCoin` and `KaseiCoinCrowdsale` contracts, which this contract will deploy. Finally, I’ll complete the `KaseiCoinCrowdsaleDeployer` contract. To do so, complete the following steps:

1. Create an `address public` variable named `kasei_token_address`, which will store the `KaseiCoin` address once that contract has been deployed.

2. Create an `address public` variable named `kasei_crowdsale_address`, which will store the `KaseiCoinCrowdsale` address once that contract has been deployed.

3. Add the following parameters to the constructor for the `KaseiCoinCrowdsaleDeployer` contract: `name`, `symbol`, and `wallet`.

4. Inside of the constructor body (that is, between the braces), complete the following steps:

    * Create a new instance of the `KaseiCoinToken` contract.

    * Assign the address of the KaseiCoin token contract to the `kasei_token_address` variable. (This will allow to easily fetch the token's address later.)

    * Create a new instance of the `KaseiCoinCrowdsale` contract by using the following parameters:

      * The `rate` parameter: Set `rate` equal to 1 to maintain parity with ether.

      * The `wallet` parameter: Pass in `wallet` from the main constructor. This is the wallet that will get paid all the ether that the crowdsale contract raises.

      * The `token` parameter: Make this the `token` variable where `KaseiCoin` is stored.

    * Assign the address of the KaseiCoin crowdsale contract to the `kasei_crowdsale_address` variable. (This will allow to easily fetch the crowdsale’s address later.)

    * Set the `KaseiCoinCrowdsale` contract as a minter.

    * Have the `KaseiCoinCrowdsaleDeployer` renounce its minter role.

5. Compile the contract by using compiler version 0.5.0.

6. Check for any errors, and debug them as needed.

7. Take a screenshot of the successful compilation of the contract, and add it to the Evaluation Evidence section of the `README.md` file for my Git repository.

### Step 4: Deploy and Test the Crowdsale on a Local Blockchain

In this subsection, I’ll deploy the crowdsale to a local blockchain. I’ll then perform a real-world, preproduction test of my crowdsale. To do so, complete the following steps:

> **Important:** Record a short video or take screenshots that illustrate the following steps as evidence of my deployed crowdsale contract.

1. Deploy the crowdsale to a local blockchain by using Remix, MetaMask, and Ganache.

2. Test the functionality of the crowdsale by using test accounts to buy new tokens and then checking the balances of those accounts.

3. Review the total supply of minted tokens and the amount of wei that the crowdsale contract has raised.

### Optional: Extend the Crowdsale Contract by Using OpenZeppelin

In this optional subsection, can extend the crowdsale contract to enhance its functionality. To do so, I’ll use the following OpenZeppelin contracts:

* The `CappedCrowdsale` contract: Allows to cap the total amount of ether that my crowdsale can raise.

* The `TimedCrowdsale` contract: Allows to set a time limit for my crowdsale by adding an opening time and a closing time.

* The `RefundablePostDeliveryCrowdsale` contract: Allows to refund my investors. Every time that launch a crowdsale, set a goal amount of ether to raise. If don’t reach the goal, it’s a common practice to refund my investors.

> **Hint:** We encourage to read more about these contracts on the [Crowdsales page](https://docs.openzeppelin.com/contracts/2.x/crowdsales) of the OpenZeppelin documentation.

To enhance my KaseiCoin crowdsale with this added functionality, complete the following steps:

1. Import the three OpenZeppelin contracts just described into the `KaseiCoinCrowdsale.sol` contract by using the following code:

    ```solidity
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/CappedCrowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/TimedCrowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/distribution/RefundablePostDeliveryCrowdsale.sol";
    ```

2. In addition to the `Crowdsale` and `MintedCrowdsale` contracts, which my contract previously inherited from OpenZeppelin, have my `KaseiCoinCrowdsale` contract inherit the following three contracts, which just imported:

    * `CappedCrowdsale`

    * `TimedCrowdsale`

    * `RefundablePostDeliveryCrowdsale`

3. In the `KaseiCoinCrowdsale` constructor, add the following parameters:

    * The `uint goal` parameter: The amount of ether that hope to raise during the crowdsale&mdash;that is, the goal of the crowdsale.

    * The `uint open` parameter: The opening time for the crowdsale.

    * The `uint close` parameter: The closing time for the crowdsale.

4. Complete the `KaseiCoinCrowdsale` constructor code by adding calls to the new contracts, as the following code shows:

    ```solidity
    constructor(
            uint256 rate, // rate in TKNbits
            address payable wallet, // sale beneficiary
            KaseiCoin token, // the KaseiCoin itself that the KaseiCoinCrowdsale will work with
            uint goal, // the crowdsale goal
            uint open, // the crowdsale opening time
            uint close // the crowdsale closing time
        ) public
            Crowdsale(rate, wallet, token)
            CappedCrowdsale(goal)
            TimedCrowdsale(open, close)
            RefundableCrowdsale(goal)
        {
            // constructor can stay empty
        }
    ```

    > **Important:** The `RefundablePostDeliveryCrowdsale` contract itself inherits the `RefundableCrowdsale` contract, which requires a `goal` parameter. So in addition to the others, must call the `RefundableCrowdsale` constructor from my `KaseiCoinCrowdsale` constructor. The `RefundablePostDeliveryCrowdsale` contract doesn’t have its own constructor, which is why we use the `RefundableCrowdsale` constructor that it inherits.
    >
    > If forget to call the `RefundableCrowdsale` constructor, `RefundablePostDeliveryCrowdsale` will fail. This is because it doesn't have its own constructor, so it relies on the `RefundableCrowdsale` constructor.

5. Update the `KaseiCoinCrowdsaleDeployer` contract to allow the deployment of the updated crowdsale contract. In the constructor of the deployer contract, add a new `uint` parameter named `goal` that will allow to set the crowdsale goal.

6. previously added an instance of the `KaseiCoinCrowdsale` contract to the KaseiCoin deployer contract. Because we modified the `KaseiCoinCrowdsale` contract to support new functionality, now need to update my previous code with the following code:

    ```solidity
    KaseiCoinCrowdsale kasei_crowdsale = new KaseiCoinCrowdsale (1, wallet, token, goal, now, now + 24 weeks);
    ```

    Note that in the preceding code, added values for the three new parameters. The `goal` parameter represents the amount of ether to raise during the crowdsale. The `now` parameter represents the crowdsale opening time. And, `now + 24 weeks` represents the closing time.

    The `now` function returns the current Ethereum block timestamp in the form of seconds since the Unix epoch. The **Unix epoch** (also known as **Unix time**, **POSIX time**, or **Unix timestamp**) is an integer representing the number of seconds that have elapsed since January 1, 1970 (at midnight coordinated universal time, UTC), not counting leap seconds.

7. Compile and test the updated contract by completing following steps:

    * Send ether to the crowdsale from a different account (that is, not the same account that’s raising funds). Then, once confirm that the crowdsale works as expected, try to add the token to my wallet and to test a transaction.

    * Set the `close` time to `now + 5 minutes` (for a shorter crowdsale) or to any timeline that I'd like to test.

    * When sending ether to the contract, make sure that meet the `goal` of the contract. Then finalize the sale by using the `finalize` function of the `Crowdsale` contract. Note that to finalize the sale, `isOpen` must return false (`isOpen` comes from `TimedCrowdsale` and checks whether the `close` time has passed). If set the `goal` to 300 ether, for example, might need to have multiple accounts buy tokens to meet the goal. If run out of prefunded accounts in Ganache, can create a new workspace.

    * Review my tokens in MetaMask. To do so in MetaMask, click Add Token, click Custom Token, and then enter the address of the token contract. Make sure to buy larger amounts of tokens to get the denomination to appear in my wallet as more than a few wei worth.

8. Create a GitHub repository and a `README.md` file that explains the process for buying KaseiCoin.
