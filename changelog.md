# 维护日志

### 2020-06-29 

- 初步搭建框架
- 完成信号量兼容
- 完成`os_time.c`系统延时有关兼容


### 2020-06-30 

- 完成软件定时器兼容


### 2020-07-01  

- 实现互斥量兼容


### 2020-07-02  

- 实现消息队列兼容


### 2020-07-03  

- 实现信号标志组兼容

- 实现任务内建寄存器兼容

- 实现任务内建消息队列兼容

### 2020-07-04  

- 实现任务内建信号量兼容
- 实现uCOS-III安全认证检查相关兼容
- 对接`os_cfg.h`宏定义
- 增加`os_cfg_app.h`并与之对接
- 完成`os_sem.c` `os_q.c`文件宏定义检查以及流程的确认

### 2020-07-05  

- 完成`os_flag.c` `os_mutex.c` `os_tmr.c` `os_task.c` `os_time.c` `os_core.c`文件宏定义检查以及流程的确认
- 优化`os_cfg_app.h`、`os_cfg.h`

### 2020-07-06  

- 充实`readme.md`
- 实现`OSSemSet`、`OSTaskSemSet`函数
- 优化`OSTaskSuspend`、`OSTaskResume`函数，使其具备嵌套挂起/解挂能力
- 实现钩子函数

### 2020-07-07  

- 移植`os_mem.c`文件
- 优化了内核对象的结构体

### 2020-07-08  

- 实现`OSTmrStateGet`函数
- 构建统计任务框架
- 修改`OSTaskDel`函数没有删除任务内建信号量、任务内建队列的bug
- 移植`OS_TaskDbgListAdd`、`OS_TaskDbgListRemove`函数
- 实现`OS_TaskInitTCB`函数
- 实现Idle任务（实则为RTT Idle任务的回调函数）
- 实现Idle任务钩子函数`OSIdleTaskHook()`

### 2020-07-09

- 实现uCOS-III内部任务——统计任务，可以正确计算CPU使用率、每个任务的使用堆栈

### 2020-07-10

- 实现`OSTimeDlyResume`函数
- 修复`OSSemDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题
- 修复`OSMutexDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题
- 修复`OSQDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题
- 修复`OSFlagDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题

### 2020-07-11


