# lemon-paperplane-plugin-keymap-eclipse

Lemon Paperplane 文件编辑器的 Eclipse 快捷键方案（插件 id `keymap-eclipse`）。内置随 App 安装（默认方案：Mac 用 eclipse-macos，其他平台用 eclipse-windows，两版互相都能选）。

- keymaps/eclipse-macos.json、keymaps/eclipse-windows.json：以 Eclipse 官方 Mac / Windows 默认键位为准，覆盖常用编辑、查找、导航、标签页命令。
- 没有业务逻辑：方案在 `plugin.json` 的 `contributes.keymaps` 里声明；这是纯声明插件：`plugin.json` 不写 `executable`，没有程序，内核从不启动进程。
- JSON 方案格式：`{"bindings": [{"key": "Cmd-d", "command": "deleteLine"}]}`，键名用 CodeMirror 写法（`Cmd`/`Ctrl`/`Alt`/`Shift`，不用 `Mod`，多键序列用空格分隔），`command` 取编辑器命令表 `lemon-paperplane-main/lemon-paperplane-main-editor/COMMANDS.md`。编辑器工程的 `npm test` 会检查方案里的命令都存在。
- module 方案由编辑器工程的 `node scripts/build-lang.mjs keymap-eclipse` 生成（CodeMirror 运行时取自编辑器的 `window.cm`）。
