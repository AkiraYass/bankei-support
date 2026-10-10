# Romanesco Apps — 盤景サポートサイト

「盤景 - Bankei」1.0.0の公式サポートサイトとプライバシーポリシーです。HTML5とCSSだけで動作します。ビルド、JavaScript、外部フレームワーク、外部フォント、アクセス解析、広告は使いません。

## ブランドと目的

Romanesco Appsは個人開発のアプリの開発・運営ブランドです。法人名でも運営者の法的な氏名でもありません。App Store Connectの法的販売者名や著作権者名を置き換えるものではありません。公開ページに個人の制作者名や本名は掲載しません。

今回のサイトは盤景の紹介、よくある質問、メールでのお問い合わせ、情報の取り扱いの説明を目的とします。Apple Musicと連携する独立したアプリであることを両ページに明記しています。

## ファイル構成

```text
bankei-support/
├── index.html     # 盤景の紹介・FAQ・お問い合わせ
├── privacy.html   # 盤景1.0.0のプライバシーポリシー
├── style.css      # 共通ブランド・レスポンシブ・ダークモード
└── README.md      # この運用案内・公開前確認・引き継ぎ
```

VinylDisplayとは別のフォルダ・Gitリポジトリとして管理します。サイトのためのアプリ本体・Xcode設定の変更は不要です。内部リンクとCSS参照は相対パスで、GitHub Pagesのリポジトリ名を含むサブパスにも対応します。公開先はGitHub Pagesです。canonical URL、OG URL、App Storeリンクは設定していません。

## ローカルでの表示

`index.html`をブラウザで開くだけで表示できます。`privacy.html`へもそのまま移動できます。

HTTPで確認する場合は、ターミナルでこのフォルダに移動し、Python 3がある環境で次を実行します。

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

ブラウザでローカル確認用の `http://127.0.0.1:8000/` を開きます。終了はターミナルで `Control-C`。これはローカルプレビューであり、Web公開ではありません。

サブパスを確認する場合は、`bankei-support`の親フォルダから、公開対象をこのフォルダだけに絞ったサーバーを使うか、ブラウザの開発者ツールで相対URLの解決先を確認してください。開発用の親フォルダ全体を外部に公開しないでください。

## GitHub Pagesで公開するとき

**2026年10月10日、ユーザーの指示によりGitHub Pagesでの初回公開を実施します。公開元は`main` / `/(root)`です。App Store Connectは変更しません。以下は公開設定の手順です。**

1. GitHubの利用アカウントとリポジトリ名を確定し、このサイト専用のリポジトリを作成します。利用プランに応じたPagesの利用条件と、ソース・コミット情報の公開範囲を確認してください。
2. 下記の公開前確認を完了します。Gitのコミット作者名・メールアドレスも、公開してよい値か確認してください。公開ページに書いていなくても、公開リポジトリの履歴は閲覧されます。
3. ローカルの完成内容を`main`ブランチに用意します。今回の作業ブランチを使う場合は、内容確認後に`main`へ取り込みます。`index.html`、`privacy.html`、`style.css`をリポジトリのルートに配置したままにします。
4. 公開が許可された段階でのみ、確定したGitHubリポジトリをremoteに登録し、`main`をpushします。remoteやユーザー名を推測して設定しないでください。
5. GitHubのリポジトリで **Settings → Pages → Build and deployment → Source: Deploy from a branch** を選びます。
6. **Branch: main / Folder: /(root)** を選んで **Save** します。この操作がサイトの公開につながります。
7. デプロイ完了後、GitHubが表示した実際のHTTPS URLを開きます。サポート・ポリシー・CSS・ページ内リンクが正しく読み込まれることを確認します。利用できる場合は **Enforce HTTPS** を有効にします。

