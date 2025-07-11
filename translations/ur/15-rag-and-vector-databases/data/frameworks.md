<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "b5466bcedc3c75aa35476270362f626a",
  "translation_date": "2025-05-20T01:50:30+00:00",
  "source_file": "15-rag-and-vector-databases/data/frameworks.md",
  "language_code": "ur"
}
-->
# نیورل نیٹ ورک فریم ورک

جیسا کہ ہم پہلے ہی سیکھ چکے ہیں، نیورل نیٹ ورکس کو مؤثر طریقے سے ٹرین کرنے کے لئے ہمیں دو چیزیں کرنی ہوتی ہیں:

* ٹینسرز پر عملدرآمد کرنا، مثلاً ضرب، جمع، اور کچھ فنکشنز کا حساب لگانا جیسے سگموئڈ یا سوفٹ میکس
* تمام اظہارات کے گریڈینٹس کا حساب لگانا، تاکہ گریڈینٹ ڈیسنٹ آپٹیمائزیشن کی جا سکے

اگرچہ `numpy` لائبریری پہلا حصہ کر سکتی ہے، ہمیں گریڈینٹس کا حساب لگانے کے لئے کچھ میکانزم کی ضرورت ہوتی ہے۔ ہمارے فریم ورک میں جو ہم نے پچھلے سیکشن میں تیار کیا تھا، ہمیں تمام مشتقات کو `backward` میتھڈ کے اندر دستی طور پر پروگرام کرنا پڑتا تھا، جو بیک پروپیگیشن کرتا ہے۔ مثالی طور پر، ایک فریم ورک ہمیں کسی بھی اظہار کے گریڈینٹس کا حساب لگانے کا موقع فراہم کرنا چاہئے جو ہم تعریف کر سکتے ہیں۔

ایک اور اہم چیز یہ ہے کہ جی پی یو یا کسی اور خصوصی کمپیوٹ یونٹس جیسے ٹی پی یو پر حسابات انجام دینے کے قابل ہونا۔ ڈیپ نیورل نیٹ ورک کی تربیت کے لئے *بہت زیادہ* حسابات کی ضرورت ہوتی ہے، اور ان حسابات کو جی پی یو پر متوازی بنانا بہت اہم ہے۔

> ✅ اصطلاح 'parallelize' کا مطلب ہے کہ حسابات کو متعدد آلات پر تقسیم کرنا۔

فی الحال، دو سب سے مشہور نیورل فریم ورک ہیں: TensorFlow اور PyTorch۔ دونوں کم سطح کی API فراہم کرتے ہیں تاکہ CPU اور GPU دونوں پر ٹینسرز کے ساتھ کام کیا جا سکے۔ کم سطح کی API کے اوپر، ایک اعلی سطح کی API بھی ہے، جسے بالترتیب Keras اور PyTorch Lightning کہا جاتا ہے۔

کم سطح کی API | TensorFlow| PyTorch
--------------|-------------------------------------|--------------------------------
اعلی سطح کی API| Keras| Pytorch

**کم سطح کی APIs** دونوں فریم ورک میں آپ کو **کمپیوٹیشنل گراف** بنانے کی اجازت دیتی ہیں۔ یہ گراف وضاحت کرتا ہے کہ دیے گئے ان پٹ پیرامیٹرز کے ساتھ آؤٹ پٹ (عام طور پر نقصان کی فنکشن) کا حساب کیسے لگایا جائے، اور اگر دستیاب ہو تو اسے جی پی یو پر حساب کے لئے بھیجا جا سکتا ہے۔ اس کمپیوٹیشنل گراف کو مختلف کرنے اور گریڈینٹس کا حساب لگانے کے لئے فنکشنز موجود ہیں، جنہیں پھر ماڈل پیرامیٹرز کو بہتر بنانے کے لئے استعمال کیا جا سکتا ہے۔

**اعلی سطح کی APIs** کافی حد تک نیورل نیٹ ورکس کو **لیئرز کی ترتیب** کے طور پر دیکھتی ہیں، اور زیادہ تر نیورل نیٹ ورکس کی تعمیر کو آسان بناتی ہیں۔ ماڈل کی تربیت عام طور پر ڈیٹا تیار کرنے اور پھر `fit` فنکشن کو کال کرنے کی ضرورت ہوتی ہے۔

اعلی سطح کی API آپ کو عام نیورل نیٹ ورکس کو بہت جلد تعمیر کرنے کی اجازت دیتی ہے بغیر بہت سی تفصیلات کے بارے میں فکر کئے۔ اسی وقت، کم سطح کی API تربیتی عمل پر بہت زیادہ کنٹرول فراہم کرتی ہیں، اور اس لئے وہ تحقیق میں بہت زیادہ استعمال ہوتی ہیں، جب آپ نئے نیورل نیٹ ورک آرکیٹیکچرز کے ساتھ کام کر رہے ہوتے ہیں۔

