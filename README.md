# EDOG powered by RK2206

智能四足机器人毕设总仓库（**软通动力通晓开发板 RK2206** + OpenHarmony LiteOS + HarmonyOS App + Spring Boot + 视觉跟随）。

> 狗端硬件为软通动力（iSoftStone）**通晓**开发板（RK2206），不是小凌派。

## 系统架构

```
手机 App (HarmonyOS)
    │  HTTP / WS
    ▼
Spring Boot 后端 ──► 华为云 IoTDA / 讯飞 ASR·TTS / 扣子 Agent
    ▲
    │ 跟随指令 /tracker
视觉 PC (YOLO+DeepSORT) ◄── ESP32-CAM JPEG 图传
    ▲
    │ MQTT 命令
狗端固件 edog_project (RK2206 12DOF 步态)
```

## 子模块结构

| 目录 | 仓库 | 说明 |
|------|------|------|
| `Application/` | [Application](https://github.com/yangzhiyong3508/Application) | HarmonyOS 手机端：遥控、陪伴、调参、舵机校准 |
| `SpringBoot/` | [SpringBoot](https://github.com/yangzhiyong3508/SpringBoot) | 后端：语音、IoTDA 下发、扣子会话、调试台 |
| `DeepLearning/` | [DeepLearning](https://github.com/yangzhiyong3508/DeepLearning) | 视觉检测跟踪与图传转发（8765/8766） |
| `ESP32/` | [ESP32](https://github.com/yangzhiyong3508/ESP32) | ESP32-CAM + OV3660 图传固件 |
| `Docker_Edog/` | [edog_project_docker](https://github.com/yangzhiyong3508/edog_project_docker) | 狗端 `edog_project` 固件源码 |

## 克隆

```bash
git clone --recurse-submodules https://github.com/yangzhiyong3508/Edog_powered_by_rk2206.git
cd Edog_powered_by_rk2206

# 已克隆但未拉子模块时：
git submodule update --init --recursive
```

## 更新子模块到最新 main

```bash
git submodule update --remote --merge
git add Application SpringBoot DeepLearning ESP32 Docker_Edog
git commit -m "chore: bump submodules"
git push origin main
```

## 安全说明

- **禁止提交密钥**。各子仓均有 `.gitignore`。
- 后端密钥模板：`SpringBoot/config/application-secrets.example.yaml`
- 固件本地配置模板：`Docker_Edog/include/edog_config.local.example.h`
- 模型权重（`.pt`）不入库，见 `DeepLearning/weights/README.md`

## 分支

| 分支 | 说明 |
|------|------|
| `main` | 当前 monorepo + submodule 架构 |
| `archive/old-main` | 历史主分支归档 |

## 文档入口

请分别阅读各子仓库 `README.md` 的编译、运行与部署说明。
