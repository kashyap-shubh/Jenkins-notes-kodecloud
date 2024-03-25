3. Installing Jenkins



1.
The user called mike has also been created in the jenkins-server.
root@jenkins-server:~# id mike
uid=1001(mike) gid=1002(mike) groups=1002(mike),27(sudo)
root@jenkins-server:~# 
Switch to this user by running the below command:
root@jenkins-server:~# su - mike 
mike@jenkins-server:~$

2.
Now add this public key (/home/mike/.ssh/jenkins_key.pub) in Jenkins for the user called mike. This will allow us to interact with Jenkins using the CLI.
To do this, copy the public key to the clipboard.
mike@jenkins-server:~$ cat .ssh/jenkins_key.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQClraYlzfxuFDiL1a+7njJlrap6kzvFhWNQ4PYVQfCzfUvED6WPGXCu3ZAqMqpOLHEQkBa+hPuB+0VPZ4GMCjyxzR9YbqgxHQV44KdEUTv52KqZa5xpH0kR0CslGzXrJfEyOjx+rG/JIq0Pj0MtgnIoclqpIoa9Vdg0yUtiioqpoKcI73nbVhxd24auUKhz+LXngzuhSwEU1Dd7NuVVfiDjh4vxjVJYfIlhxQ9gYMUwiFsQsavyLPDQF9Q5/r/wS+YIMaOTmWcSdh4Cw8zQNDJ3vvHr0xdqfua9WMo/JodAEH4w0FfHcBJbz7dZA3WLsEF/aV+TBs6bFzE/FRwJkMlAfUGzbqt/Xf/JlCxc81yssZS+dQ4BkyQ07NuBdB3tES27It6LqR3P1j311NF5ZMU4kqjjCPfam3KnHxRw51BV7PWYh1M+MS3uxLhuY4SLniOpucJwKajuzDJkKbWRg63aj7BO8OUhVQMiuWSnRt473c7LRW5NaUhHdAyvbyw6vFs= mike@jenkins-server
mike@jenkins-server:~$ 
Next, add this key for the user (Navigate to People --> mike --> Configure --> SSH Public Keys)

Paste the key and hit Save.

3.



4.
Now that we have the port used by the Jenkins SSH server, let us begin interacting with Jenkins over ssh with the user mike.
As mike, try running the following commands:

mike@jenkins-server:~$ ssh -i /home/mike/.ssh/jenkins_key -l mike -p 8022 jenkins-server help

Keep a note of the options used with the SSH command:
1.	-i flag is used to point to mike's private SSH key. Remember, we have already added the public key in the Jenkins configuration.
2.	-l is the login user which in our example is mike
3.	-p is the port which we found out in the previous step to be 8022

5.
Using the help command, find out the built-in command to safely restart Jenkins from the CLI.

ssh -i /home/mike/.ssh/jenkins_key -l mike -p 8022 jenkins-server  safe-restart



Can we install a plugin on Jenkins controller from web UI as well as using Jenkins CLI? Yes


