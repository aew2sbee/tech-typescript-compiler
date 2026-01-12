# tech-typescript-compiler
TypeScriptのコンパイラについて検証する

## Babel
- JS/TSの構文を別のJSに変換するトランスパイラ
- 将来の構文を古い環境向けに変換できる（互換性）
- プラグイン/プリセットで拡張可能
- 型チェックはしない（TSは型を消すだけ）
- 速度は速めでビルドに組み込みやすい

```bash
# 関数宣言
npx babel src/fn_arrow.ts --out-file dist/babel/fn_arrow.js

```

```bash
# アロー関数
npx babel src/fn_arrow.ts --out-file dist/babel/fn_arrow.js

```

