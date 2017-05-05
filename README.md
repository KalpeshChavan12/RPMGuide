# RPM Package manager guide

Document contain most frequently used command and troubleshooting.

#### Basic commands rpm
###### Install rpm 
Yum will install all the dependencies for rpm.
```sh
$ rpm -i package.rpm
or
$ yum install package
```
###### Upgrade rpm
Yum will upgrade the dependencies based on dependency of package.
```sh
$ rpm -U packagename.rpm
or
$ yum upgrade packagename
```
###### Dowgrade rpm
We need  old version rpm to downgrade. if we are downgrade using yum then it will pickup rpm from repo.
```sh
$ rpm -U --oldpackage packagename-old-version.rpm
or
$ yum downgrade package
```
###### Remove rpm
rpm command will not remove if it is required for another package.
Yum will remove package allog with dependencies.
```sh
$ rpm -e packagename
or
$ yum earse packagename
```
###### List and Query installed rpm
-qa option list all installed packages. command will give you only the name of rpm installed. To get details about the rpm we have to use the --queryformat option. query format contained the tags. we will get the list of tags using rpm --querytags command.
if we wanto query rpm file then use -p option.

* Query Expression:
     %|TAGNAME?{present}:{missing}|
```sh
### Get list of installed package
$ rpm -qa
### Get list of installed package with pattern e.g for  "shad*"
$ rpm -qa  "sha*"
shadow-utils-4.1.4.2-19.el6_6.1.x86_64
shared-mime-info-0.70-6.el6.x86_64
```
Get Details using --queryformat
Following command will give you version size of rpm. we can use diffrent tag in below command
 e.g.
```sh
$ rpm -qa  "sha*" --queryformat  "[%{NAME} %{SIZE} %{VERSION}\n]"
shadow-utils 2777820 4.1.4.2
shared-mime-info 1411396 0.70
```

###### List files in rpm
Option: -ql or --queryformat
```sh
$ rpm -ql packagename
## list file in rpm file.
$ rpm -qpl /path-to/package.rpm
#### or
$ rpm -qa  packagename --queryformat  "[%{=NAME} %{FILENAMES}\n] "
```
###### Query package owning file.
Option:  **-qf**
```sh
$ rpm -qf <file>
### e.g.
$ rpm -qf /bin/ls
coreutils-8.4-37.el6.x86_64
```
###### Get package info
Options: **-qi** , **-p** for rpm file.
```sh
$ rpm -qi packagename
### for rpm file
$ rpm -qpi /path-to/package.rpm
```

###### Get Scriptlets
Option: **-q --scripts**   , **-p** for rpm file
```sh
$ rpm -q --scripts packagename
#### for rpm file
$ rpm -qp --scripts /path-to/package.rpm
```

###### Get Changelog
Option: **-q --changelog**   , **-p** for rpm file
```sh
$ rpm -q --changelog packagename
#### for rpm file
$ rpm -qp --changelog /path-to/package.rpm
```

###### Get List of Dependencies
Option: **-qR**   , **-p** for rpm file
```sh
$ rpm -qR packagename
#### for rpm file
$ rpm -qpR /path-to/package.rpm
```
###### Get list of capabilities rpm provides
Option: **-q --provides**   , **-p** for rpm file
```sh
$ rpm -q --provides packagename
#### for rpm file
$ rpm -qp --provides /path-to/package.rpm
```
