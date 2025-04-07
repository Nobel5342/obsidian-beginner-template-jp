# GitHub連携の設定

Obsidianのノートをバックアップし、複数のデバイス間で同期するために、GitHubとの連携が便利です。このガイドでは、GitHub連携の設定方法を段階的に説明します。

## 🌟 GitHubとの連携メリット

GitHubと連携することで以下のメリットがあります：

1. **無料でのバックアップ**: プライベートリポジトリを無料で作成可能
2. **バージョン管理**: 変更履歴が残るので、過去の状態に戻すことができる
3. **複数デバイス間の同期**: PCとモバイルデバイス間でノートを同期できる
4. **共同編集**: 必要に応じて他の人とノートを共有・編集できる
5. **自動化**: コミットとプッシュを自動化できる

## 🔧 事前準備

### GitHubアカウントの作成

1. [GitHub公式サイト](https://github.com)にアクセス
2. 「Sign up」をクリックしてアカウント作成
3. 指示に従って登録を完了

### Gitのインストール

#### Windows

1. [Git for Windows](https://gitforwindows.org/)をダウンロード
2. インストーラーを実行し、基本的にはデフォルト設定でインストール
3. コマンドプロンプトで `git --version` を実行して確認

#### Mac

1. ターミナルを開く
2. `git --version` を実行（初回実行時にインストールプロンプトが表示される）
3. 指示に従ってインストール

または、[Homebrew](https://brew.sh/)がインストールされている場合：
```bash
brew install git
```

#### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git
```

## 📁 リポジトリの設定

### 1. GitHubでリポジトリを作成

1. GitHubにログイン
2. 右上の「+」アイコン → 「New repository」をクリック
3. リポジトリ名を入力（例: `obsidian-notes`）
4. 「Private」を選択（ノートをプライベートに保つため）
5. 「Add a README file」にチェックを入れる
6. 「Create repository」をクリック

### 2. ローカルでリポジトリをクローン

既存のObsidianボルトがある場合：

1. コマンドプロンプト/ターミナルを開く
2. Obsidianボルトとは別の場所に移動
3. 以下のコマンドを実行（URLは作成したリポジトリのものに置き換え）

```bash
git clone https://github.com/あなたのユーザー名/obsidian-notes.git
```

4. クローンしたフォルダ内にObsidianボルトの内容をコピー（.gitフォルダを除く）

新規のObsidianボルトを作成する場合：

1. クローンしたリポジトリをObsidianで新規ボルトとして開く

### 3. 初期設定

1. コマンドプロンプト/ターミナルでクローンしたリポジトリに移動
2. Gitの初期設定を行う

```bash
git config user.name "あなたの名前"
git config user.email "あなたのメールアドレス"
```

3. 初期コミットを作成（既存のボルトをコピーした場合）

```bash
git add .
git commit -m "Initial commit"
git push
```

## 🔌 Obsidian Git プラグインの設定

### 1. プラグインのインストール

1. Obsidianの設定（⚙️）を開く
2. 左メニューから「コミュニティプラグイン」を選択
3. 「サードパーティプラグインを有効にする」を選択
4. 「閲覧」をクリック
5. 検索ボックスに「Obsidian Git」と入力
6. 「インストール」をクリック
7. インストール完了後、プラグインを有効化

### 2. プラグインの設定

1. 「コミュニティプラグイン」の「Obsidian Git」横の歯車アイコン（⚙️）をクリック
2. 以下の設定を確認・調整

**基本設定**:
- 「バックアップ間隔（分）」: 自動バックアップの間隔（例: 10分）
- 「自動バックアップ」: オンにすると定期的に自動コミット
- 「自動プル間隔（分）」: 自動同期の間隔（例: 10分）
- 「起動時にプル」: オンにすると起動時に最新の状態を取得

**コミットメッセージ設定**:
- 「カスタムコミットメッセージ」: 任意のメッセージを設定可能
- 「コミット時の変更ファイル数表示」: オンにするとコミットに含まれるファイル数を表示

**詳細設定**:
- 「認証なしでGitプッシュを有効」: Gitの資格情報がすでに設定されている場合はオン
- 「.gitignoreにリストされていないファイルのバックアップを無視」: 通常はオフ

### 3. 日常的な使用方法

**手動コミット**:
1. コマンドパレット（`Ctrl+P` / `Cmd+P`）を開く
2. 「Obsidian Git: Create backup」を実行

**変更の取得（プル）**:
1. コマンドパレット（`Ctrl+P` / `Cmd+P`）を開く
2. 「Obsidian Git: Pull」を実行

**変更の送信（プッシュ）**:
1. コマンドパレット（`Ctrl+P` / `Cmd+P`）を開く
2. 「Obsidian Git: Push」を実行

**変更履歴の確認**:
1. コマンドパレット（`Ctrl+P` / `Cmd+P`）を開く
2. 「Obsidian Git: View history」を実行

## 📱 モバイルデバイスとの同期

### iOSの場合

iOSではWorking Copyというアプリを使用します。

**Working Copyの設定**:
1. App Storeから「Working Copy」をインストール
2. GitHubアカウントでログイン
3. 作成したリポジトリをクローン
4. 「設定」→「ファイルの共有」→「リポジトリを連携」

**ObsidianとWorking Copyの連携**:
1. Obsidianでボルトを作成
2. 「ローカルから開く」でWorking Copyのリポジトリを選択
3. 変更を行ったら、Working Copyアプリで変更をコミット・プッシュ

### Androidの場合

Androidでは複数の選択肢がありますが、ここではTermuxとMGitの組み合わせを説明します。

**Termuxの設定**:
1. Google PlayからTermuxをインストール
2. Termuxを起動し、以下のコマンドを実行

```bash
pkg update
pkg install git
```

3. Gitの設定を行う

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

**MGitの設定**:
1. Google PlayからMGitをインストール
2. MGitを起動し、リポジトリをクローン
3. GitHubのユーザー名とパスワード（またはトークン）を入力

**ObsidianとMGitの連携**:
1. Obsidianでボルトを作成
2. 「ローカルから開く」でMGitのリポジトリを選択
3. 変更を行ったら、MGitアプリで変更をコミット・プッシュ

## 🔐 セキュリティと認証

### 個人アクセストークンの設定

GitHubはパスワード認証よりも個人アクセストークン（PAT）の使用を推奨しています。

**トークンの作成**:
1. GitHubにログイン
2. 右上のプロフィールアイコンをクリック → 「Settings」
3. 左側のメニューで「Developer settings」 → 「Personal access tokens」 → 「Tokens (classic)」
4. 「Generate new token」をクリック
5. トークンの名前（例: Obsidian Git）を入力
6. 期限を選択
7. 「repo」にチェックを入れる
8. 「Generate token」をクリック
9. 表示されたトークンをコピー（一度しか表示されないので注意）

**トークンの使用**:
- Windows/Macの場合: 初回プッシュ時にユーザー名とトークンの入力を求められる
- 資格情報がキャッシュされるので、以降は入力不要

### .gitignoreの設定

プライベートな情報やキャッシュを同期から除外するために、.gitignoreファイルを設定しましょう。

**推奨の.gitignore設定**:
```
# Obsidian設定の一部
.obsidian/workspace.json
.obsidian/workspace
.obsidian/workspace.json
.obsidian/cache
.trash/

# プラグインのキャッシュやローカル設定
.obsidian/*.json

# プライベートなファイル（任意）
Private/
*.private.md
```

## 🔄 トラブルシューティング

### よくある問題と解決法

1. **認証エラー**
   - 個人アクセストークンが正しいか確認
   - GitHubアカウントの二要素認証設定を確認

2. **コンフリクト（競合）**
   - 手動でマージが必要
   - コマンドパレットから「Obsidian Git: Open source control view」を実行して競合を解決

3. **プッシュ/プルが動作しない**
   - インターネット接続を確認
   - Gitがインストールされているか確認
   - リモートURLが正しく設定されているか確認

4. **大きなファイルのエラー**
   - GitHubは大きなファイル（100MB以上）を拒否する場合がある
   - 大きなファイルは.gitignoreに追加するか、Git LFSを検討

### コマンドラインで問題を解決

以下のコマンドが問題解決に役立つことがあります：

**リモートURLの確認**:
```bash
git remote -v
```

**リモートURLの変更**:
```bash
git remote set-url origin https://github.com/あなたのユーザー名/obsidian-notes.git
```

**強制プル**（変更を破棄して最新を取得）:
```bash
git fetch --all
git reset --hard origin/main
```

**すべての変更を取り消す**:
```bash
git reset --hard HEAD
```

## 📊 応用テクニック

### ブランチの活用

異なる目的や実験的な変更にはブランチを活用すると便利です。

**新しいブランチの作成**:
```bash
git checkout -b 新しいブランチ名
```

**ブランチの切り替え**:
```bash
git checkout ブランチ名
```

**ブランチのマージ**:
```bash
git checkout main
git merge ブランチ名
```

### GitHub Pagesでノートを公開

特定のノートを公開したい場合、GitHub Pagesで簡単にウェブサイトとして公開できます。

**設定手順**:
1. GitHubリポジトリの「Settings」→「Pages」
2. 「Source」で「main」ブランチを選択
3. 「Save」をクリック
4. 数分後、公開URLが表示される

**注意点**:
- プライベートリポジトリでもPagesは公開される
- 公開したくないノートは別リポジトリに分けることを推奨

### GitHub Actionsの活用

GitHub Actionsを使って、自動バックアップや変換などの作業を自動化できます。

**サンプルワークフロー** (.github/workflows/backup.yml):
```yaml
name: Backup

on:
  schedule:
    - cron: '0 0 * * *'  # 毎日午前0時に実行

jobs:
  backup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Create Backup
        run: |
          echo "Backup created at $(date)" > backup.log
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add backup.log
          git commit -m "Automatic backup"
          git push
```

## 🔄 次のステップ

GitHub連携の設定が完了したら、次のステップに進みましょう：

- [[00_はじめに/008_高度なプラグインの活用]]: Dataview、Journalsなどの高度なプラグイン
- [[00_はじめに/009_Obsidianコミュニティへの参加]]: フォーラムやDiscordでの情報交換
- [[00_はじめに/010_デジタルガーデンの作り方]]: 知識ベースを育て、進化させる方法

---

GitHubとの連携は最初は複雑に感じるかもしれませんが、一度設定すれば、バックアップと同期の心配がなくなります。少しずつ試しながら、自分に合った運用方法を見つけていきましょう。
