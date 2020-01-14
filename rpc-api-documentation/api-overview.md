---
description: A brief overview of the RPC API
---

# API Overview

This document is the **RPC API** documentation for **ONTFS**. 

All the available request parameters and corresponding responses have been described in detail.

Here is the description for some of the fields that are used in the API.

### **Request parameters description**

| Field | Type | Description |
| :---: | :---: | :---: |
| jsonrpc | string | JSON RPC version no. |
| method | string | Method name |
| params | string | Required parameters for the method |
| id | string | Arbitrary ID |

### **Method parameters description**

| Field | Type | Description |
| :---: | :---: | :---: |
| desc | string | Corresponding result description |
| error | int64 | Error code |
| jsonrpc | string | JSON RPC version no. |
| id | string | Arbitrary ID |
| result | object | RPC execution result |

{% hint style="warning" %}
Different request types will return different results
{% endhint %}

### **SDK starting options description**

| Parameter name | Type | Whether required | Description |
| :--- | :--- | :--- | :--- |
| ChainRpcAddr | string | required | Ontology RPC address |
| WalletPath | string | required | Wallet file path |
| WalletPwd | string | required | Wallet password |
| GasPrice | uint64 | required | Gas price |
| GasLimit | uint64 | required | Gas limit |
| P2pProtocol | string | required | P2P protocol type |
| P2pListenAddr | string | required | P2P protocol listener's address |
| P2pNetworkId | uint64 | required | P2P network ID |
| BlockConfirm | uint64 | required | Number of blocks to confirmation |

### **File upload options description**

| Parameter name | Type | Whether required | Description |
| :--- | :--- | :---: | :--- |
| FilePath | string | required | File path |
| FileDesc | string | required | File description |
| TimeExpired | uint64 | required | File expiration time, UNIX timestamp |
| PdpInterval | uint64 | required | PDP submission interval, recommended to be set to 4\*60\*60 seconds, i.e, 4 hours, the system would be unable to find an available server if the `MinPdpInterval` of all the nodes in the network is lesser than this value |
| CopyNum | uint64 | required | Number of backup copies of the file |
| FirstPdp | bool | required | Whether the ONTFS node is computing the PDP for the first time; Under Snark version PDP mode, the waiting time to download a file right after it has been uploaded can be reduced significantly if the PDP calculation process is skipped |
| StorageType | uint64 | required | Storage type：`0` - leaseholder mode; `1` - lease mode |
| FileSize | uint64 | required | Actual file size |
| Encrypt | bool | required | Whether encrypted |
| EncryptPassword | string | required | Encryption password |
| WhiteList | \[\]string | optional | Whitelist, currently not supported |

### **File download options description**

| Parameter name | Type | Whether required | Description |
| :--- | :--- | :---: | :--- |
| FileHash | string | required | File hash |
| InOrder | bool | required | Whether download in the file block sequence, currently only support `true` |
| MaxPeerCnt | int | required | Maximum number of storage node sources for downloading the file |
| OutFilePath | string | required | Download path from the `description` file, mention name only, file is downloaded to the default path |
| DecryptPwd | string | required | Decryption password |

### **File decryption options description**

| Parameter name | Type | Whether required | Description |
| :--- | :--- | :---: | :--- |
| FilePath | string | required | Original file path |
| OutFilePath | string | required | Download path from the `description` file, mention name only, file is downloaded to the default path |
| DecryptPwd | string | required | Decryption password |

