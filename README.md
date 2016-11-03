# DQ-AutoCar
Test Programs and PCB for AutoCar

距离我第一次画PCB已经过去了5年, 期间断断续续, 这是首次尝试画4层PCB, 尽管它是非必须的. 但我还是迈出了这一步.   

Alitum Designer菜单栏中Design->Layer Stack Manager, 这样就可以添加层了, 四层板从上到下的顺序分别是: Top Layer, GND Plane, POWER Plane, Bottom Layer. 顶层和底层是Layer, 正片, 走线的地方是有铜的; 中间两层是Plane, 负片, 也就是走线的地方是没有铜的, 不走线的地方会默认敷铜. 一般GND Plane层是一整片的GND, POWER层可以按需要分割成12V, 5V, 3.3V等.    

板子资源:  
- 电源链路: 24V -> MP2303 -> 12V给雷达供电; 24V -> MP2303 -> 5V -> 3.3V;  
- MCU: STM32F207VCT6;  
- 通信: CP2105(USB转双串口), MAX3232(RS232), 共3路串口;  
- 显示: 2.2寸320x240 LCD, 使用FSMC刷屏;  
- MH1.25-4P接口: 编码器接口, 前后向开关接口;  

功能比较简单, 但为了好看些, 画出来这么大一板子(6.6cm * 8.8cm), 一个面都没有摆满...

板子用了一周才回来, 手动焊了3块, 用酒精棉擦了擦, 然后用热风枪吹化白色的残留松香, 这样看起来漂亮一些, 检查一下上电很顺利, 除了那个24V转12V的部分容易出问题, 大概是功率电感下面不能铺铜吧, 输出只有不到5V, 我把功率电感抬高才正常输出到11.88V.  

使用的话需要先安装CP2105的驱动, 会在设备管理器中出现两个串口.

现学现卖的使用 STM32CubeMX + HAL库 写了板子的几个测试程序, 才花了不到3个小时, 真的挺好使.  很推荐这种写法, 因为不论STM32那个型号, 你都不用关心时钟啊, 底层驱动啊之类的, 鼠标在STM32CubeMX中点一点就好了, 给你留出更多的时间去写功能性的东西.  

参考的话:
- Description of STM32F2xx HAL drivers.pdf
- STM32F205xx, STM32F207xx, STM32F215xx and STM32F217xx advanced ARM-based 32-bit MCUs_Reference manual.pdf
- STM32F207VET6_PDF_C59126_2015-10-07_Datasheet.pdf   

这3个文档都是需要看一下的.
