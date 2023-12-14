
## Goの環境構築
- Go言語は[The Go Programming Language - Downloads](https://go.dev/dl/)からダウンロードすることが可能
- Windowsにインストールするのでwindows-amd64.msiをインストール。なお、インストール後はPCの再起動が必要
- 終わったらcommand promptに`go version`。Go言語のバージョンが表示されれば完了。

## VSCodeの拡張機能
- 拡張機能からGoで検索してGo Team at Google (go.dev)のGoをインストール。
- Ctrl+Shift+Pを押してGO: Install/Update toolsを選択して全てにチェックを入れてOKをクリック。
- しばらくすると完了

## Hello World
- まずはフォルダーを作成して`go mod init プロジェクト名`を実行。すると go.modというファイルができる
- go.modはGoモジュールの依存関係を管理するファイル。https://go.dev/ref/mod   
  - 要するにNode.jsのpackage.jsonやPHP composer.jsonのような
- 次のgoファイルを作成
```
package main

import "fmt"

func main() {
	fmt.Printf("Hello World\n")
}
```
- F5キーをクリックすると実行されデバッグコンソールにHello Worldと表示される。
  
