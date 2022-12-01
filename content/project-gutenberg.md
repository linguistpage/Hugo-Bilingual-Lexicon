---
title: "Project Gutenberg"
tags: ['gutenberg', 'nltk', 'corpus', 'public domain']
categories: ['preprocessing']
authors: ['Steven Bird']
times: ['60+']
layout: single
---
<style>
p .en {
direction: ltr !important;
font-weight: bold;
}
</style>

<div style="display: flex; flex-direction: row; justify-content: space-around; width: 100%">
<div style="width:50px; height: 50px; background: #282828;"></div>
<div style="width:50px; height: 50px; background: #282828;"></div>
<div style="width:50px; height: 50px; background: #282828;"></div>
<div style="width:50px; height: 50px; background: #282828;"></div>
<div style="width:50px; height: 50px; background: #282828;"></div>
<div style="width:50px; height: 50px; background: #282828;"></div>
</div>

**مشروع غوتنبرغ** (بالإنجليزية: Project Gutenberg) هو مشروع تطوعي يهدف إلى تحويل وتخزين ونشر الأعمال الثقافية في هيئة **رقمية**. أسس المشروع **مايكل هارت** في عام 1971 م وهي أقدم مكتبة إلكترونية موجودة.
معظم المواد الموجودة في المشروع عبارة عن نصوص كاملة ذات **ملكية عامة (Public Domain)** . ويحاول المشروع أن يجعل المواد الموجودة فيه مجانية بقدر المستطاع وبتنسيقات تمكن جميع الحواسيب تقريباً من تشغيلها. *(~ويكيبيديا بتصرف)*


# مدونة غوتنبرغ (Gutenberg Corpus) 

تتضمن مكتبة **NLTK** مجموعات نصية صغيرة من الأرشيف النصي الإلكتروني لمشروع غوتنبرغ **(The Project Gutenberg)** ، والذي يحتوي على حوالي **25000** كتاب إلكتروني مجاني ، مستضاف على [Gutenberg]( http://www.gutenberg.org/) . نبدأ بتحميل حزمة NLTK  في محرر Python، ثم نكتب الأمر <span class="en"> nltk.corpus.gutenberg.fileids </span>،  لعرض معرفات الملفات في هذه المجموعة:

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

دعنا نختار أول هذه النصوص - "إيما" لجين أوستن - ونعين له إسمًا قصيرًا ،مثل  **"إيما"** ، ثم نحاول معرفة عدد الكلمات التي تحتوي عليها المدونة:

```python
>>> emma = nltk.corpus.gutenberg.words('austen-emma.txt')
>>> len(emma)
192427

```

عندما قمنا بتعريف emma ، استدعينا الدالة words() للعنصر gutenberg في الـ corpus الخاص بـ NLTK. ولكن نظرًا لأنه من الصعب كتابة مثل هذه الأسماء الطويلة طوال الوقت ، فإن Python توفر إصدارًا آخر من بيان الإدراج import  ، على النحو التالي:


```python
>>> from nltk.corpus import gutenberg
>>> gutenberg.fileids()
['austen-emma.txt', 'austen-persuasion.txt', 'austen-sense.txt', ...]
>>> emma = gutenberg.words('austen-emma.txt')
```


دعنا نكتب برنامجًا قصيرًا لعرض معلومات أخرى حول كل نص ، من خلال تكرار - looping -  جميع قيم - values -  معرف الملف المقابلة لمعرفات ملف جوتنبرج المدرجة سابقًا ثم حساب الإحصائيات لكل نص. ولكي نعرض الناتج في هيئة موجزة ، سنقرب كل رقم إلى أقرب عدد صحيح باستخدام <span class="en">round()</span>.






















