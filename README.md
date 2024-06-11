# mytoken1
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

contract MyToken {
    string public name = "My Token";
    string public symbol = "MTK";
    uint public totalSupply = 0;

    mapping(address => uint) public balances;

    function mint(address _to, uint _amount) public {
        totalSupply += _amount;
        balances[_to] += _amount;
    }

    function burn(address _from, uint _amount) public {
        require(balances[_from] >= _amount, "Insufficient balance");
        totalSupply -= _amount;
        balances[_from] -= _amount;
    }
}
