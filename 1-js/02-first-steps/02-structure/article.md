# ساختار کد

اولین چیزی که خواهیم آموخت نحوه ساخت بلاکِ کد است.

## Statements

Statement ها دستورات و کدهایی هستند که باعث وقوع عملی می‌شوند.

پیش از این Statement ـی دیده‌ایم : `alert('Hello, world')` که پیام Hello, world را نمایش می‌داد.

ما به هر تعداد Statement ـی که بخواهیم می‌توانیم در کدهای خود داشته باشیم. Statement ها از طریق semicolon (سِمی‌کالِن) از هم تفکیک می‌شوند. ‌برای نمونه ما در اینجا می‌توانیم عبارت "Hello World" را در دو Alert داشته باشیم :

```js run no-beautify
alert('Hello'); alert('World');
```

معمولا Statement ها به منظور خوانایی کدها، در خطوط جداگانه نوشته می‌شوند :

```js run no-beautify
alert('Hello');
alert('World');
```

## Semicolons [#semicolon]

ممکن است Semicolon در انتهای یک Line Break حذف شود.

این کد کار خواهد کرد :

```js run no-beautify
alert('Hello')
alert('World')
```
در اینجا جاوا اسکریپت Line Break را به صورت ضمنی به عنوان یک Semicolon در نظر می‌گیرد، که به آن [درج خودکار semicolon](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) گفته می‌شود.

**در نظر داشته باشید که همیشه Line Break به معنی Semicolon نیست.**

به طور نمونه :

```js run no-beautify
alert(3 +
1
+ 2);
```

خروجی این کد `6` خواهد بود به این دلیل که جاوا اسکریپت Semicolon ـی در انتهای هر Line Break قرار نمی‌دهد. همانطور که مشخص است زمانیکه `"+"` در انتهای هر خط قرار می‌گیرد، عبارت کامل نمی‌شود و در نتیجه به Semicolon نیازی نیست.

**اما شرایطی نیز وجود دارد که جاوا اسکریپت در تشخیص نیاز به Semicolon دچار خطا می‌شود.**

خطاهایی که در چنین شرایطی رخ می‌دهند به سختی پیدا می‌شود و قابل رفع هستند.

````smart header="نمونه‌ای از یک خطا"
اگر واقعا به دنبال دیدن چنین خطایی هستید کد زیر را آزمایش کنید :

```js run
[1, 2].forEach(alert)
```

فعلا نیازی نیست تا معنی [] و foreach را متوجه شوید. در آینده با آنها آشنا خواهیم شد. فعلا در نظر داشته باشید که نتیجه‌ی این کد نمایش عدد `1` و `2` است.

حال بیایید `alert` را پیش از این کد قرار دهیم و در انتهای آن semicolon قرار ندهیم.


```js run no-beautify
alert("There will be an error")

[1, 2].forEach(alert)
```

حال اگر کد را اجرا کنیم فقط `alert` اول را خواهیم دید و سپس با خطا مواجه می‌شویم.

اما اگر انتهای `alert` اول یک semicolon قرار دهیم همه چیز دوباره درست کار خواهد کرد :

```js run
alert("All fine now");

[1, 2].forEach(alert)  
```

دلیل وقوع این خطا آن است که جاوا اسکریپت پیش از براکت‌ها `[...]` semicolon در نظر نمی‌گیرد.
از آنجایی که semicolon به صورت خودکار در انتهای alert اول قرار داده نمی‌شود، تمام کد به عنوان یک Statement در نظر گرفته می‌شود. موتور جاوا اسکریپت کد را به این شکل خواهد دید :


```js run no-beautify
alert("There will be an error")[1, 2].forEach(alert)
```

این خطا ممکن است در شرایط مشابه نیز بوجود آید.
````

ما توصیه می‌کنیم که semicolon را در انتهای هر Statement قرار دهید، حتی اگر در خطوط جداگانه‌ای قرار دارند. این اصل به شکل گسترده‌ای در جامعه برنامه‌نویسان جاوا اسکریپت جا افتاده است.
یکبار دیگر تکرار می‌کنیم : این امکان وجود دارد که در اکثر مواقع semicolon را قرار ندهید. ولی قرار دادن آن امن‌تر است، مخصوصا برای تازه‌کارها.


## Comments [#code-comments]

هر چه به جلو می‌رویم برنامه ما پیچیده‌تر می‌شود و قرار دادن *comment* برای واضح‌تر شدن کد ضروری می‌شود.

Comment ها می‌توانند در هر جایی از اسکریپت قرار بگیرند و تاثیری در اجرای دستورات ندارند، چراکه به سادگی توسط موتور جاوا اسکریپت نادیده گرفته می‌شوند.

**Comment یک خطی با دو Forward Slash یعنی `//` شروع می‌شود.**

از محلی که `//` را قرار می‌دهیم، تا انتهای خط نادیده گرفته خواهد شد. همینطور Comment می‌تواند به دنبال یک Statement بیاید.

مانند :

```js run
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Comment های چند خطی با یک /  و علامت * شروع شده و با علامت * و سپس / پایان می‌یابند.**

مانند :

```js run
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

همانطور که گفتیم دستوراتی که در Comment قرار می‌گیرند اجرا نمی‌شوند، از این رو گاهی اوقات از این روش برای غیر فعال کردن بخشی از کد می‌توان استفاده نمود.

```js run
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

<<<<<<< HEAD
```smart header="از کلیدهای میان‌بُر استفاده کنید"
بعضی ویرایشگرها قابلیت Comment کردن کد از طریق کلیدهای میان‌بُر را دارند. معمولا `ctrl + /` در ویندوز Comment های تک خطی و `ctrl + shift + /` می‌تواند Comment چند خطی بوجود آورد (باید ابتدا بخشی از کد را انتخاب نمایید). همینطور در Mac می‌توانید از کلید `cmd` بجای `ctrl` استفاده نمایید. 
=======
```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
>>>>>>> 405150f1f286db19a3c1ed913fa3e905fcefbe46
```

````warn header="Comment های تو در تو حساب نمی‌شوند"
امکان قرار دادن یک Comment داخل Comment ـی دیگر وجود ندارد.

این کد با خطا مواجه خواهد شد :

```js run no-beautify
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
````

لطفا برای استفاده از Comment در کدهای خود مردد نباشید.

Comment ها حجم کد را افزایش می‌دهند، اما این اصلا اشکال نیست. ابزارهای گوناگونی وجود دارند که قبل از انتشار برنامه روی سروِر کدهای شما را کم حجم و Comment ها را حذف می‌کنند. بنابراین Comment ها روی خروجی نهایی تاثیری نخواهند داشت.

در ادامه آموزش در بخش <info:coding-style> نحوه بهتر نوشتن Comment ها را خواهیم آموخت.
