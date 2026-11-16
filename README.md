# ShiponLens

## এটার কাজ কী?

ShiponLens একটি Chrome extension, যা ওয়েবপেজের দৃশ্যমান অংশ থেকে লেখা শনাক্ত করে
(OCR)। কোনো ছবি, ভিডিও, ক্যানভাস বা পেজের লেখার চারপাশে মাউস দিয়ে এলাকা নির্বাচন
করলে এটি লেখাটি বের করে দেখায়। শনাক্ত করা লেখা সম্পাদনা ও কপি করা যায়। চাইলে নিজের
তৈরি lookup type ব্যবহার করে মানটি নির্দিষ্ট ওয়েবসাইটে খোলা যায়।

## কীভাবে ব্যবহার করবেন?

1. Chrome-এ `chrome://extensions` খুলে **Developer mode** চালু করুন।
2. **Load unpacked** ক্লিক করে `manifest.json` থাকা project folder নির্বাচন করুন।
3. যে ওয়েবপেজ থেকে লেখা নিতে চান, সেটি খুলুন।
4. ShiponLens toolbar icon-এ ক্লিক করুন অথবা `Ctrl+Z` চাপুন।
5. মাউস দিয়ে লেখার চারপাশে একটি এলাকা নির্বাচন করুন।
6. ফলাফল যাচাই বা সম্পাদনা করুন, তারপর **Copy** চাপুন। OCR-কে আবার চালাতে **Retry**
   ব্যবহার করুন।
7. কোনো মান ওয়েবসাইটে খুঁজতে চাইলে **Options**-এ নিজের lookup type ও link template
   যোগ করুন। এরপর ফলাফল প্যানেলে type নির্বাচন করে **Open in new tab** চাপুন।

## কেন ব্যবহার করবেন?

- ওয়েবপেজে সরাসরি নির্বাচন বা কপি করা যায় না—এমন ছবির বা ভিডিওর লেখা তুলতে।
- Parcel ID, Merchant ID, ফোন নম্বর, সিরিয়াল নম্বরের মতো তথ্য দ্রুত কপি করতে।
- নিজের lookup link ব্যবহার করে শনাক্ত করা মান সংশ্লিষ্ট ওয়েবসাইটে খুঁজতে।
- OCR স্থানীয়ভাবে চালাতে—অ্যাকাউন্ট, API key বা ক্লাউড OCR ছাড়াই।

## কী কী technology ব্যবহার করা হয়েছে?

| Technology | ব্যবহার |
| --- | --- |
| Chrome Extension Manifest V3 | Extension-এর কাঠামো, toolbar action, shortcut ও permission |
| JavaScript | এলাকা নির্বাচন, screenshot crop, OCR flow, লেখা পরিষ্কার ও lookup link তৈরি |
| HTML ও CSS | Result panel, OCR document ও Options পেজ |
| Chrome Extensions API | `activeTab`, `scripting`, `offscreen`, `storage` ও tabs পরিচালনা |
| Tesseract.js 7 | ডিভাইসেই ছবির লেখা শনাক্ত করা |
| WebAssembly SIMD | OCR engine চালানো |
| English `traineddata` model | ইংরেজি লেখার OCR |
| Node.js `assert` | Link logic-এর unit test; test চালাতে আলাদা framework লাগে না |

OCR engine ও ভাষার মডেল extension-এর সঙ্গে bundled, তাই OCR চালাতে ইন্টারনেট লাগে না।
ইন্টারনেট ব্যবহার হয় শুধু আপনি নিজে lookup link খুললে। বর্তমান OCR model ইংরেজি লেখার
জন্য।
