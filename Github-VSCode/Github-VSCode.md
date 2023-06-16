## Githubリポジトリ作成

@import "003.png"

|項目名|内容|
|:--|:--|
|Owner|リポジトリの持ち主アカウント|
|Repository name|リポジトリの名称|
|Description|リポジトリの説明文|
|Public|公開リポジトリとして作成|
|Private|非公開リポジトリとして作成|
|**ADD a README file**|リポジトリ作成時にREADMEファイルを追加する or しない|
|**Add .gitignore**|リポジトリ作成時に.gitignoreテンプレートを作成する(言語を選択) or しない(None)|
|Choose a license|リポジトリのライセンスを選択|




## Githubで作成したリポジトリのクローン(VSCode)

**1. 表示されるURLをコピー(画像では `https://github.com/R-Ozawa-2001/Sumple.git`)**

@import "004.png"


**2. Gitリポジトリのクローン を選択**

@import "001.png"

**3. GithubのリポジトリURLをペースト**

→ [GithubのリポジトリURL取得方法](https://zenn.dev/rata/articles/78736aa2f5736e)

@import "002.png"

**4. リポジトリのURL `https://～～～～～` をクリック**

@import "005.png"

**5. エクスプローラが表示されるので、クローン先フォルダを選択**
※選択したフォルダ内にリポジトリ名と同じ名前のフォルダが作成され、その中にソースコードなどが格納される。

@import "006.png"


※以下は、「**ADD a README file**」「**Add .gitignore**」のどちらにもチェックを入れなかった場合の手順

**6. 最初のコミットを作成**

クローンした時点ではまだブランチが存在しないので、コミットを作成→ブランチを発行 の流れでブランチを作成する
コミットがないとブランチを作成できないので、ここでは空のコミットを作成してブランチを発行できるようにする。

- 空のコミットを作成( [参考](https://qiita.com/NorsteinBekkler/items/b2418cd5e14a52189d19) )
`git commit --allow-empty -m "first commit"`


**7. 最初のコミットを作成**

`can't push refs to remote try running pull first to integrate your changes`

@import "008.png"

コミットがない状態で「ブランチの発行」を実行すると上記エラーが発生。
Gitログは以下の通り。
```
> git push -u origin main
error: src refspec main does not match any
error: failed to push some refs to 'https://github.com/R-Ozawa-2001/Sumple.git'
```
エラー詳細は[こちら](https://tubuyaki-tech.com/tubu-git-refspec/)を参考。
噛み砕くと、「"main"ってブランチがローカルにないからpushできないよ～！」って感じ。

Try running "Pull" first~ と書かれているが、プルを行うと下記エラーが発生する。 

`git your configuration specifies to merge with the ref`

@import "007.png"

Gitログは以下の通り。
```
> git pull --tags
Your configuration specifies to merge with the ref 'refs/heads/main'
from the remote, but no such ref was fetched.
```
エラーの内容としては、「'refs/heads/main'からpullしろって言ってるけど、そんなブランチはありません！」といったような感じ。
存在しないブランチに対してpullを実行すると発生するエラーのよう。


#### 発展編
[参考になる記事](https://qiita.com/atchy/items/b3cf5cde7263ec62e9b9)

1. リモートリポジトリ作成(Githubで操作)
2. ローカルリポジトリ作成(git init)
3. Gitオブジェクト(=何らかの変更)ステージング(git add)
4. Gitオブジェクトをブランチ(※1)へコミット(git commit)
5. 作成したブランチをリモートへプッシュ(git push)

※1 リポジトリ作成時(`git init` 実行時)には、現在作業しているブランチに対する参照(HEAD ※2)は作成されるが、その参照が指す実体は作成されない。ブランチの実態は、`git Commit`が行われた時点で作成される。

※2 HEADは、「`git commit`実行時にどのブランチへコミットするのか」を示している