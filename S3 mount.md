### mounting s3 file----
create bucket
Create AWS S3 bucket
Create buckets > unique name > acls enable > untick block all > create 
Select bucket and upload file > upload
Select uploaded file > uplode > permission all >
Go to properties > copy obj url > check it

add user
ADDING NEW USER IN IAM AND ENABLING MFA AUTHENTICATION
 
 
open iam
create user
give name and allow access
custom password
uncheck user must create new passwd
next
attach policies directly
Allow s3 full access
download .csv file
login as user 
check you can access only things that root user have permitted you to
 
 
PROVIDING MFA AUTHETICATION
 
 
Open IAM Dashboard go to users
create access key and download .csv file
go to security credentials > assign MFA device
select authentication app
scan QR through google authenticator and enter codes
login with user credentials and mfa code

create instance
run machine 
       sudo su -
    3  yum update -y
    yum install automake fuse fuse-devel gcc-c++ git libcurl-devel libxml2-devel make openssl-devel
   22  git clone https://github.com/s3fs-fuse/s3fs-fuse.git
   23  cd s3fs-fuse
   24  ./autogen.sh
   25  ./configure --prefix=/usr --with-openssl
   26  make
   27  sudo make install
   28  which s3fs
   29  touch /etc/passwd-s3fs
   30  vim /etc/passwd-s3fs
   31  chmod 640 /etc/passwd-s3fs
   32  mkdir /mys3bucket
       s3fs (your bucket name-aws-bucket03090000) -o use_cache=/tmp -o allow_other -o uid=1001 -o mp_umask=002 -o multireq_max=5 /mys3bucket
   35  df -h
       ls -la
   38  touch file.txt{1..100}
go to bucket refresh-check if files are added

