---
description: >-
  Detailed description for each method along with sample request and response
  messages
---

# Method Description

### 0. **startsdk**

This method enables the **SDK** and initializes it. **It is important to ensure that the SDK has been initialized before using the other procedures in the RPC interface.** This is a one-time operation.

**Parameter description**

`sdk_option`: Options available to initialize the **SDK**. Please refer to [**this**](api-overview.md#sdk-starting-options-description) for more details.

{% hint style="warning" %}
The`P2pNetworkId` should be consistent with the **ONTFS network ID**.
{% endhint %}

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "startsdk",
    "params": [{
        "ChainRpcAddr": "http://127.0.0.1:20336",
        "WalletPath": "./wallet.dat",
        "WalletPwd": "pwd",
        "GasPrice": 500,
        "GasLimit": 20000,
        "PdpVersion": 1,
        "P2pProtocol": "tcp",
        "P2pListenAddr": "127.0.0.1:20556",
        "P2pNetworkId": 0,
        "BlockConfirm": 1
    }],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 1. **uploadfile**

This method can be used to upload a file.

**Parameter description**

`upload_option`: Available upload options. Please refer to [**this**](api-overview.md#file-upload-options-description) for more details.

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "uploadfile",
    "params": [{
        "FilePath": "../testfile.tar.gz",
        "FileDesc": "testfile.tar.gz",
        "FileSize": 12341412,
        "TimeExpired": 23423434,
        "FirstPdp": true,
        "PdpInterval": 14400,
        "CopyNum": 3,
        "StorageType": 1,
        "Encrypt": true,
        "EncryptPassword": "ontfspwd",
        "WhiteList": []
    }],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "Tx": "e4b5fd08dc48160211b528f15002a80819c439d4f3f1edefb18c3ca138bdfef9",
        "FileHash": "SeNKJ5konzonQ4rqN7RRtNAmKD3hxcLuJKNAtSvjZxcyKQea",
        "Url": "ontfs://SeNKJ5konzonQ4rqN7RRtNAmKD3hxcLuJKNAtSvjZxcyKQea\u0026name=config.json\u0026owner=ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN\u0026size=167\u0026blocknum=1"
    }
}
```

### 2. **downloadfile**

This method can be used to download a file.

**Parameter description**

`download_option`: Available download options. Please refer to [**this**](api-overview.md#file-download-options-description) for more details.

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "downloadfile",
    "params": [{
        "FileHash": "SeNKJ5konzonQ4rqN7RRtNAmKD3hxcLuJKNAtSvjZxcyKQea",
        "InOrder": true,
        "MaxPeerCnt": 3,
        "OutFilePath": "./testfile.tar.gz",
        "DecryptPwd": "ontfspwd"
    }],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 3. **decryptfile**

This method can be used to decrypt a file.

**Parameter description**

`decrypt_option`: Options available for decrypting a file. Please refer to [**this**](api-overview.md#file-decryption-options-description) for more details.

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "decryptfile",
    "params": [{
        "FilePath": "./testfile.tar.gz",
        "OutFilePath": "./testfile_decrypted.tar.gz",
        "DecryptPwd": "ontfspwd"
    }],

    "id": "1"
}
```

Response:

