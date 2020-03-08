

## Deploying to S3

- [ ] create the following environment variables:

  - [ ] AWS_ACCESS_KEY_ID
  - [ ] AWS_SECRET_ACCESS_KEY
  - [ ] AWS_STORAGE_BUCKET_NAME

- [ ] pip install the following packages:

  - [ ] `pip install boto3`
  - [ ] `pip install django-storages`
    - [ ] add `'storages'` to INSTALLED_APPS under settings.py

- [ ] ```python
  #add in settings.py file
  AWS_ACCESS_KEY_ID = os.environ['AWS_ACCESS_KEY_ID']
  AWS_SECRET_ACCESS_KEY = os.environ['AWS_SECRET_ACCESS_KEY']
  AWS_STORAGE_BUCKET_NAME= os.environ['AWS_STORAGE_BUCKET_NAME']
  
  AWS_S3_FILE_OVERWRITE = False
  #to prevent same image files to be overwritten
  
  ```

  https://django-storages.readthedocs.io/en/latest/backends/amazon-S3.html

- [ ] 

## Django deployment

- [ ] Go to 'Getting Started on Heroku with Python'
- [ ] Create an Heroku account
- [ ] install pipenv
- [ ] Install git ( check git --version)
- [ ] Install Heroku CLI
- [ ] Login heroku
- [ ] Create a virtual enviroment
- [ ] Run manage.py not gonna run - pip freeze nothing installing
- [ ] Check which version django,requests you have and install it
- [ ] Run manage.py and then stop it
- [ ] Go to django heroku
- [ ] Create a Procfile and 
- [ ] Install django-heroku
- [ ] Add stuff to settings.py file
- [ ] Install guincorn 
- [ ] pip freeze - requirements.txt (use the angle bracket after pip freeze. Youtube doesn't allow angle bracket in description :/ )
- [ ] heroku create attreyaweb (to create an app on heroku)
- [ ] git status git commands - (git push heroku master
- [ ] Open up the website)
- [ ] Admin panel not working. heroku run bash. Migrations





1. `heroku config:set DISABLE_COLLECTSTATIC=1`





USERDOMAIN=DESKTOP-MO6N4D5
ChocolateyToolsLocation=C:\tools
OS=Windows_NT
COMMONPROGRAMFILES=C:\Program Files\Common Files
PROCESSOR_LEVEL=6
PSModulePath=C:\Program Files\WindowsPowerShell\Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules
GDAL_DATA=C:\OSGeo4W\share\gdal
CommonProgramW6432=C:\Program Files\Common Files
CommonProgramFiles(x86)=C:\Program Files (x86)\Common Files
LANG=en_US.UTF-8
PUBLIC=C:\Users\Public
EXEPATH=C:\Program Files\Git\bin
COLORTERM=truecolor
USERNAME=lisha
ChocolateyInstall=C:\ProgramData\chocolatey
LOGONSERVER=\\DESKTOP-MO6N4D5
PROCESSOR_ARCHITECTURE=AMD64
POSTGIS_ENABLE_OUTDB_RASTERS=1
SECRET_KEY=11^lu^--a1jxn+v6j8h#d-_ekt2cdphsvbbj+if&+43c6w@vl5
LOCALAPPDATA=C:\Users\lisha\AppData\Local
ADSK_CLM_WPAD_PROXY_CHECK=FALSE
COMPUTERNAME=DESKTOP-MO6N4D5
PROJ_LIB=C:\OSGeo4W\share\proj
SYSTEMDRIVE=C:
USERPROFILE=C:\Users\lisha
PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.PY;.PYW
SYSTEMROOT=C:\Windows
USERDOMAIN_ROAMINGPROFILE=DESKTOP-MO6N4D5
PROCESSOR_IDENTIFIER=Intel64 Family 6 Model 142 Stepping 10, GenuineIntel
OneDriveConsumer=C:\Users\lisha\OneDrive
PWD=/c/Users/lisha/Dev/myInsta
HOME=/c/Users/lisha
TMP=/tmp
TERM_PROGRAM=vscode
TERM_PROGRAM_VERSION=1.41.0
OneDrive=C:\Users\lisha\OneDrive
PROCESSOR_REVISION=8e0a
NUMBER_OF_PROCESSORS=8
ProgramW6432=C:\Program Files
COMSPEC=C:\Windows\system32\cmd.exe
APPDATA=C:\Users\lisha\AppData\Roaming
TERM=cygwin
POSTGIS_GDAL_ENABLED_DRIVERS=GTiff PNG JPEG GIF XYZ DTED USGSDEM AAIGrid
WINDIR=C:\Windows
ProgramData=C:\ProgramData
SHLVL=1
PLINK_PROTOCOL=ssh
PROGRAMFILES=C:\Program Files
ALLUSERSPROFILE=C:\ProgramData
TEMP=/tmp
DriverData=C:\Windows\System32\Drivers\DriverData
MSYSTEM=MINGW64
SESSIONNAME=Console
ProgramFiles(x86)=C:\Program Files (x86)
PATH=/mingw64/bin:/usr/bin:/c/Users/lisha/bin:/c/Program Files/Python37/Scripts:/c/Program Files/Python37:/c/Windows/system32:/c/Windows:/c/Windows/System32/Wbem:/c/Windows/System32/WindowsPowerShell/v1.0:/c/Windows/System32/OpenSSH:/c/Python34/Scripts:/cmd:/c/Users/lisha/Anaconda3:/c/Users/lisha/Anaconda3/Library/mingw-w64/bin:/c/Users/lisha/Anaconda3/Library/usr/bin:/c/Users/lisha/Anaconda3/Library/bin:/c/Users/lisha/Anaconda3/Scripts:$env:Path:/c/Python27:/c/Python27:/c/Users/lisha/AppData/Local/Programs/Microsoft VS Code/bin:/c/Users/lisha/AppData/Local/atom/bin:/usr/bin:/c/Python3X:/c/OSGeo4W/bin:/c/Python3X:/c/OSGeo4W/bin:/c/ProgramData/chocolatey/bin:/c/Program Files/nodejs:/c/Program Files (x86)/Intel/Intel(R) Management Engine Components/DAL:/c/Program Files/Intel/Intel(R) Management Engine Components/DAL:/c/Program Files/MongoDB/Server/4.2/bin:/c/Users/lisha/Anaconda3:/c/Users/lisha/Anaconda3/Library/mingw-w64/bin:/c/Users/lisha/Anaconda3/Library/usr/bin:/c/Users/lisha/Anaconda3/Library/bin:/c/Users/lisha/Anaconda3/Scripts:$env:Path:/c/Python27:/c/Python27:/c/Users/lisha/AppData/Local/Programs/Microsoft VS Code/bin:/c/Users/lisha/AppData/Local/atom/bin:/usr/bin:/c/Users/lisha/AppData/Local/GitHubDesktop/bin:/c/Users/lisha/AppData/Roaming/npm:/c/tools/Cmder:/c/Program Files/heroku/bin
PS1=\[\033]0;$TITLEPREFIX:$PWD\007\]\n\[\033[32m\]\u@\h \[\033[35m\]$MSYSTEM \[\033[33m\]\w\[\033[36m\]`__git_ps1`\[\033[0m\]\n$
HOMEDRIVE=C:
ChocolateyLastPathUpdate=132118968927452634
HOMEPATH=\Users\lisha
_=/usr/bin/env