- 增加兼容原版`OS_TCB`结构体成员变量
- 实现`OSSemPendAbort`函数，`OSSemPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能

### 2020-07-12

- 新增`os_rtwrap.c`文件，负责对RT-Thread和μCOS-III的转换提供支持。并在`os.h`文件末尾增加`os_rtwrap.c`内函数的声明
- 实现`OSTaskSemPendAbort`函数
- 实现`OSTaskQPendAbort`函数
- 实现`OSSemPendAbort`函数，`OSSemPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能
- 实现`OSSemMutexAbort`函数，`OSMutexPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能
- 实现`OSSFlagPendAbort`函数，`OSFlagPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能
- 实现`OSQPendAbort`函数，`OSQPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能

### 2020-07-14

- 实现`OSSchedRoundRobinCfg`函数
- 实现`OSFlagPendGetFlagsRdy`函数
- 实现`OSQFlush`函数
- 实现`OSTaskQFlush`函数
- 补充`timer_sample.c`例程

### 2020-07-15

- 移植`cpu_core.c`文件增加`CPU_Init`函数，老项目如果用到该函数在迁移时不会报错，函数内部没有实际动作
- 优化了`timer_sample.c`例程
- 补充`mutex_sample.c`例程

### 2020-07-16

- 任务内建消息队列、任务内建信号量直接沿用任务的name，不再strcat字符串
- 实现`OSTmrDel`函数回调函数功能
- 增加`OSTmrDbgListPtr`链表
- 实现了由RT-Thread定时器回调函数一个参数，到μCOS-III定时器回调函数两个参数的转换，在移植时可以直接沿用原版回调函数，无需再修改为RTT定时器的回调函数样式
- 完整实现了`p_tmr->State`的所有选项，重新实现了`OSTmrStateGet`函数
- 实现μCOS-III软件定时器带有延迟的周期延时功能(`os_tmr.c`受限项全部解决)

### 2020-07-18

- 开始对接FinSH，实现msh命令

### 2020-07-19

- `OSInit`函数内加入临界区保护
- 实现`OSSemDbgListPtr`链表
- 实现`OSSemQty`全局变量
- 实现`OSMutexDbgListPtr`链表
- 实现`OSMutexQty`全局变量
- 实现`OSQDbgListPtr`链表
- 实现`OSQQty`全局变量
- 实现`OSFlagDbgListPtr`链表
- 实现`OSFlagQty`全局变量

### 2020-07-20

- 在`os_rtwrap.c`文件中增加`rt_ipc_post_all`和`rt_sem_release_all`函数，并实现了`OSSemPost`函数`OS_OPT_POST_ALL`选项

### 2020-07-22

- 增加`sem_sample.c`例程

### 2020-07-23

- 增加`q_sample.c`例程
- 修改`main.c`，严格按照μCOS-III官方给出的初始化流程进行初始化

### 2020-07-24

- 增加μC/LIB全部文件（V1.39.00）
- 更改工程结构，将工程文件提到一级目录
- 实现μC/CPU中`CPU_NameClr`、`CPU_NameGet`、`CPU_NameSet`函数

### 2020-07-25

- 增加`os_dbg.c`、`os_cfg_app.c`文件，开始与μC/Probe软件进行对接
- 实现`OS_TCB`成员变量`.TaskState`
- `OS_TCB`成员变量`.StkPtr`改为在统计任务中定时更新

### 2020-07-26

- 实现`OS_TCB`成员变量`.PendOn`、`.DbgName`
- 信号量、互斥量、消息队列、事件标志组结构体增加成员变量`.DbgName`

### 2020-07-27

- 修复`OSMutexPendAbort`、`OSSemPendAbort`、`OSQPendAbort`、`OSFlagPendAbort`函数返回值由当前还有多少任务在等待该内核对象 改为 放弃了多少个任务
- 增加`task_sem_sample.c`例程
- 实现`OS_MUTEX`结构体`.OwnerNestingCtr`、`.OwnerTCBPtr`、`.OwnerOriginalPrio`成员变量
- 修复了CPU使用率突然飙升至100%的问题，该问题为μCOS-III原版（3.03版本）内部bug，即便是最新版的3.08版本该问题依然没有得到彻底解决（仅仅是将飙升至100%改成了骤降至0%）

### 2020-07-28

- 增加`OS_CFG_TASK_PROFILE_EN`宏定义，用以降低资源占用
- 在`os_cfg_app.c`文件中增加`OS_CFG_DBG_EN`宏定义，用以降低资源占用

### 2020-07-29

- 完善readme

### 2020-08-03

- 增加`OS_TASK_STATE_SUSPENDED`任务状态

### 2020-08-07

- 将例程由sample字眼改成example
- 增加`PKG_USING_UCOSIII_WRAPPER_AUTOINIT`宏

### 2020-08-08

- 增加SConscript脚本，以支持env工具进行自动化添加软件包

### 2020-08-12

- 完善readme文档

### 2020-08-13

-  修复`OSTmrRemainGet`函数计算剩余时间的错误
-  实现`OS_TMR`结构体`.Match`和`.Remain`成员变量

### 2020-08-16

- 实现错误代码`OS_ERR_TASK_SUSPENDED`  、`OS_ERR_TASK_OPT`、`OS_ERR_LOCK_NESTING_OVF`、`OS_ERR_MUTEX_NESTING`、`OS_ERR_MUTEX_OWNER`、`OS_ERR_ROUND_ROBIN_DISABLED`、`OS_ERR_STK_LIMIT_INVALID` 、`OS_ERR_FLAG_PEND_OPT`
- 对`OSTaskStkChk`函数当传入`OS_TCB*`参数为空时，转换为当前`OS_TCB*`的逻辑做了调整

### 2020-08-17

- 对函数`OSTmrRemainGet`、`OSTmrStop`、`OSTmrStateGet`、`OSTmrStart`、`OSTmrDel`仿照原版增加定时器状态检查功能

### 2020-08-18

- 修复`OSInit`函数return分支没有调用`CPU_CRITICAL_EXIT()`打开中断的bug
- 增加视频介绍&教程链接
- 增加3.08版本中新增的`OSInitialized`全局变量；`OS_FALSE`、`OS_TRUE`宏定义；错误代码`OS_ERR_OS_NOT_INIT`、`OS_ERR_OS_NO_APP_TASK`
- 删除已经在3.08中废弃的错误代码`OS_ERR_INT_Q`、`OS_ERR_INT_Q_FULL`、`OS_ERR_INT_Q_SIZE`、`OS_ERR_INT_Q_STK_INVALID`、`OS_ERR_INT_Q_STK_SIZE_INVALID`；增加3.08错误代码`OS_ERR_ILLEGAL_DEL_RUN_TIME`，同时补充该错误代码的相关实现
- 在`OSTmrDel`、`OSTaskDel`、`OSMutexDel`、`OSSemDel`、`OSQDel`、`OSFlagDel`函数增加`OS_SAFETY_CRITICAL_IEC61508`相关检查
- 增加错误代码`OS_ERR_MUTEX_OVF`，同时补充该错误代码的相关实现
- 增加错误代码`OS_ERR_TASK_SUSPEND_CTR_OVF`，同时补充该错误代码的相关实现
- 增加错误代码`OS_ERR_TMR_INVALID_CALLBACK`，同时补充该错误代码的相关实现

### 2020-08-19

- 将各个内核对象的名字指针归为到`OS_CFG_DBG_EN`宏定义管理范围（3.08版本如此）

### 2020-08-22

- 完成对`CPU_CRITICAL_ENTER`/`CPU_CRITICAL_EXIT`匹配检查
- 增加3.08版本的向下兼容宏定义（os.h）
- 增加`OS_CFG_INVALID_OS_CALLS_CHK_EN`宏及其实现
- 修复`OSTaskDel`函数在TCB指针为NULL即删除任务自己时，没有及时将内部变量`p_tcb`赋值为当前任务指针的bug
- 实现`OS_CFG_TASK_IDLE_EN`宏以及相关检查

### 2020-08-23

- 修改`OS_TMR`结构体`.Remain`、`.Match`成员变量赋值的bug
- 实现3.06版本中新增的`OSTmrSet`函数

### 2020-08-25

-  实现`OSTaskChangePrio`函数，目前兼容层仅1个API没有实现

### 2020-08-31

- 增加`suspend_example.c`例程

- 修复`p_tcb->TaskState`变量，增加以下功能：

    ```c
    #define  OS_TASK_STATE_PEND_TIMEOUT           (OS_STATE)(  3u)  /*   0 1 1     Pend + Timeout                         */
    #define  OS_TASK_STATE_DLY_SUSPENDED          (OS_STATE)(  5u)  /*   1 0 1     Suspended + Delayed or Timeout         */
    #define  OS_TASK_STATE_PEND_SUSPENDED         (OS_STATE)(  6u)  /*   1 1 0     Suspended + Pend                       */
    #define  OS_TASK_STATE_PEND_TIMEOUT_SUSPENDED (OS_STATE)(  7u)  /*   1 1 1     Suspended + Pend + Timeout             */
    ```


### 2020-09-20

- 修复没有调用`OS_MemInit`函数初始化内存池的bug

### 2020-09-21

- 修复`OS_TmrCallback`定时器内部回调函数在处理`OSTmrSet`更新参数时定时器参数可能无法重新设置的bug
- 增加对`OSInit`函数的错误码检查代码
- 修复`OSStart`函数内统计兼容层内部任务数量的错误（不应再包含空闲任务和定时器任务，这两个任务应为RTT内部任务）
- 将`OS_TmrCallback`函数设为static文件私有函数 
- 清理删除`OSTmrCreate`函数多余参数检查代码

### 2020-09-22

- 整理`os_tmr.c`注释
- 将`OSSemPost `/ `OSMutexPost`函数改为对`OS_OPT_POST_NO_SCHED`选项忽略

### 2020-09-23

- 将代码中μCOS改为uCOS防止在终端输出时由于μ不是ASCII码而出现乱码

### 2020-09-27

- 修复`OS_TmrCallback`函数中，在有延迟的周期延时没有对`.Match` `.Remain`成员变量重新赋值的问题

### 2020-09-28

- 创建任务时，将任务堆栈的首地址由`AppTask1_Stack`改为`&AppTask1_Stack[0]`以突出堆栈的首地址

### 2020-10-05

- 对齐并整理注释
- 删除无用的钩子函数（已被RT-Thread钩子函数接管）
- 修复`OSTimeDlyResume`函数中`p_tcb->TaskState`状态处理的问题
- 将空闲任务纳入到`OS_CFG_STAT_TASK_EN`控制范围内
- 删除`os_dbg.c`无用代码

### 2020-10-06

- 删除`os.h`无用代码

### 2020-10-07

- 实现`PKG_USING_UCOSIII_WRAPPER_TINY`以精简兼容层
- 删除`os_task.c`无用注释
- 增加`OS_CFG_TASK_SEM_EN`宏定义用于裁剪任务内建信号量

### 2020-10-15

- 删除无用配置宏定义

### 2020-10-16

- 优化`PKG_USING_UCOSIII_WRAPPER_TINY`

### 2020-10-26

- 删除`OSTaskSuspend()`函数无用的选择分支

### 2020-11-01

- 修复`OSQDel()`函数忘记回收消息内存池导致内存泄漏的问题
- 整理`os_q.c`注释格式
- 整理`os_mem.c`注释格式
- 整理`os_core.c`注释格式
- 整理`os_flag.c`注释格式
- 整理`os_mutex.c`注释格式
- 整理`os_stat.c`注释格式
- 整理`os_task.c`注释格式
- 整理`os_time.c`注释格式
- 整理`os_tmr.c`注释格式
- 整理`os_sem.c`注释格式

### 2020-11-08

- 细微调整代码格式
- 增加对老版本`os_pend_multi.c`文件的readme说明

### 2020-11-13

- 对`OSFlagPend()`函数`rt_option`变量赋初值

### 2020-11-14

- 优化工程文件结构
- 头文件部分包含由<>改为""
- 修复关闭某些宏定义，工程报错的问题
- `cpu.h`文件增加`CPU_CFG_STK_ALIGN_BYTES`宏定义
- 实现对`OS_ERR_PEND_WOULD_BLOCK`错误代码的支持

### 2020-11-15

- 增加`flag_example.c`例程
- 实现`OS_CFG_FLAG_MODE_CLR_EN`功能
- `OSQPost`和`OSFlagPost`函数改为对`OS_OPT_POST_NO_SCHED`选项忽略
- 实现`OS_TCB`结构体中`.FlagsPend`、`.FlagsRdy`、`.FlagsOpt`成员变量

### 2020-11-16

- 实现广播消息队列函数框架
- 实现广播消息队列

### 2020-11-24

- 将自动初始化由`INIT_DEVICE_EXPORT`提前至`INIT_PREV_EXPORT`

### 2020-11-30

- 完善`.FlagsRdy`成员变量
- 完善`p_grp->Flags`成员变量

### 2020-12-16

- 修复`OSTmrRemainGet()`函数返回结果单位不一致的问题
- 修复`OS_TMR`结构体`.Remain`成员变量数值单位不一致的问题
- 修复从RT-Thread到uCOS-III定时器换算公式没有考虑到Systick变化的问题

### 2020-12-17

- 完善`.FlagsRdy`成员变量

### 2020-12-25

- 修复定义`PKG_USING_UCOSIII_WRAPPER_TINY`后，代码报错的问题

### 2021-05-05

- 经过五个月的预发布测试，正式发布v1.0.0版本

### 2021-05-23

- 将`RT_IPC_FLAG_FIFO`改为`RT_IPC_FLAG_PRIO`以确保实时性



# Release

## v0.1.0

所有内核对象兼容已经全部实现，可以满足正常的兼容需求。本版本尚未实现μCOS-III的统计任务，该功能将在后续版本中发布。

## v0.2.0 

**[bug fix]** 修改`OSTaskDel`函数没有删除任务内建信号量、任务内建队列的bug

**[add]** 实现`OSTmrStateGet`函数（目前仅有13个uCOS-III API无法兼容）

**[add]** 实现Idle任务（实则为RTT Idle任务的回调函数）

**[add]** 实现Idle任务钩子函数`OSIdleTaskHook()`

**[add]** 实现uCOS-III内部任务——统计任务

## v0.3.0

**[bug fix]** 修复`OSSemDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题（已知）

