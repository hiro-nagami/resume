## 大規模メッセージングアプリ及び、ビジネスアカウント専用アプリの開発

### 概要
大規模メッセージングアプリ開発及び、ビジネスアカウント専用アプリの開発に携わっていました。大規模メッセージングアプリ本体では、アプリ内専用ブラウザの機能開発やスキーマの開発、キャッシュファイルやメッセージの一括削除機能の実装を行っていました。ビジネスアカウント専用アプリでは、開発初期段階からジョインして運営側のトークルームの開発やアプリ内専用ブラウザ周辺の実装、API経由で切り替え可能なタブの実装などを行っていました。

大規模メッセージングアプリ iOS開発メンバー20人、本体開発メンバー100人程度の規模。

### 技術詳細

*言語*

- Objective-C
- Swift

*アーキテクチャ・技術知識*

- MVC
- スレッド
- メモリー管理

*環境*

- GitHub
- Jenkins
- Atlassian Confluence
- Atlassian JIRA

### 課題１
大規模メッセージングアプリのアプリ内キャッシュ削除を実装しました。

*課題*

- ファイル量が多い人は、処理に時間がかかることが多い
- 削除可・削除不可のファイルが同一ディレクトリ内にある

*解決方法*
- group dispatch とdispatch async を 利用して、並行に処理を実行して処理時間を短縮して削除する
- 一気に多くのファイルを削除対象にするのではなく、複数回のリリースでファイルを仕分ける

### 課題２
トークルームの画面を、1つのビジネスアカウントを複数人で運用できるように対応した。

*課題*

- 大規模メッセージングアプリのトークルームは1アカウントに対し1ユーザー前提となっている
- メッセージ機能がメインのアプリなので、トークルームの実装は複雑
- 送信できるメディアを限定する必要がある（公式スタンプ、画像のみ）

*解決方法*

シンプルに、課題を分解しつつ1つずつ対応した。

- 少しずつリファクタリングをしつつ、ビジネスアカウントIDを利用して表示名を変える
- UIを非表示にしつつ現時点で必要ない機能は削除 or コメントアウトする
