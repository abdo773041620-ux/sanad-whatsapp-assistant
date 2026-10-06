# تشغيل سَنَد

## المتطلبات

مثيل n8n يدعم عقد AI Agent وGoogle Gemini Chat Model وHTTP Request Tool، مفتاح Gemini، ومفتاح Tavily. تحتاج نسخة واتساب أيضاً إلى تطبيق Meta وحساب WhatsApp Business Cloud ورقم مسجّل وصلاحياته. استخدم HTTPS للروابط الخارجية.

## الاعتمادات

1. أنشئ اعتماد Google Gemini في n8n وأدخل مفتاحك، ثم اختره في عقدة النموذج.
2. النموذج المصدّر هو `models/gemini-3.5-flash-lite`. إذا لم يكن متاحاً لحسابك، اختر نموذج محادثة متاحاً يدعم استدعاء الأدوات وأعد التحقق.
3. أنشئ اعتماد Header Auth: الاسم `Authorization`، والقيمة `Bearer YOUR_FULL_TAVILY_API_KEY`؛ استبدل المثال بمفتاحك الكامل دون تكرار بادئته. اختره في Islamic_Search.
4. لا تضع المفاتيح في JSON أو GitHub؛ احتفظ بها داخل اعتمادات n8n.

## نسخة واتساب

1. استورد `workflows/sanad-whatsapp.json` عبر Import from File.
2. اربط اعتمادات WhatsApp Trigger وSend message الخاصة بك.
3. استبدل `REPLACE_WITH_META_PHONE_NUMBER_ID` بمعرّف الرقم المرسل من Meta، وليس رقم الهاتف نفسه.
4. يبقى رقم المستلم ديناميكياً من رسالة WhatsApp Trigger، ونص الرد من `$json.output`.
5. أكمل ربط webhook واشتراك messages وفق إعدادات Meta ونسخة n8n المستخدمة. لا تفترض أن رقم الاختبار متاح لجميع المستخدمين؛ يتطلب مستلمين مصرحاً لهم.
6. انشر الوركفلو واختبر رسالة فعلية من رقم آخر، ثم افحص سجل التنفيذ ووصول الرد.
7. المعالجة الحالية مخصصة للرسائل النصية. عند توسيعها، أضف تصفية للأحداث التي لا تحتوي على messages/text مثل إشعارات الحالة، ومعالجة مناسبة للصوت والصور.

## نسخة الويب

1. استورد `workflows/sanad-web-demo.json` واربط Gemini وTavily.
2. Webhook يستخدم POST والمسار `sanad-demo` وخيار Using Respond to Webhook Node.
3. استبدل Allowed Origins بعنوان أصل موقعك كاملاً: مثل `https://demo.example.com`، دون مسار.
4. المدخل للوكيل هو `={{ $json.body.question }}`؛ ويرجع Respond to Webhook أول عنصر، مثل `{"output":"الإجابة"}`.
5. انشر الوركفلو وانسخ Production URL.
6. في `web/index.html` استبدل قيمة `SANAD_ENDPOINT` برابط الإنتاج. ارفع محتويات `web/` إلى استضافة ثابتة عبر HTTPS مع مجلد fonts.
7. الواجهة ترسل JSON به question وchatInput وlanguage، وتقرأ output أو answer أو text.
8. اختبر من الموقع الفعلي؛ رابط webhook-test يحتاج وضع الاستماع ولا يصلح لتجربة مستمرة.

## التشغيل العام

المفاتيح والحصص والفوترة ومدة الطلب تعتمد على خدماتك. قبل فتح التجربة على نطاق واسع، اضبط حدود الاستخدام ومراقبة التكلفة والتحقق من المدخلات ومعالجة الأخطاء. الواجهة لا تحتوي على مفاتيح API.
