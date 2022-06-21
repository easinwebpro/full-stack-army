# Lecture 10 - Asynchronous Programming in JavaScript & Lecture 11 - Async Iterator & Generator in JavaScript | Project Requirements

## Introduction

আজকের লেকচার বেসিক্যালি Asynchronous Programming নিয়ে। এখানে মূলত ১০ এবং ১১ এই দুইটা ক্লাসের লেকচার একসাথে মার্জ করা হবে। আজকের এজেন্ডাগুলো একটু দেখে নিই।

- Understand Asynchronous Programming
- Event Loop
- Ways we can handle Asynchronous Tasks
  - Callback
  - Promise
  - Async Await
  - Async Iterator
  - Async Generator

একে একে সব বিষয় আলোচনা করা হবে।

## Understand Asynchronous Programming

ধরুন আপনি ব্যাংকে লাইনে দাঁড়িয়ে আছেন। সামনের জনের কাজ শেষ হলেই পরের জনের কাজ শুরু হবে। একে বলা হচ্ছে ব্লকিং। বর্তমান কাজ শেষ না হলে পরবর্তী কাজে যাওয়া যাবে না। আপনিও লাইনে দাঁড়িয়ে থাকতে থাকতে বিরক্ত হয়ে যাবেন।

বর্তমানে কিছু কিছু ব্যাংকে এমন সার্ভিস চালু হয়েছে, আপনি ঢুকবেন, একটা টোকেন কালেক্ট করবেন, এরপর ওয়েটিং লাউঞ্জে অপেক্ষা করবেন। আপনার সিরিয়াল যখন আসবে তখন আপনাকে ডাকা হবে। আপনার আর লাইনে দাঁড়িয়ে থাকতে হলো না। প্রথম সিস্টেমে আপনি ব্যাংকে ঢুকলে আর অন্য কোনো কাজ করা সম্ভব হতো না। কিন্তু এখন আপনি টোকেন নিয়ে বসে নেট ব্রাউজিং করতে পারছেন, ল্যাপটপে প্রয়োজনীয় কাজ সারতে পারছেন, বা বাইরে থেকে কিছু ছোট কাজ সেরে আসতেও পারছেন। কারণ আপনি আপনার সিরিয়াল জানেন, আর মোটামুটি কত সময় লাগতে পারে তাও আইডিয়া করতে পারছেন। এটাকে বলা হয় নন ব্লকিং। আর যে ওয়ে সেটাকে বলা হচ্ছে Asynchronous way।

আমরা সিনক্রোনাস প্রোগ্রামিং এর একটা উদাহরণ দিই।

```js
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
console.log(6);
console.log(7);
console.log(8);
console.log(9);
console.log(10);
```

এখানে ততক্ষণ পর্যন্ত ১০ এক্সিকিউট হবে না যতক্ষণ না ৯ পর্যন্ত এক্সিকিউট হয়। এটাকে বলে সিনক্রোনাস প্রোগ্রামিং। একটার পর একটা লাইন সিরিয়ালি এক্সিকিউট হবে।