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

## markdownのTIPS

### 特定の場所で改ページ

改ページしたい場所で`\newpage`を書く。
