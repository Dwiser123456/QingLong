### 🧾 魔方财务每日签到脚本
一个用于自动完成魔方财务插件签到的 Python 脚本，支持多账户执行，基于 requests 模拟请求签到接口。

**✨ 功能介绍**
✅ 支持多个账号循环签到

🔐 使用 Cookie 登录，无需账号密码

🕘 自动记录签到时间和返回信息

🛠 可配合定时任务（如 crontab）实现每日自动运行

**📦 环境依赖**
确保已安装 Python（推荐版本：3.6+）

安装所需依赖：

pip install requests


**⚙️ 使用配置**
1. 获取 UID 和 Cookie<br>
登录你的魔方财务面板（如：https://example.com）<br>
打开浏览器开发者工具（F12）<br>
访问此路径：<br>
https://your-domain.com/addons?_plugin=4&_controller=index&_action=index<br>
在请求列表中找到该请求，复制 Request Headers 中的 Cookie<br>
此页面 URL 参数中的 uid=XXXX，就是你的 UID

2. 编辑脚本配置<br>
在 accounts 数组中，添加多个账号信息：

```
accounts = [
    {
        "uid": "12345",
        "cookie": "your_cookie_1_here"
    },
    {
        "uid": "67890",
        "cookie": "your_cookie_2_here"
    }
]
```

3. 修改签到地址（如有需要）<br>
将以下 url 替换为你魔方财务插件的实际签到地址：<br>
url = "https://your-domain.com/addons?_plugin=4&_controller=index&_action=index"


**📄 返回信息示例**

```
成功：
uid=12345 签到结果: {'status': 1, 'msg': '签到成功', 'credit': '5'}
```
```
失败或 Cookie 失效：
uid=12345 签到出错: Expecting value: line 1 column 1 (char 0)
```
