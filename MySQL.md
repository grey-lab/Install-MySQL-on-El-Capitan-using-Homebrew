## Installing MySQL on older MAC OS X
## Install MySQL on OS X El Capitan
Normally the installation of [MySQL](https://www.mysql.com) can be achieved with a single command, which executes a  script provided by [MacMiniVault](https://github.com/MacMiniVault/Mac-Scripts) : 
`bash <(curl -Ls http://git.io/eUx7rg)`

_However, at the time of writing the script is not compatible with OS X El Capitan (10.11)_

#### Install MySQL using Homebrew
An alternative to the aforementioned installation script is installing MySQL using Homebrew. This gist assumes you already have Homebrew installed, if not **first read** the article "[Homebrew and El Capitan](http://t.co/goPLgP6GfD)"

Make sure Homebrew has the latest formulae, so run `brew update` first   
**-OR-** make sure Homebrew has MySQL version 5.6.27 as default formulae in its main repository :   

* Enter the following command : `brew info mysql`  
* Expected output: **mysql: stable 5.6.27 (bottled)**

Next install MySQL with : `brew install mysql`
  

###Additional configuration
Open Terminal and execute the following commands :  

* To have launchd start mysql at login :   
`ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents`
* To load mysql immediately :   
`launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist`
* Finally add the mysql directory to your PATH environment variable in `.bash_profile` :   

```  
export MYSQL_PATH=/usr/local/Cellar/mysql/5.6.27  
export PATH=$PATH:$MYSQL_PATH/bin
```

* Reload shell and type `mysql -v` to confirm  
Expected output : **Server version: 5.6.27 Homebrew**  
Quit the mysql CLI via `mysql> \q`

###Configure MySQL
Open Terminal and execute the following command to set the root password:  
 `mysqladmin -u root password 'yourpassword'`  

**Important** : Use the single ‘quotes’ to surround the password and make sure to select a strong password ! 

###Database Management
To manage your databases, I recommend using [Sequel Pro](http://www.sequelpro.com), a MySQL management tool designed for OS X# Install-MySQL-on-El-Capitan-using-Homebrew
