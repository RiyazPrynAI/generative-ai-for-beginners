<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a45c318dc6ebc2604f35b8b829f93af2",
  "translation_date": "2025-05-19T09:44:41+00:00",
  "source_file": "04-prompt-engineering-fundamentals/README.md",
  "language_code": "ja"
}
-->
# プロンプトエンジニアリングの基礎

## はじめに
このモジュールでは、生成AIモデルで効果的なプロンプトを作成するための基本的な概念と技術をカバーします。LLMに対するプロンプトの書き方も重要です。注意深く作成されたプロンプトは、より高品質な応答を得ることができます。しかし、_プロンプト_ や _プロンプトエンジニアリング_ という用語は具体的に何を意味するのでしょうか？LLMに送信するプロンプトの _入力_ をどのように改善すればよいのでしょうか？これらの質問に、この章と次の章で答えていきます。

_生成AI_ は、ユーザーのリクエストに応じて新しいコンテンツ（テキスト、画像、音声、コードなど）を作成することができます。これは、自然言語やコードを使用して訓練されたOpenAIのGPT（"Generative Pre-trained Transformer"）シリーズのような _大規模言語モデル_ を使用して達成されます。

ユーザーは、技術的な専門知識やトレーニングを必要とせずに、チャットのような馴染みのあるパラダイムを使用してこれらのモデルと対話できます。これらのモデルは _プロンプトベース_ であり、ユーザーはテキスト入力（プロンプト）を送信し、AIの応答（補完）を受け取ります。その後、ユーザーは「AIとチャット」しながら、期待に応じた応答が得られるまでプロンプトを洗練することができます。

「プロンプト」は今や生成AIアプリの主要な _プログラミングインターフェース_ となり、モデルに何をするかを指示し、返される応答の品質に影響を与えます。「プロンプトエンジニアリング」は、スケールで一貫した高品質の応答を提供するためのプロンプトの _設計と最適化_ に焦点を当てた急成長中の研究分野です。

## 学習目標

このレッスンでは、プロンプトエンジニアリングとは何か、それがなぜ重要なのか、そして特定のモデルやアプリケーションの目的に対してより効果的なプロンプトを作成する方法を学びます。プロンプトエンジニアリングの基本的な概念とベストプラクティスを理解し、これらの概念を実際の例に適用することができるインタラクティブなJupyterノートブックの「サンドボックス」環境について学びます。

このレッスンの終わりまでに、以下のことができるようになります：

1. プロンプトエンジニアリングとは何か、なぜそれが重要なのかを説明する。
2. プロンプトの構成要素とその使用方法を説明する。
3. プロンプトエンジニアリングのベストプラクティスと技術を学ぶ。
4. 学んだ技術を実際の例に適用し、OpenAIエンドポイントを使用する。

## 主要用語

プロンプトエンジニアリング: AIモデルを望ましい出力に導くための入力の設計と洗練の実践。
トークン化: テキストをモデルが理解し処理できる小さな単位（トークン）に変換するプロセス。
指示調整済みLLM: 特定の指示で精緻化され、応答の精度と関連性を向上させた大規模言語モデル（LLM）。

## 学習サンドボックス

プロンプトエンジニアリングは現在、科学というよりも芸術に近いものです。直感を磨く最良の方法は、_多く練習し_、アプリケーションドメインの専門知識を推奨技術やモデル固有の最適化と組み合わせた試行錯誤のアプローチを採用することです。

このレッスンに付随するJupyterノートブックは、学んだことを試すことができる _サンドボックス_ 環境を提供します。進行中または最後のコードチャレンジの一部としてこれを実行します。演習を実行するには、以下が必要です：

1. **Azure OpenAI APIキー** - デプロイされたLLMのサービスエンドポイント。
2. **Pythonランタイム** - ノートブックを実行するための環境。
3. **ローカル環境変数** - _準備するために[SETUP](./../00-course-setup/SETUP.md?WT.mc_id=academic-105485-koreyst)の手順を今すぐ完了する_。

ノートブックには _スターター_ 演習が含まれていますが、さらに多くの例やアイデアを試すために、自分自身の _Markdown_（説明）や _コード_（プロンプト要求）セクションを追加することをお勧めします。プロンプト設計の直感を磨いてください。

## イラスト付きガイド

このレッスンでカバーする内容を詳しく学ぶ前に、大きな絵を把握したいですか？このイラスト付きガイドをチェックしてください。ここでは、カバーされる主なトピックと、それぞれについて考えるべき重要なポイントを紹介しています。レッスンのロードマップは、基本的な概念と課題を理解し、それに関連するプロンプトエンジニアリングの技術とベストプラクティスで対処する方法を示します。このガイドの「高度な技術」セクションは、このカリキュラムの _次の_ 章でカバーされる内容を指しています。

