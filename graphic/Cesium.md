# Cesium Ion 上传发布过程


[Cesium Ion](https://cesium.com/ion)是Cesium的一个模型发布平台，提供上传模型、影像、地形的数据，并以服务的方式提供前端Cesium加载，同时，可以对访问进行权限控制。

Cesium Ion 3DTile发布的具体过程如下

## 第一步

先调用 `POST`  `https://api.cesium.com/v1/assets` 创建一个 asset对象

request body

```json
{
    "name": "AGI_HQ",
    "description": "",
    "type": "3DTILES",
    "options": { 
        "sourceType": "KML" 
    } 
}
```

response body
```json
{
    "assetMetadata": {
        "id": 23200,
        "type": "3DTILES",
        "name": "AGI_HQ",
        "description": "",
        "bytes": 0,
        "attribution": "",
        "dateAdded": "2019-05-10T10:34:01.838Z",
        "status": "AWAITING_FILES",
        "percentComplete": 0,
        "userId": 9665,
        "labels": [],
        "isPremium": false,
        "isExternal": false,
        "error": null,
        "progressMessage": null
    },
    "uploadLocation": {
        "bucket": "assets.cesium.com",
        "prefix": "sources/23200/",
        "accessKey": "ASIATXRQLSFCEEPSTYJN",
        "secretAccessKey": "313FV4/RjM1ieYDvpUaHAw3tHiC6jZCvvyDe+bW1",
        "sessionToken": "FQoGZXIvYXdzEIz//////////wEaDK+8dPPHMzCAM1BD2iKtAvcKso6//T30oLZnbC1NtgkKvpinuF519tTu9JXiN5BlAEOi751ARNicYKcL5+uPB8jT+evI2g2ocap3v/TxihI8iDD9NWQq5QRNuOWjUvE+eJN4QVQziq3RlFlxDi7plq8Z00MbTwMQ7cBe9OSqz3fsNJXDOQ7XPzfrLF7BywEoeWZZv0FcH/tZzw7xgsvqCTW+cENC6WaAoingcPb+Nh/2mPvF5UUgRDwtIeQkj1/8j/VALccbSe/G1KtPusMcE5LOEB7PsEbsoQTIL7itY+scy6jt+m0tRpC5IezW3oxLzMJQ+0J9wXs1tM6Cr797Nzw/v7BAfMv+HCc/pkeNSvoqXKzHdsx7uy2NYBly4epMGn0niRymg3Km0SrNC1zGpoA2JkEHH6OWxXa03DIomafV5gU="
    },
    "onComplete": { "method": "POST", "url": "https://api.cesium.com/v1/assets/23200/uploadComplete", "fields": {} }
}
```
在响应体中，

status 有几种状态：

1. AWAITING_FILES : 表示等待文件上传
2. NOT_STARTED    : 表示原模型文件以及上传，但还没开始进行格式转换
3. IN_PROGRESS    : 表示正在处理，progressMessage: "Retrieving data for processing..."
    IN_PROGRESS    : 正在处理  percentComplete: 39，progressMessage: "Tiling..."
4. COMPLETE       : 完成  Deploying new tileset for streaming...

## 第二步 上传文件

调用 `POST`  `https://s3.amazonaws.com/assets.cesium.com/sources/23200/AGI_HQ.kmz?uploads`

新建一个上传实例，

响应体
```xml
<?xml version="1.0" encoding="UTF-8"?>
<InitiateMultipartUploadResult xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    <Bucket>assets.cesium.com</Bucket>
    <Key>sources/23200/AGI_HQ.kmz</Key>
    <UploadId>ODoOI_XIwoY3ZQ625ccISZ12HuOZjyKgUcasPJdOVTfQC8QDvUcRy.gy2UPirO_VM59q3XqOQGEHoMEFclplY.3mrsg_wa7Qv1heprtqGrivDS8rVIadBIGhLJM5RC0EsjOIMVkP5tvrjNYxCsKADg--</UploadId>
</InitiateMultipartUploadResult>
```

然后，根据返回的UploadId上传文件

调用 `PUT` `https://s3.amazonaws.com/assets.cesium.com/sources/23200/AGI_HQ.kmz?partNumber=2&uploadId=ODoOI_XIwoY3ZQ625ccISZ12HuOZjyKgUcasPJdOVTfQC8QDvUcRy.gy2UPirO_VM59q3XqOQGEHoMEFclplY.3mrsg_wa7Qv1heprtqGrivDS8rVIadBIGhLJM5RC0EsjOIMVkP5tvrjNYxCsKADg--`

请求体（二进制数据）
```binary
PKlJMr= ù,SIû
AGI_HQ.dae¤ÉåH×ð©f]·ÃFBÌ£
T@
h
```

等到文件上传完毕后，调用结束

调用 `POST`  `https://s3.amazonaws.com/assets.cesium.com/sources/23200/AGI_HQ.kmz?uploadId=ODoOI_XIwoY3ZQ625ccISZ12HuOZjyKgUcasPJdOVTfQC8QDvUcRy.gy2UPirO_VM59q3XqOQGEHoMEFclplY.3mrsg_wa7Qv1heprtqGrivDS8rVIadBIGhLJM5RC0EsjOIMVkP5tvrjNYxCsKADg--`
请求体
```xml
<CompleteMultipartUpload xmlns="http://s3.amazonaws.com/doc/2006-03-01/"><Part><ETag>"b7baeacb18c57ca6e59b0284f0f6d297"</ETag><PartNumber>1</PartNumber></Part><Part><ETag>"4a6c8a62d5c0860f1131b508ef698f11"</ETag><PartNumber>2</PartNumber></Part></CompleteMultipartUpload>
```

响应体
```xml
<?xml version="1.0" encoding="UTF-8"?>

<CompleteMultipartUploadResult xmlns="http://s3.amazonaws.com/doc/2006-03-01/"><Location>https://s3.amazonaws.com/assets.cesium.com/sources%2F23200%2FAGI_HQ.kmz</Location><Bucket>assets.cesium.com</Bucket><Key>sources/23200/AGI_HQ.kmz</Key><ETag>&quot;d24638afe4c47ae92faaf2ec4b750f92-2&quot;</ETag></CompleteMultipartUploadResult>
```

## 第三步 更新asset的状态

调用 `POST` `https://api.cesium.com/v1/assets/23200/uploadComplete`
无请求头和响应头


## 第四步 查看asset的状态

调用 `GET`  `https://api.cesium.com/v1/assets/23200`

响应体
```json
{
    "id": 23200,
    "type": "3DTILES",
    "name": "AGI_HQ",
    "description": "",
    "bytes": 7273836,
    "attribution": "",
    "dateAdded": "2019-05-10T10:34:01.838Z",
    "status": "NOT_STARTED",
    "percentComplete": 0,
    "userId": 9665,
    "labels": [],
    "isPremium": false,
    "isExternal": false,
    "error": null,
    "progressMessage": null
}
```

间隔5秒，发起一次请求查看asset状态，直到状态变为"COMPLETE"


## 第五步 获取Tile.json描述信息

当瓦片发布完后，可以`GET`调用 `https://api.cesium.com/v1/assets/23200/endpoint` 获取终端信息
请求头
```yml
Accept: application/json,*/*;q=0.01
Origin: https://cesium.com
Referer: https://cesium.com/ion/assets/23200
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.131 Safari/537.36
```

响应头
```yml
access-control-allow-credentials: true
access-control-allow-origin: https://cesium.com
access-control-expose-headers: link
cache-control: no-cache
content-encoding: gzip
content-type: application/json
date: Fri, 10 May 2019 10:34:44 GMT
server: nginx/1.14.1
status: 200
via: 1.1 f722e1639e83e9d775bb4fbed4fbcc4e.cloudfront.net (CloudFront)
x-amz-cf-id: 4HSOlW4h0wxP1UXbKF6tz7nH6kUbtzvFqrfHtZEe2xekjWtFSkWCUQ==
x-cache: Miss from cloudfront
```

响应体
```json
{
    "type": "3DTILES",
    "url": "https://assets.cesium.com/23200/tileset.json?v=1",
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJhNTc1ZmI1YS0zODkxLTQ3ZGUtYTFkNi00Y2Q0YTFhYzBlZTEiLCJpZCI6OTY2NSwiYXNzZXRzIjp7IjIzMjAwIjp7InR5cGUiOiIzRFRJTEVTIn19LCJzcmMiOiIyZmFmMmI1YS0wMDA4LTQ5YmQtYjAzNi0xYTNkNzUyODA2NTEiLCJpYXQiOjE1NTc0ODQ0ODQsImV4cCI6MTU1NzQ4ODA4NH0.GVpBK9gf1bNhydj_3xosPg0pVpoYC1GAo9JoOSPE8Oo",
    "attributions": [
        {
            "html": "<span><a href=\"https://cesium.com\" target=\"_blank\"><img alt=\"Cesium ion\" src=\"https://assets.cesium.com/ion-credit.png\"></a></span>",
            "collapsible": false
        },
        {
            "html": "<a href=\"https://cesium.com/pricing/\" target=\"_blank\">Upgrade for commercial use.</a>",
            "collapsible": false
        }
    ]
}
```

如果文件没用上传完，那么会显示
```json
{"code":"BadRequest","message":"Asset is still being processed"}
```


## 第六步 获取Tile.json原文件

发起请求 `GET` `https://assets.cesium.com/23200/tileset.json?v=1`

响应体
```json
{
    "asset": { "version": "1.0", "extras": { "ion": { "georeferenced": true, "movable": false } } },
    "geometricError": 773.9228030080011,
    "root": {
        "boundingVolume": {
            "region": [
                -1.3194620680333093,
                0.6987656516400003,
                -1.3193538949432,
                0.6988542204615121,
                -2.5704154968261577,
                38.02749061584471
            ]
        },
        "geometricError": 773.9228030080011,
        "refine": "ADD",
        "children": [
            {
                "boundingVolume": {
                    "region": [
                        -1.3194620680333093,
                        0.6987656516400003,
                        -1.3193538949432,
                        0.6988542204615121,
                        -2.5704154968261577,
                        38.02749061584471
                    ]
                },
                "geometricError": 0,
                "content": { "uri": "0/0/0.b3dm" }
            }
        ]
    }
}

```

## 第七步 获取b3dm

`GET` `https://assets.cesium.com/23200/0/0/0.b3dm`

请求头
```yml
Accept: */*;access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIwZmRjOGQ5ZC0zYjM5LTRjZTItOTUwNS1jOTRhNTE0OGNmN2MiLCJpZCI6OTY2NSwiYXNzZXRzIjp7IjIzMjAwIjp7InR5cGUiOiIzRFRJTEVTIn19LCJzcmMiOiIyZmFmMmI1YS0wMDA4LTQ5YmQtYjAzNi0xYTNkNzUyODA2NTEiLCJpYXQiOjE1NTc0ODQ0OTAsImV4cCI6MTU1NzQ4ODA5MH0.psmRQC9HGkS73wGhURjkuHLeA49Y-7JXi_zW8ZWyM-8
Origin: https://cesium.com
Referer: https://cesium.com/ion/assets/23200
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.131 Safari/537.36

```

响应头
```yml
accept-ranges: bytes
access-control-allow-methods: GET, PUT, POST, DELETE
access-control-allow-origin: *
access-control-expose-headers: ETag
access-control-max-age: 86400
cache-control: public, max-age=31536000
content-encoding: gzip
content-length: 2283726
content-type: application/octet-stream
date: Fri, 10 May 2019 10:34:54 GMT
etag: "55c6cc84bf9f261341744c86fc2c1cf0"
last-modified: Fri, 10 May 2019 10:34:42 GMT
server: AmazonS3
status: 200
vary: Origin,Access-Control-Request-Headers,Access-Control-Request-Method
via: 1.1 4798af72c7f6cead30e0da0525c1880c.cloudfront.net (CloudFront)
x-amz-cf-id: zI_KCWzl8JTvbbwHwaEG2pMFYD4l820CIJYOEYVfdgKAaDu9fo8pJg==
x-amz-id-2: GjuzXSxZvemhLhhdeBtQCckCb5ze91AoN8dTnhtYK2ToTh7K0zzGMJH1eb0abB43KWapWdciq8k=
x-amz-request-id: 25ABA774C8D96ABE
x-cache: Miss from cloudfront
```


响应体
```text
b3dm（二进制）
```


# 总结分析

Cesium Ion部署使用了AmazonS3（Simple Storage Service，对象存储）存储原始模型文件和转换后的3DTile文件，这些静态资源存储通过assets.cesium.com域名进行访问。访问资源需要携带访问令牌（access_token），这个access_token通过向 `api.cesium.com/assets/{id}/endpoint` 获取。

如上述access_token（JWT） 解析后的部分内容如下
```json
{
  "jti": "0fdc8d9d-3b39-4ce2-9505-c94a5148cf7c",
  "id": 9665,
  "assets": {
    "23200": {
      "type": "3DTILES"
    }
  },
  "src": "2faf2b5a-0008-49bd-b036-1a3d75280651",
  "iat": 1557484490,
  "exp": 1557488090
}
```

相关API接口，可以通过api.cesium.com调用，这部分接口由nginx/1.14.1返回，说明系统应该使用Nginx进行反向代理。