## 使い方

- 画像とかの容量大きなファイルはこちらに配置します
  - CDN代わりとして。赤石の民衆の参照用
- 重いデータはこっちに配置して、1GB制限を回避したい。
- 画像はURL直指定で読もう。
  - こっちもGitHub pages対応だ。
- csvなどは以下コードで読める。

```
//CSVファイルを読み込む関数getCSV()の定義
function getCSV() {
    var req = new XMLHttpRequest();// HTTPでファイルを読み込むためのXMLHttpRrequestオブジェクトを生成
    req.open("get", "https://sokomin.github.io/update/js/monster.csv", true);//アクセスするファイルを指定
    req.send(null);// HTTPリクエストの発行
    // レスポンスが返ってきたらconvertCSVtoArray()を呼ぶ	
    req.onload = function () {
        convertCSVtoArray(req.responseText);// 渡されるのは読み込んだCSVデータ
    }
}
```

- 特にマップはこの方式で読み込みしないとデータ激重なので注意。
- アイテム・スキル・モンスター画像辺りも移植できそう。
- `https://sokomin.github.io/sokomin_repository/db/quest.csv` とかでDLできる。