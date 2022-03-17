# AVM功能

接口总览：

1. 控制接口
   1. 启动/关闭 AVM
   2. 设置雷达音量
   3. ==切换AVM视图==
2. 状态接口
   1. AVM工作状态
   2. 故障



控制命令

| Key        | value                                                        | 注释               |      |
| ---------- | ------------------------------------------------------------ | ------------------ | ---- |
| AvmStsReps | int (探头的个数)                                             |                    |      |
| _1         | 0x0:Tone zero No warning 、 0x1:Tone one Long beep 、 0x2:Tone two 1.5 Hz 、 0x3:Tone three 3Hz | 发出前雷达报警音   |      |
| _2         | 0x0:Tone zero No warning 、 0x1:Tone one Long beep 、 0x2:Tone two 1.5 Hz 、 0x3:Tone three 3Hz | 发出后雷达报警声音 |      |
| ...        | ...                                                          | ...                |      |







