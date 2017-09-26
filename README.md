# net-core


.net core runtime is about 25 MB.  Much smaller than mono.  

Instructions from here:   centos
https://www.microsoft.com/net/core#linuxcentos



    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'


    sudo yum update
    sudo yum install libunwind libicu
    sudo yum install dotnet-sdk-2.0.0
    

## Hacking Pisces code to compile with .net core 2.0
    May need to add source to DataTableExtensions
    
    https://github.com/dotnet/corefx.git
    
    Copied files from here , and hacked some String Resources named   'SR' to compile
    https://github.com/dotnet/corefx/tree/master/src/System.Data.DataSetExtensions/src
    
    https://github.com/dotnet/corefx/issues/19771



