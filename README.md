# Markdownの編集環境

## pdf生成

```ash
pandoc report.md -o out/report.pdf -d pandoc/config.yaml 
```

## メタデータ

メタデータ内で改行するには、title: に続く形で|を入力し、改行したいところで半角スペース2文字を行末に入力することで改行できる。

```markdown
---
title: |
    title1  
    title2
subtitle: |
    subtitle1  
    subtitle2
author: |
    author1  
    author2  
date: \today
---
```

## pandoc

### markdownのTIPS

#### 改ページ

改ページしたい場所で`\newpage`を書く。`\clearpage`を使うと未出力の画像をすべて出力してから、改行する。

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

#### 図

##### 参照の仕方

画像に`{#fig:tag_name}`と書くことでタグをつけることができる。つけたタグで参照をすることができる。参照は、`[@fig:tag_name]`でできる。

```markdown
![私のアプリ](app.png){#fig:myfig}

[@fig:myfig]は私が作ったアプリの画像です。
```

#### サイズ調整

画像に`{ with=割合 }`と書くことで大きさを指定できる。

```markdown
![私のアプリ](app.png){ width=50% }
```

#### 配置調整

画像を`<div id="fig:tag"></div>`で囲うことで複数の画像をひとまとめにできる。参照は[@fig:tag]でできる。
また、`\hfill`で画像の横の隙間を等間隔にできる。

```markdown
<div id="fig:tag">

![私のアプリ](app.png){#fig:tag_1 width=33% }
![私のアプリ](app.png){#fig:tag_1 width=33% }
![私のアプリ](app.png){#fig:tag_1 width=33% }

![私のアプリ](app.png){#fig:tag_1 width=33% }\hfill
![私のアプリ](app.png){#fig:tag_1 width=33% }\hfill
![私のアプリ](app.png){#fig:tag_1 width=33% }

fig:tagのキャプション
</div>
```

pandocでは`<div>`と`:::`は同等なので以下のようにも書ける。

```markdown
::: {#fig:tag}

![私のアプリ](app.png){#fig:tag_1 width=33% }
![私のアプリ](app.png){#fig:tag_1 width=33% }
![私のアプリ](app.png){#fig:tag_1 width=33% }

![私のアプリ](app.png){#fig:tag_1 width=33% }\hfill
![私のアプリ](app.png){#fig:tag_1 width=33% }\hfill
![私のアプリ](app.png){#fig:tag_1 width=33% }

fig:tagのキャプション
:::
```

divタグを使って下記のように画像を横並びにする(行数1,列数n)場合、それぞれの画像のキャプションとlabelは反映されなので注意。:::にするとなぜか反映される。

```markdown
<div id="fig:tag">

![私のアプリ](app.png){#fig:tag_1 width=50% }
![私のアプリ](app.png){#fig:tag_1 width=50% }

fig:tagのキャプション
</div>
```

#### コードの参照の仕方

`{#lst:tag_name caption="title"}`とコードブロックにつけることでタグとタイトルをつけることができる。参照は、`[@lst:tag_name]`でできる。

```python {#lst:my-code caption="私のコード"}
print(""Hello World)
```

#### 数式

##### 数式の参照

`{#eq:Amdahl}`と数式につけることでタグをつけることができる。参照は、`[@eq:Amdahl]`でできる。

```markdown
$$
\alpha = \frac{1}{(1-P)+\frac{P}{n}}
$${#eq:Amdahl}
```

##### 数式の改行

`aligned`で囲むことで`\\`を使って改行をすることができる。`&`を基準として縦のラインをそろえることができる。

```markdown
$$
\begin{aligned}
x(t + \Delta t) &= x(t) + v(t) \Delta t + O(\Delta t^2)\\
v(t + \Delta t) &= v(t) + a(t) \Delta t + O(\Delta t^2)
\end{aligned}
$${#eq:Taylor-expansion-of-simple-harmonic-motion}
```
