原理图绘制:
->整体结构
	PIXHAWK结构使用双MCU结构，较为复杂
	如果改成单MCU结构需要调试烧录的固件，
	（具体在固件的“板级配置”部分）
	对软件部分缺乏了解，可能无法烧录固件
	
	选用BetaFlight作为固件烧录软件
	开源资料较为全面，板级配置较灵活
	支持单MCU结构，成功率高
	参考资料链接：https://oshwhub.com/lyh6767/board

->关于主控：STM32F405VGT6

->关于电源(power_supply)
	未知接口通讯协议，
	飞控板需要稳定5V输入，
	保留5V-5V-CURRENT-VOLTAGE-GND-GND接口
	保留焊盘
	(参考DS-009 PIXHAWK->P8.Analog Power,开源自动驾驶仪飞控板)

*	补充:资料表示无人机飞控供电来自电机驱动板(ESC)
	需要实际观察了解验证

*	可能需要额外焊接DCDC板子作为电池升压供电
	飞控板不保留DCDC焊盘位置
**	需要了解ESC板子的供电

->关于传感器：
	>MP6500：六轴姿态传感器
	>BMP280：气压计
	均集成在电路板上，作为核心测试内容

->关于接口：
	>摄像头：保留AT7456焊盘位置
	>串口：使用PIXHAWK接口线序，但CTS/RTS悬空，仅保留TX/RX
	>蜂鸣器：蜂鸣器和WS3812直接在电路板上集成



引脚使用情况：
->传感器:
	>MPU6500(六轴):
		PA6->SDO
		PA5->SCL
		PA7->SDA
		PC2->CS
		PC3->INT
	>BMP280(气压计):
		PB7->SDI
		PB6->SCK
->存储：
	>TF卡座：(*注：TF卡通信采用SPI，下述仅用于区分引脚)
		PB3->CLK
		PB4->DAT0
		PB5->CMD
		PC1->DAT3
->电量：
	>电流：PC4
	>电压：PC5
->指示：
	>WS2812(LED_STRIP)：
		PB8













——————分割线——————