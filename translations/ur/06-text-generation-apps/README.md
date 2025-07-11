<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "5ec6c92b629564538ef397c550adb73e",
  "translation_date": "2025-05-19T16:42:29+00:00",
  "source_file": "06-text-generation-apps/README.md",
  "language_code": "ur"
}
-->
# ٹیکسٹ جنریشن ایپلیکیشنز بنانا

آپ نے اس نصاب کے ذریعے ابھی تک دیکھا ہے کہ کچھ بنیادی تصورات ہیں جیسے پرامپٹس اور یہاں تک کہ ایک پوری ڈسپلن "پرامپٹ انجینئرنگ" کہلاتی ہے۔ بہت سے ٹولز جیسے ChatGPT، Office 365، Microsoft Power Platform وغیرہ آپ کو پرامپٹس استعمال کر کے کچھ حاصل کرنے کی حمایت کرتے ہیں۔

کسی ایپ میں ایسا تجربہ شامل کرنے کے لیے، آپ کو پرامپٹس، مکملات کو سمجھنا اور کام کرنے کے لیے ایک لائبریری کا انتخاب کرنا ضروری ہے۔ یہی آپ اس باب میں سیکھیں گے۔

## تعارف

اس باب میں، آپ:

- openai لائبریری اور اس کے بنیادی تصورات کے بارے میں سیکھیں گے۔
- openai کا استعمال کرتے ہوئے ایک ٹیکسٹ جنریشن ایپ بنائیں گے۔
- سمجھیں گے کہ ٹیکسٹ جنریشن ایپ بنانے کے لیے پرامپٹ، ٹیمپریچر، اور ٹوکنز جیسے تصورات کو کیسے استعمال کریں۔

## سیکھنے کے اہداف

اس سبق کے اختتام پر، آپ قابل ہوں گے:

- وضاحت کریں کہ ٹیکسٹ جنریشن ایپ کیا ہے۔
- openai کا استعمال کرتے ہوئے ایک ٹیکسٹ جنریشن ایپ بنائیں۔
- اپنی ایپ کو زیادہ یا کم ٹوکنز استعمال کرنے کے لیے کنفیگر کریں اور آؤٹ پٹ کو مختلف بنانے کے لیے ٹیمپریچر کو بھی تبدیل کریں۔

## ٹیکسٹ جنریشن ایپ کیا ہے؟

عام طور پر جب آپ کوئی ایپ بناتے ہیں تو اس کی کچھ قسم کی انٹرفیس ہوتی ہے جیسے:

- کمانڈ پر مبنی۔ کنسول ایپس عام ایپس ہیں جہاں آپ ایک کمانڈ ٹائپ کرتے ہیں اور یہ ایک کام انجام دیتی ہے۔ مثال کے طور پر، `git` ایک کمانڈ پر مبنی ایپ ہے۔
- صارف انٹرفیس (UI)۔ کچھ ایپس کے گرافیکل یوزر انٹرفیس (GUIs) ہوتے ہیں جہاں آپ بٹن کلک کرتے ہیں، ٹیکسٹ درج کرتے ہیں، اختیارات منتخب کرتے ہیں وغیرہ۔

### کنسول اور UI ایپس محدود ہیں

اسے کمانڈ پر مبنی ایپ سے موازنہ کریں جہاں آپ ایک کمانڈ ٹائپ کرتے ہیں:

- **یہ محدود ہے**۔ آپ کوئی بھی کمانڈ ٹائپ نہیں کر سکتے، صرف وہی جو ایپ سپورٹ کرتی ہے۔
- **زبان مخصوص**۔ کچھ ایپس کئی زبانوں کو سپورٹ کرتی ہیں، لیکن ڈیفالٹ کے طور پر ایپ ایک مخصوص زبان کے لیے بنائی گئی ہوتی ہے، چاہے آپ مزید زبان کی سپورٹ شامل کر سکتے ہیں۔

### ٹیکسٹ جنریشن ایپس کے فوائد

تو ٹیکسٹ جنریشن ایپ کیسے مختلف ہے؟

