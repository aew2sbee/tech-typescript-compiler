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

## tsc (TypeScript Compiler)
- TypeScript公式のコンパイラ
- 型チェックを行い、型エラーがあればコンパイルに失敗する
- JSへ変換しつつ型情報は取り除かれる
- `target`/`module`/`lib`などで出力仕様を調整可能
- プロジェクトでは`tsconfig.json`で設定を一括管理できる

```bash
# 関数宣言
tsc src/fn_declaration.ts --outDir dist/tsc

```

```bash
# アロー関数
tsc src/fn_arrow.ts --outDir dist/tsc

```

## SWC
- Rust製の高速トランスパイラ/コンパイラ
- TypeScriptの型チェックは行わず、型情報は取り除かれる
- Babel互換の設定に加えて、独自の高速最適化が可能
- `@swc/cli`と`@swc/core`で利用するのが一般的

```bash
# 関数宣言
npx swc src/fn_declaration.ts -o dist/SWC/fn_declaration.js

```

```bash
# アロー関数
npx swc src/fn_arrow.ts -o dist/SWC/fn_arrow.js

```

## esbuild
- Go製の超高速ビルドツール/バンドラ
- TypeScriptの型チェックは行わず、型情報は取り除かれる
- バンドル/ミニファイ/ツリーシェイキングまで一括で可能
- `esbuild`のCLIで単体ファイルの変換もできる

```bash
# 関数宣言
npx esbuild src/fn_declaration.ts --outfile=dist/esbuild/fn_declaration.js

```

```bash
# アロー関数
npx esbuild src/fn_arrow.ts --outfile=dist/esbuild/fn_arrow.js

```