---
aliases:
  - AIサービスのAPI利用に関して
title: Regarding the use of APIs for AI services
---
OpenAIとClaudeのAPIを利用する際の主な特徴と手順を以下にまとめます。

## OpenAI API

1. アカウント登録: OpenAIのウェブサイトでアカウントを作成します[4]。

2. APIキーの取得: 開発者ダッシュボードからAPIキーを生成します[1]。

3. 支払い方法の登録: APIを利用するには有料プランへの登録が必要です[4]。

4. モデルの選択: プロジェクトに適したモデル（例：GPT-4、DALL·E）を選びます[1]。

5. 実装:
   ```python
   import openai
   openai.api_key = 'YOUR_API_KEY'
   response = openai.ChatCompletion.create(
     model="gpt-3.5-turbo",
     messages=[{"role": "user", "content": "こんにちは"}]
   )
   ```

## Claude API

1. Anthropicにサインアップ: Anthropicの開発者向けページでアカウントを作成します[2][3]。

2. APIキーの取得: ダッシュボードから「Create Key」をクリックしてAPIキーを生成します[3]。

3. ライブラリのインストール: 
   ```bash
   pip install anthropic
   ```

4. 実装:
   ```python
   import anthropic
   client = anthropic.Anthropic(api_key="YOUR_API_KEY")
   message = client.messages.create(
     model="claude-3-haiku-20240307",
     max_tokens=100,
     messages=[{"role": "user", "content": "こんにちは"}]
   )
   print(message.content)
   ```

両APIとも、高度な自然言語処理機能を提供しますが、インターフェースや利用可能なモデルが異なります[6]。APIの選択は、プロジェクトの要件や予算に応じて行うことが重要です。

Citations:
[1] https://book.st-hakky.com/data-science/chatgpt-api-for-businessperson/
[2] https://chatgpt-lab.com/n/n7a179846cc6e
[3] https://notai.jp/librechat/
[4] https://fixel.co.jp/blog/openai-api/
[5] https://qiita.com/nekkoneko/items/a81c121251918f107199
[6] https://tech-blog.abeja.asia/entry/llm-service-interface-diversity-202408
[7] https://gizumo-inc.jp/media/openai-api-with-php/
[8] https://weel.co.jp/media/innovator/claude-api/
[9] https://qiita.com/Isaka-code/items/b50983796636503b44c5
[10] https://apidog.com/jp/blog/claude-3-api-tutorial/

---
- https://www.perplexity.ai/search/aisahisunoapili-yong-niguan-si-drimV5_KRsCbDhg5kqR6nQ
## About Free Tier
Free Tierはない？？

## Note
OpenAIもAnthropicも最初に5ドル以上の課金を求められう。

## Cost Usage URL
- Anthropic: https://console.anthropic.com/settings/cost
- OpenAI: https://platform.openai.com/settings/organization/usage
