# سَنَد | Sanad

مساعد للمعرفة الإسلامية عبر واتساب، مع واجهة ويب للتجربة. يسترجع نصوصاً من مصادر محددة باستخدام Tavily، ثم يصوغ Gemini الإجابة وفق تعليمات الاستناد إلى المصادر. يجيب بلغة السائل وتبقى الآيات المقتبسة بالعربية.

**التجربة المباشرة:** https://sanad-islamic-search.abdo773041620.chatgpt.site

## البنية الفعلية

- واتساب: WhatsApp Trigger → AI Agent → Send message.
- الويب: Webhook → AI Agent → Respond to Webhook.
- يرتبط الوكيل بـ Google Gemini Chat Model وبأداة Islamic_Search التي تستدعي Tavily Search API.
- البحث مباشر لكل سؤال ديني؛ لا توجد قاعدة متجهات أو فهرسة محلية في هذه النسخة.

## محتويات المستودع

- `workflows/sanad-whatsapp.json`: نسخة واتساب قابلة للاستيراد بعد ضبط الاعتمادات والرقم.
- `workflows/sanad-web-demo.json`: نسخة تجربة الويب.
- `prompts/`: تعليمات الوكيل ووصف الأداة وتعبير جسم طلب البحث، مستخرجة من المشروع.
- `web/`: واجهة الويب الثابتة وخطوطها.
- `docs/SETUP.md`: خطوات التشغيل.
- `docs/VALIDATION.md`: طريقة التحقق والحدود المعروفة.

## المصادر المحددة في أداة البحث

`dawa.center`، `islamic-content.com`، `quranpedia.net`، `dorar.net`، `shamela.ws`.

ترسل الأداة قائمة النطاقات في `include_domains`. تطلب التعليمات استخدام النص المسترجع الكافي، إرفاق المصدر، وعدم تقديم حكم شخصي أو تعويض نقص الدليل من ذاكرة النموذج. هذه تعليمات للوكيل وليست ضماناً آلياً لصحة كل إجابة أو اقتباس.

## الحالة

تم تشغيل نسخة واتساب على رقم Meta التجريبي للمستلمين المصرح لهم. إتاحة الرقم الفعلي للجميع لم تكتمل؛ تجربة الويب هي المسار المتاح للاختبار العام. أزيلت مراجع الاعتمادات ومعرّفات الحساب والرقم وبيانات التنفيذ من ملفات النشر. يتعين إنشاء الاعتمادات لدى المشغّل الجديد.

لا توجد نسب دقة أو أزمنة استجابة معيارية مقاسة. سَنَد مساعد معرفي وليس جهة إفتاء.

## الخصوصية

تمر الأسئلة إلى خادم n8n ومزودي Gemini وTavily. قد تحتفظ هذه الخدمات بسجلات وفق إعداداتها وسياساتها. لا تضف مفاتيح API أو سجلات المحادثات إلى المستودع.

## English

Sanad is an Islamic knowledge assistant with WhatsApp and web-demo workflows. It uses live Tavily retrieval from five configured domains and a Gemini agent. Replies follow the question language, while quoted Quranic text remains Arabic. Import the workflows, reconnect your own credentials, configure the sender phone ID or web endpoint, and publish the appropriate workflow. See `docs/SETUP.md`. Source grounding and abstention are prompt-based; independent citation and theological review are still needed.
