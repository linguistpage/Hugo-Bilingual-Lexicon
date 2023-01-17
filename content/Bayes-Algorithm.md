---
title: "Bayes Algorithm"

categories: ['Statistics', 'Machine Learning']

tags: ['Bayes', 'Algorithm']

arwords: 'خوارزم بايز'

arexps: []

enwords: ['Bayes Algorithm']

enexps: []

arlexicons: 'خ'

enlexicons: 'B'

authors: ['Ruqayya Roshdy']

translators: ['X']

citations: 'تطبيقات أساسية في المعالجة الآلية للغة العربية'

sources: 'https://smart3arabi.com/'

slug: ""
---

Naive Bayes هي طريقة [تعلم آلي](https://smart3arabi.com/%d8%aa%d8%b9%d9%84%d9%85-%d8%a7%d9%84%d8%a2%d9%84%d8%a9-machine-learning/) تعتمد على الاحتمالات تم اختراعها من قبل العالم توماس بيز (Thomas Bayes). تستخدم لعمل تصنيف للبيانات مثلا تصنيف البريد الالكتروني الوراد إلى مرغوب وغير مرغوب (spam not spam) او تصنيف المشاعر للمستخدمين في وسائل التواصل الاجتماعي عن منتج معين       (Customer Sentiment Analysis) او التنبؤ بحالة الطقس.

هذه الطريقة تفترض ان الخصائص المستخدمة لبناء النموذج منفصلة عن بعض فتَغُّير قيم خاصية معينة لايؤثر على خاصية أخرى. وهي من الخوارزميات السريعة جدا عند عمل التصنيف ولذلك تستخدم في التصنيف اللحظي للبيانات (real time classification). بشكل عام فان المصنف البايزي الساذج  naïve bayes يعمل  مع البيانات الفئوية categorical data بشكل افضل من البيانات الرقمية numerical data.

لفهم Naïve Bayes يجب ان نفهم أولا [الاحتمال المشروط](https://ar.wikipedia.org/wiki/%D8%A7%D8%AD%D8%AA%D9%85%D8%A7%D9%84_%D8%B4%D8%B1%D8%B7%D9%8A).