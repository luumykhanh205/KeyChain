# KeyChain - KẾ HOẠCH THỰC HIỆN VÀ TIMELINE CÁ NHÂN

**Người thực hiện: Mỹ Khánh**
**Hạn nộp: 18/06/2026 | Bắt đầu: 28/05/2026**

---

## Tổng Quan Công Việc

Dự án **KeyChain** được thực hiện cá nhân, bao gồm cả phần phát triển hệ thống và phần báo cáo. Người thực hiện chịu trách nhiệm từ giai đoạn nghiên cứu, phân tích yêu cầu, thiết kế hệ thống, xây dựng smart contracts, phát triển giao diện, kiểm thử, triển khai thử nghiệm và hoàn thiện báo cáo.

| Người thực hiện | Vai trò                                                      | Code                                                                                                                           | Report                      |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ | --------------------------- |
| **Mỹ Khánh**    | Full-stack Blockchain Developer + Researcher + Report Writer | Smart contracts, frontend, backend/API routes, unit tests, integration tests, deploy scripts, triển khai Sepolia, kiểm thử E2E | Toàn bộ Chương 1 → Chương 7 |

---

## Phạm Vi Công Việc

### 1. Phần Code

| Hạng mục               | Nội dung thực hiện                                                  | Ưu tiên                     |
| ---------------------- | ------------------------------------------------------------------- | --------------------------- |
| KeyCoin.sol            | ERC-20 token, buyKeyCoin, setRate, withdraw                         | 🔴 Đầu tiên                 |
| GameToken.sol          | ERC-1155, ERC-2981, mint, royaltyInfo, uri                          | 🔴 Đầu tiên                 |
| GameStore.sol          | Catalog, purchaseLicense, RBAC                                      | 🔴 Thứ hai                  |
| ActivationContract.sol | Hardware hash binding, activate/deactivate                          | 🟡 Thứ ba                   |
| Marketplace.sol        | List, buy, auto-royalty, activation reset                           | 🟡 Thứ ba                   |
| GamePass.sol           | Subscribe, renew, expiry check                                      | 🟢 Cuối cùng                |
| Frontend               | Landing, Store, Library, Marketplace, Vendor Portal                 | 🟡 Song song với contracts  |
| API Routes             | Pinata upload, IPFS resolver                                        | 🟢 Sau khi có contracts     |
| Hooks + Providers      | useWallet, useGameStore, useActivation, useMarketplace, useGamePass | 🟢 Sau khi contracts xong   |
| Unit Tests             | Test 6 smart contracts                                              | 🟢 Sau khi có từng contract |
| Integration Tests      | Happy path, secondary market, game pass flow                        | 🟢 Sau unit tests           |
| Deploy Scripts         | deploy.ts, setup-roles.ts, seed-games.ts, verify.ts, copy-abi.sh    | 🟢 Giai đoạn cuối           |
| Sepolia Deployment     | Deploy, setup roles, seed data, verify contract                     | 🟢 Trước demo               |
| E2E Testing            | Test trên trình duyệt và ví thật, chụp screenshots                  | 🟢 Trước khi viết kết quả   |

---

### 2. Phần Báo Cáo

| Chương   | Nội dung                                                                                       | Người thực hiện |
| -------- | ---------------------------------------------------------------------------------------------- | --------------- |
| Chương 1 | Bối cảnh, lý do chọn đề tài, mục tiêu, phạm vi, cấu trúc báo cáo                               | Mỹ Khánh        |
| Chương 2 | Cơ sở lý thuyết: blockchain, Ethereum, smart contract, ERC standards, RBAC, DRM                | Mỹ Khánh        |
| Chương 3 | Phân tích hệ thống: use case, BPMN, customer/vendor/admin journeys                             | Mỹ Khánh        |
| Chương 4 | Thiết kế hệ thống: kiến trúc tổng thể, state machine, RBAC, sequence diagrams, frontend design | Mỹ Khánh        |
| Chương 5 | Hiện thực hệ thống: smart contracts, frontend, backend, deploy Sepolia                         | Mỹ Khánh        |
| Chương 6 | Kiểm thử và đánh giá: unit tests, integration tests, E2E screenshots, security analysis        | Mỹ Khánh        |
| Chương 7 | Kết luận, hạn chế và hướng phát triển                                                          | Mỹ Khánh        |

---

## Chi Tiết Công Việc Cá Nhân

### Mỹ Khánh: Full Project Implementation

