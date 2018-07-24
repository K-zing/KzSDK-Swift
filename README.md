# KzSDK-Swift
## Installation
Cocoapods

    pod 'KzSDK-Swift'
## Getting Started
Initialize with your API and MD5 key.

    KzSetting.initialize(apiKey: "API KEY", md5Key: "MD5 KEY")
Get RSA public key from `ApiAction.GetKey` and configure with `KzSetting.setPublicKey`

    ApiAction.GetKey().addListener(ApiListener<ApiAction.GetKey.Result>.init(onSuccess: { (result) in
        guard let clientPublicKey = result.body?.data?.publicKeyString else {
            return
        }
        
        KzSetting.setPublicKey(clientPublicKey)
    }, onFail: { (result) in
        print(result.body)
    })).post()