# tuya_iot-Arduino
涂鸦智能&amp;Arduino的一周
his project is developed using Tuya SDK, which enables you to quickly develop
branded apps connecting and controlling smart scenarios of many devices.
For more information, please check Tuya Developer Website.
这是一个涂鸦智能训练营的项目，简单实现了涂鸦模组联网控制WS2812灯珠的效果。
### 作品基本情况
 
本人是却非缺乏创造性思维一个人。训练营做的幻彩灯带，那本作品肯定就只有灯带这一个效果，也是偷懒的表现，各位小伙伴别学我啊。
本作品采用Arduino nano主板加涂鸦CBU模组，外加8颗WS2812灯珠，实现了基本的亮灯及变换颜色的效果。

### 为什么项目名称里会是一周？
并不是开发用了一周，而是用亚克力板做了一周的心情灯板，插上灯板后还真有那么一丝丝的好看，不信的小伙伴后面看视频去。

为了感觉自己还是做了那么一丢丢的事，十几个元件，还自己画了电路图+PCB，还自己打了板。电路设计时为了供电的方便，设计了两种不同的USB接口，随便拿跟手机充电线来都能玩，水果机的就别来了。

### 物料选购
因为涂鸦IOT平台，让物联网可以变得如此简单。在开发之前需要先购买涂鸦的联网模组。涂鸦模组在连接涂鸦IOT平台时候是通过唯一的PID来识别不同的设备的，这个PID很重要，需要在涂鸦IOT平台上创建物联网设备后系统自动生成。