**Code**

| Hạng mục          | File / Module                                                            | Nội dung                                                                                                           |
| ----------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| Smart Contract 1  | KeyCoin.sol                                                              | Xây dựng token thanh toán nội bộ KEY, cho phép người dùng mua KeyCoin bằng ETH, admin có thể chỉnh rate và rút ETH |
| Smart Contract 2  | GameToken.sol                                                            | Xây dựng ERC-1155 game license token, hỗ trợ ERC-2981 royalty cho secondary market                                 |
| Smart Contract 3  | GameStore.sol                                                            | Quản lý catalog game, đăng ký game, mua license, phân quyền vendor/admin                                           |
| Smart Contract 4  | ActivationContract.sol                                                   | Quản lý kích hoạt license bằng machineHash, hỗ trợ activate/deactivate                                             |
| Smart Contract 5  | Marketplace.sol                                                          | Cho phép người dùng list license, mua lại license, xử lý royalty và reset activation                               |
| Smart Contract 6  | GamePass.sol                                                             | Quản lý subscription theo thời hạn, hỗ trợ subscribe, renew và kiểm tra expiry                                     |
| Frontend          | Landing, Store, Library, Marketplace, Vendor Portal                      | Xây dựng giao diện người dùng cho customer, vendor và admin                                                        |
| API Routes        | Pinata upload, IPFS resolver                                             | Upload metadata lên IPFS và đọc dữ liệu metadata                                                                   |
| Hooks             | useWallet, useGameStore, useActivation, useMarketplace, useGamePass      | Kết nối frontend với smart contracts                                                                               |
| Unit Tests        | KeyCoin, GameToken, GameStore, ActivationContract, Marketplace, GamePass | Kiểm thử từng smart contract                                                                                       |
| Integration Tests | happy-path, secondary-market, game-pass                                  | Kiểm thử luồng nghiệp vụ hoàn chỉnh                                                                                |
| Deploy Scripts    | deploy.ts, setup-roles.ts, seed-games.ts, verify.ts                      | Tự động deploy, phân quyền, seed dữ liệu và verify contract                                                        |
| E2E Testing       | Browser + wallet testing                                                 | Kiểm thử giao diện thật với ví MetaMask trên Sepolia                                                               |

---

## Timeline 21 Ngày

```text
Tuần 1        28/05 (T5) → 01/06 (CN)      Nghiên cứu + Nền tảng
Tuần 2        02/06 (T2) → 08/06 (CN)      Core Contracts + Frontend cơ bản
Tuần 3        09/06 (T2) → 15/06 (CN)      Hoàn thiện hệ thống + Kiểm thử
Buffer        16/06 (T2) → 18/06 (T4)      Format báo cáo + Nộp bài
```

---

## Tuần 1: 28/05 – 01/06

### Nghiên cứu + Nền tảng

| Ngày  | Việc cần làm                                                                  | Kết quả cần đạt                                 |
| ----- | ----------------------------------------------------------------------------- | ----------------------------------------------- |
| 28/05 | Khảo sát đề tài, xác định phạm vi hệ thống, tạo project structure             | Có outline hệ thống và cấu trúc thư mục ban đầu |
| 29/05 | Viết Chương 1: bối cảnh, lý do chọn đề tài, mục tiêu, phạm vi                 | Hoàn thành draft Chương 1                       |
| 30/05 | Viết Chương 2.1 – 2.2: blockchain, Ethereum, smart contract                   | Hoàn thành phần cơ sở blockchain                |
| 31/05 | Setup Hardhat project, viết KeyCoin.sol và GameToken.sol                      | Có 2 smart contracts đầu tiên                   |
| 01/06 | Viết unit tests cho KeyCoin và GameToken, bắt đầu thiết kế kiến trúc tổng thể | Có test cơ bản và draft Chương 4.1              |

---

## Tuần 2: 02/06 – 08/06

### Core Contracts + Frontend Cơ Bản