独自のビルド設定やActionsワークフローは不要です。通常のHTML/CSSをルートから配信できます。Pagesの公開元となったファイルは、リンクしていないREADMEも公開され得ます。READMEやGit履歴にも、秘密情報や不要な個人情報を残さないでください。ホスティング側によるアクセス情報の取り扱いは、公開時の設定・規約を確認し、必要な説明をポリシーに追加してください。

公式手順： [GitHub Pagesの公開元を設定する](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## App Store Connectで使うURL

公開が完了してから、実際に表示確認したHTTPS URLを使います。

| 項目 | 対象 |
| --- | --- |
| Support URL | `index.html`（サイトのトップページ） |
| Privacy Policy URL | `privacy.html`（プライバシーポリシーを直接開くページ） |

GitHubリポジトリのソース閲覧URLやREADMEのURL、localhost、未公開のURLは登録しません。公開リポジトリは`AkiraYass/bankei-support`です。実際の公開URLと検証結果は末尾の引き継ぎに記録します。独自ドメインは使用しません。

## ページの更新方法

- FAQ・紹介・問い合わせ案内は`index.html`を編集します。問い合わせ先を変える場合は、両HTMLの表示文字列とすべての`mailto:`を同時に更新します。
- 情報の扱いが変わった場合は、最新の製品実装を確認して`privacy.html`を更新します。対象バージョン、文書作成日・最終更新日、初回公開日の状態を見直します。初回公開日は2026年10月10日です。更新時は初回公開日を維持し、最終更新日を更新してください。
- 色・余白・共通レイアウトは`style.css`を編集します。`:root`とダークモードの変数を対応させ、文字やリンクのコントラストを維持します。
- 共通ヘッダー・フッターは両HTMLにあります。変更時には両ページをそろえます。ブランド名は`Romanesco Apps`、アプリ名は`盤景 - Bankei`に統一します。
- 更新後、下記の表示・リンク確認と`git diff --check`を実行し、全差分を確認してローカルコミットを作ります。pushは公開を行う判断の後に実施します。Pagesの公開元にpushすると再公開される点に注意してください。

## 将来ほかのアプリを追加するとき

現段階では盤景の2ページだけを公開対象とします。実在する次のアプリができた時点で、ブランドトップとアプリごとのページを分ける構成を検討します。例としてブランドトップ＋`bankei/`配下のサポート・ポリシーが考えられますが、今は空のアプリ紹介やプレースホルダーを作りません。

共通CSSの色・文字・ヘッダー・フッターはブランド単位で維持し、各アプリの機能やデータ処理は個別に説明します。移行時には、App Store Connectに登録済みのURLを壊さないよう、既存の`index.html`・`privacy.html`に案内を残すなど移行方法を決めます。内部リンクは移動後の相対パスで再確認します。

## 実装とポリシーの照合根拠

確認日：2026年10月10日。対象：VinylDisplayのコミット`fed3cfa`、盤景1.0.0 (1)。過去の検討履歴より現在のRelease向け実装を優先しました。

| 確認対象（VinylDisplay内の相対パス） | ポリシーに反映した内容 |
| --- | --- |
| `docs/PRIVACY_REVIEW.md`、`docs/SPEC.md`、`docs/DECISIONS.md` | 収集と機能上の通信の区別、Lookup廃止、保存・権限制御、既存の制約 |
| `VinylDisplay/Music/MusicPlaybackMonitor.swift` | MediaPlayerの現在曲・再生状態・再生位置・同一曲のライブラリ画像補完 |
| `VinylDisplay/Music/AppleMusicProvider.swift` | MusicKitによるID指定の楽曲情報・画像URL取得 |
| `VinylDisplay/Music/CatalogArtworkLoader.swift` | HTTPS画像取得、一時セッション、独自の永続画像キャッシュなし |
| `VinylDisplay/Views/TrackInfoView.swift` | プレイリスト画像のAsyncImage。OS管理キャッシュの可能性を除外しない |
| `VinylDisplay/Music/MusicPlaylistsController.swift` | ライブラリPlaylist一覧・entries取得、明示選択時のシステムキュー置換 |
| `VinylDisplay/Music/AppleMusicFavoritesService.swift`、`MusicFavoritesController.swift` | Apple Musicへの状態照会・変更、メモリ上の一時状態、国／地域の照会 |
| `VinylDisplay/Music/AppleMusicAuthorizationService.swift` | MusicKitでの認証・トークン管理。Debug専用診断と製品機能を区別 |
| `VinylDisplay/VinylDisplayApp.swift`、`Views/SettingsMenuView.swift` | 自動ロック防止設定のAppStorage保存 |
| `VinylDisplay/Resources/PrivacyInfo.xcprivacy` | Tracking=false、収集・tracking domainsは空、UserDefaultsにCA92.1 |

アプリのManifestで収集が空であることから、Appleも情報を保持しない、メールも保存しない、とは判断していません。Apple Music側の全通信先・保持期間、OS診断共有をこのソース確認だけで確定することもできません。

## 権利・商標の確認

2026年10月10日にApple公式の[Apple Music Identity Guidelines](https://marketing.services.apple/apple-music-identity-guidelines)（9.2 Credit Lines）と[Apple商標・著作権の利用ガイドライン](https://www.apple.com/legal/intellectual-property/guidelinesfor3rdparties.html)を確認しました。

Apple Musicの名称を使用するため、両ページの法的表記をまとめたフッターに次の指定文を掲載しています。

> Apple and Apple Music are trademarks of Apple Inc., registered in the U.S. and other countries.

Apple Musicの名称は機能の説明に使い、盤景やRomanesco Appsより目立つ表示にはしていません。Appleのロゴ、バッジ、公式サイト風の意匠は使いません。装飾レコードはCSSで作成しており、Apple Musicの楽曲や第三者のジャケット画像をサイトの宣伝素材として転載していません。楽曲・Artworkの権利をRomanesco Appsに帰属させる表記や、ブランドを法的著作権者として扱うクレジットは追加していません。

参考： [Apple Musicとプライバシー](https://www.apple.com/legal/privacy/data/en/apple-music/)、[Appleのアプリ削除・ストレージ管理案内](https://support.apple.com/ja-jp/108429)

## 公開前の確認事項

- 運営主体の法的氏名・連絡先等について、配信地域や適用法令、ストアの要件に応じて何を開示すべきかを確認すること。必要なら専門家に確認し、ブランド名だけで法的な開示義務を満たすと推測しないこと。公開ページで個人名を出さない方針との両立を確認すること。
- App Store Connectの法的販売者名・著作権者名・必要な事業者情報は、Romanesco Appsというブランド表示と別に確認すること。サイトの表記から自動的に転記しないこと。
- 実際に提出する盤景1.0.0のRelease実装・Privacy Manifest・App Privacy申告・権限説明・本ポリシーが一致していること。SDKや通信先の追加があれば再確認すること。
- 既存SPECには、お気に入り解除の公開APIの契約と実機で確認した挙動に差がある旨の記録がある。採用済みのLibrary評価削除の公開可否・現在の公式仕様・実機挙動は、`docs/FAVORITES_INVESTIGATION.md`等も参照して別途確認すること。本サイト作成はこの問題の解消やApp Store審査適合を保証するものではない。
- 問い合わせ先`romanescoapps@gmail.com`で受信・返信できること。問い合わせメールの保持・削除対応の実際の運用が本文と一致すること。受信テストは今回未実施。
- 初回公開日を確定し、ポリシーの公開準備注記・最終更新日を見直すこと。未確定の公開日を遡って記載しないこと。
- Pagesのホスティング側で扱うIPアドレス等の情報、メールサービスの取り扱い、公開範囲・規約を確認すること。必要な説明とリンクをポリシーへ反映すること。
- スマートフォン・タブレット・PC、明暗テーマ、文字拡大、キーボード、必要に応じて実機スクリーンリーダーで再確認すること。リンク先・サブパス・メールアドレスも確認すること。
- 公開HTML、README、Git履歴・作者情報に不要な個人情報がないこと。ブランドを法人と誤認させる表現、架空のアプリ、未確定URLがないこと。
- Appleの商標ガイドラインの更新、公開ページの商標文、独立したアプリである旨を確認すること。

## 初期作成時の検証

2026年10月10日作成。VinylDisplay側は調査のみとし、ファイル・Xcode設定・「盤景について」は変更しません。ユーザー指定のアプリ変更禁止を優先し、同リポジトリの`docs/HANDOFF.md`も変更せず、サイト側の引き継ぎをこの節にまとめます。

ローカル作成、表示確認、サイト専用リポジトリのローカルコミットまでが今回の範囲です。GitHub remoteの登録・push・Web公開・App Store Connect操作・アプリのClean Build・Xcodeテストは対象外です。

検証結果：

- HTMLの開始・終了タグ、重複属性／ID、見出し階層、言語指定、各ページの単一のh1・main、ポリシー9項目、ページ内リンクの参照先を確認。
- 内部リンク・CSSは相対パス。HTTPサーバーの`/bankei-support/`配下で両ページを開き、相互リンクと目次の移動を確認。mailtoの宛先はすべて指定のアドレスと一致。メールアプリの実起動・メール送信は行っていない。
- ローカルChromeで、両ページ×8条件の計16ケースを確認：1440pxのPC、1024pxのタブレット、390pxと320pxのスマートフォン幅、PC／スマートフォンのダークモード、390px／320pxでの文字サイズ200%。横方向のはみ出しなし。
- 通常・暗色・文字拡大のスクリーンショットを確認。本文の文字と背景は両テーマでコントラスト比4.5:1以上。装飾専用のレコードは読み上げ対象外。リンクの操作領域は高さ44px以上。
- JavaScriptを無効にしたブラウザでも表示と内部ナビゲーションが動作。キーボードのTabでスキップリンクに移動し、フォーカス表示とEnterによる本文への移動を確認。強制カラーモード・印刷用スタイルも確認。
- ページ読み込み時の外部リソース要求とJavaScriptエラーは0件。外部フォント、スクリプト、解析・広告・第三者画像なし。外部リンクをクリックした先の通信は、この確認とは別。
- 両HTMLでブランド名・独立アプリの説明・商標文を確認。公開ページへの個人の制作者名や個人名義の混入なし。本文の日本語と現在の実装の対応を確認。
- サイトの全差分と`git diff --check`を最終確認してローカルコミットを作成する。実機Safari／VoiceOver、問い合わせ受信、公開後の実URL・ホスティングの確認は未実施。

確認用のブラウザ自動化やスクリーンショットは一時作業領域に置き、公開用の4ファイルにテストツールや外部ライブラリを追加していません。


## 公開作業・引き継ぎ

2026年10月10日。既存の`a80af68`から公開準備ブランチを作成し、履歴を維持して`main`へ反映します。初回公開日を確定し、GitHub公式文書に基づいてPagesのIPアドレス記録・保存の説明をポリシーに追記しました。

- 公開前の`main`は`a80af68`で作業ツリーはクリーン、remoteなし。GitHubの認証済みアカウントは`AkiraYass`で、同名リポジトリが存在しないことを確認。
- 公開対象と既存履歴はHTML 2件・CSS・READMEの4ファイルのみ。アプリ本体、Xcode設定、鍵、トークン、不要な個人情報は含まれていません。コミット作者・コミッターはRomanesco Appsと公開問い合わせ用メールアドレスです。
- 問い合わせ先は両ページとも`mailto:romanescoapps@gmail.com`。メールの実送信は行いません。
- VinylDisplay本体・同リポジトリの文書・App Store Connectは変更しません。サイトの引き継ぎはこのREADMEで管理します。
- 公開後のURL・デプロイ結果・表示検証は、完了後にこの節へ追記します。