#### 创建设备
![001.jpg](https://images.tuyacn.com/developer/community/1624354654aaa815860aa.jpg)

打开涂鸦IOT平台https://iot.tuya.com/平台，没有账号的有手机号注册一个账号并登录，登录后如上图所示，点击“创建产品”。
![002.jpg](https://images.tuyacn.com/developer/community/1624354779c2206b7b2d1.jpg)
因为做的是一个灯带的效果，所以在此选择照明大类下的“幻彩灯带”。此步骤是因人而异的，你做的是个开关，开关类，一句话，根据你自己的实际项目选择就好。

![003.jpg](https://images.tuyacn.com/developer/community/16243549146a51b20e407.jpg)

选择完产品类型后，会展开产品的开发方案选择，涂鸦平台做了零代码开发，不需要任何代码基础就能开发自己的物联网设备，这种方式适合没有代码基础的小伙伴，在此选择“自定义方案”，其实就是mcu方案，需要用mcu去控制涂鸦模组的方案。选择完后需要点击一下下方的“幻彩灯带”才会展开第3步的设置信息，不然第3不为灰色不可用状态。
![004.jpg](https://images.tuyacn.com/developer/community/1624355178f58112236c1.jpg)

在展开的第3步中填写相关信息。产品名称就是在涂鸦智能APP上显示的实际名字，后续可以改。产品型号没要求，通讯协议建议采用蓝牙+wifi的方式。
以上信息都填写完成后，最下方的“创建产品”按钮才会变为可用状态，点击它，完成产品的创建。
创建完成后，将跳转到产品的设置与开发界面，如下图所示，红框内显示的PID就是物联网设备的唯一标识，在编程是需要用到，建议直接复制，不要自己输入。
下方的各个功能点可以自行根据自己的需求增减。涂鸦智能把每个功能虚化为一个DP点，每个DP点有一个DP_ID，用DP_ID来区分不同的功能。
![005.jpg](https://images.tuyacn.com/developer/community/1624355681b5e29c8e0f2.jpg)
各个功能点选择完成后，点击面板开发，在此选择“公版面板”，测试和个人DIY足够用了。
![006.jpg](https://images.tuyacn.com/developer/community/162435597607f93761611.jpg)
面板选择完成，继续向后，选择“硬件开发”，于云端的链接方式中选择“涂鸦标准模组MCU SDK开发”，此时下方将会显示符合你选择的工作方式的涂鸦模组。其实都差不多，价格都是一样，选择一个自己看着顺眼的就好，这里我们选择CBU，带WiFi+蓝牙，板载天线的模组。
![007.jpg](https://images.tuyacn.com/developer/community/162435594877fbc39782f.jpg)
继续下方的固件选择，选择通用固件。
![008.jpg](https://images.tuyacn.com/developer/community/1624494373c364fab4bb5.jpg)
这些都选择完后，最下方会生成一份完整的开发资料，建议全部下载，在后续的编程中会用到。
注意：以上设置如果在开发过程中修改过，建议重新下载这里的开发资料，特别是修改过DP后强烈建议修改。
![008.jpg](https://images.tuyacn.com/developer/community/162449442951259b7336a.jpg)
到此，在涂鸦IOT平台的操作基本完成，最后一步需要把之前选择好的涂鸦模组下单--付款。付款后官方会烧写好通用固件后发货，参与训练营免费白嫖3个模组，顺丰包邮到家。

### 电路板设计
在等待快递的同时，可以设计电路，完成PCB板设计，再把PCB板发去打样，嘉立创5块钱顺丰包邮到家的PCB打样，板扎。
![PCBA.jpg](https://images.tuyacn.com/developer/community/16244946969d7c9312d91.jpg)
注意：在电路设计时，涂鸦模组需要3.3V供电，在配网时，电流需求大，设计时需要注意。因为采用MCU开放方案，涂鸦模组只负责配网，接收下发数据和上报数据，所以涂鸦模组只需要通过串口和MCU相连就好，这样一来关于涂鸦模组的电路设计就简单了，所有用到的资料都能在创建产品时选择模组的地方查看到所选模组的详细信息。在 串口连线时注意涂鸦模组和MCU需要交叉连接串口的两根线，即mcu_rx连接涂鸦模组的TX，mcu_tx连接涂鸦模组的RX，注意实现电平转换，实测涂鸦模组和5V供电的Arduino nano不需要电平转换也能正常通讯。


### 软件准备
因为采用的是Arduino开发，所以我们需要用到Arduino IDE、涂鸦模组的Arduino库、还需要WS2812点灯的驱动库文件，可以提前下载好安装好。所用到库文件可以点击复制以下链接下载（https://mcujishuzhai.lanzoui.com/iDxY3qnh0ij）

### 涂鸦模组测试
测试涂鸦模组可以直接采用飞线方式，也可以自己焊接PCB电路板，我们已经打板，肯定焊接板子测试。手工贴片，在此推荐一个神器，LED灯珠拆焊台，5S恒温，某宝10块钱到手，你值得拥有。
![123.jpg](https://images.tuyacn.com/developer/community/162449532709698c42afe.jpg)

打开Arduino IDE ，选择“文件”菜单-->“示例”选项卡，在展开的程序列表中选择“第三方库”中的“Tuya_WiFi_MCU_SDK”-->“start”，打开涂鸦官方提供的示例代码，如下图，我们可以简单修改后就能连上涂鸦IOT平台，控制Arduino主板上的D13LED灯的亮灭。
![009.jpg](https://images.tuyacn.com/developer/community/1624495965594869bb8e5.jpg)
如上图所示。
第24行是配网按键连接引脚，如果电路有此按键，需要修改按键连接到Arduino的引脚接口，官方默认是在7号引脚。
第37行的PID数组，在涂鸦IOT平台创建产品时，得到的一个涂鸦IOT平台唯一的标识（PID），可以直接到平台上找到创建的产品下直接复制。
    修改完后上传程序到Arduino主板。手机安装涂鸦智能APP，登录账号。此时，可以按下配网按键，让涂鸦模组进入配网模式，再涂鸦APP上添加设备，选择自动发现模式就能找到设备，跟着引导完成配网。添加完成后就能用涂鸦APP控制Arduino主板上的D13小灯的亮灭了。
完成物联网，靠涂鸦就是这么简单。

### WS2812点灯
WS2812灯珠的驱动，需要用到相应的库文件，可以直接在Arduino IDE中搜索“Adafruit_NeoPixel”下载，也可以把前面下载的库文件放到Arduino的默认库位置下。
在ArduinoIDE中打开“Adafruit_NeoPixel”库中的示例程序（随便找一个打开）简单看一下点灯的程序，可以上传程序测试一下实际的显示效果。

### 涂鸦AND点灯
完成以上两步的测试，那这个项目基本功能就没问题了，只需要把以上的两个程序整合起来就可以了。
在编写实际项目程序时，建议采用涂鸦库中“DataPointType”来修改，修改程序时将会需要用到在涂鸦上穿件产品时候生成的完整的开发资料，里面有你所添加的所有DP点的数据类型，DP的名称等相关的信息定义，直接复制来替换掉“DataPointType”示例中的对应部分即可。
至于灯的显示相关，就看你的审美了，难度几乎为零。

![01.jpg](https://images.tuyacn.com/developer/community/1624849365ac51b712cb3.jpg)
![02.jpg](https://images.tuyacn.com/developer/community/16248495237cf4d8822c0.jpg)
![03.jpg](https://images.tuyacn.com/developer/community/16248495376b158ba5906.jpg)
![04.jpg](https://images.tuyacn.com/developer/community/162484955347db4d446a9.jpg)
![05.jpg](https://images.tuyacn.com/developer/community/1624849565885aefd05e1.jpg)
![06.jpg](https://images.tuyacn.com/developer/community/16248495787b7f00fac53.jpg)
![07.jpg](https://images.tuyacn.com/developer/community/16248495907cb9d54a544.jpg)

### 遇到的问题
####PCB布局问题：
粗心大意把电源开关，两个USB接口放到了顶层；重大错误的把配网按键的方向放反了，造成顶板左边不是规整的形状，而且顶板不能紧贴灯珠。可以把以上提到的元件摆放到背面去，让顶层只有WS2812灯珠，整体效果会好很多，后面版本再改了。
####涂鸦APP问题：在调试时时长出现APP点击后没法进入到灯的控制界面，而是提示“请稍后再试”，联系涂鸦工程师咨询后问题得到了解决，但是出现的次数有点多。官方解答说会尽快修复此问题。
总结：用涂鸦模组实现设备的联网，扎实的简单，不管什么样的MCU，只需要能写串口程序，物联网那都不是问题，快快行动起来吧。
####涂鸦APP界面卡死问题
这个问题一度让项目停止了3天，一直以为是代码哪里有问题，但是仔细检查看没发现问题，无耐只有咨询涂鸦工程师，完了一语道破天机，问题完美解决，因为串口缓冲区的问题，具体如下图所示。
![涂鸦面板卡死问题解决办法.jpg](https://images.tuyacn.com/developer/community/1624842904bbb107f7357.jpg)

