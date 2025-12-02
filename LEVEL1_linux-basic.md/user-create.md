## Create user
   mkdir users
   mkdir users/alice users/bob
   

## Create user and add user to the group

   sudo groupadd devs
   sudo useradd -m -G devs -s /bin/bash alice
   sudo useradd -m -G devs -s /bin/bash bob
   sudo passwd alice
   sudo passwd bob
