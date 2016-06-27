# PyNSXv
PyNSXv is a higher level python based library (exposing ready to use workflows) and a CLI tool to control NSX for vSphere

PyNSXv can be used in two different ways, as a library by importing the files in the /library subdirectory into your code, or as a cli tool by calling `pynsxv`on the CLI after you installed pynsxv using pip on your system

**More extensive documentation will follow soon, including python and shell script examples**

# dependencies
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

Make sure to install XCODE and XCODE Command Line utilities:
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


NOTE: Some problems with the 'six' library have been seen with OSX 10.11 El Capitan. Details can be found here:
http://stackoverflow.com/questions/31900008/oserror-errno-1-operation-not-permitted-when-installing-scrapy-in-osx-10-11 

If you run into this error:

`OSError: [Errno 1] Operation not permitted: '/tmp/pip-nIfswi-uninstall/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six-1.4.1-py2.7.egg-info'` 

Simply install PyNSXv with the `--ignore-installed` flag:
```shell
sudo pip install --ignore-installed pynsxv
```
