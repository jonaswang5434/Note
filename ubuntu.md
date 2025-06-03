install ubuntu on Oracle virtualBox
can't execute "sudo apt uypdate"
1. download ubuntu iso file from https://ubuntu.com/download/alternative-downloads
2.change the connection as bridage 
3. if encounter can't 'sudo apt update'
  3.1 check ping baidu.com,if can't, this need config DNS server :
      sudo nano /etc/resolv.conf
      add the folowwing content:
      nameserver 8.8.8.8
      nameserver 1.1.1.1
      if in china,add：
      nameserver 223.5.5.5
      nameserver 114.114.114.114
4. if you can ping www.baidu.com, but can't "sudo apt update"
  replace the source to aliyun mirror.
  sudo sed -i 's|http://.*.ubuntu.com|http://mirrors.aliyun.com|g' /etc/apt/sources.list

vs code connect ubuntu.
if can't connect ,maybe ubuntu not install openssh-server,so we need execute "sudo apt install openssh-server" on ubuntu terminal.


can't find poetry after exec "pip3 install poetry"

check poetry:
  "pip3 show poetry"
check poetry path:
  "which poetry"
add poetry into enverionment:
  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
  source ~/.bashrc
check whether successful:
   poetry --version


Install postgresql server:
  sudo apt update
  sudo apt install postgresql postgresql-contrib
      postgresql：安装数据库核心服务。
      postgresql-contrib：安装官方附加功能包（推荐）。

  check postgresql status:
  sudo systemctl status postgresql

  switch postgresql default user:
  sudo -i -u postgres
  exec postgresql command:
  psql
  exit postgre user:
  exit
  exit postgre:
  ctrl + D

  create database and user 
    CREATE USER myuser WITH PASSWORD 'mypassword';
    CREATE DATABASE mydb OWNER myuser;
    GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;
  expose remote connection :
  step1.
     sudo nano /etc/postgresql/15/main/postgresql.conf
     change #listen_addresses = 'localhost' as listen_addresses = '*'
  step2.
     sudo nano /etc/postgresql/15/main/pg_hba.conf
     add a new line:
     host    all             all             0.0.0.0/0               md5
  step3.
    sudo systemctl restart postgresql


wget can't access oversease websit:
set proxy to solve this issue,把下面内容加到你的 ~/.bashrc 或 ~/.zshrc：
  export http_proxy=http://127.0.0.1:7890
  export https_proxy=http://127.0.0.1:7890
  export ftp_proxy=http://127.0.0.1:7890
  export no_proxy="localhost,127.0.0.1,::1"

and then execute:
  source ~/.bashrc   # 或者 source ~/.zshrc
    





