# Donkey Staking
## Description
Donkey Staking Contract allows users to stake their DON tokens for a predetermined term(lockupTerm) after which users can claim their principal with interest.  
## Test

### Network
`Ropsten`
### DON Faucet
Every account can faucet 1000 DONs each day
- Contract Address : `0xeb67F8889A183000f4a04eD9d42b9710FA418c8a`
- Function
    - mintDonkey()
### Contract

> To ease the testing process, the lockup term in each contract has been set in minutes. The lockup term on production will be significantly longer (ranging from months to years).


Before mint DON tokens, you must first make `Donkey Contract` approve Staking Contract to spend DON amount greater than mint amount.

``` solidity
approve(address spender, uint rawAmount)

ex) approve(Staking Contract address, 1000)
```


`0x3fF3C4690dA9718c55299e2dC77aFBc4ABcEBB88`
- lockupTerm : 3 minutes
- interestLimitAmount : 3000
- interestRate : 30%

`0x32379e1dDe44290d06F243cC9911B4893E2eBA22`
- lockupTerm : 6 minutes
- interestLimitAmount : 6000
- interestRate : 50%

`0x507D94e8B9f8Db73166F8aaE7764C5B9cF0B4d6b`
- lockupTerm : 12 minutes
- interestLimitAmount : 12000
- interestRate : 100%

`0x87be2F22e0796123F9828EDED11Bd1Dc796e39e5`
- lockupTerm : 24 minutes
- interestLimitAmount : 24000
- interestRate : 200%

`0x1D1130a8fBF98d97733b37D92FD9D84CA1E909Db`
- lockupTerm : 36 minutes
- interestLimitAmount : 36000
- interestRate : 300%

`0xEdf0435407a06bFfCed997F9F2703eE813e6614A`
- lockupTerm : 60 minutes
- interestLimitAmount : 60000
- interestRate : 500%

### Staking Contract ABI
``` javascript
[
    {
      "constant": true,
      "inputs": [
        {
          "name": "",
          "type": "address"
        },
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "name": "stakingProductOf",
      "outputs": [
        {
          "name": "releaseTime",
          "type": "uint256"
        },
        {
          "name": "principal",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "stakingMetaData",
      "outputs": [
        {
          "name": "lockupTerm",
          "type": "uint256"
        },
        {
          "name": "interestLimitAmount",
          "type": "uint256"
        },
        {
          "name": "interestRate",
          "type": "uint256"
        },
        {
          "name": "totalPrincipalAmount",
          "type": "uint256"
        },
        {
          "name": "totalPaidInterestAmount",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "",
          "type": "address"
        },
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "name": "allStakingProductsTimestampOf",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "admin",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "minter",
          "type": "address"
        },
        {
          "indexed": false,
          "name": "mintAmount",
          "type": "uint256"
        }
      ],
      "name": "Mint",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "redeemer",
          "type": "address"
        },
        {
          "indexed": false,
          "name": "redeemAmount",
          "type": "uint256"
        }
      ],
      "name": "Redeem",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "redeemer",
          "type": "address"
        },
        {
          "indexed": false,
          "name": "redeemAmount",
          "type": "uint256"
        }
      ],
      "name": "RedeemPrincipal",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "newLockupTerm",
          "type": "uint256"
        },
        {
          "indexed": false,
          "name": "newLimitAmount",
          "type": "uint256"
        },
        {
          "indexed": false,
          "name": "newInterestRate",
          "type": "uint256"
        }
      ],
      "name": "UpdateStakingStandard",
      "type": "event"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "donkeyAddress_",
          "type": "address"
        },
        {
          "name": "lockupTerm_",
          "type": "uint256"
        },
        {
          "name": "interestLimitAmount_",
          "type": "uint256"
        },
        {
          "name": "interestRate_",
          "type": "uint256"
        },
        {
          "name": "controller_",
          "type": "address"
        }
      ],
      "name": "initialize",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "mintAmount",
          "type": "uint256"
        }
      ],
      "name": "mint",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "registeredTimestamp",
          "type": "uint256"
        }
      ],
      "name": "redeem",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "registeredTimestamp",
          "type": "uint256"
        }
      ],
      "name": "redeemPrincipal",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "newLockupTerm",
          "type": "uint256"
        },
        {
          "name": "newLimitAmount",
          "type": "uint256"
        },
        {
          "name": "newInterestRate",
          "type": "uint256"
        }
      ],
      "name": "updateStakingStandard",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "currentUsedRateOfInterestLimit",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "account",
          "type": "address"
        }
      ],
      "name": "stakingProductsOf",
      "outputs": [
        {
          "components": [
            {
              "name": "startTime",
              "type": "uint256"
            },
            {
              "name": "releaseTime",
              "type": "uint256"
            },
            {
              "name": "principal",
              "type": "uint256"
            },
            {
              "name": "lockupTerm",
              "type": "uint256"
            },
            {
              "name": "interestRate",
              "type": "uint256"
            }
          ],
          "name": "",
          "type": "tuple[]"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "account",
          "type": "address"
        }
      ],
      "name": "currentTotalDonBalanceOf",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    }
  ]
```
### DON Minter ABI
``` javascript
[
    {
      "constant": true,
      "inputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "name": "mintedBlockNumberOf",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "lockupTerm",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "donkeyAddress",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "owner",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "inputs": [
        {
          "name": "donkeyAddress_",
          "type": "address"
        },
        {
          "name": "lockupTerm_",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "donkeyAddressNew",
          "type": "address"
        },
        {
          "name": "lockupTermNew",
          "type": "uint256"
        }
      ],
      "name": "updateInfo",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "mintDonkey",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    }
  ]
```
## Error code  

E1
- revert when unauthorized

E67
- revert when reentered

E80
- revert when transferIn overflow

E81
- revert when transferOut failed

E101
- revert when `mintAmount` is equal to or below zero

E102
- revert when the same timestamp exists in `stakingProductOf[acocunt]`

E103
- revert when `totalExpectedInterest` exceeds `interestLimitAmount`

E104
- revert when user has not enough balance to mint

E105
- revert when `claimDonBehalf` fails

E106
- revert when trying to redeem product which has principal equal or below zero

E107
- revert in `redeem` when current block.timestamp < relaseTime

E108
- revert in `redeem`, `redeemPrincipal` when contract has insufficient balance to transfer

## Notice
Staking Contract use `claimDonkeyBehalfOf` function of Controller Contract.
```
  function claimDonkeyBehalfOf(address account) external returns (bool) {
      require(isStakingContract[msg.sender], "E1");
      claimDonkey(account); 
      return true;
  }
```
This function claim controller's donkeyAccrued to account and returns true if succeeds.
> Only Staking Contracts can call this function.  
> Only admin can set isStakingContract.
## Attribution

Some of this codebase is modified from existing works, including:

[Compound](https://github.com/compound-finance)  
[OpenZepplin](https://github.com/OpenZeppelin)


> refers to [Donkey License](https://docs.donkey.fund/about/security)

## License

### BSD 3-Clause "New" or "Revised" License
> A permissive license similar to the BSD 2-Clause License, but with a 3rd clause that prohibits others from using the name of the project or its contributors to promote derived products without written consent.


```
Copyright 2021 Donkey

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```