ایک ٹیکسٹ جنریشن ایپ میں، آپ کے پاس زیادہ لچک ہوتی ہے، آپ کمانڈز کے ایک سیٹ یا مخصوص ان پٹ زبان تک محدود نہیں ہوتے۔ اس کے بجائے، آپ ایپ کے ساتھ تعامل کرنے کے لیے قدرتی زبان استعمال کر سکتے ہیں۔ ایک اور فائدہ یہ ہے کہ چونکہ آپ پہلے ہی ایک ڈیٹا سورس کے ساتھ تعامل کر رہے ہیں جو معلومات کے وسیع ذخیرے پر تربیت یافتہ ہے، جبکہ ایک روایتی ایپ ڈیٹا بیس میں موجود چیزوں تک محدود ہو سکتی ہے۔

### میں ٹیکسٹ جنریشن ایپ کے ساتھ کیا بنا سکتا ہوں؟

آپ بہت سی چیزیں بنا سکتے ہیں۔ مثال کے طور پر:

- **ایک چیٹ بوٹ**۔ ایک چیٹ بوٹ جو آپ کی کمپنی اور اس کی مصنوعات جیسے موضوعات کے بارے میں سوالات کے جوابات دیتا ہے ایک اچھا میچ ہو سکتا ہے۔
- **مددگار**۔ LLMs متن کو خلاصہ کرنے، متن سے بصیرت حاصل کرنے، متن تیار کرنے جیسے ریزیومے وغیرہ میں بہترین ہیں۔
- **کوڈ اسسٹنٹ**۔ آپ جس زبان ماڈل کا استعمال کرتے ہیں اس پر منحصر ہے، آپ ایک کوڈ اسسٹنٹ بنا سکتے ہیں جو آپ کو کوڈ لکھنے میں مدد کرے۔ مثال کے طور پر، آپ GitHub Copilot کے ساتھ ساتھ ChatGPT جیسی مصنوعات استعمال کر سکتے ہیں تاکہ آپ کو کوڈ لکھنے میں مدد ملے۔

## میں کیسے شروع کر سکتا ہوں؟

ٹھیک ہے، آپ کو LLM کے ساتھ انضمام کا راستہ تلاش کرنا ہوگا جس میں عام طور پر درج ذیل دو طریقے شامل ہوتے ہیں:

- API کا استعمال کریں۔ یہاں آپ اپنی پرامپٹ کے ساتھ ویب درخواستیں بنا رہے ہیں اور واپس تیار شدہ متن حاصل کر رہے ہیں۔
- لائبریری کا استعمال کریں۔ لائبریریاں API کالز کو انکیپسولیٹ کرنے میں مدد کرتی ہیں اور انہیں استعمال میں آسان بناتی ہیں۔

## لائبریریاں/SDKs

LLMs کے ساتھ کام کرنے کے لیے کچھ معروف لائبریریاں ہیں جیسے:

- **openai**، یہ لائبریری آپ کے ماڈل سے جڑنا اور پرامپٹس بھیجنا آسان بناتی ہے۔

پھر کچھ لائبریریاں ہیں جو اعلیٰ سطح پر کام کرتی ہیں جیسے:

- **Langchain**۔ Langchain معروف ہے اور Python کو سپورٹ کرتا ہے۔
- **Semantic Kernel**۔ Semantic Kernel ایک مائیکروسافٹ کی لائبریری ہے جو زبانوں C#, Python، اور Java کو سپورٹ کرتی ہے۔

## openai کا استعمال کرتے ہوئے پہلی ایپ

آئیے دیکھتے ہیں کہ ہم اپنی پہلی ایپ کیسے بنا سکتے ہیں، ہمیں کن لائبریریوں کی ضرورت ہے، کتنا ضروری ہے وغیرہ۔

### openai انسٹال کریں

OpenAI یا Azure OpenAI کے ساتھ تعامل کے لیے بہت سی لائبریریاں موجود ہیں۔ متعدد پروگرامنگ زبانوں کا استعمال ممکن ہے جیسے C#, Python, JavaScript, Java اور مزید۔ ہم نے `openai` Python لائبریری استعمال کرنے کا انتخاب کیا ہے، لہذا ہم `pip` کا استعمال کریں گے اسے انسٹال کرنے کے لیے۔

### ایک ریسورس بنائیں

آپ کو درج ذیل مراحل انجام دینے کی ضرورت ہے:

