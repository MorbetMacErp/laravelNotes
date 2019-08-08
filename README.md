# Laravel Use

## And supporting software setup

* PHP clearly...<https://www.php.net/downloads.php>
  * This involves installing the MS Visual C++ redistributable (link on th php downloads page)
  * Then unzip the php downloaded binaries to a preferred location (`C:\php7` keeps it easy)
  * Appen the unzipped folder location to the system PATH variable
  * Append `.php` to the system PATHEXT variable
  * Run the following two commands in the terminal:

  ```bash
  # Associate the php extension with a file type
  assoc .php=phpfile

  # Associate the phpfile file type with the appropriate php executable
  ftype phpfile="C:\php7\php.exe" -f "%1" -- %~2
  ```

  * Also, check that  the C:\php7\php.ini and uncomment out the line `extension=fileinfo` if it isn't already

* PHP package manager composer used once for the Laravel installer, but will probably be used again. For Windows get the composer installer here <https://getcomposer.org/doc/00-intro.md>
* install the laravel installer using the composer package manager, in a terminal run `composer global require laravel/installer`
* for source control, install git <https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>
* for source code repo sharing, create an account on github <https://github.com>
* virtual machine for local development server (Homestead VM) - platform: **install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)** and VM manager: **install [Vagrant](https://www.vagrantup.com/downloads.html)**, guest additions for mapped drives may or may not still be a separate process, works for me but I might have set it up a while ago or maybe it comes pre setup in newer versions
* the laravel pre-packaged dev server VM, add the homsetead vagrant box by running this command in a terminal `vagrant box add laravel/homestead`

## Ready to Create a Laravel project

* Using a terminal, go to a directory where you'd like to store you're code. Keep it simeple...again in the terminal `mkdir \code` `cd \code`. Now run the laravel installer from a terminal and give it a new projects name: `laravel new myNewProjectName`
* the laravel pre-packaged dev server VM on the per project setup, `require` the laravel/homestead package into the root project directory, it's a pre-packaged vagrant box that'll use the vagrant box added previously as a base box. Commands like `vagrant up` `vagrant ssh` and `vagrant destroy` will then be available within the project directory.

```bash
cd \code\myNewProjectName

# require laravel
composer require laravel/homestead --dev

# generate the vagrantfile and homestead.yaml
Mac / Linux:
php vendor/bin/homestead make

Windows:
vendor\bin\homestead make
```

* update the hosts file with an entry matching the ip and domain set in the homestead.yaml file
* If a `.env` file is not in the project root at this point, rename the `.env.example` file to `.env` and check that `APP_KEY=` has a value, if it doesn't then run the following command in the terminal: `php artisan key:generate`
* In a terminal run the command `vagrant up` this will start the Homestead VM, check the Forwarding ports... output and look for the MySQL port forwarding numbers. e.g. `links: 3306 (guest) => 33060 (host) (adapter 1)`, meaning the ./config/database.php will need port 3306 (which is probably has by default), .env will want `DB_PORT=33060` if your're using a host terminal from now on, or left at `DB_PORT=3306` if you're going to use the Homestead terminal avaible via `vagrant ssh`
* Change the .env and the ./config/database.php connection username and passwords to:

```bash
## note the last 0 only if you're using the HOST terminal from here on for migrations etc.
host: 127.0.0.1
port: 3306__0__
username: homestead
password: secret
```

## Source Control

* Time to initialise a repository and put it up to github. Create a completely new TOTALLY empty (no license or README) called `[myNewProjectName]`, use the same name you used on the `laravel new ...` command, then run the following in a terminal within your projects root directory

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:[githubUsername]/[myNewProjectName]
git push -u origin master
```

## Time to Learn Laravel

* <https://laravel.com/docs>

## Extras

* A nice bash shell makes the world of difference if you're using the host terminal, try ZSH with oh-my-zsh. Enable [WSL on Win 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10), then use apt-get for zsh `sudo apt-get install zsh`. Google how to make it the default terminal. Then [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)...this is all untested though as I don't have access to Win10 at the moment.
* Decent text editor for code, [VSCode](https://code.visualstudio.com/Download) (_my own Preffered_), [Atom](https://flight-manual.atom.io/getting-started/sections/installing-atom/), [Sublime](https://www.sublimetext.com/3) are three of the best right now.
