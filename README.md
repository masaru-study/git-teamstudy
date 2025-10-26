# git-teamstudy

- git/githubを学びましょう
- 実際に使ってみましょう
- チームでの開発を体験しましょう

## gitを学ぼう
- https://backlog.com/ja/git-tutorial/

## githubのアカウントを作ろう

- https://github.com/ よりsign up する
- MFAはしておくことを推奨します

## 秘密鍵を作ってgithubに登録しよう

```bash
## ssh鍵の作成
tsukabo-notepc@root:~ $ ssh-keygen -t ed25519 -C "your_email@example.com" // ご自身のメアドで
Generating public/private ed25519 key pair.
Enter file in which to save the key (/root/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase): // 空で
Enter same passphrase again: // 空で
Your identification has been saved in /root/.ssh/id_ed25519
Your public key has been saved in /root/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX your_email@example.com
The key's randomart image is:
+--[ED25519 256]--+
|B@oE .           |
|&XO . .          |
|%%o. .           |
|O*+ .  +         |
|*=.o  + S        |
|*+.. . .         |
|o.+ .            |
| o               |
|                 |
+----[SHA256]-----+
tsukabo-notepc@root:~ $ cd .ssh/
tsukabo-notepc@root:.ssh $ ll
合計 32
drwx------  3 root root 4096 10月 26 21:16 ./
drwx------ 27 root root 4096 10月 26 21:09 ../
-rw-------  1 root root  419 10月 26 21:16 id_ed25519 // 秘密鍵
-rw-r--r--  1 root root  104 10月 26 21:16 id_ed25519.pub // 公開鍵

## sshの設定ファイルを作成
tsukabo-notepc@root:~ $ vim config
Host github.com
  User git
  Port 22
  Hostname github.com
  IdentityFile ~/.ssh/id_ed25519 // ご自身の秘密鍵のパス

## permissionの設定
tsukabo-notepc@root:~ $ chmod 600 ~/.ssh/config
tsukabo-notepc@root:~ $ chmod 600 ~/.ssh/id_ed25519

## 公開鍵の中身を確認してgithubに登録
tsukabo-notepc@root:.ssh $ cat id_ed25519.pub
ssh-ed25519 XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX your_email@example.com
公開鍵の中身を https://github.com/settings/keys に登録する

## githubに接続確認
tsukabo-notepc@root:~ $ ssh -T git@github.com
Hi XXXXXXXX! You've successfully authenticated, but GitHub does not provide shell access.
```

## gitの基本コマンド
- git init
- git clone
- git checkout
- git add
- git commit
- git push
- git pull
- git branch
- git fetch
- git merge

## コンフリクト（衝突）を体験しよう
- AさんとBさんが同じファイルを編集してpushした場合に発生する

## おまけ
- 意外と知らない？ Gitコマンド 100本ノック
  - https://qiita.com/ueki05/items/5c233773e3186989bfd3
