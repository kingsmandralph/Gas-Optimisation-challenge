# Gas Optimization Bounty by StackUp Explanation

![12 July - Gas Optimisation Challenge](https://github.com/clement-stackup/gas_challenge/assets/120361535/21c826fb-8776-4837-a8fe-b7040426eafa)

## Overview of Bounty

Gas is the unit of measurement for the computational work required to execute a transaction or deploy a smart contract on the Ethereum blockchain. Gas optimization techniques are important because they can significantly reduce the cost of deploying and executing smart contracts, making them more affordable for users.

This bounty challenges you to optimize a smart contract by applying the various listed gas optimization techniques. To complete this bounty, you must apply the techniques described below to the provided smart contract and write a simple unit test. Once you are done, upload your working files to your GitHub repository and submit the GitHub URL to successfully complete the bounty.

## Overview of Gas Optimization Techniques

To successfully complete this bounty, you will need to apply the following gas optimization techniques:

1. **Fixed Size over Dynamic Arrays**: Using fixed-size arrays instead of dynamic arrays can reduce gas consumption because Solidity has to perform less work to manage the memory allocation of arrays in the smart contract

2. **Caching State Variable**: Caching frequently accessed state variable can reduce gas consumption by reducing the number of storage reads required

3. **Implement Uncheck Block**: Using the `unchecked` block can reduce gas consumption by skipping certain checks such as integer overflows

4. **For Loop Increment Syntax**: Using a different for loop increment syntax can help reduce gas consumption

## Explanation of gas optimisation technique used
```js
function optimizedFunction() public {
        uint[10] memory cachedVar = numbers; // caching the numbers arrays
        for (uint i = 0; i < cachedVar.length; ) {
            // using the unchecked block
            unchecked {
                numbers[i] = 0;
                ++i; //used ++i instead of i++ is cheaper
            }
        }
    }
```
The `optimizedFunction` is designed to reduce the gas cost of setting all elements of the `numbers` array to 0. 

1. The function creates a local memory variable `cachedVar` and assigns it the value of the `numbers` array. This is done to cache the `numbers` array in memory, which is cheaper to access than storage.

2. The function then enters a `for` loop that iterates over the length of the `cachedVar` array.

3. Inside the loop, an `unchecked` block is used. This means that arithmetic operations inside this block will not revert if an overflow or underflow occurs. This can save gas because the Solidity compiler does not need to generate code to check for overflows or underflows.

4. Inside the `unchecked` block, the function sets the current element of the `numbers` array to 0.

5. The loop counter `i` is then incremented using the pre-increment operator (`++i`) instead of the post-increment operator (`i++`). This can save a small amount of gas because the pre-increment operator does not need to create a temporary variable to store the original value of `i`.

Overall, the `optimizedFunction` uses several techniques to reduce gas costs, including caching storage variables in memory, using unchecked arithmetic, and using pre-increment instead of post-increment. These techniques can help make the function more efficient and cheaper to execute.