| Ngày  | Việc cần làm                                                             | Kết quả cần đạt                       |
| ----- | ------------------------------------------------------------------------ | ------------------------------------- |
| 02/06 | Viết GameStore.sol, hoàn thiện chức năng registerGame và purchaseLicense | Có contract quản lý cửa hàng game     |
| 03/06 | Viết ActivationContract.sol, xử lý activate/deactivate bằng machineHash  | Có contract quản lý kích hoạt license |
| 04/06 | Viết unit tests cho GameStore và ActivationContract                      | Test được các luồng mua và kích hoạt  |
| 05/06 | Viết Chương 2.3, 2.4, 2.5 về ERC standards, RBAC và DRM                  | Hoàn thành Chương 2                   |
| 06/06 | Xây dựng frontend với mock data: Landing, Store, Library                 | Có giao diện cơ bản                   |
| 07/06 | Viết Chương 3: use case, BPMN, customer/vendor/admin journeys            | Hoàn thành draft Chương 3             |
| 08/06 | Viết Chương 4: kiến trúc, state machine, RBAC, sequence diagrams         | Hoàn thành draft Chương 4             |

---

## Tuần 3: 09/06 – 15/06

### Hoàn Thiện Hệ Thống + Kiểm Thử

| Ngày  | Việc cần làm                                                                 | Kết quả cần đạt                            |
| ----- | ---------------------------------------------------------------------------- | ------------------------------------------ |
| 09/06 | Viết Marketplace.sol và GamePass.sol                                         | Hoàn thành đủ 6 smart contracts            |
| 10/06 | Viết unit tests cho Marketplace và GamePass                                  | Hoàn thành unit tests toàn bộ contracts    |
| 11/06 | Viết integration tests: happy path, secondary market, game pass flow         | Có kiểm thử luồng nghiệp vụ hoàn chỉnh     |
| 12/06 | Hoàn thiện frontend: Marketplace, Vendor Portal, real hooks thay mock data   | Frontend kết nối với smart contracts       |
| 13/06 | Viết API routes: Pinata upload, IPFS resolver; hoàn thiện deploy scripts     | Có backend/API và script deploy            |
| 14/06 | Deploy lên Sepolia, setup roles, seed games, verify contracts trên Etherscan | Có địa chỉ contract và link Etherscan      |
| 15/06 | Kiểm thử E2E trên trình duyệt với ví thật, chụp screenshots                  | Có hình ảnh minh họa kết quả chạy hệ thống |

---

## Buffer: 16/06 – 18/06

### Hoàn Thiện Báo Cáo + Nộp Bài

| Ngày  | Việc                                                                                               |
| ----- | -------------------------------------------------------------------------------------------------- |
| 16/06 | Viết Chương 5: hiện thực smart contracts, frontend, backend, deployment                            |
| 17/06 | Viết Chương 6 và Chương 7: kiểm thử, đánh giá, hạn chế, hướng phát triển, kết luận                 |
| 18/06 | Kiểm tra toàn bộ báo cáo, format Word, kiểm tra hình ảnh, bảng biểu, tài liệu tham khảo và nộp bài |

---

## Mục Tiêu Hoàn Thành

| Hạng mục          | Mục tiêu                                                         |
| ----------------- | ---------------------------------------------------------------- |
| Smart Contracts   | Hoàn thành 6 contracts chính của hệ thống                        |
| Frontend          | Có giao diện demo cho customer, vendor và marketplace            |
| Backend/API       | Hỗ trợ upload metadata lên IPFS và đọc metadata                  |
| Unit Tests        | Kiểm thử các chức năng chính của từng contract                   |
| Integration Tests | Kiểm thử các luồng nghiệp vụ quan trọng                          |
| Deployment        | Deploy hệ thống lên Sepolia testnet                              |
| Report            | Hoàn thành đầy đủ Chương 1 đến Chương 7                          |
| Demo              | Có screenshots, contract addresses và link Etherscan để minh họa |

---

## Ghi Chú

Do dự án được thực hiện cá nhân, timeline được điều chỉnh theo hướng ưu tiên hoàn thành các chức năng cốt lõi trước, sau đó mới mở rộng phần kiểm thử, giao diện và báo cáo. Các chức năng quan trọng nhất cần đảm bảo gồm:

1. Người dùng mua KeyCoin.
2. Vendor đăng ký game.
3. Người dùng mua game license.
4. Người dùng kích hoạt license trên thiết bị.
5. Người dùng bán lại license trên marketplace.
6. Hệ thống tự động xử lý royalty cho vendor.
7. Người dùng có thể đăng ký GamePass theo thời hạn.
8. Hệ thống được deploy và kiểm thử trên Sepolia testnet.

Trong trường hợp thời gian hạn chế, mức độ ưu tiên sẽ là:

```text
Smart contracts → Unit tests → Frontend demo → Deploy Sepolia → Report → Integration/E2E screenshots
```
