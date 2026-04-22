# TTS Emotion Router (Felis Abyssalis fork)

- **`tts_say` 解析改进**：支持用 `<...>` 包裹文本，保留空格和多行内容。换行会被 normalize 为单个空格。
  ```
  tts_say <Noir。

  我的Noir。>
  ```
  不带尖括号时行为不变（向后兼容，但只能读到第一个空格前的内容）。

- **`tts_speak` LLM 工具重写**：改用 `return` 替代原版的 `yield` + `clear_result` 流程，修复语音发送后上下文丢失的问题。

- **tool_call 历史清洗**：在 `on_llm_request` 中自动剥离对话历史里残留的 `tts_speak` tool_call/tool_result 序列，防止 AstrBot 重建历史时触发 API 409 (tool binding mismatch) 错误。
