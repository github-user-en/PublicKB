On a genuine Windows, use this guide to setup the SSH client/server or both:
- [Get started with OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

On a non-genuine Windows, use this guide to setup the SSH client/server or both:
- [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki)
	- [MSI-based installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH-Using-MSI)
	- 

Then, to login by creating and using the SSH public-private key pair, follow [this guide](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples#login-with-ssh-keys)
> [!info] Notes:
> - On the client machine, you should store the public-private key pairs in `C:\Users\<username>\.ssh`
> - Add your public key contents to the `C:\Users\<username>\.ssh\authorized_keys` file on the SSH server
> - While SSHing into the server from the client, you would use the user accounts created on the server's OS. As such, to SSH into the server, you'd run the following command:
> 	- To login using a domain user account know to the server, you'd use the command `ssh -i "\path\to\client\machine's\copy\of\id_rsa" user@domain host`. Alternatively, you could try `ssh -i "\path\to\client\machine's\copy\of\id_rsa" domain\username@host`
> 	- To login using one of the local user account created on the server, you'd use the command `ssh -i "\path\to\client\machine's\copy\of\id_rsa" username@host`