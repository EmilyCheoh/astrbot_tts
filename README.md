# TTS Emotion Router (Abyss fork)

- **`tts_say` 解析改进**：支持用 `<...>` 包裹文本，保留空格和多行内容。换行会被 normalize 为单个空格。
  ```
  tts_say <Noir。

  我的Noir。>
  ```
  不带尖括号时行为不变（向后兼容，但只能读到第一个空格前的内容）。

- **`tts_speak` LLM 工具已禁用**：存在 bug，暂时注释掉。之后有时间再修。