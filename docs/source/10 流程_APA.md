# APA流程接口

![image-20220318143808879](images/image-20220318143808879.png)

APA（Auto Parking Asist）自动泊车是生活中最常见的泊车辅助系统。泊车辅助系统在汽车低速巡航时，使用传感器感知周围环境，帮助驾驶员找到尺寸合适的空车位，并在驾驶员发送泊车指令后，将汽车泊入车位。

## 状态接口

| 接口              | key                                                          | value                                                        |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ==xx状态？==      | APS_status                                                   | 0x0:Disable <br />0x1:Standby <br />0x2:Searching 搜索库位<br />0x3:Guidance 导航 <br />0x4:Failed <br />0x5:Wait for Engine restart <br />0x6~0X7:Reserved |
| APA功能状态       | APA_FuncSts                                                  | 0x0: standby <br />0x1: active <br />0x2: disable <br />0x3:Reservedap |
| ==APA??==         | APA_MenuDispCtr lCmd                                         | 0x0:No_Disp_avm_menu <br />0x1:park_in_indicate_menu <br />0x2:park_in_select_slot_menu <br />0x3:park_in_mode_select_menu <br />0x4:park_in_process <br />0x5:remote_park_in_process <br />0x6:park_out_confirm_menu <br />0x7:park_out_process<br />0x8:park_in_indicate_menu_NoRPA <br />0x9:park_in_select_slot_menu_NoRPA <br />0xA:park_in_mode_select_menu_NoRPA <br />0xB:park_out _indicate_menu <br />0xC:User_Defined_Parking_Slot_Menu <br />0xD:park_in_RemoteSearchingSlot_menu <br />0xE:PAVP_screen_section_A 0xF:Reversed |
| 显示提示信息      | APS_TextDisp                                                 | 详见《提示列表》...                                          |
| ==？==            | HAP_SwtDispCtrl Cmd                                          | 0x0:no display <br />0x1:park out direction Select menu <br />0x2:continue park menu <br />0x3:Study finish button <br />0x4:continue RADS menu <br />0x5:continue FADS menu <br />0x6~0x7:Reserved |
| 泊车进度          | ProcBar                                                      | 0x0-0x64: 0~100% <br />0x65-0x7E: Reserved <br />0x7F: No Display |
| 播放报警音        | sound                                                        | 0x0:Tone 0 - No Warning <br />0x1:Tone 1 - failed tone <br />0x2:Tone 2 - successful tone <br />0x3:Tone 3 - warning tone <br />0x4:Tone 4 - request tone 0x5~0x7:Reserved |
| ==atparkgrage==   | 0：IDEL 1:地库内   2：地库外                                 |                                                              |
| distance_parking  | [float,float,float,float] [总泊车距离，泊车剩余行驶距离，本次操作总行驶距离，本次操作剩余行驶距离]，单位米 |                                                              |
| distance          | 距离车位距离，单位米                                         |                                                              |
| avoid_pedestrian  | 避让行人次数                                                 |                                                              |
| avoid_vehicle     | 避让车辆次数                                                 |                                                              |
| distance_learning | 学习距离  单位米                                             |                                                              |
| bumper_num        | 减速带条数                                                   |                                                              |
| prompt            | 系统提示 0:无 1：开出地库回到地面  2：从地库出口驶离约200米  3：重新回到起点 |                                                              |
| driving_state     | 0:IDEL 1:直行   2:左转    3:右转   4:路口请注意   5:等待前车行驶  6:即将到达指定车位 |                                                              |
| MapDevPercentage  | 建图百分比，0~100                                            |                                                              |
|                   |                                                              |                                                              |

## 控制接口

| 接口                     | key                                                          | value                                                        |
| ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 进入\退出 APA功能        | Enable_APA                                                   | 0x0: select <br />0x1: cancel                                |
| 选择泊入车位             | select_parking_lot                                           | 0x0~0x1F                                                     |
| 选择泊车模式             | PrkgCtrlModReq                                               | 0x0:No action <br />0x1:Parking in car <br />0x2:Remote parking <br />0x3:Remote searching slot |
| 设置泊出方向             | SelPrkOutDirReq                                              | 0x0:No selection <br />0x1:Park out front/vertical head out <br />0x2:Park out rear/vertical tail out <br />0x3:Park out left/parallel left out <br />0x4:Park out right/parallel right out <br />0x5-0x7:Reserved |
| 开始泊车                 | StartParkCmd                                                 | 0x0:No_Request <br />0x1:Request                             |
| ==pathid==               |                                                              | 路径id                                                       |
| ==mapid==                |                                                              | 地图id                                                       |
| ==BtnEnaReq_modestatus== | 0x0:None <br />0x1:Mapbuilt_weak_active <br />0x2:HAVP_active_signal <br />0x3:Confrim_mapbuilt <br />0x4:Change_route <br />0x5:Confrim_start_parking <br />0x6:Parking_in_weak_active <br />0x7:Cancel <br />0x8:Continue_HAVP<br />0x9:Map_build_completed_click <br />0xA:HAVP_function_open <br />0xB:HAVP_function_closed <br />0xC:Weak_alert_function_open <br />0xD:HAVP_Weak_alert_function_closed <br />0xE:Learning_completed <br />0xF:Cancel_current_weak_active_button <br />0x10:SVP_function_open <br />0x11:SVP_function_closed <br />0x12:Start_HAVP_VR <br />0x13:Start_SVP <br />0x14:Start_SVP_VR <br />0x15:Try <br />0x16:Continue_Learn <br />0x17:Search_Slot_along_way <br />0x18:HAVP_Completed | 开关点击信号                                                 |
| ==BtnEnaReq==            | 0 //0:default  <br />1:扫库 <br />2:开始泊入车位  <br />3:继续  <br />4:退出 <br />5:确认学习  <br />6:完成学习  <br />7:退出指引   <br />8:开始记忆泊车 <br />9:恢复记忆泊车 <br />10:遥控泊车<br />11:遥控泊车返回 <br />12: 停止学习（学习失败） <br />13:PAVP开始 | 开关点击信号                                                 |

