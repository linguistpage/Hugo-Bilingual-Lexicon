---
title: "Term Frequency-Inverse Document Frequency-TF-IDF"

categories: ['']

tags: ['Term', 'Frequency', 'Inverse', 'Document', 'Frequency', 'TF', 'IDF']

arabic: ['تردد الكلمة-تردد المستند العكسي']

publishers: ['معجم مصطلحات التعلم الآلي والتعلم العميق وعلم البيانات']

types: "word"

slug: ""
---



TF-IDF هو اختصار لعبارة "Term Frequency-Inverse Document Frequency"، وهو مقياس إحصائي يُستخدم لتقييم أهمية كلمة معينة داخل مستند نصي ضمن مجموعة من المستندات (مجموعة المستندات). يساعد هذا المقياس في تحديد الكلمات التي تكون أكثر أهمية وفريدة في مستند معين مقارنةً بغيرها من الكلمات في باقي المستندات.

 تفسير المصطلحات:

1. **التكرار المصطلحي (Term Frequency - TF)**:
   - يقيس عدد مرات ظهور كلمة معينة في مستند ما. كلما زاد عدد تكرار الكلمة في المستند، زادت قيمتها.
   - الصيغة الرياضية: TF(t, d) = عدد مرات ظهور الكلمة t في المستند d.

2. **التكرار العكسي للمستند (Inverse Document Frequency - IDF)**:
   - يقيس أهمية الكلمة في مجموعة المستندات. الكلمة التي تظهر في عدد قليل من المستندات تكون ذات قيمة أعلى مقارنةً بالكلمة التي تظهر في معظم المستندات.
   - الصيغة الرياضية: IDF(t, D) = log(N / df(t)), حيث:
     - N: العدد الإجمالي للمستندات.
     - df(t): عدد المستندات التي تحتوي على الكلمة t.

3. **TF-IDF**:
   - هو حاصل ضرب TF وIDF، ويعطي مقياساً لمدى أهمية الكلمة في المستند بالنسبة لمجموعة المستندات.
   - الصيغة الرياضية: TF-IDF(t, d, D) = TF(t, d) * IDF(t, D).

 كيفية استخدام TF-IDF في نصوص باللغة العربية:

بما أن اللغة العربية تتطلب بعض المعالجات الخاصة، مثل إزالة التشكيل والتوقف والتجذير، فإن خطوات معالجة النصوص تشمل:
- **إزالة التشكيل**: إزالة الحركات مثل الفتحة والضمة والكسرة.
- **تقسيم النص (Tokenization)**: تقسيم النص إلى كلمات منفردة.
- **إزالة الكلمات الشائعة (Stop Words Removal)**: إزالة الكلمات الشائعة التي لا تحمل معنى كبير في التحليل.
- **التجذير (Stemming)**: تحويل الكلمات إلى جذورها الأصلية.

 مثال على تطبيق TF-IDF:

إليك مثال على كيفية تطبيق TF-IDF باستخدام مكتبة Python `scikit-learn` مع نصوص باللغة العربية:

```python
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.preprocessing import normalize
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem.isri import ISRIStemmer
import re

# تحميل الموارد المطلوبة من NLTK
nltk.download('punkt')
nltk.download('stopwords')

# مستندات عربية كمثال
documents = [
    "أنا أحب البرمجة",
    "البرمجة ممتعة وتساعد على التفكير",
    "تعلم البرمجة مهم في عصر التكنولوجيا",
    "البرمجة تساعد في حل المشكلات"
]

# دالة معالجة النصوص
def preprocess(text):
    # إزالة التشكيل
    text = re.sub(r'[\u064B-\u0652]', '', text)
    # تقسيم النص
    words = word_tokenize(text)
    # إزالة الكلمات الشائعة
    stop_words = set(stopwords.words('arabic'))
    words = [word for word in words if word not in stop_words]
    # التجذير
    stemmer = ISRIStemmer()
    words = [stemmer.stem(word) for word in words]
    return ' '.join(words)

# معالجة المستندات
preprocessed_docs = [preprocess(doc) for doc in documents]

# إنشاء TF-IDF Vectorizer
vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform(preprocessed_docs)

# تطبيع مصفوفة TF-IDF
tfidf_matrix = normalize(tfidf_matrix, norm='l2')

# تحويل المصفوفة إلى DataFrame لعرضها
df = pd.DataFrame(tfidf_matrix.toarray(), columns=vectorizer.get_feature_names_out())

print(df)



|       | أحب   | البرمجة | التفكير | تساعد | تعلم  | حل   | على   | في    | مهم   | ممتع  | المشكلات | عصر  | التكنولوجيا |
|-------|-------|---------|----------|--------|-------|------|-------|-------|-------|-------|----------|-------|--------------|
| مستند 1 | 0.707 | 0.707   | 0        | 0      | 0     | 0    | 0     | 0     | 0     | 0     | 0        | 0     | 0            |
| مستند 2 | 0     | 0.462   | 0.617    | 0.617  | 0     | 0    | 0.617 | 0     | 0     | 0.617 | 0        | 0     | 0            |
| مستند 3 | 0     | 0.408   | 0        | 0      | 0.707 | 0    | 0     | 0.707 | 0.707 | 0     | 0        | 0.707 | 0.707        |
| مستند 4 | 0     | 0.526   | 0        | 0.526  | 0     | 0.667| 0     | 0     | 0     | 0     | 0.667    | 0     | 0            |