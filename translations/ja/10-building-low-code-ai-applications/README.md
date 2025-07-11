<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f5ff3b6204a695a117d6f452403c95f7",
  "translation_date": "2025-05-19T19:53:17+00:00",
  "source_file": "10-building-low-code-ai-applications/README.md",
  "language_code": "ja"
}
-->
# ローコードAIアプリケーションの構築

## はじめに

画像生成アプリケーションの構築方法を学んだ今、ローコードについて話しましょう。生成AIはローコードを含むさまざまな分野で使用できますが、ローコードとは何で、どのようにAIを組み込むことができるのでしょうか？

ローコード開発プラットフォームの利用により、伝統的な開発者や非開発者がアプリやソリューションを簡単に構築できるようになりました。ローコード開発プラットフォームは、少しのコードまたはコードなしでアプリやソリューションを構築できる環境を提供します。これは、コンポーネントをドラッグ＆ドロップすることでアプリやソリューションを構築するビジュアル開発環境を提供することで実現されます。これにより、より速く、より少ないリソースでアプリやソリューションを構築することができます。このレッスンでは、ローコードの使用方法と、Power Platformを使用してAIを活用したローコード開発の向上方法について詳しく説明します。

Power Platformは、直感的なローコードまたはノーコード環境を通じて、組織がチームに独自のソリューションを構築する力を与える機会を提供します。この環境は、ソリューションの構築プロセスを簡素化するのに役立ちます。Power Platformを使用すると、ソリューションは数ヶ月または数年ではなく、数日または数週間で構築できます。Power Platformは、Power Apps、Power Automate、Power BI、Power Pages、Copilot Studioの5つの主要な製品で構成されています。

このレッスンでは次のことをカバーします：

- Power Platformにおける生成AIの概要
- Copilotの紹介とその使い方
- Power Platformでアプリとフローを構築するための生成AIの使用
- AI Builderを使用したPower PlatformのAIモデルの理解

## 学習目標

このレッスンの終わりまでに、以下のことができるようになります：

- Power PlatformでのCopilotの動作を理解する。

- 教育スタートアップのための学生課題追跡アプリを構築する。

- 請求書から情報を抽出するためにAIを使用する請求書処理フローを構築する。

- GPT AIモデルを使用してテキストを作成する際のベストプラクティスを適用する。

このレッスンで使用するツールと技術は次のとおりです：

- **Power Apps**：学生課題追跡アプリ用で、データを追跡、管理、対話するためのアプリを構築するためのローコード開発環境を提供します。

- **Dataverse**：学生課題追跡アプリのデータを保存するためのもので、アプリのデータを保存するためのローコードデータプラットフォームを提供します。

- **Power Automate**：請求書処理フロー用で、請求書処理プロセスを自動化するためのワークフローを構築するためのローコード開発環境を提供します。

- **AI Builder**：請求書処理AIモデル用で、スタートアップの請求書を処理するための事前構築AIモデルを使用します。

## Power Platformにおける生成AI

ローコード開発とアプリケーションを生成AIで強化することは、Power Platformの重要な焦点領域です。目標は、データサイエンスの専門知識を必要とせずに、誰もがAIを活用したアプリ、サイト、ダッシュボードを構築し、AIでプロセスを自動化できるようにすることです。この目標は、Power Platformのローコード開発体験にCopilotとAI Builderの形で生成AIを統合することで達成されます。

### どのように機能するのか？

Copilotは、自然言語を使用した一連の会話ステップで要件を説明することで、Power Platformソリューションを構築するAIアシスタントです。例えば、アプリで使用するフィールドを指示すると、アプリと基礎となるデータモデルの両方を作成したり、Power Automateでのフローの設定方法を指定したりできます。

Copilot駆動の機能をアプリ画面の機能として使用して、ユーザーが会話を通じて洞察を得ることを可能にすることができます。

AI Builderは、Power Platformで利用可能なローコードAI機能で、プロセスを自動化し、結果を予測するためにAIモデルを使用することができます。AI Builderを使用すると、DataverseまたはSharePoint、OneDrive、Azureなどのさまざまなクラウドデータソースに接続するアプリやフローにAIをもたらすことができます。