## 私たちのスタートアップ

では、このトピックがどのようにしてAIイノベーションを教育に提供するという私たちのスタートアップの使命に関連しているかについて話しましょう。私たちは _個別学習_ のAI対応アプリケーションを構築したいと考えています。ですから、私たちのアプリケーションの異なるユーザーがどのようにプロンプトを「設計」するかを考えてみましょう：

- **管理者** は、AIに _カリキュラムデータを分析してカバーのギャップを特定する_ よう依頼するかもしれません。AIは結果を要約したり、コードで可視化したりすることができます。
- **教育者** は、AIに _ターゲットオーディエンスとトピックのためのレッスンプランを生成する_ よう依頼するかもしれません。AIは指定された形式で個別化されたプランを作成できます。
- **学生** は、AIに _難しい科目を教えてもらう_ よう依頼するかもしれません。AIは、彼らのレベルに合わせたレッスン、ヒント、例を提供して学生を指導できます。

これはほんの一例に過ぎません。[教育用プロンプト](https://github.com/microsoft/prompts-for-edu/tree/main?WT.mc_id=academic-105485-koreyst) をチェックしてください。教育の専門家がキュレーションしたオープンソースのプロンプトライブラリで、可能性の広がりを感じることができます！サンドボックスでそれらのプロンプトをいくつか実行したり、OpenAI Playgroundを使ってみて、何が起こるか見てみましょう！

## プロンプトエンジニアリングとは？

このレッスンでは、**プロンプトエンジニアリング** を、特定のアプリケーションの目的とモデルに対して一貫性のある高品質な応答（補完）を提供するために、テキスト入力（プロンプト）を _設計し最適化する_ プロセスとして定義しました。これを2ステップのプロセスとして考えることができます：

- 特定のモデルと目的に対する初期プロンプトの _設計_
- 応答の品質を向上させるためのプロンプトの _反復的な洗練_

これは必然的に試行錯誤のプロセスであり、最適な結果を得るためにはユーザーの直感と努力が必要です。それでは、なぜこれが重要なのでしょうか？この質問に答えるためには、まず3つの概念を理解する必要があります：

- _トークン化_ = モデルがプロンプトをどのように「見る」か
- _ベースLLM_ = 基礎モデルがプロンプトをどのように「処理」するか
- _指示調整済みLLM_ = モデルが「タスク」をどのように見ることができるか

### トークン化

LLMはプロンプトを _トークンのシーケンス_ として認識します。異なるモデル（またはモデルのバージョン）は、同じプロンプトを異なる方法でトークン化することがあります。LLMはトークンで訓練されているため（生のテキストではなく）、プロンプトがどのようにトークン化されるかは、生成された応答の品質に直接影響を与えます。

トークン化の仕組みを直感的に理解するには、[OpenAI Tokenizer](https://platform.openai.com/tokenizer?WT.mc_id=academic-105485-koreyst) のようなツールを試してみてください。プロンプトをコピーしてトークンに変換される様子を見て、空白文字や句読点がどのように扱われるかに注目してください。この例は古いLLM（GPT-3）を示していますので、新しいモデルで試すと異なる結果が得られるかもしれません。

### 概念: 基礎モデル

プロンプトがトークン化されると、「ベースLLM」（または基礎モデル）の主な機能は、そのシーケンス内の次のトークンを予測することです。LLMは大量のテキストデータセットで訓練されているため、トークン間の統計的関係をよく把握しており、ある程度の自信を持ってその予測を行うことができます。ただし、プロンプトやトークン内の単語の _意味_ を理解しているわけではなく、次の予測で「完了」できるパターンを見ているだけです。ユーザーの介入や事前に設定された条件によって終了されるまで、シーケンスを予測し続けることができます。

プロンプトベースの補完がどのように機能するかを見たいですか？上記のプロンプトをAzure OpenAI Studioの [_Chat Playground_](https://oai.azure.com/playground?WT.mc_id=academic-105485-koreyst) にデフォルト設定で入力してください。システムはプロンプトを情報の要求として扱うように設定されているため、このコンテキストを満たす補完が表示されるはずです。

しかし、ユーザーが特定の基準やタスクの目的に合ったものを見たい場合はどうでしょうか？ここで、_指示調整済み_ LLMが登場します。

### 概念: 指示調整済みLLM

[指示調整済みLLM](https://blog.gopenai.com/an-introduction-to-base-and-instruction-tuned-large-language-models-8de102c785a6?WT.mc_id=academic-105485-koreyst) は、基礎モデルから始まり、明確な指示を含む例や入力/出力ペア（例えば、マルチターンの「メッセージ」）で精緻化され、AIの応答がその指示に従おうとします。

これは、強化学習と人間のフィードバック（RLHF）のような技術を使用して、モデルが _指示に従う_ と _フィードバックから学ぶ_ ことを訓練し、実用的なアプリケーションにより適した応答を生成し、ユーザーの目的に関連するものにします。

試してみましょう - 上記のプロンプトに戻り、今度は _システムメッセージ_ を次の指示としてコンテキストを提供してください：

> _提供された内容を2年生の学生向けに要約してください。結果を1段落にまとめ、3〜5の箇条書きで示してください。_

結果が希望する目標と形式を反映するように調整されていることがわかりますか？教育者は今、この応答をクラスのスライドに直接使用できます。

## なぜプロンプトエンジニアリングが必要なのか？

プロンプトがLLMによってどのように処理されるかを理解したので、なぜプロンプトエンジニアリングが必要なのかについて話しましょう。その答えは、現在のLLMが _信頼性のある一貫した補完_ を達成するのが難しいという課題をいくつか抱えているため、プロンプトの構築と最適化に努力を注ぐ必要があるからです。例えば：

1. **モデルの応答は確率的です。** _同じプロンプト_ でも、異なるモデルやモデルのバージョンで異なる応答が生成される可能性があります。また、_同じモデル_ でも異なる時間に異なる結果を生成することがあります。_プロンプトエンジニアリング技術は、より良いガードレールを提供することでこれらの変動を最小限に抑えるのに役立ちます_。

1. **モデルは応答を捏造することがあります。** モデルは _大規模だが有限の_ データセットで事前に訓練されているため、そのトレーニング範囲外の概念についての知識が欠けています。その結果、事実と矛盾する不正確な、架空の、または直接的に矛盾する補完を生成することがあります。_プロンプトエンジニアリング技術は、AIに引用や推論を求めるなど、ユーザーがそのような捏造を特定し、軽減するのに役立ちます_。

1. **モデルの能力は異なります。** 新しいモデルやモデルの世代は、より豊富な能力を持つことがありますが、コストや複雑さのトレードオフもあります。_プロンプトエンジニアリングは、違いを抽象化し、モデル固有の要件に適応するベストプラクティスやワークフローを開発するのに役立ちます_。

OpenAIやAzure OpenAI Playgroundでこれを実際に見てみましょう：

- 同じプロンプトを異なるLLMデプロイメント（例：OpenAI、Azure OpenAI、Hugging Face）で使用してみてください - 変動が見られましたか？
- 同じプロンプトを _同じ_ LLMデプロイメント（例：Azure OpenAI Playground）で繰り返し使用してみてください - これらの変動はどのように異なりましたか？

### 捏造の例

このコースでは、LLMがトレーニングの制約や他の制約のために事実と異なる情報を生成する現象を **「捏造」** と呼んでいます。これを _「幻覚」_ として説明している一般的な記事や研究論文を目にしたことがあるかもしれません。しかし、_「捏造」_ という用語を使用することを強くお勧めします。これにより、機械駆動の結果に人間のような特性を帰属させることで、その行動を擬人化しないようにします。これは、用語の観点からも[責任あるAIガイドライン](https://www.microsoft.com/ai/responsible-ai?WT.mc_id=academic-105485-koreyst)を強化し、一部のコンテキストでは攻撃的または非包括的と見なされる可能性のある用語を排除します。

捏造がどのように機能するかを感じたいですか？トレーニングデータセットに含まれていない架空のトピックのコンテンツを生成するようAIに指示するプロンプトを考えてみてください。例えば、私は次のプロンプトを試しました：

> **プロンプト:** 2076年の火星戦争についてのレッスンプランを生成してください。

ウェブ検索では、火星戦争に関する架空の話（例：テレビシリーズや本）がありましたが、2076年のものはありませんでした。常識的に考えても、2076年は _未来_ であり、実際のイベントと関連付けら
テンプレートの本当の価値は、特定のアプリケーション領域に対して_プロンプトライブラリ_を作成し公開する能力にあります。ここでは、プロンプトテンプレートがアプリケーション固有のコンテキストや例を反映するように_最適化_され、対象のユーザーにとってより関連性が高く正確な応答を提供します。[Prompts For Edu](https://github.com/microsoft/prompts-for-edu?WT.mc_id=academic-105485-koreyst) リポジトリは、このアプローチの優れた例であり、教育分野に特化したプロンプトライブラリを作成し、授業計画、カリキュラム設計、学生指導などの重要な目的に重点を置いています。

## サポートコンテンツ

プロンプト構築を指示（タスク）とターゲット（主要コンテンツ）として考えると、_二次コンテンツ_は出力に何らかの影響を与えるために提供する追加のコンテキストのようなものです。これには、パラメータの調整、フォーマットの指示、トピックの分類などが含まれ、モデルがユーザーの目的や期待に合わせて応答を_調整_するのを助けることができます。

例えば、カリキュラムにあるすべてのコースに関する詳細なメタデータ（名前、説明、レベル、メタデータタグ、講師など）があるコースカタログを考えてみましょう：

- 「2023年秋のコースカタログを要約する」という指示を定義できます。
- 望ましい出力の例をいくつか提供するために主要コンテンツを使用できます。
- 興味のあるトップ5の「タグ」を特定するために二次コンテンツを使用できます。

これにより、モデルは数例で示されたフォーマットで要約を提供できますが、結果に複数のタグがある場合は、二次コンテンツで特定された5つのタグを優先できます。

---

<!--
レッスンテンプレート：
このユニットはコアコンセプト#1をカバーする必要があります。
概念を例や参考文献で強化します。

コンセプト#3：
プロンプトエンジニアリング技術。
プロンプトエンジニアリングの基本技術は何ですか？
いくつかの演習で説明してください。
-->

## プロンプトのベストプラクティス

プロンプトがどのように_構築_されるかを理解した今、ベストプラクティスを反映するようにそれらを_設計_する方法を考え始めることができます。これを2つの部分で考えることができます。正しい_マインドセット_を持ち、正しい_技術_を適用することです。

### プロンプトエンジニアリングのマインドセット

プロンプトエンジニアリングは試行錯誤のプロセスなので、3つの広範な指針を心に留めてください：

1. **ドメイン理解が重要です。** 応答の正確性と関連性は、そのアプリケーションやユーザーが操作する_ドメイン_の関数です。直感とドメイン専門知識を適用して技術をさらに_カスタマイズ_します。例えば、システムプロンプトで_ドメイン固有のパーソナリティ_を定義したり、ユーザープロンプトで_ドメイン固有のテンプレート_を使用したりします。ドメイン固有のコンテキストを反映する二次コンテンツを提供したり、モデルを馴染みのある使用パターンに導くための_ドメイン固有の手がかりと例_を使用します。

2. **モデル理解が重要です。** モデルは本質的に確率的であることを知っています。しかし、モデルの実装は、使用するトレーニングデータセット（事前学習知識）、提供する機能（例：APIやSDKを介して）、最適化されているコンテンツの種類（例：コード、画像、テキスト）に応じて異なることがあります。使用するモデルの強みと限界を理解し、その知識を使用して_タスクを優先_したり、モデルの能力に最適化された_カスタマイズされたテンプレート_を構築します。

3. **反復と検証が重要です。** モデルは急速に進化しており、プロンプトエンジニアリングの技術も同様です。ドメイン専門家として、あなたの特定のアプリケーションに適用される他のコンテキストや基準があるかもしれません。それが広範なコミュニティには適用されない場合があります。プロンプトエンジニアリングツールと技術を使用してプロンプト構築を「ジャンプスタート」し、次に自分の直感とドメイン専門知識を使用して結果を反復し検証します。洞察を記録し、他の人が将来より速く反復できるようにするための新しい基準として使用できる_知識ベース_（例：プロンプトライブラリ）を作成します。

## ベストプラクティス

次に、[OpenAI](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api?WT.mc_id=academic-105485-koreyst)と[Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/concepts/prompt-engineering#best-practices?WT.mc_id=academic-105485-koreyst)の実践者が推奨する一般的なベストプラクティスを見てみましょう。

| 内容                             | 理由                                                                                                                                                                                                                                          |
| :------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 最新のモデルを評価する           | 新しいモデル世代は改善された機能と品質を持っている可能性が高いですが、より高いコストが発生する可能性もあります。それらの影響を評価し、移行の決定を行います。                                                                                                           |
| 指示とコンテキストを分離する     | モデル/プロバイダーが指示、主要コンテンツ、二次コンテンツをより明確に区別するための_区切り記号_を定義しているか確認してください。これにより、モデルがトークンに対してより正確に重みを割り当てるのを助けることができます。                                            |
| 明確に具体的にする               | 望ましいコンテキスト、結果、長さ、フォーマット、スタイルなどの詳細を提供します。これにより、応答の品質と一貫性が向上します。再利用可能なテンプレートでレシピをキャプチャします。                                                                                         |
| 説明的で、例を使用する           | モデルは「ショー＆テル」アプローチにより良く反応する可能性があります。 `zero-shot` approach where you give it an instruction (but no examples) then try `few-shot` as a refinement, providing a few examples of the desired output. Use analogies. |
| Use cues to jumpstart completions | Nudge it towards a desired outcome by giving it some leading words or phrases that it can use as a starting point for the response.                                                                                                               |
| Double Down                       | Sometimes you may need to repeat yourself to the model. Give instructions before and after your primary content, use an instruction and a cue, etc. Iterate & validate to see what works.                                                         |
| Order Matters                     | The order in which you present information to the model may impact the output, even in the learning examples, thanks to recency bias. Try different options to see what works best.                                                               |
| Give the model an “out”           | Give the model a _fallback_ completion response it can provide if it cannot complete the task for any reason. This can reduce chances of models generating false or fabricated responses.                                                         |
|                                   |                                                                                                                                                                                                                                                   |

As with any best practice, remember that _your mileage may vary_ based on the model, the task and the domain. Use these as a starting point, and iterate to find what works best for you. Constantly re-evaluate your prompt engineering process as new models and tools become available, with a focus on process scalability and response quality.

<!--
LESSON TEMPLATE:
This unit should provide a code challenge if applicable

CHALLENGE:
Link to a Jupyter Notebook with only the code comments in the instructions (code sections are empty).

SOLUTION:
Link to a copy of that Notebook with the prompts filled in and run, showing what one example could be.
-->

## Assignment

Congratulations! You made it to the end of the lesson! It's time to put some of those concepts and techniques to the test with real examples!

For our assignment, we'll be using a Jupyter Notebook with exercises you can complete interactively. You can also extend the Notebook with your own Markdown and Code cells to explore ideas and techniques on your own.

### To get started, fork the repo, then

- (Recommended) Launch GitHub Codespaces
- (Alternatively) Clone the repo to your local device and use it with Docker Desktop
- (Alternatively) Open the Notebook with your preferred Notebook runtime environment.

### Next, configure your environment variables

- Copy the `.env.copy` file in repo root to `.env` and fill in the `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT` and `AZURE_OPENAI_DEPLOYMENT` の値から始めます。[学習サンドボックスセクション](../../../04-prompt-engineering-fundamentals/04-prompt-engineering-fundamentals)に戻って学びましょう。

### 次に、Jupyter Notebookを開きます

- ランタイムカーネルを選択します。オプション1または2を使用する場合は、開発コンテナによって提供されるデフォルトのPython 3.10.xカーネルを選択するだけです。

これで演習を実行する準備が整いました。ここには正解も誤答もありません。試行錯誤によるオプションの探求と、特定のモデルやアプリケーション領域で何がうまくいくかの直感を構築するだけです。

_この理由から、このレッスンにはコードソリューションセグメントはありません。代わりに、ノートブックには「私の解決策：」というタイトルのMarkdownセルがあり、参考用に1つの例の出力を示しています。_

 <!--
レッスンテンプレート：
セクションを要約と自己学習のためのリソースでまとめます。
-->

## 知識チェック

以下のうち、いくつかの合理的なベストプラクティスに従った良いプロンプトはどれですか？

1. 赤い車の画像を見せてください
2. 崖の近くに駐車され、夕日が沈むVolvo製XC90モデルの赤い車の画像を見せてください
3. Volvo製XC90モデルの赤い車の画像を見せてください

A: 2、それは「何」を提供し、具体的な詳細に入る最良のプロンプトです（単なる車ではなく特定のメーカーとモデル）、そして全体の設定も説明しています。次に良いのは3で、多くの説明を含んでいます。

## 🚀 チャレンジ

プロンプト「Volvo製の赤い車の画像を見せてください」の文章を完成させる際に「手がかり」技術を活用できるかどうか確認してください。それはどのように応答し、それをどのように改善しますか？

## 素晴らしい仕事！学びを続けましょう

異なるプロンプトエンジニアリングの概念についてもっと学びたいですか？このトピックに関する他の優れたリソースを見つけるために[学習継続ページ](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst)にアクセスしてください。

レッスン5に進み、[高度なプロンプト技術](../05-advanced-prompts/README.md?WT.mc_id=academic-105485-koreyst)を見てみましょう！

**免責事項**:  
この文書はAI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されています。正確性を期しておりますが、自動翻訳には誤りや不正確さが含まれる可能性があることをご了承ください。原文の言語で書かれた文書が権威ある情報源とみなされるべきです。重要な情報については、専門の人間による翻訳をお勧めします。この翻訳の使用に起因する誤解や誤訳について、当社は一切の責任を負いません。