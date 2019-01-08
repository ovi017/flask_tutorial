ডাইনামিক্যালি ইউআরএল বিল্ডিংয়ের জন্য **url\_for\(\)** ফাংশনের কথা ছাড়া এই বই সম্পূর্ণ হবে না। এই ফাংশনের কাজ বুঝার জন্য কোড লেখা শুরু করি---

```py
from flask import Flask, redirect, url_for
app = Flask(__name__)

@app.route('/admin')
def hello_admin():
   return "You are the Great Admin"

@app.route('/guest/<guest>')
def hello_guest(guest):
   return ('Welcome ",guest)

@app.route('/user/<name>')
def user(name):
   if name =='admin':                         #name টা admin হলে
      return redirect(url_for('hello_admin')) #যাবে localhost:5000/admin ইউআরএল এ
   else:                                      #তা না হলে যাবে localhost:5000/guest/<guest> ইউআরএল এ
      return redirect(url_for('hello_guest',guest = name)) #এখানে guest প্যারামিটারে name আর্গুমেন্ট দেওয়া হয়েছে
                                                           #কারণ hello_guest এর প্যরামিটার guest

if __name__ == '__main__':
   app.run(debug = True)
```

উপরের প্রোগ্রামে user\(name\) ফাংশনটি একটি name ভ্যারিয়েবল ইনপুট নিবে। তারপর তুলনা করে দেখবে এটা** 'admin'** কিনা, যদি হয় তবে **return redirect\(url\_for\('hello\_admin'\)\)** স্টেটমেন্টটি চলবে। এখানে **url\_for\('hello\_admin'\)** জিনিসটা **hello\_admin\(\)** ফাংশনের জন্য যে ইউআরএলটি বরাদ্দ সেই ইউআরএলটি রিটার্ন করবে। আর redirect\(\) ফাংশনটি সেই ইউআরএল এ আমদের নিয়ে যাবে।

এরপর দেখ **url\_for\('hello\_guest',guest = name\)** স্টেটমেনটি, এখানে **'hello\_guest'** দেওয়া হয়েছে কারণ আমরা এবার **hello\_guest\(guest\)** ফাংশনের ইউআরএল বের করতে চাচ্ছি। **guest **প্যরামিটারে **name** আর্গুমেন্ট দেওয়া হয়েছে কারণ **hello\_guest\(guest\)** ফাংশনে **guest** প্যারামিটার আছে।

একটা জিনিস খেয়াল করে দেখেছেন **app.run\(debug = True\)** এ আমি একটা **debug** প্যারামিটারে **True** আর্গুমেন্ট দেওয়া হয়েছে। এর মাধ্যমে আমরা কোডিং এর সময় বাড়তি সুবিধা পাব। কোডিং এর সময় আমাদের অনেক ভুলত্রুটি হয়। তা সংশোধন করে কিন্তু আবার প্রোগ্রামটা\(ফ্লাস্ক স্ক্রিপ্টের কথা বলছি\) রান করতে হয়। কিন্তু এই কাজটা করলে ফ্লাস্ক স্ক্রিপ্ট বারবার রান করতে হয় না। সংশোধন করার পর এমনিতেই রান হতে থাকা স্ক্রিপ্ট পুনরায় প্রথম থেকে রান হওয়া শুরু করে।

পরের অধ্যায়ের জন্য তৈরী থাক......

