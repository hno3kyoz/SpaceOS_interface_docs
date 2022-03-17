# APA信息

接口总览：

1. 控制接口
   1. 启动/关闭 AVM
   2. 设置雷达音量
   3. ==切换AVM视图==
2. 状态接口
   1. AVM工作状态
   2. 故障



## 状态接口

| Key             | Value                                                        | 注释               |
| --------------- | ------------------------------------------------------------ | ------------------ |
| ShakehandResp   | 0x0:No_Response <br />0x2:Response                           | 握手反馈信号       |
| AvmStsReq       | 0x0:Off <br />0x1:On                                         | AVM 请求开启 信号  |
| FunctBtnSts     | 0x0:Set_Ash <br />0x1:HAVP_function_active <br />0x2:Highlight | 功能按键状态       |
| Signal_Indnc    | 0x0:APA 0x1:AVP                                              | ==信号优先级判断== |
| FunctWorkSts    | 0x0:Standby 0x1:Mapbuilding 0x2:Mapbuilt_complete 0x3:Cruise 0x4:Failure 0x5:Pause 0x6:Parking | 工作状态           |
| InterfaceDisTyp | 0x0:None <br />0x1:Pre_HAVP <br />0x2:Mapbuilt <br />0x3:Cruise <br />0x5:Mapbuilt_complete <br />0x6:HAVP_completed <br />0x7:MapShowToStart | 界面显示类型       |
| PopupDisp       | 详见弹窗提示                                                 | 提示弹窗           |
| FunctTextDisp   | 详见文字提示                                                 | 文字显示           |
| BtnEnaAck       | 0x0:No_Response 0x1:Response                                 | 开关点击反馈       |
| FunctBtnDisp    | 0x0:None <br />0x1:Start_HAVP <br />0x2:Start_mapbuilt <br />0x3:Parking_in_weak_active <br />0x4:Mapbuilt_weak_active_signal <br />0x5:Continue_HAVP <br />0x6:Map_build_completed <br />0x7:Start_APA <br />0x8:Start_SVP <br />0x9:Continue_SVP | 按键显示           |



## 控制接口：

| Key          | value                                                        | 注释              |
| ------------ | ------------------------------------------------------------ | ----------------- |
| ShakehandReq | 0x0:No_Request <br />0x1: Request                            | APA与HUT 握手信号 |
| AvmStsResp   | 0x0:Off <br />0x1:On                                         | 启动/关闭 AVM功能 |
| SelectslotID | 0x0~0x1F                                                     | 选择泊入信号      |
| BtnEnaReq    | 0x0:None <br />0x1:Mapbuilt_weak_active <br />0x2:HAVP_active_signal <br />0x3:Confrim_mapbuilt <br />0x4:Change_route <br />0x5:Confrim_start_parking <br />0x6:Parking_in_weak_active <br />0x7:Cancel <br />0x8:Continue_HAVP<br />0x9:Map_build_completed_click <br />0xA:HAVP_function_open <br />0xB:HAVP_function_closed <br />0xC:Weak_alert_function_open <br />0xD:HAVP_Weak_alert_function_closed <br />0xE:Learning_completed <br />0xF:Cancel_current_weak_active_button <br />0x10:SVP_function_open <br />0x11:SVP_function_closed <br />0x12:Start_HAVP_VR <br />0x13:Start_SVP <br />0x14:Start_SVP_VR <br />0x15:Try <br />0x16:Continue_Learn <br />0x17:Search_Slot_along_way <br />0x18:HAVP_Completed | 开关点击信号      |

## 报警字段

