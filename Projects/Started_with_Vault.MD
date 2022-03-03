Download the vault package 
Set path where the packaged in placed 
S C:\Users\> $env:VAULT_ADDR="http://127.0.0.1:8200"
S .\vault.exe server -dev
Take the Api Address: http://127.0.0.1:8200 from the output
Take the Root Token: s.xxxxxxxxxxxxxxxxxxxxxx from the output
browse it http://127.0.0.1:8200 and use the Root token for login

