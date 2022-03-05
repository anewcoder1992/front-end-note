1. brew update 
2. brew install postgresql
3.  brew services start  postgresql
4.  brew services restart  postgresql
5.  socket in /tmp 
6. 查看 /tmp 是否存在 sudo find /tmp/ .s.PGSQL.5432
7.  链接database_url :postgres:///[databasename]?host=/tmp
8.  查看