**[bug fix]** 修复`OSMutexDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题（已知）

**[bug fix]** 修复`OSQDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题（已知）

**[bug fix]** 修复`OSFlagDel`函数无法返回当前等待信号量数量、无法使用`OS_OPT_DEL_NO_PEND`选项的问题（已知）

**[bug fix]** `OSSemPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能（已知）

**[bug fix]** `OSMutexPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能（已知）

**[bug fix]** `OSQPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能（已知）

**[bug fix]** `OSFlagPend`函数增加了处理`OS_ERR_PEND_ABORT`的功能（已知）

**[add]** 增加兼容原版`OS_TCB`结构体成员变量

**[add]** 实现`OSTimeDlyResume`函数

**[add]** 实现`OSSemPendAbort`函数

**[add]** 实现`OSTaskSemPendAbort`函数

**[add]** 实现`OSMutexPendAbort`函数

**[add]** 实现`OSQPendAbort`函数

**[add]** 实现`OSTaskQPendAbort`函数

**[add]** 实现`OSFlagPendAbort`函数

**[add]** 实现`OSSchedRoundRobinCfg`函数

**[add]** 实现`OSFlagPendGetFlagsRdy`函数

**[add]** 实现`OSFlagPendGetFlagsRdy`函数

**[add]** 实现`OSTaskQFlush`函数

**[add]** 实现`OSQFlush`函数（目前仅有2个uCOS-III API无法兼容）

## v0.4.0

**[add]** 移植`cpu_core.c`文件增加`CPU_Init`函数，防止老项目移植时因为没有该函数而报错，在函数内没有任何动作(DO NOTHING)

**[del]** 任务内建消息队列、任务内建信号量直接沿用任务的name，不再strcat字符串

**[bug fix]** 实现了由RTT定时器回调函数一个参数，到μCOS-III定时器回调函数两个参数的转换，在移植时可以直接沿用原版回调函数，无需再修改为RTT定时器的回调函数样式。（已知）

**[add]** 完整实现了`p_tmr->State`的所有选项，重新实现了`OSTmrStateGet`函数

**[bug fix]** 实现μCOS-III软件定时器带有延迟的周期延时功能(已知，`os_tmr.c`受限项全部解决)

**[bug fix]** `OSInit`函数内加入临界区保护

**[add]** 内核对象双向Dbg链表全部实现，并与FinSH对接，可以在msh模式下使用ucos命令查看兼容层管理的内核对象以及相关信息（例如CPU使用率）

## v0.5.0

**[bug fix]** 实现并解决`OSSemPost`函数`OS_OPT_POST_ALL`选项（已知）

**[add]** 增加μC/LIB全部文件（V1.39.00）

**[add]** 实现μC/CPU中`CPU_NameClr`、`CPU_NameGet`、`CPU_NameSet`函数

**[add]** 实现与μC/Probe软件的对接以及对接所需的必要成员变量

**[bug fix]** 修复`OSMutexPendAbort`、`OSSemPendAbort`、`OSQPendAbort`、`OSFlagPendAbort`函数返回值由 当前还有多少任务在等待该内核对象 改为 放弃了多少个任务

**[bug fix]** 修复了CPU使用率突然飙升至100%的问题，该问题为μCOS-III原版（3.03版本）内部bug，即便是最新版的3.08版本该问题依然没有得到彻底解决（仅仅是将飙升至100%改成了骤降至0%）

## v0.6.0

**[add]** 增加`OS_TASK_STATE_SUSPENDED`任务状态

**[bug fix]** 修复`OSTmrRemainGet`函数计算剩余时间的错误

**[add]** 实现`OS_TMR`结构体`.Match`和`.Remain`成员变量

**[add]** 实现错误代码`OS_ERR_TASK_SUSPENDED`  、`OS_ERR_TASK_OPT`、`OS_ERR_LOCK_NESTING_OVF`、`OS_ERR_MUTEX_NESTING`、`OS_ERR_MUTEX_OWNER`、`OS_ERR_ROUND_ROBIN_DISABLED`、`OS_ERR_STK_LIMIT_INVALID` 、`OS_ERR_FLAG_PEND_OPT`

**[enhance]** 对`OSTaskStkChk`函数当传入`OS_TCB*`参数为空时，转换为当前`OS_TCB*`的逻辑做了调整

**[bug fix]** 对函数`OSTmrRemainGet`、`OSTmrStop`、`OSTmrStateGet`、`OSTmrStart`、`OSTmrDel`仿照原版增加定时器状态检查功能

## v0.7.0

**[bug fix]** 修复`OSInit`函数return分支没有调用`CPU_CRITICAL_EXIT()`打开中断的bug

**[add 3.08]** 增加3.08版本中新增的`OSInitialized`全局变量；`OS_FALSE`、`OS_TRUE`宏定义；错误代码`OS_ERR_OS_NOT_INIT`、`OS_ERR_OS_NO_APP_TASK`

**[add 3.08]** 删除已经在3.08中废弃的错误代码`OS_ERR_INT_Q`、`OS_ERR_INT_Q_FULL`、`OS_ERR_INT_Q_SIZE`、`OS_ERR_INT_Q_STK_INVALID`、`OS_ERR_INT_Q_STK_SIZE_INVALID`；增加3.08错误代码`OS_ERR_ILLEGAL_DEL_RUN_TIME`，同时补充该错误代码的相关实现

**[add 3.08]** 在`OSTmrDel`、`OSTaskDel`、`OSMutexDel`、`OSSemDel`、`OSQDel`、`OSFlagDel`函数增加`OS_SAFETY_CRITICAL_IEC61508`相关检查

**[add 3.08]** 增加错误代码`OS_ERR_MUTEX_OVF`，同时补充该错误代码的相关实现

**[add 3.08]** 增加错误代码`OS_ERR_TASK_SUSPEND_CTR_OVF`，同时补充该错误代码的相关实现

**[add 3.08]** 增加错误代码`OS_ERR_TMR_INVALID_CALLBACK`，同时补充该错误代码的相关实现

3.08版本错误代码相关的兼容已经全部完成

**[add 3.08]** 增加3.08版本的向下兼容宏定义（os.h）

**[add 3.08]** 增加`OS_CFG_INVALID_OS_CALLS_CHK_EN`宏及其实现

**[add]** 在每个c和h文件开始位置都补充了μCOS-III最新的开源协议信息

**[bug fix]** 修复`OSTaskDel`函数在TCB指针为NULL即删除任务自己时，没有及时将内部变量`p_tcb`赋值为当前任务指针的bug

**[add]** 实现`OS_CFG_TASK_IDLE_EN`宏以及相关检查

**[bug fix]** 修改`OS_TMR`结构体`.Remain`、`.Match`成员变量赋值的bug

**[add 3.08]** 实现3.06版本中新增的`OSTmrSet`函数

## v0.8.0

**[add]** 实现`OSTaskChangePrio`函数，目前兼容层仅1个API没有实现

## v0.9.0

**[bug fix]**  修复`p_tcb->TaskState`变量，增加以下功能：

```c
#define  OS_TASK_STATE_PEND_TIMEOUT           (OS_STATE)(  3u)  /*   0 1 1     Pend + Timeout                         */
#define  OS_TASK_STATE_DLY_SUSPENDED          (OS_STATE)(  5u)  /*   1 0 1     Suspended + Delayed or Timeout         */
#define  OS_TASK_STATE_PEND_SUSPENDED         (OS_STATE)(  6u)  /*   1 1 0     Suspended + Pend                       */
#define  OS_TASK_STATE_PEND_TIMEOUT_SUSPENDED (OS_STATE)(  7u)  /*   1 1 1     Suspended + Pend + Timeout             */
```

**[add]** 增加`suspend_example.c`例程

## v0.10.0

**[bug fix]** 修复没有调用`OS_MemInit`函数初始化内存池的bug

**[bug fix]** 修复`OS_TmrCallback`定时器内部回调函数在处理`OSTmrSet`更新参数时定时器参数可能无法重新设置的bug

**[add]** 增加对`OSInit`函数的错误码检查代码

**[bug fix]** 修复`OSStart`函数内统计兼容层内部任务数量的错误（不应再包含空闲任务和定时器任务，这两个任务应为RTT内部任务）

**[fix]** 将`OS_TmrCallback`函数设为static文件私有函数 

**[del]** 清理删除`OSTmrCreate`函数多余参数检查代码

整理`os_tmr.c`注释

将`OSSemPost `和 `OSMutexPost`函数改为对`OS_OPT_POST_NO_SCHED`选项忽略

**[bug fix]** 将代码中μCOS改为uCOS防止在终端输出时由于μ不是ASCII码而出现乱码

**[bug fix]** 修复`OS_TmrCallback`函数中，在有延迟的周期延时没有对`.Match` `.Remain`成员变量重新赋值的问题

创建任务时，将任务堆栈的首地址由`AppTask1_Stack`改为`&AppTask1_Stack[0]`以突出堆栈的首地址

## v0.11.0

对齐并整理注释 

**[del]** 删除无用的钩子函数（已被RT-Thread钩子函数接管）

**[bug fix]** 修复`OSTimeDlyResume`函数中`p_tcb->TaskState`状态处理的问题

将空闲任务纳入到`OS_CFG_STAT_TASK_EN`控制范围内

**[del]** 删除`os_dbg.c`无用代码

**[del]** 删除`os.h`无用代码

**[add]** 实现`PKG_USING_UCOSIII_WRAPPER_TINY`以精简兼容层

**[del]** 删除`os_task.c`无用注释

## v0.12.0

**[add]** 增加`OS_CFG_TASK_SEM_EN`宏定义用于裁剪任务内建信号量

**[add]** 在`os.h`中增加宏定义检查代码

**[del]** 删除无用配置宏定义

**[adjust]** 优化`PKG_USING_UCOSIII_WRAPPER_TINY`

**[del]** 删除`OSTaskSuspend()`函数无用的选择分支

**[bug fix]** 修复`OSQDel()`函数忘记回收消息内存池导致内存泄漏的问题

**[adjust]** 整理`os_q.c`、`os_mem.c`、`os_core.c`、`os_core.c`、`os_flag.c`、`os_stat.c`、`os_task.c`、`os_time.c`、`os_tmr.c`、`os_sem.c`文件注释格式

**[doc]** 增加对老版本`os_pend_multi.c`文件的readme说明

**[bug fixed]** 对`OSFlagPend()`函数`rt_option`变量赋初值

**[adjust]** 优化工程文件结构

**[adjust]** 头文件部分包含由<>改为""

**[bug]** 修复关闭某些宏定义，工程报错的问题

**[add]** `cpu.h`文件增加`CPU_CFG_STK_ALIGN_BYTES`宏定义

**[add]** 实现对`OS_ERR_PEND_WOULD_BLOCK`错误代码的支持

**[add]** 增加`flag_example.c`例程

**[add]** 实现`OS_CFG_FLAG_MODE_CLR_EN`功能

**[adjust]** `OSQPost`和`OSFlagPost`函数改为对`OS_OPT_POST_NO_SCHED`选项忽略

**[add]** 实现`OS_TCB`结构体中`.FlagsPend`、`.FlagsRdy`、`.FlagsOpt`成员变量

## v0.13.0

**[add]** 实现广播消息队列

**[adjust]** 将自动初始化由`INIT_DEVICE_EXPORT`提前至`INIT_PREV_EXPORT`

完善`.FlagsRdy`成员变量

完善`p_grp->Flags`成员变量

**[fix]** 修复`OSTmrRemainGet()`函数返回结果单位不一致的问题

**[fix]** 修复`OS_TMR`结构体`.Remain`成员变量数值单位不一致的问题

**[fix]** 修复从RT-Thread到uCOS-III定时器换算公式没有考虑到Systick变化的问题

## v1.0.0

经过五个月的预发布测试，正式发布v1.0.0版本

## V1.0.1

将`RT_IPC_FLAG_FIFO`改为`RT_IPC_FLAG_PRIO`以确保实时性



# 已知问题

受上游RT-Thread影响(https://github.com/RT-Thread/rt-thread/issues/3946) 导致兼容层的任务挂起/解挂API在挂起其他任务时，不能正确工作。任务自己挂起自己时，可以正常工作。