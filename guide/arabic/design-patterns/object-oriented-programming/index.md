---
title: Object Oriented Programming (OOP)
localeTitle: البرمجة الشيئية (OOP)
---
## الخطوط العريضة

*   لماذا كائن المنحى (من الآن فصاعدا اختصار OO)؟
*   مفاهيم OO
*   ماذا بعد؟

## لماذا OO؟

في هذا النموذج ، يتم تمثيل الكيانات كبيانات العالم الحقيقي. على سبيل المثال ، نريد تمثيل كلب. في نموذج OO ، نقوم ببساطة بإنشاء فئة تسمى "dog" ، ونعطيها سمات (اللون ، العمر ، الجنس ، الخ) والسلوك (اللحاء ، الجري ، الأكل ، الخ). يتم تغيير السلوك من خلال "أساليب" (وظائف في كلمات بسيطة) التي تجري تغييرات على السمات.

## مفاهيم OO

ما يجعل برمجة OO قوية هي قدرتها على القيام بما يلي:

*   الإرث
*   تعدد الأشكال
*   التغليف
*   التجريد

في البرمجة الإجرائية ، نقوم ببساطة بإنشاء المتغيرات وتغييرها عند الحاجة. ومع ذلك ، في برمجة OO ، يمكننا حرفيا محاكاة كائنات العالم الحقيقي. يتم تحقيق التغليف عن طريق إنشاء فئة معينة لكيان ، على سبيل المثال الكلب. ثم يتم إنشاء كائنات من هذه الفئة ، والتي ليست سوى مثيلات للفصل. كل كائن له قيم السمات الخاصة به.

مفهوم آخر مفيد للغاية هو أن من الميراث. الفكرة هي أن الطبقة يمكن أن ترث سمات وسلوك من طبقة أساسية. على سبيل المثال ، أثناء إنشاء اللعبة ، لدينا لاعب وعدو. يمكننا إنشاء فئة أساسية تسمى الشخص ، وإعطائها سمات مثل الاسم والعمر والجنس ، وما إلى ذلك. يمكن أن يكون سلوك الشخص هو المشي والقفز. يمكن لللاعب والعدو أن يرث هذه "الصفات" من الشخص ، ويمكن أن يضيف صفات مثل القتل ، والنتيجة ، وتناول الطعام ، إلخ.

هذا يساعد في إعادة استخدام التعليمات البرمجية وجعل لكم هيكل rcode أكثر نظيفة. إخفاء البيانات هو ميزة أخرى رائعة. في OO ، لدينا مفهوم السمات الخاصة والعامة. لا يمكن الوصول إلى السمات الخاصة وتعديلها إلا بطرق تلك الفئة المحددة ، بينما يمكن تعديل البيانات العامة من أي مكان في البرنامج (ضمن النطاق بوضوح).

## ماذا بعد؟

اختر لغة OO ، وابن لعبة أساسية تعتمد على المحطة الطرفية لتوضيح هذه المفاهيم.