یہ سمجھنا بھی اہم ہے کہ آپ دونوں APIs کو اکٹھا استعمال کر سکتے ہیں، مثلاً آپ اپنی نیٹ ورک لیئر آرکیٹیکچر کو کم سطح کی API کا استعمال کرتے ہوئے تیار کر سکتے ہیں، اور پھر اسے بڑی نیٹ ورک کے اندر استعمال کر سکتے ہیں جو اعلی سطح کی API کے ساتھ تعمیر اور تربیت کی جاتی ہے۔ یا آپ اعلی سطح کی API کا استعمال کرتے ہوئے لیئرز کی ترتیب کے طور پر نیٹ ورک کی تعریف کر سکتے ہیں، اور پھر اپنی کم سطح کی تربیتی لوپ کا استعمال کر کے آپٹیمائزیشن انجام دے سکتے ہیں۔ دونوں APIs ایک ہی بنیادی تصورات کا استعمال کرتی ہیں، اور انہیں اکٹھا کام کرنے کے لئے ڈیزائن کیا گیا ہے۔

## سیکھنا

اس کورس میں، ہم زیادہ تر مواد PyTorch اور TensorFlow دونوں کے لئے پیش کرتے ہیں۔ آپ اپنا پسندیدہ فریم ورک منتخب کر سکتے ہیں اور صرف متعلقہ نوٹ بکس کے ذریعے جا سکتے ہیں۔ اگر آپ کو یقین نہیں ہے کہ کون سا فریم ورک منتخب کرنا ہے، تو انٹرنیٹ پر **PyTorch بمقابلہ TensorFlow** کے بارے میں کچھ مباحثے پڑھیں۔ آپ دونوں فریم ورک کو دیکھ کر بھی بہتر سمجھ حاصل کر سکتے ہیں۔

جہاں ممکن ہو، ہم سادگی کے لئے اعلی سطح کی APIs کا استعمال کریں گے۔ تاہم، ہمارا یقین ہے کہ یہ سمجھنا اہم ہے کہ نیورل نیٹ ورکس کیسے کام کرتے ہیں، اس لئے شروع میں ہم کم سطح کی API اور ٹینسرز کے ساتھ کام کرتے ہیں۔ تاہم، اگر آپ تیزی سے شروع کرنا چاہتے ہیں اور ان تفصیلات پر زیادہ وقت نہیں گزارنا چاہتے، تو آپ انہیں چھوڑ کر سیدھے اعلی سطح کی API نوٹ بکس میں جا سکتے ہیں۔

## ✍️ مشقیں: فریم ورک

مندرجہ ذیل نوٹ بکس میں اپنی سیکھنے کو جاری رکھیں:

کم سطح کی API | TensorFlow+Keras نوٹ بک | PyTorch
--------------|-------------------------------------|--------------------------------
اعلی سطح کی API| Keras | *PyTorch Lightning*

فریم ورک کو ماسٹر کرنے کے بعد، آئیے اوور فٹنگ کے تصور کا اعادہ کرتے ہیں۔

# اوور فٹنگ

اوور فٹنگ مشین لرننگ میں ایک انتہائی اہم تصور ہے، اور اسے صحیح طریقے سے سمجھنا بہت اہم ہے!

مندرجہ ذیل مسئلے پر غور کریں جہاں 5 نقطے (جن کی نمائندگی `x` سے کی گئی ہے) کی تخمینہ لگائی جا رہی ہے:

!linear | overfit
-------------------------|--------------------------
**لکیری ماڈل، 2 پیرامیٹرز** | **غیر لکیری ماڈل، 7 پیرامیٹرز**
تربیتی غلطی = 5.3 | تربیتی غلطی = 0
تصدیقی غلطی = 5.1 | تصدیقی غلطی = 20

* بائیں جانب، ہم ایک اچھی سیدھی لائن کی تخمینہ دیکھتے ہیں۔ کیونکہ پیرامیٹرز کی تعداد مناسب ہے، ماڈل نقطوں کی تقسیم کے پیچھے کے خیال کو صحیح طریقے سے حاصل کرتا ہے۔
* دائیں جانب، ماڈل بہت زیادہ طاقتور ہے۔ کیونکہ ہمارے پاس صرف 5 نقطے ہیں اور ماڈل کے پاس 7 پیرامیٹرز ہیں، یہ اس طرح ایڈجسٹ ہو سکتا ہے کہ تمام نقطوں سے گزر سکے، جس کی وجہ سے تربیتی غلطی 0 ہو جاتی ہے۔ تاہم، یہ ماڈل کو ڈیٹا کے پیچھے کے صحیح پیٹرن کو سمجھنے سے روکتا ہے، اس لئے تصدیقی غلطی بہت زیادہ ہوتی ہے۔

یہ بہت اہم ہے کہ ماڈل کی بھرپوریت (پیرامیٹرز کی تعداد) اور تربیتی نمونوں کی تعداد کے درمیان صحیح توازن قائم کیا جائے۔

## اوور فٹنگ کیوں ہوتی ہے

  * تربیتی ڈیٹا کی کمی
  * بہت زیادہ طاقتور ماڈل
  * ان پٹ ڈیٹا میں بہت زیادہ شور

## اوور فٹنگ کا پتہ کیسے لگائیں

