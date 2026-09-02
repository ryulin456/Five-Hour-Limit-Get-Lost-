# Five-Hour Limit, Get Lost!（原生 Windows 轻量版）

下载或克隆项目后，在项目目录运行 `install.ps1`，程序会在当前用户桌面创建 **Five-Hour Limit, Get Lost!** 快捷方式。也可以双击 `start-five-hour-limit-get-lost.bat` 直接运行。程序只调用本机 `codex.exe`，不使用远程服务，也不读取 Claude 数据。

监管任务时有两种模式：

- 自动检测：尝试读取 Codex 本地日志里的限额信息。
- 手动五小时循环：用时间选择器选择一个恢复的“时:分”，不需要填写年月日；界面会预览连续的 5 小时计划（例如 20:32、01:32、06:32、11:32、16:32、21:32），程序会在每个周期重新尝试仍未完成的监控任务，并在恢复后按“缓冲分钟”再启动任务。

时间依据是 Windows 本机系统时间，不联网取时间。建议缓冲分钟保留默认的 2 分钟。

任务队列保存在 `%LOCALAPPDATA%\CodexQueueCN\queue.json`。成功输出的会话 ID 会用于 `codex exec resume`。程序不会绕过五小时或每周限制，也不会自动打开危险权限模式。
