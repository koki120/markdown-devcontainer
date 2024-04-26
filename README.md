# Markdownの編集環境

## pdf生成

```ash
pandoc report.md -o out/report.pdf -d pandoc/config.yaml 
```

## メタデータ

メタデータ内で改行するには、title: に続く形で|を入力し、改行したいところで半角スペース2文字を行末に入力することで改行できる。

```yaml
title: |
    title1  
    title2
author: |
    author1  
    author2  
date: \today
```

## pandoc

### markdownのTIPS

#### 特定の場所で改ページ

改ページしたい場所で`\newpage`を書く。

#### 表の参照の仕方

表の下に`:title_name {#tbl:tag_name}`と書くことで表にタイトルとタグをつけることができる。title_nameとtag_nameの間に空白が必要なので気を付けること。つけたタグで参照をすることができる。参照は、`[@tbl:tag_name]`でできる。

```markdown
|   i | サイコロの目 |
| --: | :----------: |
|   1 |      3       |
|   2 |      2       |
|   3 |      6       |
|   4 |      5       |
|   5 |      1       |
|   6 |      4       |
|   7 |      2       |
|   8 |      6       |

:私の表 {#tbl:mytable}

[@tbl:mytable]はサイコロの出た目の結果です。
```

#### 図の参照の仕方

画像に`{#fig:tag_name}`と書くことでタグをつけることができる。つけたタグで参照をすることができる。参照は、`[@tbl:tag_name]`でできる。

```markdown
![私のアプリ](app.png){#fig:myfig}

[@fig:myfig]は私が作ったアプリの画像です。
```

#### コードの参照の仕方

`{#lst:tag_name caption="title"}`とコードブロックにつけることでタグとタイトルをつけることができる。参照は、`[@lst:tag_name]`でできる。

```python {#lst:my-code caption="私のコード"}
print(""Hello World)
```
