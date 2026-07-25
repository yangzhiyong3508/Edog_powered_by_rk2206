# EDOG powered by RK2206

智能四足机器人（小凌派 RK2206 + 鸿蒙）毕设 monorepo。

## 仓库结构（git submodule）

| 目录 | 仓库 | 说明 |
|------|------|------|
| `Application/` | [Application](https://github.com/yangzhiyong3508/Application) | HarmonyOS 手机 App |
| `SpringBoot/` | [SpringBoot](https://github.com/yangzhiyong3508/SpringBoot) | 后端（语音/IoTDA/扣子） |
| `DeepLearning/` | [DeepLearning](https://github.com/yangzhiyong3508/DeepLearning) | YOLO + DeepSORT 跟随与图传转发 |
| `ESP32/` | [ESP32](https://github.com/yangzhiyong3508/ESP32) | ESP32-CAM 图传固件 |
| `Docker_Edog/` | [edog_project_docker](https://github.com/yangzhiyong3508/edog_project_docker) | 狗端 edog_project 固件源码 |

## 克隆

```bash
git clone --recurse-submodules https://github.com/yangzhiyong3508/Edog_powered_by_rk2206.git
cd Edog_powered_by_rk2206
# 若已克隆未带子模块：
git submodule update --init --recursive
```

## 安全说明

- **不要提交密钥**。各子仓已配置 `.gitignore`。
- SpringBoot 密钥模板：`SpringBoot/config/application-secrets.example.yaml`
- 固件本地配置模板：`Docker_Edog/include/edog_config.local.example.h`
- 模型权重（`.pt`）不入库，见 `DeepLearning/weights/README.md`

## 分支

- `main`：当前最新架构（submodule）
- `archive/old-main`：历史主分支归档

## License

见各子仓库。
