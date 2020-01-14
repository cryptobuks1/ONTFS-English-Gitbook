---
description: Available methods in the RPC API
---

# Method List

| Method | Parameters | Description | Note |
| :--- | :--- | :--- | :---: |
| startsdk | `sdk_option` | Start SDK service | For detailed description of `sdk_option` please refer to this |
| uploadfile | `upload_option` | Upload file | For detailed description of `upload_option` please refer to this |
| downloadfile | `download_option` | Download file | For detailed description of `download_option` please refer to this |
| decryptfile | `decrypt_option` | Decrypt file | For detailed description of `decrypt_option` please refer to this |
| renewfile | `file_hash`, `add_time` | Renew expiration time of the file by adding time \(seconds\) | - |
| deletefiles | \[`file_hash1`, `file_hash2`\] | Delete multiple files | - |
| getfileinfo | `file_hash` | Fetch file information of an uploaded file | - |
| getfilelist |  | Get list of all the files | - |
| changefileowner | `file_hash`, `new_owner` | Change the owner of a file | - |
| getfilereadpledge | `file_hash` | Fetch pledge details from the contract w.r.t downloading a file | - |
| cancelfilereadpledge | `file_hash` | Claim pledge amount from the file download contract | - |
| getfilepdpinfolist | `file_hash` | Fetch PDP record details for a file | - |
| getspaceinfo |  | Fetch user space information | - |
| createspace | `volume`,`copy_num`,`time_expired` | Create a new user space | - |
| deletespace |  | Delete user space | - |
| updatespace | `volume`,`time_expired` | Update user space properties | - |
| getfsnodeslist | `limit` | Fetch the list of storage nodes along with the relevant information | - |

