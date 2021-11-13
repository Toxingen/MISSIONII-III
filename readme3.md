## 嵌软第三次培训

### 状态机

#### 知识学习

1.有限状态机

​    即需要事件满足一定条件时使用一定的动作从一个状态转为另一个状态的实现方式。

#### 工程实现

状态机消抖思路

* 定义按键的四种状态及按键是否有效的结构体

  typedef enum {KEY_RELEASED,KEY_PRESSED,KEY_PROCESSED}KEY_STATUS;
              //释放           按下          处理过的
  typedef struct {
      uint8_t  byCounter;//按键是否有效
      KEY_STATUS eKeyStatus;//按键状态
  }KEY_ATTRIB;
  KEY_ATTRIB Key0;

* 回调函数两种增加counter的方式：①左移一位 ②自增 

  即每过10ms进行定时器中断扫描，若连续8次扫描都保持按下状态则为按下状态，即counter达到0xff时为有效按键。

* 后续为按键进行不同状态的标记

  

### 舵机驱动

#### 实验实现

* 舵机在一定频率不同占空比的pwm下会转动不同的角度。
* 2.5%-12.5%占空比的20ms周期的pwm波能正常驱动180度电机达到从0°到180°的不同角度。
* 工程结合了状态机消抖。