# Legacy 归档区（M1 任务产物）

由 OpenHands 在 M1 任务中物理迁出 Lite 旧代码。
约定结构：

```
drafts/legacy/
├── utopia/           # utopia_service.py + chat_extractor.py + routers/utopia.py + models/utopia.py
├── psychology/       # psychology_engine.py + models/user_profile.py
├── collision/        # collision_engine.py + models/thought_collision.py
├── agent/            # agent_runtime.py + sub_agent_coordinator.py + dual_key.py +
│                     # auto_mode.py + skill_extractor.py + curator.py
├── approval/         # approval_gate.py + models/{pending_approval,approval_log}.py
├── queue/            # task_queue.py + message_priority.py + models/task_queue.py
├── classification/   # classification_service.py + models/classification_node.py
├── search/           # layered_search.py
├── vector/           # vector_store.py
├── feedback/         # feedback_service.py + models/feedback.py
├── tools/            # tool_service.py + models/tool.py
├── llm/              # model_service.py + llm/mimo_adapter.py + models/model_profile.py
├── integrations/     # integration_service.py + models/external_integration.py
├── i18n/             # i18n_service.py + middleware/locale.py + i18n/*.json
├── ops/              # startup_checker.py
├── snapshot/         # snapshot_service.py + models/snapshot.py
└── scheduler/        # idle_scheduler.py
```

每个迁出文件顶部必须加注释：
```python
# 归档自 MBclaw-Lite@<commit-hash>, 路径 app/services/<file>.py
# 移出原因：见 MBclaw-Memory/decisions/rejected/ 或 MBclaw/design/audit/SURVIVAL-REVIEW-2026-06-21.md
# R0 状态：移出 Core；R2 重启或永久放弃见上述文档
```

不修改任何代码内容。OpenHands 用 MBclaw-Lite/PROMPTS-FOR-EXECUTORS.md 提示词 3 执行。
