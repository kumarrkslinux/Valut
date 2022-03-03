- Download the vault package 
- Set path where the packaged in placed 
- S C:\Users\> $env:VAULT_ADDR="http://127.0.0.1:8200"
- S .\vault.exe server -dev
- Take the Api Address: http://127.0.0.1:8200 from the output
- Take the Root Token: s.xxxxxxxxxxxxxxxxxxxxxx from the output
- Browse it http://127.0.0.1:8200 and use the Root token for login

# secret 
```
PS C:\Users\>  .\vault.exe status
Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.9.3
Storage Type    inmem
Cluster Name    vault-cluster-3215cd1d
Cluster ID      c66d0936-a55c-5870-8040-b2b332c6d6a3
HA Enabled      false
```
```
2. PS C:\Users\> .\vault.exe kv get secret/kumar
======= Metadata =======
Key                Value
---                -----
created_time       2022-03-03T11:25:22.4564842Z
custom_metadata    <nil>
deletion_time      n/a
destroyed          false
version            1

==== Data ====
Key      Value
---      -----
kumar    xxxxxx
```

```
PS C:\Users$ .\vault.exe kv put secret/kumar1 kummar=admin011
Key                Value
---                -----
created_time       2022-03-03T11:35:32.5673645Z
custom_metadata    <nil>
deletion_time      n/a
destroyed          false
version            1
```
```
PS C:\Users> .\vault.exe kv get secret/kumar1
======= Metadata =======
Key                Value
---                -----
created_time       2022-03-03T11:35:32.5673645Z
custom_metadata    <nil>
deletion_time      n/a
destroyed          false
version            1

===== Data =====
Key       Value
---       -----
kummar    xxxxxx
```
```
PS C:\Users\> .\vault.exe kv delete secret/kumar1 
Success! Data deleted (if it existed) at: secret/kumar1
```
```
PS C:\Users\ .\vault.exe kv undelete -versions=1 secret/kumar1 
Success! Data written to: secret/undelete/kumar1
```
```
PS C:\Users\> .\vault.exe kv destroy -versions=1 secret/kumar1 
Success! Data written to: secret/destroy/kumar1
```
```
PS C:\Users> .\vault.exe kv metadata get secret/kumar1
========== Metadata ==========
Key                     Value
---                     -----
cas_required            false
created_time            2022-03-03T11:35:32.5673645Z
current_version         1
custom_metadata         <nil>
delete_version_after    0s
max_versions            0
oldest_version          0
updated_time            2022-03-03T11:35:32.5673645Z

====== Version 1 ======
Key              Value
---              -----
created_time     2022-03-03T11:35:32.5673645Z
deletion_time    n/a
destroyed        true
```

```
PS C:\Users>  .\vault.exe kv metadata delete secret/kumar1 
Success! Data deleted (if it existed) at: secret/metadata/kumar1
