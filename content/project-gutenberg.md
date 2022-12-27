---
title: "Project Gutenberg"
tags: ['gutenberg', 'nltk', 'corpus', 'public domain']
categories: ['preprocessing']
authors: ['Steven Bird']
times: ['60+']
lexicons: ['مشروع غوتنبرج']
layout: single
---
<style>
li {
  list-style-type: "- ";
  list-style-position: inside;
}
</style>

<br>

### مشروع غوتنبرج (Project Gutenberg)

- **مشروع غوتنبرغ** (بالإنجليزية: Project Gutenberg) هو مشروع تطوعي يهدف إلى تحويل وتخزين ونشر الأعمال الثقافية في هيئة **رقمية**.
- أسس المشروع **مايكل هارت** في عام 1971 م وهي أقدم مكتبة إلكترونية موجودة.
- معظم المواد الموجودة في المشروع عبارة عن نصوص كاملة ذات **ملكية عامة (Public Domain)** .
- ويحاول المشروع أن يجعل المواد الموجودة فيه مجانية بقدر المستطاع وبتنسيقات تمكن جميع الحواسيب تقريباً من تشغيلها.


 *المصدر: ويكيبيديا بتصرف*


### مدونة غوتنبرغ (Gutenberg Corpus) 

- تتضمن مكتبة **NLTK** مجموعات نصية صغيرة من الأرشيف النصي الإلكتروني لمشروع غوتنبرغ **(The Project Gutenberg)**
- يحتوي على حوالي **25000** كتاب إلكتروني مجاني
- مستضافة على الموقع [Gutenberg]( http://www.gutenberg.org/)


### تمرين عملي:

- من الممكن تحميل حزمة أدوات **NLTK** في محرر **Python** ، ثم كتابة الأمر **nltk.corpus.gutenberg.fileids**،  لعرض ملفات **Gutenberg** النصية عن طريق الأكواد التالية:

```python
>>> import nltk
>>> nltk.corpus.gutenberg.fileids()
['austen-emma.txt', 'austen-persuasion.txt', 'austen-sense.txt', 'bible-kjv.txt',
'blake-poems.txt', 'bryant-stories.txt', 'burgess-busterbrown.txt',
'carroll-alice.txt', 'chesterton-ball.txt', 'chesterton-brown.txt',
'chesterton-thursday.txt', 'edgeworth-parents.txt', 'melville-moby_dick.txt',
'milton-paradise.txt', 'shakespeare-caesar.txt', 'shakespeare-hamlet.txt',
'shakespeare-macbeth.txt', 'whitman-leaves.txt']
```

- إذا اخترنا أول هذه النصوص - "إيما" لجين أوستن - ونعين له إسمًا قصيرًا (أي variable)،مثل  **"emma"** فسوف نستطيع معرفة عدد الكلمات التي تحتوي عليها المدونة\القصة:

```python
>>> emma = nltk.corpus.gutenberg.words('austen-emma.txt')
>>> len(emma)
192427

```

- عندما قمنا بتعريف **emma** ، استدعينا الدالة **words()** للعنصر **gutenberg** في الـ **corpus** الخاص بـ **NLTK**. ولكن نظرًا لأنه من الصعب كتابة مثل هذه الأسماء الطويلة طوال الوقت ، فإن **Python** توفر طريقةً أخرى من بيان الإدراج **import**  ، على النحو التالي:


```python
>>> from nltk.corpus import gutenberg
>>> gutenberg.fileids()
['austen-emma.txt', 'austen-persuasion.txt', 'austen-sense.txt', ...]
>>> emma = gutenberg.words('austen-emma.txt')
```


















