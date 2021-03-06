#### Deploy / 部署
[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?button-url=https%3A%2F%2Fgithub.com%2FTrumpy%2Fbrook-heroku&template=https%3A%2F%2Fgithub.com%2FTrumpy%2Fbrook-heroku)

#### Usage / 用法
```
Brook wss: replace [app-name], [/ws] and [password]
要把 [app-name] 和 [/ws] 和 [password] 改成自己的

Server:   wss://[app-name].herokuapp.com:443[/ws]
Password: [password]
```

```
Available only if app_name is specified
只有指定了app_name才可用，不然404 Not Found

QR code:    https://[app-name].herokuapp.com:443/[password]/qr.png
Brook link: https://[app-name].herokuapp.com:443/[password]/link.txt
```

======================================================================

#### Cloudflare workers 加速，把第四行的[app-name]改成自己的 / (Recommended if you are in China)

去 [cloudflare workers](https://dash.cloudflare.com/) 加入以下內容
```
addEventListener(
  'fetch',event => {
     let url=new URL(event.request.url);
     url.hostname='[app-name].herokuapp.com';
     let request=new Request(url,event.request);
     event.respondWith(
          fetch(request)
    )
  }
)
```
用法
```
Brook wss: replace [xxx], [yyy], [/ws] and [password]
把cf workers的域名 [/ws] [password]那些都改成自己的

Server:   wss://[xxx].[yyy].workers.dev:443[/ws]
Password: [password]
```

======================================================================

### Logs
`heroku logs --tail -a [app-name]`
