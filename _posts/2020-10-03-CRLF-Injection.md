---
title: CRLF Injection - ثغرة حقن سطر جديد
author: Khaled Mohamed [xElkomy]
categories: CRLF
tags: ["CRLF","Carriage Return Line Feed"]
math: true
---

# CRLF Injection

![CRLF](/assets/img/crlf-injection.jpg)

# البداية :-

السلام عليكم في البداية كدا هنتكلم عن ثغرة تسميتها بالعربية

`تغذية خط إرجاع أول السطر` - Carriage Return Line Feed

بمعني انك بتضيف سطر جديد عبارة عن هيدر او محتوي للصفحة عن طريق رابط الموقع 

الثغرة بتم بسبب ان الموقع بيتحققش من المدخلات في الرابط من مدخلات اليوزر اذا كان 
POST - GET Requests

لان بيضيف مدخلات اليوزر علي محتوي الريسبونس فالمخترق او مختبر الاختراق في المنطقة دي الي بيعمله انه بيضيف هيدر جديد يضيف بيه كوكيز جديدة او ان يضيف محتوي للصفحة يوصل منه لحقن محتوي في الصفحة

الي ممكن يحدث بسبب بعض الثغرات كمثال
XSS - Cross Site Scripting

CSRF - Cross Site Request Forgery

او بعض الثغرات الاخري علي حسب السيناريو الموجود في الموقع المصاب الهكر بيفكر بعد اما يعرف ان فيه خطا في استلام المعلومات من اليوزر بعد كدا بيبدا يستغل فيها وبيختلف السيناريو عن الموقع وموقع

## خطورة الثغرة:-

زي ماقولنا انها بتختلف من سيناريو للتاني ولكن في العموم الثغرة ببسطة بتسمحلك كمهاجم تحقن رؤس ارسالات او الريكوستات يعني او محتوي في الصفحة توصل منه لما ذكر فوق او اكثر لان السيناريو بيختلف من موقع للاخر والخطورة الخاصة بالثغرة كتقيم من متوسط لصعب

## ازاي تكتشف الثغرة ؟

هنا بقا انت بتمسك التارجت الخاص بيك و اول ماتجرب جرب بعد اول سلاش في الموقع تضيف سطر جديد

عبارة عن ترميز الروابط او المعروف  URL Encode %0d CR and %0a LF. 

كمثال لاضافة كوكيز في الريكوست 

%0d%0aSet-Cookie:fuzz=fuzz

فانت حضرتك بعد اما بتضيف الي فوق دا في برامتر ان كان او بعد سلاش ما تشوف الريسبونس اذا لقيت 

في فعلا كوكيز جديدة انضافت الي الريسبونس اسمها Fuzz والمحتوي بتاعها Fuzz

يبقا انت كدا عرفت ان في ثغرة حقن سطور هنا وانت استغلتها بس استغلال متوسط 

فالو انت حضرتك عايز ترفع الخطورة من متوسط لصعب الي المطلوب منك هو انك تضيف محتوي للصفحة ياثر لو مستخدم في الموقع فتح الرابط دا انه يحصل Takeover 

علي الاكونت بتاعه ودا زي ماقولنا فوق بيختلف من سيناريو للتاني فانت تشوف السيناريو الي معاك 
وتكون عندك خبرة انك تقيم بين الفرق بين الخطورة العامة للثغرة

والخطورة الخاصة للسيناريو الي معاك لانك لو متابع ممكن تكون شوفت واحد في يوم بلغ

Reflected XSS 

واخذ عليها بونتي توصل ل3000 دولار واكتر وانت قعدتك تستغرب دا لي دا بيبقا بسبب

ان الثغرة في السيناريو دا صعبة علي الموقع وحجمه وحجم مستخدميه ودا الفرق بين الخطورة العامة والخطورة الخاصة بالثغرات

## الحماية من هذة الثغرة :-

في بعض الاحيان بيبقا السبب بان الموقع بيستلم قيمة من المستخدم للكوكيز

الحماية ممكن بانك لاتسق في مايدخله المستخدم داخل رؤس الموقع او الهيدرز اي ان يكن 

او انك تستخدم لفلترة لمثل هذة المدخلات او انك تحدث لغة البرمجة الخاصة بالموقع الي اصدار او لغة اخري لاتسمح بحقن هذة الرؤس بالافتراضي الخاص بها

## بعض المصادر :-

### بعض الحمولات الخاصة بالثغرة

[`https://github.com/cujanovic/CRLF-Injection-Payloads/blob/master/CRLF-payloads.txt`](https://github.com/cujanovic/CRLF-Injection-Payloads/blob/master/CRLF-payloads.txt)

### وهذة الاداة جديدة وسريعة في الاستغلال لهذة الثغرة اي معني اصح مش استغلال فحص ان كانت موجودة او لا ممكن في ليستة او موقع واحد تتشيك عليه

[`https://github.com/dwisiswant0/crlfuzz`](https://github.com/dwisiswant0/crlfuzz)

### بعض الريورتات لهذة الثغرة :-

[`https://hackerone.com/reports/446271`](https://hackerone.com/reports/446271)

[`https://hackerone.com/reports/191380`](https://hackerone.com/reports/191380)

[`https://hackerone.com/reports/192749`](https://hackerone.com/reports/192749)

[`https://hackerone.com/reports/25275`](https://hackerone.com/reports/25275)

[`https://hackerone.com/reports/39261`](https://hackerone.com/reports/39261)

[`https://hackerone.com/reports/181939`](https://hackerone.com/reports/181939)

[`https://hackerone.com/reports/154306`](https://hackerone.com/reports/154306)

### الشخص دا من افضل الناس الي تتابعهم بالخصوص علشان الثغرة هذة

[`https://twitter.com/Black2Fan`](https://twitter.com/Black2Fan)

### ودا كان ملف بي دي اف هو عامله من مايقارب السنتين من اجل ثغرة هذة الثغرة

[`https://2018.zeronights.ru/wp-content/uploads/materials/4 ZN2018 WV - BugBounty automation.pdf`](https://2018.zeronights.ru/wp-content/uploads/materials/4%20ZN2018%20WV%20-%20BugBounty%20automation.pdf)

### Acunetix

[`https://www.acunetix.com/websitesecurity/crlf-injection/`](https://www.acunetix.com/websitesecurity/crlf-injection/)

### CRLF Injection Playbook

[`https://medium.com/cyberverse/crlf-injection-playbook-472c67f1cb46`](https://medium.com/cyberverse/crlf-injection-playbook-472c67f1cb46)

### Forcing Firefox to Execute XSS Payloads during 302 Redirects

[`https://www.gremwell.com/firefox-xss-302`](https://www.gremwell.com/firefox-xss-302)
