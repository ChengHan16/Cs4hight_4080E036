# 晶心開發系統技術能力分級檢定
> `http://www.andestech.com/tw/%E6%8A%80%E8%A1%93%E6%94%AF%E6%8F%B4/acet%E6%AA%A2%E5%AE%9A%E8%A8%88%E5%8A%83/`
# 筆試題庫
> `http://www.andestech.com/wp-content/uploads/ACET%E6%AA%A2%E5%AE%9A%E7%AD%86%E8%A9%A6%E9%81%B8%E6%93%87%E9%A1%8C-v1.0.pdf ` 
# 實作題庫
> `http://www.andestech.com/wp-content/uploads/ACET-%E5%AF%A6%E4%BD%9C%E9%A1%8C-v1.0.pdf`
```

```
#
```c

#define NUM 25 // 首先定義LED的數目
int leds[NUM] = {
  0, 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, D14, D15, A0, A1, A2, A3, LED1, LED2, LED3,LED4
};

// 將每個腳位模式設為OUTPUT
void setup() {               
  for(int i = 0; i < NUM; i++){
    pinMode(leds[i], OUTPUT);
  }    
}
// 雖然A3、A2、A1、A0是類比腳位，
// 但也可以把它當做數位腳位使用。

// 然後是兩個迴圈，
// 第一個迴圈從這邊跑到那邊，
// 第二個迴圈跑回來。
void loop() {
  for(int i = 0; i < NUM; i++){
    digitalWrite(leds[i], LOW);
    delay(500);
    digitalWrite(leds[i], HIGH);
  }
  for(int i = NUM-1; i >= 0; i--){
    digitalWrite(leds[i], LOW);
    delay(200);
    digitalWrite(leds[i], HIGH);
  }
}
```
```C
/*
 * #define NUM 25 // 首先定義LED的數目
 * 
 int leds[NUM] = {
  0, 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, D14, D15, A0, A1, A2, A3, LED1, LED2, LED3,LED4
};
*/
#define NUM 16
int leds[NUM] = {
  0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, D14, D15};

// 將每個腳位模式設為OUTPUT
void setup() {               
  for(int i = 0; i < NUM; i++){
    pinMode(leds[i], OUTPUT);
    digitalWrite(leds[i], HIGH);
  }    
}
// 雖然A3、A2、A1、A0是類比腳位，
// 但也可以把它當做數位腳位使用。

// 然後是兩個迴圈，
// 第一個迴圈從這邊跑到那邊，
// 第二個迴圈跑回來。
void loop() {
  int cnt=0;

  for(int i = 0; i < 11; i++){
    digitalWrite(leds[i], LOW);
    delay(500);
    digitalWrite(leds[i], HIGH);
  }
  for(int i = 11-2; i >= 1; i--){
    digitalWrite(leds[i], LOW);
    delay(500);
    digitalWrite(leds[i], HIGH);
  }

  for (int i=0; i<8; i++)
  {
    digitalWrite(leds[8+i], LOW);
    digitalWrite(leds[7-i], LOW);
    delay(500);
    digitalWrite(leds[8+i], HIGH);
    digitalWrite(leds[7-i], HIGH);
  }
  for (int i=1; i<8; i++)
  {
    digitalWrite(leds[i], LOW);
    digitalWrite(leds[15-i], LOW);
    delay(500);
    digitalWrite(leds[i], HIGH);
    digitalWrite(leds[15-i], HIGH);
  }
}
```