| 0x0:  None                               |      | /                                  |                              | /                                      |
| ---------------------------------------- | ---- | ---------------------------------- | ---------------------------- | -------------------------------------- |
| 0x1:  Turn on background functions       | N    | 未打开功能开关，点击LVP开关        | 请先打开记忆泊车功能开关     | 请先打开记忆泊车功能开关               |
| 0x2: Please adjust under P               | N    | 在非P档开启或关闭LVP后台功能开关   | N                            | 请在P档下进行调节                      |
| 0x3:  rampway                            | N    | 坡道中                             | 记忆泊车暂不可用             | 请驶离坡道再试                         |
| 0x4:  Environment empty                  | Y    | 环境过于空旷                       | 记忆泊车暂不可用             | 当前环境无法满足记忆泊车开启条件       |
| 0x5:  Outside the underground car park   | Y    | 地下停车场之外                     | 记忆泊车暂不可用             | 在地下停车场之外，记忆泊车暂不可用     |
| 0x6:  camera blocked                     | Y    | 摄像头被遮挡                       | 记忆泊车暂不可用             | 摄像头被遮挡, 记忆泊车暂不可用         |
| 0x7:  loop camera faulty                 | Y    | 摄像头故障                         | 记忆泊车暂不可用             | 摄像头故障，记忆泊车暂不可用           |
| 0x8:  Radar faulty                       | Y    | 雷达故障                           | 记忆泊车暂不可用             | 前视摄像头故障，记忆泊车暂不可用       |
| 0x9:  Associated system faulty           | Y    | 关联系统故障                       | 记忆泊车暂不可用             | 关联系统故障，记忆泊车暂不可用         |
| 0xA:  System faulty                      | Y    | 系统故障                           | 记忆泊车暂不可用             | 系统故障，记忆泊车暂不可用             |
| 0xB:  Door open                          | Y    | 车门未关闭                         | 记忆泊车暂不可用             | 车门打开，记忆泊车暂不可用             |
| 0xC:  Rear door open                     | Y    | 后背门未关闭                       | 记忆泊车暂不可用             | 后背门打开，记忆泊车暂不可用           |
| 0xD:  Safety belt unfastened             | Y    | 未系安全带                         | 记忆泊车暂不可用             | 未系安全带，记忆泊车暂不可用           |
| 0xE:  Engine cover open                  | Y    | 机舱盖未关闭                       | 记忆泊车暂不可用             | 机舱盖打开，记忆泊车暂不可用           |
| 0xF:  RCTB/FCTB activation               | N    | RCTB/FCTB激活                      | 记忆泊车暂不可用             | 主动安全功能激活激活，记忆泊车暂不可用 |
| 0x10:  AEB activation                    | N    | AEB激活                            | 记忆泊车暂不可用             | 主动安全功能激活激活，记忆泊车暂不可用 |
| 0x11:  TCS/ABS activation                | Y    | TCS/ABS 激活                       | 记忆泊车暂不可用             | 主动安全功能激活激活，记忆泊车暂不可用 |
| 0x12:  ESP activation                    | Y    | ESP激活                            | 记忆泊车暂不可用             | 主动安全功能激活激活，记忆泊车暂不可用 |
| 0x13:  HDC activation                    | Y    | HDC激活                            | 记忆泊车暂不可用             | 主动安全功能激活激活，记忆泊车暂不可用 |
| 0x14:  Tire pressure is too low          | Y    | 胎压过低                           | 记忆泊车暂不可用             | 胎压过低，记忆泊车暂不可用             |
| 0x15:  Illumination conditions           | Y    | 光照条件ODD不满足                  | 记忆泊车暂不可用             | 光照过量或过暗，记忆泊车暂不可用       |
| 0x16:  Raining conditions                | Y    | 雨量条件ODD不满足                  | 记忆泊车暂不可用             | 雨量过大，记忆泊车暂不可用             |
| 0x:17 click Finish                       | Y    | 用户泊入挂P档                      | 如果已泊入你的车位请点击完成 | 如果已泊入你的车位请点击完成           |
| 0x18: Keep going                         | Y    | 进入停车场未到路线起点             | 再往前开开                   | 再往前开开                             |
| 0x19:  The learning route is not located | N    | 未定位到学习路线，点击记忆泊车按键 | 记忆泊车暂不可用             | 未定位到学习路线，记忆泊车暂不可用     |
| 0x1A:  Please switch to D gear           | Y    | 车辆在R、N档                       | 请先挂入D档                  | 请先挂入D档                            |
