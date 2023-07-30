---
theme: default
class: lead
size: 16:9
paginate: true
backgroundColor: #fff
color: white
---

# The Presentation about NixOS by haruki7049

EN:haruki7049
JP:はるき

![bg](./nix-wallpaper-recursive.png)

---
<!--
color: black
-->

# About me...

だいたいこんなかんじ。ふんいきでよんで

```rust
#[allow(dead_code)]
pub struct AboutHaruki7049 {
    name: String,
    age: u32,
    hobby: String,
    not_good_at: String,
}

impl AboutHaruki7049 {
    pub fn new() -> AboutHaruki7049 {
        AboutHaruki7049 {
            name: "haruki7049".to_string(),
            age: 17,
            hobby: "Installing the OS".to_string(),
            not_good_at: "Kanji".to_string(),
        }
    }
}
```

---

# What is the NixOS?

関数型言語である、Nixという言語を用いているパッケージマネージャー（汎用性があるらしくて、パッケージマネージャーなのかも疑問、かつ不明）を使ったOS。しかし、実際にはパッケージや設定を宣言して設定しているために、関数型と言えるのか疑問の余地あり。単純に自分の知識がないだけかもしれへん。

---

## What is the Nix?????

こんなコードを求められる言語。

```nix
let
  pkgs = import <nixpkgs> {};
in
  pkgs.mkShell {
    packages = with pkgs; [
      cargo
      rustc
      rustfmt
      rust-analyzer
    ];
  }
```

---

## ここでmkShellに気づく

シェルを作るとは？

---

## このプロジェクトのディレクトリ構造の確認

```
|-- shell.nix
|-- Cargo.toml
|-- Cargo.lock
|-- src
    |-- main.rs

省略
```

---

# そう、mkShellとは！！！

---

# 環境を汚さずにプログラミングをする環境を作れる！！

先ほど書いた程度なら、  
nix-shell -p cargo rustc rustfmt rust-analyzer
