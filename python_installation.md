Good Resource this is based on: [https://www.linuxcapable.com/how-to-install-python-3-10-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-python-3-10-on-ubuntu-22-04-lts/)

Prep - Linux (mainly for new servers)
=====================================

1.  You may need a C compiler if you haven’t yet downloaded: `sudo apt update && sudo apt install build-essential`
    
2.  Other dependencies: `sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev curl libbz2-dev pkg-config make -y`
    
3.  Python3.11 and Ubuntu 20+ `sudo apt install libpq-dev`
    

Installation - Linux
====================

1.  [https://www.python.org/downloads/](https://www.python.org/downloads/) Download the latest version, ie 3.10.x
    
    1.  Choose Gzipped Tarball
        
    2.  Copy link and run `wget LINKYOUCOPIED` to download a python file like Python3.10.xxx
        
    3.  Unzip to directory: `tar -xvf UNZIPPEDPYTHONFILE` you will now have a directory like Python3.10.xxx
        
    4.  Optional: `sudo mv Python3.{version} /opt/` Move python installation directory to /opt/ to keep home clean
        
    5.  `cd` into the directory and run each command :
        
        1.  `./configure --enable-optimizations`
            
        2.  `make` Builds Python
            
        3.  `sudo make altinstall` Installs the binaries, this step may take some time. `altinstall` skips creating the `python` link and the manual pages links, `install` will hide the system binaries and manual pages. This means that we will leave the system python installation untouched
            
        4.  Python is now installed. Last step is to configure the system links, fill in {version} by tabbing: `sudo ldconfig /opt/Python3.{version}`
            

Be careful which commands use `sudo` as running the ./configure or first make as `sudo` will cause Python to have files which require elevated permissions.

Installation - macOS
====================

1.  [https://www.python.org/downloads/](https://www.python.org/downloads/) Download and install the latest version, ie 3.10.x
    

Create A Virtual Environment for Python
=======================================

Virtual environments are siloed environments that let you install any packages / modules to python that you wish, this will not have any impact on the original installation of python. This allows you to have separate environments for separate projects or separate versions of python, all without ever modifying your original pristine version of python.

1.  If you do not have a directory for your virtual environments yet, make one:
    
    1.  `mkdir` ie: `mkdir ~/venv`
        
    2.  or for VSCode put a directory in the project directory `mkdir ~/PROJECTNAME/.virtualenv`
        
2.  Assuming your target python you’ve installed is python3.10 run:
    
    1.  `python3.10 -m venv ~/venv/MYENVNAME` for example `python3.10 -m venv ~/venv/james-test-env`
        
    2.  or for VSCode: eg for .virtualenv in the project directory: `python3.10 -m venv ~/PROJECTNAME/.virtualenv`
        
3.  Test your virtual environment by:
    
    1.  Before activating, check which installation the word ‘python’ is pointing to: by running
        
        1.  `which python`
            
        2.  `which python3.10`
            
    2.  Activate your environment
        
        1.  `source ~/venv/MYNAME/bin/activate`
            
        2.  Note that next to your prompt you should see (MYNAME) so you know you’re using that python environment
            
    3.  Check your python virtual environment
        
        1.  `which python` should this time point to one you made in step 2
            
        2.  Running `python` should start your correct version of python, ie 3.10
            

Install Python Packages
=======================

Packages are modules that extend pythons features. The majority of work you do will likely be done using packages. The core packages you should get are: `pandas, sqlalchemy, requests` though there will likely be many packages you install overtime.

1.  Activate your environment:
    
    1.  `source ~/venv/MYNAME/bin/activate`
        
2.  Use Pip to install packages
    
    1.  `pip install PACKAGENAME` ie `pip install pandas, sqlalchemy` or `pip install pandas`
