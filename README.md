# xcpkg
a package manager for [Xcode](https://developer.apple.com/xcode) to build C/C++/Rust project.

## Install xcpkg via HomeBrew

```bash
brew tap leleliu008/fpliu
brew install xcpkg
```

## Install xcpkg via cURL
```bash
curl -LO https://raw.githubusercontent.com/leleliu008/xcpkg/master/bin/xcpkg
chmod a+x xcpkg
mv xcpkg /usr/local/bin/

# following instrutions is optional, and these instructions only worked in zsh
xcpkg integrate zsh
autoload -U compinit && compinit
```

## xcpkg command usage
*   show the help of this command.
        
        xcpkg -h
        xcpkg --help
        
*   show the version of this command
        
        xcpkg -V
        xcpkg --version

*   show home directory of this software

        ndk-pkg --homedir

*   show home webpage of this software

        ndk-pkg --homepage

*   show current machine os and [Xcode](https://developer.apple.com/xcode) toolchain info
        
        xcpkg env

*   integrate `zsh-completion` script
        
        xcpkg integrate zsh
        xcpkg integrate zsh -x
        xcpkg integrate zsh --china
        xcpkg integrate zsh --china -x
        
    I have provide a zsh-completion script for `xcpkg`. when you've typed `xcpkg` then type `TAB` key, it will auto complete the rest for you.

    **Note**: to apply this feature, you may need to run the command `autoload -U compinit && compinit`
*   update the formula repositories

        xcpkg update
        
    **Note:** this software supports multi formula repositories. Offical formula repository is [xcpkg-formula-repository](https://github.com/leleliu008/xcpkg-formula-repository) 

*   search packages can be installed
        
        xcpkg search curl
        xcpkg search lib
        
*   show infomation of the given package or all available packages
        
        xcpkg info curl
        xcpkg info curl version
        xcpkg info curl summary
        xcpkg info curl webpage
        xcpkg info curl src.git
        xcpkg info curl installed-dir
        xcpkg info curl installed-metadata
        xcpkg info curl installed-files
        xcpkg info curl installed-abis
        xcpkg info curl installed-datetime-unix
        xcpkg info curl installed-datetime-formatted
        xcpkg info curl installed-pkg-version
        xcpkg info curl --json
        xcpkg info curl --json | jq .
        xcpkg info @all
        xcpkg info @all --json
        xcpkg info @all --json | jq .
         
    For more keys please read [README.md](https://github.com/leleliu008/xcpkg-formula-repository/blob/master/README.md#the-function-must-be-invoked-on-top-of-the-formula)

*   install packages
        
        xcpkg install curl
        xcpkg install curl bzip2 --rule=xx
        xcpkg install curl bzip2 --rule=xx --jobs=4
        xcpkg install curl bzip2 --rule=xx --jobs=4 -v
        xcpkg install curl bzip2 --rule=xx --jobs=4 -v -d
        xcpkg install curl bzip2 --rule=xx --jobs=4 -v -d -x
        xcpkg install curl bzip2 --rule=xx --jobs=4 -v -d -x --dry-run
        xcpkg install curl bzip2 --rule=xx --jobs=4 -v -d -x --dry-run --keep-work-dir
        
*   reinstall packages
        
        xcpkg reinstall curl
        xcpkg reinstall curl bzip2 -v
        
*   uninstall packages
        
        xcpkg uninstall curl
        xcpkg uninstall curl bzip2
        
*   upgrade the outdated packages
        
        xcpkg upgrade
        xcpkg upgrade curl
        xcpkg upgrade curl bzip2 -v
        
*   upgrade this software

        xcpkg upgrade @self
        xcpkg upgrade @self -x
        xcpkg upgrade @self --china
        xcpkg upgrade @self --china -x
        
*   list the avaliable formula repos
        
        xcpkg formula-repo list
        
*   add a new formula repo
        
        xcpkg formula-repo add my_repo https://github.com/leleliu008/xcpkg-formula-repository.git
        
*   delete a existing formula repo
        
        xcpkg formula-repo del my_repo
        
*   view the formula of the given package

        xcpkg formula view curl
        
*   edit the formula of the given package

        xcpkg formula edit curl
        
*   create the formula of the given package

        xcpkg formula create curl
        
*   delete the formula of the given package

        xcpkg formula delete curl
        
*   rename the formula of the given package to new name

        xcpkg formula rename curl curl7
        
*   view the given rule

        xcpkg rule view curl
        
*   edit the given rule

        xcpkg rule edit curl
        
*   create a new rule

        xcpkg rule create xx
        
*   delete the given rule

        xcpkg rule delete xx
        
*   rename the given rule to new name

        xcpkg rule rename xx yy
        
*   list rules
        
        xcpkg rule list
        
*   list the supported target platforms
        
        xcpkg target platforms
        
*   list the supported target platform's versions

        xcpkg target versions
        xcpkg target versions iPhoneOS
        
*   list the supported target archs

        xcpkg target archs
        xcpkg target archs iPhoneOS
        xcpkg target archs iPhoneOS 64bit
        xcpkg target archs iPhoneOS 32bit
        xcpkg target archs iPhoneOS all
        
*   list the supported target abis

        xcpkg target abis
        xcpkg target abis 64bit
        xcpkg target abis 32bit
        xcpkg target abis all

*   list the supported target triples

        xcpkg target triples
        xcpkg target triples 64bit
        xcpkg target triples 32bit
        xcpkg target triples all
        
*   list the available packages
        
        xcpkg ls-available
        
*   list the installed packages
        
        xcpkg ls-installed
        
*   list the outdated packages
        
        xcpkg ls-outdated
        
*   is the given package available ?
        
        xcpkg is-available curl
        xcpkg is-available curl ge 7.50.0
        xcpkg is-available curl gt 7.50.0
        xcpkg is-available curl le 7.50.0
        xcpkg is-available curl lt 7.50.0
        xcpkg is-available curl eq 7.50.0
        xcpkg is-available curl ne 7.50.0
        
*   is the given package installed ?
        
        xcpkg is-installed curl
        
*   is the given package outdated ?
        
        xcpkg is-outdated curl
        
*   list files of the given installed package in a tree-like format.
        
        xcpkg tree curl
        xcpkg tree curl --dirsfirst
        xcpkg tree curl -L 3
        xcpkg tree curl -L 3 --dirsfirst
        
*   download formula resources of the given package to the cache
        
        xcpkg fetch curl
        
*   show logs of the given installed package
        
        xcpkg logs curl iPhoneOS/armv7s
        xcpkg logs curl iPhoneOS/arm64
        
*   pack the given installed package
        
        xcpkg pack curl
        xcpkg pack curl --type=tar.gz
        xcpkg pack curl --type=tar.xz
        xcpkg pack curl --type=tar.bz2
        xcpkg pack curl --type=zip
        xcpkg pack curl --type=7z
        
*   show or open the homepage of the given package or this project
        
        xcpkg homepage
        xcpkg homepage --open
        xcpkg homepage --open curl
        xcpkg homepage curl --open
        
*   show the depended packages of the given package
        
        xcpkg depends curl
        
*   cleanup the unused cache
        
        xcpkg cleanup
        
