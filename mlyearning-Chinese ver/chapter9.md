## 9. 优化和满足指标

这是组合多个评估指标的另一个方法。

假定你同时关心算法的准确率和运行时间，你需要从下列三个分类器中选一个最好的。

分类器|准确率|运行时间
---|---|---
A|90%|80ms
B|92%|895ms
C|95%|1500ms

此时，将准确率和运行时间放入单一公式计算得到单一指标的做法似乎并不合适，比如：

$$Accuracy-0.5 \times RunningTime$$

下面，是你可以尝试的操作：首先，设定一个“可接受”的运行时间，假定说只要是运行时间在100ms以内的算法都是可以接受的。然后，从满足时间要求的分类器里，最大化准确率。在这里，“运行时间”就是“满足指标”——你的分类器只需要在这个指标上表现的足够好就行了（运行时间低于100ms），而“准确率”就是“优化指标”。

当你正在权衡N个不同的标准的时候，比如，一个模型的二进制文件的大小（这对于一个移动App来说很重要，因为用户并不想下载很大的App）、运行时间和准确率。可以考虑将其中的N-1个标准设置为“满足指标”，也就是说，只需要这些条件满足一定的值就行了。然后将剩下那个设置为“优化指标”。还是上头的例子，可以将模型的二进制文件大小和运行时间都设置为“满足指标”，并尝试在这些约束条件下不断优化准确率（优化指标）。

作为本节最后一个例子，假设你在搭建一个硬件设备，该设备使用麦克风来监听用户说出的某个特定的唤醒词(Wakeword)，从而唤醒系统。就好比亚马逊的“Echo”听到“Alexa”、苹果Siri听到“hey Siri”、百度应用听到“你好百度”都会唤醒系统一样。你不仅需要关心假正例( False Positive Rate)——系统在用户没有人说出唤醒词的时候被唤醒，而且还要关心假反例(False Negative Rate)——当用户说出唤醒词系统却没有被唤醒。那么，对于该系统的性能而言，一个合理的优化目标就是最大限度的减少假反例的比例（优化指标），同时满足每隔24小时最多出现一个假正例（满足指标）即可。
