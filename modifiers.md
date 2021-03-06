# اصلاح کننده‌ها {#modifiers}

اصلاح کننده‌ها یا تغییر دهنده‌ها در جاوا، کلید واژه‌هایی هستند که به تعاریفی همچون متغیرها، متدها، کلاس‌ها و ... اضافه می‌شوند و معنی آن‌ها را تغییر می‌دهند. زبان جاوا طیف گسترده‌ای از اصلاح کننده‌ها یا تغییر دهنده‌ها را پوشش می‌دهد که شامل اصلاح کننده‌های دسترسی و اصلاح کننده‌های غیر دسترسی است.

## اصلاح کننده‌های دسترسی

جاوا چهار نوع سطح دسترسی جهت استفاده از کلاس‌ها، توابع، متغیرها و سازنده‌ها در نظر گرفته است که عبارت اند از:

**۱.** **public **-- کلاس‌ها، توابع، متغیرها و سازنده‌هایی که با این نوع سطح دسترسی مشخص می‌شوند، اصطلاحا برای تمام دنیای برنامه‌ی شما در دسترس اند یعنی از هر جایی که فکرش را بکنید، می‌توانید به آن‌ها دسترسی داشته باشید!

**۲. protected **-- ** **کلاس‌ها، توابع، متغیرها و سازنده‌هایی که با این نوع سطح دسترسی مشخص می‌شوند، از داخل کلاس، بسته و تمام کلاس‌های فرزند در دسترس خواهند بود.

**۳. default **-- این نوع از سطح دسترسی هنگامی که هیچ کلیدواژه‌ای تعریف نکنید در نظر گرفته می‌شود. کلاس‌ها، توابع، متغیرها و سازنده‌هایی که با این نوع سطح دسترسی مشخص می‌شوند، از داخل کلاس، بسته و کلاس‌های فرزند که با کلاس اصلی در یک بسته قرار دارند، در دسترس هستند.

**۴. private **-- کلاس‌ها، توابع، متغیرها و سازنده‌هایی که با این نوع سطح دسترسی مشخص می‌شوند، فقط از داخل کلاس خودشان در دسترس خواهند بود. 

در زیر می‌توانید جدولی از دسته بندی اصلاح کننده‌های دسترسی مشاهده کنید:

| **تمام دنیای برنامه** | **کلاس فرزند \(بسته غیر یکسان\)** | **کلاس فرزند \(بسته‌ یکسان\) ** | **بسته** | **کلاس** |  |
| :---: | :---: | :---: | :---: | :---: | :---: |
| + | + | + | + | + | **public** |
|  | + | + | + | + | **protected** |
|  |  | + | + | + | **default** |
|  |  |  |  | + | **private** |

برای استفاده از اصلاح کننده‌های دسترسی کافیست کلید واژه‌ی آن را به محل تعریف کلاس، متغیر یا متد خود اضافه کنید تا آن‌ها تحت تاثیر اصلاح کننده‌ی مورد نظر عمل کنند.

مثال‌ زیر نمونه‌ای از ساخت چند متغیر و متد با سطوح دسترسی مختلف است: 

```java
public class MyModifiers {
    private String name;
    protected int age;
    
    // a method with default modifier
    void myMethod() {
    }
    // same as this
    default void myMethod() {
    }
    
    
}
```

## اصلاح کننده‌های غیر دسترسی

علاوه بر اصلاح کننده‌های دسترسی، زبان جاوا چندین اصلاح کننده‌ی غیر دسترسی نیز در نظر گرفته است که عبارت اند از:

**۱. static** -- متدها و متغیرهای ساخته شده در یک کلاس با این نوع اصلاح کننده، بدون ساختن شی از کلاس در دسترس هستند. در واقع وقتی متغیر یا متدی را با این اصلاح کننده می‌سازید، قادر خواهید بود خارج از کلاس اصلی آن و بدون ساختن شی از روی آن کلاس، به آن متغیر یا متد دسترسی داشته باشید. نحوه‌ی دسترسی به صورت زیر است:

