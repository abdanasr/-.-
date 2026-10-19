# 📱 تطبيق أندرويد لنظام إدارة الكتائب العسكرية — BMS Pro Android
## الدليل الشامل للتشغيل والتثبيت وبناء ملف APK (Enterprise Defense Grade v2.4)

تحتوي هذه الحزمة على **3 مسارات جاهزة للإنتاج** لتحويل وتشغيل نظام **BMS Pro** كتطبيق أندرويد أصيل يعمل دون اتصال بالإنترنت (`Offline-First`):

| المسار | الوصف والمحتويات | متى تستخدمه؟ |
| :--- | :--- | :--- |
| **1. البناء السحابي التلقائي لملف APK (بدون تثبيت برامج)** | ملف `.github/workflows/build-android-apk.yml` يبني ملف `BMS-Pro-Release.apk` تلقائياً عند رفع المجلد إلى GitHub | أسرع طريقة للحصول على ملف `.apk` جاهز للتثبيت على الهواتف والأجهزة اللوحية العسكرية |
| **2. تطبيق Flutter الأصيل (`flutter_bms_pro/`)** | كود Flutter كامل (`lib/main.dart`, `pubspec.yaml`, `AndroidManifest.xml`, `Hive`, `Provider`, `FCM/Crashlytics`) متصل بنفس REST API | للتطوير المخصص الميداني وربط الكاميرا والبصمة الحيوية وبطاقات NFC |
| **3. تطبيق Android Native WebView / Capacitor (`android_native_webview/`)** | مشروع Android Studio (Kotlin + Gradle) يغلف الواجهة التفاعلية الكاملة (`bms_pro_app.html` + `Dexie.js`) داخل APK أصيل | لتشغيل جميع الـ 14 وحدة والـ 52 تقريراً والخريطة التكتيكية فوراً داخل تطبيق أندرويد |

## أولاً: خطوات استخراج ملف APK عبر Flutter محلياً
```bash
cd flutter_bms_pro
flutter pub get
flutter build apk --release --split-per-abi
# ستجد ملف التثبيت في:
# build/app/outputs/flutter-apk/app-arm64-v8a-release.apk
```

## ثانياً: خطوات استخراج ملف APK عبر مشروع Android Studio الأصيل
```bash
cd android_native_webview
./gradlew assembleRelease
# ستجد ملف التثبيت في:
# app/build/outputs/apk/release/app-release.apk
```
