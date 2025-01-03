# گزارش کار :  سنسور (IR)

## قطعات و تجهیزات مورد نیاز
1. آردوینو (  Arduino uno)
2. سنسور مادون قرمز (IR Sensor)
3.ال ای دی
4. کابلهای جامپر
5. برد بورد (Breadboard)
## شرح مدار
سنسور (IR) به پین A0 آردوینو متصل شده و به عنوان ورودی تعریف شده است . LED به پین دیجیتال 4 متصل شده و به
عنوان خروجی تعریف شده است . هنگام تشخیص جسم توسط سنسور IR ، LED روشن میشود و پیام مناسب از طریق پورت
سریال ارسال میشود .


![IR_SCHEMATIC](https://github.com/user-attachments/assets/4981db1b-0193-472d-bf09-4f642692269a)

## شرح کد
1. تنظیمات اولیه
```c++
void setup() {
  pinMode(A0, INPUT);
  pinMode(led, OUTPUT);
  Serial.begin(9600);

}
```
پین A0 به عنوان ورودی برای خواندن دادههای سنسور تنظیم شده است . پین 4 به عنوان خروجی برای کنترل LED تنظیم
شده است . ارتباط سریال برای ارسال پیامها به کامپیوتر آغاز شده است .
2. حلقه اصلی (Loop) 
```c++
void loop() {
  int IR;
  IR = digitalRead(A0);
  if (IR == 0)
  {
    Serial.print("object detected=");
    Serial.println(IR);
    digitalWrite(led, HIGH);
  }
  else {
    Serial.print("NOT detected");
    Serial.println(IR);
    digitalWrite(led, LOW);
  }
  delay(300);
}
```
وضعیت سنسور IR با استفاده از digitalRead خوانده میشود . اگر سنسور جسمی را تشخیص دهد ( مقدار 0) ، LED روشن میشود و پیام "object detected" به پورت سریال ارسال میگردد . اگر جسمی تشخیص داده نشود ( مقدار 1) ،
ال ای دی خاموش شده و پیام "NOT detected" ارسال میشود . 
## نتایج
1. در صورت تشخیص جسم : - LED روشن میشود . - پیام "object detected=0" از طریق سریال مانیتور نمایش داده میشود .
2. در صورت عدم تشخیص جسم : - LED خاموش میشود . - پیام "NOT detected" از طریق سریال مانیتور نمایش داده میشود .
3. 
 ![IR](https://github.com/user-attachments/assets/acac023c-ecff-4f3e-8d15-ed0a60ee6b2e)


## نتیجه گیری
این پروژه به درستی پیاده سازی شد و توانست جسم را با استفاده از سنسور IR تشخیص داده و وضعیت را از طریق LED و
ارتباط سریال نمایش دهد .

