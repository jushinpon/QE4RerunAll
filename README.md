# QE4RerunAll

QE 批量重跑自動化系統。

針對已經提交過但需要重新執行的 QE 工作，自動識別 Dead 狀態、修正參數、重新提交。

---

## 程式功能說明

### 工作流程

```
掃描 QE 工作狀態 → 識別 Dead 工作 → 修正 QE 輸入 → 重新提交
```

### 核心腳本

| 腳本 | 功能 |
|---|---|
| `check_QEjobs.pl` | 檢查所有 QE 工作狀態 |
| `check_QEjobs4rerunAll.pl` | 為重跑模式檢查 |
| `ModQEin4Dead4rerunAll.pl` | 修正 Dead 工作 QE 輸入 |
| `Modsh4Dead.pl` | 修正 Dead 工作 slurm 腳本 |
| `submit4allDead.pl` | 重新提交所有 Dead 工作 |

---

## 依賴環境

| 項目 | 需求 |
|---|---|
| 語言 | Perl 5.x |
| DFT | Quantum ESPRESSO |
| 排程 | Slurm |

---

## 使用方法

```bash
perl check_QEjobs.pl               # 檢查狀態
cat QEjobs_status/Dead.txt         # 查看 Dead 列表
perl ModQEin4Dead4rerunAll.pl     # 修正
perl submit4allDead.pl            # 重新提交
```

---

## AI Agent 操控指南

```
任務: 重新跑所有失敗的 QE 工作
步驟:
1. perl check_QEjobs.pl
2. cat QEjobs_status/Dead.txt 確認需修復的工作
3. perl ModQEin4Dead4rerunAll.pl 自動修正
4. perl submit4allDead.pl 重新提交
5. perl check_QEjobs.pl 確認重新提交成功
```