جیسا کہ آپ اوپر کے گراف سے دیکھ سکتے ہیں، اوور فٹنگ کا پتہ بہت کم تربیتی غلطی اور زیادہ تصدیقی غلطی سے لگایا جا سکتا ہے۔ عام طور پر تربیت کے دوران ہم دیکھیں گے کہ تربیتی اور تصدیقی غلطیاں دونوں کم ہونا شروع ہو جاتی ہیں، اور پھر کسی نقطے پر تصدیقی غلطی کم ہونا بند کر سکتی ہے اور بڑھنا شروع کر سکتی ہے۔ یہ اوور فٹنگ کا اشارہ ہو گا، اور یہ اشارہ کہ ہمیں شاید اس نقطے پر تربیت کو روک دینا چاہئے (یا کم از کم ماڈل کی ایک اسنیپ شاٹ لے لینی چاہئے)۔

## اوور فٹنگ کو کیسے روکا جائے

اگر آپ دیکھ سکتے ہیں کہ اوور فٹنگ ہو رہی ہے، تو آپ مندرجہ ذیل میں سے کوئی ایک کام کر سکتے ہیں:

 * تربیتی ڈیٹا کی مقدار میں اضافہ کریں
 * ماڈل کی پیچیدگی کو کم کریں
 * کچھ ریگولرائزیشن تکنیک کا استعمال کریں، جیسے Dropout، جس پر ہم بعد میں غور کریں گے۔

## اوور فٹنگ اور بایاس واریانس تجارت

اوور فٹنگ دراصل شماریات میں ایک زیادہ عمومی مسئلے کی ایک صورت ہے جسے بایاس واریانس تجارت کہا جاتا ہے۔ اگر ہم اپنے ماڈل میں ممکنہ غلطیوں کے ذرائع پر غور کریں، تو ہم دو قسم کی غلطیوں کو دیکھ سکتے ہیں:

* **بایاس غلطیاں** ہمارے الگورتھم کی وجہ سے ہوتی ہیں جو تربیتی ڈیٹا کے درمیان رشتہ کو صحیح طور پر گرفت نہیں کر پاتی۔ یہ اس حقیقت کی وجہ سے ہو سکتی ہے کہ ہمارا ماڈل اتنا طاقتور نہیں ہے (**انڈر فٹنگ**).
* **واریانس غلطیاں**، جو ماڈل کی وجہ سے ان پٹ ڈیٹا میں شور کو معنی خیز رشتے کی بجائے اندازہ لگا رہی ہیں (**اوور فٹنگ**).

تربیت کے دوران، بایاس غلطی کم ہوتی ہے (جب ہمارا ماڈل ڈیٹا کی تخمینہ لگانا سیکھتا ہے)، اور واریانس غلطی بڑھتی ہے۔ یہ اہم ہے کہ تربیت کو روکیں - یا تو دستی طور پر (جب ہم اوور فٹنگ کا پتہ لگاتے ہیں) یا خودکار طور پر (ریگولرائزیشن متعارف کروا کر) - تاکہ اوور فٹنگ کو روکا جا سکے۔

## نتیجہ

اس سبق میں، آپ نے دو سب سے مشہور AI فریم ورک، TensorFlow اور PyTorch کے مختلف APIs کے درمیان فرق کے بارے میں سیکھا۔ اس کے علاوہ، آپ نے ایک بہت اہم موضوع، اوور فٹنگ کے بارے میں سیکھا۔

## 🚀 چیلنج

ہمراہ نوٹ بکس میں، آپ کو نیچے 'ٹاسکس' ملیں گے؛ نوٹ بکس کے ذریعے کام کریں اور ٹاسکس کو مکمل کریں۔

## جائزہ اور خود مطالعہ

مندرجہ ذیل موضوعات پر کچھ تحقیق کریں:

- TensorFlow
- PyTorch
- اوور فٹنگ

خود سے مندرجہ ذیل سوالات پوچھیں:

- TensorFlow اور PyTorch میں کیا فرق ہے؟
- اوور فٹنگ اور انڈر فٹنگ میں کیا فرق ہے؟

## اسائنمنٹ

اس لیب میں، آپ سے کہا جاتا ہے کہ آپ دو درجہ بندی کے مسائل کو واحد اور کثیر پرتوں والے مکمل طور پر مربوط نیٹ ورکس کا استعمال کرتے ہوئے PyTorch یا TensorFlow کے ساتھ حل کریں۔

**ڈسکلیمر**:  
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کا استعمال کرتے ہوئے ترجمہ کی گئی ہے۔ ہم درستگی کے لیے کوشش کرتے ہیں، لیکن براہ کرم آگاہ رہیں کہ خودکار ترجمے میں غلطیاں یا خامیاں ہو سکتی ہیں۔ اصل دستاویز کو اس کی مقامی زبان میں مستند ذریعہ سمجھا جانا چاہیے۔ اہم معلومات کے لیے، پیشہ ور انسانی ترجمہ کی سفارش کی جاتی ہے۔ ہم اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے ذمہ دار نہیں ہیں۔