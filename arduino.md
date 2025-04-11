# Arduino


## 1. Arduino简介  

Arduino是一种开源电子原型平台，致力于通过易于使用的硬件和软件，帮助爱好者、学生和专业人士创造互动项目。Arduino使用微控制器作为核心，可以轻松地控制各种传感器、执行器和电子元件。Arduino的开发环境允许用户用C/C++语言编程，同时也支持多种图形化编程工具，如Scratch、Mixly等，特别适合初学者学习基本的编程和电子知识。由于其模块化的设计和强大的社区支持，Arduino广泛应用于智能家居、机器人、物联网等各种创新项目，成为电子制作和学习的重要工具。  

## 2. 连接图  

![](media/5ab73cfb621c9fcfd736d0fc3a3310a6.png)  

## 3. 测试代码  

```cpp  
int flamePin_D = 3; // 定义数字口3  
int flamePin_A = A0; // 定义模拟口A0  
int ledPin = 13; // 定义数字口13  

// 变量将变化  
int State_D = 0; // 定义数字变量State_D  
int State_A = 0; // 定义数字变量State_A  

void setup() {  
    Serial.begin(9600); // 设置串口波特率为9600  
    pinMode(ledPin, OUTPUT); // 将ledPin设置为输出  
    pinMode(flamePin_D, INPUT); // 将flamePin设置为输入  
}  

void loop() {  
    State_D = digitalRead(flamePin_D); // 读取数字口的数值，并赋值给State_D  
    State_A = analogRead(flamePin_A); // 读取模拟口的数值，并赋值给State_A  
    Serial.println(State_A); // 串口打印出来  

    if (State_D == LOW) { // 当sensorState为低电平时，LED亮起  
        digitalWrite(ledPin, HIGH); // LED亮起  
    } else {  
        digitalWrite(ledPin, LOW); // LED变暗  
    }  
}  
```  

## 4. 测试结果  

按照上图接好线，烧录好代码；上电后，打开串口监视器并设置波特率为9600，可以看到从火焰传感器读取到的模拟值。调节模块电位器，使模块上D1处于亮起和关闭的临界点，使D1关闭。传感器没有检测到火焰时，传感器上的D1灯关闭，板上的D13指示灯也关闭；当传感器检测到火焰时，传感器上的D1灯亮起，板上的D13指示灯亮起。


