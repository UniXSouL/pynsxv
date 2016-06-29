# PyNSXv
PyNSXv is a high level python based library that exposes ready to use workflows and a CLI tool that can be used to control VMware NSX for vSphere

PyNSXv can be used in two different ways, as a library by importing the files in the /library subdirectory into your code, or as a CLI tool by executing `pynsxv`on the command line after installation. For easier installation please use PIP on your system

**More extensive documentation will follow soon, including python and shell script examples**

# Dependencies
PyNSXv has the following dependencies:
- pyvmomi (https://github.com/vmware/pyvmomi)
- nsxramlclient (https://github.com/vmware/nsxramlclient)
- tabulate (https://bitbucket.org/astanin/python-tabulate) 

Please check the installation instructions of these projects if you run into installation issues

# Installing PyNSXv

PyNSXv can be installed using pip:
```shell
pip install pynsxv
```

### Installing PyNSXv on a MAC

Make sure to install XCODE and its Command Line utilities:
https://itunes.apple.com/app/xcode/id497799835?mt=12 

```shell
xcode-select --install
```
If not yet present on your system, install python pip. The instructions on how to do so can be found here: https://pip.pypa.io/en/latest/installing/#install-or-upgrade-pip 
```shell
curl https://bootstrap.pypa.io/get-pip.py > get-pip.py
sudo python get-pip.py
```
If you don't have it yet, install homebrew on your system: http://brew.sh 
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Now install some of the xml formating dependencies needed by PyNSXv and the underlying nsxramlclient
```shell
brew install libxml2
brew install libxslt
brew link libxml2 --force
brew link libxslt --force
```

Finaly we are ready to install PyNSXv using pip:
```shell
sudo pip install pynsxv
```

**NOTE**: OSX 10.11 El Capitan introduces problems due to an outdated dependency `six`. Due to OSX's new System Integrity Protection (SIP) pip cannot remove the outdated version and install the needed one:
http://apple.stackexchange.com/questions/209572/how-to-use-pip-after-the-os-x-el-capitan-upgrade/210021#210021
http://stackoverflow.com/questions/31900008/oserror-errno-1-operation-not-permitted-when-installing-scrapy-in-osx-10-11

If you run into this error:

`OSError: [Errno 1] Operation not permitted: '/tmp/pip-nIfswi-uninstall/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six-1.4.1-py2.7.egg-info'` 

You should install a new non-bundled python version:
```shell
brew install python

sudo pip uninstall pynsxv
sudo pip uninstall six
sudo pip uninstall PyYAML
sudo pip uninstall pyraml-parser
sudo pip uninstall nsxramlclient

pip install pyopenssl
pip install pynsxv
```

### Various caveats

Should you see this warning message:
`UserWarning: /home/vagrant/.python-eggs is writable by group/others and vulnerable to attack when used with get_resource_filename. Consider a more secure location (set with .set_extraction_path or the PYTHON_EGG_CACHE environment variable).`

You can solve this by changing the permissions of the .python-eggs folder:
```shell
chmod g-wx,o-wx ~/.python-eggs
```