```javascript
{
    "desc": "SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 4. **renewfile**

This method can be used to renew the expiration time of a file by adding time \(in seconds\) to the original expiration time.

{% hint style="warning" %}
Expiration time is specified using a `UNIX` timestamp, unit being **seconds**
{% endhint %}

**Parameter description**

`file_hash`: File hash

`add_time`: The amount of time to be added, unit being seconds

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "renewfile",
    "params": ["SeNKJ5konzonQ4rqN7RRtNAmKD3hxcLuJKNAtSvjZxcyKQea", 3600],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 5. **deletefiles**

This method can be used to delete multiple files together.

**Parameter description**

`file_hash`: File hash

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "deletefiles",
    "params": [
        ["SeNKJ5konzonQ4rqN7RRtNAmKD3hxcLuJKNAtSvjZxcyKQea", "Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe"]
    ],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 6. **getfileinfo**

This method can be used to fetch the file information of an uploaded file.

**Parameter description**

`file_hash`: File hash

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getfileinfo",
    "params": ["Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe"],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "FileHash": "Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe",
        "FileOwner": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
        "FileDesc": "ont-fs-sdk_0.1.0.tgz",
        "FileBlockCount": 13,
        "RealFileSize": "2.8 MB",
        "CopyNumber": 2,
        "PayAmount": "0.002715648 ONG",
        "RestAmount": "0.002156544 ONG",
        "FileCost": "0.000559104 ONG",
        "FirstPdp": true,
        "PdpInterval": 14400,
        "TimeStart": "2019-12-09 19:05:14 +0800 CST",
        "TimeExpired": "2019-12-12 15:04:05 +0800 CST",
        "PdpParam": "gQFrQHmalXSUBnZ1M7Bu0BC+JCCd1+UsPO4g6jwa56VmHl8TWwBINIgnUh5/PMoQRPHHRNRSmJDV+YrJ6u2EXzdAeRbVWptVuPEVSvWQlzKZuTiRsaovm2nVTVAgFJBHKTcUxTzLFtmKCLJ5OzP1ZLXNiRZYUx91kJ1j2OTUwmu+gkBHeO+3LfIc81loeRAjL/wK9MvWdTYUlCL6/zork4hNG1KKuA0z8XMxUJlWL8vvJa9Iyhc8HYAWO0jTj0d8tQp+gQEvn4dLat/J6+k/UTyjHbKSb18Wvblc6t/qgg+6WozuAzTqEbBcBJ050HtVCIUXfAJ+My5be+39lhPlv5Dw27t5N4pjwyl4kpGp8NqRMhhYlp1TrpixpSX79wWpdXDVYuUjMU6hmpNe8KMQGZJi6bgw58nZdmEpkfWgfEH6xo6ZqSDOnaRlFuMEJ0EiSn+QYeMYGlpNF6u6crboKSKvN1PXVg==",
        "ValidFlag": true,
        "StorageType": 1
    }
}
```

### 7. **getfilelist**

This method can be used to fetch the list of all the files.

**Parameter description**

{% hint style="info" %}
This method does not take parameters since it returns a list of files for which the **current user** is the **owner**.
{% endhint %}

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getfilelist",
    "params": [],
    "id": "1"
}
```

Response:

```javascript
{
    "desc": "SUCCESS",
    "error": 0,
    "id": "1",
    "jsonrpc": "2.0",
    "result": [
        "SeNK9CUPQUycH29qHUNWHkvjk9kY1QcB1VdpYTG3rnSfqKaN",
        "Sk9yJBSzGRwEdcuWiECz6hTNMSjwbF7Zq2tbi3TTubuYEBPm",
        "Sk9yNEbq84Bmm1ydGsCZWqvAJefnh2C8G1BAU4tfFyrzCXgw",
        "Sk9yNUHUgWR2BUBqqZpCDBw5BsVodrNxoEqhCautqo2MAWpE"
    ]
}
```

### 8. **changefileowner**

This method can be used to change the owner of a file.

**Parameter description**

`file_hash`: File hash

`new_owner`: Address of the new owner of the file

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "changefileowner",
    "params": ["Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe", "ATa3TJYs4vU4EJWiFjUpxcQZjZkWs813aj"],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 9. **getfilereadpledge**

This method can be used to fetch pledge details from the contract w.r.t downloading a file

**Parameter description**

`file_hash`: File hash

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getfilereadpledge",
    "params": ["Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe"],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "FileHash": "Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe",
        "Downloader": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
        "BlockHeight": 56025,
        "ExpireHeight": 56136,
        "RestMoney": 145408,
        "ReadPlans": [
            {
                "NodeAddr": "AZxSPsXBnNrWdMyrhTG6CqTxFQgZoiN2Xd",
                "MaxReadBlockNum": 81,
                "HaveReadBlockNum": 40
            },
            {
                "NodeAddr": "AJeuPaxfvrzJjTdpLZXpVgBtdQcHVaNM8f",
                "MaxReadBlockNum": 81,
                "HaveReadBlockNum": 41
            }
        ]
    }
}
```

Here's a description for the `ReadPlans` field.

| Field | Type | Description |
| :--- | :---: | :--- |
| NodeAddr | string | Node address |
| MaxReadBlockNum | int | The maximum number of file blocks that can be read from this node |
| HaveReadBlockNum | int | The number of blocks that were read during the read operation |

### 10. **cancelfilereadpledge**

This method can be used to cancel the pledge and claim the pledge amount from the file download contract.

**Parameter description**

`file_hash`: File hash

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "cancelfilereadpledge",
    "params": ["Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe"],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 11. **getfilepdpinfolist**

This method can be used to fetch PDP record details for a file.

**Parameter description**

