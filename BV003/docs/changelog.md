# BV003 修订记录

本文档记录 BV003 硬件设计、BOM 及文档的变更历史。

## 格式说明

- **日期**：变更发布或验证日期
- **版本**：硬件或 BOM 版本标识（如有）
- **状态**：`已验证` / `待验证` / `已废弃`

---

## 2026-08-01 — BV003REV1.0 初始发布

**版本**：REV 1.0  
**状态**：待验证

> **警告：本版本为未验证原型，请勿期望直接可用。**

- 上传 KiCad 工程至 `BV003/pcb/BV003REV1.0/`
- 调整仓库目录结构，BV003 资料归集至 `BV003/` 目录
- 新增 `BV003/docs/` 文档目录

**设计概要（未经实机验证）：**

- 基于 [NerdOCTAXE-Gamma](https://github.com/Patsch91/NerdOCTAXE-Gamma)（8× BM1370 多 ASIC 矿机）改板
- 主要变更：ASIC 改为 4× BM1373；电源改为 TPS546 四相（上游 Rev3.4 为六相 Buck）
- 4× BM1373 ASIC（`bm1373_1` ~ `bm1373_4` 子图）
- TPS546 四相电源（`power.kicad_sch`）
- T-Display-S3 显示与控制
- W5500 以太网（`w5500.kicad_sch`）
- 电平转换（`level_shifter.kicad_sch`）

**已知限制：**

- 尚未完成打板、焊接或上电测试
- 无性能、功耗、散热数据
- BOM 可能尚未同步发布或完善
- KiCad 工程中 `plot` 路径预留了 REV1.1，后续改版待补充

---

## 与 BV001 / BV002 的关系

| 项目 | BV001 | BV002 | BV003 |
|------|-------|-------|-------|
| 上游参考 | [qaxe](https://github.com/shufps/qaxe) | — | [NerdOCTAXE-Gamma](https://github.com/Patsch91/NerdOCTAXE-Gamma) |
| 验证状态 | 已验证 | 未验证原型 | 未验证原型 |
| ASIC 数量 | 1× BM1373 | 2× BM1373 | 4× BM1373 |
| 适用场景 | 可参考复刻 | 实验性设计 | 实验性设计 |

如需实际可用的参考设计，请优先参考 **BV001**。

---

## 上游参考

BV003 基于 **[NerdOCTAXE-Gamma](https://github.com/Patsch91/NerdOCTAXE-Gamma)** 修改而来。该项目是 8× BM1370 多 ASIC 矿机，源自 NerdQaxe 生态；当前上游版本为 Rev-3.4（六相 Buck、ASIC 内部温度读取等）。

BV003 相对上游的主要改动：

- ASIC：BM1370 × 8 → **BM1373 × 4**
- 电源：六相 Buck → **TPS546 四相**
- 其余模块（T-Display-S3、多 ASIC 互联架构等）沿用上游设计思路

上游修订历史请参阅 [NerdOCTAXE-Gamma 仓库](https://github.com/Patsch91/NerdOCTAXE-Gamma)。固件方面，上游使用修改版 [ESP-Miner-NerdQAxe+](https://github.com/shufps/ESP-Miner-NerdQAxe-plus)（AxeOS），BV003 移植适配 **尚未验证**。