- Azure پر اکاؤنٹ بنائیں [https://azure.microsoft.com/free/](https://azure.microsoft.com/free/?WT.mc_id=academic-105485-koreyst)۔
- Azure OpenAI تک رسائی حاصل کریں۔ [https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai](https://learn.microsoft.com/azure/ai-services/openai/overview#how-do-i-get-access-to-azure-openai?WT.mc_id=academic-105485-koreyst) پر جائیں اور رسائی کی درخواست کریں۔

  > [!NOTE]
  > لکھتے وقت، آپ کو Azure OpenAI تک رسائی کے لیے درخواست دینی ہوگی۔

- Python انسٹال کریں <https://www.python.org/>
- Azure OpenAI سروس ریسورس بنایا ہوا ہو۔ [create a resource](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal?WT.mc_id=academic-105485-koreyst) کے لیے اس گائیڈ کو دیکھیں۔

### API کی اور اختتامی نقطہ کا پتہ لگائیں

اس وقت، آپ کو اپنی `openai` لائبریری کو بتانا ہوگا کہ کون سی API کی استعمال کرنی ہے۔ اپنی API کی تلاش کرنے کے لیے، اپنے Azure OpenAI ریسورس کے "Keys and Endpoint" سیکشن پر جائیں اور "Key 1" ویلیو کو کاپی کریں۔

اب جب کہ آپ نے یہ معلومات کاپی کر لی ہے، آئیے لائبریریوں کو اس کے استعمال کی ہدایت دیں۔

> [!NOTE]
> اپنے API کی کوڈ سے الگ کرنا قابل قدر ہے۔ آپ ایسا ماحول کے متغیرات کا استعمال کرتے ہوئے کر سکتے ہیں۔
>
> - ماحول کا متغیر سیٹ کریں `OPENAI_API_KEY` to your API key.
>   `export OPENAI_API_KEY='sk-...'`

### Azure کنفیگریشن سیٹ اپ کریں

اگر آپ Azure OpenAI استعمال کر رہے ہیں، تو یہاں آپ کنفیگریشن کیسے سیٹ اپ کرتے ہیں:

اوپر ہم درج ذیل ترتیب دے رہے ہیں:

ہم نے اوپر کوڈ میں ایک مکملات آبجیکٹ بنایا اور ماڈل اور پرامپٹ پاس کیا۔ پھر ہم تیار شدہ متن کو پرنٹ کرتے ہیں۔

### چیٹ مکملات

اب تک، آپ نے دیکھا ہے کہ ہم `Completion` to generate text. But there's another class called `ChatCompletion` استعمال کر رہے ہیں جو چیٹ بوٹس کے لیے زیادہ موزوں ہے۔ یہاں اسے استعمال کرنے کی ایک مثال ہے:

اس فعالیت کے بارے میں مزید ایک آنے والے باب میں۔

## مشق - اپنی پہلی ٹیکسٹ جنریشن ایپ

اب جب کہ ہم نے openai کو سیٹ اپ اور کنفیگر کرنے کا طریقہ سیکھا، اب اپنی پہلی ٹیکسٹ جنریشن ایپ بنانے کا وقت ہے۔ اپنی ایپ بنانے کے لیے، ان مراحل پر عمل کریں:

1. ایک ورچوئل ماحول بنائیں اور openai انسٹال کریں:

   > [!NOTE]
   > اگر آپ Windows استعمال کر رہے ہیں تو ٹائپ کریں `venv\Scripts\activate` instead of `source venv/bin/activate`.

   > [!NOTE]
   > Locate your Azure OpenAI key by going to [https://portal.azure.com/](https://portal.azure.com/?WT.mc_id=academic-105485-koreyst) and search for `Open AI` and select the `Open AI resource` and then select `Keys and Endpoint` and copy the `Key 1` ویلیو۔

1. ایک _app.py_ فائل بنائیں اور اسے درج ذیل کوڈ دیں:

   > [!NOTE]
   > اگر آپ Azure OpenAI استعمال کر رہے ہیں، تو آپ کو `api_type` to `azure` and set the `api_key` اپنے Azure OpenAI کی پر سیٹ کرنا ہوگا۔

   آپ کو درج ذیل کی طرح آؤٹ پٹ نظر آنا چاہیے:

## مختلف چیزوں کے لیے مختلف قسم کے پرامپٹس

اب آپ نے دیکھا ہے کہ پرامپٹ کا استعمال کرتے ہوئے متن کیسے تیار کیا جائے۔ آپ کے پاس ایک پروگرام بھی چل رہا ہے جسے آپ تبدیل اور تبدیل کر سکتے ہیں تاکہ مختلف قسم کے متن تیار کر سکیں۔

پرامپٹس کو ہر قسم کے کاموں کے لیے استعمال کیا جا سکتا ہے۔ مثال کے طور پر:

- **ایک قسم کا متن تیار کریں**۔ مثال کے طور پر، آپ ایک نظم، کوئز کے لیے سوالات وغیرہ تیار کر سکتے ہیں۔
- **معلومات کی تلاش**۔ آپ پرامپٹس کا استعمال معلومات تلاش کرنے کے لیے کر سکتے ہیں جیسے درج ذیل مثال 'ویب ڈویلپمنٹ میں CORS کا کیا مطلب ہے؟'۔
- **کوڈ تیار کریں**۔ آپ کوڈ تیار کرنے کے لیے پرامپٹس کا استعمال کر سکتے ہیں، مثال کے طور پر ای میلز کی توثیق کرنے کے لیے استعمال ہونے والے ریگولر ایکسپریشن تیار کرنا یا کیوں نہ ایک پورا پروگرام تیار کریں، جیسے ایک ویب ایپ؟

## ایک زیادہ عملی استعمال کیس: ایک ریسیپی جنریٹر

تصور کریں کہ آپ کے گھر میں اجزاء ہیں اور آپ کچھ پکانا چاہتے ہیں۔ اس کے لیے آپ کو ایک ریسیپی کی ضرورت ہے۔ ریسیپیز تلاش کرنے کا ایک طریقہ سرچ انجن کا استعمال کرنا ہے یا آپ LLM کا استعمال کر سکتے ہیں۔

آپ ایک پرامپٹ اس طرح لکھ سکتے ہیں:

> "مجھے درج ذیل اجزاء کے ساتھ ڈش کے لیے 5 ریسیپیز دکھائیں: چکن، آلو، اور گاجر۔ ہر ریسیپی میں استعمال ہونے والے تمام اجزاء کی فہرست بنائیں"

اوپر دی گئی پرامپٹ کے پیش نظر، آپ کو ممکنہ طور پر درج ذیل جواب مل سکتا ہے:

یہ نتیجہ زبردست ہے، مجھے معلوم ہے کہ کیا پکانا ہے۔ اس وقت، جو مفید بہتری ہو سکتی ہیں وہ ہیں:

- وہ اجزاء نکالنا جو مجھے پسند نہیں ہیں یا جن سے مجھے الرجی ہے۔
- خریداری کی فہرست تیار کرنا، اگر میرے پاس گھر میں تمام اجزاء نہیں ہیں۔

اوپر کے کیسز کے لیے، آئیے ایک اضافی پرامپٹ شامل کریں:

> "براہ کرم وہ ریسیپیز نکال دیں جن میں لہسن ہے کیونکہ مجھے اس سے الرجی ہے اور اسے کسی اور چیز سے بدل دیں۔ نیز، براہ کرم ریسیپیز کے لیے خریداری کی فہرست تیار کریں، یہ غور کرتے ہوئے کہ میرے پاس پہلے ہی گھر میں چکن، آلو اور گاجر ہیں۔"

اب آپ کے پاس ایک نیا نتیجہ ہے، یعنی:

یہ آپ کی پانچ ریسیپیز ہیں، جن میں کہیں بھی لہسن کا ذکر نہیں ہے اور آپ کے پاس گھر میں جو کچھ پہلے سے موجود ہے اس کو مدنظر رکھتے ہوئے آپ کے پاس خریداری کی فہرست بھی ہے۔

## مشق - ایک ریسیپی جنریٹر بنائیں

اب جب کہ ہم نے ایک منظر نامہ پیش کیا ہے، آئیے کوڈ لکھتے ہیں تاکہ مظاہرہ کیے گئے منظر نامے سے میل کھائے۔ ایسا کرنے کے لیے، ان مراحل پر عمل کریں:

1. موجودہ _app.py_ فائل کو ایک نقطہ آغاز کے طور پر استعمال کریں
1. `prompt` متغیر کو تلاش کریں اور اس کے کوڈ کو درج ذیل میں تبدیل کریں:

اگر آپ اب کوڈ چلاتے ہیں، تو آپ کو ممکنہ طور پر درج ذیل کی طرح آؤٹ پٹ نظر آنا چاہیے:

> نوٹ، آپ کا LLM غیر متعین ہے، لہذا آپ کو ہر بار پروگرام چلانے پر مختلف نتائج مل سکتے ہیں۔

زبردست، آئیے دیکھتے ہیں کہ ہم چیزوں کو کیسے بہتر بنا سکتے ہیں۔ چیزوں کو بہتر بنانے کے لیے، ہم چاہتے ہیں کہ کوڈ لچکدار ہو، لہذا اجزاء اور ریسیپیز کی تعداد کو بہتر بنایا جا سکتا ہے اور تبدیل کیا جا سکتا ہے۔

1. آئیے کوڈ کو درج ذیل طریقے سے تبدیل کریں:

کوڈ کو ٹیسٹ رن کے لیے لے جانا، اس طرح نظر آ سکتا ہے:

### فلٹر اور خریداری کی فہرست شامل کر کے بہتر بنائیں

اب ہمارے پاس ایک کام کرنے والی ایپ ہے جو ریسیپیز تیار کرنے کی صلاحیت رکھتی ہے اور یہ لچکدار ہے کیونکہ یہ صارف کے ان پٹس پر انحصار کرتی ہے، دونوں ریسیپیز کی تعداد کے ساتھ ساتھ استعمال ہونے والے اجزاء پر۔

اسے مزید بہتر بنانے کے لیے، ہم درج ذیل شامل کرنا چاہتے ہیں:

- **اجزاء کو فلٹر کریں**۔ ہم ان اجزاء کو فلٹر کرنے کے قابل ہونا چاہتے ہیں جو ہمیں پسند نہیں ہیں یا جن سے ہمیں الرجی ہے۔ اس تبدیلی کو انجام دینے کے لیے، ہم اپنے موجودہ پرامپٹ میں ترمیم کر سکتے ہیں اور اس کے آخر میں فلٹر کی حالت شامل کر سکتے ہیں جیسے:

  اوپر، ہم نے `{filter}` کو پرامپٹ کے آخر میں شامل کیا اور ہم نے صارف سے فلٹر ویلیو بھی حاصل کی۔

  پروگرام چلانے کے مثال ان پٹ اب اس طرح نظر آ سکتا ہے:

  جیسا کہ آپ دیکھ سکتے ہیں، اس میں دودھ کے ساتھ کوئی بھی ریسیپی فلٹر ہو گئی ہے۔ لیکن، اگر آپ کو لییکٹوز سے الرجی ہے، تو آپ دودھ کے ساتھ ریسیپیز کو بھی فلٹر کرنا چاہتے ہیں، لہذا واضح ہونے کی ضرورت ہے۔

- **خریداری کی فہرست تیار کریں**۔ ہم چاہتے ہیں کہ جو ہمارے پاس پہلے سے گھر میں موجود ہے اس کو مدنظر رکھتے ہوئے خریداری کی فہرست تیار کریں۔

  اس فعالیت کے لیے، ہم یا تو سب کچھ ایک پرامپٹ میں حل کرنے کی کوشش کر سکتے ہیں یا ہم اسے دو پرامپٹس میں تقسیم کر سکتے ہیں۔ آئیے بعد کے طریقے کی کوشش کرتے ہیں۔ یہاں ہم اضافی پرامپٹ شامل کرنے کا مشورہ دے رہے ہیں، لیکن اس کے کام کرنے کے لیے، ہمیں پہلے پرامپٹ کے نتیجے کو بعد کے پرامپٹ کے لیے سیاق و سباق کے طور پر شامل کرنے کی ضرورت ہے۔

  کوڈ میں اس حصے کو تلاش کریں جو پہلے پرامپٹ کے نتیجے کو پرنٹ کرتا ہے اور اس کے نیچے درج ذیل کوڈ شامل کریں:

  مندرجہ ذیل نوٹ کریں:

  1. ہم پہلے پرامپٹ کے نتیجے کو نئے پرامپٹ میں شامل کر کے ایک نیا پرامپٹ بنا رہے ہیں:

  1. ہم ایک نئی درخواست بنا رہے ہیں، لیکن پہلے پرامپٹ میں مانگے گئے ٹوکنز کی تعداد کو بھی مدنظر رکھتے ہوئے، اس لیے اس بار ہم کہتے ہیں `max_tokens` 1200 ہے۔

     اس کوڈ کو ایک چکر لگانے کے لیے لے جانا، ہم اب درج ذیل آؤٹ پٹ پر پہنچتے ہیں:

## اپنی سیٹ اپ کو بہتر بنائیں

جو ہمارے پاس اب تک ہے وہ کوڈ ہے جو کام کرتا ہے، لیکن کچھ اصلاحات ہیں جو ہمیں چیزوں کو مزید بہتر بنانے کے لیے کرنی چاہئیں۔ کچھ چیزیں جو ہمیں کرنی چاہئیں وہ ہیں:

- **رازوں کو کوڈ سے الگ کریں**، جیسے API کی۔ راز کوڈ میں نہیں ہوتے اور انہیں محفوظ مقام پر ذخیرہ کیا جانا چاہیے۔ کوڈ سے راز کو الگ کرنے کے لیے، ہم ماحول کے متغیرات اور لائبریریوں جیسے `python-dotenv` to load them from a file. Here's how that would look like in code:

  1. Create a `.env` فائل کے ساتھ درج ذیل مواد استعمال کر سکتے ہیں:

     > نوٹ، Azure کے لیے، آپ کو درج ذیل ماحول کے متغیرات سیٹ کرنے کی ضرورت ہے:

     کوڈ میں، آپ ماحول کے متغیرات کو اس طرح لوڈ کریں گے:

- **ٹوکن کی لمبائی پر ایک لفظ**۔ ہمیں اس پر غور کرنا چاہیے کہ ہم کتنے ٹوکنز کو اس متن کو تیار کرنے کے لیے استعمال کرنے کی ضرورت ہے جو ہم چاہتے ہیں۔ ٹوکنز کی قیمت ہوتی ہے، لہذا جہاں ممکن ہو، ہمیں استعمال کیے جانے والے ٹوکنز کی تعداد کے ساتھ اقتصادی ہونے کی کوشش کرنی چاہیے۔ مثال کے طور پر، کیا ہم پرامپٹ کو اس طرح بنا سکتے ہیں کہ ہم کم ٹوکنز استعمال کر سکیں؟

  استعمال کیے جانے والے ٹوکنز کو تبدیل کرنے کے لیے، آپ `max_tokens` پیرامیٹر استعمال کر سکتے ہیں۔ مثال کے طور پر، اگر آپ 100 ٹوکنز استعمال کرنا چاہتے ہیں، تو آپ ایسا کریں گے:

- **درجہ حرارت کے ساتھ تجربہ کرنا**۔ درجہ حرارت کچھ ایسا ہے جس کا ہم نے اب تک ذکر نہیں کیا لیکن یہ ہمارے پروگرام کی کارکردگی کے لیے ایک اہم سیاق و سباق ہے۔ درجہ حرارت کی قدر جتنی زیادہ ہوگی، آؤٹ پٹ اتنا ہی بے ترتیب ہوگا۔ اس کے برعکس درجہ حرارت کی قدر جتنی کم ہوگی، آؤٹ پٹ اتنا ہی پیش قیاسی ہوگا۔ غور کریں

**ڈسکلیمر**:  
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کا استعمال کرتے ہوئے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کی پوری کوشش کرتے ہیں، براہ کرم آگاہ رہیں کہ خودکار ترجمے میں غلطیاں یا غلط بیانی ہو سکتی ہیں۔ اصل دستاویز کو اس کی مقامی زبان میں مستند ذریعہ سمجھا جانا چاہیے۔ اہم معلومات کے لیے، پیشہ ورانہ انسانی ترجمہ کی سفارش کی جاتی ہے۔ ہم اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے ذمہ دار نہیں ہیں۔