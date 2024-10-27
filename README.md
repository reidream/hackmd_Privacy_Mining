# Privacy Mining セットアップガイド

## 概要

Privacy Miningは、ブロックチェーン上でプライバシーを保ちながらマイニングを行うシステムです。以下の特徴があります：

- 入金と出金のアドレスを分けて管理することで、プライバシーを確保
- 入金アドレスと出金アドレス間の関連性が低いほど、より高い報酬を獲得可能
- Base networkで実行され、ETHを使用

## 準備するもの

1. PC (Windows, Mac, または Linux)
2. ETH（マイニングユニット分：デフォルトで0.1×10　1ETH使用）
3. RPC プロバイダーのアカウント（Alchemy または Infuraなど）
4. 出金用のウォレット（秘密鍵が必要）

## インストール手順

1. 以下のリンクから最新バージョン（現在v1.1.3）をダウンロード：
   https://github.com/InternetMaximalism/intmax2-mining-cli/releases

2. お使いのOSに合わせたファイルを選択：
   - Windows: `intmax2-mining-cli-windows.exe`
   - Mac: `intmax2-mining-cli-macos`
   - Linux: `intmax2-mining-cli-linux`

3. ダウンロードしたファイルを実行可能にして起動

## セットアップ手順

1. ネットワーク選択
   ```
   Choose network:
   > base
     base-sepolia (testnet)
     mainnet (legacy)
     holesky (legacy-testnet)
   ```
   - `base` を選択してください

2. 利用規約の確認
   ```
   Please read and accept the terms of use
   https://github.com/InternetMaximalism/intmax2-mining-cli/blob/main/docs/terms.md
   Do you accept the terms of use? [y/N]
   ```
   - 内容を確認の上、`y` を入力

3. RPCプロバイダーの設定
   ```
   Choose RPC provider:
   > Alchemy
     Infura
     Other
   ```
   - いずれかのプロバイダーを選択
   - 選択したプロバイダーのProject IDを入力
     - Infuraの場合：https://app.infura.io/ で取得
     - IDのみを入力（https://などは不要）

4. デフォルト設定の確認
   ```
   Use default settings for max gas price (10 gwei), mining unit (0.1 ETH) and mining times (10)? [Y/n]
   ```
   - デフォルト推奨：`Y` を入力
   - カスタマイズする場合：`n` を入力して個別設定

5. 出金用ウォレットの設定
   ```
   Withdrawal private key of base:
   ```
   - 出金先ウォレットの秘密鍵を入力
   - 表示されるアドレスを必ず確認
   - 秘密鍵は安全に保管してください

6. 暗号化パスワードの設定
   ```
   Do you set password to encrypt private keys? [Y/n]
   ```
   - セキュリティのため、パスワード設定を推奨：`Y` を入力

# これで基礎設定は終わりです、次は入金の説明です

## 操作方法

メインメニューには以下のオプションがあります：

```
Select mode (press ctrl+c to abort):
> Mining: performs mining by repeatedly executing deposits and withdrawals
  Claim: claims available ITX tokens
  Exit: withdraws all balances currently and cancels pending deposits
  Export: export deposit private keys
  Check Update: check for updates of this CLI
```

### 各モードの説明

1. **Mining**
   - マイニングを開始するモード
   - 入金アドレスが表示され、必要額（デフォルト0.1 ETH）の入金を待機
   - 入金確認後、自動的にマイニングを開始

2. **Claim**
   - 獲得したITXトークンの請求
   - 報酬が発生している場合に使用

3. **Exit**
   - すべての残高を出金
   - 保留中の入金をキャンセル
   - 処理には約2時間程度かかる場合あり

4. **Export**
   - 入金用ウォレットの秘密鍵をエクスポート
   - MetaMaskなどにインポートして残高確認可能

5. **Check Update**
   - CLIの更新確認

### マイニング開始手順

1. `Mining` を選択
2. 表示される入金アドレスに必要額を送金
   ```
   Network: base
   Withdrawal address(don't deposit Ether to this): 0x... [出金アドレス]
   Total claimable amount: 0 ITX
   Processing mining for deposit address 0x... [入金アドレス]
   ```

3. 入金確認後、自動的にマイニングが開始
   ```
   STATUS: Balance updated
   STATUS: deposit tx hash: 0x...
   Successfully deposited
   STATUS: Deposits: 1 (success: 0 pending: 1 rejected: 0 cancelled: 0) Withdrawn: 0
   ```

### 設定変更について

起動時に以下のオプションが表示される場合：
```
Please select config to use: Config #0 (withdrawal address: 0x...)
What do you want to do with for the config #0?:
> Continue: continue with the existing config
  Overwrite: overwrite the existing config
  Modify: modify the existing config
```

- `Continue`: 既存の設定を継続
- `Overwrite`: 設定を上書き
- `Modify`: 特定の設定のみ変更

## 注意事項

1. 入金アドレスと出金アドレスは別々に管理してください
2. 両アドレス間の関連性が見つかると報酬が減額される可能性があります
3. 秘密鍵は安全に保管してください
4. ガス代や手数料に注意してください
5. 不明な点がある場合は、公式ドキュメントを参照してください

## トラブルシューティング

- プロセスを停止したい場合：`Ctrl + C`
- 入金が確認できない場合：ネットワークの混雑状況を確認
- エラーが発生した場合：ログを確認し、必要に応じて再起動

## 参考リンク

- 公式ドキュメント：https://hackmd.io/zNLtkMXXSCernbkTf1BTrQ#Privacy-Mining
- GitHub リポジトリ：https://github.com/InternetMaximalism/intmax2-mining-cli

## 最後に

このガイドは、Privacy Miningブロックチェーン技術の学習として触れてみたい方向けの参考資料として作成しています。トークンの獲得を目的とする、参加を推奨するものでもありません。
また先ほど、興味で作成して動かしたところなので、理解不足あるとおもいます。
興味のある方は、リスクを理解した上で、学習の一環として触れていただければと思います。不明点や改善点があれば、時間あればアップデートしていく予定です。