Copilotは、Power Platformのすべての製品（Power Apps、Power Automate、Power BI、Power Pages、Power Virtual Agents）で利用可能です。AI Builderは、Power AppsとPower Automateで利用可能です。このレッスンでは、Power AppsとPower AutomateでCopilotとAI Builderを使用して教育スタートアップのソリューションを構築する方法に焦点を当てます。

### Power AppsにおけるCopilot

Power Platformの一部として、Power Appsはデータを追跡、管理、対話するためのアプリを構築するためのローコード開発環境を提供します。これは、スケーラブルなデータプラットフォームとクラウドサービスやオンプレミスデータへの接続能力を備えたアプリ開発サービスのスイートです。Power Appsを使用すると、ブラウザ、タブレット、電話で動作し、同僚と共有できるアプリを構築できます。Power Appsはシンプルなインターフェースでユーザーをアプリ開発に誘導し、すべてのビジネスユーザーやプロ開発者がカスタムアプリを構築できるようにします。アプリ開発体験は、Copilotを通じて生成AIでさらに向上します。

Power AppsのCopilot AIアシスタント機能により、必要なアプリの種類や追跡、収集、表示したい情報を説明できます。Copilotは、説明に基づいて応答性のあるキャンバスアプリを生成します。その後、アプリをカスタマイズしてニーズに合わせることができます。AI Copilotは、追跡したいデータを保存するために必要なフィールドを持つDataverseテーブルとサンプルデータを生成し提案します。このレッスンの後半でDataverseとは何か、Power Appsでの使用方法について見ていきます。会話ステップを通じてAI Copilotアシスタント機能を使用して、ニーズに合わせてテーブルをカスタマイズできます。この機能はPower Appsのホーム画面から簡単に利用できます。

### Power AutomateにおけるCopilot

Power Platformの一部として、Power Automateはアプリケーションとサービス間で自動化されたワークフローを作成することを可能にします。これは、コミュニケーション、データ収集、意思決定承認などの繰り返しビジネスプロセスを自動化するのに役立ちます。そのシンプルなインターフェースにより、初心者から経験豊富な開発者まで、すべての技術的能力を持つユーザーが作業タスクを自動化できます。ワークフロー開発体験は、Copilotを通じて生成AIでさらに向上します。

Power AutomateのCopilot AIアシスタント機能により、必要なフローの種類やフローに実行させたいアクションを説明できます。Copilotは、説明に基づいてフローを生成します。その後、フローをカスタマイズしてニーズに合わせることができます。AI Copilotは、自動化したいタスクを実行するために必要なアクションも生成し提案します。このレッスンの後半でフローとは何か、Power Automateでの使用方法について見ていきます。会話ステップを通じてAI Copilotアシスタント機能を使用して、ニーズに合わせてアクションをカスタマイズできます。この機能はPower Automateのホーム画面から簡単に利用できます。

## 課題: Copilotを使用してスタートアップの学生課題と請求書を管理する

私たちのスタートアップは、学生にオンラインコースを提供しています。スタートアップは急速に成長しており、コースの需要に対応するのが難しくなっています。スタートアップは、学生の課題と請求書を管理するためのローコードソリューションを構築するために、あなたをPower Platform開発者として雇いました。彼らのソリューションは、アプリを通じて学生の課題を追跡し管理し、ワークフローを通じて請求書処理プロセスを自動化するのに役立つべきです。あなたは、生成AIを使用してソリューションを開発するよう求められました。