```java
// for variables
ClassName.VariableName;

// for methods
ClassName.MethodName();
```

مثال:

```java
class MyFirstClass {
    static int power;
    static void powerPlusOne() {
        power = power + 1;
    }
}
public class MyMainClass {
    public static void main(String []args){
        MyFirstClass.power = 5;
        MyFirstClass.powerPlusOne();
        System.out.println("power is:‌ " + MyFirstClass.power);
    }
}
```

در این مثال، در داخل کلاس `MyFirstClass` یک متغیر و یک متد `static` تعریف کردیم و سپس در کلاس دیگری \(یعنی `MyMainClass`\) از متغیر و متد تعریف شده، بدون ساختن شی از کلاس اول، استفاده کردیم.

نتیجه:

```
➜  /tmp javac MyMainClass.java
➜  /tmp java MyMainClass      
power is: 6
```

**۲. final **-- هنگامی که این اصلاح کننده را روی یک متغیر اعمال کنید، تنها قادر خواهید بود یک‌بار آن را مقدار دهی کنید. البته عملیات مقداردهی نیاز نیست حتما در زمان تعریف متغیر انجام شود اما صرفا این نوع از متغیرها یک‌بار مقدار می‌گیرند! همچنین اگر این اصلاح کننده را روی یک کلاس اعمال کنید، آن کلاس دیگر نمی‌تواند کلاس فرزند داشته باشد. همچنین اگر در کلاس پدر یک متد را با این اصلاح کننده تعریف کنید، در کلاس فرزند قادر به بازنویسی سفارشی آن متد نخواهید بود.
 برای مثال می‌توانید نگاهی به کد زیر بیندازید:
```java
public class MyClass {
    final boolean myVariable = true;
    public static final int MYINT = 5;

    public void varChange() {
        myVariable = false;
        MYINT = 10;
    }
}
```
حال اگر این کلاس را کامپایل کنیم نتیجه‌ی زیر را خواهیم گرفت:
```
➜  /tmp javac MyClass.java
MyClass.java:6: error: cannot assign a value to final variable myVariable
        myVariable = false;
        ^
MyClass.java:7: error: cannot assign a value to final variable MYINT
        MYINT = 10;
        ^
2 errors
```
همان‌طور که مشاهده می‌کنید، برنامه کامپایل نشد چرا که ما دو متغیر `final` داشتیم و در متد `varChange` سعی در تغییر دادن مقدار آن‌ها کردیم که این کار در جاوا امکان‌پذیر نیست! خطای کامپایلر نیز همین موضوع را بیان می‌کند.
**۳. abstract **-- هنگامی که از کلید واژه‌ی abstract در ساخت کلاس استفاده کنیم، آن کلاس فقط یک کلاس پدر خواهد بود و صرفا جهت ساخت کلاس‌های زیر شاخه استفاده خواهد شد! همچنین نمی‌توانید از روی این نوع کلاس‌ها با کلمه‌ی کلیدی `new` شی بسازید! حال اگر از این اصلاح کننده برای ساخت متد استفاده شود، متد را پیاده سازی نمی‌کنیم و صرفا نحوه‌ی تعریف آن را مشخص می‌کنیم! البته باید در نظر داشته باشید که متدهای abstract را فقط می‌توان در کلاس‌های abstract نوشت! همچنین کلاس‌های abstract می‌توانند متدهای غیر abstract نیز داشته باشند.
به مثال زیر توجه کنید:
```java
public abstract class MyClass {
    abstract void myAbstractMethod();
    void myMethod(){}
}
```
توجه کنید، هنگام ساخت متد به‌صورت abstract صرفا باید نحوه‌ی تعریف آن را مشخص کنیم و پس از `()` باید علامت `;`  را قرار دهیم.

علاوه بر این‌ها، در اصلاح کننده‌های غیردسترسی دو مورد دیگر به نام `synchronized` و `volatile` داریم که مربوط به بحث تِرِدها (threads) است و در این بخش نمی‌گنجد.