`file_hash`: File hash

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getfilepdpinfolist",
    "params": ["Sk9yPZdThcHikj1L1sQmxgXAJap9x24vMVJUdG2cky4KEpAe"],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": [
        {
            "NodeAddr": "AJeuPaxfvrzJjTdpLZXpVgBtdQcHVaNM8f",
            "FileHash": "Sk9yJBSzGRwEdcuWiECz6hTNMSjwbF7Zq2tbi3TTubuYEBPm",
            "FileOwner": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
            "PdpCount": 29,
            "LastPdpTime": "2019-12-12 08:06:18 +0800 CST",
            "NextHeight": 52504,
            "SettleFlag": false
        },
        {
            "NodeAddr": "AZxSPsXBnNrWdMyrhTG6CqTxFQgZoiN2Xd",
            "FileHash": "Sk9yJBSzGRwEdcuWiECz6hTNMSjwbF7Zq2tbi3TTubuYEBPm",
            "FileOwner": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
            "PdpCount": 29,
            "LastPdpTime": "2019-12-12 08:46:18 +0800 CST",
            "NextHeight": 52506,
            "SettleFlag": false
        }
    ]
}
```

### 12. **getspaceinfo**

This method can be used to fetch details regarding the user space.

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getspaceinfo",
    "params": [],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "SpaceOwner": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
        "Volume": "10 MB",
        "RestVol": "10 MB",
        "CopyNumber": 1,
        "PdpInterval": 14400,
        "PayAmount": "1.0720256 ONG",
        "RestAmount": "1.0720256 ONG",
        "TimeStart": "2019-12-16 14:06:37 +0800 CST",
        "TimeExpired": "2021-12-12 14:20:53 +0800 CST",
        "ValidFlag": true
    }
}
```

### 13. **createspace**

This method can be used to create a new user space.

**Parameter description**

`volume`: Size of the space \(in KB\), for e.g. 10GB = 10485760 KB

`pdp_interval`: **PDP** submission interval, recommended to be set to 4\*60\*60 seconds, i.e, 4 hours, the system would be unable to find an available server if the `MinPdpInterval` of all the nodes in the network is lesser than this value

`copy_num`: Number of copies to be maintained for the files in the space

`time_expired`: Expiration time, `UNIX` timestamp

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "createspace",
    "params": [10485760, 3, 1607762042],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "SpaceOwner": "ALJwq2WYwL26E55dWJs66cAF1E79cDpXeN",
        "Volume": "10 MB",
        "RestVol": "10 MB",
        "CopyNumber": 1,
        "PdpInterval": 14400,
        "PayAmount": "1.0720256 ONG",
        "RestAmount": "1.0720256 ONG",
        "TimeStart": "2019-12-16 14:06:37 +0800 CST",
        "TimeExpired": "2021-12-12 14:20:53 +0800 CST",
        "ValidFlag": true
    }
}
```

### 14. **deletespace**

This method can be used to delete a user space.

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "deletespace",
    "params": [],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 15. **updatespace**

This method can be used to update certain user space properties, such as the size and expiration time of a user space.

**Parameter description**

`volume`: Size of the space \(in KB\), for e.g. 10GB = 10485760 KB

`time_expired`: Expiration time, `UNIX` timestamp

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "updatespace",
    "params": [10485760, 1607762042],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": null
}
```

### 16. **getfsnodeslist**

This method can be used to fetch the list of storage nodes along with the relevant information.

**Parameter description**

`limit`: The maximum number of records to be returned in the response

**Sample messages**

Request:

```javascript
{
    "jsonrpc": "2.0",
    "method": "getfsnodeslist",
    "params": [50],
    "id": "1"
}
```

Response:

```javascript
{
    "desc":"SUCCESS",
    "error":0,
    "jsonrpc": "2.0",
    "id": "1",
    "result": [
        {
            "Pledge": 9765625,
            "Profit": 38694400,
            "Volume": "9.3 GB",
            "RestVol": "8.8 GB",
            "ServiceTime": "2019-12-30 08:00:00 +0800 CST",
            "MinPdpInterval": 14400,
            "NodeAddr": "AJeuPaxfvrzJjTdpLZXpVgBtdQcHVaNM8f",
            "NodeNetAddr": "127.0.0.1:30335"
        },
        {
            "Pledge": 10485760,
            "Profit": 32311552,
            "Volume": "10 GB",
            "RestVol": "9.6 GB",
            "ServiceTime": "2019-12-30 08:00:00 +0800 CST",
            "MinPdpInterval": 14400,
            "NodeAddr": "AZxSPsXBnNrWdMyrhTG6CqTxFQgZoiN2Xd",
            "NodeNetAddr": "127.0.0.1:30445"
        }
    ]
}
```

