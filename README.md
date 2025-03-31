# BRX-SCAN

一个基于Python的高性能端口扫描工具，支持多线程扫描、服务识别等功能。

## 功能特点

- 多线程端口扫描
- 支持多种扫描方式 (TCP, SYN, FIN, NULL, XMAS, UDP)
- 自动服务识别
- 进度条显示
- 支持扫描结果导出
- 灵活的端口范围设置

## 依赖安装

```bash
# 基础依赖
pip install tqdm

# 高级功能依赖(可选)
pip install scapy
```

## 使用方法

### 基本扫描
```bash
# 扫描默认端口(1-1024)
python main.py example.com

# 指定端口范围
python main.py example.com -s 1 -e 65535

# 指定特定端口
python main.py example.com -p 80,443,8080
```

### 高级选项
```bash
# 调整扫描速度(1-5)
python main.py example.com -T 4

# 显示详细信息
python main.py example.com -v

# 随机化端口顺序
python main.py example.com -r

# 服务版本检测
python main.py example.com --service-detection
```

## 参数说明

| 参数 | 说明 | 默认值 |
|------|------|--------|
| `-p, --ports` | 指定端口列表 | 无 |
| `-s, --start-port` | 起始端口 | 1 |
| `-e, --end-port` | 结束端口 | 1024 |
| `-t, --timeout` | 超时时间(秒) | 1.0 |
| `-T, --timing` | 扫描速度(1-5) | 3 |
| `-v, --verbose` | 显示详细信息 | False |
| `-r, --randomize` | 随机化端口顺序 | False |
| `-f, --force` | 强制扫描大型网络 | False |

## 扫描速度说明

- T1: 极慢 - 最少资源占用，最隐蔽
- T2: 慢速 - 低资源占用
- T3: 正常 - 默认扫描速度
- T4: 快速 - 高性能主机推荐
- T5: 极快 - 可能导致结果不准确

## 输出示例

```
[*] 开始扫描主机: 192.168.1.1
[+] 80/tcp 开放 - HTTP
[+] 443/tcp 开放 - HTTPS
[+] 22/tcp 开放 - SSH

[*] 扫描完成: 发现 3 个开放端口
[*] 扫描用时: 2.35 秒
```

## 注意事项

1. SYN、FIN、NULL、XMAS扫描需要root/管理员权限
2. 高速扫描可能触发目标主机的IDS/IPS系统
3. 建议在授权环境下使用
4. 部分功能需要安装scapy库
