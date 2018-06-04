
# net-core


.net core runtime is about 25 MB.  Much smaller than mono.  

Instructions from here:   centos
https://www.microsoft.com/net/core#linuxcentos



    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'


    yum update
    yum install libunwind libicu
    
    yum install dotnet-sdk-2.0.0   # full SDK  133 M
    or
    yum install yum install dotnet-runtime-2.0.0   # basics   25 M

    

## Hacking Pisces code to compile with .net core 2.0
    May need to add source to DataTableExtensions
    
    https://github.com/dotnet/corefx.git
    
    Copied files from here , and hacked some String Resources named   'SR' to compile
    https://github.com/dotnet/corefx/tree/master/src/System.Data.DataSetExtensions/src
    
    https://github.com/dotnet/corefx/issues/19771

## script file to start API --


ConnectionString=server=localhost;database=timeseries;user id=app_user
PiscesAPIDatabase=postgresql
/usr/bin/dotnet  /home/hydromet/bin/cgi/PiscesAPI/PiscesAPI.dll


# On Linux having trouble connecting from remote host.  
I had to change the hosting.json to use actual IP address instead of locahost.

# using RHEL7/Centos7 to run asp.net

https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/linux-apache



# creating a wget re-play script from apache logs for testing memory usage and performance.

 awk -F\" '{print $2}' /var/log/httpd/access_log-20180604 | awk  '{print "wget -O a.txt "$2}' > ./karl/replay
 
 The output of this query is a script that can simulate doing 100,000+ queries on a test server.
 

