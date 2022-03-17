# PAS信息

接口总览：

1. 控制接口
   1. 启动/关闭 PAS
   2. 设置雷达音量
   3. ==切换AVM视图==：2D模式、3D模式
2. 状态接口
   1. AVM工作状态
   2. 故障



## 测量命令

| Key             | value                                                        | 注释                   |      |
| --------------- | ------------------------------------------------------------ | ---------------------- | ---- |
| FPAS_AutoModSts | 0x0:Not available 0x1:Available                              | 前雷达自动开启功能状态 |      |
| SDWActiveSts    | 0x0:Not active 0x1:Active                                    | 侧翼保护开关状态       |      |
| FPAS_DispCmd    | 0x0: OFF 0x1: ON                                             | 前雷达显示请求         |      |
| AVM_CurrSts     | 0x0:Off 0x1:ON <br />0x2:AVM no video（雷达模式） <br />0x3:Reserved | AVM 工作状态           |      |
| FPAS_WorkSts    | 0x0: Disable <br />0x1: Enable <br />0x2: Active <br />0x3: Failed | 前雷达工作状态         |      |
| FPAS_SoundIndcn | 0x0:Tone zero No warning <br />0x1:Tone one Long beep <br />0x2:Tone two 1.5 Hz <br />0x3:Tone three 3Hz | 前雷达报警声音提示     |      |
| CarMdlDispSts   | 0x0:2D mode <br />0x1:3D mode                                | 当前显示模式           |      |
|                 |                                                              |                        |      |
|                 |                                                              |                        |      |

## 控制命令



| Key           | value                            | 注释              |      |
| ------------- | -------------------------------- | ----------------- | ---- |
| CarMdlDispCmd | 0x0:No Request <br />0x1:Request | 切换2D 3D显示模式 |      |
| SDWActiveSts  | 0x0:Not active 0x1:Active        | 侧翼保护开关状态  |      |



