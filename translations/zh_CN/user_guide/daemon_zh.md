# 守护进程化

当一个 `Pingora` 服务器被配置为作为`守护进程`运行时，在其引导完成后，它将自行移动到后台，并可选择切换到配置的用户和组下运行。在这种情况下，`pid_file` 选项非常方便，用户可以跟踪后台守护进程的 `PID`。

`守护进程化`还允许服务器执行特权操作，比如加载密钥，然后在从网络接受任何请求之前切换到非特权用户。

这个过程发生在 `run_forever()` 调用中。因为`守护进程化`涉及到 `fork()`，所以在此调用之前创建的某些线程可能会丢失。
