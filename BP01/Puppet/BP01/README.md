
BP01

VDI Platform - On Premises - First for B - Full Puppet Environment

#Developer Setup Steps

##Initiation
Note : Command lines need to be run in Powershell


##Download and Install Applications

###Github

-     new-item C:\VDI_SRC_B-P\BP01\Files-Apps\  -itemType directory
        cd  C:\VDI_SRC_B-P\BP01\Files-Apps\ 
        Invoke-WebRequest https://github-windows.s3.amazonaws.com/GitHubSetup.exe -OutFile .\GitHubSetup.exe
        .\GitHubSetup.exe

- Log into the Github application
- Clone https://github.com/listlfa/VDI_SRC_B-P to C:\

###Everything Else
(This installs an older Puppet version. This is a requirement of jriviere-windows_ad)

```powershell
cd  C:\VDI_SRC_B-P\BP01\Scripts\
.\RequiredApplications.ps1
```


##Confirm Requirements
N/A


##Project

#### Setup this project as the one in development
```powershell
cd  C:\VDI_SRC_B-P\
```

```powershell
.\Common\Scripts\SetupCurrentPuppetEnvironment.ps1 `
-puppetEnvironmentSourceFolder '"C:\VDI_SRC_B-P\BP01\Puppet\BP01"' `
-puppetEnvironmentSymbolicFolder '"C:\ProgramData\PuppetLabs\code\environments\BP01"' `
-puppetEnvironmentName BP01
```


##Puppet

#### Config and 3rd party Modules
```powershell
cd  C:\VDI_SRC_B-P\
.\BP01\Scripts\PuppetConfig.ps1
```

#### Run

```powershell
cd  C:\ProgramData\PuppetLabs\code\environments\BP01
puppet apply --noop .\modules\active_directory\tests\init.pp
```
