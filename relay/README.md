# 🌐 News Relay — 外网IP封锁信源中继

绕过阿里云VPC IP封锁，通过GitHub Actions US runner获取BBC/Reuters/Guardian等站点内容。

## 使用方式

1. 把目标URL写入 `relay/request.md`
2. commit + push
3. 等待~30秒，workflow自动执行
4. 从 `relay/responses/` 读结果

## 示例

```bash
echo "https://www.bbc.com/sport/football" > relay/request.md
git add relay/request.md
git commit -m "relay: bbc sport"
git push
# 30秒后：
# curl https://raw.githubusercontent.com/k286c7hg65-hub/sports-heroes/main/relay/responses/
```

## API触发（备选）

需GitHub CLI登录：
```bash
gh workflow run news-relay.yml -f url="https://www.reuters.com/sports/"
```
