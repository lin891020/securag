# HANDOFF

最後更新：2026-11-07。

## 現在在哪一步

**封存 2026-11-07**：停在「專案已完成，維護模式」（2026-09-20，CI 綠、backend 132 passed、frontend 6 passed）。為什麼停：作品集已成形，兩個月沒動、沒在跑；Mike 2026-11-07 盤點時決定封裝。重啟先做：`docker compose up` 後跑一次測試確認還綠（image 10.7 GB 與 3 個 volume 還在本機）。dev.test 的啟動按鈕與 PORTS.md 的 8310–8313、15432 保留。以下是封存前的狀態。

專案已完成，維護模式。2026-09-20 補了 CI（`.github/workflows/tests.yml`）：backend 測試不用 docker 也能跑，frontend 的 vitest 也跑。

## 已驗證

- CI 綠燈：backend 132 passed、frontend 6 passed（https://github.com/lin891020/SecuRAG/actions/runs/35518289019）
- 本機不用 docker 跑 backend：`PYTHONPATH=../dags SECURAG_UPLOAD_DIR=/tmp/x python -m pytest tests/` → 132 passed

## 只是寫了、還沒驗證

- （無）

## 已知但沒修

- `tests/test_dag_ingest.py` 把 `/dags` 寫死在 `sys.path`；`Settings.upload_dir` 預設 `/app/uploads`。CI 用環境變數繞過，沒改測試或程式。
- 5 個 `RuntimeWarning: coroutine ... was never awaited`（`app/api/chat.py:63`、`audit_service.py:20`），是測試裡 AsyncMock 的用法，不影響結果。
