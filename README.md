# Laravel Use

## And supporting software setup

* PHP clearly...<https://www.php.net/downloads.php>
* PHP package manager composer used once for the Laravel installer, but will probably be used again. For Windows get the composer installer here <https://getcomposer.org/doc/00-intro.md>
* install the laravel installer using the composer package manager run `composer global require laravel/installer`
* for source control, git <https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>
* for source code repo sharing, create an account on github <https://github.com>
* virtual machine for local development server (Homestead VM) - platform: **install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)** and VM manager: **install [Vagrant](https://www.vagrantup.com/downloads.html)**, guest additions for mapped drives may or may not still be a separate process, works for me but I might have set it up a while ago or maybe it comes pre setup in newer versions
* the laravel pre-packaged dev server VM, add the homsetead vagrant box `vagrant box add laravel/homestead`
* the laravel pre-packaged dev server VM, `require` the laravel/homestead repo into the root project directory, it's a pre-packaged vagrant box that'll use the vagrant box added previously as a base box. Commands like `vagrant up` `vagrant ssh` and `vagrant destroy` will now be available within the project directory.

```bash
# require laravel
composer require laravel/homestead --dev

# generate the vagrantfile and homestead.yaml
Mac / Linux:
php vendor/bin/homestead make

Windows:
vendor\\bin\\homestead make
```

* Within the parent of the directory you want to work on the source code for the project, checkout the initial codebase already put up on github `git clone git@github.com:MorbetMacErp/shiftBooker` or if I haven't done it yet run `laravel new shiftbooker`, and then get it into git by creat a new repo at github and then follow these commands within the local project folder created by `laravel new`

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:MorbetMacErp/shiftBooker
git push -u origin master
```

remember to update the hosts file with an entry matching the ip and domain set in the homestead.yaml file

## Time to Learn Laravel

* <https://laravel.com/docs>

## Extras

* A nice bash shell makes the world of difference, try ZSH with oh-my-zsh. Enable [WSL on Win 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10), then use apt-get for zsh `sudo apt-get install zsh`. Google how to make it the default terminal if you like. Then [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
* Decent text editor for code, [VSCode](https://code.visualstudio.com/Download), [Atom](https://flight-manual.atom.io/getting-started/sections/installing-atom/), [Sublime](https://www.sublimetext.com/3) are three of the best right now.
