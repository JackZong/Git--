# Git--Common-problems-and-solutions.
Git 常见问题与解决办法
1.git-fatal the-remote-end-hung-up-unexpectedly
解决办法：
  sudo vim /etc/ssh/ssh_config 
  Host *
  ServerAliveInterval 60
