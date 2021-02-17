 # JavaScript Useful Array Functions

## 1. ```array.map()```

যখন কোন অ্যারেতে ```.map()``` ব্যবহার করা হয়, ইহা নতুন অ্যারে বানাবে, অরিজিনাল অ্যারে এর মডিফাইড ভারসন। ```.map()``` এ্কটি ফাংশন নেয়, যা ওই অ্যারে এর প্রতিটা আইটেম কে লুপ করবে এবং পরিবর্তন করবে্ প্রয়োজন অনুযায়ী। 

```.map()``` মেথড টা কাজে লাগে যখন আমরা কোন অ্যারে এর প্রতিটা আইটেম কে আপডেট করতে চাই এবং নতুন একটি অ্যারে তে সংরক্ষণ  করতে চাই। 

_চলুন হাত নোংরা করিঃ_

ধরে নেই আমাদের একটি car এর অ্যারে আছেঃ 

 ``` const cars = ['BMW', 'AUDI', 'COROLA']; ```
 
 আমরা চাই প্রতিটা গাড়ি এর পর একটি বাক্য জুরে দিতে। চলুন দেখি এই কাজটি কিভাবে করতে পারি ```.map()``` মেথড দিয়ে। 
 
```
const coolCars = cars.map( car => {
  return `{$car is a cool car}`;
} );

// result: ['BMW is a cool car', 'AUDI is a cool car', 'COROLA is a cool car']
```

অস্থির!!! ```.map()``` মেথড টি নতুন  এ্কটি অ্যারে তৈরি করল এবং প্রতিটা আইটেম এ নতুন টেক্সট জুরে দিল। 

চলুন কতগুলো ```object``` এর  একটি অ্যারে কে মডিফাই করি ```.map()``` মেথড দিয়ে। ধরে নেই আমাদের ্কাছে কত গুলো গাড়ির টেক্স প্রাইস বিহীন অব্জেক্ট রয়েছে এবং আমরা চাচ্ছি প্রটি টা ```car```  এ ```priceWithTax``` যোগ করতে। 

```

const cars = [
  { brand: 'Porshe', price: 5000 },
  { brand: 'Audi', price: 4000}
];

const carsWithTax = cars.map(car => {
  // যেহেতু আমরা অব্জেক্ট রিটার্ন করতে চাই
  return {
    ...car,  // অরিজিনাল কার অব্জেক্ট কে রিটার্ন করবে
    priceWithTax: car.price * 1.4  // এবং নতুন একটি ভ্যালু যোগ করবে সাথে ট্যাক্স সহ প্রাইস এর 
  }
});

// result: 
[
  {brand: 'Porshe', price: 5000, priceWithTax: 7000},
  {brand: 'Audi', price: 4000, priceWithTax: 5600}
]

```
### কখন ```.map()``` ব্যবহার করব?
আপনি যখন কোন অ্যারে এর আইটেম কে পরিবর্তন করতে চান এবং পরিবর্তিত ফলাফল নতুন একটি অ্যারে তে সংরক্ষণ করতে চান।  কলব্যাক ফাংশনে কন্ডিশন অনুযায়ী এক বা একাধিক অথবা সব ডাটা কে আপনি পরিবর্তন করতে পারবেন। মনে রাখবেন ```.map()``` মেথড সম্পূর্ণ নতুন একটি অ্যারে রিটার্ন করবে,পূর্বের অ্যারে তে কোন পরি্বর্তন করবে না। 

আর জানতে ঢুঁ মারুন [এইখানে](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

## 2. ```array.filter()```

নামেই  পরিচয় পাওয়া যাচ্ছে এই মেথড বা ফা্ংশনটি কি কাজ করে। ```.filter()``` মেথডটি নির্দিষ্ট শর্তের ভিত্তিতে  আরের আইটেমগুলো রিটার্ন করে। ```.map()``` মেথড এর মত ```.filter()``` মেথডও নতুন একটি মডিফাইড অ্যারে তৈরি করে, মূল অ্যারে এর কোন পরিবর্তন করে না। 
যেমন আমরা কোনও গাড়ির মূল্যের উপরে একটি নির্দিষ্ট মানের উপরে ভিত্তি করে গাড়ির অ্যারে ফিল্টার করতে পারি।
গাড়ির অ্যারেঃ 
```
const cars = [
 {brand: "Porsche", price: 100000},
  {brand: "Audi", price: 80000},
  {brand: "Toyota", price: 30000}
];

```

এখন ধরা যাক 40,000 বা তার বেশি মূল্যের সমস্ত গাড়ি ব্যয়বহুল। আমরা ```.filter()``` মেথড দিয়ে সস্তা এবং ব্যয়বহুল গাড়ি বের করতে পারি। 

```
const expensiveCars = cars.filter( car => car.price >= 40000);
const cheapCars = cars.filter(car => car.price < 40000);
// Result - Expensive Cars
[
  {brand: "Porsche", price: 100000},
  {brand: "Audi", price: 80000}
];// Result - Cheap Cars
[
  {brand: "Toyota", price: 30000}
];
```
এইখানে অ্যারে এর  প্রতিটি আইটেমকে চেক করা হয়েছে যদি কন্ডিশন কে ফুলফিল করে তাহলে নতুন অ্যারে তে রিটার্ন করা হয়েছে। 

### কখন ```.filter()``` ব্যবহার করব? 
যখন আপনি কোন কন্ডিশন এর উপর ভিত্তি করে অ্যারে থেকে আইটেম কে বাদ দিতে চান। ```.map()``` মেথড কিন্তু কোন আইটেম কে বাদ দেয়নি যেখানে ```.filter()``` মেথড আইটেম কে বাদ দিয়ে দেয়।

আর জানতে ঢুঁ মারুন [এইখানে](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
