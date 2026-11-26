# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->


- STEP 1のツールの名前: glossary_search_glossary
- STEP 2の[tool call]:
  glossary_search_glossary({'query': '3レベル'})
- STEP 3の[tool call]:
  fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- STEP 4の[tool call]:
  aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要'})
  aws_aws___search_documentation({'search_phrase': '"Using versioning" Amazon S3 overview'})

- 気づき・疑問：
  - MCPサーバーを追加すると、エージェントが利用できるツールが増えることが分かった。
  - glossaryはローカルのコマンド、fetchはuvx、AWSはURL接続というように、MCPサーバーの起動方法が異なっていた。
  - --traceを付けると、モデルがどのツールをどの引数で呼び出したか確認できて便利だった。
  - AWSの検索では、1回目の検索結果を受けて、モデルが別の検索語でもう一度検索していた。ツールを1回だけ呼ぶとは限らないことに気づいた。
  - 疑問：MCPサーバーを増やしすぎた場合、ツールの選択や回答の正確さにどのような影響があるのか知りたい。

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

## 宿題

- 取り組んだレベル：基礎
- やったこと：
  `app/mcp_server.py` に `get_lecture_summary` ツールを追加し、
  「第2回では何を学びますか？」という質問を実行した。
- 結果：
  `glossary_get_lecture_summary` が呼び出され、
  第2回の内容としてファインチューニングとLoRAについて回答された。
- 気づき・疑問：
  ツールを追加すると、質問内容に応じてエージェントがそのツールを選んで呼び出すことが分かった。
  `--trace` を使うと、ツールの呼び出しと返り値を確認できた。