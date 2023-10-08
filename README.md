# 2023 年度輪講 Git 編
## #1 Git と関連ツール
### Git
Git はファイルの散型バージョン管理システムである. 詳しくは[このサイト](https://www.sejuku.net/blog/5756 "Git とは") 等を参考.
#### インストール
##### ubuntu の場合
ターミナルで以下のコマンドを叩く.
```
sudo apt-get install git
```
##### Windows の場合
[Git for Windows](https://gitforwindows.org/ "Git for Windows") からインストール.

##### Macの場合
ターミナルで以下のコマンドを叩く
```
brew install git
```

### GitHub
GitHub は Git のリモートリポジトリの 1 つで, 世界中の人が自身のコードやデータを保存・公開し, 共有することができるサービスである. 詳しくは[このサイト](https://www.sejuku.net/blog/7901 "GitHub とは") 等を参考.
#### アカウントの作成と 1g-hub への招待
1. [GitHub](https://github.co.jp/ "Github") にアクセスし, "GitHub に登録する" をクリック.
1. ユーザー名とメールアドレス(研究室のもので OK ), パスワードを入力してアカウントを作成する.
1. 各自のメールに 1g-hub への招待が送られるので, URL にアクセスし, 招待を受け入れる.

1g-hub にある manual リポジトリは 1 研での過ごし方や資料の規則などが書かれているので時間があるときに見ておくことを推奨する.

#### Access Token の作成
[個人用アクセス トークンを管理する](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) を参考にアクセストークンを設定する.  
トークンは生成時にしかコピーすることができないため, 自分がわかるようにローカルに保存しておきましょう.


#### git の初期設定
ターミナルを開いて以下のコマンドを実行. アドレスや名前は Github で登録したユーザー名とメールアドレスを用いる.
```
git config --global user.email ここに自分のアドレス
git config --global user.name ここに自分の名前
```

#### GitHub Education の申請(必須ではない)
GitHub Education は学生に与えられた権利であり, 登録することで[様々なメリット](https://education.github.com/pack/offers "Benefits") が得られる.
申請方法は以下の通り.

1. [GitHub Education](https://education.github.com/ "GitHub Education") にアクセスし, 右上の "Sign in" をクリック.
1. 先程作った GitHub アカウントでサインインし, 必要な情報を入力する. "How do you plan to use GitHub?" は "To study." 等適当で OK.
1. GitHub のプロフィールに PRO マークがついていれば申請完了. 早ければ 10 分程度で完了している.


## #2 Git, GitHub 実践
1 研では 1g-hub にそれぞれリモートリポジトリを作成し, そこに毎週の研究報告会や前後期研究発表会の資料をあげる. 今回の輪講では 1g-hub にリモートリポジトリを作成し, ファイルをプッシュする練習をする.
1. リポジトリの作成  
GitHub の "Repositories" の横にある "New" をクリックし, `b3-rinkou` という名前のリポジトリを作る. リポジトリの種類は "Public", "Private"とあるがどちらでも良い. オプションは "Add a README file" にチェックを付ける (他は自由). これでリモートリポジトリが作成される.

1. リポジトリのクローン  
作成したレポジトリを開いて "Code" をクリックして "Clone" から HTTPS の URL をコピペする.
ターミナルで以下のコマンドを叩く.
```
git clone <コピペしたURL>
```

3. ローカルレポジトリの編集(Markdown の書き方練習)  
クローンしたローカルレポジトリ内に新しく rinkou というフォルダを作成し、その中に　rinkou.md というファイルを作成する. 適当なエディタを開いて rinkou.md を開いて編集する.

4. リモートリポジトリへのプッシュ  
カレントディレクトリをクローンしたディレクトリに戻して以下のコマンドを上から順に実行する.
```
git add .
```
```
git commit -m "ここの中の文字列は自由に編集可能"
```
```
git push origin main
```
push の際に `username` と `passward` が求められますが, `username` は Github のユーザー名, `passward` は保存してあるはずのトークンをコピペしてください.

正常に動作すれば,リモートレポジトリにローカルで施した変更が反映されているはずです. 確認してみましょう.

## #3 終わりに

### 強く推奨
本資料中で述べていますが, 改めてまとめておきます.

- 1g-hub にある [manual](https://github.com/1g-hub/manual/tree/master) を熟読する  
  特に [Regulation](https://github.com/1g-hub/manual/blob/master/views/regulation/index.md) の部分は重要です.   

- #2.4 リモートレポジトリへのプッシュ の操作に慣れる  
  4 回生からの週 1 のゼミ, 半期に 1 回の研究会では基本的に資料を Github にあげてその url 経由で資料を提示することになります. そのため, 今回の操作は非常に重要です. ぜひ慣れてください.

### 余裕があれば

- 1g-hub の他の先輩のレポジトリを見てみる  
  フォルダの構成など参考になる点が多いと思います.ゼミの資料用の `WeeklyReport` ディレクトリ , 研究会の資料を入れる `prsn` ディレクトリなどはみんな作ってる印象があります.

- gitの概念の勉強  
  本資料中では時間の都合上, リモートレポジトリなどの語句やプッシュにあたっての各種コマンド (`git add`, `git commit`, `git push`) の意味を説明できていません. なんとなくでも理解しておけばトラブった時の対処の際に役立つと思います. (ex. コミットを間違えた際に`git revert`等のコマンドを使う場合)
  
  