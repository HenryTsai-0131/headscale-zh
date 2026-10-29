🌏 **繁體中文** ｜ [English 原文](https://github.com/juanfont/headscale)

> **非官方翻譯**：本 repo 是 [juanfont/headscale](https://github.com/juanfont/headscale) README 的中文翻譯，與原作者無關，亦非官方出品。
> 原專案授權：BSD-3-Clause（見 [LICENSE](LICENSE)）。翻譯依據原專案 commit `00f597a`（2026-10-29），內容可能落後原文，請以原專案為準。
> 📚 想從零上手？[中文實戰教程](https://vocus.cc/salon/Henry)

---

![headscale logo](https://raw.githubusercontent.com/juanfont/headscale/main/docs/assets/logo/headscale3_header_stacked_left.png)

![ci](https://github.com/juanfont/headscale/actions/workflows/test.yml/badge.svg)

Tailscale 控制伺服器（control server）的開源、可自行託管的實作。

歡迎加入我們的 [Discord server](https://discord.gg/c84AZQhmpx) 一起聊聊。

**注意：** 請務必選擇與你所使用的正式發行版本相同的 GitHub tag，
以確保取得正確的範例設定。`main` 分支可能
包含尚未發行的變更。文件提供穩定版與
開發版兩種版本：

- [穩定版文件](https://headscale.net/stable/)
- [開發版文件](https://headscale.net/development/)

## 什麼是 Tailscale

Tailscale 是建構在 [Wireguard](https://www.wireguard.com/) 之上的
[現代化 VPN](https://tailscale.com/)。
它透過 [NAT 穿透（NAT traversal）](https://tailscale.com/blog/how-nat-traversal-works/)，
在你的網路中的各台電腦之間
[以覆蓋網路（overlay network）的方式運作](https://tailscale.com/blog/how-tailscale-works/)。

Tailscale 的一切皆為開源，唯獨專有作業系統
（Windows 與 macOS/iOS）的 GUI 用戶端，以及控制伺服器除外。

控制伺服器扮演 Tailscale 網路中各節點之間交換 Wireguard 公開金鑰的集散點。
它負責指派用戶端的 IP 位址、
建立各使用者之間的界線、讓使用者之間可以共享機器，
並公開各節點所宣告（advertise）的路由。

[Tailscale 網路（tailnet）](https://tailscale.com/docs/concepts/tailnet)是
Tailscale 指派給個人使用者或組織的
私有網路。

## 設計目標

Headscale 旨在實作一個可自行託管、開源的
[Tailscale](https://tailscale.com/) 控制伺服器替代方案。Headscale 的目標是
為自行託管者與愛好者提供一個開源伺服器，讓他們能用於
自己的專案與實驗環境。它的範圍刻意設得很小，僅支援_單一_ Tailscale
網路（tailnet），適合個人使用，或小型開源
組織使用。

## 支持 Headscale

如果你喜歡 `headscale` 並覺得它有用，儲存庫中提供了贊助與捐款
按鈕。

## 功能

請參閱[文件中的「Features」](https://headscale.net/stable/about/features/)。

## 用戶端作業系統支援

請參閱[文件中的「Client and operating system support」](https://headscale.net/stable/about/clients/)。

## 執行 headscale

**請注意，我們不支援也不鼓勵使用反向代理（reverse proxy）
與容器來執行 Headscale。**

請參閱 [`documentation`](https://headscale.net/stable/)。

NixOS 使用者可在 [`nix/`](https://github.com/juanfont/headscale/blob/main/nix) 取得模組。

## 來自 `main` 的建置版本

來自 `main` 分支的開發建置版本以容器映像檔與
執行檔的形式提供。詳情請參閱[開發建置版本](https://headscale.net/stable/setup/install/main/)
文件。

## 演講

- Fosdem 2026（影片）：[Headscale & Tailscale: The complementary open source clone](https://fosdem.org/2026/schedule/event/KYQ3LL-headscale-the-complementary-open-source-clone/)
  - 講者：Kristoffer Dalby
- Fosdem 2023（影片）：[Headscale: How we are using integration testing to reimplement Tailscale](https://fosdem.org/2023/schedule/event/goheadscale/)
  - 講者：Juan Font Alonso 與 Kristoffer Dalby

## 免責聲明

本專案與 Tailscale Inc. 無關。

然而，Headscale 的其中一位活躍維護者[任職於 Tailscale](https://tailscale.com/blog/opensource)，且他獲准在工作時間投入本專案的貢獻。這位維護者的貢獻會由其他維護者進行審查。

維護者們共同決定專案的方向。其基本原則是服務自行託管者、愛好者與業餘玩家的社群，同時維持專案的永續經營。

## 貢獻

請閱讀 [CONTRIBUTING.md](https://github.com/juanfont/headscale/blob/main/CONTRIBUTING.md) 檔案。

也請參閱我們的 [AI_POLICY.md](https://github.com/juanfont/headscale/blob/main/AI_POLICY.md)。

### 需求

若要為 headscale 做出貢獻，你需要最新版本的 [Go](https://golang.org)
與 [Buf](https://buf.build)（Protobuf 產生器）。

我們建議使用 [Nix](https://nixos.org/) 來建立開發環境。這可以
透過 `nix develop` 完成，它會安裝所需工具並提供一個 shell。
這能確保你擁有與 `headscale` 維護者相同的開發環境。

### 程式碼風格

為了在貢獻數量不斷增加的情況下維持一定程度的一致性，
本專案採用了 lint 與風格／格式化規則：

**Go** 程式碼以 [`golangci-lint`](https://golangci-lint.run) 進行 lint，
並以 `golangci-lint` 的格式化工具
（[`gofumpt`](https://github.com/mvdan/gofumpt)、`gci`、`goimports`）進行格式化。
請設定你的編輯器在開發時執行這些工具，並確保在提交任何程式碼之前
執行 `make lint` 與 `make fmt`。

**Proto** 程式碼以 [`buf`](https://docs.buf.build/lint/overview) 進行 lint，
並以 [`clang-format`](https://clang.llvm.org/docs/ClangFormat.html) 進行格式化。

**文件**以 [`mdformat`](https://mdformat.readthedocs.io) 進行格式化。

**其餘部分**（Markdown、YAML 等）以 [`prettier`](https://prettier.io) 進行格式化。

請查看 `.golangci.yaml` 與 `Makefile` 以了解具體設定。

### 安裝開發工具

- Go
- Buf
- Protobuf tools

安裝並啟用：

```shell
nix develop
```

### 測試與建置

專案的某些部分需要由 Protobuf 產生 Go 程式碼
（若你變更了 `proto/` 中的內容），且必須以下列指令（重新）產生：

```shell
make generate
```

**注意**：請將 `gen/` 中的變更放在獨立的 commit 中提交，以便審查。

執行測試：

```shell
make test
```

建置程式：

```shell
make build
```

### 開發工作流程

我們建議使用 Nix 來管理相依套件，以確保你擁有所有必要的工具。如果你偏好自行管理相依套件，也可以直接使用 Make：

**使用 Nix（建議）：**

```shell
nix develop
make test
make build
```

**使用你自己的相依套件：**

```shell
make test
make build
```

若缺少任何必要工具，Makefile 會發出警告並建議執行 `nix develop`。執行 `make help` 可查看所有可用的目標。

## 貢獻者

<a href="https://github.com/juanfont/headscale/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=juanfont/headscale" />
</a>

使用 [contrib.rocks](https://contrib.rocks) 製作。
