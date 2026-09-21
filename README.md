
gitee.com 是国内域名，DNS 永远返回真实 IP。把 https://raw.githubusercontent.com/Loyalsoldier/geoip/release/text/cn.txt 自动上传到 gitee 库 imno/kexue 根目录，命名 chinaIP-cn.txt

方案：GitHub Actions 定时同步。链路完全在云端：`GitHub Actions 拉 cn.txt（同域无障碍）→ 调 gitee API 写入`，家庭网络只负责最后一步 ikuai-bypass 从 gitee 拉。


1. GitHub 建一个私有仓库（比如 `geoip-mirror`），**Settings → Secrets and variables → Actions → Repository secrets** → 新建 secret：`GITEE_ACCESS_TOKEN` = `你的 gitee token`

1. 新建 workflow 文件

1. Actions 页手动 Run workflow 验证一次——看到"上传成功"且 gitee 库 imno/kexue 根目录，命名 `chinaIP-cn.txt`，链路即通。私有仓库每月 2000 分钟免费额度，这个任务每次不到 1 分钟。
