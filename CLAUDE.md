# securag

內部資安政策與 SOP 的對話式問答，檢索與生成全在本機。前端 Vue（`frontend/src`，三個路由：/、/documents、/settings），後端 FastAPI，Airflow 監看 `watched_docs/`。維護模式。

- 狀態與下一步看 `HANDOFF.md`。
- 做頁面前先讀 `DESIGN.md`（設計合約，數值為準；「決定」欄是 TODO 的還沒談定）。
- port 8310–8313、15432（`~/Projects/PORTS.md`）；`securag.test`、`api.securag.test`、`airflow.securag.test` 經 Caddy 轉進來；Vite 的 `allowedHosts` 要有這些名字。
- LLM 走 host 的 ollama（容器內用 `host.docker.internal:11434`），compose 裡不開 ollama。
- 家裡層規則在 `~/Projects/claude-config`，這裡只寫差異。