Copilotの使用を開始する際には、[Power Platform Copilot Prompt Library](https://github.com/pnp/powerplatform-prompts?WT.mc_id=academic-109639-somelezediko)を使用してプロンプトを開始できます。このライブラリには、Copilotを使用してアプリやフローを構築するために使用できるプロンプトのリストが含まれています。また、ライブラリのプロンプトを使用して、Copilotに要件を説明する方法のアイデアを得ることができます。

### スタートアップのための学生課題追跡アプリを構築する

私たちのスタートアップの教育者たちは、学生の課題を追跡するのに苦労しています。彼らはスプレッドシートを使用して課題を追跡していましたが、学生の数が増えるにつれて管理が難しくなってきました。彼らは、課題を追跡し管理するのに役立つアプリを構築するように求めています。アプリは、新しい課題を追加し、課題を表示し、課題を更新し、課題を削除することを可能にするべきです。また、教育者と学生が評価済みの課題と未評価の課題を表示することを可能にするべきです。

以下の手順に従って、Power AppsのCopilotを使用してアプリを構築します：

1. [Power Apps](https://make.powerapps.com?WT.mc_id=academic-105485-koreyst)のホーム画面に移動します。

1. ホーム画面のテキストエリアを使用して、構築したいアプリを説明します。例えば、**_学生の課題を追跡し管理するアプリを構築したい_**と入力します。**送信**ボタンをクリックしてプロンプトをAI Copilotに送信します。

1. AI Copilotは、追跡したいデータを保存するために必要なフィールドとサンプルデータを含むDataverseテーブルを提案します。その後、会話ステップを通じてAI Copilotアシスタント機能を使用してテーブルをカスタマイズできます。

   > **重要**: Dataverseは、Power Platformの基盤となるデータプラットフォームです。アプリのデータを保存するためのローコードデータプラットフォームです。Microsoft Cloud内でデータを安全に保存する完全に管理されたサービスであり、Power Platform環境内でプロビジョニングされます。データ分類、データ系統、きめ細かなアクセス制御などの組み込みデータガバナンス機能を備えています。Dataverseについての詳細は[こちら](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro?WT.mc_id=academic-109639-somelezediko)をご覧ください。

1. 教育者たちは、課題を提出した学生に進捗状況を更新するためのメールを送りたいと考えています。Copilotを使用して、学生のメールを保存するための新しいフィールドをテーブルに追加できます。例えば、次のプロンプトを使用して新しいフィールドをテーブルに追加します：**_学生のメールを保存する列を追加したい_**。**送信**ボタンをクリックしてプロンプトをAI Copilotに送信します。

1. AI Copilotは新しいフィールドを生成し、その後ニーズに合わせてフィールドをカスタマイズできます。

1. テーブルが完了したら、**アプリを作成**ボタンをクリックしてアプリを作成します。

1. AI Copilotは、説明に基づいて応答性のあるキャンバスアプリを生成します。その後、アプリをカスタマイズしてニーズに合わせることができます。

1. 教育者が学生にメールを送信するために、アプリに新しい画面を追加するためにCopilotを使用できます。例えば、次のプロンプトを使用してアプリに新しい画面を追加します：**_学生にメールを送信する画面を追加したい_**。**送信**ボタンをクリックしてプロンプトをAI Copilotに送信します。

1. AI Copilotは新しい画面を生成し、その後ニーズに合わせて画面をカスタマイズできます。

1. アプリが完了したら、**保存**ボタンをクリックしてアプリを保存します。

1. アプリを教育者と共有するには、**共有**ボタンをクリックし、もう一度**共有**ボタンをクリックします。その後、教育者のメールアドレスを入力してアプリを共有できます。

> **宿題**: あなたが構築したアプリは良いスタートですが、改善の余地があります。メール機能では、教育者は手動で学生にメールを送信する必要があります。Copilotを使用して、教育者が課題を提出したときに自動的に学生にメールを送信する自動化を構築することができますか？ヒントは、適切なプロンプトを使用してPower AutomateのCopilotを使用してこれを構築できることです。

### スタートアップのための請求書情報テーブルを構築する

私たちのスタートアップの財務チームは、請求書を追跡するのに苦労しています。彼らはスプレッドシートを使用して請求書を追跡していましたが、請求書の数が増えるにつれて管理が難しくなってきました。彼らは、受け取った請求書の情報を保存し、追跡し、管理するのに役立つテーブルを構築するように求めています。このテーブルは、すべての請求書情報を抽出してテーブルに保存する自動化を構築するために使用されるべきです。また、財務チームが支払済みの請求書と未払いの請求書を表示することを可能にするべきです。

Power Platformには、アプリやソリューションのデータを保存するための基盤となるデータプラットフォームであるDataverseがあります。Dataverseは、アプリのデータを保存するためのローコードデータプラットフォームを提供します。これは、Microsoft Cloud内でデータを安全に保存する完全に管理されたサービスであり、Power Platform環境内でプロビジョニングされます。データ分類、データ系統、きめ細かなアクセス制御などの組み込みデータガバナンス機能を備えています。Dataverseについての詳細は[こちら](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro?WT.mc_id=academic-109639-somelezediko)をご覧ください。

なぜ私たちのスタートアップにDataverseを使用するべきなのでしょうか？Dataverseの標準およびカスタムテーブルは、データのための安全でクラウドベースのストレージオプションを提供します。テーブルを使用すると、Excelの単一のワークブックで複数のワークシートを使用するのと同様に、さまざまな種類のデータを保存できます。組織やビジネスのニーズに特化したデータを保存するためにテーブルを使用できます。私たちのスタートアップがDataverseを使用することで得られる利点には、次のようなものがありますが、これに限定されません：

- **管理が簡単**：メタデータとデータの両方がクラウドに保存されるため、それらがどのように保存または管理されるかについて心配する必要はありません。アプリやソリューションの構築に集中できます。

- **安全**：Dataverseは、データのための安全でクラウドベースのストレージオプションを提供します。役割ベースのセキュリティを使用して、テーブル内のデータへのアクセスを制
テキスト。 - **感情分析**: このモデルはテキスト内のポジティブ、ネガティブ、中立、または混合感情を検出します。 - **名刺リーダー**: このモデルは名刺から情報を抽出します。 - **テキスト認識**: このモデルは画像からテキストを抽出します。 - **物体検出**: このモデルは画像から物体を検出し抽出します。 - **ドキュメント処理**: このモデルはフォームから情報を抽出します。 - **請求書処理**: このモデルは請求書から情報を抽出します。カスタムAIモデルを使用すると、自分のモデルをAI Builderに持ち込むことができ、AI Builderのカスタムモデルのように機能させることができ、自分のデータを使ってモデルをトレーニングできます。これらのモデルを使用して、Power AppsとPower Automateの両方でプロセスを自動化し、結果を予測することができます。自分のモデルを使用する際には制限があります。これらの[制限](https://learn.microsoft.com/ai-builder/byo-model#limitations?WT.mc_id=academic-105485-koreyst)について詳しく読むことができます。

## 課題#2 - スタートアップのための請求書処理フローを構築

財務チームは請求書の処理に苦労しています。彼らは請求書を追跡するためにスプレッドシートを使用していましたが、請求書の数が増えるにつれて管理が難しくなっています。彼らはAIを使用して請求書を処理するワークフローを構築するよう求めています。ワークフローは請求書から情報を抽出し、その情報をDataverseテーブルに保存できるようにする必要があります。また、抽出した情報を財務チームにメールで送信できるようにする必要があります。AI Builderが何であるか、なぜ使用するべきかを理解したので、請求書処理AIモデルを使用して、財務チームが請求書を処理するのを助けるワークフローを構築する方法を見ていきましょう。AI Builderの請求書処理AIモデルを使用して財務チームが請求書を処理するのを助けるワークフローを構築するには、以下の手順に従ってください：

1. [Power Automate](https://make.powerautomate.com?WT.mc_id=academic-105485-koreyst)のホーム画面に移動します。
2. ホーム画面のテキストエリアを使用して、構築したいワークフローを説明します。例えば、**_メールボックスに請求書が届いたときに処理する_**。**送信**ボタンをクリックしてAIコパイロットにプロンプトを送信します。

3. AIコパイロットは、あなたが自動化したいタスクを実行するために必要なアクションを提案します。**次へ**ボタンをクリックして次のステップに進むことができます。
4. 次のステップでは、Power Automateがフローに必要な接続を設定するよう促します。完了したら、**フローを作成**ボタンをクリックしてフローを作成します。
5. AIコパイロットがフローを生成し、その後、フローをカスタマイズしてニーズに合わせることができます。
6. フローのトリガーを更新し、**フォルダー**を請求書が保存されるフォルダーに設定します。例えば、フォルダーを**受信トレイ**に設定することができます。**詳細オプションを表示**をクリックし、**添付ファイルのみ**を**はい**に設定します。これにより、フォルダーに添付ファイル付きのメールが届いたときにのみフローが実行されるようになります。
7. フローから以下のアクションを削除します：**HTMLからテキストへ**、**作成**、**作成2**、**作成3**、**作成4**。これらは使用しないためです。
8. **条件**アクションをフローから削除します。これも使用しないためです。次のスクリーンショットのようになります：

9. **アクションを追加**ボタンをクリックし、**Dataverse**を検索します。**新しい行を追加**アクションを選択します。
10. **請求書から情報を抽出**アクションで、**請求書ファイル**をメールの**添付ファイルコンテンツ**にポイントするように更新します。これにより、フローが請求書の添付ファイルから情報を抽出することができます。
11. 以前に作成した**テーブル**を選択します。例えば、**請求書情報**テーブルを選択します。前のアクションからの動的コンテンツを選択して、次のフィールドを埋めます：
    - ID
    - 金額
    - 日付
    - 名前
    - ステータス
    - ステータスを**保留中**に設定します。
    - サプライヤーのメール
    - **新しいメールが届いたとき**のトリガーからの**From**動的コンテンツを使用します。

12. フローが完了したら、**保存**ボタンをクリックしてフローを保存します。その後、トリガーで指定したフォルダーに請求書を添付したメールを送信してフローをテストできます。

> **宿題**: 今構築したフローは良いスタートですが、財務チームがサプライヤーに請求書の現在のステータスを更新するメールを送信できるようにする自動化をどのように構築するか考えてください。ヒント: フローは請求書のステータスが変わったときに実行されなければなりません。

## Power Automateでテキスト生成AIモデルを使用する

AI BuilderのGPT AIモデルでテキストを生成することで、プロンプトに基づいてテキストを生成することができます。これはMicrosoft Azure OpenAIサービスによって提供されます。この機能を使用すると、GPT（Generative Pre-Trained Transformer）技術をアプリやフローに組み込んで、さまざまな自動フローや洞察に満ちたアプリケーションを構築できます。

GPTモデルは大量のデータで徹底的にトレーニングされており、プロンプトを与えられると人間の言語に近いテキストを生成することができます。ワークフローの自動化と統合することで、GPTのようなAIモデルを活用して多くのタスクを効率的に自動化することができます。

例えば、さまざまな用途のために自動的にテキストを生成するフローを構築できます。メールの下書き、製品説明などです。また、チャットボットやカスタマーサービスアプリのようなアプリのためにテキストを生成するためにもモデルを使用できます。これにより、カスタマーサービスエージェントが顧客の問い合わせに効果的かつ効率的に対応できるようになります。

このAIモデルをPower Automateで使用する方法について学ぶには、[AI BuilderとGPTでインテリジェンスを追加](https://learn.microsoft.com/training/modules/ai-builder-text-generation/?WT.mc_id=academic-109639-somelezediko)モジュールを参照してください。

## 素晴らしい仕事です！学び続けましょう

このレッスンを完了したら、[生成AI学習コレクション](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst)をチェックして、生成AIの知識をさらに深めましょう！

レッスン11に進み、[機能呼び出しと生成AIを統合する方法](../11-integrating-with-function-calling/README.md?WT.mc_id=academic-105485-koreyst)を見ていきましょう！

**免責事項**:  
この文書は、AI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されています。正確さを期すよう努めていますが、自動翻訳には誤りや不正確さが含まれる可能性があることをご了承ください。原文は信頼できる情報源として考慮されるべきです。重要な情報については、専門の人間による翻訳をお勧めします。この翻訳の使用に起因する誤解や誤訳について、当社は責任を負いません。