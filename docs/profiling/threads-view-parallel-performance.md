---
title: “线程”视图（并行性能） | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccb86d36429f8695222f69fbf6d78635a338bfe5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="threads-view-parallel-performance"></a>线程视图（并行性能）
线程视图是并发可视化工具中最详细且具备丰富功能的视图（选择“分析” > “并发可视化工具”来启动并发可视化工具）。 使用此视图可以确定线程是在执行还是由于同步、I/O 或某些其他原因而阻塞。  
  
 在分析过程中，并发可视化工具会对每个应用程序线程检查所有操作系统上下文切换事件。 上下文切换可能由于许多原因而发生，如以下这些：  
  
-   线程在同步基元上受阻。  
  
-   线程的量程到期。  
  
-   线程进行了阻塞 I/O 请求。  
  
 当线程停止执行时，“线程”视图会向每个上下文切换分配类别。 类别显示在视图左下部分的图例中。 并发可视化工具通过在线程的调用堆栈中搜索已知阻塞 API，来对上下文切换事件进行分类。 如果没有调用堆栈匹配，则使用 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 提供的等待原因。 但是，[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 类别可能基于实现详细信息，并且可能无法反映用户意图。 例如，[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 会将在本机精简读取器/编写器锁上阻塞的等待原因报告为 I/O 而不是同步。 在大多数情况下，可以通过检查与上下文切换事件对应的调用堆栈来确定阻塞事件的根本原因。  
  
 “线程”视图还显示线程之间的依赖关系。 例如，如果识别了在同步对象上阻塞的线程，则可以查找对它取消阻塞的线程，并且可以检查该线程对另一个线程取消阻塞时该线程的调用堆栈上的活动。  
  
 当线程正在执行时，并发可视化工具会收集样本。 在“线程”视图中，可以分析一个或多个线程在执行段期间执行的代码。 还可以检查阻塞报告以及分析调用堆栈树执行的报告。  
  
## <a name="usage"></a>用法  
 下面是一些可以用于使用“线程”视图的方式：  
  
-   确定应用的用户界面 (UI) 在特定执行阶段中无响应的原因。  
  
-   确定在同步、I/O、页面错误和其他事件上阻塞所花的时间量。  
  
-   确定来自系统上执行的其他进程的干扰的程度。  
  
-   确定并行执行的负载平衡问题。  
  
-   确定非最优或不存在的可伸缩性的原因（例如，在有更多逻辑核心可用时，并行应用的性能未提高的原因）。  
  
-   了解应用中的并发度以帮助进行并行化。  
  
-   了解工作线程和执行的关键路径间的依赖关系。  
  
## <a name="examining-specific-time-intervals-and-threads"></a>检查特定时间间隔和线程  
 “线程”视图会显示时间线。 可以在时间线中缩放和平移以检查应用程序的特定间隔和线程。 X 轴上是时间，y 轴上是几个通道：  
  
-   系统上每个磁盘驱动器两个 I/O 通道，一个通道用于读取，另一个用于写入。  
  
-   进程中每个线程一个通道。  
  
-   标记通道（如果跟踪中存在事件标记）。 标记通道最初出现在生成这些事件的线程通道下。  
  
-   GPU 通道。  
  
 下面是“线程”视图的图示：  
  
 ![“线程”视图](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
线程视图  
  
 最初，线程按创建顺序进行排序，以便主应用程序线程处于第一位。 可以使用视图左上角的排序选项按其他条件对线程排序（例如，按执行最多执行工作）。  
  
 可以通过在左侧列中选择未在执行工作的线程的名称，然后选择工具栏上的“隐藏所选线程”按钮，来隐藏这些线程。 我们建议隐藏完全受阻的线程，因为其统计信息不相关，可能会阻碍报告。  
  
 若要确定要隐藏的其他线程，请在活动图例中，选择“分析报告”选项卡上的“每线程摘要”报告。这会显示执行细分图，其中显示当前所选时间间隔的线程状态。 在某些缩放级别，某些线程可能不会显示。 发生这种情况时，省略号会显示在右侧。  
  
 选择了时间间隔及其中的某些线程之后，可以启动性能分析。  
  
## <a name="analysis-tools"></a>分析工具  
 本节介绍报告和其他分析工具。  
  
### <a name="thread-blocking-details"></a>线程阻塞详细信息  
 若要获取有关线程上特定区域中的阻塞事件的信息，请将指针停留在该区域上以显示工具提示。 如果存在工具提示，则它会包含诸如类别、区域开始时间、阻塞持续时间和阻塞 API 这类信息。 如果选择阻塞区域，则该时间点上的堆栈以及工具提示中显示的相同信息会显示在窗格底部。 通过检查调用堆栈，可以确定线程阻塞事件的基本原因。 通过选择段并检查“当前”选项卡，可以查找其他进程和线程信息。  
  
 执行的路径可能会具有多个阻塞事件。 可以按阻塞类别检查这些事件，以便可以更快地找到问题区域。 只需在左侧图例中选择一个阻塞类别。  
  
### <a name="dependencies-between-threads"></a>线程之间的依赖关系  
 并发可视化工具可以显示进程中线程之间的依赖关系，以便可以确定受阻线程尝试执行的操作，并了解其他线程使它可以执行的操作。 若要确定哪个线程对另一个线程取消了阻塞，请选择相关阻塞段。 如果并发可视化工具可以确定取消阻塞线程，则它会在取消阻塞线程与跟在阻塞段之后的执行段之间绘制一条线。 此外，“取消阻塞堆栈”选项卡上会显示相关调用堆栈。  
  
### <a name="thread-execution-details"></a>线程执行详细信息  
 在线程的时间线关系图中，绿色段在该线程在执行代码时显示。 可以获取有关执行段的更多详细信息。  
  
 选择执行段中的一个点时，并发可视化工具会在相关调用堆栈上查找该时间点，然后在执行段中所选点上方显示黑色脱字号，并在“当前堆栈”选项卡上显示调用堆栈本身。可以在执行段上选择多个点。  
  
> [!NOTE]
>  并发可视化工具可能无法解析执行段上的选择。 通常，当段的持续时间小于一毫秒时，会发生这种情况。  
  
 若要获取当前所选时间范围内所有已启用（未隐藏）线程的执行分析，请选择活动图例中的“执行”按钮。  
  
### <a name="timeline-graph"></a>时间线关系图  
 时间线关系图显示主计算机上的进程与所有物理磁盘设备中的所有线程的活动。 它还显示 GPU 活动和标记事件。  可以放大以查看更多详细信息，也可以缩小以查看更长的时间间隔。 还可以在关系图上选择各点以获取有关类别、开始时间、持续时间和调用堆栈状态的详细信息。  
  
 在时间线关系图中，一种颜色指示线程在给定时间的状态。 例如，绿色段表示已在执行， 红色段指示已因同步而受阻，黄色段指示已被抢占，紫色段指示已参与设备 I/O。 可以使用此视图检查并行循环和并发任务所涉及的线程间的工作平衡。 如果某个线程完成所用时间要长于其他线程，则工作可能会不平衡。 可以使用此信息提高程序的性能，具体方法是在线程间更均匀地分布工作。  
  
 如果在某个时间点只有一个线程是绿色（正在执行），则应用可能无法在系统上充分利用并发。 可以使用时间线关系图检查线程之间的依赖关系以及阻塞线程与被阻塞线程之间的临时关系。 若要重新排列线程，请选择一个线程，然后在工具栏上选择向上或向下按钮。 若要隐藏线程，请选择它们，然后选择“隐藏线程”按钮。  
  
### <a name="profile-reports"></a>分析报告  
 时间线关系图下方是时间线分析以及具有各种报告的选项卡的窗格。 更改“线程”视图时，报告会自动更新。 对于大型跟踪，在计算更新时，报告窗格可能不可用。 每个报告都具有两个筛选器调整：“降噪”和“仅我的代码”。 使用降噪可筛选出所花时间极少的调用关系树条目。 默认筛选器值为 2%，但是可以将它从 0% 调整到 99%。 若要仅查看代码的调用树，请选中“仅我的代码”复选框。 若要查看所有调用树，请清除该复选框。  
  
#### <a name="profile-report"></a>分析报告  
 此选项卡显示与活动图例中的条目对应的报告。 若要显示报告，请选择一个条目。  
  
#### <a name="current-stack"></a>当前堆栈  
 此选项卡显示时间线关系图中某个线程段上的所选点的调用堆栈。 调用堆栈会进行修整以显示与程序相关的活动。  
  
#### <a name="unblocking-stack"></a>取消阻塞堆栈  
 若要查看哪个线程在哪个代码行上对线程取消了阻塞，请选择“取消阻塞堆栈”选项卡。  
  
#### <a name="execution"></a>执行  
 执行报告显示应用程序在执行过程所用的时间的细分。  
  
 若要查找在其中花费执行时间的代码行，请展开调用关系树，然后在调用树条目快捷菜单上，选择“查看源”或“查看调用站点”。 “查看源”会查找执行的代码行。 “查看调用站点”会查找调用执行的代码行的代码行。 如果只有一个调用站点存在，则会突出显示其代码行。 如果存在多个调用站点，则可以在出现的对话框中选择所需站点，然后选择“转到源”按钮以突出显示该调用站点代码。 在查找具有最多实例和/或最大时间的调用站点时，这往往最为有用。 有关详细信息，请参阅[执行分析报告](../profiling/execution-profile-report.md)。  
  
#### <a name="synchronization"></a>同步  
 同步报告显示对同步块负责的调用，以及每个调用堆栈的合计阻塞时间。 有关详细信息，请参阅[同步时间](../profiling/synchronization-time.md)。  
  
#### <a name="io"></a>I/O  
 I/O 报告显示对 I/O 块负责的调用，以及每个调用堆栈的合计阻塞时间。 有关详细信息，请参阅 [I/O 时间（“线程”视图）](../profiling/i-o-time-threads-view.md)。  
  
#### <a name="sleep"></a>休眠  
 休眠报告显示对休眠块负责的调用，以及每个调用堆栈的合计阻塞时间。 有关详细信息，请参阅[休眠时间](../profiling/sleep-time.md)。  
  
#### <a name="memory-management"></a>内存管理  
 内存管理报告显示出现内存管理块的调用，以及每个调用堆栈的合计阻塞时间。 可以使用此信息确定具有过多分页或垃圾回收问题的区域。  有关详细信息，请参阅[内存管理时间](../profiling/memory-management-time.md)。  
  
#### <a name="preemption"></a>优先  
 抢占报告显示其中的系统上进程抢占当前进程的实例以及替换了当前进程中的线程的各个线程。 可以使用此信息确定对抢占负有最多责任的进程和线程。 有关详细信息，请参阅[抢占时间](../profiling/preemption-time.md)。  
  
#### <a name="ui-processing"></a>UI 处理  
 UI 处理报告显示对 UI 处理块负责的调用，以及每个调用堆栈的合计阻塞时间。 有关详细信息，请参阅 [UI 处理时间](../profiling/ui-processing-time.md)。  
  
#### <a name="per-thread-summary"></a>每线程摘要  
 此选项卡显示每个线程在运行、阻塞、I/O 和其他状态下所用的总时间的彩色编码列视图。 各列在底部进行标记。 调整时间线关系图中的缩放级别时，此选项卡会自动更新。 在某些缩放级别，某些线程可能不会显示。 发生这种情况时，省略号会显示在右侧。 如果所需线程未出现，则可以隐藏其他线程。 有关详细信息，请参阅[“每线程摘要”报告](../profiling/per-thread-summary-report.md)。  
  
#### <a name="disk-operations"></a>磁盘操作  
 此选项卡显示代表当前进程的磁盘 I/O 中涉及的进程和线程、它们接触的文件（例如，已加载的 DLL）、读取的字节数以及其他信息。 可以使用此报告评估在执行过程中用于访问文件的时间（尤其是在进程似乎受到 I/O 限制时）。 有关详细信息，请参阅[“磁盘操作”报告](../profiling/disk-operations-report-threads-view.md)。  
  
## <a name="see-also"></a>请参阅  
 [并发可视化工具](../profiling/concurrency-visualizer.md)