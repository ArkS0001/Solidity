# Next Major
## Coming Soon 🤞
![33](https://github.com/ArkS0001/Solidity/assets/113760964/9bf455d1-25ec-4b54-98ff-e222b8486ee0)

[remix](https://remix-project.org/)
[IDE](https://remix.ethereum.org)


![11](https://github.com/ArkS0001/Solidity/assets/113760964/56e70b06-03a9-43b5-8f99-5866b143515c)

![22](https://github.com/ArkS0001/Solidity/assets/113760964/1dc311e2-1f9f-490f-92c3-f75ff585439b)


# money.sol

    // SPDX-License-Identifier: GPL-3.0
     pragma solidity >=0.4.16 <0.9.0;
    
     contract coin{
         address public minter;
         mapping (address =>uint) public balances;
    
         event Sent(address from, address to, uint amount);
    
         constructor(){
             minter =msg.sender;
         }
    
         function mint (address receiver, uint amount) public{
             require(msg.sender ==minter);
             balances[receiver]+=amount;
         }
    
         error InsufficientBalanace(uint requested, uint available);
    
         function send(address receiver, uint amount) public{
             if(amount > balances[msg.sender])
             revert InsufficientBalanace({
                 requested : amount,
                 available:balances[msg.sender]
             });
             balances[msg.sender]-= amount;
             balances[receiver]+=amount;
             emit Sent(msg.sender,receiver, amount);
         }
    
         }
