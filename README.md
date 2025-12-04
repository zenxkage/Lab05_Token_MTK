# Лабораторная работа №05

## Тема: Доработка контракта, Верификация (BSC Testnet)

### Цель

Научиться дорабатывать смарт‑контракт ERC‑20, реализовать ограничения на функцию mint, развернуть контракт в BNB Smart Chain Testnet и выполнить его верификацию.

---

## Используемые инструменты

* Remix IDE
* MetaMask
* OpenZeppelin Contracts
* Solidity 0.8.20
* BNB Smart Chain Testnet
* BscScan Testnet

---

## Описание выполненной работы

### Реализована функция mint

* Mint доступен только владельцу контракта (onlyOwner)
* Максимальная эмиссия ограничена: 1 000 000 MTK

### Параметры токена

* Name: MyToken
* Symbol: MTK
* Decimals: 18

### Деплой контракта

Контракт развернут в BNB Smart Chain Testnet. Адрес контракта: 0xCBaAdbc9f228B038cD4d81A55bD489B33480B1b2.

### Верификация

Контракт будет верифицирован через BscScan Testnet.

### Выпуск токенов

После деплоя будет выполнен mint на указанный адрес.

---

## Скриншоты

Ниже перечислены скриншоты, которые будут добавлены в папку `/screenshots` после загрузки в GitHub:

* deploy_contract.png — скриншот деплоя контракта
* verify_contract.png — скриншот верификации
* mint_tokens.png — выполнение mint
* metamask_token_added.png — добавление токена в MetaMask
* bscscan_transactions.png — отображение транзакций в BscScan

---

## Структура проекта

```
/contract
    MyToken.sol
/screenshots
    (сюда будут добавлены скриншоты)
Отчет_по_токену_MTK.docx
README.md
```

---

## Код контракта

Файл контракта будет расположен в папке `/contract/MyToken.sol`.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    uint256 public constant MAX_SUPPLY = 1_000_000 * 10**18;

    constructor() ERC20("MyToken", "MTK") Ownable(msg.sender) {}

    function mint(address to, uint256 amount) external onlyOwner {
        require(totalSupply() + amount <= MAX_SUPPLY, "Exceeds MAX_SUPPLY");
        _mint(to, amount);
    }
}
```

---

## Ссылки

### ✔ Контракт в BscScan Testnet

[https://testnet.bscscan.com/address/0xCBaAdbc9f228B038cD4d81A55bD489B33480B1b2](https://testnet.bscscan.com/address/0xCBaAdbc9f228B038cD4d81A55bD489B33480B1b2)

### ✔ Верификация контракта

[https://testnet.bscscan.com/address/0xCBaAdbc9f228B038cD4d81A55bD489B33480B1b2#code](https://testnet.bscscan.com/address/0xCBaAdbc9f228B038cD4d81A55bD489B33480B1b2#code)

### ✔ Транзакция деплоя

(находится на вкладке **Transactions**):
[https://testnet.bscscan.com/tx/](https://testnet.bscscan.com/tx/) — смотри первую транзакцию `Contract Creation`.

### ✔ Репозиторий GitHub

[https://github.com/USERNAME/Lab05_Token_MTK](https://github.com/USERNAME/Lab05_Token_MTK)

Будут добавлены после деплоя и верификации контракта.
