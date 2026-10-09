ELECTRIC KNOWLEDGE BY RIPON — ANDROID PROJECT (v1.0)
====================================================

এই ZIP-এ কী আছে?
- www/ : আপনার ওয়েব অ্যাপের ফাইল
- package.json : Android wrapper তৈরির dependency
- capacitor.config.json : অ্যাপের নাম ও ID
- .github/workflows/build-apk.yml : GitHub-এ APK বানানোর স্বয়ংক্রিয় কাজ

সবচেয়ে সহজ পদ্ধতি: GitHub দিয়ে APK বানানো (কম্পিউটারে Android Studio লাগবে না)
---------------------------------------------------------------------------------
প্রয়োজন: GitHub অ্যাকাউন্ট এবং এই ZIP ফাইল extract করার ব্যবস্থা।

১) ZIP extract করুন।
২) GitHub.com-এ লগইন করে একটি নতুন repository তৈরি করুন।
   Repository name: electric-knowledge-by-ripon
   শুরুতে Public বেছে নিলে সেটআপ সহজ হবে। ব্যক্তিগত রাখতে চাইলে Private-ও করা যায়।
৩) repository পেজে Add file → Upload files নির্বাচন করুন।
৪) extract করা ফোল্ডারের ভেতরের সব ফাইল ও ফোল্ডার আপলোড করুন।
   খেয়াল রাখবেন: index.html যেন repository-র www/index.html-এ থাকে,
   আর .github/workflows/build-apk.yml-ও আপলোড হয়।
   কিছু ব্রাউজার .github-এর মতো hidden folder আপলোড করে না। এমন হলে GitHub-এ
   Add file → Create new file দিয়ে .github/workflows/build-apk.yml তৈরি করে
   ZIP-এর একই নামের ফাইলের লেখা কপি করে Save করুন।
৫) Commit changes চাপুন।
৬) repository-র Actions ট্যাব খুলুন।
৭) “Build Android APK” workflow নির্বাচন করুন।
৮) Run workflow → Run workflow চাপুন।
৯) কয়েক মিনিট অপেক্ষা করুন; কাজটি সবুজ ✓ হলে সেটি সফল।
১০) সেই run-এ নিচে Artifacts অংশে
    Electric-Knowledge-by-Ripon-debug-APK নামের ফাইলটি ডাউনলোড করুন।
১১) APK ZIP ডাউনলোড হলে extract করে app-debug.apk ফাইল Android ফোনে পাঠান।
১২) APK-তে চাপুন। ফোন চাইলে শুধু এই ফাইলের জন্য “Install unknown apps” অনুমতি দিন।
    ইনস্টল শেষে অনুমতি বন্ধ করে দিতে পারেন।

যদি Actions ট্যাব না দেখায়:
- repository-র Settings → Actions → General-এ গিয়ে Actions চালু আছে কি না দেখুন।
- workflow ফাইলটি ঠিক এই পথে আছে কি না যাচাই করুন:
  .github/workflows/build-apk.yml
- Actions run-এ লাল X হলে সেটিতে চাপ দিয়ে error log দেখুন।

লোকাল কম্পিউটারে APK বানাতে (বিকল্প):
১) Node.js 20 LTS এবং Android Studio ইনস্টল করুন।
২) এই project folder-এ Terminal/Command Prompt খুলুন।
৩) চালান:
   npm install
   npx cap add android
   npx cap sync android
৪) Android Studio-তে android ফোল্ডার খুলুন।
৫) Gradle sync সম্পন্ন হলে Build → Build Bundle(s) / APK(s) → Build APK(s) নির্বাচন করুন।
৬) debug APK সাধারণত android/app/build/outputs/apk/debug/app-debug.apk-এ থাকবে।

গুরুত্বপূর্ণ সীমাবদ্ধতা:
- এটি debug APK; নিজের ফোনে পরীক্ষা করার জন্য। Play Store বা জনসাধারণের কাছে প্রকাশের আগে
  release signing, privacy review, app testing ও Play Console-এর নিয়ম পূরণ করতে হবে।
- APK বানানো মানেই Play Store-এ প্রকাশ করা নয়।
- অ্যাপের ক্যালকুলেটরগুলো শিক্ষামূলক আনুমানিক হিসাব। বাস্তব electrical installation-এ
  local code, manufacturer data, cable ampacity, protective coordination এবং safety যাচাই জরুরি।
- নিজের GitHub repository-তে কখনো password, signing key বা secret token আপলোড করবেন না।
- এই workflow প্রতি build-এ নতুন Android wrapper তৈরি করে; project build log-এ কোনো error
  এলে log-এর শেষের অংশ কপি করে সাহায্য চাইতে পারেন।
