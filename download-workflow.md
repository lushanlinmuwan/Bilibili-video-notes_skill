# PeanutDL 视频下载详细流程

## 网站信息



* 地址：[https://peanutdl.com/zh/bilibili](https://peanutdl.com/zh/bilibili)

* 支持平台：B 站、抖音、TikTok

* 默认清晰度：720P（MP4 格式）

## 完整步骤

### 1. 打开网站



```
import aha_browser_use as bu

bu.navigate("https://peanutdl.com/zh/bilibili")
bu.wait_for_load(timeout=15)
```

### 2. 处理弹窗



* **Cookie 弹窗**：如果出现 "由你决定 Cookie 的使用" 弹窗，点击 "接受全部 Cookie"

* **推荐客户端弹窗**：点击关闭按钮（X）即可，不需要下载客户端

### 3. 输入链接



```
# 找到输入框（通常是 n28 或类似的 ref）
bu.type("n28", "<B站视频链接>", submit=False)
bu.wait_for_load(timeout=1)

# 点击"获取视频"按钮
bu.click("n29")
bu.wait_for_load(timeout=15)
```

### 4. 验证码处理

**如果出现验证码弹窗**：



* 立即调用 `interaction.request_action`，类型为 `browserControl`

* 提示用户："PeanutDL 网站出现了人机验证，请手动完成验证后交回控制权"

* 用户完成后，重新 `bu.resync()` 并观察页面

**不要尝试自己绕过验证码**，这是硬性规则。

### 5. 找到下载链接

验证码通过后，页面会显示：



* 视频播放器

* 视频标题、作者、时长、大小信息

* 一个 "下载" 链接（`<a>` 标签）



```
# 方法1：通过快照找到下载链接的 ref
snapshot = bu.snapshot(within="viewport", view="interactive", max_chars=5000)
# 在输出中找 "下载" 字样，对应的 ref 类似 n179

# 方法2：用 find 直接搜索
matches = bu.find("下载", search_type="interaction", limit=5)
print(matches)
```

### 6. 下载视频



```
# 直接用 download 方法下载
record = bu.download(download_ref, timeout=60)
print(record)
# 返回示例：
# {
#   'state': 'completed',
#   'url': 'https://...mp4',
#   'filename': '856871210-1-192.mp4',
#   'path': 'C:\\Users\\xxx\\Downloads\\856871210-1-192.mp4',
#   'bytes': 115977115
# }
```

### 7. 移动到目标文件夹

下载完成后，文件默认在 Downloads 文件夹，需要移动到用户指定的文件夹：



```
Move-Item -Path "<下载的文件路径>" -Destination "<用户指定文件夹>\<有意义的文件名>.mp4" -Force
```

**命名建议**：



* 单集：`课程名_第X集.mp4`

* 多集：`课程名_第X集_标题.mp4`

* 不要用原始的数字文件名，要让用户一眼看懂是什么

## 分 P 链接处理

B 站分 P 链接格式：



```
https://www.bilibili.com/video/BVxxxxxxxxxx/?p=6
```

提取 BV 号：从链接中提取 `BV` 开头的字符串

分 P 号：`p=` 后面的数字

批量下载时：



1. 先询问用户总共有多少 P

2. 依次替换 `?p=1`、`?p=2`... 直到最后一集

3. 每集单独走完整流程

## 注意事项



1. **不要在同一个标签页反复输入链接**：如果按钮变灰，刷新页面重试

2. **下载链接有时效**：解析出来的下载链接有效期约几小时，尽快下载

3. **720P 是默认**：网站会自动提供最高可用清晰度，通常是 720P

4. **文件大小参考**：15 分钟左右的 720P 视频约 100-120MB