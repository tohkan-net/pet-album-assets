# pet-album-assets

[pet-album](https://github.com/tohkan-net/pet-album) の app に同梱するが、リポジトリには入れない生成物を release で配る。

いずれも pet-album 側で gitignore されていて、clone 後とリリース CI で取得する。

| release タグ | 中身 | 取得 |
| - | - | - |
| [`mobileclip-s0-v1`](../../releases/tag/mobileclip-s0-v1) | Apple MobileCLIP-S0 の CoreML パッケージ（image encoder / text encoder）。app 本体が同梱するのは image encoder だけで、text encoder は PoC 用 | `task ios:models:fetch` |
| [`sticker-fonts-v1`](../../releases/tag/sticker-fonts-v1) | ステッカー用フォント 20 本（欧文 10 + 和文 10）+ OFL ライセンス 20 本 + manifest | `task ios:fonts:fetch` |

## 生成物の作り方

- **フォント** … pet-album の `scripts/fonts/build.py` が生成する。Google Fonts から commit SHA 固定で取得し、ウェイトを固定して subset する。収録範囲を決めた経緯は pet-album の `docs/engineering/sticker-fonts.md`
- **モデル** … 変換手順は pet-album 側の PoC を参照

## 注意

このリポジトリは 2026-09 に `pet-album-models` から改名した。モデルだけでなくフォントも配るようになったため。GitHub が旧名からリダイレクトするので旧 URL も当面は解決するが、同じ org で `pet-album-models` という名前が再利用されるとリダイレクトは失われる。
