## 1. PostgreSQL কী?

PostgreSQL হলো একটি বিনামূল্যের ও ওপেন সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম। এটি মূলত এমন একটি সফটওয়্যার যা ডেটা সংরক্ষণ, সাজানো এবং প্রয়োজনে খুঁজে পেতে সাহায্য করে। যখন বিশাল পরিমাণ বিস্তারিত তথ্য গুছিয়ে ও নিরাপদভাবে সংরক্ষণের প্রয়োজন হয়, তখন PostgreSQL ব্যবহার করাটা সবচেয়ে উপযুক্ত।

#### PostgreSQL যা করতে পারে:

✅ তথ্য সংরক্ষণ করতে,

✅ বড় বড় তথ্য সেট ম্যানেজ করতে,

✅ খুব দ্রুত তথ্য খুঁজে বের করতে,

✅ একাধিক টেবিলের মধ্যে সম্পর্ক (Relationship) তৈরি করতে 

### PostgreSQL-এর গুরুত্বপূর্ণ ফিচার:

✅ ওপেন সোর্স: একেবারে ফ্রি ও কাস্টমাইজ করা যায়,

📚 রিলেশনাল ডেটাবেস: তথ্য গুছিয়ে টেবিলে রাখা যায় (যেমন: Excel),

🧠 SQL ব্যবহার করে প্রশ্ন করা যায়	যেমন: কে সবচেয়ে বেশি নাম্বার পেয়েছে?,

🔗 সম্পর্ক তৈরি করা যায়	যেমন: ছাত্র ও তার মার্কসের মধ্যে সম্পর্ক,

📦 JSON সাপোর্ট করে	জটিল ডেটা টাইপও রাখা যায়,

🔒 নিরাপদ ইউজার পারমিশনসহ ডেটা সুরক্ষা,

📈 স্কেলযোগ্য ছোট অ্যাপ থেকে শুরু করে বড় ব্যাংকিং সিস্টেমেও চলে

### PostgreSQL কোথায় কোথায় ব্যবহার হয়?

#### PostgreSQL ব্যবহৃত হয়:

✅ ওয়েব অ্যাপ্লিকেশন (যেমন: Twitter, Reddit)

✅ ব্যাংকিং সিস্টেম

✅ ই-কমার্স ওয়েবসাইট

✅ সরকারি অফিস ও হাসপাতালের তথ্য সংরক্ষণে

✅ ডেটা বিশ্লেষণ বা রিপোর্টিং-এ

### 🏪 উদাহরণ: একটি অনলাইন দোকানের প্রোডাক্ট ডেটা ম্যানেজমেন্ট

ধরো, তোমার একটা ইলেকট্রনিক্স দোকান আছে যেখানে হাজার হাজার পণ্য (products) আছে। এখন তুমি PostgreSQL ব্যবহার করে সেই ডেটা সংরক্ষণ করবে ও CRUD অপারেশন করবে।

#### ✅ ১. 📦 products টেবিল তৈরি করো:
```
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  description TEXT,
  price NUMERIC(10, 2),
  quantity INT,
  category VARCHAR(50)
);
```
#### 📝 এখানে:

name = পণ্যের নাম

description = পণ্যের বিস্তারিত

price = মূল্য

quantity = স্টকে কত আছে

category = কোন ক্যাটাগরির পণ্য (যেমন Mobile, Laptop)

#### ✅ ২. ➕ নতুন পণ্য যোগ করো (Create):
```
INSERT INTO products (name, description, price, quantity, category)
VALUES ('Samsung Galaxy S23', 'Latest model with AMOLED display', 899.99, 20, 'Mobile');
```

#### ✅ ৩. 📖 সব পণ্য দেখো (Read):
```
SELECT * FROM products;
```

#### ✅ ৪. ✏️ পণ্যের দাম ও স্টক আপডেট করো (Update):
```
UPDATE products
SET price = 849.99, quantity = 15
WHERE id = 1;
```
#### ✅ ৫. ❌ একটি পণ্য ডিলিট করো (Delete):
```
DELETE FROM products
WHERE id = 1;
```


## 2. Primary Key (প্রাইমারি কি) কী? এবং Foreign Key (ফরেন কি) কী?

 #### Primary Key:

Primary Key হচ্ছে এমন  কলাম  যার মান প্রতিটি রেকর্ডের (row) জন্য একটি ইউনিক আইডেন্টিফায়ার হয়।

✅ এটি অবশ্যই ইউনিক (দু'বার একই মান রাখা যাবে না)

✅ এটি null হতে পারে না

✅ প্রতিটি টেবিলের মধ্যে শুধু একটি Primary Key থাকতে পারে

#### কি কাজ করে?

✅ Primary Key হচ্ছে টেবিলের প্রতিটি রেকর্ডকে সুনির্দিষ্টভাবে শনাক্ত করার জন্য।

✅ এটি এমন একটি ফিল্ড (বা একাধিক ফিল্ড), যার মাধ্যমে প্রতিটি রো (row) আলাদা করে চেনা যায়।

#### উদাহরণ (Primary Key):
```
CREATE TABLE products (
  product_id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  price NUMERIC(10, 2)
);
```
product_id এখানে Primary Key।

প্রতিটি পণ্যের জন্য এটি ইউনিক হবে: 1, 2, 3...

#### Foreign Key: 

 Foreign Key এমন একটি কলাম যা অন্য একটি টেবিলের Primary Key এর সাথে সম্পর্কযুক্ত (Link) থাকে।

✅ এক টেবিলের রেকর্ডের সাথে অন্য টেবিলের রেকর্ডকে সংযুক্ত করে

✅ এটি টেবিলগুলোর মধ্যে সম্পর্ক (Relationship) তৈরি করে

✅ এটি ডেটার ইন্টিগ্রিটি বজায় রাখে (ভুল ডেটা ঢুকতে দেয় না)


#### ✅ কাজের ধরন:
তুমি যদি চাও orders টেবিল যেন customers টেবিলের সাথে যুক্ত থাকে, তবে orders.customer_id হবে customers.customer_id এর foreign key।

#### ✅ বৈশিষ্ট্য (Features):

1. Parent-Child সম্পর্ক তৈরি করে
→ customers = parent, orders = child

2. Referential Integrity বজায় রাখে
→ যদি parent-এ কোন id না থাকে, child-এ সেই id ঢুকবে না।

3. ON DELETE / ON UPDATE rules
→ তুমি নির্ধারণ করতে পারো, parent রেকর্ড ডিলিট হলে child-এ কি হবে।


#### উদাহরণ (Foreign Key):
```
CREATE TABLE customers (
  customer_id SERIAL PRIMARY KEY,
  name VARCHAR(100)
);

CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  order_date DATE,
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```
orders টেবিলের customer_id কলামটি হচ্ছে Foreign Key।







