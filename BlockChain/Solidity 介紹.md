# Solidity 介紹

Solidity 是以太坊區塊鏈上最受歡迎的智能合約程式語言，它是一種靜態型別的、物件導向的語言，語法與 JavaScript 相似。

## 主要特性

*   **靜態型別**：變數的型別在編譯時確定。
*   **物件導向**：支援繼承、函式庫等概念。
*   **專為區塊鏈設計**：內建對地址、交易、區塊等區塊鏈特有概念的支援。
*   **Gas 機制**：所有操作都需要消耗 Gas，防止無限循環和資源濫用。

## 基本結構

一個典型的 Solidity 合約包含：

*   **版本聲明 (Pragma)**：指定 Solidity 編譯器版本。
*   **合約定義 (Contract)**：類似於類別，包含狀態變數、函式、事件等。
*   **狀態變數 (State Variables)**：儲存在區塊鏈上的變數。
*   **函式 (Functions)**：定義合約的行為。
*   **事件 (Events)**：用於記錄區塊鏈上的操作，方便外部應用監聽。

## 範例 (ERC-20 代幣合約簡化版)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    string public name = "MyToken";
    string public symbol = "MTK";
    uint256 public totalSupply = 1000000;

    mapping(address => uint256) public balanceOf;

    constructor() {
        balanceOf[msg.sender] = totalSupply;
    }

    function transfer(address to, uint256 amount) public returns (bool) {
        require(balanceOf[msg.sender] >= amount, "Not enough tokens");
        balanceOf[msg.sender] -= amount;
        balanceOf[to] += amount;
        return true;
    }
}
```

[[智能合約的程式語言]]
[[智能合約]]
[[區塊鏈如何運作]]
